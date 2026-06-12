---
title: "rkhunter warnings"
date: 2010-04-04
forum: Security
---

### Post by mjc4043 on 2010-04-04
Hi all,   I am a brand new ubuntu user as of 3 days ago and I am still probably of the windows mindset when it comes to security. I ran rootkit this morning and received the following error messages;
 
 
[09:43:49] /usr/sbin/unhide                                  [ Warning ]
 [09:43:49] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.   
 [09:43:49] /usr/sbin/unhide-linux26                          [ Warning ] 
[09:43:49] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.    

[09:44:44]   Checking /dev for suspicious file types         [ Warning ] 
[09:44:44] Warning: Suspicious file types found in /dev: 
[09:44:45]          /dev/shm/pulse-shm-3022199250: data 
[09:44:45]          /dev/shm/pulse-shm-4111408146: data 
[09:44:45]          /dev/shm/pulse-shm-1780086092: data 
[09:44:45]          /dev/shm/pulse-shm-2664733514: data 
[09:44:45]          /dev/shm/pulse-shm-4255803581: data    

[09:44:45]   Checking for hidden files and directories       [ Warning ] 
[09:44:45] Warning: Hidden directory found: /dev/.udev  [09:44:45] Warning: Hidden directory found: /dev/.initramfs    

[09:44:50] Checking application versions...  
[09:44:50] Info: Starting test name 'apps'  
[09:44:55]   Checking version of Exim MTA                    [ Warning ] 
[09:44:55] Warning: Application 'exim', version '4.69', is out of date, and possibly a security risk.   
[09:44:55]   Checking version of GnuPG                       [ Warning ] 
[09:44:56] Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.   
[09:44:56]   Checking version of OpenSSL                     [ Warning ] 
[09:44:56] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.    
-  

 I am wondering if any of you could help me by pointing out if these warnings need futher action or what?   Thank you,  Michael

---

### Post by Bachstelze on 2010-04-04
None of those are of any concern (which is the case for the vast majority of rkhunter warnings, it's not a very good security tool).

---

### Post by mjc4043 on 2010-04-04
thank you very much

---

