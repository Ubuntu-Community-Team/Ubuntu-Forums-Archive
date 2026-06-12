---
title: "network install"
date: 2004-12-17
forum: The Cafe
---

### Post by ubuntu_demon on 2004-12-17
Hi,

I couldn't find anything about this.

Is there going to be a network install for Ubuntu ? A lot of servers don't have a cd-rom drive (especially home servers).

---

### Post by budyong on 2004-12-17
yup, my CD-ROM also broken..... i can't install ubuntu ! hope there will be a network installation

---

### Post by ubuntu_demon on 2004-12-21
I mean a tiny Ubuntu  netinst image that fits on floppy.

I know I can do this with debian and after that upgrade to ubuntu but a friend of mine wants an easy way to install ubuntu and he hasn't got a cd-rom drive)

---

### Post by ubuntu_demon on 2004-12-21
<demon666_nl> hi
<demon666_nl> are you working on a netinst floppy image ?
<Kamion> in which project?
<Kamion> assuming you mean Debian, no; why did you think I might be?
<demon666_nl> in ubuntu. A guess by bob2
<demon666_nl> Do you know if there will be a netinst floppy image for ubuntu
in the future ?
<Kamion> only if I can get the 2.6 kernel to fit on a floppy, which I
currently can't
<Kamion> that's kind of a total showstopper
<demon666_nl> too bad. How big is the image currently ?
<demon666_nl> Are you working on trying to compress it more ?
<demon666_nl> Maybe a customized debian bootfloppy with the ubuntu
installation taking over at some point is a possibility ?
<Kamion> Debian doesn't have 2.6 floppies either
<Kamion> no, not an option, sorry
<Kamion> I don't have current figures
<demon666_nl> I friend of mine wants to run Ubuntu on a server with no
cd-rom attached. What would you advise ?
<Kamion> it's already compressed about as far as it'll go; the only option
seems to be taking stuff out of the kernel
<Kamion> netboot
<Kamion> it's in the installation manual
<demon666_nl> thnx
<demon666_nl> but he does need a second pc with debian/ubuntu installed for
that ?
<Kamion> any Unix should do
<Kamion> USB stick is also a possibility in Hoary
<demon666_nl> USB is the easiest way to go then 
<demon666_nl> thnx
<demon666_nl> bye!
<Kamion> note that much of the documentation is accidentally missing from the current installation manual build, fixing that now
<demon666_nl> :)
<demon666_nl> can i publish this on ubuntuforums ? 
<Kamion> publish what?
<demon666_nl> this chat
<demon666_nl> I know at least one other person who wants to know this :)
<Kamion> sure
<demon666_nl> ok thnx I'll leave you alone then :)
 



Installation from USB : Images available, need polishing

[http://www.ubuntulinux.org/wiki/HoaryGoals](http://www.ubuntulinux.org/wiki/HoaryGoals)

---

### Post by skrat on 2005-04-11
I would appriciate existence of some sort of netinst image like one in debian (aprox 110MB) which fits on USB key. The fact is that my laptop doesen't have CDROM but it can boot from USB key. I am currently using Debian but would really like to try Ubuntu on that. I don't really feel like setting up my own PXE install to install only one laptop. So there would be really helpful to have minimum ISO image, which can be booted from USB key and would include only base system. Than user can choose what to install further on. For example he can choose to turn his system to server, Ubuntu, Kubuntu or something completely different :)

---

### Post by totalshredder on 2005-04-11
I don't understand this; why can't there be one floppy disk that loads some programs into RAM, then you put, say, three more in, each with a piece of the kernel on it. Then the program you loaded at first puts them all together. Why is this not possible?

Luke

---

### Post by CRCampbell on 2005-04-11
[QUOTE=demon666_nl]I mean a tiny Ubuntu  netinst image that fits on floppy.

I know I can do this with debian and after that upgrade to ubuntu but a friend of mine wants an easy way to install ubuntu and he hasn't got a cd-rom drive)[/QUOTE]

Why not just go to the store and buy a cheap CD-ROM drive?

---

### Post by kassetra on 2005-04-11
[QUOTE=CRCampbell]Why not just go to the store and buy a cheap CD-ROM drive?[/QUOTE]

That is not an option for some users.

---

### Post by jobezone on 2005-04-11
[QUOTE=totalshredder]I don't understand this; why can't there be one floppy disk that loads some programs into RAM, then you put, say, three more in, each with a piece of the kernel on it. Then the program you loaded at first puts them all together. Why is this not possible?

Luke[/QUOTE]
 Yeah, I've installed Debian this way, with 3 floppy disks, first booted, 2nd for kernel, 3rd for drivers. It would then download the install system from the net. I did this a year ago. But hey, there are so many people working in Cannonical, and maybe this isn't such a priority of theirs.

---

