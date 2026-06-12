---
title: "Apache2 start at boot"
date: 2006-07-21
forum: Server Platforms
---

### Post by Kurdt on 2006-07-21
Well, i have a similar problem to [This]("http://www.ubuntuforums.org/showthread.php?t=205737&highlight=")

The thing is, i start Apache2 as root and everything works fine, but i want it to start at boot, i have the script apache2 located in /etc/init.d/ and i used the command

```
update-rc.d apache2 defaults
```

to make sure it's starting at boot, but, apache2 won't start. I do not want to start it manually everytime i power up my computer.

Where should i look for a log entry to see what's going on?

Many Thanks

Ubuntu 6.06 2.6.15-26-386

---

### Post by Thirsteh on 2006-07-21
You might want to do 'chkconfig apache2 on' (or chkconfig httpd2 on) to enable it at boot time.

Another solution:

Type: sudo apt-get install bum

Go to: System -> Administration -> Boot-Up Manager

Manage boot services from there. Much easier.

---

### Post by Kurdt on 2006-07-21
First, thanks for your answer.

chkconfig gives me a "command not found" error, searching through forums i read that update-rc.d is similar, should i get a package for chkconfig?

I installed bum and it's nice, it says that apache2 **is enabled to boot** but it's not started (light bulb off) i tried to start it and says "service started" (or sort of, i have it in spanish, so i am translating) but apache2 won't start.
So the only way to start it is on my own and as root.

System -> Administration -> Services 

Also says that apache2 is enabled to start at boot.

---

### Post by Thirsteh on 2006-07-21
'chkconfig' might just be one of my habits from Debian, I really thought that existed in Ubuntu...

It is weird indeed, does starting apache2 give any warnings?

---

### Post by Kurdt on 2006-07-24
> **Thirsteh said:**
> 'chkconfig' might just be one of my habits from Debian, I really thought that existed in Ubuntu...

It is weird indeed, does starting apache2 give any warnings?

none, apache2 starts perfectly.

---

### Post by LordHunter317 on 2006-07-24
chkconfig(8) is a RedHat-ism and doesn't exist on Debian or Ubuntu.

Anyway, if you didn't run update-rc.d as root or via sudo, it wouldn't have worked.  I suspect that's your problem.

---

### Post by harisund on 2006-07-24
Maybe you can try doing ```
sudo dpkg-reconfigure apache2-common
```

---

### Post by Kurdt on 2006-07-25
> **LordHunter317 said:**
> chkconfig(8) is a RedHat-ism and doesn't exist on Debian or Ubuntu.

Anyway, if you didn't run update-rc.d as root or via sudo, it wouldn't have worked.  I suspect that's your problem.

I ran it as root.

> **harisund said:**
> Maybe you can try doing ```
sudo dpkg-reconfigure apache2-common
```

If that will not harm my current config i'll try that.

---

### Post by eeried on 2006-07-25
Didi you install Apache as described in the Ubuntu Wiki?

I did, both on Ubuntu and on Debian, and Apache (and mysql) starts at boot.

You may have missed a dialog config while installing. Reconfiguring should be the solution, as harisund suggests. 

You may have to edit a couple of Apache config files afterwards but it's worthwhile if you want Apache start at boot. Back up your present config files.
Or else delve into Apache files, and try to find some line related to the subject -- I have edited Apache config to the minimum so I'm not really knowledgeable. 

Good luck!

---

### Post by harisund on 2006-07-25
I am pretty sure your files are not going to be affected. 

However just to be sure, backup your entire /etc/apache2 directory. The reconfigure command will ideally recreate the startup sequence. 

In the case of losing your config files, just replace the new directory with the directory you backed up and you are good to go.

---

### Post by Kurdt on 2006-07-31
Hi guys :)

I am sorry to say that i did a "dpkg-reconfigure apache2-common" but apache2  is still not loading at startup...

I just do not know what to do now. Any comments will be very appreciated.

edit: i will try something i read and tell you :)

---

### Post by az on 2006-07-31
Skype uses port 80.  Are you running skype?

---

### Post by llbbl on 2006-07-31
> **eeried said:**
> Didi you install Apache as described in the Ubuntu Wiki?

I did, both on Ubuntu and on Debian, and Apache (and mysql) starts at boot.

You may have missed a dialog config while installing. Reconfiguring should be the solution, as harisund suggests. 

You may have to edit a couple of Apache config files afterwards but it's worthwhile if you want Apache start at boot. Back up your present config files.
Or else delve into Apache files, and try to find some line related to the subject -- I have edited Apache config to the minimum so I'm not really knowledgeable. 

Good luck!

Installing it via apt-get and starting apache using #/etc/init.d/apache2 start command got it to start at boot for me also.

---

### Post by Kurdt on 2006-08-01
Thanks for the answers.. i still can't make it to start at boot.

I am not using Skype.

Is there a log file of services started at boot? Where should i look at it?

Thanks

---

### Post by djdicbob on 2006-08-01
If you want to start apache2 with the following command you have to specify run-level!

```
update-rc.d apache2 defaults
``` change to

```
 sudo update-rc.d apache2 defaults 20
```
This will start Apache as soon as it hits run-level 2.  If you replace 20 with 22.  I will start lower in run level 2!

---

### Post by Kurdt on 2006-08-02
> **djdicbob said:**
> If you want to start apache2 with the following command you have to specify run-level!

```
update-rc.d apache2 defaults
``` change to

```
 sudo update-rc.d apache2 defaults 20
```
This will start Apache as soon as it hits run-level 2.  If you replace 20 with 22.  I will start lower in run level 2!

Thanks for your reply

executing:
```
 sudo update-rc.d apache2 defaults 20
```
gives me:
```
 System startup links for /etc/init.d/apache2 already exist.
```

- maybe i should remove it before trying that?
- Looking in /etc/rcX.d i see apache2 script on every level.

---

### Post by xanthmode on 2006-08-03
I am having the exact same issues...

I got this output from the reconfigure command.

```
sudo dpkg-reconfigure apache2-common
Password:
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

---

### Post by nlz on 2008-02-11
maybe it's a stupid remark but when i was setting up my box for apache, i once removed it from BUM (boot-up manager) but i couldn't find a way to get it back in my boot record. Until i found system>preferences>services there you can mark Apache2 at start-up.

good luck

---

### Post by xanthmode on 2008-02-11
I fixed my problem by installing the Ubuntu Server Edition.  Now if I could only get my sound card to work...

xanthmode

---

### Post by MJN on 2008-02-11
That's a bit extreme! I'm sure we could've walked you through working out what was wrong (and how to fix it).

Mathew

---

### Post by xanthmode on 2008-02-11
The server edition was actually a whole lot easier.  I didn't lose anything anyway since it was a new install.  About a year and a half ago now anyway.  :)

---

