---
title: "Server amd64 install stuck at 40% - Configuring APT"
date: 2012-05-20
forum: Server Platforms
---

### Post by TheFu on 2012-05-20
Trying to install Ubuntu Server 12.04 amd64 on a physical server. I'm a long time 8.04 and 10.04 server installer and user - primarily a CLI user.

Validated the optical media - it checks as fine.

**Stuck**
Install seemed fine for the first few minutes - normally this would take 20 minutes at the most for the complete install and reboot, but it has been stuck at 40% - Configuring APT - for the last 2-3 hours.  This is before the first reboot. Stuck isn't really correct - the count of files is changing .... very ....  slowly.

**Networking**
I opened another console and verified networking using ifconfig - it seems fine (DHCP address) and google pinged quickly.  

**All Ubuntu Internet Servers Slow Today**?
Today everything related to Ubuntu servers on the internet seems to be slow. Not my internal servers, just the Canonical-run-servers. The ubuntuforums.org servers took about 5 minutes to load this page - actually, data is still being transfered as I type now. The page hasn't fully loaded yet.

I did not ask for remote patches or management during the installation.
Asked for 20G to be used for LVM, not the entire disk. According to "fdisk -l", that worked correctly.

**Hardware**
This machine has been running ESXi for a few years, so it has pretty standard hardware with VT-x support. The only thing funny is a 4 yr old nVidia Quadro FX GPU. With a text/cli-only interface, that shouldn't matter at all.  It has a Core2Duo Extreme CPU, GigE NIC, 8G RAM and a 500G SATA HDD. Normal stuff.

Help!  What can I do to avoid the network dependencies during install to get up and testing?  Is there an alternate install option?

---

### Post by Cheesemill on 2012-05-20
Try disconnecting from the network before attempting the installation. If all goes OK you can set up your network afterwards.

---

### Post by TheFu on 2012-05-21
I left the install running for another hour (went to lunch) and it had finished when I returned.  Unplugging during install does seem like a good idea, but a few things might not be auto-configured like TZ and keyboards. 

Everything seems faster today at least with this site, so perhaps it was just all the weekend DIY people hitting the Ubuntu servers hard.

---

### Post by outspoken on 2012-05-27
I'm getting the same thing and finding it quite troubling for a so-called production ready LTS installer from what is widely considered the largest install base distro.

---

### Post by TheFu on 2012-05-27
I did another install into a VM and had the same issue the next time, though it was only 40 minutes total.   Installing 10.04 was 20 minutes total, so there's something in the "Configuring APT" processing that *ain't quite right.*

---

### Post by outspoken on 2012-05-29
After a few more tries and using different install discs (daily server iso, full dvd, etc) I decided to run a diagnostics on my hardware. Turns out the memory was bad. Replaced that and the install went smooth without issue.

---

### Post by TheFu on 2012-06-16
I've determined that the issue is a network configuration problem.  To the machine, there is a network, but it couldn't route to the internet.  APT was confused by that for entirely too long - ENTIRELY.

The problem becomes worst in a VM environment.  virt-manager assumes a network and starts the VM+installation.  Questions related to networking come after this APT config effort - too late.

I can see where this is an odd configuration, but we aren't allowed to put servers on the network before they are hardened and ready for production.  We're just starting to try this new release out - seems we have much to learn.

Would having an internal APT-repository work?  Would it be recognized by a stock installer?

---

### Post by koenpunt on 2012-09-14
I was installing 12.04 in VMWare Fusion and it was almost stalled at configuring APT. After a while I disabled my automatic proxy configuration (.pac) in System Preferences, i chose 'cancel' once and it went on smoothly.

---

