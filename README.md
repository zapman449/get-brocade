get-brocade
===========

Retrieve a SAN Fabric's information from the brocade switches.

get-brocade.py <fabric_name>
will retrieve the switchshow output, zoneshow output (from the first switch), 
and parse out the alias list from zoneshow.  The alias list is in a convienient format for parsing with standard UNIX tools later.  One huge feature of this:
If it runs across an L-Port, the program will descent to 'portshow' to gather 
the WWN list for that L-Port, and do an alias match against it.

get-brocade.conf
The config file.  This shows the switch DNS name => fabric name mapping.  
In theory, there's no limit to the number of switches in a fabric, but the 
data gathering is serialized currently, so it could be slow for very large
fabrics.
Ex:
switch1.domain.com => fabric_a  
switch2.domain.com => fabric_a  
switch3.domain.com => fabric_a  
switch4.domain.com => fabric_b  
switch5.domain.com => fabric_b  
switch6.domain.com => fabric_b  

defines two fabrics, each with three switches in them
Switch names must be FQDN's

NOTE: This program requires paramiko to be installed somewhere in the python
path.  Otherwise, this should be fairly generic to python 2.4 or higher
