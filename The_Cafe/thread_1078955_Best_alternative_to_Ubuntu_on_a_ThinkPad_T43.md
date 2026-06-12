---
title: "Best alternative to Ubuntu on a ThinkPad T43?"
date: 2009-02-23
forum: The Cafe
---

### Post by 50words on 2009-02-23
I waited a while to upgrade to 8.10. It has been pretty flaky for me, so I am thinking about giving something else a try until 9.04 comes out.

I am not very interested in spending a lot of time configuring a distro from the command line, so I am looking for a distro with a level of polish similar to that of Ubuntu. I also need to install VirtualBox, Skype, and Dropbox, and would rather not install from source.

OpenSuse and Fedora seem like the best alternatives. Dropbox only has a binary for Ubuntu and Fedora, but installing one of three from source isn't too bad, if I go with OpenSuse.

Is there anything else I should look at? Which would you install?

---

### Post by konqueror7 on 2009-02-23
try linuxmint, its literally the polished version of ubuntu and its also based on ubuntu, only difference is that it comes with the restricted extras already, out-of-the-box experience so to speak, but not all...:p

---

### Post by 50words on 2009-02-23
> **konqueror7 said:**
> try linuxmint

I can't imagine another Ubuntu-based distro is going to work any better than the one I am using now.

---

### Post by konqueror7 on 2009-02-23
ah,,,so you want something different from ubuntu...

i've tried fedora, and its good, not much difference with ubuntu, only the package management is different...

as for openSuse, in my opinion its better than fedora, very organized, great for starters and regular users alike...

you can also try mandriva...

---

### Post by Miguel on 2009-02-23
You may want to give Debian Stable a go, now that it's been just released. Software versions are mostly like in Intrepid except Gnome, which is in Hardy's 2.22 without gvfs.

Why would you want to install Debian? Works in a similar way to Ubuntu, so you'll feel at home with synaptic/aptitude/runlevels and most of the working philosophy of the system. Stable has many bugs squashed and you can opt between the expert ncurses install to the graphical installed. In any case, if you have a fast connection I'd use netinstall. Furthermore, a T43 is not bleeding edge hardware, so support will be fine in 2.6.26 kernel included in Lenny.

---

### Post by 50words on 2009-03-01
I decided to give Fedora a try, since I can install all three apps without compiling anything. The install went very smooth, and so far, it is running rock solid.

In some respects, Fedora feels a bit more polished than Ubuntu. The GUI installer made setting up an encrypted disk a piece of cake, for example. The last time I did that in Ubuntu, it required the text-based alternate install disc. And when starting up, I get a graphical prompt to enter my LVM password, instead of the messy, text-based prompt in 8.10 (which is really messy and way worse than 8.04, for some reason). The LVM management is also outstanding.

Sudo works a bit differently, and I needed to make some changes to Nautilus so that the file browser shows up the way I like. But those changes were easy. Adding the MS core fonts was not so easy, however, and there is nothing like the Ubuntu restricted packages. I had to install Flash by downloading the .rpm file from Adobe's website.

Still, overall, a very easy transition.

Hopefully this will tide me over until 9.04 comes out. I may fall for Fedora in the meantime, but compared with Ubuntu, Fedora does not seem to have nearly the community support. Every time I try to Google something for Fedora, I get Ubuntu articles and forum posts.

---

