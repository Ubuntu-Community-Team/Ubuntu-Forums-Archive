---
title: "Looking for advice on Virtualisation software and setup"
date: 2015-05-18
forum: Virtualisation
---

### Post by Shugs81 on 2015-05-18
Hi peeps...

Looking to set up a Virtual Machine...

I plan to install windows in a VM so I can run Unity3d and Manga Studio under windows along side everything else under linux.

Have a decent system with 16gb ram and plenty of space...

Just wondering what will give me the best accessability between the two?

I tried boxes which seemed really simple but was wondering if there was a better system out there..

would it also be possible to have a partition or section that both linux and the vm could use at the same time?

I only need limited internet access for updates and such so even if i have to download these under linux and install them as and when I'm happy to do that too!!

any advice greatly appreciated!!

---

### Post by SeijiSensei on 2015-05-18
[VirtualBox](http://www.virtualbox.org)

Follow the instructions for "Debian-based distributions" on the [Linux downloads page]("https://www.virtualbox.org/wiki/Linux_Downloads") to add the Oracle repository to your system and install VB from there.  You'll want to install the [Extension Pack](https://www.virtualbox.org/manual/ch01.html#intro-installing) if you need USB support or a wider array of video resolutions.

---

### Post by Shugs81 on 2015-05-18
Thanks... installing as we speak... will post more questions shortly no doubt!! :D

---

### Post by Shugs81 on 2015-05-24
Reet.... tried xp but managed to blue screen into oblivion so that went out the window... managed to get win 7 installed...

Now...

How do I get windows to recognize USB devices? Would like to get my wacom tablet and a USB pen stick working so that I don't have to swap files via rw dvd which seems the only way I can do it so far....

Sorry for being a noob!!

---

### Post by SeijiSensei on 2015-05-24
As I said, you need the extension pack to use USB devices.  Some aspects of USB technology are [patented]("http://www.usb.org/developers/docs/") so the drivers cannot be open-sourced.

The VB manual is quite extensive; here's the section on USB devices: [https://www.virtualbox.org/manual/ch03.html#idp95121872](https://www.virtualbox.org/manual/ch03.html#idp95121872)

---

### Post by flaymond on 2015-05-24
+1 for VirtualBox

Clean and easy, and you need extension packs as mentioned by SeijiSensei to do more. You also need that for wireless connection in virtualbox.

---

### Post by Shugs81 on 2015-05-24
Hmm... was sure I installed them... I will have to have a look and see what has happened...

---

### Post by v3.xx on 2015-05-24
Check out the last post
[http://askubuntu.com/questions/169024/how-can-i-tell-if-the-virtualbox-guest-additions-were-installed-on-an-ubuntu-vm](http://askubuntu.com/questions/169024/how-can-i-tell-if-the-virtualbox-guest-additions-were-installed-on-an-ubuntu-vm)

more here
[https://www.google.com/search?client=ubuntu&channel=fs&q=virtualbox+check+guest+additions&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=virtualbox+check+guest+additions&ie=utf-8&oe=utf-8)

---

### Post by v3.xx on 2015-05-24
Also be sure to install dkms to the linux guest.  In terminal (on the guest machine):
```
sudo apt-get install virtualbox-guest-dkms
```
This makes a difference on my 14o4 setup.

---

### Post by SeijiSensei on 2015-05-24
> **Shugs81 said:**
> Hmm... was sure I installed them... I will have to have a look and see what has happened...
You need to do more than just install the extension pack.  You'll also need to define the devices by creating "filters" as described in the manual chapter I linked to above.  I have one defined that connects to my Logitech universal TV remote for instance.

---

