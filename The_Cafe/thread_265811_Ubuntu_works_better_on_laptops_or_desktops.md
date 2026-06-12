---
title: "Ubuntu works better on laptops or desktops?"
date: 2006-09-26
forum: The Cafe
---

### Post by tirian on 2006-09-26
Currently in our house, we have three laptops, all running Ubuntu. Recently, I bought replacement for our desktop: ([here]("http://www.newegg.com/Product/Product.asp?Item=N82E16883102664")) and decided to put Linux on it.

Although the installation on the laptops was a snap, Ubuntu really hated my desktop:

[LIST]
[*] Firstly, the install would crash or hang randomly. It took about 2-4 tries on average before I would be able to install the system
[*] The LiveCD would also hang and crash (although X would start fine) and acted strangely. For example, if I started the LiveCD with a disk in the floppy drive, the system wouldn't be able to detect either the floppy drive or the second CD drive. If I booted with a disk in the drive it worked fine. Then, if I tried to access the floppy drive, I would loose controll of my mouse.
[*] GRUB wouldn't install. The install would claim to have installed GRUB, but it would just boot into windows when I restarted. I ended up having to format my root partition as XFS in order to force LILO to install.
[*] The system wouldn't boot reliably. It would work most of the time, but about 1/4 of the time, it would hang while trying to load drivers
[*] The onboard NVidia wouldn't work. If I tried to load the drivers (following the instructions on the wiki) the system would lock up as soon as GDM (I couldn't switch to a virtual terminal or kill X)
[*] However, I then accidentily deleted my xorg config file and then X11 worked file (why?)
[*] Then, when I finally got into my shiny new ubuntu desktop, my sound card wouldn't work.
[/LIST]

At this point, I gave up :)

I finially went to openSUSE and it worked better (although it didn't automatically detect my wireless card which Ubuntu did).

I don't understand. Ubuntu has been rock solid on my laptop (other than suspend problems once in a while) and I love it. Why would it fail on a desktop where hardware is more standardized.

Is this normal?

---

### Post by prizrak on 2006-09-26
Laptop or desktop, it is all dependent on the hardware you are using. If that hardware plays well with Linux you will have no problem if not you will have a problem :)

---

