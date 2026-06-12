---
title: "Building an HTPC/NAS/VPN/Gateway"
date: 2010-02-28
forum: Server Platforms
---

### Post by tertius on 2010-02-28
I want all of those in one.  I'm pretty ok working with linux but I need some help to be pushed in the right direction.

What would be the best way to go for a build like this?

I already have the hardware.  Here is essentially what I'd like to do.

1. Use the computer as an HTPC with an HDMI cable, maybe use Boxee?
2. Have the computer set up as a NAS server (that will be accessed locally and "locally" when connected as a VPN.  I'll back this up daily online (difference) and want to give my family access (via VPN) to backup).
3. VPN connectable with a gateway: I.e. I want to go to starbucks, VPN to my home server to have an encrypted conection and then also being on my home local network.

I'd like to base this all in an Ubuntu installation which I'm pretty comfortable with.

Thanks for any help!  Feel free to point me to articles.  And yes, I have searched. :)

Thanks!

---

### Post by tertius on 2010-02-28
Bump.

Changing the flavour to all.

---

### Post by tixetsal on 2010-03-25
I'm looking for info on a problem with the Boxee web interface and stumbled on this post somehow.  

You need a MOBO (or vid card) with HDMI, which you must already have.  Beware if you are planning on piping your sound through the HDMI though, as I have had problems with HDMI video + Ubuntu in general, but unresolvable issues with HDMI audio specifically, on 2 different chipsets.  YMMV.

Just serve samba shares to meet your NAS scenario.  You can access samba shares on linux, mac, and win boxes easily.

It sounds like you are describing a bridged (not routed) VPN scenario when you mention the VPN and gateway.  I would encourage you to continue to use router as your gateway, and run OpenVPN to meet your VPN needs.  Configuring a gateway involves some pretty tricky iptables wizardry (among other things).

You can find great tutorials on samba and openvpn below.  HTH.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

You could do a poor man's VPN if you become comfortable enough with SSH.

---

