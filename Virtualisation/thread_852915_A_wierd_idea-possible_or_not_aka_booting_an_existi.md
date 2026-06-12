---
title: "A wierd idea-possible or not? aka booting an existing physical drive on a virtual PC"
date: 2008-07-08
forum: Virtualisation
---

### Post by DexterLB on 2008-07-08
I am dual booting with windows XP, and I have a NTFS drive for it. I almost don't use windows, only for programs which don't work under wine. But restarting the computer to boot under windows seems too slow. So, is it possible to boot the physical NTFS hard drive with VirtualBOX or VMWare? Or they can ONLY boot virtual hard drives? :popcorn:

---

### Post by stevebakerj on 2008-07-08
I havent done it in Hardy and VBox 1.6.x but I used this guide under Feisty and VBox 1.5.x and all worked well:

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

---

### Post by DexterLB on 2008-07-08
I tried to do it...
I fixed the HDD permitions, I made the pointer file, I made the virtual machine. Then I started it. I've got the virtualbox BIOS screen, then it booted the hard disk. And... black screen with a cursor. Inactive cursor. I restarted the virtual machine and I pressed F12, and the hard disk is available. When I try to boot it, I get the black screen with the cursor. Sending ctrl-alt-del or shutdown signals to the virtual machine does nothing. This evening I am gonna get a PE builder and test if it boots through CDROM. But what could be preventing windows from booting?

-----------------------------------------------
UPDATE
-----------------------------------------------
I also tried to boot the "install guest additions" virtual CDROM, and I get "FATAL: could not read from the boot medium!Systam halted"

---

### Post by Sand Lee on 2008-07-08
Here, I made a tutorial on it: [Boot an existing XP (Physical HD) install with VirtualBox]("http://ubuntuforums.org/showthread.php?t=769883"). Updating it as we speak...

---

### Post by DexterLB on 2008-07-09
Yeeeeee now I have windows in a box!
Just one more problem to fix: no mouse or keyboard.
When I capture the mouse, and I move it, nothing happens. Keyboard also doesn't work.

P.S. The usb devices indicator shows that the USB mouse is unavailable.
P.P.S. Thanks for the tutorial!

---

### Post by DexterLB on 2008-07-09
I think it will work if I install the GUEST ADDITIONS, but then I won't be able to log in to windows without virtualbox, which is bad because dad works under windows. But isn't there other way?

---

### Post by Sand Lee on 2008-07-09
> **DexterLB said:**
> I think it will work if I install the GUEST ADDITIONS, but then I won't be able to log in to windows without virtualbox, which is bad because dad works under windows. But isn't there other way?

I would **not** recommend taking that risk! I've been in this situation a while ago, and thus, I don't remember what I did to solve it exactly (or if I even did solve it). 
If you must try it out, however, I would recommend you _image_ your XP installation with Clonezilla-Live. If something happens to go wrong, then you would be able to restore the image.

---

### Post by DexterLB on 2008-07-10
That's true, but the GUEST ADDITIONS are the last thing I can do.
In [THIS](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/) tutorial they say that USB devices work with no problem. Why they aren't on my computer? What could I be doing wrong? :confused:

---

### Post by Sand Lee on 2008-07-12
> **DexterLB said:**
> That's true, but the GUEST ADDITIONS are the last thing I can do.
In [THIS](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/) tutorial they say that USB devices work with no problem. Why they aren't on my computer? What could I be doing wrong? :confused:

That tutorial is quite dated, I would look for a more recent one. And I won't discourage you from trying any out. Just warning that you should image your xp before installing guest additions.. as it may be the last time you boot it natively.

---

### Post by DexterLB on 2008-07-13
true. Then I'll try...

---

### Post by DexterLB on 2008-07-14
I didn't install the guest additions. I didn't need to...

I was running the virtual machine (mouse & keyboard were still not working). Then I plugged in a second usb mouse (didn't unplug the first one), captured the interface and... VOILA! Both mice & the keyboard started to work perfectly! :lolflag: Then I unplugged the second mouse, and everything continued to work fine. After 1 day everything keeps running fine. :popcorn: I just wonder what the problem was...

P.S. Windoze works on the VM even bettar than on the physical :guitar:

---

### Post by Sand Lee on 2008-07-14
Good to hear! I hope everything works out for you! =p

---

