---
title: "RT Kernel install/uninstall"
date: 2009-06-06
forum: Ubuntu Studio
---

### Post by dawiba on 2009-06-06
I've downloaded the 64 Studio rt kernel 2.6.29-1-multimedia-686_2.6.29-9_i386.deb and the same for the headers.

My question is this. If I install, am I right in thinking that this will simply give me the option to choose this kernel when I'm booting up?

Also, if I find it doesn't work, how would I uninstall this kernel?

I should say, that after my mini rant against UbuntuStudio last week, I've since done a clean install of 9.04 then upgraded to US and so far everything I've tried works like a charm (with some help from others here!). Patience is a virtue right enough.

I've downloaded this other kernel because I've seen in another thread that someone else is using it and reckons things are running much better, so curiosity is getting the better of me!

Thanks

---

### Post by logos34 on 2009-06-06
yeah, it'll just add the -rt kernel image to menu.lst (sudo update-grub), where you can choose which one you want boot.  If it doesn't work out and you decide you want to entirely remove it from your system, use synaptic to reverse what you did (linux-image- and linux-headers-2.6.29-rt).  You can also just leave them in /boot (they don't take up too much room) and remove just the entries from menu.lst

I use x64 8.04 studio.  The -rt kernel speeds things up (especially noticeable on a fresh install, but less so over time, it seems, as crap accumulates). 

hope that helps

---

### Post by dawiba on 2009-06-06
Oh well...

It doesn't work - the screen is just a mess.

I can't see it in Synaptic either to remove it, so I'll just have to make sure to choose the right kernel when I turn on the computer.

Thanks anyway.

---

### Post by dawiba on 2009-06-06
Following the advice I found in another thread, I've commented out that new kernel as it was loading that one when I switched the computer on. It now boots fine.

With that in mind, am I right in thinking that the order in which the kernels appear in grub is the order in which the computer will try to load them? On mine, the regular kernel comes before the rt kernel. So if I left it to do it's own thing, would it boot into the normal kernel?

I realise this might not really belong in this forum, so I'll ask no more after this about kernels!

Thanks

---

### Post by raboofje on 2009-06-07
> **dawiba said:**
> am I right in thinking that the order in which the kernels appear in grub is the order in which the computer will try to load them? On mine, the regular kernel comes before the rt kernel. So if I left it to do it's own thing, would it boot into the normal kernel?

Your /boot/grub/menu.lst probably has a 'default 0' entry, which tells grub to boot the first kernel by default.

(it also has a 'timeout' option, where you can specify how many seconds grub will allow you to choose a different kernel before booting the default one)

---

