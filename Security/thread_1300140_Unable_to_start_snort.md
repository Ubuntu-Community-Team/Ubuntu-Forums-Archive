---
title: "Unable to start snort"
date: 2009-10-24
forum: Security
---

### Post by anupamk on 2009-10-24
I am running ubuntu server 9.04 as a vmware instance. When I try to start snort process, it is unable to start properly. Command : /etc/init.d/snort status states that it says failed.

error message in daemon.log under /var/log folder displays following error message :

snort[8443]: database: must enter database name in the configuration file.

Fatal Error.

++++++++++++++
I have already carried out following steps to fix the problem:

a) reinstall Snort-MySQL with all affected packages several times.

b) recreated a root mysql user and tried to use that instead of root user. I was able to connect using that user via phpmyadmin or mysql directly and grant / persmissions also looked correct.

c) change the order from:

output database: log, mysql, user=snort password= 
dbname=snort_log host=localhost 

to read 

output database: log, mysql, dbname=snort_log 
user=snort password= host=localhost 



but that also did not help. In some forum is stated that it fixed the problem in his case.


I have spend more than 7-8 hours to fix the issue but have not been able to make any progress..


I would really appreciate any help on this front.


Thnks
Rgds
Anupam

---

### Post by rkurti on 2009-11-16
Hi guys,

i was trying to install snort on Ubuntu 8.04 LST Server...but I am getting this error

omerta@ssp:/etc/snort$ sudo apt-get install snort
Reading package lists... Done
Building dependency tree 
Reading state information... Done
snort is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

it says that it is installed...but there is nothing in the /etc/snort/ ... just a rules folder is no conf file or anything....nither in the init.d there is no snort

When I tried to remove it and installit again I got this:

omerta@ssp:/etc/snort$ sudo apt-get remove snort
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages were automatically installed and are no longer required:
snort-rules-default snort-common libprelude2 snort-common-libraries libltdl3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
snort
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 1057kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 23667 files and directories currently installed.)
Removing snort ...
invoke-rc.d: unknown initscript, /etc/init.d/snort not found.
dpkg: error processing snort (--remove):
subprocess pre-removal script returned error exit status 100
postinst called with unknown argument `abort-remove'
Errors were encountered while processing:
snort
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please could someone help me with this...cuz I need it for a school project which is due wendesday!

Thanks,

Rob

---

