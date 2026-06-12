---
title: "Save an installation as a snapshot..."
date: 2011-09-28
forum: Server Platforms
---

### Post by fizgig on 2011-09-28
So right now I have a list of steps to install ubuntu server headless onto a computer to accomplish a certain task.  I install LAMP, Ruby, some random gems, install a database structure, configure apache and so on.  Since this small computer doesn't have a CD, I install Ubuntu from a thumbdrive.

When I get it to how I want it, I'd really like to save it sort of like a snapshot that I can then apply to an identical machine quickly.  I don't want to use a virtual machine since the computer I'm using isn't very high powered and I'd really like to stick to the bare metal.

Anyone know how I could do this?

---

### Post by SeijiSensei on 2011-09-29
Take a look at [Remastersys](http://www.geekconnection.org/remastersys/).

---

### Post by aeiah on 2011-09-29
if the machine is going to be identical, you could just clone the hard drive, either with dd or clonezilla. remastersys as mentioned is another option but is more for creating a customised installable media, and may over complicate things if you're just going to be using it on the same / identical hardware

---

### Post by fizgig on 2011-09-29
Thanks all.  I'll check out remastersys first since I'm not sure if I'll always be using the same size hard drive each time.

---

