---
title: "Running Mac OS 9.x under Kubuntu"
date: 2024-03-24
forum: Virtualisation
---

### Post by Tom_ZeCat on 2024-03-24
I wish to run Mac OS 9.x under Kubuntu 22.04.  I ran Mac System 7 under Kubuntu some years back.  It's probably been 6 to 8 years since I did that.  I did it via some online instructions that said to use a utility known as SheepShaver.  Online search results would indicate that SheepShaver, or possibly something I've never used called QEMU, could be the way to go for OS 9.x.  I already run Windows 7, Windows 2000, and regular Ubuntu under VirtualBox, but the online sources would indicate that trying it that way is quite the nightmare.  

I have 9.04 from a broken Mac that I used to use in the 90s.  I'm pretty clueless on what I might do to restore that old machine.  Plus, if I could run OS 9 under Kubuntu, I would have access to old Mac applications alongside my Linux ones.  I still have my install CDs.  

It would seem like SheepShaver is the way to go, though most of the online info is about running it under Windows or Mac OS X.  However, it is known to run under Linux.  I've done it myself (to run Mac System 7), but it's been a very long time.  I found a deb install file for it, but it was very old, and it did not work.  I found a Snap installer for it ([https://snapcraft.io/install/sheepshaver/ubuntu](https://snapcraft.io/install/sheepshaver/ubuntu)), but I couldn't get that to work either.  It says it installed, but it established no run icon in the GUI, and when I try to run it from the command line, I get this: 

> AppImages require FUSE to run. 
You might still be able to extract the contents of this AppImage 
if you run it with the --appimage-extract option. 
See [https://github.com/AppImage/AppImageKit/wiki/FUSE](https://github.com/AppImage/AppImageKit/wiki/FUSE) 
for more information

AppImage?  I thought I was installing from the command line.  

So it would appear my next step is to install this Fuse thing, which I've never heard of.  I won't install it unless I know it's safe.  Is it?  

My other thought was to get SheepShaver's source code and compile it myself.  However, it's been ages since I compiled any application, and I've never done so for Linux.  From about 1998 to 2006, I used to program in Microsoft Visual BASIC 6.  That was an all-in-one package that included the IDE/debugger and the compiler.  That compiled only for Windows.  I would therefore have a learning curve to get through if I start compiling stuff for Linux, especially since they'll be languages I don't know and code that I did not write.  

Or maybe this Fuse thing is perfectly okay to install.  Is it safe?  Or maybe I would be better off checking out QEMU?

---

### Post by #&amp;thj^% on 2024-03-24
I love and prefer KVM/QEMU for my VM's but that's just me.

And Fuse this might help: "Description     : A library that makes it possible to implement a filesystem in a userspace program."

More here: URL             : [https://github.com/libfuse/libfuse](https://github.com/libfuse/libfuse)

---

### Post by MAFoElffen on 2024-03-24
+1 on KVM

Attached is a screenshot of Ubuntu 22.04.4 with OSX catalina running as a KVM VM...

---

### Post by Tom_ZeCat on 2024-03-24
> **MAFoElffen said:**
> +1 on KVM

Attached is a screenshot of Ubuntu 22.04.4 with OSX catalina running as a KVM VM...

Very nice, but will Mac OS 9.x run with that?

---

