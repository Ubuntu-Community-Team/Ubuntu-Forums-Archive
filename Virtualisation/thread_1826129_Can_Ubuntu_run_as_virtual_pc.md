---
title: "Can Ubuntu run as virtual pc ?"
date: 2011-08-16
forum: Virtualisation
---

### Post by FMS.SouL on 2011-08-16
Hello guys,I wondering if the linux remote desktop or any features can run as virtual PC,so I can leave my application running on the virtual desktop.
Here the source [http://www.alwaysonpc.com/about.php](http://www.alwaysonpc.com/about.php)
The graphic interface almost same with linux,I wondering if linux have this feature for I leave my virtual desktop running.
I tried to download this AlwaysOnPc software,but it doesn't support java so I can't run any application/program on it.

---

### Post by sanderd17 on 2011-08-16
Yes, it is possible, but you need your own server that is always online and always running.

You can install a Virtual machine on that server (I would recommend Vritualbox) and afterwards, you can connect to that virtual machine from other computers: [http://www.virtualbox.org/manual/ch07.html](http://www.virtualbox.org/manual/ch07.html)

I don't know if you can do it with other devices like iPhone or Android.

---

### Post by FMS.SouL on 2011-08-16
Thank you so much however I only wanted virtual pc,doesn't need ipad or iphone.

---

### Post by raja.genupula on 2011-08-16
you can run Ubuntu in virtual PC . but my suggestion if your afraid to install Ubuntu as in its own partition then use a program called WUBI . by this you can install Ubuntu in the inside of your windows , if you Don't want it you can remove it by un installing it in add/remove programs . what do you say ?

---

### Post by FMS.SouL on 2011-08-16
I installed Ubuntu,just wondering how do I can create the virtual Pc on it
Anyways,can show me the step for create it ?

---

### Post by sanderd17 on 2011-08-16
What you want is a remote virtual PC. You can also have a virtual PC that stays on one computer (this is often used to run Windows inside Linux or to test an OS).

But I don't really think it's worth the trouble. Isn't file sharing (with programs like Ubuntu One or Dropbox) enough? Running a virtual OS is always a lot slower.

---

### Post by sanderd17 on 2011-08-16
> **FMS.SouL said:**
> 
Anyways,can show me the step for create it ?

Is your server headless (without a graphical environment) or headed? For a headed server, you can just install Virtualbox from their website: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Install it, make a new Virtual PC, use an Ubuntu iso file to install Ubuntu on that virtual PC and check the link I gave before to run that virtual PC on another computer (you also need to have Virtualbox installed there).

A headless server will ask more work.

---

### Post by FMS.SouL on 2011-08-16
After installed,it need some configuration or something else more ?

---

### Post by sanderd17 on 2011-08-16
> **FMS.SouL said:**
> After installed,it need some configuration or something else more ?

Setting up the networked mode asks some work, but setting up a local VM doesn't ask more configuration than installing the OS.

---

### Post by raja.genupula on 2011-08-16
> **FMS.SouL said:**
> After installed,it need some configuration or something else more ?

i mean you,  yes you have to . but nothing like to get it into work , its like making it as you like .after installing ubuntu no more configurations man , you can directly put into work .

---

### Post by bodhi.zazen on 2011-08-16
*Thread moved to **Virtualization**.*

---

### Post by FMS.SouL on 2011-08-16
Thank for advice of you guys.:D

---

