---
title: "Snort Installation"
date: 2011-11-19
forum: Security
---

### Post by vishnu1074 on 2011-11-19
Hello All
 
When i am installing snort using apt-get install snort ,
 
I am seeing the folloeing error 

```

* Stopping Network Intrusion Detection System snort 
* No running snort instance found
* Starting Network Intrusion Detection snort [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort-mysql (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
snort
E: Sub-process /usr/bin/dpkg returned an error code (1) 
 

```
I am not able to find a solution for this problem.
 
Please help me.
 
 
Thanks

---

### Post by Dangertux on 2011-11-20
> **vishnu1074 said:**
> Hello All
 
When i am installing snort using apt-get install snort ,
 
I am seeing the folloeing error 
 
* Stopping Network [COLOR=blue][COLOR=blue !important][FONT=Verdana][COLOR=blue !important][FONT=Verdana]Intrusion [/FONT][/FONT][/COLOR][FONT=Verdana][COLOR=blue !important][FONT=Verdana]Detection[/FONT][/COLOR][/FONT][/COLOR][/COLOR] System snort 
* No running snort instance found
* Starting Network Intrusion [COLOR=blue][COLOR=blue !important][FONT=Verdana][COLOR=blue !important][FONT=Verdana]Detection [/FONT][/FONT][/COLOR][FONT=Verdana][COLOR=blue !important][FONT=Verdana]System[/FONT][/COLOR][/FONT][/COLOR][/COLOR] snort [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort-mysql (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
snort
E: Sub-process /usr/bin/dpkg returned an error code (1) 
 
 
I am not able to find a solution for this problem.
 
Please help me.
 
 
Thanks

Did you configure your database for Snort? 

[https://help.ubuntu.com/community/SnortIDS](https://help.ubuntu.com/community/SnortIDS)

try that it should help.

---

