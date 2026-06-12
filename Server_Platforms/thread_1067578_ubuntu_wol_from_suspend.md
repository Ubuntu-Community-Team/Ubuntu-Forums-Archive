---
title: "ubuntu wol from suspend"
date: 2009-02-12
forum: Server Platforms
---

### Post by Serangan on 2009-02-12
I was wondering, my wol works. But it would be nice to be able to wol it from suspend. Not a cold start.
My server machine takes about 2 mins to start (has to check all the memory).

I have the wonderful 3c59x nic... so i've had to 'hack' wol to work. But if I can make it wol from a cold start, surely it must be possible to start it from sleep.

Also, from memory, I think the nic driver isnt unloaded as the light stays on on the hub when ubuntu is in suspend mode.

If you need to know anything else, just ask, im happy to tell you.

---

### Post by Serangan on 2009-06-03
Very late bump.

Also, im now running 9.04 server edition.
WOL is working from cold boot (as before)

I still have the 3c59x driver

Anyone?

---

### Post by tgalati4 on 2009-06-04
Sometimes there's a BIOS setting:  "Allow PCI devices to wake from suspend"

If this is turned off, then the card will try to wake, but the BIOS will trap it.  This is similar to trapping mouse or keyboard events to prevent wake-up.

Should be in your power management settings of the BIOS.

---

### Post by Serangan on 2009-06-04
From memory, the BIOS has is allowing PCI devices to wake from suspend (ill check it though).

Also, I've bought a new NIC - now a dlink. so it does support wol properly.

I was reading that it could be the fact that the NIC gets unloaded during suspend. I have no idea how to stop this happening, Im using ```
sudo pm-suspend
``` if that helps

The BIOS is configured to allow the network card to wake up the computer. So im thinking that it is the fact that Ubuntu unloads the NIC while going into suspend mode?

---

### Post by tgalati4 on 2009-06-04
whereis resume.sh

also check sleep.sh and suspend.sh
/etc/default/acpi also has some settings.

---

### Post by Serangan on 2009-06-05
Im assuming whereis resume.sh is a command?

As it comes up with
```
Vectra:/etc/default$ whereis resume.sh
resume:

```

Sleep.sh
```

Vectra:/etc/default$ whereis sleep.sh
sleep: /bin/sleep /usr/share/man/man1/sleep.1.gz

```

suspend.sh
```

Vectra:/etc/default$ whereis suspend.sh
suspend:

```

Also, /etc/default/acpi doesnt exist.
acpid is there - is this similar?

---

### Post by tgalati4 on 2009-06-05
cat /etc/default/acpi-support
cat /etc/acpi/resume.sh
cat /etc/acpi/hibernate.sh
cat /etc/acpi/sleep.sh

examine all the files in /etc/acpi/resume.d

---

### Post by Serangan on 2009-06-05
As you can see, I can't do this. 
```
cat: /etc/default/acpi-support: No such file or directory

```
```
cat: /etc/acpi/resume.sh: No such file or directory

```
```
cat: /etc/acpi/hibernate.sh: No such file or directory

```
```
cat: /etc/acpi/sleep.sh: No such file or directory

```

```
-bash: cd: /etc/acpi/resume.d: No such file or directory

```

None of it exists.

Suspending is done via ```
echo -n mem > /sys/power/state
```
As it works better than ```
pm-suspend
```

I'm still newish to Linux. Is there something extra I need to install?
I remember when I was using the desktop edition of Ubuntu as a server, these files existed. I know that there are packages not installed when using server edition, but as to which ones need to be installed, I have no idea.

Acpi is installed; ```
$ sudo apt-get install acpi
Reading package lists... Done
Building dependency tree
Reading state information... Done
acpi is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by tgalati4 on 2009-06-05
Those files contain switches for modifying sleep/resume behavior in gutsy.  You are running jaunty, so you will have to search for similar files.

---

### Post by Serangan on 2009-06-06
Any ideas of the where abouts they might be?

---

### Post by tgalati4 on 2009-06-06
ls -la /etc/default
ls -la /etc/acpi

find /etc -name "resume.sh"
find /etc -name "sleep.sh"
find /etc -name "hibernate.sh"
find /etc -name "acpi-support"

---

### Post by Serangan on 2009-06-07
```
$ ls -la /etc/default
total 152
drwxr-xr-x   2 root root 4096 2009-06-04 18:42 .
drwxr-xr-x 115 root root 4096 2009-06-07 12:05 ..
-rw-r--r--   1 root root  514 2008-09-26 11:25 acpid
-rw-r--r--   1 root root  637 2009-04-02 03:01 apache2
-rw-r--r--   1 root root  219 2009-03-23 21:17 avahi-daemon
-rw-r--r--   1 root root   47 2009-03-31 20:01 bootlogd
-rw-r--r--   1 root root 1937 2009-05-15 04:37 console-setup
-rw-r--r--   1 root root  469 2008-11-13 02:47 cron
-rw-r--r--   1 root root  122 2009-04-17 19:16 cups
-rw-r--r--   1 root root  297 2009-01-28 01:37 dbus
-rw-r--r--   1 root root   92 2009-03-31 20:01 devpts
-rw-r--r--   1 root root  316 2009-06-01 23:10 dhcp3-server
-rw-r--r--   1 root root   13 2009-04-04 02:18 hal
-rw-r--r--   1 root root   86 2009-03-31 20:01 halt
-rw-r--r--   1 root root 1225 2009-05-15 21:15 hddtemp
-rw-r--r--   1 root root   69 2009-04-09 11:16 kernel-helper-rc
-rw-r--r--   1 root root  313 2009-01-24 05:33 klogd
-rw-r--r--   1 root root  823 2009-03-27 01:43 linux-restricted-modules-common
-rw-r--r--   1 root root   19 2009-05-15 04:37 locale
-rw-r--r--   1 root root  456 2009-03-21 11:49 ntpdate
-rw-r--r--   1 root root   75 2009-03-19 11:46 powernowd
-rw-r--r--   1 root root  211 2009-02-14 10:34 proftpd
-rw-r--r--   1 root root  284 2009-05-15 06:03 rcS
-rw-r--r--   1 root root 1352 2009-02-27 12:27 rsync
-rw-r--r--   1 root root  258 2009-05-15 06:00 samba
-rw-r--r--   1 root root  146 2009-05-15 06:00 saned
-rw-r--r--   1 root root  608 2008-12-23 00:31 shorewall
-rw-r--r--   1 root root  428 2008-12-18 21:07 smartmontools
-rw-r--r--   1 root root  908 2009-02-26 17:22 spamassassin
-rw-r--r--   1 root root  244 2009-05-29 18:38 squid
-rw-r--r--   1 root root  381 2009-01-29 08:01 ssh
-rw-r--r--   1 root root  186 2009-01-24 05:33 syslogd
-rw-r--r--   1 root root  559 2009-06-03 19:01 sysstat
-rw-r--r--   1 root root  289 2009-03-31 20:01 tmpfs
-rw-r--r--   1 root root 1375 2009-05-17 18:06 ufw
-rw-r--r--   1 root root 1118 2009-04-04 16:49 useradd
-rw-r--r--   1 root root  153 2009-03-28 03:02 winbind
-rw-r--r--   1 root root  316 2008-07-28 22:26 xinetd
$ ls -la /etc/acpi
total 20
drwxr-xr-x   3 root root 4096 2009-06-06 12:57 .
drwxr-xr-x 115 root root 4096 2009-06-07 12:05 ..
-rwxr-xr-x   1 root root 2534 2009-06-03 20:30 autosleep.sh
drwxr-xr-x   2 root root 4096 2009-05-14 21:13 events
-rwxr-xr-x   1 root root  517 2009-04-28 20:18 powerbtn.sh
```

```

$ sudo find /etc -name "resume.sh"
$ sudo find /etc -name "sleep.sh"
$ sudo find /etc -name "hibernate.sh"
$ sudo find /etc -name "acpi-support"

```

There isn't an output for any of the finds. I tried replacing the /etc with just a / and this still resulted in nothing being found. Im starting to think that acpi might not be fully installed?
Or the server edition of acpi could be different to the desktop edition?

---

### Post by tgalati4 on 2009-06-08
I feel like an  idiot.  Those files don't exist on the server version!  I missed that in your earlier post.

If you need wake from suspend, then install the desktop version and simply run it like a server.

(crawling back into hole . . .)

---

### Post by Serangan on 2009-06-08
:P its all right. we all make mistakes

Would it be possible to take the files from the non-server edition? cause i really dont want to have to reinstall...

0r, would there be another way of waking from being suspended?

Would installing a GUI make the kernal change to the desktop edition?

---

### Post by Serangan on 2009-06-09
Right, new small question.

If i install the desktop edition. is it possible to disable/remove the gui with all the 'extras'?

---

### Post by tgalati4 on 2009-06-09
There are kernel differences between the two.  The desktop version is more responsive for mouse and desktop use.  Search the forums for the differences.  Task scheduling is different, buffering, cache useage, swapiness, etc are all optimized for each environment.

I don't think you can add the resume scripts to the server addition because the suspend/resume hooks have probably been removed from the kernel for performance reasons.

You could use a light desktop version (such as xubuntu with XFCE desktop).  You don't have to start the desktop.

Look for the "startx" or "xinit" in one of the boot up scripts.  Simply comment it out and it will leave you with a terminal.  You can also change the session at the login gdm (graphical display manager).

The server edition loads about 50 processes at boot.  The desktop loads around 100 with the graphical desktop in use.

For home use, you probably won't notice any performance difference between desktop and server editions.  If you are trying to save power (my power bill is about $67 US per year per server, so it adds up quickly), then suspend is a good idea, if you can get it to work reliably.

---

### Post by Serangan on 2009-06-09
Hmm,

Well, i have a low powered server (it's a P3 and with only 512mb ram. Uses most of that already), so I dont want to have lots running.

Installing xfce in the server edition? would that install the resume/suspend hooks?

Also, is the desktop edition of Ubuntu as secure or can be as secure as the server edition?

---

### Post by Serangan on 2009-06-10
Working. I installed Ubuntu Desktop edition make a few scripts and it worked!

Thanks for the help/suggestions. I just have to remove the GUI now.

---

### Post by rickwookie on 2009-07-07
> **tgalati4 said:**
> I feel like an  idiot.  Those files don't exist on the server version!  I missed that in your earlier post.

If you need wake from suspend, then install the desktop version and simply run it like a server.

(crawling back into hole . . .)

Hi there

I've been trying to get WOL from S3 working on my server for over a year and can only get it so that is wakes from S3 once, then I have to reboot to get it to work again (otherwise it will ignore WOL packets when put to sleep for a second time and subsequent times). It will always wake fom shutdown, but then I have a minute to wait before my server is ready as opposed to the 2 or 3 seconds from sleep and I don't think there's much power usage difference between the S3 state and shutdown (S5) on my machine.

Just so I understand this properly before I make a major change to my server, is there a known flaw with the server kernel that is not present in the desktop kernel that prevents WOL from S3 from working?

---

### Post by Serangan on 2009-07-07
What i've done is use the desktop edition kernel. I couldnt get wol from suspend (s3) working at all. like you said, it would wol from 'off' flawlessly.

Is it safe to assume your using the server edition kernel?

and that you somehow have ```

sudo ethtool -s ethX wol g
```
run each time your server comes back up?

*edit*

If you are running the server kernel, and have wol working (once) from suspend (s3) can you tell me how you managed this? I'd love to be able to run the server edition of ubuntu

---

### Post by rickwookie on 2009-07-07
> **Serangan said:**
> What i've done is use the desktop edition kernel. I couldnt get wol from suspend (s3) working at all. like you said, it would wol from 'off' flawlessly.

Is it safe to assume your using the server edition kernel?

and that you somehow have ```

sudo ethtool -s ethX wol g
```
run each time your server comes back up?

*edit*

If you are running the server kernel, and have wol working (once) from suspend (s3) can you tell me how you managed this? I'd love to be able to run the server edition of ubuntu

Yes, my 'ethtool set' to tell the NIC to wake on magic packets is in a script I created called wol-enable that I put in /etc/network/if-up.d/ so that it runs every time the network interface is brought up. (Remember to make the script executable folks!)

This is the script:
```
#!/bin/bash
PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
sudo ethtool -s eth0 wol g
echo enabled > /sys/class/net/eth0/device/power/wakeup
```

Now that last line is what I though got the system to WOL from S3. If I comment it out though (just tried it now) it makes no difference, so ignore it! Thing is I can't work out why it's only one-shot from S3. If I first ```
sudo ethtool -s eth0 wol d
``` then ```
sudo /etc/init.d/networking restart
``` that script gets called since it sets wol back to 'g'. But after a resume from S3 even though ethtool is telling me wol=g, the system won't resume again from pm-suspend (S3). In fact it gets so broken that it won't even wake from S5 the next shutdown, I have to boot, then shutdown again. It's this that makes me think that something happens when the OS boots that puts the NIC in the right mood to wol, but I can't seem to find what it does so I can replicate it in my script. I've even tried unloading and reloading the NIC driver module (via-rhine in my case) but it still won't work.

If it is the kernel that's at fault then can't I just use aptitude to install the desktop version of the kernel and leave everything else as it is? Will that even leave me with a working system?

---

### Post by Serangan on 2009-07-08
As tgalati4 said, you need to install the desktop edition if you want wol from sleep (as i have found out)

Installing the desktop via aptitude wont install the desktop server kernel i think, you'd need to reinstall with the desktop edition.

At one stage, i installed gnome onto the server edition and it didnt change the kernel.

---

### Post by rickwookie on 2009-07-08
I managed to install the generic (desktop) kernel fine using the linux-image-generic and linux-restricted-modules-generic packages, then booted to the desktop kernel from grub and did a 'uname -a' to check that it was not the server kernel running. I also installed the acpi-support package (which gives all the acpi scripts). None of that made any difference.

Do you no exactly what component of the desktop version is making this thing work as it doesn't seem to be the kernel alone. I really don't want to clean in stall to the desktop version, since I have so much set up just how I want it already.

---

### Post by Serangan on 2009-07-08
well, apparently the server kernel removes all the acpi 'hooks' but since you say you have hte generic (desktop) kernel working, it should just work. Im still knew the linux, so i have no idea what component it is. 

Could it be that the acpi-support-package (or any acpi package) for the server install could be different due to the usages for each kernel?

---

### Post by sipu123 on 2009-07-14
hello i have applied these changes and WOL is working fine when i used it to wake my machine from turn off mode....

But it is not working when i switches my machine to sleep mode. My machine is not responding to magic packet sent , if it is in sleep mode. Also this all happens with ubuntu only .....If i go to sleep mode through Windows 7 ultimate. Then my machine can detect the magic packet and resume all the state of machine as earlier.

Can WOL for sleep/suspend/hibernate is possible in ubuntu......if yes do we require some more changes and what are those changes required.

please reply.

---

### Post by xraynorm on 2009-10-04
I have the same problem. WOL works from 

shutdown -h now

but not from

pm-suspend  (suspend to ram)

Any help would be appreciated

ubuntu server 9.04

---

### Post by alumin on 2010-02-09
> **xraynorm said:**
> I have the same problem. WOL works from 

shutdown -h now

but not from

pm-suspend  (suspend to ram)

Any help would be appreciated

ubuntu server 9.04

Same problem here. Ubuntu Minimal 9.04.

---

