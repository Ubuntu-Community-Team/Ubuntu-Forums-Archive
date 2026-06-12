---
title: "Thread Repost: Keeps asking for wireless password and doesn't connect!"
date: 2011-01-25
forum: Security
---

### Post by chipppy on 2011-01-25
Good Morning

This is a cross posted thread.  It is from Networking and Wireless forums ([http://ubuntuforums.org/showthread.php?t=1674309]("http://ubuntuforums.org/showthread.php?t=1674309"))

I have cross posted as it is not really a wireless network problem (wireless networking works fine) but a wireless security problem (WEP and WPA security kill wireless networking).  I am not total sure which forums it should be in.

_From original post in networking and wireless forum:_

I am having a heap of issues with wireless and hopefully the following will help someone out there in guru land help me fix this problem.
It seems to be more then a simple computer to wireless security problem. This is long, get a cuppa and a cumfy seat and yes this did take me the better part of 1/2 a day to complete all this testing

I have the following computers
Mythbuntu 10.10 (custom built with 1 wireless adapter)
Main desktop Ubuntu 10.10 (custom built with different wireless adapter)
Emachines netbook ubuntu netbook respin 10.10(different wireless adapter again)
compac laptop window 7 (yet another different wireless adapter)

setup wireless router to no encryption and all 4 machines connect and surf perfectly. great

change wireless router to WAP2 with simple password (1234567890)
Window works great
3 X linux machines dont connect and keep asking for password

Change router to WEP with simple password (1234567890) required 8-32 character password in wireless router.
Windows works great
3 X linux machines dont connect and keep asking for password

Played around with letting linux autowlan connection and then type in passkey. also tried editing connections and entering passkey in there and then try and connect. Every time I tried to connect a linux machine I disconnected and reconnect windows to prove that it was linux machine problem only and not something else.

Tried silly things like putting my keyring password and sudo password in where it asked for passkey instead of the passkey (just in case it was something that simple) Still no luck.

To me it looks like something more then an individual adapter or computer or wireless router brand/model issue.
Reading through the various forums through the web searches that I have done, it looks like wireless security is a little hit and miss still on linux.

I volunteer my various machines and time to try and fault find the issue on all machines to help the developers to fix this problem on mine and I can document everything. Hopefully this will help someone fix wireless security on Linux once and for all.

Just tell me what to do and i will do it.

Cheers
chipppy

---

### Post by chaozuper on 2011-01-26
badabump

---

### Post by bwackwat on 2011-10-20
I have a similar problem.

I have a desktop upstairs running CentOS 6.

It will be using a Belkin n600 Wireless USB adapter as its wireless network card.

It is functioning, is loaded in as wlan0, and can detect all access points.

However, I simply cannot maintain a connection, let alone connect completely.

I can enter a password for the desired access point, but then am repeated asked again.

No connection seems to ever be made.

Is this a DHCP problem? An automatic IP problem?

When I try:
ifcfg wlan0

I am told that I am missing an IP address argument.

Any ideas?

~Bwackwat

---

### Post by lightsaberlesbian on 2013-01-09
did this ever get resolved?

---

### Post by mörgæs on 2013-01-09
The thread is two years old, and a lot has happened in the development of Buntu. The information here is likely to be obsolete.

If you have a problem in 12.10, please open a new thread. Closing this one.

---

