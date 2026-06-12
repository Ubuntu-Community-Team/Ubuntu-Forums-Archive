---
title: "VBox -- no access to DVD burners ?!?"
date: 2008-06-29
forum: Virtualisation
---

### Post by A-dogg on 2008-06-29
I have a sony Vaio with a built-in DVD+-RW drive, as well as an external Pioneer DVD+-RW drive and I can't get Vbox (non-ose) to recognize either of them. It recognizes my built-in as a DVD-ROM.

I have pass-through enabled, but...

Is it just a matter of this not being possible in vbox? It's an XP virtualization, by the way...

I want to use it so I can use Norton Ghost to make a backup of my vbox XP install before I update to Hardy Heron so I can protect myself against losing things I've taken a long time to set up.

Can anyone offer any advice?

---

### Post by b0b138 on 2008-06-30
I'm guessing that you can't. When you hold the mouse over the enable passthrough box, the description at the bottom say writing audio cd inside the vm is not yet supported. 

Also, if I'm understanding you correctly, you don't need norton to backup your vbox xp install. The virtual disk is just a file. If you want, you can just back that up just as you would anything else. It should be located at /home/yourusername/.VirtualBox/VDI

---

