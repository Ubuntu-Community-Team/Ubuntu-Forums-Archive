---
title: "Sun Microsystem Sunfire V100"
date: 2009-01-31
forum: Server Platforms
---

### Post by Grosneg on 2009-01-31
I was given a Sun Microsystem model: sunfire v100 and am looking for something to do with it. Two questions here. 1) Will the "ubuntu-8.04.1-server-sparc.iso" CD run on it? 2) If not, other than Solaris, will anything else run on it? Thanks!

---

### Post by RealPSL on 2009-02-01
Ubuntu will most likely run as well as other Linux distributions that support SPARC architecture. You can also run FreeBSD. [http://www.freebsd.org/where.html]("http://www.freebsd.org/where.html")

You can also give OpenSolaris a look as well. 

[http://opensolaris.org/os/downloads/]("http://opensolaris.org/os/downloads/")

---

### Post by Grosneg on 2009-03-10
> **RealPSL said:**
> Ubuntu will most likely run as well as other Linux distributions that support SPARC architecture. You can also run FreeBSD. [http://www.freebsd.org/where.html]("http://www.freebsd.org/where.html")

You can also give OpenSolaris a look as well. 

[http://opensolaris.org/os/downloads/]("http://opensolaris.org/os/downloads/")
Thanks for your answer RealPSL. I have found several O/Ss to try, however they are all on DVD. I have an external USB DVD unit but can't figure out the command to get the server to boot from that device; and don't even know if it can boot from a USB device. Does anyone know?
Thanks,
Grosneg

---

### Post by dguitar on 2009-03-10
Use CDs? :)

I wouldn't use FreeBSD, they don't provide Net or Open BSD would be a better option (imo). OpenSolaris is another great and easy option if you aren't a Solaris person, Solaris 10 isn't that bad either. ;)

I don't personally run Ubuntu on my Sparcs but I've heard good things about Ubuntu on sparc.

---

### Post by NativeAngels on 2010-06-17
I also have 3 of these but have yet to sucessfully install linux on them. Can anyone help can opensolaris be installed via cdrom as theyre not yet connected to a network.

---

### Post by Lsurzy on 2010-07-31
For booting a sparc off of a USB driver read this: [http://www.sun.com/io_technologies/usb/USB-Faq.html](http://www.sun.com/io_technologies/usb/USB-Faq.html)

"25. Can I boot from a USB disk or USB CD/DVD drive?
...

Sparc systems with USB 2.0 support can boot from USB disks if the OBP(Open Boot Prom) is upgraded to version 4.27 or later. ..."

The FAQ goes into further detail, as you can see, this can be somewhat trikeydickey.

I recommend you download a boot-only installer image, burn it on to a CD and install downloading off internet. Solaris 10 should still be available on CD from Oracle, albeit they have stopped free support. AFAIR.

There are several Linux and BSD distros/releases that support the V100 and offer CD images for the architecture.

---

