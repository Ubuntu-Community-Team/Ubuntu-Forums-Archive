---
title: "rkhunter detects suspicious files types in /dev"
date: 2016-07-23
forum: Security
---

### Post by dominoes2 on 2016-07-23
Dear ubuntu community, clamtk has been PERSISTANTLY getting detections on a single type of trojan called "Trojan agent 37075", and even after updating ubuntu software, scanning again and removing the agent several times, there is nothing to be done, and the trojan keeps returning!  

So after installing and scanning for rkhunter to check for rootkits, there were detections such as these.  ```
 [12:23:22] Warning: Suspicious file types found in /dev: 
[12:23:22]          /dev/shm/pulse-shm-3169314186: data
 [12:23:22]          /dev/shm/pulse-shm-103860278: data 
[12:23:22]          /dev/shm/pulse-shm-3876879498: data 
[12:23:22]          /dev/shm/pulse-shm-1004738134: data 
[12:23:22]          /dev/shm/pulse-shm-3495351011: data 
[12:23:22]          /dev/shm/user-Shm_125376fc: data
 [12:23:22]          /dev/shm/user-Shm_97a4d6b0: Amiga Workbench
 [12:23:22]          /dev/shm/user-Shm_8ec94f4e: dBase III DBT, version number 0, next free block index 26910
 [12:23:22]          /dev/shm/pulse-shm-3930161738: data
 [12:23:22]          /dev/shm/user-Shm_3d9d4079: data
 [12:23:22]          /dev/shm/user-Shm_eec7db1e: data
 [12:23:22]          /dev/shm/user-Shm_3c3a3c3d: data
 [12:23:22]          /dev/shm/user-Shm_c9edbd50: data
 [12:23:22]          /dev/shm/pulse-shm-145637901: data
 [12:23:22]          /dev/shm/user-Shm_4ece24b7: data
 [12:23:22]          /dev/shm/user-ValveIPCSharedObjects5: data 
[12:23:22]          /dev/shm/pulse-shm-1089988604: data
 [12:23:22]          /dev/shm/pulse-shm-1083684022: data
 [12:23:22]          /dev/shm/pulse-shm-4068732159: data
 [12:23:22]          /dev/shm/pulse-shm-1293559738: data
 [12:23:22]          /dev/shm/pulse-shm-3973289782: data
 [12:23:22]          /dev/shm/pulse-shm-391874365: data 
[12:23:22]          /dev/shm/pulse-shm-3713964016: data
 [12:23:22]          /dev/shm/pulse-shm-2765873840: data
 [12:23:22]          /dev/shm/pulse-shm-4115922955: data
 [12:23:22]          /dev/shm/pulse-shm-2693726754: data 
[12:23:22]          /dev/shm/pulse-shm-3282690935: data 
[12:23:22]          /dev/shm/pulse-shm-102715192: data
 [12:23:22]          /dev/shm/pulse-shm-3961093023: data 
[12:23:22]          /dev/shm/pulse-shm-3910303618: data
 [12:23:22]          /dev/shm/pulse-shm-3687846684: data 
[12:23:22]          /dev/shm/pulse-shm-1089988604: data
 [12:23:22]          /dev/shm/pulse-shm-1083684022: data
 [12:23:22]          /dev/shm/pulse-shm-4068732159: data
 [12:23:22]          /dev/shm/pulse-shm-1293559738: data
 [12:23:22]          /dev/shm/pulse-shm-3973289782: data
 [12:23:22]          /dev/shm/pulse-shm-391874365: data
 [12:23:22]          /dev/shm/pulse-shm-3713964016: data
 [12:23:22]          /dev/shm/pulse-shm-2765873840: data
 [12:23:22]          /dev/shm/pulse-shm-4115922955: data
 [12:23:22]          /dev/shm/pulse-shm-2693726754: data
 [12:23:22]          /dev/shm/pulse-shm-3282690935: data 
[12:23:22]          /dev/shm/pulse-shm-102715192: data
 [12:23:22]          /dev/shm/pulse-shm-3961093023: data 
[12:23:22]          /dev/shm/pulse-shm-3910303618: data
 [12:23:22]          /dev/shm/pulse-shm-3687846684: data 


[12:23:22]   Checking for hidden files and directories     
  [ Warning ] [12:23:22] Warning: Hidden directory found: /etc/.java   and these.... 
 [12:27:23] File properties checks... [12:27:23] Files checked: 148 [12:27:23]

 Suspect files: 1 
[12:27:23]
 [12:27:23] Rootkit checks... 
[12:27:23] Rootkits checked : 365
 [12:27:23] Possible rootkits: 0  

and, in general,  

  Performing group and account checks    
 Checking for passwd file                                 [ Found ]  
   Checking for root equivalent (UID 0) accounts         [ None found ]   
  Checking for passwordless accounts           [ None found ]    
 Checking for passwd file changes                  [ Warning ]     
Checking for group file changes                          [ Warning ]     
Checking root account shell history files                [ None found ]  
 
 Performing system configuration file checks   
Checking for an SSH configuration file                   [ Not found ]     
Checking for a running system logging daemon             [ Found ]     
Checking for a system logging configuration file         [ Found ]     
Checking if syslog remote logging is allowed             [ Not allowed ]    
Performing filesystem checks     Checking /dev for suspicious file types                  [ Warning ]    

 Checking for hidden files and directories                [ Warning ]
```  

What can I do about these? are these caused by trojan agant 37075?   
Also interestingly, there are no suspicious goings on in firefox or any other browser by the way. Did not experience any noticeable or significant slow downs.

---

### Post by wildmanne39 on 2016-07-23
Thanks I was going to ask you to fix it and I am going to move it to the security section you will bee the most likely to get the help you need there.

Thanks

---

### Post by dominoes2 on 2016-07-23
If I hear false positive just once.... ](*,)

---

### Post by dominoes2 on 2016-07-23
I guess I have to learn some of the ropes, the first post alone, I forgot to turn on the scripts and the post ended up looking like a block to text. I am also new to Ubuntu and might need some guidence.

---

### Post by wildmanne39 on 2016-07-23
Welcome to the forum! in my signature is posting guidelines click on that for best practices to get your question answered.
Thanks

---

### Post by dominoes2 on 2016-07-24
I suspect I may have caught it while looking at the WinUsb website. The webpage appears to be either fake or neglected, increasing the chances of catching an infection while using an outdated version of firefox. Please be weary of that site, all.

---

### Post by Habitual on 2016-07-25
["To avoid these warnings]("https://help.ubuntu.com/community/RKhunter")" section ?

---

