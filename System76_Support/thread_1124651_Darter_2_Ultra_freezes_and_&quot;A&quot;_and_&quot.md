---
title: "Darter 2 Ultra freezes and &quot;A&quot; and &quot;S&quot; lights blink on and off"
date: 2009-04-13
forum: System76 Support
---

### Post by izquierdista on 2009-04-13
My darter 2 ultra has been recently been freezing up randomly while I am working on it and the "A" and "S" green lights start blinking on and off. This just started about a week ago. 
I think it is a hardware problem because I havent noticed anything abnormal about any application or other software issue.

What could be the problem?

---

### Post by thomasaaron on 2009-04-13
That sounds like a kernel panic.

Next time it happens, reboot and *immediately* go to System > Administration > System76 Driver > Support > Create and attach the logs.tar file it creates in your home directory.

Also, *immediately* after rebooting, run this command...
cat /var/log/syslog > ~/Desktop/syslog.txt
...and attach the file that this command creates on your desktop.

---

### Post by izquierdista on 2009-04-13
what do you mean by "attach"? 

I greatly appreciate your help, this problem just had to start when I have exams coming up and thus I need for my computer to work well.

---

### Post by thomasaaron on 2009-04-13
Click on "New Reply" and then scroll down and click on "Manage Attachments." Then you can attach the logs to this thread for me (or anybody else) to look at.

---

### Post by TheBuzzSaw on 2009-04-13
This has happened to me in the past. I've never been able to reliably reproduce this problem. It would just happen at awkward times during boot or install. It just freezes and blinks.

---

### Post by greg_g on 2009-04-14
I have also had this happen but for me it usually happens when I close my lid and walk somewhere else.  It has happened both when the laptop is fully on (lid closed) in my backpack and also just holding it in my hand.  It hasn't really done it while I was actively doing work.

---

### Post by thomasaaron on 2009-04-14
Have you guys ever tried running...

sudo apt-get install linux-backports-modules-intrepid

...? It seems like it could be a kernel panic caused by the wireless driver. I need some logs to test further, particularly...

/var/log/messages
/var/log/syslog

---

### Post by izquierdista on 2009-04-16
Here is the system 76 logs.tar file.

I hope this can help solve this problem

let me know what you guys think. I have no Idea what prompted this problem as I have no experience with actually tinkering around with the OS.

---

### Post by thomasaaron on 2009-04-17
Well, you have the motherload of these...

atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0)

...which is weird. But *immediately* before it dies, you have this...
battery-stats-collector[4899]: apm_read failed with error code 1 

That sounds like the old ACPI error re-incarnated.

This thread...
[http://ubuntuforums.org/showthread.php?t=1055188&highlight=daru2&page=5](http://ubuntuforums.org/showthread.php?t=1055188&highlight=daru2&page=5)
...has a workaround that I think will fix it.

If you have a problem with the workaround, post on that thread for assistance.

---

