---
title: "Windows XP Install"
date: 2008-02-03
forum: System76 Support
---

### Post by lightnb on 2008-02-03
I'm trying to add a Windows partition to my Serval, and running into a minor dilemma. I have re-partitioned and created a FAT32 space for the install.

But- the Windows installer can't find my hard drive. I'm assuming this is because it's an SATA HDD and XP doesn't have a driver for it.

So naturally, I hit F6 to load a third party driver, when it tells me that I don't have a floppy drive installed. Windows really has a knack for the obvious.

Why on earth would Micros- never mind. The real question is, how can I get Windows installed on a SATA Hard Drive without using a floppy drive to load the drivers?

(or is there a full featured CAD program for Linux yet, so I can be rid of Microshaft forever?)

---

### Post by osx424242 on 2008-02-03
Strictly speaking, this isn't the answer to your question.  But, it seems like it might be more along the lines of what you want:
[http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/](http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/)
Could you use this technique to get to the Windows install point (with the bonus that you might not need an extra partition)?
Then, you not only have Windows, so you can run your all-important CAD app [P.S. if you find a good Linux CAD app let me know, as that's the biggest hurdle keeping a friend of mine from switching], but you can run CAD _without_ having to reboot: in fact you should be able to 'seamlessly' switch between your CAD app and your normal Ubuntu apps.

---

### Post by lightnb on 2008-02-03
I'm playing with this now and it's pretty sick.

It would be cool if the virtual machines could tie into the multiple desktop feature though, so you don't have a start menu on top of the K menu or vis-versa...

We'll see how it goes...

---

### Post by palintheus on 2008-02-03
There is another thread about this somewhere in the sys76 sub-forum, it has links dealing with customizing the windows install cd so it has the drivers in it. I will dig and try to find the links, if I can I will edit my post.

== Edit ==

Found them, hope they help

[http://ubuntuforums.org/showthread.php?t=601745](http://ubuntuforums.org/showthread.php?t=601745)

[http://ubuntuforums.org/showthread.php?t=686287](http://ubuntuforums.org/showthread.php?t=686287)

---

### Post by lightnb on 2008-02-04
Thanks for the links. (The second one is a link back to this thread...)

But the first one seems to have the solution, adding the driver to the windows CD.

At the moment, I've got Windows running on a virtual machine, per osx424242, which is pretty cool. In the next couple days, I'll try running more thorough tests with my few Windows apps to see if they're stable enough for use inside the VM.

I may not even need to dual-boot at all.

---

### Post by palintheus on 2008-02-04
DOH! copied the wrong one....

[http://ubuntuforums.org/showthread.php?t=636617](http://ubuntuforums.org/showthread.php?t=636617)

---

