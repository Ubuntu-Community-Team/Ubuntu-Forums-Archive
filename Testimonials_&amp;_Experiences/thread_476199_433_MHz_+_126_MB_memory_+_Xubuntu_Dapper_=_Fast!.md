---
title: "433 MHz + 126 MB memory + Xubuntu Dapper = Fast!"
date: 2007-06-17
forum: Testimonials &amp; Experiences
---

### Post by DarkN00b on 2007-06-17
So my brother's old HP desktop with Windows ME died after 8 or 9 years of good use. Windows finally had so many errors that it could no longer boot. He asked me if I could reinstall ME for him. I no longer have the install CD, so I asked him if he would be interested in trying Xubuntu. He agreed and I installed Xubuntu Dapper. 

So now here I am with an old Pentium 433 MHz computer with 128 megs of ram that runs almost as fast as my 2 gigahertz - 512 meg desktop. The difference is unbelievable. All I need to do is get his _old_ ATI card working and he'll be set up with a modern OS.

My brother thanks the Ubuntu community for the rejuvenation of his old machine.

[img]http://www.themanandhischeese.pwp.blueyonder.co.uk/mariorock2.gif[/img]

EDIT: Thread title should read 12[b8[/b] megs ram. :)

---

### Post by Geekkit on 2007-06-17
Great to hear. Hah, and I love that Mario animated GIF, that's funny.

---

### Post by kerry_s on 2007-06-17
You should try debian-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

It would really smoke with a custom install of just what you need. I use debian+fluxbox on a vaio pcg-f430 450mhz 256ram and it flies.

net installer-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

at the selection stage just uncheck everything to get a base install.

apt-get install xorg gdm synaptic fluxbox emelfm mousepad dillo

reboot(ctrl+alt+delete)

select fluxbox in the session menu<important

login

open synaptic and get what ever else you want.

emelfm=filemanager
mousepad=editor
dillo=fast web browser

---

### Post by zheepeez on 2007-06-17
There's an old IBM 64MB computer sitting around my house... I should try it with Xubuntu sometime... When the Windows 98 installation on it died, my parents asked me to install XP on it....

They've got a laptop now.

---

### Post by DarkN00b on 2007-06-17
I worked on this machine some more today and noticed that the I.S.A. sound card wasn't detected. Its just an old Sound Blaster 16 card. I have no idea why it wasn't autodetected or how to get it working right now.

Also If I could find an ATI driver that'll drive the old Rage 128 card that would be great too. :D

---

### Post by kerry_s on 2007-06-18
> **DarkN00b said:**
> I worked on this machine some more today and noticed that the I.S.A. sound card wasn't detected. Its just an old Sound Blaster 16 card. I have no idea why it wasn't autodetected or how to get it working right now.

Also If I could find an ATI driver that'll drive the old Rage 128 card that would be great too. :D

That's why you should try debian, ubuntu butchers the kernel to make generic, it also drops alot of older system drivers. Plus it's just plain faster.

that sound card should still be supported by alsa, in terminal run> sudo alsaconf

i don't know about the ati.

---

### Post by DarkN00b on 2007-06-18
I tried it. Alsaconf does not exist on that machine. Alsa is installed though.

I may try debian. :???:

---

### Post by MattDTownsend on 2007-06-19
You probably need to use isapnp and pnpdump to get the card working.  I remember doing this in ye olden days of yore (pre-PCI for everything).

Disclaimer:  the following might make your machine projectile vomit, catch aflame, or grow legs and run away.  Don't blame me if it does, 'cause I just gave warning.

Ubuntu no longer makes, so far as I can tell, any packages for isapnptools.  Which kind of makes sense, since the current demand right now is, well, one.  Two if you count my testing it.  Nonetheless, debian, in all of its crusty glory, does have an old package available:

Open a terminal and run the following commands:

wget debian.oregonstate.edu/debian/pool/main/i/isapnptools/isapnptools_1.26-5_i386.deb
sudo dpkg -i isapnptools_1.26-5_i386.deb
sudo pnpdump

It'll talk about scanning cards.  Whether it is doing it or just faking, I can't tell you, as this package is older than the hills.  If it doesn't work, you'll see it go through lots of # Trying ports and then get the message "# No boards found."  If it does report a found board, don't jump for joy, as this is only step one.

If you pass step one, then we'll see if it's still possible to do step two.  If you decide to go to step two on your own, be careful before you change any config files or boot scripts, as you might cement your machine into a VFS PANIC on every boot.

Cheers,
MT

---

### Post by DarkN00b on 2007-06-19
I had actually found isapnptools and installed it, I just didn't have time Sunday to figure out how to use it.. The problem is that I can only work on this machine on the weekends because of its location. I can't bring it to my home because my brother is using it and **loves** it even though it has no sound or 3D acceleration. I'll get to work on it again Saturday.

---

### Post by MattDTownsend on 2007-06-20
As I recall, you have to point pnpdump to a file, like pnpdump > /etc/isapnp.conf
I believe this is the default location.

The package contains an initscript in init.d, so it may read the file on the next boot, and then you're sitting pretty.

If not, you may have to call isapnp /etc/isapnp.conf in a bootscript like rc.local

Of course, this is only useful if pnpdump turns up a card.

Regarding access, is the machine online?  Thought about using ssh?

---

### Post by DarkN00b on 2007-06-20
> **MattDTownsend said:**
> As I recall, you have to point pnpdump to a file, like pnpdump > /etc/isapnp.conf
I believe this is the default location.

The package contains an initscript in init.d, so it may read the file on the next boot, and then you're sitting pretty.

If not, you may have to call isapnp /etc/isapnp.conf in a bootscript like rc.local

Of course, this is only useful if pnpdump turns up a card.

Regarding access, is the machine online?  Thought about using ssh?

Nah, it would need to be moved about 50 yards down to my sister's house to be on line. I would have to go do this personally. I should be able to get it working this weekend, what with the help I'm getting here. Y'all have pointed me in the right direction. Thanks.

---

