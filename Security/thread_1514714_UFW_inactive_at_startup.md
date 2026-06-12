---
title: "UFW inactive at startup"
date: 2010-06-21
forum: Security
---

### Post by KonfuseKitty on 2010-06-21
I have enabled UFW with default values of Deny for Incoming and Allow for outgoing. However, after every startup, when I run <sudo ufw status>  the reply is 'inactive'. This was on original 10.04 that I installed last week. I did a complete update today, and the behaviour is the same. Am I doing something wrong, do I need to issue a command to make the setting stick?

A related question about the system update: the startup screen now presents the updated kernel as a system I can load, as well as the old kernel. Is this normal? I would have expected the update would have replaced the kernel.

---

### Post by cdenley on 2010-06-21
Post this output
```

grep ^ENABLED /etc/ufw/ufw.conf
sudo service ufw start
sudo ufw status
cat /etc/init/ufw.conf

```

Also, kernels are not removed or replaced when you install a newer version. That way, if the newer kernel breaks something, you can boot to the previous one.

---

### Post by KonfuseKitty on 2010-06-21
Thank you, here it is:

```
lynx@lynx-desktop:~$ sudo ufw status
[sudo] password for lynx: 
Status: inactive
lynx@lynx-desktop:~$ grep ^ENABLED /etc/ufw/ufw.conf
ENABLED=yes
lynx@lynx-desktop:~$ sudo service ufw start
start: Job is already running: ufw
lynx@lynx-desktop:~$ sudo ufw status
Status: inactive
lynx@lynx-desktop:~$ cat /etc/init/ufw.conf
# ufw - Uncomplicated Firewall
#
# The Uncomplicated Firewall is a front-end for iptables, to make managing a
# Netfilter firewall easier.

description    "Uncomplicated firewall"

# Make sure we start before an interface receives traffic
start on (starting network-interface
          or starting network-manager
          or starting networking)

stop on runlevel [!023456]

console output

pre-start exec /lib/ufw/ufw-init start quiet
post-stop exec /lib/ufw/ufw-init stop
lynx@lynx-desktop:~$ 


```Can you make sense of that?

---

### Post by Fatman_UK on 2010-06-24
Sorry if this is a silly question but have you done a

```
$ sudo ufw enable
```

? I think it sets some internal state... it's tripped me before.

---

### Post by KonfuseKitty on 2010-06-24
Yes, of course, Fatman.  I've since reinstalled Ubuntu and the firewall is now active at statup.  I'll be reinstalling once more when I'm done researching and testing things, so hopefully all will be well.  I think what spooked things up for me was that I downloaded two GUIs for ufw and there may have been a conflict.  Now I just use the command line.

---

### Post by bodhi.zazen on 2010-06-24
> **KonfuseKitty said:**
> Yes, of course, Fatman.  I've since reinstalled Ubuntu and the firewall is now active at statup.  I'll be reinstalling once more when I'm done researching and testing things, so hopefully all will be well.  I think what spooked things up for me was that I downloaded two GUIs for ufw and there may have been a conflict.  Now I just use the command line.

That is most likely your problem.

The graphical tools configure itpables and if you install both firestarter and ufw the config files conflict and ufw will not start.

The problem is simply removing firestarter does not solve this as remove does not remove the firestarter config files, you need to purge firestarter.

```
sudo apt-get purge firestarter
```

Of course you may nee dto re-install it before you can purge it, lol.

I reported this bug (firestarter vs ufw) more then a year ago.

---

### Post by KonfuseKitty on 2010-06-24
Interesting info, thank you.  In general terms is the "purge" parameter what I should use to completely get rid of any software?  When I removed Firefox I noticed some files were not removed and deleted them manually.  Would purge have done that for me?

---

### Post by cdenley on 2010-06-24
> **KonfuseKitty said:**
> Interesting info, thank you.  In general terms is the "purge" parameter what I should use to completely get rid of any software?  When I removed Firefox I noticed some files were not removed and deleted them manually.  Would purge have done that for me?

The command to purge a package was already given. A purge should remove all configuration files created when a package was installed. Files which may have been created by the application, such as your firefox profile in your home directory (~/.mozilla/firefox), would not be deleted by removing or purging the package. Also, other related packages such as firefox-branding or firefox-gnome-support sometimes get installed as dependencies.

---

### Post by Vimmander on 2010-06-27
I, too, have noticed this issue in both Ubuntu 10.04 and the sister release of Linux Mint 9 Isadora.  When I restart after doing the following:

     sudo ufw enable
     sudo ufw default deny

And I then do:

     sudo iptables -L

None of the output I see indicates my "default deny" settings.  Upon checking the status of ufw with the appropriate command, it is listed as inactive.  And when I activate ufw, the settings from "default deny" magically reappear.  This happens in both virtual machines and "real" installs on partitions, which I painstakingly set up and tested.  It's quite annoying and very discouraging.  When I read that ufw is enabled on startup, I expect to see that hold true when I use the "sudo ufw status" command, and I also expect to see the "default deny" rules in iptables whenever I do "sudo iptables -L".  It's a simple matter of control:  I want my system to do what I want it to do and what it says it will do, so why does it do neither?

---

### Post by cdenley on 2010-06-28
> **GrogTheDreamer said:**
> I, too, have noticed this issue in both Ubuntu 10.04 and the sister release of Linux Mint 9 Isadora.  When I restart after doing the following:

     sudo ufw enable
     sudo ufw default deny

And I then do:

     sudo iptables -L

None of the output I see indicates my "default deny" settings.  Upon checking the status of ufw with the appropriate command, it is listed as inactive.  And when I activate ufw, the settings from "default deny" magically reappear.  This happens in both virtual machines and "real" installs on partitions, which I painstakingly set up and tested.  It's quite annoying and very discouraging.  When I read that ufw is enabled on startup, I expect to see that hold true when I use the "sudo ufw status" command, and I also expect to see the "default deny" rules in iptables whenever I do "sudo iptables -L".  It's a simple matter of control:  I want my system to do what I want it to do and what it says it will do, so why does it do neither?

Have you ever installed another package which may update iptables? Do your systems have a network connection? I can't seem to reproduce your problem.

---

### Post by Vimmander on 2010-06-28
> **cdenley said:**
> Have you ever installed another package which may update iptables? Do your systems have a network connection? I can't seem to reproduce your problem.

Not that I know of.  All I do is run Update Manager and I installed things like rkhunter, chkroot (?), and the restricted file format packages (including the one for DVD playback).

---

### Post by cdenley on 2010-06-28
It seems to work fine by default. You must have done something to break it. If not, you can file a bug, but you would have to provide steps to reproduce the bug.

---

### Post by Vimmander on 2010-07-12
> **cdenley said:**
> It seems to work fine by default. You must have done something to break it. If not, you can file a bug, but you would have to provide steps to reproduce the bug.

I just enabled ufw in a fresh install of Lucid, and it came right up as active after a full shutdown and restart.  I can't imagine any of my packages messing with it.  All I ever downloaded was the two drivers for my wireless card, Vim, the restricted extras, the DVD reading package, and Pidgin.  Unrelated to the built in FW and ufw, I use a few FF addons like FireBug and TabMix Plus.  Do I just download one package set at a time and restart to see what might have broken it, in any order?

I'd also like to note that this might have occurred in a virtual machine for Lucid, I can't really remember.  If that's when it happened, however, then that's probably it.  VBox is weird about some stuff at times >.>

---

### Post by Vimmander on 2010-07-12
Okay, it seems that none of those installs do anything to ufw, it loads at startup.  Moving on to the massive amount of updates I need to download.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Okay, nothing I do will replicate the problem.  It must have happened in a virtual machine.  My next question is what commands can I enter to restore the output of

iptables -L

to the output it produces before doing

ufw enable
ufw default deny

I'd like to mess around with the settings a bit, since I have adequate protection with my router and the default setting for all ports, which I still find hard to believe, but I can't return the firewall settings to the installation default.

---

### Post by bodhi.zazen on 2010-07-12
> **GrogTheDreamer said:**
> Okay, it seems that none of those installs do anything to ufw, it loads at startup.  Moving on to the massive amount of updates I need to download.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Okay, nothing I do will replicate the problem.  It must have happened in a virtual machine.  My next question is what commands can I enter to restore the output of

iptables -L

to the output it produces before doing

ufw enable
ufw default deny

I'd like to mess around with the settings a bit, since I have adequate protection with my router and the default setting for all ports, which I still find hard to believe, but I can't return the firewall settings to the installation default.

```
sudo ufw disable
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -X
sudo iptables -t nat -X
```

---

### Post by Vimmander on 2010-07-13
> **bodhi.zazen said:**
> ```
sudo ufw disable
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -X
sudo iptables -t nat -X
```

Should I also reset ufw, or do these commands pigyback to it and just reset it?

```
 sudo ufw reset
```

That's something I've done before, but it looks like it just disabled ufw, and made no changes to iptables.

---

### Post by bodhi.zazen on 2010-07-13
> **GrogTheDreamer said:**
> Should I also reset ufw, or do these commands pigyback to it and just reset it?

```
 sudo ufw reset
```That's something I've done before, but it looks like it just disabled ufw, and made no changes to iptables.

ufw reset resets ufw to the default rules.

ufw is a front end for iptables.

When you ```
ufw disable
``` , it deletes all the rules ufw set for iptables, and allows all traffic, but ufw does not clean up the user chains.

See the output of these commands :

```
sudo ufw disable
sudo iptables -L -v -n
```

To clean up all the user chains, you need to use iptables -X , but you can not delete tables unless they are empty, so you need to flush them first.

> root@ufbt:~#iptables -F
root@ufbt:~#iptables -X

root@ufbt:~#iptables -L -v -n
Chain INPUT (policy ACCEPT 111 packets, 8132 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 79 packets, 12460 bytes)
 pkts bytes target     prot opt in     out     source               destination

The final output of iptables -L -v -n , after flushing and deleting the ufw rules are the defaults.

For additional information , see

[http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/ufw.8.html)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

