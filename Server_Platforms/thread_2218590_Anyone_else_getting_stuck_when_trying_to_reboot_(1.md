---
title: "Anyone else getting stuck when trying to reboot (14.04)?"
date: 2014-04-21
forum: Server Platforms
---

### Post by aysiu on 2014-04-21
I have a non-critical server I upgraded to 14.04 (from 12.04.4) and another server I installed using 14.04 from scratch (not an upgrade).

On both, if I run the command ```
sudo shutdown -r now
``` it'll get stuck on ```
**Stopping System V runlevel compatibilty**
```

I've done some Googling on this issue, and all the solutions involve taking ownership of the home directory in order to start the X session properly, which doesn't fix the issue, and, more importantly, wouldn't fix it anyway, because I'm not running X (no graphical environment--just the command line).

So two questions:

1. Anyone else running into this with 14.04 server (not desktop)?

2. Any potential solutions?

P.S. I don't know if this makes a difference, but these are virtualized servers running 64-bit server edition. Never had this issue (same environment) with 12.04.4 or with 13.10.

---

### Post by aysiu on 2014-04-22
Today's kernel update seems to have fixed the issue.

---

### Post by aysiu on 2014-04-23
So the last kernel update didn't fix it for you?

---

### Post by aysiu on 2014-05-08
Unfortunately, it's happening again... so the kernel update did not, as I'd previously thought, fix this.

Any ideas?

---

### Post by bapoumba on 2014-05-08
I'm sure your search-fu is better than mine, here is a shot at something not directed to video drivers or lightdm/gdm issues. Both older threads, both related to disk space and unable to write the keyboard conf files :

[http://forums.techarena.in/operating-systems/1460293.htm#post5604149](http://forums.techarena.in/operating-systems/1460293.htm#post5604149)
[http://ubuntuforums.org/showthread.php?t=1807612&p=11538740#post11538740](http://ubuntuforums.org/showthread.php?t=1807612&p=11538740#post11538740)

---

### Post by aysiu on 2014-05-08
Thanks, bapoumba. I've got a full 5.4 G available (only 1.5 G used) when I run ```
df -h
```

---

### Post by bapoumba on 2014-05-08
Well, I saw your thread when you posted it and looked around at the time. That is all I found not related to video drivers, X configuration files, .Xauthority or desktop packages, sorry. Searched again today more specifically. There are some threads here or elsewhere regarding memory tests, but without real answers (for ex, test suggested but the OP never came back to confirm or not).

---

### Post by aysiu on 2014-05-08
Thanks. Maybe someone else is experiencing this, too...

---

### Post by gustavotonini on 2014-05-27
I'm facing the same behavior on Ubuntu 14.04 Server on VMWare ESxi 5.1.
I've tried to install linux-kernel and linux-virtual packages but I had no success. The system is completely up to date.
Have you solved the problem?

---

### Post by aysiu on 2014-05-28
Nope. In fact, I recently upgraded another virtualized server from 13.10 to 14.04, and it's exhibiting the same behavior.

If I send a Control-Alt-Delete event to the machine, it will reboot, but a traditional ```
sudo shutdown -r now
``` will make it hang instead of rebooting.

I've tried Googling the issue, but you and I seem to be the only ones experiencing this on an X-less server...

---

### Post by aysiu on 2014-05-28
Okay, it was [this](http://askubuntu.com/questions/259749/asking-all-remaining-processes-to-terminate-fail) for me: >  1 down vote
	

I was experiencing the same behaviour when using a NAS (samba share) with fixed mounting points. It was caused by some kind of race condition between the unmounting process and network-manager during termination stage on shutdown. Here's a small workaround that fixed it for me:

Fire up a terminal by pressing Ctrl + Alt + T and paste these commands:

```
sudo mv /etc/rc0.d/S31umountnfs.sh /etc/rc0.d/K15umountnfs.sh
sudo mv /etc/rc6.d/S31umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```

This simply moves the unmounting process up the priority list when shutting down or rebooting the system. At least my system is shutting down very fast again without errors.

Good luck!

---

### Post by gustavotonini on 2014-05-28
I've tested with kernels 2.6.39, 3.13.0-27 3.14.4, 3.15rc7. All kernels [COLOR=#000000]exhibit[/COLOR] the same behavior. 
I have tried to uninstall VMWare tools too. No success. We will keep using Ubuntu 12.04 in production environment until the problem is solved.
Have you reported the bug oficially to kernel dev group?

---

### Post by gustavotonini on 2014-05-28
I've tested kernels 2.6.39-02063904, 3.13.0-27, 3.14.4-031404 and 3.15.0-031500rc7. All [COLOR=#000000]exhibit [/COLOR][COLOR=#000000]the same behavior.
I have tried to uninstall VMWare tools too. No sucess.
Diid you already submit an official bug report to kernel developers?[/COLOR]

---

### Post by aysiu on 2014-05-28
No, I haven't. The weird thing is that the solution above works for me, but it was originally posted for a much older version of Ubuntu. And I didn't have this problem until Trusty.

Did that workaround work for you?

---

### Post by aysiu on 2014-05-28
Looks as if someone else already reported it (a while ago):
[https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/844317](https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/844317)

---

### Post by gustavotonini on 2014-05-28
In my case, the shutdown stops at "Asking all remaining processes to terminate".
I have changed the waitime on /etc/init.d/sendsigs to 5 but it still stops in the same step.
Have you changed anything else?

---

### Post by aysiu on 2014-05-28
I didn't change the wait time or anything besides what's in [post #11](http://ubuntuforums.org/showthread.php?t=2218590&page=2&p=13035374&viewfull=1#post13035374) of this thread.

---

### Post by gustavotonini on 2014-05-29
It didn't work for me.

---

### Post by aysiu on 2014-05-29
> **gustavotonini said:**
> It didn't work for me. It may be the same principle, though. For me, it was waiting for the network shares to unmount. For you, it may be waiting for something else that's happening in the wrong order.

Any experts out there on diagnosing shutdown/reboot issues? Which logs to check, for example?

---

### Post by bapoumba on 2014-05-29
[http://ubuntuforums.org/showthread.php?t=2084208&p=12359797#post12359797](http://ubuntuforums.org/showthread.php?t=2084208&p=12359797#post12359797), I sort of had this idea already that logs cannot be recorded past a certain point. So having a look at the screen message during booting or shutdown as Bashing-om suggests may be an option.
The files I had a look at on some other issue were /var/log/kern.log,  /var/log/pm-powersave.log and  /var/log/pm-suspend.log

No expert here, so not sure this will be helpful.

---

### Post by candlerb on 2014-07-16
I'm getting this too. Mac Mini, Ubuntu 14.04 server amd64, previously was running 12.04 no problems. No X or GUI, just console.

It was originally getting stuck at:

```

...
* Stopping System V runlevel compatibility
* rpcbind terminating on signal. Restart with "rpcbind -w"

```

but after removing nfs-kernel-server / nfs-common / rpcbind, it now finishes at "Stopping System V runlevel compatibility". This suggests that the problem is somewhere *after* this point.

If I hit ctrl-alt-del when it has hung I get

```

* Starting emergency keypress handling
* Stopping emergency keypress handling
* Stopping save system clock to hardware clock

```

---

### Post by candlerb on 2014-07-16
If I leave it for just over 6 minutes, it does reboot. Trying "halt" instead of "reboot" to capture the final messages, I just got:

```

* Stopping System V runlevel compatibility   [ OK ]
[  400.905194] reboot: system halted

```

Great... no help at all :-(

I did have a large number of interfaces (bridges and taps). I simplified this down to:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

```

(there is also a virbr0 from libvirt) and now it hangs for only about 12 seconds.

If I now add:

```

auto eth0
iface eth0 inet manual
address 10.10.0.241
netmask 255.255.255.0

```

then the hang goes up to 22 seconds.

---

### Post by candlerb on 2014-07-16
Aside: I notice that the message "Stopping System V runlevel compatibility" is left over from boot time - press Alt-F7 to see it. Also do

```

echo --- >/dev/tty7

```

to get a divider, before you reboot. It seems *no* messages get logged during the shutdown :-(

Anyway, I decided to completely wipe and reinstall this machine to try to pin it down. I have quite a lot of packages installed but they are driven by ansible so I can get it back to where it was in steps - rebooting a couple of times after each step to see if the problem re-appeared.

Initially a reboot took just under 2 seconds from issuing the command to the screen going black; even with the large number of bridge/tap interfaces added it only took about 3 seconds.

Where the problem reappeared was after the step of installing apt-cacher-ng. This also pulls in as dependencies:
avahi-daemon libavahi-core7 libdaemon0 libnss-mdns

Removing just apt-cacher-ng doesn't fix the problem, but removing avahi-daemon does (which is only a "recommends" dependency of apt-cacher-ng)

Workaround:
```

apt-get remove --purge apt-cacher-ng
apt-get autoremove --purge
apt-get install apt-cacher-ng --no-install-recommends

```

So: the problem I see could be quite specific to my scenario (lots of interfaces *and* specific daemons installed). Other people's hangs might be due to a different problem. But more generally, the fact there's no console messaging during system shutdown is very bad indeed, as it makes it pretty impossible to work out what's handing.

---

### Post by candlerb on 2014-07-16
Bug reports created upstream:

No shutdown debugging: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1342856](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1342856)
avahi-daemon shutdown delays: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1342865](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1342865)

I also think that the "Recommends: avahi-daemon" in apt-cacher-ng is pretty spurious, but I suppose somebody thinks you might want to announce an apt-cacher on your network without properly configuring it in DNS.

---

### Post by bapoumba on 2014-07-16
Thanks for all your troubleshooting :)

---

### Post by geebee75 on 2014-08-11
I'm also getting this problem on Ubuntu Server 14.04LTS, No X, no GUI.

Intel i7 PC platform tons of disk space. RAID5 root volume.

I do not have the above-mentioned apt-cache package or the avahi daemon/libraries installed.

---

### Post by Caveat_Emptor on 2014-08-24
Have the same problem. It hangs on trying to shutdown or restart. This started happening only after I upgraded to 14.04 from 13.10 and even after I did a clean install.

I was trying all the different grub options that several threads mention, to no success. As part of that, I removed "quiet splash", just to see detailed messages (dmesg does not yield any clues).

When I shutdown, here is what I get:

"wait-for-state stop/waiting
Enabling radios: wifi
Applying power save settings...[166.3242127] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x140101 action 0x6
...

I notice it is trying to activate wifi, which is strange, since I don't even have it enabled. Although I have a wifi card.
this seems to be similar to others on the thread, albeit with a different specific hold up.

Help appreciated.

---

### Post by Fausto_Paiva on 2015-02-04
It's happening in a 14.04.1 Dell PowerEdge T310 server managed by me. If I boot system hangs after "Stopping System V runlevel compatibility" message. No error is displayed in console. I discovered that if I disconnect all 3 network interfaces cables it boots normally. Seems something related to NIC initialization. After system boots and I connect the cables network works. Oddly it happens too when I try to reboot. The same message appears. I tried several solutions but nothing works. Everything is updated.
'

---

### Post by raguspag on 2015-03-04
Is there a fix yet? happened when I installed March 3 2015 kernel. 
Linux ubuntu-x 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I get the following errors:

    Stopping System V runlevel compatibility
    Stopping CPU interupts balancing daemon
  
Ofcourse I can startx once I open up a terminal, but it sure is slow.

---

### Post by sleif on 2015-03-05
Same problem on my system (Ubuntu 14.04.1 LTS) - reboot stops after:  * Stopping System V runlevel compatibility * rpcbind terminating on signal. Restart with "rpcbind -w"

---

