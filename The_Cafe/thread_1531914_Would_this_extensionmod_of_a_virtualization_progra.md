---
title: "Would this extension/mod of a virtualization program be possible? has it been done?"
date: 2010-07-15
forum: The Cafe
---

### Post by Dustin2128 on 2010-07-15
Maybe other people are different, but I like to swap distros every few months just to get some variation. There are some distros and operating systems I'd like to try, but I don't feel comfortable partitioning my drive seeing as some of the installers are far short of intuitive (freeBSD, gentoo minimal, ect.) so I run them in virtualbox. However, I don't always like virtual machines because they can only have a fraction of the power of my laptop without slowing down the program containing them and thus slowing them down. So, why couldn't you have a virtualization program that takes all or most of the resources of your computer by shutting down all background programs and replacing heavy GUIs like gnome or kde  with an extremely light one like flux. Then it goes fullscreen and has tabs across the bottom with OSes you currently have installed. When you swap from one tab to another, the machine you were on suspends your session to its hard drive file so that you can get all system resources on the one you're working with. Machine swap speed is my only concern as far as speed goes unless you were using a SSD. I have a 'concept art' thing I made with GIMP.
EDIT: I have the picture now.

---

### Post by lykwydchykyn on 2010-07-15
I'm not sure that getting rid of the GUI's and so forth would really help all that much.  It might free up some RAM, but unless your machine is RAM-poor to begin with that probably won't make a huge difference.  Have you tested this with a lightweight window manager (or no window manager) to see if it makes a significant difference?

---

### Post by Dustin2128 on 2010-07-15
> **lykwydchykyn said:**
> I'm not sure that getting rid of the GUI's and so forth would really help all that much.  It might free up some RAM, but unless your machine is RAM-poor to begin with that probably won't make a huge difference.  Have you tested this with a lightweight window manager (or no window manager) to see if it makes a significant difference?
It helps, yes, but what I'm proposing is a program (not written by MS) that can take all of your system resources to work with.

---

### Post by wewantutopia on 2010-07-15
I always thought the same thing would be great, especially full access/use of the video card for the virtual machine.

---

### Post by Lucradia on 2010-07-15
Qemu has a GUI for options and just a simple window to show the guest OS...but it's all run from the command line.

Might want torun fbgui, and no xorg. Xorg is usually the biggest RAM sucker on a linux box. (especially older versions of ubuntu, and depending on hardware.)

---

### Post by undecim on 2010-07-15
All you need for that is a simple OS that loads virtual machines and can save the state of them. You would probably have a very long delay in switching machines as their ram would need to be saved to the hard disk (like a hibernation) before you can allocate all the ram to the other VM.

You can pretty much do this with VirtualBox already. Just save the machine state and start another one.

---

### Post by Dustin2128 on 2010-07-15
> **undecim said:**
> All you need for that is a simple OS that loads virtual machines and can save the state of them. You would probably have a very long delay in switching machines as their ram would need to be saved to the hard disk (like a hibernation) before you can allocate all the ram to the other VM.

You can pretty much do this with VirtualBox already. Just save the machine state and start another one.

Hm, makes me wonder if something simple and light like arch might do the trick. Still, a distro designed for virtualization would be interesting to use if I could find or build one.

---

### Post by juancarlospaco on 2010-07-15
*That already exist, LXC, native speed, the Jail get the real hardware speed...*

---

### Post by 3rdalbum on 2010-07-16
What you're proposing could be coded quite easily to call VirtualBox on the command-line. When the user clicks on a different tab, it runs the command to tell Virtualbox to suspend the current computer, and then restore the new one.

---

### Post by doorknob60 on 2010-07-16
What you need is CPU Virtualization Support (like AMD-V or Intel VT-x). [http://en.wikipedia.org/wiki/X86_virtualization#Hardware_assist](http://en.wikipedia.org/wiki/X86_virtualization#Hardware_assist)

Virtualbox is very very smooth (for regular tasks, it's just as fast about as a native XP installation) on my Desktop with Athlon 64 X2 5200 that has AMD-V, it's so much more sluggish on CPUs without it. Now things like GPU hardware accelleration certainly need some improvement, but I don't think switching from Compiz or Metacity to Openbox would do much, if anything. Also, try out seamless mode in Virtualbox, it's pretty cool :)

EDIT: Just to clarify, I'm not absolutely positive that's what makes the big difference, but I'm pretty sure of it, since on computers with it, it's just as fast as a native install, and on computers without, it's like half the speed of a native install. Makes sense to me.

---

