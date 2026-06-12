---
title: "Autologin from cli"
date: 2006-07-06
forum: Server Platforms
---

### Post by olliraa on 2006-07-06
How can I accomplish this? I need to login with a certain username to get things running ( at least I think so ;) I know hao to do it from X, but what about cli. What's the appropriate config file?

---

### Post by lamego on 2006-07-06
Huh ? Why should you need to autologin in text mode ?
Do you want something to be run automatically during the system startup ? That is not achieve with autologin.

---

### Post by olliraa on 2006-07-06
Yep,

this may (or surely) sound(s) lame and noobish, but I have Ubuntu LTS server installed and I want to run webcam server automatically at bootup. Actually I GOT THE automatical running ok. I played with the rc.local -file, but after it runs my webcam-script it gets stuck and never even enters the login screen. I can't get out of that situation otherwise that rebooting the computer :(  I need to get it the other way around? That's why I'm asking about the autologin. What should I do?

---

### Post by lamego on 2006-07-07
If your web cam server script hangs then you need to fix it.
Anyway you can call it from /etc/rc.local using "&" after the command to make sure it will run on the background and avoid hanging the bootup process.

---

### Post by ap0th1s on 2007-02-11
Hi there, fairly new to running a box without X.

Could someone guide me as to how I can solve this. 

1. Have an Edgy Lamp server running a 3rd party application that requires execution of a script as a particular user to run a license agent , and then run the application.

The scripts make use of user variables like /APP_USER$/start-license which get created when user logs on

I would like to automate the loading of these services if the server reboots. 

I have tried using crontab   ( specifying the @reboot /APP_USER$/start-license )   no luck. 
I also know that there is a way to use /etc/inittab , although Edgy uses /events.d

Any Ideas? ....

---

