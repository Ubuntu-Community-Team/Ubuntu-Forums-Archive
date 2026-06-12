---
title: "Ubuntu midi"
date: 2016-08-18
forum: Ubuntu Studio
---

### Post by jonas-thornvall on 2016-08-18
I am new to Linux/Ubuntu

I need the following commands to be run at startup of ubuntu
aconnect 24:0 14:0

1. Can i just add the command to a script just like in dos?
2. Where do i put the file
3. What do i name the file

JT

---

### Post by jonas-thornvall on 2016-08-18
Well i can tell what i have tried i created a file midi.conf containing aconnect 24:0 14:0 and put in /etc/init did not work probably missing some execution command?

---

### Post by jejeman on 2016-08-19
You need command to run when Ubuntu boots, or user logins?

Yes, you can use script.

---

### Post by jonas-thornvall on 2016-08-19
As i understand it aconnect stay resident in memory once loaded like a dos TSR? 
So it doesn't really matter when it loads at boot or at login, preferably it should stay in memory when logged out but it doesn't seem to matter if it is loaded when you login again.

I just want to now the format of the command, and the place and name of file to put it within.

JT

---

### Post by jejeman on 2016-08-20
Procedure for starting while login:
1. Make shell script. Use editor, make "somefile.sh". Save it somewhere in $HOME. Put this code in it
```
#!/bin/bash
aconnect 24:0 14:0
```
2. This is for UbuntuStudio (XFCE). Add this script to autorun. Setings (manager) > Session and Startup > Applicaiton autostart > Add

---

### Post by jonas-thornvall on 2016-08-20
Thank you Jejeman, now i learned a bit about howto make a script that run on startup. I created the file midi.sh in home as you said, but i run LXDE so i run starndardprograms for LXsession "autostart tab" and added "sh midi.sh" first i tried without command but it was not automatically invoked so i had to add it.

Where do you mark the thread as solved?

Thanks!

---

### Post by coldraven on 2016-08-20
> Where do you mark the thread as solved? Look for "Thread Tools" on the right hand side of your first post.

---

