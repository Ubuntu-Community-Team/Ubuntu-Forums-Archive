---
title: "can ubuntu handle dissimilar hardware image deployment?"
date: 2008-05-06
forum: Server Platforms
---

### Post by at0mic on 2008-05-06
Hi,

I was wondering how well ubuntu / linux handles dissimilar hardware. For example imaging a ubuntu server install from one pc and using it with another pc with different hardware specs? Is it ill advised or a reasonable practise?

---

### Post by ephro on 2008-05-06
I've done this quite a few times without too much trouble. The things to watch out for (off the top of my head remembering):


[LIST]
[*]/etc/fstab will be jacked up with UUIDs, so if possible set up your disks the same and change all the UUIDs to the /dev/* equivalents
[*]xorg.conf will be screwed up if the hardware is quite a bit different (since it's server this might not bother you at all)
[*]/etc/modules may be a problem depending on different hardware configs (most times this doesn't matter with server hardware)
[*]/etc/hostname will need to be changed (or things will get very confusing later)
[*]/etc/hosts needs to reflect that change
[*]To make life easier make sure to install your rsa keys in you ~/.ssh directory
[/LIST]
If you do your config in the 'UNIX' way tons of the problems you would hit with Windows aren't a problem.

On a side note most of the servers that I use at work have a HP ILO interface so you can still get a local terminal if you make any mistakes, hopefully you have the same or physical access (CoLos all over the country obviously make this difficult without ILO.)

I hope this gives you a good start. Using the stock linux kernels gives you quite a bit of flexibilty for different hardware.

If you have any specific questions, I can try to help.

---

### Post by songshu on 2008-05-07
i think it can be done with imaging,

but i'm personally trying a different approach in the aim i can have more control over the systems after they are initially set up.

you could offcourse modify the install cd wich is not that hard to do, at the moment i'm using the netboot install cd

it is not properly configured yet, but it is a working setup......almost that is.... because i'm pretty much stuck at the post-chicken configuration at the moment.

you can find my attempt here, it might give an idea you could use
[http://songshu.org/doku/doku.php?id=custom-ubuntu](http://songshu.org/doku/doku.php?id=custom-ubuntu)

---

