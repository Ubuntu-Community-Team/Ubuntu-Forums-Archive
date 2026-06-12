---
title: "[SOLVED] Virtualbox Always Freezing"
date: 2008-02-07
forum: Virtualisation
---

### Post by Kristopher on 2008-02-07
When I run Virtual box with a Windows XP VM, and run several programs (one at a time) i.e. Photoshop 7, download manager etc... it always freezes on me. 

Sometimes i move the mouse and its fine, others i need to hold my laptops power button down to restart my whole system.

I tried giving it 1GB of RAM in case it was that but nope? 

I am runing 1.5.0 on Ubuntu 7.10, any ideas what is wrong?

HP Pavilion dv6238ea Notebook PC | Ubuntu 7.10
2 Gb RAM | 120Gb HD | Nvidia Go 7400 256MB | Intel® Core™ Duo CPU T2250 @ 1.73GHz

---

### Post by starfry on 2008-02-07
There's a kernel option you need to set on booting the HOST. Have you done this?
I can't remember of the top of my head what the option it but it is documented in  the vbox user guide. I seem to remember it is something like "no hz"...

**update** what you want is to add "nohz=off" to the end of your "kernel" line in "/boot/grub/menu.lst" Like this:

kernel          /vmlinuz-2.6.20-16-generic root=UUID=db6c0561-048a-4f13-af4a-4aeec22cc819 ro quiet splash nohz=off

---

### Post by Kristopher on 2008-02-08
Thanks WOW such a difference and 100% better cool thank you so much.

---

### Post by Kristopher on 2008-02-21
Ok that fixed that, but when i run Amarok and VB with XP it starts to freeze. Any ideas how to fix this? apart from dont run Amarok at the same time lol

---

### Post by ol3ears on 2008-03-02
I had/have the virtual box freezing problem (gutsy host / xp guest) dual core - 100% cpu utilisation on one core and seems to stop gnome irrespective of VIrtualBox task priority.
No problem on fiesty host / xp guest (suggests a nohz issue?) dual core
I have not done the kernal nohz thing on gutsy instead I bring VirtualBox up on one core
taskset -c 1 /usr/lib/virtualbox/VirtualBox
Seems to do the trick - though would be a bit limiting if you were attempting to run multiple guests

---

### Post by Kristopher on 2008-03-10
I found what the issue was. Within Amarok if i have the send info lastfm that causes the freezes, with this turned off it runs 100% smooth and not one freeze now since my last post here :)

---

### Post by Fire_Chief on 2008-06-25
> **ol3ears said:**
> I had/have the virtual box freezing problem (gutsy host / xp guest) dual core - 100% cpu utilisation on one core and seems to stop gnome irrespective of VIrtualBox task priority.
No problem on fiesty host / xp guest (suggests a nohz issue?) dual core
I have not done the kernal nohz thing on gutsy instead I bring VirtualBox up on one core
taskset -c 1 /usr/lib/virtualbox/VirtualBox
Seems to do the trick - though would be a bit limiting if you were attempting to run multiple guests

Excellent!! This fixed my intermittent freezing issue as well. I had previously done the nohz switch in GRUB but I like this better. Thanks! :guitar:

---

### Post by Anubis on 2009-06-18
nohz=off  does not work for me.

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/347487]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/347487")

[http://www.virtualbox.org/ticket/4179]("http://www.virtualbox.org/ticket/4179")

---

### Post by tapin13 on 2009-07-15
exactly the same problem.
Some one know did they fix it in VirtualBox 3.0.2?

---

### Post by ArielEnter on 2009-11-17
How to solved:
[http://www.ctrlaltgeek.com/category/virtualbox/](http://www.ctrlaltgeek.com/category/virtualbox/)
[http://vbox.innotek.de/pipermail/vbox-users/2008-March/003017.html](http://vbox.innotek.de/pipermail/vbox-users/2008-March/003017.html)

---

### Post by shortstack on 2010-04-27
> **starfry said:**
> There's a kernel option you need to set on booting the HOST. Have you done this?
I can't remember of the top of my head what the option it but it is documented in  the vbox user guide. I seem to remember it is something like "no hz"...

**update** what you want is to add "nohz=off" to the end of your "kernel" line in "/boot/grub/menu.lst" Like this:

kernel          /vmlinuz-2.6.20-16-generic root=UUID=db6c0561-048a-4f13-af4a-4aeec22cc819 ro quiet splash nohz=off


THANK YOU! worked like a charm.

---

