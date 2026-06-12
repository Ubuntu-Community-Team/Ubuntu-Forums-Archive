---
title: "HOWTO: Webcam Surveillance on Screensaver Lock"
date: 2010-09-26
forum: Tutorials
---

### Post by unimatrix on 2010-09-26
[SIZE="5"]Goal[/SIZE]
The goal is to use your webcam to monitor activity in your room (or wherever you want to point it to), but with a twist. The monitoring needs to start and stop automatically. To do this we will rely on the screensaver. We will start monitoring when the session is locked (either automatically when the screensaver starts or when the user locks the screen manually).

[SIZE="5"]Requirements[/SIZE]
Assuming we are using one of the recent Ubuntu versions, we will require two additional things:
[LIST]
[*]Webcam surveillance software: [motion]("http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome")
[*]My Perl script which detect when the screen is locked (see attachments)
[/LIST]

[SIZE="5"]Installation[/SIZE]
[LIST=1]
[*]Install *motion* using the Ubuntu Software Center. Find it using the search box. (Alternatively you may apt-get it)
[*]Press Alt+F2 and type:
```
gksudo cp -Rp /etc/motion ~/.motion; gksudo chown -R `whoami` ~/.motion; gksudo chmod a+w /tmp/motion
```
Explanation: We need this to run motion without root privileges.
[*]Download the attached archive (*src-mon.tar.gz*) to your home folder.
[*]Go to your home folder (Places --> Home Folder), right click the archive (*src-mon.tar.gz*) and select Extract Here.
[*]Make sure the script starts automatically after login:
System --> Preferences --> Startup Applications --> Add
Name: *Idle Webcam Monitor* (can be whatever you want)
Command: *perl ~/.motion/src-mon.pl*
Comment: Leave empty or write whatever you like.
[*] Log out and log back in.
[/LIST]

[SIZE="5"]Usage[/SIZE]
[LIST=1]
[*]Lock your screen or wait for the screensaver to fire up.
[*]When the screensaver is active you have 30 seconds to leave your room before the webcam starts monitoring it.
[*]After you come back you again have 30 seconds to unlock the screensaver. Any motion longer than 30 seconds prior to unlocking will be recorded.
[*]Look into /tmp/motion too see what was going on while you were away.
[/LIST]

---

### Post by Yakir on 2012-06-12
Excellent idea!
Wish it worked.. The motion package is turned on every time I log in without turning off. I need to "sudo /etc/init.d/motion stop" it manually every time.
Any idea what it is I'm doing wrong?

---

### Post by Dlambert on 2012-06-12
Sweet idea. But can you set it to limit the amount of disk space it uses?

---

### Post by Yakir on 2012-06-12
Dlambert, you had no problem getting it to work properly?

---

### Post by giuliopepe on 2012-06-13
Motion is amazing and worked like a charm with me (I was scared when I left some worker people all alone in my house)

---

