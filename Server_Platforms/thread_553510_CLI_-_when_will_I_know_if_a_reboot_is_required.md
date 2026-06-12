---
title: "CLI - when will I know if a reboot is required?"
date: 2007-09-17
forum: Server Platforms
---

### Post by bone2006 on 2007-09-17
I've been trying to keep the server updated and I'm new to just running the system with no gui.  

Well I ran a sudo apt-get upgrade, which produced these two packages now being installed

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Therefore after searching somebody said to just do the sudo apt-get install package for each package that didn't get installed.  It looks like the kernal is going to be updated and if I remember correctly when I had the gui I was warned to do a reboot.  Will there be any warning or how will I see a waning in a GUI?

I did one install and after it's done I tried doing an update and upgrade and it's not telling me I have any packages to install.  Do I need to reboot or how would I know?

when I do a uname -a it returns
2.6.20-15-server

which I thought the latest was 2.6.20.16, so is a reboot required?

---

### Post by p_quarles on 2007-09-17
To use the new kernel, yes, you need to reboot:
```
sudo shutdown -r now
```
On a server installation, though, APT holds back the minor kernel upgrades (as I understand it) because 1) they're not that useful to a system running minimal hardware/peripherals, and 2) servers are better off maintaining uptime and hard drive space rather than being bleeding-edge.

---

### Post by bodhi.zazen on 2007-09-17
Reboot is required for a new kernel or new hardware, at least as far as I know.

Thre may be a way to start a kernel without rebooting, but I do not know how ...

Other then that, you can restart services :

sudo /etc/init.d/<service> restart

---

### Post by bone2006 on 2007-09-17
I'll do a reboot, but even without doing a reboot it wouldn't effect anything right?  So I can just reboot when I get around to it?

The only time linux ever requires a reboot is kernel updates?

---

### Post by p_quarles on 2007-09-17
> **bone2006 said:**
> I'll do a reboot, but even without doing a reboot it wouldn't effect anything right?  So I can just reboot when I get around to it?

The only time linux ever requires a reboot is kernel updates?
Kernel updates and system crashes. That's about it. :)

(Hardware installation, too, but please don't do that while the system is running).

---

### Post by Brazen on 2007-09-18
Yeah a kernel update is the only update that needs a reboot.  And Yes, it doesn't affect anything if you wait to do the reboot.  I've had servers go through several kernel updates without a reboot, just because it kept running fine so there was no need for the downtime.

Also, I'm surprised no one has said this yet, but the way to get kernel updates is with "sudo apt-get dist-upgrade".

---

### Post by tgalati4 on 2007-09-18
One issue to be aware of:

If you do a bunch of updates at once and then don't reboot in 6 months, you could run into a problem.  For instance if there is an update that breaks one of your services (say CUPS for printing--it breaks frequently with updates), you won't know what is causing the problem.

It's tempting to update often, but then you should reboot after each group of updates to make sure everything is working.  Otherwise, you will be scratching your head 6 months from now why something is broken because of a reboot that now runs a new kernel that was updated 6 months ago.

---

### Post by bodhi.zazen on 2007-09-18
Well, if you are running a server that can not tolerate a reboot, I would do only security updates. Otherwise, contrary to my sig, if it is not broken, don't fix it.

Outside of security updates, only update if it brings a featrue you need.

---

### Post by bone2006 on 2007-09-19
I was under the impression that some kernel updates are security updates.  I guess it was from reading about the virsus in Linux and how all of them are theory and if any virsus in the past did work the kernel update fixed them.  Is this wrong?

---

### Post by tgalati4 on 2007-09-19
Most of the security updates deal with services (daemons) that run on top of the kernel.  The kernel deals with hardware interaction.  It's the daemons that are providing the useful server functions, but also some are susceptible to viruses if they are exposed to the internet.  The updates patch these vulnerabilities.  The risk is low for most of these vulnerabilities under Linux.

Kernel updates are needed to support new hardware.  So, if you are running a machine that is already working, it's doubtful that a kernel update will improve performance.  If you bought a brand-new server, and you can't see your Uber-RAID drives, then you might be interested in a kernel update.

There are lots of tutorials in these forums on security.  Log files to check, scripts to run, configurations to lock down.  These techniques are more important than updates.  Linux is a networked operating system in the first place.  It's open by design.  It requires some effort to lock it down.  

The updates tend to fix obsure vulnerabilities.  These are low risk compared to basic security measures such as a firewall and strong passwords.

---

### Post by bone2006 on 2007-09-19
thanks so much for all the information, good stuff

---

