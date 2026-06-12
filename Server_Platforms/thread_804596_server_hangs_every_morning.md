---
title: "server hangs every morning"
date: 2008-05-23
forum: Server Platforms
---

### Post by pasoderholm on 2008-05-23
I'm using ubuntu 6.06 lts as a www server (apache2 + mysql) and also as file server. One of the applications I'm running is webcalendar which is slightly customized for our needs at work. 

My problem is that the server hangs every morning! I have an automatic database backup every day (around 7.35am) and I recieve a report by e-mail when it's done which means the server hang after that. Also, in the morning when I try to do anything on the computer it freezes as soon as I click on anything. At this point the web server and webcalendar stops working, but I can browse the shared folders from another workstation. The only way to get it working again is to pull the plug so to speak.
Also, if I don't touch the server but instead just start to surf on another workstation to our web pages it all works fine, but if I try to use the webcalendar the server hangs. 

The server has worked flawlessly for years, except for two times (once in February, and once a couple years ago). Last time it was resolved with fsck.

Any suggestions where to start searching for errors? 
What logs to go through? 
The daemon.log ends with kdm_greet: internal error: memory corruption detected, and is also warns that the user debian-sys-maint was connected to the webcalendar and didn't close the table.


-Paul

---

### Post by jonabyte on 2008-05-23
Are you sure that x is not hanging, if you cannot move the mouse around, BUT can still access the shares remotely, I would assume that the x window has crashed. Restart it by ctl-alt-backspace.

Also, check /var/log/messages for any clues.

---

### Post by pasoderholm on 2008-05-24
x shouldn't have anything to do with mysql or apache, right? As I mentioned, if I try to use the webcalendar (through a web browser on another computer) the server will hang.

---

