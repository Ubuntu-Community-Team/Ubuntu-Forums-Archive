---
title: "Kismet issue"
date: 2005-03-26
forum: Server Platforms
---

### Post by trivialpackets on 2005-03-26
When trying to run Kismet, I'm getting the following error message.  Will kismet use my wireless card if I have to get it running with ndiswrapper?  it's a broadcom card in my HP.  My concerns are that this could be the issue, but I'm hoping not.  

ep@freedom:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (ciscosource): Enabling monitor mode for cisco source interface eth0 channel 6...
FATAL: Unable to open cisco control file '/proc/driver/aironet/eth0/Config' 2:No such file or directory
Waiting for server to start before startuing UI...
ep@freedom:~$




Thanks all inadvance for whatever advice you can give.

---

### Post by moopere on 2005-03-27
More network cards are unsupported than supported with kismet as I recall.  Without having a good long read of the docos (/usr/share/doc/kismet) you will have a world of trouble trying to guess how to set up the configuration file.

As I remember, and its been a while for me, kismet won't support binary blob drivers wrapped in ndiswrapper...perhaps this has changed now....in any event, the docs will explicitly tell you which cards/chipsets are supported.

Regards,
Craig

---

### Post by Polymira on 2005-03-29
If you have to use ndiswrapper for yer card, your S.O.L on using kismet with it. 

You see, as kismet requires to put your card into rfmon mode, which is not supported in windows ... and since your using your windows driver ... well .. you get the idea...

What I did was go out and buy a pcmcia card that's supported (a netgear wg511 v2 at circuit city) and i use that for kismet / general sniffing, and my onboard with ndiswrapper for connectivity ... i mean, i can be sitting in a coffee shop sniffin packets while browsing the web, although .. i am sniffing my own as well =/

---

### Post by trivialpackets on 2005-03-30
Thanks, as I suspected.  I'll have to go and do just that then.

---

