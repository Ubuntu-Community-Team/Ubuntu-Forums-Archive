---
title: "So all those months ago"
date: 2014-04-23
forum: Ubuntu Development Version
---

### Post by Elfy on 2014-04-23
I was almost right with Unreal Unicorn :p

> IRC logs - first one I looked in 
[QUOTE]
Feb 19 15:38:51 <elfy>	3 things on the qa one, can't do one till unreal unicorn, other one I postponed - just the one that isn't going to happen this cycle to not do :)[/QUOTE]

The forum topic is going to be staying - we'll change it every 6 months.

The schedule is not there yet though :)

---

### Post by novatillasku on 2014-04-23
Ubuntu 14.10 codename is Utopic Unicorn say Mark in his blog:

U talking to me?
[http://www.markshuttleworth.com/archives/1363](http://www.markshuttleworth.com/archives/1363)

---

### Post by cariboo on 2014-04-23
Merged two similar threads. 

I say it's about time, now I can edit the stickies. :)

---

### Post by Elfy on 2014-04-23
but not the notice ... 

I'll do that when I get Xubuntu blue html code :p

I edited the sources list - but ...

---

### Post by NikTh on 2014-04-23
In case you don't know it already, the new release 14.10 [will be (code)named : Utopic Unicorn]("http://www.markshuttleworth.com/archives/1363"). The repositories are open for anyone wants to test the new development branch. In current state you can replace the sources in soucres.list file and migrate from trusty to utopic. One command is enough 

```

sudo sed 's/trusty/utopic/g' -i /etc/apt/sources.list

``` 

Then
```

sudo apt-get update; sudo apt-get dist-upgrade

```
and reboot. 

Also some systemd packages are available for testing, you can follow [Martin Pitt blog]("http://www.piware.de/2014/04/booting-ubuntu-with-systemd-test-packages-available/") on how you can test the newcoming systemd on Ubuntu. 

I'm already there and happy about it :)

[IMG]http://i.imgur.com/ALs7chQl.jpg[/IMG]

---

### Post by NikTh on 2014-04-23
Ok, I think a moderation action is needed here. I didn't see this thread [http://ubuntuforums.org/showthread.php?t=2219271](http://ubuntuforums.org/showthread.php?t=2219271) . If someone merge above post, would be nice. 
Thanks (and sorry for inconvenience)

---

### Post by cariboo on 2014-04-23
Merged by request.

---

### Post by cariboo on 2014-04-23
After having an oppertunity to read Mark's blog post, I can see why it took a couple of days for him to come up with it. all those words starting with **U**. :-P

---

### Post by cecilpierce on 2014-04-23
Just started, only one update   :p

Description:	Ubuntu Utopic Unicorn (development branch)
Release:	14.10
Codename:	utopic

---

### Post by zika on 2014-04-24
Ubuntu Unified Unity in Utopic Unicorn will be Unexpected I expect... ;)

---

### Post by zika on 2014-04-24
> **NikTh said:**
> Also some systemd packages are available for testing, you can follow [Martin Pitt blog]("http://www.piware.de/2014/04/booting-ubuntu-with-systemd-test-packages-available/") on how you can test the newcoming systemd on Ubuntu. Still on 14.04 but [COLOR=#000000][FONT=Courier New]ppa[:]pitti/systemd[/FONT][/COLOR] works nicely... With some deep and point-to-point tweaking I'm writing this from new systemd... ;)
Still having some doubts about jumping on UU wagon due to huge promises of phone/desktop unification... ;)

---

### Post by ventrical on 2014-04-24
Looks like a plug for ubuntu-myth. :)

```

Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
ventrical@ventrical-desktop:~$ 

```

---

### Post by ventrical on 2014-04-24
Quoting Mark Shuttleworth:

"Time to purge the ugsome and prune the unusable."

  I wonder if this spells the death knell for CCSM.

Regards..

---

### Post by slickymaster on 2014-04-24
One more coin, one more ride.

Everything went smoothly and with 3.15.0-031500rc2-generic kernel:```
lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
3.15.0-031500rc2-generic
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files distro-info-data
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 72,7 kB of archives.
After this operation, 1024 B disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://pt.archive.ubuntu.com/ubuntu/ utopic/main base-files i386 7.2ubuntu6 [68,7 kB]
Get:2 http://pt.archive.ubuntu.com/ubuntu/ utopic/main distro-info-data all 0.18ubuntu1 [4008 B]
Fetched 72,7 kB in 0s (76,0 kB/s)     
(Reading database ... 187757 files and directories currently installed.)
Preparing to unpack .../base-files_7.2ubuntu6_i386.deb ...
Unpacking base-files (7.2ubuntu6) over (7.2ubuntu5) ...
Processing triggers for cracklib-runtime (2.9.1-1build1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for plymouth-theme-ubuntu-text (0.8.8-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.15.0-031500rc2-generic
Setting up base-files (7.2ubuntu6) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text (0.8.8-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.15.0-031500rc2-generic
(Reading database ... 187757 files and directories currently installed.)
Preparing to unpack .../distro-info-data_0.18ubuntu1_all.deb ...
Unpacking distro-info-data (0.18ubuntu1) over (0.18ubuntu0.1) ...
Setting up distro-info-data (0.18ubuntu1) ...
```

---

### Post by Ian_Worrall on 2014-04-24
Unicorn? That's the Bronies in, then! :D

---

### Post by NikTh on 2014-04-25
> **zika said:**
> Still on 14.04 but [COLOR=#000000][FONT=Courier New]ppa[:]pitti/systemd[/FONT][/COLOR] works nicely... With some deep and point-to-point tweaking I'm writing this from new systemd... ;)
Still having some doubts about jumping on UU wagon due to huge promises of phone/desktop unification... ;)

The PPA actually is for 14.04, but you can add it to 14.10 (manually) as well. There will be no PPA for Utopic as far as Martin told me, the systemd packages will be uploaded directly to Official (Utopic) repositories. We can expect that 14.10 will have (if everything roll normal) systemd by default. 

I think is a bit early for keeping such promises (if you mean Unity 8...etc). From 15.04 or 15.10 we could speak more surely about mobile/phone/desktop convergence.

---

### Post by zika on 2014-04-25
> **NikTh said:**
> The PPA actually is for 14.04, but you can add it to 14.10 (manually) as well. There will be no PPA for Utopic as far as Martin told me, the systemd packages will be uploaded directly to Official (Utopic) repositories. We can expect that 14.10 will have (if everything roll normal) systemd by default. 
I think is a bit early for keeping such promises (if you mean Unity 8...etc). From 15.04 or 15.10 we could speak more surely about mobile/phone/desktop convergence.This day or so of living with systemd was nice... I do not have any need to go back... I've even learned some new tricks of keeping things tide and neat with systemd. Thank You for this opportunity. Still on 14.04 and waiting to see real direction 14.10 goes... ;)
First thing I've learned about systemd is that there is no rc.local way of making things happen on startup but it can be done... ;)
I'm always happy to learn new tricks even though I'm an old dog, very old... ;) Keep it coming... ;) Thank You for this opportunity, indeed.
Update&#8321;: I've caught some spare time and SystemD works with (as mentioned above) kernel-3.15-999, and also with 3.13.0-24-lowlatency and liquorix-amd64-3.13-8...

---

### Post by Cavsfan on 2014-04-25
> **Elfy said:**
> I was almost right with Unreal Unicorn :p



The forum topic is going to be staying - we'll change it every 6 months.

The schedule is not there yet though :)

Yeah you were real close and I liked Unreal Unicorn but Utopic Unicorn sounds pretty cool too. :p

```
utopic

Web definitions
A  utopia is a community or society possessing highly desirable or perfect  qualities. 
The word was coined in Greek by Sir Thomas More for his 1516  book Utopia, describing a 
fictional island society in the Atlantic Ocean....
[http://en.wikipedia.org/wiki/Utopic](http://en.wikipedia.org/wiki/Utopic)
```

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-04-25152212.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-04-25152212.php")

---

### Post by ventrical on 2014-04-25
Another cryptic way of looking at it..

U -Topic Unity Kernel  (Ubuntu Topic - Unity Kernel -Uni-corn) :) lol

---

### Post by sammiev on 2014-04-25
I am waiting to see if anyone with the ubuntu gnome updated to Utopic Unicorn yet. I will likely update the source.list tonight.

---

### Post by ventrical on 2014-04-25
> **sammiev said:**
> I am waiting to see if anyone with the ubuntu gnome updated to Utopic Unicorn yet. I will likely update the source.list tonight.

yeah .. I put in gnome-session-flashback.

---

### Post by sammiev on 2014-04-25
> **ventrical said:**
> yeah .. I put in gnome-session-flashback.

Thanks

---

### Post by ventrical on 2014-04-26
> **sammiev said:**
> Thanks


  I switched to gnome-session-compiz last night from login menu while running a unity session. After a while I shut down. Now, thismorning, after booting up,  I have no lightdm/unity-greeter. It just booted right up to gnome-session compiz.

---

### Post by sammiev on 2014-04-26
> **ventrical said:**
> I switched to gnome-session-compiz last night from login menu while running a unity session. After a while I shut down. Now, thismorning, after booting up,  I have no lightdm/unity-greeter. It just booted right up to gnome-session compiz.

Update went very well last night and updates were smooth. Today I took a load of updates and now lost my wire/wireless connections. Time to play. :)

Edit: 48 more updates taken. Over 150 today alone. Time to reboot.

---

### Post by ventrical on 2014-04-26
> **sammiev said:**
> Update went very well last night and updates were smooth. Today I took a load of updates and now lost my wire/wireless connections. Time to play. :)

I think it was mir and unity8 code that caused the problems I had.

---

### Post by Cavsfan on 2014-04-26
Me too on the Gnome Flashback (with Compiz). I haven't been off of it yet.
No issues to speak of. Received like 142 updates earlier. I probably should reboot and see it that still holds true.

I just commented out the Extra repositories. If I recall correctly those aren't available until later.

---

### Post by Cavsfan on 2014-04-26
> **sammiev said:**
> Update went very well last night and updates were smooth. Today I took a load of updates and now lost my wire/wireless connections. Time to play. :)

Rebooted and 24 more updates still smooth. Logged out and the sessions were all there went back into flashback with compiz. Haven't lost anything.

---

### Post by NikTh on 2014-04-26
> **zika said:**
> This day or so of living with systemd was nice... I do not have any need to go back... I've even learned some new tricks of keeping things tide and neat with systemd. Thank You for this opportunity. Still on 14.04 and waiting to see real direction 14.10 goes... ;)
First thing I've learned about systemd is that there is no rc.local way of making things happen on startup but it can be done... ;)
I'm always happy to learn new tricks even though I'm an old dog, very old... ;) Keep it coming... ;) Thank You for this opportunity, indeed.
Update&#8321;: I've caught some spare time and SystemD works with (as mentioned above) kernel-3.15-999, and also with 3.13.0-24-lowlatency and liquorix-amd64-3.13-8...

If you have decided to use systemd as PID 1, please take the time to report bugs(if any). 
Tag them with #systemd-boot and prefix the title with [systemd] so we can track them down easily, here &#8594; [https://bugs.launchpad.net/ubuntu/+bugs?field.tag=systemd-boot](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=systemd-boot) 

Thank you.

---

### Post by sammiev on 2014-04-26
I'm backup and running. Going after the other updates now. looks like about 20 more or so. :)

---

### Post by zika on 2014-04-26
> **NikTh said:**
> If you have decided to use systemd as PID 1, please take the time to report bugs(if any). 
Tag them with #systemd-boot and prefix the title with [systemd] so we can track them down easily, here &#8594; [https://bugs.launchpad.net/ubuntu/+bugs?field.tag=systemd-boot](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=systemd-boot) 
Thank you.Yet to find something to complain about. Even boot with linux-libre (gnu, all-free, kernel) went well with systemd (only resolution with radeon was very low, due to Saturday I did not have time to investigate...)... Have not switched (even to see if it still works) in upstart yet... ;)

---

### Post by Yahoé on 2014-04-26
For the very very early testers out there, the utopic repos are up, just update your sources.list

---

### Post by Elfy on 2014-04-26
yep - we know :)

merged

---

