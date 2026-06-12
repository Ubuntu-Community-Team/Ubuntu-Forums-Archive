---
title: "looking for a minimalist linux distro for cli word processing"
date: 2009-11-16
forum: The Cafe
---

### Post by pythonscript on 2009-11-16
Does anyone know of a minimal linux distribution that I can use for *only* command line text editing? I'll be using vi as my editor, but I'm looking for something that
a) I can install in under 200 MB of space
b) will absolutely *maximize* the battery life of my laptop (see signature for specs)
c) I can install a tiny app on that will tell me the percentage of my battery left
d) can run something like htop
e) has a small app that will tell me the current system time (2:45 pm, etc, in a format kind of like that). 

I don't need internet access, advanced graphics driver, x server, etc. Pretty much the only programs I'm going to run are vi, htop, and whatever program I find for battery life. I don't want to use ubuntu for this, just because even a command line only ubuntu is still way more bloated than I need. 

Right now, I get about two hours of battery life out of my laptop when I'm running ubuntu with gnome, but I'd love to have something that I can use for basic text editing that will give me at least 4 (since it's not using really any of my processor/memory/graphics). 

Thanks for reading the long question, and thanks for the help!

---

### Post by The Real Dave on 2009-11-16
Try a CLI install of [DSL]("www.damnsmalllinux.org"), [MicroCore]("www.tinycorelinux.com") or [Puppy Linux]("www.puppylinux.org").

MicroCore is CLI, though its 10Mb brother TinyCore has a GUI. 
Puppy is 100Mb, but would scream on your laptop, like overkill power. Its got plenty of apps, and you can probably strip it down if you like. 
DSL is my personal favourite, 50Mb, will run with 16Mb of RAM, it'll be stupid fast on your laptop :D

---

### Post by pythonscript on 2009-11-16
> **The Real Dave said:**
> Try a CLI install of [DSL]("http://www.damnsmalllinux.org"), [MicroCore]("http://www.tinycorelinux.com") or [Puppy Linux]("http://www.puppylinux.org").

MicroCore is CLI, though its 10Mb brother TinyCore has a GUI. 
Puppy is 100Mb, but would scream on your laptop, like overkill power. Its got plenty of apps, and you can probably strip it down if you like. 
DSL is my personal favourite, 50Mb, will run with 16Mb of RAM, it'll be stupid fast on your laptop :D

Would these give me the kind of battery life I'm looking for, too? That's mostly what I'm looking for, because I travel quite a bit, but don't feel like spending money on a netbook when I already have a perfectly functioning laptop.

---

### Post by earthpigg on 2009-11-16
> **pythonscript said:**
> Would these give me the kind of battery life I'm looking for, too?

i think one significant thing you could do for that is underclock your CPU on whatever distribution you end up choosing.

for example:
[http://wiki.archlinux.org/index.php/Cpufrequtils](http://wiki.archlinux.org/index.php/Cpufrequtils)

you will need to 'translate' that to apply to whichever distribution you choose.

i keep mine at 1.67 ghz.

---

### Post by Simian Man on 2009-11-16
Arch would be a good choice as it's designed to start as a command line system.  You can just do the minimal install and then install whatever packages you want on top of that eg vim, latex etc.  You would only need the first few pages of the beginner's guide.

If you already know a distro well, you can install most anything as a base command line system.  From that you may need to, for example turn off daemons you don't need or maybe compile a custom kernel.

BTW, that is a beast of a laptop.

---

### Post by pythonscript on 2009-11-16
> **earthpigg said:**
> i think one significant thing you could do for that is underclock your CPU on whatever distribution you end up choosing.

for example:
[http://wiki.archlinux.org/index.php/Cpufrequtils](http://wiki.archlinux.org/index.php/Cpufrequtils)

you will need to 'translate' that to apply to whichever distribution you choose.

i keep mine at 1.67 ghz.

That's probably my best bet, yeah. I use Arch now on my laptop for the sake of obtaining bleeding-edge software before it's available in Ubuntu, so maybe I'll see it I can strip it down even more to fit in under 200 MB which is the only space I have right now on my laptop hard drive that's not taken up by other partitions, which I don't want to change)

> **Simian Man said:**
> 

BTW, that is a beast of a laptop.

Because of the aforementioned amount of traveling that I do, my production machine has to be a laptop, so I made a pretty significant investment on it (1400 USD from the states about 1.5 years ago) and so far, I haven't been disappointed. Not that I don't love the Athlon 2000+ desktop sitting in my flat; its just not conducive to international flight.

---

### Post by The Real Dave on 2009-11-17
> **pythonscript said:**
> Would these give me the kind of battery life I'm looking for, too? That's mostly what I'm looking for, because I travel quite a bit, but don't feel like spending money on a netbook when I already have a perfectly functioning laptop.

Well, their so lightweight, on your hardware, they would be using like 2-3% of your CPU average like, so ya, they should give good battery life. But look into underclocking too if your h/w supports it. DSL will happily run on 200Mhz if you can underclock that much :)

---

### Post by Warpnow on 2009-11-17
If you install your OS onto a usb thumbdrive you can power down the hard drive and save power.

Also, your files and OS will be together, to work on whatever computer you want, and with CLI you won't see the lag of a gui that comes from slower write times. It will speed along fine. I did this for a while using tty linux. Its iso is only like 5mbs, but I only used that because my thumb drive was so small. If I were doing it now, I'd use something like Debian on a bigger thumb drive. I literally was working with like 32mbs then.

---

### Post by LowSky on 2009-11-17
you wont get 4 hours no matter what GUI or CLI, wont happen.

Buy the extended (12cell) battery and you will probably double your usable time

And just use Arch Linux without a GUI, if you already know it then you will be fine

---

### Post by phrizek on 2009-11-17
In my experience, the distro I use makes little to no difference with regards to battery life. Power management is terrible under linux. I have an Asus UL80vt which get about 10 hours of battery life with Windows 7. With Ubuntu, I am lucky if I get 5-6 hours. I've tried lighter distros like DSL with the same results. YMMV, but I think the state of power management under linux is just crappy at the moment.

---

### Post by phrizek on 2009-11-17
Just took a look around brainstorm and found this: [http://brainstorm.ubuntu.com/idea/81/](http://brainstorm.ubuntu.com/idea/81/)

They claim to be working on the issue, but its been a while since that has been proposed. Hopefully we'll see better battery life with 10.04.

---

### Post by pythonscript on 2009-11-17
I really like the feel of TinyCore Linux, but is this something I can install on the hard drive? I don't want to be booting from the hard drive every time. I'm going to do more research into underclocking my CPU (ubuntu lets me go to 800 Mhz, but if I can go lower that's preferable) and post what I find here, if anyone's interested.

---

### Post by openuniverse on 2009-11-17
.

---

### Post by matthew.ball on 2009-11-17
You can add a custom "layout" to Screen, for instance, mine shows me a list of currently available windows on the left side, and the date and system time on the right side - I'm guessing for a full CLI system you'd be using Screen already, just modify the ~/.screenrc file.

I have found emacs + auctex make for a good word processing combination.

---

### Post by K.Mandla on 2009-11-17
+1 for Arch, and take a look at Wordgrinder if you are interested in word processor beyond vi.

---

### Post by pythonscript on 2010-01-02
Thanks for all the help; I've found that tiny core has a great wiki with a lot of helpful information. Thank you again for the help!

For the sake of reference:
[http://wiki.tinycorelinux.com/tiki-index.php](http://wiki.tinycorelinux.com/tiki-index.php)

---

