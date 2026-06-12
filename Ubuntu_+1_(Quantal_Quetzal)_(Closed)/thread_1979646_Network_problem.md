---
title: "Network problem"
date: 2012-05-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cecilpierce on 2012-05-13
When I reboot theres no network connection until I unclick "Enable Networking" and wait till it says disconnected, then click it again and it starts up.
Anyone else have this problem or what could be wrong ?

---

### Post by ronacc on 2012-05-13
had that for awhile several cycles back , haven't seen it recently , check you network settings and make sure the one you want ( if you have more than one ) is set to connect at boot .

---

### Post by cecilpierce on 2012-05-13
Its checked in "Startup Applications" so Im lost !

---

### Post by ronacc on 2012-05-13
I never did find out what the problem was when I had it a few cycles back it just fixed itself as things progressed .

---

### Post by cecilpierce on 2012-05-13
> **ronacc said:**
> I never did find out what the problem was when I had it a few cycles back it just fixed itself as things progressed .

Thanks for the reply, I'll wait and see what happens.

---

### Post by cariboo on 2012-05-13
Is Networking actually disabled, or is Network-manager just indicating that it is. I had the same problem several versions back, it was eventually fixed via updates.

---

### Post by cecilpierce on 2012-05-14
Enable Networking is checked in the top icon but no connection at startup, have to un-click and re-click to get connected ???

---

### Post by cecilpierce on 2012-05-14
Just noticed the weather forecast comes up on boot and the router light flashes alot but firefox is dead until I restart networking, buggin the heck out of me.
:mad:

---

### Post by ronacc on 2012-05-14
try another browser , I suggest chrome or Opera ( note opera is not in the repos the deb direct from Opera woks fine ) .

---

### Post by roelforg on 2012-05-14
Do you have some sort of hw-switch (laptops usually have, or gaming kbd's or whatever)?
If it's set to off, network-manager might be defaulting to that setting.

---

### Post by dino99 on 2012-05-14
on my side i've dropped NM since a while, too many headaches, and installed wicd.

---

### Post by zika on 2012-05-14
> **cecilpierce said:**
> Just noticed the weather forecast comes up on boot and the router light flashes alot but firefox is dead until I restart networking, buggin the heck out of me.
:mad:Do try in Terminal (ping or similar to see if network is working...) before restart-ing NM's net just to be sure where the problem lies, in FF or in NM, or elsewhere...
> **dino99 said:**
> on my side i've dropped NM since a while, too many headaches, and installed wicd.As far as I can see OP is using WiredConnection so NM could be completely by-passed ...
It is not difficult to edit several files and have network without NM even being awaken from a deep sleep...

---

### Post by cecilpierce on 2012-05-14
> **dino99 said:**
> on my side i've dropped NM since a while, too many headaches, and installed wicd.

Installed wicd and it seems to be working fine.

Thanks for the help.

---

### Post by arpanaut on 2012-05-14
That's not a solution, just a workaround...
I have this problem on my PP fallback install,
started late in dev cycle.

Funny that I have quite a few other installs of LL, NN, OO, PP and QQ,
without this problem, I would like to find a solution for a "stock" install
But, that's just me.

---

### Post by cecilpierce on 2012-05-14
> **arpanaut said:**
> That's not a solution, just a workaround...
I have this problem on my PP fallback install,
started late in dev cycle.

Funny that I have quite a few other installs of LL, NN, OO, PP and QQ,
without this problem, I would like to find a solution for a "stock" install
But, that's just me.

I agree with you but it was getting to be such a pain in the ars I had to try it, it was happening on PP and one of my QQ's.
I flop around from one to another alot    ):P

I guess the developers never restart there computers !

---

### Post by cariboo on 2012-05-14
I know not having a working network connection can be a big pain, but doing a bit of troubleshooting before using a work-around, would have been nice.

We are here to test and report bugs, by installing a different network manager, you sort of bypass that process.

Just for documentation purposes, it would be nice if anyone else runs into the problem, that they post the output of the following commands, if it seems that networking isn't working:

```
ifconfig
```

This command allows use to see if an ip address has been obtained.

```
ping www.google.com
```

This command will allow us to see if DNS is working properly, if the above command doesn't work then try:

```
ping 74.125.127.147
```

If this command works, then it points to DNS not working properly. With this information, a bug can be filed with the proper information against network-manager

---

### Post by cecilpierce on 2012-05-15
@cariboo907

Thanks, I try those and see what happens.

---

### Post by dino99 on 2012-05-15
note that the newest resolvconf seems to help a bit with NM, get less "cant resolve url" errors.

I'm having trouble with NM only with one PC having a sky2 chipset, other PC does not have issue as such.

---

### Post by cariboo on 2012-05-15
My problem is that when my system is first started DNS works the way it should, but after a couple of hours, I get "can't resolve urls" messages too. This is on two systems using the same Nvidia based motherboard. The network adapter on these motherboards are bridge devices, and not an actual networking chip. I believe VinDSL, ran into the same sort of thing. I resolved my problem by setting a static ip address and entering the DNS addresses I use in Network-manager.

Other systems I have using dynamic ip addresses don't have the problem.

---

### Post by cecilpierce on 2012-05-15
This is 12.04, happens in one 12.10 and one other 12.10 works fine ?

---

### Post by VinDSL on 2012-05-16
> **cariboo907 said:**
> The network adapter on these motherboards are bridge devices, and not an actual networking chip. I believe VinDSL, ran into the same sort of thing.
Correctamundo! 

Evidently, they dropped support for my pseudo, southbridge-driven, onboard (e.g. fake) LAN device.  

I solved all my NM problem(s) by installing a real NIC, with the venerable DEC Tulip chipset (i.e. something "they" can't drop support for, because there are still too many of these chipsets being used in enterprise hardware).  ;)

---

