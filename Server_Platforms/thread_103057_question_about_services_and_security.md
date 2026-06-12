---
title: "question about services and security"
date: 2005-12-13
forum: Server Platforms
---

### Post by nephish on 2005-12-13
Hey there, 
i run an arch linux server. i am very tempted to move to ubuntu 5.10 with it because i loaded it on my wifes desktop and everything just worked. It found everything ! 
i need my server to be a secure server, but i also need to use it for some office productivity and just regular desktop stuff too, so i would not install the server version, but the regular gnome-destop version on the cd that i have. 
i have read that the server version has no services enabled at startup and install. This is to make it more secure as a server. Is this also true with the desktop version ?

and the sudo thing, i dont know that much about it, but is the sudo thing as secure as having a root user?

thanks for any tips about this. What attracts me to this flavor of linux is how stable it seems to be, and how everything just seems to work. 

any takers?
thanks

---

### Post by 23meg on 2005-12-13
There isn't a separate server version, to begin with, and any version of Ubuntu has no open ports by default.

> and the sudo thing, i dont know that much about it, but is the sudo thing as secure as having a root user?Short answer: yes. Long answer depends on your working methods and what you mean by secure.

For more, see [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by cactus on 2005-12-13
hi nepish..
I still prefer archlinux as my server os, but I don't really require a gui/desktop on any of my servers (not part of my usage scenarios) so your needs are likely quite different than mine.

As far as security, and securing your "server", I would venture to say that archlinux is by default more secure.. because it is more minimalistic, and has by default hosts.deny set to all (tcp_wrappers). I would also say, that it is an easy matter to make ubuntu secure, so the argument is more or less moot.

:) 
Good luck.

---

### Post by nephish on 2005-12-13
Well, i wouldn't normally be thinking of changing over. I like the tinkerability and striped down sleekness of arch. Not to mention the performance. However, i have to reformat my machine anyway to re-arrange the partitions set up to make more room available for my web stuff.
so....
in light of how easy it is to maintain, upgrade and how well it all works together, i was thinking ubuntu, that and the fact that it is a really smooth desktop. Security was just a focus of concern before i reallly decided to switch over...  So thanks for your tips and info. Really.

man, i still dont know what to do here, they are both great distros on the opposite ends of the spectrum, really. pacman and apt are about the same ( as far as what i do with them )
and anything i would need to do in ubuntu, i could eventually figgure out how to do in arch.

wow. thanks

---

