---
title: "Hack my own secure wireless network"
date: 2009-12-06
forum: Security
---

### Post by gigaforce1111 on 2009-12-06
Hi all,
I hope this is the right place for this issue.
I want to learn about the security of wireless networks and try hacking my own.
The thing is, as far as I know, my wireless card / driver is not supporting such operation.
I just want your wise advise / confirmation.

I'm trying to hack a WEP secured network because I read it easier.
My card is:
```
sudo lspci -nn |grep Network
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```The commands that I ran:
```
user@user-laptop:~$ sudo airmon-ng stop wlan0


Interface   Chipset      Driver

wlan0      Unknown       wl (monitor mode disabled)

user@user-laptop:~$ sudo ifconfig wlan0 down
user@user-laptop:~$ sudo macchanger --mac 00:11:22:33:44:55 wlan0
Current MAC: **:**:**:**:**:** (unknown)
ERROR: Can't change MAC: interface up or not permission: Too many open files in system
user@user-laptop:~$ sudo airmon-ng start wlan0


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID   Name
981   NetworkManager
982   avahi-daemon
984   avahi-daemon
1235   wpa_supplicant


Interface   Chipset      Driver

wlan0      Unknown       wl (monitor mode enabled)

user@user-laptop:~$ sudo airodump-ng wlan0
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.
```I added **  above to hide my MAC address.
Please reply!

---

### Post by koenn on 2009-12-06
if you want to learn to hack anything, first learn to
a/ read, understand, interpret error messages and other feedback from programs you run
B/ ask good questions. 
There isn't even a question in your post.

---

### Post by gigaforce1111 on 2009-12-06
> **koenn said:**
> if you want to learn to hack anything, first learn to
a/ read, understand, interpret error messages and other feedback from programs you run
B/ ask good questions. 
There isn't even a question in your post.
First, If you read my post you could see that I asked for opinion on the wireless card.
Second, I wrote the errors I got in order to help others come to conclusion that I didn't come regarding my request.
Third, I sense a little insulting approach in your reply. Of course I tried googling my errors and reading beyond.
I've already **_[read]("http://ubuntuforums.org/showthread.php?t=528276")_** about the methods and asking for guidance on whether my assumption was correct. Maybe you're NOT the guy I should ask.

---

### Post by mikewhatever on 2009-12-07
I really don't think this is a legitimate request. We aren't a cracker's forum, but let the mods decide.

---

### Post by teward on 2009-12-07
I mod a tech support forum (not this one), and that forum's policy is any questions regarding hacking in any form are to be instantly locked, deleted, and the poster is to be banned.  I'm not a mod here (be glad I'm not), but you should be glad I don't hit the "report" button getting their attention.  Seriously, I can do it, and without regrets.

---

### Post by gigaforce1111 on 2009-12-07
Hi all,
My intention in this thread was educational only. 
I did ask for your help in order to see if an outside person could hack into my WEP wireless network, and then I'll have to change to a new WPA/2 router.
I think that someone has hacked into my wireless network.
I understand that it has an illegal side, even thou there is a well detailed thread on this forum: [http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)
Due to all said I'll try find answers elsewhere.
Thanks for all the (none) help. ;)

---

### Post by User0123 on 2009-12-07
> **TrekCaptainUSA said:**
> I mod a tech support forum (not this one), and that forum's policy is any questions regarding hacking in any form are to be instantly locked, deleted, and the poster is to be banned.  I'm not a mod here (be glad I'm not), but you should be glad I don't hit the "report" button getting their attention.  Seriously, I can do it, and without regrets.

o w0w bro.

---

### Post by __p1n__ on 2009-12-07
> **User0123 said:**
> o w0w bro.

Lol - I agree.

To the OP: all wifi is vulnerable - even WPA2.  The only relevant question is how long does it take to crack which in turn maps out to number of captured packets and processing power.

If you want some real security then you need to run a VPN tunnel from the wifi client through to a firewall/vpn server on the far side of your wifi ap.  Appropriate packages for this function are available for ubuntu.

---

### Post by lisati on 2009-12-07
Two issues present themselves to me in the original post, one of a technical nature, and the other of what busniess you might have hacking into a network.

---

### Post by JBAlaska on 2009-12-07
The Broadcom chip-set is notoriously ill suited for monitor mode and packet injection.

If you intend to use [aircrack-ng](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=eeaa6c2af4c84110e77c70fea43449ea) That link shows compatible wifi adapters.

If you search these forums I'm sure I saw a member had written a very nice front-end for aircrack that basically automates the process of **security penetration testing**. Which I believe the OP intends to do with his **own** network.

As far as "Hacking" a WEP protected connection, anyone who uses one in this day and age might as well have a open system, as once packet injection is achieved it takes just a matter of seconds to retrieve the key.

---

### Post by __p1n__ on 2009-12-07
> **TrekCaptainUSA said:**
> I mod a tech support forum (not this one), and that forum's policy is any questions regarding hacking in any form are to be instantly locked, deleted, and the poster is to be banned.  I'm not a mod here (be glad I'm not), but you should be glad I don't hit the "report" button getting their attention.  Seriously, I can do it, and without regrets.

This is a security forum so discussions relating to hacking are on-point inasmuch as they relate to ubuntu configuration and administration.  No one is going to post a blackhat/kiddie how-to however.

I am pretty confident in suggesting that your other forum's mod policies have exactly zero relevance or even interest here so with respect I find your post extremely off-topic.  If you'd like to discuss policy with the mods you may care to contact either cariboo907 or bodhi.zazen.

---

