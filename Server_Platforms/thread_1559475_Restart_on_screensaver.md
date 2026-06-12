---
title: "Restart on screensaver"
date: 2010-08-23
forum: Server Platforms
---

### Post by exploitations on 2010-08-23
Whenever the screen goes blank, my server restarts by itself.
Is there anyway to turn this off? I've been searching all day, and I can't find anything.

---

### Post by arrrghhh on 2010-08-23
Are you running X on the server...?  I didn't think there are any screensaver settings or even a screensaver option if you don't have X installed.

There may be some low-power monitor settings without X, I'm not sure...

---

### Post by exploitations on 2010-08-23
I don't think so, I did a clean installation yesterday. All I installed was xampp

---

### Post by arrrghhh on 2010-08-23
xampp... as in LAMP?  Did you install it thru the Ubuntu Server install disc or by hand/on your own...?

Either way that shouldn't install X.  This is a server installation, right?

---

### Post by exploitations on 2010-08-23
yeah, it has everything installed into one.
I'm setting up everything now, I have apache, php, mysql working, but I'm still trying to get FTP to work

---

### Post by arrrghhh on 2010-08-23
K, what do your logs look like?  Do you have any X.org logs?

---

### Post by exploitations on 2010-08-23
how would I check that?

(Sorry, I'm a total noob at this)

---

### Post by arrrghhh on 2010-08-23
> **exploitations said:**
> how would I check that?

(Sorry, I'm a total noob at this)

Hrm, perhaps we should start a little lower.

How do you know it's the screensaver?  You really have a monitor hooked up to your server install always?

So as soon as the screen goes blank, it goes off... back on... and then you see POST?  (Basically the thing you see when the machine first starts booting...)

Perhaps there's something else happening here, and it's not your screen saver at all.  Have you tried to keep the session running?  Have you noticed how long it takes to reboot?  I honestly don't think a screensaver is your problem.

Does the server bootup no problem?  Can you login without an issues on a fresh boot?

---

### Post by exploitations on 2010-08-23
It randomly restarts itself. I noticed it does this soon after the screen goes blank. Yes, I do keep the session going. But, everything seems to be working fine now.

I have another question, I need to get FTP going.. I've tried proftpd and vsftpd
I can't get either going

---

### Post by arrrghhh on 2010-08-23
> **exploitations said:**
> It randomly restarts itself. I noticed it does this soon after the screen goes blank. Yes, I do keep the session going. But, everything seems to be working fine now.

I have another question, I need to get FTP going.. I've tried proftpd and vsftpd
I can't get either going

So it doesn't randomly restart anymore...?

Have you tried doing some searches on setting up an FTP server in Ubuntu?

[Here's](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html) the server guide on FTP servers in Ubuntu.  Perhaps you should look into something like Webmin for managing the server...?

---

### Post by exploitations on 2010-08-23
Nope, it hasn't for a couple hours.

Yeah, I've been going off that guide, but I don't understand how to make users, and when I did, I don't know how to make it go to my WWW directory

---

### Post by arrrghhh on 2010-08-23
> **exploitations said:**
> Nope, it hasn't for a couple hours.

Yeah, I've been going off that guide, but I don't understand how to make users, and when I did, I don't know how to make it go to my WWW directory

So users on the box need to belong to the proper group.

Perhaps [this](http://ubuntuforums.org/showthread.php?t=518293) will help more...

Also, [this](http://cviorel.easyblog.ro/2009/03/05/how-to-setup-vsftpd-ftp-on-ubuntu-linux/) site goes thru the user setup of vsftpd.  The previous ubuntuforums guide I posted is amazingly thorough.

---

