---
title: "How small can linux get?"
date: 2009-04-23
forum: The Cafe
---

### Post by jwbrase on 2009-04-23
How small could linux get while still being capable of booting to the command line? Could you boot a bare kernel, or would you need a bit more than that? I'm not asking for existing distros, just the theoretical bare minimum size.

---

### Post by Firestem4 on 2009-04-23
> **jwbrase said:**
> How small could linux get while still being capable of booting to the command line? Could you boot a bare kernel, or would you need a bit more than that? I'm not asking for existing distros, just the theoretical bare minimum size.

no need to be theoretical
[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)   10mb's

---

### Post by sertse on 2009-04-23
I raise that 

[http://basiclinux.com.ru/](http://basiclinux.com.ru/)

3mb.

---

### Post by calrogman on 2009-04-23
> **sertse said:**
> I raise that 

[http://basiclinux.com.ru/](http://basiclinux.com.ru/)

3mb.

And a server hard drive to match. =/

---

### Post by MaxIBoy on 2009-04-23
Less than 1.44 Mb. (There are single-floppy distros.)

---

### Post by swoll1980 on 2009-04-23
You couldn't use just a kernel. you would need some bare minimums in order to interact with it, like a shell, and some basic shell programs. The kernel is just a go between for the application, and the hardware. With out either of these, the kernel is useless. The command line interface is an application, like bash, for example. Bash takes your command inputs, translates them to the kernel, then the kernel tells the hardware what to do. You don't even need an OS. You could write programs that talk directly to the hardware, the problem with this is that it would only work on the one hardware set up that it was designed for.

---

### Post by ghindo on 2009-04-23
Strip out all but the bare necessities, compile your own kernel and see for yourself.

---

### Post by JohnFH on 2009-04-23
Linux can be absolutely tiny.  I once installed Ubuntu on a 2Gb micro SD card!  I needed tweezers and magnifying glasses to handle the thing!

---

### Post by PaulReaver on 2009-04-23
Tiny core rocks. a distro with a usable desktop under 10mb.

---

### Post by jwbrase on 2009-04-23
> **ghindo said:**
> Strip out all but the bare necessities, compile your own kernel and see for yourself.

That's basically what my question was: What are the "bare necessities"?

---

### Post by NightwishFan on 2009-04-23
> **JohnFH said:**
> Linux can be absolutely tiny.  I once installed Ubuntu on a 2Gb micro SD card!  I needed tweezers and magnifying glasses to handle the thing!

:):):):):)

I use Ubuntu as the OS on my Microrobots. They are smaller than a virus.

---

### Post by swoll1980 on 2009-04-23
> **jwbrase said:**
> That's basically what my question was: What are the "bare necessities"?

a shell(like Bash), a text editor(like Nano), for starters. the rest would depend on your needs. Do you need networking? do you need a printer? You would need to know these things before you could decide what the bare necessities are.

---

### Post by wolfen69 on 2009-04-23
> **PaulReaver said:**
> Tiny core rocks. a distro with a usable desktop under 10mb.

i installed it in virtualbox and was amazed by it.

---

### Post by cb951303 on 2009-04-23
basically, for a working system you need
[LIST]
[*]a kernel image
[*]a shell like bash or zsh, korn etc..
[*]some command line tools such as ls, cp etc... [busybox]("http://www.busybox.net/about.html") is a great alternative that covers all your basic needs in one application
[*]a boot manager like grub or lilo
[*]custom scripts to init the system
[/LIST]a kernel image, a shell

edit: you may also need libc but I'm not sure

---

### Post by khelben1979 on 2009-04-23
> **JohnFH said:**
> Linux can be absolutely tiny.  I once installed Ubuntu on a 2Gb micro SD card!  I needed tweezers and magnifying glasses to handle the thing!

2 GB is far more than you need, actually. But I suspect that you already know this. I have been using Linux on the Amiga 10 years ago...

---

### Post by ice60 on 2009-04-23
i tried out basic linux in qemu -

---

### Post by 0per4t0r on 2009-04-23
smaller than the attachment, but at that point it just turns into a dot :D

[spoiler]All it is is a picture of tux scaled down a **lot**.[/spoiler]

---

### Post by unoodles on 2009-04-23
I do believe that this is as small as it gets.
Userland tools were rewritten in assembly language.
About 150 utilities (cat,cp,ls,sh you name it!).
The entire thing compiled is 83kb.

[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

---

### Post by MaxIBoy on 2009-04-23
To get a full Linux system with standard tools, use a 2.4-series kernel, strip out all hardware support except for what you need (this includes removing graphics support for anything more advanced than 80*25 characters,) and use a stripped-down busybox instead of a full busybox or full GNU Coreutils userspace.

Or, you could write everything in assembly like what was linked to above.

EDIT: Seems like a full distro using those assembly utilities is 660.7 KB.

---

