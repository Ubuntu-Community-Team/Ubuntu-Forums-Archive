---
title: "ntp.conf help needed!"
date: 2008-07-29
forum: Server Platforms
---

### Post by ruipedroca on 2008-07-29
Hi,

I'm running an ubuntu 8.04 server (not actually the server version, but instead the desktop version) running vmware server 1.0.6 with a Fedora 7 virtual machine.
I need some help configuring the ntp.conf files for both the host and the guest.

Here's the host (ubuntu 8.04) ntp.conf (ip 192.168.10.9):
restrict 192.168.10.0 mask 255.255.255.0 nomodify notrap
restrict 127.0.0.1
[note: the ubuntu uses the motherboard clock and this is fine for now]

Here's the guest (Fedora 7) ntp.conf (ip 192.168.10.7):
driftfile /var/lib/ntp/drift
broadcastdelay 0.008
restrict 127.0.0.1
server 192.168.10.9
restrict 192.168.10.9 mask 255.255.255.0 nomodify notrap noquery



Regards,

---

### Post by ruipedroca on 2008-07-30
It's strange, but I've went to old backups searching for the ntp.conf files from a previous host (kubuntu 7.10) and guests (fedora 7) and followed some notes I've had written but it doesn't work.

However, the only differences between that last configuration and this is the host (kubuntu 7.10 to ubuntu 8.04) and the processor (intel 420 @ 1.6ghz  in the past and now e6550 dual core 2 @ 2.33ghz) and after some googling, I've found an article mentioning that the use of dual core 2 processors might be an obstacle to time configuration between hosts and guests, be it through vmware tools or even ntp.

So, I've disabled the ntpd and created a ntpdate cron job to run every minute (in 60 host seconds the guests run 68...).


Hope it's useful for somebody!

---

### Post by ruipedroca on 2008-08-05
Just to post feedback!

The problem and the solution are in this tread:
[http://ubuntuforums.org/showthread.php?t=876961](http://ubuntuforums.org/showthread.php?t=876961)

---

