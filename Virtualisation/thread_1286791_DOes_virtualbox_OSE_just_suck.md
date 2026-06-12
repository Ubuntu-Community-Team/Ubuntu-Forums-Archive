---
title: "DOes virtualbox OSE just suck?"
date: 2009-10-09
forum: Virtualisation
---

### Post by c0mput3r_n3rD on 2009-10-09
I'm using virtualbox to virtualize windows inside ubuntu 8.10, how ever I can not access usb ports, my ubuntu files, and I can not download files off of the web.

Anybody have any idea what's going on here?

Thanks.

---

### Post by Perryg on 2009-10-10
OSE does not support USB you need the PUEL version for that.  You also need to install the guest additions to be able to get the shared folders to work.

---

### Post by linux4life88 on 2009-10-10
I've always been curios why these 4 features are not open source. It just doesn't make sense to me to have a problem completely open source but the have a separate edition with 4 more features and close the source on just those 4 features.

---

### Post by Perryg on 2009-10-10
According to Sun they do this to be able to make some money off of the product to be able to support the OSE.  Here read this [http://www.virtualbox.org/wiki/Licensing_FAQ](http://www.virtualbox.org/wiki/Licensing_FAQ)

But if you are going to use this for personal use you are covered by the PUEL license as well.

---

### Post by blur xc on 2009-10-10
> **c0mput3r_n3rD said:**
> I'm using virtualbox to virtualize windows inside ubuntu 8.10, how ever I can not access usb ports, my ubuntu files, and I can not download files off of the web.

Anybody have any idea what's going on here?

Thanks.

Yup, that's pretty much what I concluded, and went with the peul version.  It stinks because I have to manage updates on my own, rather than have them automatically done through the repositories. 

BM

---

### Post by Perryg on 2009-10-10
You can add the VBox as third part repository.  I do and it works flawlessly.  Follow the instructions here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and you will always be up-to-date.

---

### Post by blur xc on 2009-10-10
> **Perryg said:**
> You can add the VBox as third part repository.  I do and it works flawlessly.  Follow the instructions here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and you will always be up-to-date.

I did not know you could do that, is it a new development?  thanks for the tip!  

BM

---

