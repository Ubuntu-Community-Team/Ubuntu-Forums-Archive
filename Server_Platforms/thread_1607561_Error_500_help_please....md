---
title: "Error 500 help please..."
date: 2010-10-27
forum: Server Platforms
---

### Post by ashton324 on 2010-10-27
Heyy guys...
I recently installed Ubuntu server 10.10 on my pc, i installed it on a partioned 250gb hardrive. This is not my first time with ubuntu server or a linux based server.
For the last 2 days i have tried to access my server from a different pc on a completly different network. I can access it via SSH, SFTP i can also access it via my remote ip. I can see the "It Works!" default apache page. I can also access phphmyadmin. Recently i installed WHMCS. I double checked i had the correct requirments in which i did and went ahead with the installation. It installed with no problems but when i came to access WHMCS after it had been installed i could not access it at all. In firefox i just get a blank webpage and in internet explorer 9 i recieve the Error 500 page. At first i thought this was a problem with WHMCS so i reinstalled and recieved the same problem. I then went ahead and totally formatted and reinstalled today. I then installed whmcs again and recieved the same problem once again. So then i tried installing phpBB and recieved the same problem on both browsers. I followed this tutorial in setting my server up. [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) after reading around and searching google extensively i believe this is a PHP problem but i cannot find no solution. if i anyone can help it will be greatly appreciated.
P.S im using this server for local development but will be using it as a public server when it is setup and working correctly.
Thanks
Ashton324

---

### Post by ashton324 on 2010-10-27
Just a quick update..
I have also tried to access it locally on 127.0.0.1 and my 192.168.*.* ip address aswell and i still get the same problem.

---

### Post by ashton324 on 2010-10-28
Bump...
Still need help guys please.

---

### Post by ashton324 on 2010-10-28
Anyone know how to solve this problem???

---

### Post by linuxpyro on 2010-10-28
What do your log files say?  See what comes up in both the access and error logs.

---

### Post by ashton324 on 2010-10-29
hey thanks for reply...
After doing some more searching i restarted the whole box and found out it was that WHMCS was corrupt. 
Thanks anyway

---

