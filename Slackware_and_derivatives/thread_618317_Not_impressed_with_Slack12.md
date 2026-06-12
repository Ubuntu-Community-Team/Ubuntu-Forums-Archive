---
title: "Not impressed with Slack12"
date: 2007-11-20
forum: Slackware and derivatives
---

### Post by shane2peru on 2007-11-20
Ok, I installed Slackware 12 about 3 days ago, and still have no internet.  I assume that my eth0 card was not installed properly, or not included with the kernel.  I don't use odd hardware, I use rather standard hardware.  I was able to get Gentoo up and running very well in this amount of time.  They have great documentation and I don't have to wait for help to come to my rescue.  Slackware is lacking that.  Here is my post on LinuxQuestions.  [http://www.linuxquestions.org/questions/linux-networking-3/no-network-600651/](http://www.linuxquestions.org/questions/linux-networking-3/no-network-600651/)  If you can help I will give it a few more days to be fair to Slackware, but if it doesn't get fixed I'm going back to Gentoo.  I would really like to learn Slackware (and hence learn linux). 

Shane

---

### Post by Whiffle on 2007-11-20
For some reason the 'e100' driver is blacklisted in your /etc/modprobe.d/blacklist, but still loading.  Try doing:

```

modprobe -r e100
modprobe eepro100
ifconfig

```

If that fixes it we'll have to see why the wrong one is loading.

---

### Post by shane2peru on 2007-11-20
> **Whiffle said:**
> For some reason the 'e100' driver is blacklisted in your /etc/modprobe.d/blacklist, but still loading.  Try doing:

```

modprobe -r e100
modprobe eepro100
ifconfig

```

If that fixes it we'll have to see why the wrong one is loading.

Ok, I did this by chrooting into my slack partition here are the results:```
 modprobe -r e100
FATAL: Could not load /lib/modules/2.6.22-14-generic/modules.dep: No such file or directory
bash-3.1# modprobe eepro100
FATAL: Could not load /lib/modules/2.6.22-14-generic/modules.dep: No such file or directory
bash-3.1# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:E4:6F:B5  
          inet addr:192.168.0.170  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fee4:6fb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:302416567 (288.4 MiB)  TX bytes:26864874 (25.6 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74657 (72.9 KiB)  TX bytes:74657 (72.9 KiB)

```
The reason I mention that I chrooted, is because it steals the connection from ubuntu and uses it instead of properly loading the stuff.  At least that is what it seems like to me, I could be wrong.
Thanks for the help!

Shane

---

### Post by Whiffle on 2007-11-20
I think chrooting is probably messing things up, which is why it can't find modules.dep  When you chroot, all you're doing is changing root directories, you're not actually booting up slackware, which is what we need to do to figure out whats going wrong.

---

### Post by shane2peru on 2007-11-20
Ok, booted into Slackware, and ran those commands.  Didn't get any errors or anything.  Then ran the ifconfig, and only the lo thing was there.  No eth0.  The reason I do things in chroot, is because I don't know a good way other than paper and pen to get the error messages and the commands from the internet.  If there is a better way, I'm open to suggestions.

Shane

---

### Post by Whiffle on 2007-11-20
save them to a file, and then reboot to ubuntu and post them from there.  Im not sure what to think on your issue though,hmm.

---

### Post by shane2peru on 2007-11-20
> **Whiffle said:**
> save them to a file, and then reboot to ubuntu and post them from there.  Im not sure what to think on your issue though,hmm.

I keep forgetting that I have KDE installed and can boot into that.  I just work straight from the tty shell that comes up to issue a few commands, I have a hard time finding the terminal in KDE.  :)  In Gnome I put it right on the panel so I have easy access to it.  Good idea.  I will have to do that.  Thanks.

Shane

---

### Post by tommcd on 2007-11-21
Shane,
Sorry you are having such a hard time with Slack. Those guys on the LQ forums gave good advice for troubleshooting, better than I could have given.
Have you tried running "lspci -v" and "lsmod" from ubuntu, and then comparing the output of those commands in ubuntu with the output of those same commands in slackware to see what is different for the nic?

---

### Post by shane2peru on 2007-11-22
> **tommcd said:**
> Shane,
Sorry you are having such a hard time with Slack. Those guys on the LQ forums gave good advice for troubleshooting, better than I could have given.
Have you tried running "lspci -v" and "lsmod" from ubuntu, and then comparing the output of those commands in ubuntu with the output of those same commands in slackware to see what is different for the nic?

Hey I got it.  Finally.  Now I can really take a good look at Slack.  Thanks for the help.

Shane

---

