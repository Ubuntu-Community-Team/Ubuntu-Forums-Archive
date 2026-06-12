---
title: "security question"
date: 2007-11-06
forum: Server Platforms
---

### Post by il coatto on 2007-11-06
hi everybody.

i would like to ask if is it save to post the output of this command " ifconfig -a " a guy ask for it for help me out find a solution of a problem but i don't know if it save to do it , maybe contain some personal information .  thanks for the eventual help

---

### Post by MJN on 2007-11-06
The only bit of info that some consider sensitive is your IP address - this uniquely identifies your connection to the Internet.
 
My opinion is that there's no point keeping this secret - if you're vulnerable then you'll get caught out simply due to the number of automated scanners out there looking for unpatched software, weak password SSH logins etc.
 
Furthermore, in a lot of cases the full ifconfig output is being asked for because it is pertinent to the problem you're discussing so withholding some info can hamper the diagnosis.
 
If you are connecting to the Internet via a router then chances are your ifconfig output will be showing a private (e.g. 192.168.*, 10.*) address anyway as opposed to your 'real' public address so there really is no need to hide it.
 
There's no real right or wrong - I'm sure others will see things from a different, and perhaps equally logical, perspective.
 
Mathew
 
P.S. My sig contains the URL of my website which I run at home - all someone has to do is run a DNS query against the name and they'll know my IP address anyway. Of course, this just reflects my situation and the fact that I see no harm in people knowing my address.
 
P.P.S. All this assumes you're not asking a question along the lines of 'My SSH server seems to be accepting logins without a password being required, whats wrong?' in which case posting your IP address is likely to be an open invitation to anyone to come along a cause mischief...!

---

### Post by il coatto on 2007-11-06
thank u very much .. been helpfull .... all the best to u ...ciao

---

### Post by stmurray on 2007-11-06
The other bit of info given by ifconfig is the MAC address (sometimes called the hardware address).  That number is readily available to anyone on your local network (lan), but not to anyone else (although Microsoft OSes will leak it to remote machines).  The only security risk of giving someone your MAC address is that sometimes it is can be used as authentication mechanism to attach to a wireless network.  That is, you can set your wireless access point to only allow certain MAC addresses to attach to it.  (This is very limited security-- you really must use (WPA or WPA2) encryption and shared secrets (keys) to limit folks from connecting your WAP).  So, if you have a wireless access point that doesn't use WPA or WPA2, and only uses MAC filtering to keep people from attaching to it, then giving out your MAC address would be a bad idea

---

