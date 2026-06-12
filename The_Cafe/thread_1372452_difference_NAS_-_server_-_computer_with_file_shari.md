---
title: "difference NAS - server - computer with file sharing"
date: 2010-01-04
forum: The Cafe
---

### Post by supermooshman on 2010-01-04
Hi all,  

quick question that has been puzzling me for quite a while now: 
What is the difference between a NAS, a server, and a computer with file sharing? 
 A 1TB NAS goes for about 400 on newegg, so what is the advantage of this in comparison to lets say a nettop running ubuntu server(probably with an upgraded hard drive, which pricewise would be doable) or a regular pc running ubuntu desktop, with filesharing?

someone help me to get this thing out of my head and let me get some sleep at night :) 
Thanks!

---

### Post by whiskeylover on 2010-01-04
NAS -> [http://en.wikipedia.org/wiki/Network-attached_storage](http://en.wikipedia.org/wiki/Network-attached_storage)

---

### Post by supermooshman on 2010-01-04
Thanks for the link... but that didn't really answer my question?
> A 1TB NAS goes for about 400 on newegg, so what is the advantage of this in comparison to lets say a nettop running ubuntu server(probably with an upgraded hard drive, which pricewise would be doable) or a regular pc running ubuntu desktop, with filesharing?

---

### Post by whiskeylover on 2010-01-04
I'm not sure either :) I thought I was just providing a part of the answer.

---

### Post by doas777 on 2010-01-04
a NAS is just a small server, that focuses on file/content serving.
they are usually cheaper (discounting disks, as you would have to purchase them either way), and often run a little smoother, if server administration is not your thing. NAS's are supposed to be applicances, so that is one of their main draws. they do one thing, and do it well. (although modern NASs have all kinds of extra features like DLNA streaming, browser access with ftp, internet accessibility etc). 

that 1TB nas on newegg seems overpriced at 400$ , but you would have trouble putting together a cheap but reliable box with a 1TB hdd for much less than that.

I got a synology NAS the other day (without disks) because my fileserver had run out of additional sata ports and usb ports, so that I could not add another drive when I needed too. I am really happy with it. it's fast, ext3 native,and it's linux based so I can ssh in and tweak it. for instance I symlinked several usb drives I added to it, so that I can treat multiple physical volumes as one, and adjusted the samba config a bit.
still need to figure out how to install a python interpreter on it though.

---

### Post by supermooshman on 2010-01-04
> **doas777 said:**
> a NAS is just a small server, that focuses on file/content serving.
So what would be the advantage of paying more for a nas (which I would guess has less options) than an energy efficient nettop?
- only the "(hopefully) works out of the box" feeling?

---

### Post by doas777 on 2010-01-04
> **supermooshman said:**
> So what would be the advantage of paying more for a nas (which I would guess has less options) than an energy efficient nettop?
- only the "(hopefully) works out of the box" feeling?

I think if you do the math, a nas is cheaper than a server, but if you go with really cheap parts, then perhaps.

as I said, the real draw is that it is an appliance. an *nix server is a blank slate, and you need to know how to paint the server you want. a NAS however, is a completed painting, and all you have to do is configure it with a highlight or two.

also most NASs use more than one disk, and are expandable. many servers however, need additional enclosures with funny connections (fibre channel is still around, believe it or not) or SANs, which are far from cheap

---

### Post by pgp_protector on 2010-01-04
> **supermooshman said:**
> So what would be the advantage of paying more for a nas (which I would guess has less options) than an energy efficient nettop?
- only the "(hopefully) works out of the box" feeling?

One advantage of NAS out of the box systems is you can give it to your parents* and they can use it with minimal fuss, vs a Linux box with SAMBA.

Most NAS have just a web interface for configuration / management.




*Assuming your parents aren't linux gurus :)

---

### Post by 03spirit on 2010-01-04
Google "FreeNas"
 
It will run on most anything 
 
Keeps the costs down and it does quite a bit..

---

### Post by Firestem4 on 2010-01-04
A True NAS is a purpose-built machine that typically run an optimized operating system specifically designed for file-sharing. They do not access the internet, or run any programs. They are headless (no monitor/peripherals attached). Essentially it a network capable HDD.

I hope this helps to clarify what i think the OP has been wondering.

---

### Post by supermooshman on 2010-01-04
Thanks!
Solves my question (have to reread it a few times though :P)

> **pgp_protector said:**
> *Assuming your parents aren't linux gurus :)
the day they start using linux, I think I'll start being a professional bullfighter

---

