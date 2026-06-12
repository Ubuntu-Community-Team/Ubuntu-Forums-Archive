---
title: "Something connected to my router..."
date: 2009-03-01
forum: Security
---

### Post by gjoellee on 2009-03-01
I was changing some settings in my router when I discovered a device which didn't have a IP adress like this: 10.0.0.x, but it has 8x.xx.xx.x

The device name is by default called: Unknown-xx-xx-xx-xx-xx-xx (x=a number or letter). The IP is the same as my own, but with 2 numbers less. Can it by some other person hacking my ROUTER or is it just my self?

I have had some problems with hackers in about a year ago, but I changed the password got a new router since then. It might be the same guy, or can this be some kind of virus? Because I use Arch Linux, by sister uses Xandros, but everone else uses Wndows!
[U]
I notice this as well:[/U]
-Slow Internet sometimes (every day)
-Sometimes the router just restart, when the Internet is slow then suddenly the Ethernet sometimes stop working sometimes and wireless still work

---

### Post by abn91c on 2009-03-01
if you had the router reset to admin/manufacturers settings during the changes,someone "snifing" for wifi can get in, also if a laptop with intergrated wireless in within range can connnect also. Try mac adress filetering and alow only the PC's in your house, make sure you use WPA or higher ecryption.
Change passwords :-)
change the router channel, if yours by default is channel 6, that its the same frequency of as some of the newer cordless phones, change to 7 or some other channel

---

### Post by howefield on 2009-03-01
> **gjoellee said:**
> The device name is by default called: Unknown-xx-xx-xx-xx-xx-xx (x=a number or letter). The IP is the same as my own, but with 2 numbers less. Can it by some other person hacking my ROUTER or is it just my self?

How does "xx-xx-xx-xx-xx-xx" compare with the MAC address of your network card ?

---

### Post by night_fox on 2009-03-01
Its easy to block this guy. Mac filtering or change password. Dont use WEP encryption as it's easy to hack.

Firstly (dont really do this it's a joke) use wireshark to intercept some of his packets and find out who he is from it. See if he has a windows share, copy everything from it, then, install windows on an old computer, get as many viruses as possible and hope they transmit themselves onto his machine

---

