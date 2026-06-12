---
title: "Cacti install problem"
date: 2007-08-02
forum: Server Platforms
---

### Post by Viruk on 2007-08-02
Hi, 

I have set up a LAMP server using Ubuntu server 6.06.1
 I have installed ssh and webmin (I run the servers with only network and power plugged in) and this is all working ok. 

I installed the rrdtool package with no problems.

I have followed the guide on the cacti website for installing on unix systems. 

I have got to the point where I point a browser at the server and go through the first couple of screens of the cacti setup then hit a problem on the last screen before the first log on. 

I then see the following:

Cacti Installation Guide 
Make sure all of these values are correct before continuing.

[FOUND] RRDTool Binary Path: The path to the rrdtool binary.
 


[NOT FOUND] PHP Binary Path: The path to your PHP binary file (may require a php recompile to get this file).
 


[NOT FOUND] snmpwalk Binary Path: The path to your snmpwalk binary.
 


[NOT FOUND] snmpget Binary Path: The path to your snmpget binary.
 


[NOT FOUND] snmpbulkwalk Binary Path: The path to your snmpbulkwalk binary.
 


[NOT FOUND] snmpgetnext Binary Path: The path to your snmpgetnext binary.
 


[FOUND] Cacti Log File Path: The path to your Cacti log file.
 


SNMP Utility Version: The type of SNMP you have installed. Required if you are using SNMP v2c or don't have embedded SNMP support in PHP.
UCD-SNMP 4.x NET-SNMP 5.x 


RRDTool Utility Version: The version of RRDTool that you have installed.
RRDTool 1.0.x RRDTool 1.2.x 


NOTE: Once you click "Finish", all of your settings will be saved and your database will be upgraded if this is an upgrade. You can change any of the settings on this screen at a later time by going to "Cacti Settings" from within Cacti.

I have attached a screenshot of this screen.

Has anyone got any ideas how to sort this? I know php must be installed but I'm not so sure about the snmp items.
Can anyone tell me if any of the missing items will be installed by default on a LAMP installation and if so where these binaries are stored on ubuntu server 6.06.1 ?

Thanks in advance for any help with this =)

---

### Post by Viruk on 2007-08-03
I have solved most of the errors by installing the following packages:
libsnmp-base 
libsnmp5 
snmp 
snmpd packages 

Unfortunately these were not listed in the install guide I was using.

I am still not sure how to solve the PHP binary path problem...

---

### Post by Viruk on 2007-08-09
The problem was that the binaries for php were not installed when I did the LAMP install from the server CD. 

I dont know if this was a problem with my install, something I did wrong or if they are just not included with the default install. 

I installed a couple of extra packages (after some help elsewhere on the forums :) ) and its sorted.

---

