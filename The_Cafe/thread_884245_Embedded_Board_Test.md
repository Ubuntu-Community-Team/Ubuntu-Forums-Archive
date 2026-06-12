---
title: "Embedded Board Test"
date: 2008-08-08
forum: The Cafe
---

### Post by solarwind on 2008-08-08
Embedded Board Test

Hey all, Someone gave me an Intel 80486 embedded board with 16 mb of ram. I have lots of plans for this thing, but I need to first know if it's working or not. The guy who gave it to me said it was working, but I have no idea how to test it.

It has a vga port, but it's not a D-SUB connector. It has an ethernet port, but it's not a standard ethernet port. They're all block connectors. Also has an IDE port, but again, not standard connector. It does, however, have serial ports with standard connectors and a floppy port with standard connector. I want to somehow test if this board is working. I don't want to go making any special connectors to hook up the VGA just yet. I want to first make sure if its working.

In summary, I have an accessible serial port and a floppy port and a working floppy disk drive. I think it also has a pc speaker (the ones on the motherboard that make the "beep" noise). I was thinking, if somehow I could get a bootable floppy or something to boot and just make a beep noise, I would know if it was working, but I have no idea where I could get such a floppy. Does anyonee have any ideas on how to test if this embedded board is working? It also has non-standard keyboard and mouse ports.

---

### Post by ModelM on 2008-08-08
You can probably get all your fixin's to make a boot floppy here...

[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

### Post by solarwind on 2008-08-08
> **ModelM said:**
> You can probably get all your fixin's to make a boot floppy here...

[http://www.bootdisk.com/](http://www.bootdisk.com/)

Ok, so what do I do with the bootdisk? I have no display/keyboard/mouse for this embedded machine as I have mentioned.

---

### Post by solarwind on 2008-08-10
bump

---

### Post by markbuntu on 2008-08-10
Unless you have and ocsilloscope or bus reader, you are not going to be able to do anything with that without a keyboard and a display and a floppy drive. You could try to talk to it through the serial port, but you need to boot it first.

The first time I tried linux was on a 486 machine, it worked, though configuring x caused my monitor to catch on fire, lol.

Some of those old embedded boards had a POST (Power on self test) which sent messages through the serial port).

---

### Post by Friqenstein on 2008-08-10
Embedded devices are a bit different than most 'normal' PC parts.
I've done a bit of embedded design/development with my old company.

We ran everything through 2 different OSes. EmbeddedXP and EmbeddedLinux.
Unfortunately for me at the time, both were a hassle beyond belief. RedHat was the 'leading' embedded Linux distro and was charging something ridiculous as Microsoft does/did.

I eventually compiled my own *nix via LFS (*[Linux From Scratch]("http://www.linuxfromscratch.org/")*) because the RedHat license fees were just laughable.
We ran both systems parallel to one another to test the differences. Needless to say the LFS OS boot image was much smaller, faster, and had more utilities than the EmbeddedXP version. We did also try the WindowsCE, but it just lacked anything useful at the time.

Long story short, you might need to build a specific linux kernel and toss it on a floppy.
Oreilly has a few books worth looking into, or you can just Google the needed info. I'm sure now-a-days the Embedded projects have come a long way. (My last embedded project was about 8yrs ago)

---

### Post by solarwind on 2008-08-10
> **Friqenstein said:**
> Embedded devices are a bit different than most 'normal' PC parts.
I've done a bit of embedded design/development with my old company.

We ran everything through 2 different OSes. EmbeddedXP and EmbeddedLinux.
Unfortunately for me at the time, both were a hassle beyond belief. RedHat was the 'leading' embedded Linux distro and was charging something ridiculous as Microsoft does/did.

I eventually compiled my own *nix via LFS (*[Linux From Scratch]("http://www.linuxfromscratch.org/")*) because the RedHat license fees were just laughable.
We ran both systems parallel to one another to test the differences. Needless to say the LFS OS boot image was much smaller, faster, and had more utilities than the EmbeddedXP version. We did also try the WindowsCE, but it just lacked anything useful at the time.

Long story short, you might need to build a specific linux kernel and toss it on a floppy.
Oreilly has a few books worth looking into, or you can just Google the needed info. I'm sure now-a-days the Embedded projects have come a long way. (My last embedded project was about 8yrs ago)
Thanks. I'm using QNX for this. QNX is simply amazing.

---

