---
title: "need advice..."
date: 2008-03-29
forum: The Cafe
---

### Post by mikawber on 2008-03-29
After installing Ubuntu more than a year ago, I told myself I would never go back to Windows. I love everything about Ubuntu and I thought I would never have to return. However, like many people, I fell into the iPhone trap. Don't get me wrong, my iPhone is by far the best phone/device I've ever owned. 

I know have a huge problem. I find myself consistently using Windows and Microsoft Office so that I can sync my iPhone with iTunes and Outlook. I don't have a HUGE hatred to Windows but I'd really like to use only Ubuntu. 

Like many other people I thought I would be able to sync my iPhone using a virtual machine. Since this option is pretty much useless, I find myself torn between the operating system I love and complete functionality of my beloved iPhone. 

So I guess I'm here because I no longer feel the need to use Ubuntu. Why use it when I can use iTunes, Outlook, and other Office applications and have the full functionality of my iPhone?

I love Ubuntu and if there was a way to do all this in Ubuntu I would. So I guess I'm here to ask for some advice from other iPhone users. What have you done to overcome this? 

Thanks in advance

---

### Post by xArv3nx on 2008-03-29
Doesn't WINE support iTunes?

Also, you could wait on Crossover 7.0 which, when released, should support Microsoft Office 2007 (I think).

---

### Post by hhhhhx on 2008-03-29
> **xArv3nx said:**
> Doesn't WINE support iTunes?

yes, but not usb devices

-----------

also you may wan to take a look at these links :
[http://www.timfanelli.com/item/204](http://www.timfanelli.com/item/204)
[http://zdavatz.wordpress.com/2007/11/05/sync-your-iphone-with-linux-who-has-done-that/](http://zdavatz.wordpress.com/2007/11/05/sync-your-iphone-with-linux-who-has-done-that/)
[http://www.hackitlinux.com/50226711/how_to_use_your_iphone_on_linux.php](http://www.hackitlinux.com/50226711/how_to_use_your_iphone_on_linux.php)

---

### Post by Sinkingships7 on 2008-03-29
EDIT: having some second thoughts... i'll get back to you.

---

### Post by ryanhaigh on 2008-03-29
Virtualbox (not the OSE release available in the repos but the PUEL version from the website) supports access to usb devices. I have sucessfully had a wireless adaptor working in a windows vm as a way of getting direct access to my network. You need to make some simple changes to /etc/fstab but apart from that I don't think I had any issues.

```
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

---

### Post by ntetreau on 2008-03-29
You can easily sync your music using gtkpod or amarok in ubuntu Gutsy and newer Ubuntu.  If you follow the wiki to the letter, it should get you there: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Furthermore, I sync my contacts with evolution via the web using syncevolution and the Funambol app on the iphone.  Notes and calendar syncing are almost there but need a bit of fiddling to get it to work.

As for virtual machines, none of them can get the iphone and itunes to work yet.

---

### Post by mikawber on 2008-03-31
> **ntetreau said:**
> You can easily sync your music using gtkpod or amarok in ubuntu Gutsy and newer Ubuntu.  If you follow the wiki to the letter, it should get you there: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Furthermore, I sync my contacts with evolution via the web using syncevolution and the Funambol app on the iphone.  Notes and calendar syncing are almost there but need a bit of fiddling to get it to work.

As for virtual machines, none of them can get the iphone and itunes to work yet.

Syncing via SSH doesn't seem like a good solution to me. Way too slow if you are transferring more than a couple songs at a time and pretty much useless for a movie.

---

