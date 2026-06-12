---
title: "Ubuntu Router will not ping domain names"
date: 2011-06-09
forum: Server Platforms
---

### Post by Monery on 2011-06-09
For clairification, I can ping. I have tried several IP addresses and 100% success rate. When I noticed the problem I was trying to run
**sudo apt-get update && apt-get upgrade**
 
After some time I noticed these error messages to start with
 
```
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
0% [Connecting to us.archive.ubuntu.com]
```
 
I tried to ping the adddress **security.ubuntu.com** from my Windows machine to verify that I could connect and was surprised when I could. I then pinged the address  **91.189.92.167** which is what my windows machine resolved the name as and it went though. 
 
My thoughts on this are that when my Ubuntu Router came up, for some reason it did not incorporate the ISP's DHCP servers into the ip address it obtained. Sadly I know to view ALL IP infomation in windows via **ipconfig /all** command but I do not know what this is in the *nix world. Can someone help me by giving me some commands that I can use to check and troubleshoot this apparently DHCP issue so I Can start to update my server and expand on its services?

---

### Post by Monery on 2011-06-09
[SOLVED]
 
A simple hard reboot of the machine seems to have solved the issue in the mean-time, **but** the infomation would be useful still.... Hitting the big magical box with my hammer will not always work

---

