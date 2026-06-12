---
title: "[SOLVED] A couple of question about virtual box"
date: 2008-01-27
forum: Virtualisation
---

### Post by famous3warriors on 2008-01-27
Ok I went to the virtual box web site and I got the ose version of virtual box I need the full version of virtual box.  Now the question is I got everything loaded onto my system no is there just an upgrade to the full version or do I loose everything when I get the binary version of it?  Thanks for your help.

---

### Post by The Cog on 2008-01-27
I think what you're asking is whether you can upgrade from the open source VirtualBox that comes with the Ubuntu distro to the restricted binary version that can be downloaded from their site.

I don't actually know for sure, but personally, I would prefer to play safe and uninstall the version from the repos before installing the downloaded version. I have succesfully installed the downloaded version (without installing the FOSS version first). Make sure you have installed the package build-essential first - I'm not sure if it's still needed but it used to be. Then click on the downloaded .deb file and choose to install. The install will appear to freeze partway through, but when you open the detailed pane, you see it's waiting for you to agree ot the license terms.

---

### Post by famous3warriors on 2008-01-27
ok I will do that.  One question thoug will virtual box work on ubuntu studio 7.10 i386 also.

---

### Post by mister_pink on 2008-01-27
Don't see any reason why it wouldnt work in studio. And if you were wondering if itll find your current guest OSes, it should do automatically. If it doesnt then their virtual disk files are by default saved in a folder .virtualbox in your home directory, its straightforward enough to import them when you reinstall. I did this when I reinstalled ubuntu - i installed the OSE forgetting it lacked the one feature i needed - usb support to sync my mobile phone.

---

### Post by famous3warriors on 2008-01-27
Ok cool thanks I really do apprecitate you help.

---

### Post by famous3warriors on 2008-01-27
I downloaded the binary code from virtual box and got it working but how do you set it up to accept the usb devices?

---

### Post by famous3warriors on 2008-01-27
I keep getting this error

---

### Post by hums07 on 2008-01-27
Faced that problem before and found the answer after searching this forum. Something about setting on /etc/fstab then restart Ubuntu.
Sry for not helping more.

---

### Post by famous3warriors on 2008-01-27
I found something like that also I just don't know how to go about it.  I really need some files that I created in adobe for work tomorrow.

---

### Post by famous3warriors on 2008-01-29
Thanks guys I really do appreciate your help.  [http://ubuntuforums.org/showthread.php?t=670238](http://ubuntuforums.org/showthread.php?t=670238) This is where I found a step by step how to get the usb working.:lolflag:

---

