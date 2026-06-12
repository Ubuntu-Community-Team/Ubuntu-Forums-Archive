---
title: "Virtualbox, guides, usb and 8.04"
date: 2008-05-17
forum: Virtualisation
---

### Post by corrosion on 2008-05-17
Hi all,

I've been following the guides here to make USB work on my Virtualbox.
Nothing seems to work. I want to use the Virtualbox package on the repositories, just to be safe when upgrading to the next ubuntu version.

But I am really getting tired of this. Is it possible to have USB on the OSE version of the repositories? If not, tell me please, I will have to use the commercial version.

Thanks.

---

### Post by corrosion on 2008-05-17
I will answer to myself, with the hope it will help any other one. OSE does NOT support USB. What a ****

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by SlappyPappy on 2008-05-17
You got it dude, stay away from the Synaptic and the OSE version. 

I'm in Gutsy and USB works great. Just be sure to do the guest additions.

You can try this for USB too:

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

And for printing:

[http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer](http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer)

Good luck brah!   :)

---

### Post by tonyargento on 2008-05-24
First off, you need to download the virtual box .deb package from Sun's website directly.

Second, edit your /etc/fstab file with this command:

[COLOR="Red"]sudo gedit /etc/fstab[/COLOR]

Once in fstab, you have to make your final line of code read:
[COLOR="Red"]
none     /proc/bus/usb     usbfs      devgid=124,devmode=664    0    0[/COLOR]

Replace "124" with whatever your group ID is for vboxusers, and you should be in business.

---

### Post by jmtritch on 2008-05-24
I just got VirtualBox OSE 1.6 working with USB yesterday on Xubuntu 8.04 using the following guide:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html")

  It worked like a charm for me and I suggest you check it out.  Also, I recommend downloading the 1.6 version and not the 1.5 version:

[http://www.ubuntu-unleashed.com/2008/05/virtualbox-160-just-released-for-ubuntu.html]("http://www.ubuntu-unleashed.com/2008/05/virtualbox-160-just-released-for-ubuntu.html")

Like tonyargenta said, **Do not use the repository**.  Use the .deb package.  I first tried installing from the repositories, but couldn't get USB support.  The deb package worked like a charm though.  Good luck!

---

