---
title: "Updating virus definitions"
date: 2009-06-12
forum: Security
---

### Post by jkapera1988 on 2009-06-12
Hello

I was wondering how do I update virus definitions using the program virus scanner (CLAM AV to be exact)? When I go to update them it says that I have to log on as root to update virus definitions but I can't log on as root using the log on screen. Is there another way of updating the virus definitions.

---

### Post by ajgreeny on 2009-06-12
When you installed clamav you will also have installed freshclam, which is the app to keep the definitions updated, so you don't need to worry about it as it starts automatically at boot.

---

### Post by jkapera1988 on 2009-06-12
I see.

So it does update even when I go to Help > anti-virus  information, it says; Signatures: 0

---

### Post by ajgreeny on 2009-06-13
When you use the command ```
clamscan -ri
```to check your /home in the terminal it will tell you if the program and/or the virus signatures are out of date.  Don't worry about the program, even if you are seeing that message, and also I suspect that you will not see any errors about the virus signatures, as they should be updated automatically.  If you are using either Klamav or clamtk GUI which both offer updates, they are not usually active or effective and I would not bother with that way of updating, or trying to update.

---

### Post by jkapera1988 on 2009-06-13
I typed in the command in a terminal and says my virus definitions are older than 7 days.  When I open up the virus scanner it says. Clamtk virus scanner but when I go to Help > antivirus information it says ClamAV. The build version is 0.94.2. I think I have done something wrong.

---

### Post by ajgreeny on 2009-06-14
It's a long time since I used clamav, and I've never used clamtk, but see if freshclam is running by looking in System Monitor.  I seem to remember that it was started at boot time and just sat there sleeping for the session, checking for updates every so often.  Also check that freshclam is installed.

PS  Just checked to see if freshclam is installed as a dependency of clamav and clamtk, and note that it is now called **clamav-freshclam**.  I have no idea what will show in system monitor so look for both just to be sure.

---

### Post by jkapera1988 on 2009-06-15
Checked the system monitor and it isn't even in the list. Its probably not installed. Is there a way I can update them manually?

---

### Post by ajgreeny on 2009-06-15
Sorry, I've no idea any more.  I don't have a virus checker on my Ubuntu install, and it's so long since I did.  See if ```
man clamav-freshclam
``` helps

---

### Post by jkapera1988 on 2009-06-19
I finally got it working now. I just updated my Ubuntu version. It was version 8 but after I upgraded to version 9, it started to update. But thanks for your help anyway. I appreciate it.

---

### Post by JockVSJock on 2009-07-20
I have Clam TK Virus Scanner 3.08 on Ubuntu 8.04.  

Have read thru this thread, however want to know the following: 

-Is there a way to setup a System Cron job so that it grab the signatures automatically?  I  could run the following: 

```

 sudo ./usr/bin/clamtk

```

However still have to do help > update signatures manually.

---

### Post by cariboo on 2009-07-20
Running:

```
sudo freshclam
```

sets up a cron job that checks for new signatures hourly, if I remember correctly.

---

### Post by ajji on 2009-07-21
:o

---

### Post by DAB4970 on 2010-11-16
I have clamtk vs 4.30.  If you click on Advanced > Scheduler, you can set times for it to automatically scan and update antivirus signatures.

---

