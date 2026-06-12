---
title: "Trouble Virtualizing Ubuntu on a Macbook"
date: 2008-09-06
forum: Virtualisation
---

### Post by Tigercat212 on 2008-09-06
Hey guys!  I am having a bit of trouble when I am virtualizing Ubuntu using xVM Virtualbox on my Macbook. First off, it says that I have no sound care installed which obviously, the Macbook does have one. Also, I am trying to install and run Compiz Fusion. I read someone's directions that said to go to Preferences > Appearence and enable Normal or Extra effects. I tried to enable Normal and it said "Desktop effects could not be enabled." Any idea why? Does the Macbook have a good enough video card? I've seen videos on Youtube of people running Ubuntu with Compiz Fusion on their Macbook. 

Also, is Amarok a good program to use with my iPod in Ubuntu. Last two things. In Sun xVM Virtualbox, is there a way to run Ubuntu in fullscreen mode without a black frame around it? One last thing. Is there a way for me to delete the .ISO file from my Mac hard drive so it is only in the VM because I don't want it cluttering up my desktop and OSX hard drive?

So, do you think most of these problems are because I need to install drivers of some sort?

Thanks in advance,

Tigercat212

---

### Post by Virtua-Touch on 2008-09-07
1st. The sound problem is common, I think. I have never been able to get sound to work in my Ubuntu guest.
2nd. The special desktop effects and compiz do not work on a virtual machine because VBox does not have 3D graphics drivers. 
3rd. Amarok is a good program, I think, if I can remember.

---

