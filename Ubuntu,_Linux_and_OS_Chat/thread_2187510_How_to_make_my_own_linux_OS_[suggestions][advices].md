---
title: "How to make my own linux OS [suggestions][advices]"
date: 2013-11-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Tejas_Ghalsasi on 2013-11-12
hello everyone,I am a engineering student ,very much interested in open source development,
i wanna make my own linux distro as a final year project,currently i'm in 3rd year i still have around 6months to actually start development.

i did some research by reading LFS 7.1 PDF and referring to google
but m confused .
i kno c,c++,java,shell scripting in linux,php(it wont be used though).I have covered the basics of OS in our academic subjects pertinent to it.
i am going to use the linux kernel present in ubuntu 12.04 as the default coz my parent os would be ubuntu obviously
the bootloader would be grub-2
the gui would be gnome
apart from that wat else do i need to know before starting the development

any new ideas/suggestions are welcome 
thanks in advance

---

### Post by lykwydchykyn on 2013-11-12
If you just want to make a respin of Ubuntu, you probably don't need to know much more than how to use apt-get and where to download the minimal install iso.  But that's a weekend hobby project, not a final project for university.

There's a lot of things that "Making a distro" can mean, I suppose the first thing you want to do is determine what you mean by this:

- It can mean respinning some parent distro with different default packages, configs, and artwork and giving it a snazzy name (e.g. any number of one-man project around the web)
- It can mean doing the same as above, but adding in a repo of packages not available in the parent distro
- It can mean building the whole stack from source and rolling your own package managment system
- It can mean starting with a base install from some mainstream distro and rolling your own management tools, desktop environment, etc.

The core issue is "what separates your distro from everyone else's?"  If there's some part of the stack that you intend to develop differently than every other distro, you want to focus on that first.  Take a few distros as examples:

- Tinycore:  the defining feature of this distro is that it's tiny and its core runs completely in RAM.  So the authors focused on creating a simple, minimal GNU/Linux stack from scratch with some lightweight package management tools.
- ZorinOS:  the defining features of Zorin all center around the desktop look & feel and tools to manage it.  So the author just took Ubuntu as a base, then developed the unique desktop shell over that.
- Crunchbang:  the focus of crunchbang was to provide "the best possible out-of-the-box Openbox experience".  It's mainly focussed on doing dekstop configuration, so they simply built this on Debian stable as a base.

Does this help?

---

### Post by TheFu on 2013-11-12
Seems like you know more than necessary to get started.
You might want to look at TinyCore to see everything in an OS, but in a more manageable size.  Looking at lots of other special-purpose distros would be useful too - especially when they are smaller.

---

