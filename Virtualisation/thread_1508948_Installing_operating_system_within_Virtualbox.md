---
title: "Installing operating system within Virtualbox"
date: 2010-06-13
forum: Virtualisation
---

### Post by akelsall on 2010-06-13
I had been running a 2.x version of Vbox, but things have changed with the new version of vbox (just installed 3.2.4). Also running Ubuntu 10.04. 

I can't for the life of me figure out how to install the OS for a virtual machine. I thought last time I did this I converted my WinXP CD to an iso image and mounted that, but I can't figure out to do it with Vbox 3.2.4. It doesn't seem to be as intuitive this time around.

Anyone have ideas on how I can boot to an ISO image with vbox 3.2.4?

Thanks

Andy

---

### Post by jeremyswalker on 2010-06-13
The place to select an iso image as the CD drive is in the "Storage" area of the "Settings" dialog. This will then bring up the "[Virtual Media Manager]("http://www.virtualbox.org/manual/ch05.html")". That is where you select your iso image. Of course, don't forget to place the CD drive as the boot first device in the settings.

You could also just use your CD to boot from. You don't have to create an iso. Just select the host drive in the same area described above.

---

### Post by akelsall on 2010-06-16
Thanks jeremyswalker. That got me back on track.

Thanks,

Andy

---

### Post by Drone4four on 2010-06-17
This is an incredibly useful thread.  Thanks akelsall for asking the question about isos and VirtualBox.  And thanks jeremyswalker for answering the question.

---

