---
title: "Software RAID Warnings go where?"
date: 2008-12-28
forum: Server Platforms
---

### Post by coffee_bean on 2008-12-28
I have set up a computer with Ubuntu Server 8.10 installed, the main reason for which being that a reliable file server was needed here.

It has two SATA drives configured with software RAID and is headless. I check on it from time to time with SSH/X11 but that will soon stop. It has the LAMP stack installed.

The point of all this is that the people here now have a reliable backup location. This is only true if I know if a drive fails, or starts to, so that I may change it before the second drive goes too.

My question: What warnings will be made, and is it possible to send these warnings, say, to an external email address? Are there any other suggestions?

---

### Post by Krupski on 2008-12-29
> **coffee_bean said:**
> I have set up a computer with Ubuntu Server 8.10 installed, the main reason for which being that a reliable file server was needed here.

It has two SATA drives configured with software RAID and is headless. I check on it from time to time with SSH/X11 but that will soon stop. It has the LAMP stack installed.

The point of all this is that the people here now have a reliable backup location. This is only true if I know if a drive fails, or starts to, so that I may change it before the second drive goes too.

My question: What warnings will be made, and is it possible to send these warnings, say, to an external email address? Are there any other suggestions?

Sure. Create a file named ".forward" in root's home directory. The file should be -rw-r--r-- (chmod 0644) and it should contain only one line... your real outside email address. Note that the filename is ".forward" (dot-forward).

Whenever your server sends ANY messages to "root", they will be forwarded to your real email address.

Neat, huh?

---

### Post by Cracauer on 2008-12-29
> **coffee_bean said:**
> I have set up a computer with Ubuntu Server 8.10 installed, the main reason for which being that a reliable file server was needed here.

It has two SATA drives configured with software RAID and is headless. I check on it from time to time with SSH/X11 but that will soon stop. It has the LAMP stack installed.

The point of all this is that the people here now have a reliable backup location. This is only true if I know if a drive fails, or starts to, so that I may change it before the second drive goes too.

My question: What warnings will be made, and is it possible to send these warnings, say, to an external email address? Are there any other suggestions?

Are you talking about Linux' md RAID or about mainboard onboard junk RAID?

md will send selected messages via syslog to kernel.log or whatever you have configured in syslogd.conf.  You can and should configure syslog to do over-network reporting to a machine where you tail -F a file. If you want more you need to run md's userland utilities from a crontab.

Myself, I just let a cronjob mail the diff of /proc/mdstat every minute.

For onboard junk raid, good luck.

---

### Post by borahshadow on 2008-12-30
There is a way to tell mdadm through mdadm.conf what email to send email to but the .forward method seems just as good or better because by default mdadm will send it to root.

BTW thanks for the .forward tip Krupski I didn't know that until now :D

---

### Post by coffee_bean on 2008-12-30
Cheers guys! I had set up an e-mail subscription on this thread, but received no notifications... I'll look into that.

Anyway. The .forward tip sounds excellent. I must admit I don't fully understand Cracauer's tips, and I'm not a complete Linux moron, just don't appear to have much experience in that area.

It is MDADM being used (not the rubbish 'on-board/off-board' middle solution).

I'll implement Krupski's beautifully simple solution, and wait to see whether Cracauer comes back to enlighten me.

---

