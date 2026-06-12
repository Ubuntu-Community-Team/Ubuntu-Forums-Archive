---
title: "Installing Ubuntu on Sun Netra's"
date: 2008-04-21
forum: Sun Sparc Users
---

### Post by djh82uk on 2008-04-21
Hiya Guys

I have 40 rackmount machines, all have Ultrasparc IIe 500MHZ CPU's, the ones ive opened so far have 512MB Ram, 20GB HDD, no CD Drives, No VGA PORTS :(


So where the hell do I start?  I have gotten access to the Openboot OK command prompt via a serial cable.

Now Im presuming I need to setup a normal PC as a TFTP server and serve the files to boot and install that way

But how do I do it, Im kinda stuck on where to start

Please Help

DJH

---

### Post by kdepa on 2008-06-18
I have a similar situation with my Netra X1.  What I did is find a generic ATA CD drive, set it to Master, and plug it into the secondary ATA port.  At the ok> prompt, enter "boot cdrom - nowin"
(without the quotes, of course).  The computer then boots from the CD.

-- Kyle

---

### Post by bkortleven on 2008-06-25
I guess, if you don't have a VGA or other graphics port, just hook up a serial terminal to the (first?) serial port on the back of the machine, and you'll get to see the boot stuff on there...
You might need to 'stop' the OpenBoot procedure and run the 'boot cdrom' commands needed to boot from cd...

Worked with my Sun Ultra 5, so it must work on the Netra's too, no???
Correct me if I'm wrong, we all learn from yours and each others' mistakes...

---

