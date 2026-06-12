---
title: "Bitten by using the proposed repositories"
date: 2015-10-30
forum: Ubuntu Development Version
---

### Post by cariboo on 2015-10-30
I enabled the proposed repositories, on both my laptop and desktop systems, and after rebooting, I ran into an endless login loop. I couldn't log in from either the login screen or the command prompt. Has anyone else run into this, and aside from a full re-install is there anyway around it.

I did a wily install on this laptop and then used:

```
upgrade-manager -d
```

to get back to xenial, because I can't get into my desktop install, I'm hoping someone else has run into the problem and found a away to solve the problem, as I'll have to do a full backup of my home directory, as the latest backup is more than a week old.

---

### Post by zika on 2015-10-30
1. did You try UpStart?
2. did You try (in kernel boot line) systemd.unit=multi-user.target ?
3. did You try chroot?
4. was that a dist-upgrade in which ubuntu-edsktop, metacity or stuff like that was offered to be removed? If so that could be fixed...
5. You should give us some more info to start making a bridge back... ;)

---

### Post by cariboo on 2015-10-30
> **zika said:**
> 1. did You try UpStart?
2. did You try (in kernel boot line) systemd.unit=multi-user.target ?

I tried it, it didn't help

> 3. did You try chroot?

Not yet, I'm waiting for a friend to bring me his malware loaded laptop, will try it after I'm done with the laptop. :)

> 4. was that a dist-upgrade in which ubuntu-edsktop, metacity or stuff like that was offered to be removed? If so that could be fixed...

I'm running Ubuntu, so no metacity, upgrade did ask to install metacity, but it wanted to remove compiz and associated files, so I didn't upgrade it.

> 5. You should give us some more info to start making a bridge back... ;)

The desktop is running an 8 core AMD processor with 16Gib of ram, A Geforce GT-210, both a SSD for the OS and 1TB HDD for data. The install started as Utopic, and was upgraded to Vivid, then Wily and now Xenial.

I also updated while in recovery mode but that still didn't allow me to log in.

---

### Post by zika on 2015-10-30
1. when You say log-in, You mean GUI?
2. that smells like nvidia driver issue
3. did You try to log in CLI (I gave SystemD switch) and then start startx/xinit to see log... Yes, You could see log without startx/xinit since that would be last log from failure, just what we need.

---

### Post by cariboo on 2015-10-30
From my first post:

>  I couldn't log in from either the login screen or the command prompt

>  did You try to log in CLI (I gave SystemD switch) and then start startx/xinit to see log... Yes, You could see log without startx/xinit since that would be last log from failure, just what we need.

As it is now nothing is in the logs, I'll give startx/xinit a try a little later.

---

### Post by sudodus on 2015-10-30
During isotesting we have found some [COLOR="#FF0000"]**red**[/COLOR] bugs,

[http://launchpad.net/bugs/1511376](http://launchpad.net/bugs/1511376)
[http://launchpad.net/bugs/1511528](http://launchpad.net/bugs/1511528)
[http://launchpad.net/bugs/1511825](http://launchpad.net/bugs/1511825)

Maybe you are affected by one or more of them, for example the 'mtab' bug #1511376.

---

### Post by grahammechanical on 2015-10-30
I have a relative of the Nvidia GT210, the GT220. Also known as GT216. I can tell you this about it.

It is not supported by an Nvidia driver older than the 340 series. So, if you were running on the Nvidia driver when you did the upgrade,  then purge it.

Regards.

Edit: I have just checked the Nvidia drivers web site and the best on offer for the GT210 is 340.93

---

### Post by QDR06VV9 on 2015-10-30
These may be helpful if you get to tty
```
systemd.unit= 
```
Overrides the unit to activate on boot. This may be used to temporarily boot into a different boot unit, for example rescue.target or emergency.target. ( Defaults to default.target. )
```
systemd.dump_core= 
```
Takes a boolean argument. If true systemd dumps core when it crashes. Otherwise no core dump is created. ( Defaults to true )
```
systemd.crash_shell= 
```
Takes a boolean argument. If true systemd spawns a shell when it crashes. Otherwise no core dump is created. Defaults to false, for security reasons, as the shell is not protected by any password authentication.
```
systemd.crash_chvt= 
```
[COLOR=#000000][FONT=sans-serif]Takes an integer argument. If positive systemd activates the specified virtual terminal when it crashes. ( Defaults to -1 )[/FONT][/COLOR]
```
systemd.show_status= 
```
Takes a boolean argument. If true shows terse service status updates on the console during bootup. ( Defaults to true )

Booting into Rescue or Emergency Targets


**To boot directly into rescue target add systemd.unit=rescue.target** or just 1 to the kernel command line. This target is useful if the problem occurs somewhere after the basic system is brought up, during the starting of "normal" services. If this is the case, you should be able to disable the bad service from here. If the rescue target will not boot either, the more minimal emergency target might.


To boot directly into emergency shell add systemd.unit=emergency.target or emergency to the kernel command line. Note that in the emergency shell you will have to remount the root filesystem read-write by yourself before editing any files:
```
mount -o remount,rw /
```



Some more here 
[https://fedoraproject.org/wiki/How_to_debug_Systemd_problems](https://fedoraproject.org/wiki/How_to_debug_Systemd_problems)
[http://freedesktop.org/wiki/Software/systemd/Debugging/](http://freedesktop.org/wiki/Software/systemd/Debugging/)

---

### Post by ventrical on 2015-10-30
> **cariboo said:**
> I enabled the proposed repositories, on both my laptop and desktop systems, and after rebooting, I ran into an endless login loop. I couldn't log in from either the login screen or the command prompt. Has anyone else run into this, and aside from a full re-install is there anyway around it.

I did a wily install on this laptop and then used:

```
upgrade-manager -d
```

to get back to xenial, because I can't get into my desktop install, I'm hoping someone else has run into the problem and found a away to solve the problem, as I'll have to do a full backup of my home directory, as the latest backup is more than a week old.

What has helped me in a few similar situations is that I have been able to install razorqt or fvwm-crystal DE

```

sudo apt-get install razorqt

or

sudo apt-get install fvwm-crystal


```

If you have installed synaptic you can get to it by using fvwm-crystal. In fact I have been able to run it right from the command line in earlier cycles.

Once there  (I would be able to disable proposed) and then sudo update , sudo upgrade.

```

sudo apt-get dist-upgrade

```

for some reason , that command has been a real lifesaver during earlier parts of dev cycles , especially if I had left proposed on.

Regards..

---

### Post by ventrical on 2015-10-30
> **cariboo said:**
> I enabled the proposed repositories, on both my laptop and desktop systems, and after rebooting, I ran into an endless login loop. I couldn't log in from either the login screen or the command prompt. Has anyone else run into this, and aside from a full re-install is there anyway around it.

I did a wily install on this laptop and then used:

```
upgrade-manager -d
```

to get back to xenial, because I can't get into my desktop install, I'm hoping someone else has run into the problem and found a away to solve the problem, as I'll have to do a full backup of my home directory, as the latest backup is more than a week old.

I have full upgraded system with proposed enabled on:
```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```

with

```

ventrical@ventrical-OptiPlex-755:~$ inxi -b
System:    Host: ventrical-OptiPlex-755 Kernel: 4.2.0-16-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 2995 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.2 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 11.0.4
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 80.0GB (12.5% used)
Info:      Processes: 184 Uptime: 4 min Memory: 552.2/2000.1MB
           Client: Shell (bash) inxi: 2.2.28 
ventrical@ventrical-OptiPlex-755:~$ 

```

without a glitch

---

### Post by ventrical on 2015-10-30
Here are todays updates with proposed on:

```

Use 'apt-get autoremove' to remove them.
Done
The following packages will be REMOVED:
  libhogweed2 libnettle4
The following NEW packages will be installed:
  gstreamer1.0-clutter-3.0
The following packages will be upgraded:
  e2fslibs e2fsprogs firefox firefox-locale-en gir1.2-freedesktop
  gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-peas-1.0 gir1.2-totem-1.0
  gnome-contacts gnome-control-center-shared-data libcomerr2 libetonyek-0.1-1
  libgail-3-0 libgcrypt20 libgirepository-1.0-1 libgnutls-deb0-28
  libgnutls-openssl27 libgtk-3-0 libgtk-3-bin libgtk-3-common libmtp-common
  libmtp-runtime libmtp9 liboauth0 libpeas-1.0-0 libpeas-common libss2
  libtiff5 libtotem0 mime-support rsyslog tcl tk totem totem-common
  totem-plugins unity-greeter
38 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 50.3 MB of archives.
After this operation, 484 kB disk space will be freed.
Do you want to continue? [Y/n] 

```

so I will upgrade and reboot and see if that will bust my system.

Hard reboot worked just fine.

Edit:

I must add additional information that might be helpful to others. This install was originally an ubuntu-desktop (unity7) 15.10 install. I edited my sources.list to xenial with 'proposed' on. After this it had removed ubuntu-desktop completely and I would get the login loop to unity greeter. I tried to re-install ubuntu-desktop but it told me my system was broken - no gui. Si , in cli , I used 

```

sudo apt-get install xubuntu-desktop

```

 and I got the login greeter and was able to load the xubuntu-desktop GUI. Of course I had software-properties -gtk  report but fixed that with constant update/upgrade with proposed on and editing the ubuntu.info file.

Also .. at this stage of the game (since I did not loose any /home files) I will not reinstall ubuntu-desktop but leave it as an xubuntu-desktop with proposed on until it breaks.

Regards..

---

### Post by cariboo on 2015-10-30
I should add that my system had been up for 9 days, as I suspend the system when I head off to work, there were approximately 200 updates installed yesterday, and I figured that after so many updates I should reboot the system.

---

### Post by ventrical on 2015-10-30
Don't forget .. (as you probably already know) that if you get your GUI back tic OFF the proposed repo and update/upgrade, it will remove all that was upgraded from proposed and put back that which it has removed (downgrade back) before proposed and that could also prove to be a nightmare Bwahahaha .. Happy Holloween  (trick or treat) :) lol

regards..

---

### Post by cariboo on 2015-10-30
Checking /var/crash, It seems there is a couple of  crash logs created about the time I rebooted the system one, is for compiz, and the other is for lightdm, so zika may have been on to something.

**Update:** Purging and re-installing compiz, ubuntu-desktop and unity didn't help. Checking /var/log/auth.log I see:

> PAM adding faulty module: pam_kwallet5.so
PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory

I checked my laptop, runnig xenial, it doesn't have that file or directory either.

---

### Post by ventrical on 2015-10-30
> **cariboo said:**
> Checking /var/crash, It seems there is a couple of  crash logs created about the time I rebooted the system one, is for compiz, and the other is for lightdm, so zika may have been on to something.

He usually always is :)

Regards..

---

### Post by Chanath on 2015-10-31
Boot in with a live iso, mount the system, chroot into it, tick off the proposed repo, check the /etc/lightdm folder and do update & upgrade

---

### Post by cariboo on 2015-10-31
It seems to be a problem with PAM, purging pam-kwallet5 didn't solve the problem. I've tried long enough to get the system up again, but as I use this system for email, I need to get it working again, so I did a re-install, and all is good again.

I'm marking this as solved, even though the problem wasn't.

---

### Post by ventrical on 2015-11-01
> **cariboo said:**
> I enabled the proposed repositories, on both my laptop and desktop systems, and after rebooting, I ran into an endless login loop. I couldn't log in from either the login screen or the command prompt. Has anyone else run into this, and aside from a full re-install is there anyway around it.

I did a wily install on this laptop and then used:

```
upgrade-manager -d
```

to get back to xenial, because I can't get into my desktop install, I'm hoping someone else has run into the problem and found a away to solve the problem, as I'll have to do a full backup of my home directory, as the latest backup is more than a week old.

I can't find 

```

upgrade-manager -d

```
nowhere.

update-manager -d .. yes

---

### Post by cariboo on 2015-11-01
> **ventrical said:**
> I can't find 

```

upgrade-manager -d

```
nowhere.

update-manager -d .. yes

That's a typo on my part :)

---

