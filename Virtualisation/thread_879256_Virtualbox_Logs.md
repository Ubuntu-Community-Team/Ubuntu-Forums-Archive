---
title: "Virtualbox Logs"
date: 2008-08-03
forum: Virtualisation
---

### Post by itchanddino on 2008-08-03
Hello.  I installed the newest version of Virtualbox, and it saves the log files to the home folder.  Is there a way to disable/change this?  Thanks!

---

### Post by Loaded.len on 2008-08-08
Yup.  Add VBOX_LOG_DEST=nofile to your environment variables. 

in your terminal...
**sudo nano ~/.profile** 

add the following lines to the end of the file...

**VBOX_LOG_DEST=nofile**
**export VBOX_LOG_DEST**


save, reboot, enjoy.

---

### Post by itchanddino on 2008-08-12
Awesome, thank you!

---

### Post by sojusnik on 2008-08-14
Hi,

Please describe it a little bit more detailed for a Linux newbie.

When I copy

sudo nano ~/.profile

in the Terminal, I see only an empty nano window with nothing in it...

How to proceed?

---

### Post by Loaded.len on 2008-08-14
This may help you...(specifically, the section on **Persistent environment variables**)

[https://help.ubuntu.com/community/EnvironmentVariables]("https://help.ubuntu.com/community/EnvironmentVariables")

---

### Post by sojusnik on 2008-08-14
Thx,

It's simplier than I thougt!

---

### Post by turezky on 2008-09-08
10x!!!

---

### Post by alexebird on 2008-10-10
Thanks!

---

