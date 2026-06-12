---
title: "CyberPower PowerPanel UPS daemon error"
date: 2011-11-13
forum: Server Platforms
---

### Post by Joe Curtis on 2011-11-13
I am using Ubuntu Server 10.04.3 with Linux kernel 2.6.32-35-generic   with CyberPower's PowerPanel version 1.2.  Currently using a serial cable with a CP1500AVRLCD UPS unit.  I installed the i386 .deb   package, but every time I try to use pwrstat, it keeps coming back as   "Daemon service is not found."  Executing as root does not fix the problem, and when trying to inquiry the daemon, I keep getting segmentation faults.  However, top and init.d claim the service is already running!
```
joe@server:~$ pwrstat -status
Daemon service is not found.
joe@server:~$ pwrstatd start
Segmentation fault
joe@server:~$ pwrstatd stop
Segmentation fault
joe@server:~$ pwrstatd restart
Segmentation fault
joe@server:~$ sudo /etc/init.d/pwrstatd start
 * Starting pwrstatd 1.2                                                                             /usr/sbin/pwrstatd already running.
                                                                                              [fail]
joe@server:~$

```Did I install the .deb package wrong?  (I just sudo dpkg -i powerpanel_1.2_i386.deb  it)
How can I fix this?  :confused:  I would rather use the manufacturer's driver/program, but should I use NUT instead, and if so, how?

---

### Post by Entilza on 2011-11-14
Your installation is fine, you using the correct 32 or 64 bit version?

Is this for a single PC connected to the UPS, because you would have to use the agent version / with client to control multiple PC shutdowns.  Because this agent software was so bloated with their linux version, I ended up using APCUSPD and it worked perfectly.

---

### Post by Joe Curtis on 2011-11-15
Thanks for the reply :)

I am using the 32-bit version (i386) since my system is 32-bit.  I only have one small server connected to the UPS, using the pwrstat agent installed.  I think I may have forgotten to use sudo when calling the agent previously, since it works after I rebooted.  Trying to stop/reload/start the daemon directly however, just messes the whole thing up.  It won't do anything, and when I then try calling the regular pwrstat, it says the process is not running.  Thankfully it loads at startup automatically (without me configuring an init script manually).

I have tried some configuration, but the agent seems a bit limited.  Is APCUSPD difficult to set up?  (I am not quite an advanced user as yet.)  I am wondering if I should change over to something with more features?

---

### Post by Entilza on 2011-11-15
The pwrstat utility is for a single computer connected to the ups, if that's all you need you are ok.

Cyber power just recently released the linux version of their agent software.  Previously it would run just as a client so you would need a windows pc running as the host connected to the UPS.  I still found their software too resource intensive, it's all java/web based and seemed to be a memory hog.  I prefered apcupsd since it was so compact.  

Apcupsd is very easy to setup, you just have to take your time.

---

### Post by Joe Curtis on 2011-11-16
Thanks for all the info!  I will definitely check out apcupsd and see if I am missing anything.  For now, the Linux agent works ok for me (at least, it appears to...)  and doesn't seem to take up too much ram/cpu resources.

---

### Post by uh-huh on 2012-01-25
> **Entilza said:**
> 

Apcupsd is very easy to setup, you just have to take your time.

Is apcupsd on some special repo or something? Whenever I try I get this:

```
cordyceps@gnubu:~$ sudo apt-get install apcupsd
[sudo] password for cordyceps: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apcupsd
cordyceps@gnubu:~$ 
```

Cant find it in Synaptic either.

---

### Post by CharlesA on 2012-01-25
> **uh-huh said:**
> Is apcupsd on some special repo or something? Whenever I try I get this:

```
cordyceps@gnubu:~$ sudo apt-get install apcupsd
[sudo] password for cordyceps: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apcupsd
cordyceps@gnubu:~$ 
```

Cant find it in Synaptic either.
It should be in the default repos. It was in there in 10.04 and it looks like it is in the [Universe repo for 11.10]("https://launchpad.net/ubuntu/oneiric/amd64/apcupsd").

---

### Post by Joe Curtis on 2012-01-31
try this:
```
aptitude search apcupsd
```
You may have put limits on your universe repositories, or inadvertently uninstalled them.

---

