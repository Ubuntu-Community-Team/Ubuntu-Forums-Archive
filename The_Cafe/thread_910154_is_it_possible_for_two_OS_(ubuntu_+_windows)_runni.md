---
title: "is it possible for two OS (ubuntu + windows) running on two monitors seperately?"
date: 2008-09-04
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2008-09-04
for example, if i have a dual-core cpu and dual-monitor, and i have two harddisks, mice and keyboards too, is it possible to install ubuntu on harddisk 1 and windoze on harddisk 2 and then boot them up simultaneously so that two users are able to use them without affecting the others? is it possible to make it work like two "identical" computers -- one for ubuntu and one for windows?

---

### Post by TheSlipstream on 2008-09-04
Only one drive at a time can operate as a Master drive (with the other as a Slave), which means you probably (note my cluelessness) cannot have two running an operating system, but what do I know.

---

### Post by Canis familiaris on 2008-09-04
I think you can Virtualize one of the OS and run the virtualised OS in the other monitor.

Sorry I dunno how to configure for multiple monitors, but it is possible.

---

### Post by quanumphaze on 2008-09-04
Sorry, it's not possible with today's current hardware.

PCs today are designed with a BIOS that loads up an OS by reading the first boot sector it finds on the drives from the set boot order. The BIOS itself is not designed to handle 2 operating systems running concurrently. Things like the motherboard (chipsets, PCI controller etc.) are also not designed for this kind of operation as there will be conflicts between who is controlling the hardware.

The best semi-solution I can give you is to set up a virtual machine where there is a clearly defined host and guest configuration and start a new thread about how to play with the window manager and X to let the second screen, keyboard and mouse control the VM window. I know you can have two users using the same computer with a different set of input and screen. It's the setting up the input devices to control different X sessions that would be a pain to configure.

I doubt that we will ever see hardware that is capable of doing what you are thinking in the near future since it's not exactly easy to design and little demand for it as of now. So you will be pretty much stuck with dual booting if virtualisation doesn't 'scratch your itch'.

---

### Post by afeasfaerw23231233 on 2008-09-04
thanks for your suggestions!

---

### Post by lamenoid on 2008-09-17
[QUOTE=Anurag_panda;5725480]I think you can Virtualize one of the OS and run the virtualised OS in the other monitor.QUOTE]

yes you can do this, using java virtual machine (or any other if you wish) and virtualizing a second OS.  use the OS with smallest footprint as primary.

but to have a comp running to OS's independently is not possible.

---

### Post by JetskiDude911 on 2008-09-17
I wouldn't do this without at least 4GB of RAM, and a dual or quad core CPU. But this is how I would set this up:

1. Install Windows XP as the main operating system. Vista would also be ok too, but I'm going with the least hardware intensive operating system.

2. Setup Windows XP to use dual monitors.

3. Install VMware Server.

4. Setup a virtual machine for Ubuntu. Probably give it one CPU, 1 GB of RAM to start with. 

5. Install Ubuntu from the ISO (faster, easier, doesn't require using a CD).

6. Once Ubuntu is installed, I'd setup the VMware tools in Ubuntu. Then, I would just place the Ubuntu virtual machine over on the second monitor and maximize the screen as much as possible. 

That's how I would do it. It's not a perfect setup, but would work. 

If you had two computers I would recommend setting the two computers up side by side, install the operating systems, then setup Synergy so you could use the same mouse and keyboard for both computers. 

The second setup is the more elegant setup (and less time consuming).

---

### Post by BDNiner on 2008-09-17
but you cannot use 2 keyboards and mice on one computer without a lot of confusion and frustration. so the answer is no. I don't think that there is software that would allow 2 cursors to be operated independently by 2 mice.

---

### Post by olskar on 2008-09-17
> **BDNiner said:**
> but you cannot use 2 keyboards and mice on one computer without a lot of confusion and frustration. so the answer is no. I don't think that there is software that would allow 2 cursors to be operated independently by 2 mice.

MPX? :)

[http://en.wikipedia.org/wiki/MPX](http://en.wikipedia.org/wiki/MPX)

---

### Post by smartboyathome on 2008-09-17
Though what will allow you to use two keyboards? I don't think there is a way to do that without hacking Xorg. :(

---

### Post by pp. on 2008-09-17
> **BDNiner said:**
> but you cannot use 2 keyboards and mice on one computer without a lot of confusion and frustration. so the answer is no. I don't think that there is software that would allow 2 cursors to be operated independently by 2 mice.

Doesn't look too difficult to me, as long as there's one USB keyboard and one USB mouse. Using Virtualbox, it should be possible to attach any USB device to the virtual machine, I think. Read the fine manual.

---

### Post by brnetonboy on 2008-09-17
> **afeasfaerw23231233 said:**
> for example, if i have a dual-core cpu and dual-monitor, and i have two harddisks, mice and keyboards too, is it possible to install ubuntu on harddisk 1 and windoze on harddisk 2 and then boot them up simultaneously so that two users are able to use them without affecting the others? is it possible to make it work like two "identical" computers -- one for ubuntu and one for windows?

There is one way that I can think of. Set up a virtual machine inside of your OS: either Ubuntu inside of Windows or Windows inside of Ubuntu. Then you just hook up a standard dual-monitor setup to your computer and put the virtual machine maximized in one of the monitors.

There wouldn't really be any other way to do it because they would have to share the motherboard, the ram, the processor, etc...  so it's not possible unless they are run through software as virtual machines. 

Regarding multiple mice/keyboards working simultaneously, you can do that with MPX, but nobody on the internet knows how to set it up--or if they do know (like the MPX creator, whom I emailed about this) they won't write a useful tutorial.

---

### Post by RedPandaFox on 2008-09-17
It is easy to do as long as you only used one mouse and keyboard.
What grapics card are you using. 

Also, what I think your trying to build is called "a second computer" :)

---

### Post by statmonkey on 2008-09-19
As I think someone already said.  I do this with virtual box.  Very easy to do and great tutorial on [http://tombuntu.com/index.php/2008/09/08/virtualbox-20-released/]("http://tombuntu.com/index.php/2008/09/08/virtualbox-20-released/") Not sure why you want two keyboards as at this moment I am using XP on one screen and Heron on the other.

If you want the other OS in a separate box try this: [http://tombuntu.com/index.php/2008/09/15/share-one-keyboard-and-mouse-between-multiple-systems/]("http://tombuntu.com/index.php/2008/09/15/share-one-keyboard-and-mouse-between-multiple-systems/")

2 kb's two mice?  Sure, you could set up a virtual box with MSux in Heron and use pin mouse and keyboard plus usb mouse and keyboard.  But, with all due respect.  Why?

---

### Post by binbash on 2008-09-19
I am doing this with 2 gb ram.

Ubuntu Hardy and winxp (virtual).But you cant use 2 cursors,you can use 2 mouses with mpx but only 1 cursor (i am not sure about mpx part )

---

### Post by UbuWu on 2008-09-19
You can setup ubuntu with multiple monitors each using a different keyboard and mouse. The most easy way is probably using [Userful]("http://www2.userful.com/products/downloads/free-2-user").

Such a configuration is called multiseat and if you google for ubuntu multiseat you will find a lot of information although much of it is outdated.

If you get this set up properly you can then run windows in your favorite virtualization solution on one of them.

---

### Post by binbash on 2008-09-19
> **UbuWu said:**
> You can setup ubuntu with multiple monitors each using a different keyboard and mouse. The most easy way is probably using [Userful]("http://www2.userful.com/products/downloads/free-2-user").

Such a configuration is called multiseat and if you google for ubuntu multiseat you will find a lot of information although much of it is outdated.

If you get this set up properly you can then run windows in your favorite virtualization solution on one of them.

I will test it out soon : ) THanks for the link

---

### Post by UbuWu on 2008-09-19
I later saw that the userful software hasn't been updated either in a long time so I doubt it still works in recent ubuntu versions.

---

### Post by smartboyathome on 2008-09-19
Also, look into thin clients. I think they do something similar to what you want (not quite sure though).

---

### Post by brnetonboy on 2008-09-19
> **binbash said:**
> But you cant use 2 cursors,you can use 2 mouses with mpx but only 1 cursor (i am not sure about mpx part )

Acually, MPX does let you use 2 cursors--or as many cursors as you have mice. 

Check out this video of MPX: 
[INDENT][http://www.youtube.com/watch?v=0MUOn_nJmRA]("http://www.youtube.com/watch?v=0MUOn_nJmRA")[/INDENT]

---

### Post by zmjjmz on 2008-09-19
MPX can also have two or more active windows (you need a special WM though), so having two keyboards would be possible.
But yes, at that point you might want a second computer.

---

### Post by UbuWu on 2008-09-19
> **binbash said:**
> I will test it out soon : ) THanks for the link

Ok, I found something very cool for you, this was released only a few hours ago, hot off the press: multiseat display manager. Read about it here:

[http://lists.freedesktop.org/archives/xorg/2008-September/038674.html](http://lists.freedesktop.org/archives/xorg/2008-September/038674.html)

It greatly simplifies setting up a multiseat configuration, and they even provide a live cd (based on Ubuntu) so you can try it out before you decide to install it.

:guitar:

I added a brainstorm idea for packaging and integrating it in Ubuntu here: [http://brainstorm.ubuntu.com/idea/13436/](http://brainstorm.ubuntu.com/idea/13436/)

---

