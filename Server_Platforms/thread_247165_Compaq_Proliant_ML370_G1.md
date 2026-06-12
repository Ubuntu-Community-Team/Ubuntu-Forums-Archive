---
title: "Compaq Proliant ML370 G1"
date: 2006-08-30
forum: Server Platforms
---

### Post by miltiad on 2006-08-30
Hi,

I just installed Ubuntu Dapper (server version) on a Compaq Proliant ML370 (first generation). I'm using the lastest 686 SMP kernel from Ubuntu repositories.

When I press num lock, caps lock or scroll lock the computer freeze  and I have to hold the power button to shut it down.

And that's not all ! When I try to reboot (sudo reboot) it or power it down (shutdown -h now) it freeze too :-? 

I have tried to install the lastest 2.4 686 SMP kernel from the Ubuntu's repositories but I can't boot on it. This kernel is just unable to mount the root filesystem for some reasons.

I have tried another Linux distrib with 2.6.x kernel and I got the same problem. I have tried Redhat 9 wich have a 2.4 series kernel and it work fine.

Anyone could help me on this problem plz ? :)

---

### Post by magicfab on 2006-09-18
Hi there,

I am attempting to use Ubuntu (Dapper or Eft) on the same system as you.

I found out by trial and error that only the Alternate ISO images would let me install, when using the " Instal a server" option.

Once I had a server (bare-bones) system installed, I could install the linux-686 meta-package and both processors were up without problems.

I haven' t experienced the lock-up problems you' re describing, though.

Now I am looking for a way to make the HPASM drivers work so I can turn the loud fans lower... The script for Debian Sarge are here:
[http://debian.catsanddogs.com](http://debian.catsanddogs.com)

However I can't get them to work, although they seem to install OK. When I try to launch hpasm I get a error:
exec: 1: 10: not found

I' ll post under another topic about this, but if you have any info on how to turn the fan down, let me know ;)

---

