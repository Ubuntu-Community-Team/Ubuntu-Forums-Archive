---
title: "good VM software?"
date: 2009-02-12
forum: Virtualisation
---

### Post by Arminius on 2009-02-12
I'm running ubuntu, but I wanna run xp in Virtual, but I need to be able to transfer files from real drives to the virtual drive, the last software I used couldn't do that.

---

### Post by heartwarmer on 2009-02-12
I use vmware and its great, you can just copy paste between the real drives and the virtual drive, but its not free, and its a bit heavy.
there is an open source alternative which is virtualbox, I've never used it but as i hear (read), its has most of vmwares features, and its lighter.

---

### Post by kdcoetzee on 2009-02-12
VirtualBox is a good bet.

---

### Post by finer recliner on 2009-02-12
vote vmware

---

### Post by cb951303 on 2009-02-12
+1 for virtualbox

---

### Post by KuroYoma on 2009-02-12
I agree.  Go to this website:
[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/)

follow the instructions so you can have usb support as well and you are good to go.

---

### Post by Joshonekenobi on 2009-02-12
Virtual box is amazing!

---

### Post by Arminius on 2009-02-13
ok, I've tried Virtualbox, and it's going ok so far, but where I have entered all my usb devices in the virtualbox program side of things.
only my iphone is showing up in the virtual drive, my usb hard drive which is the most important isn't showing up on the XP my computer in the virtual drive?

infact I'm not seeing any means to transfer files back and forth yet, on the xp side the only hard drive is the virtual drive.

---

### Post by cb951303 on 2009-02-13
> **Arminius said:**
> ok, I've tried Virtualbox, and it's going ok so far, but where I have entered all my usb devices in the virtualbox program side of things.
only my iphone is showing up in the virtual drive, my usb hard drive which is the most important isn't showing up on the XP my computer in the virtual drive?

infact I'm not seeing any means to transfer files back and forth yet, on the xp side the only hard drive is the virtual drive.

-You need to select the usb devies from virtualbox first.
-You can create a shared folder for file transfer. But first you need to install guest additions (it's in the menu somwhere, after booting the vm)

PS: I recommend installing the lates version 2.1.2, the one in the ubuntu repo is OSE version which doesn't support USB and it's old.

---

### Post by lakersforce on 2009-02-13
With VMWare, you just drag and drop from desktop-to-desktop...

It requires the VMWare tools installed in the guest OS. You can aquire these tools by downloading the Enterprise edition (free to download) and extracting the isos from the package, then install it in the Player. Stupid, I know, but it works.

---

### Post by Arminius on 2009-02-13
I'm not using the OSE version I am using the one that let's you use USB, my iphone is the only USB device that's showing up though

---

### Post by SLiguykyle on 2009-02-13
> **KuroYoma said:**
> I agree.  Go to this website:
[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/)

follow the instructions so you can have usb support as well and you are good to go.

will this method work on 8.04?? i want to try that, but dont want to waste my time if it's just going to fail.

---

### Post by cb951303 on 2009-02-13
> **SLiguykyle said:**
> will this method work on 8.04?? i want to try that, but dont want to waste my time if it's just going to fail.

how are you supposed to know if it will fail before trying? :lolflag:

---

### Post by howefield on 2009-02-13
> **cb951303 said:**
> how are you supposed to know if it will fail before trying? :lolflag:

By asking some-one who has tried it,.. oh wait, that's what he has done :lolflag::lolflag:

No it won't work, very similar but a couple of differences, I'll try and get you a link.

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by cb951303 on 2009-02-13
> **howefield said:**
> By asking some-one who has tried it,.. oh wait, that's what he has done :lolflag::lolflag:

No it won't work, very similar but a couple of differences, I'll try and get you a link.

there is no guarantee that it won't work on his system just because it didn't work on yours.
it's a 10 min job anyway. he could have tried it by time he posted that message :lolflag:

---

### Post by howefield on 2009-02-13
> **cb951303 said:**
> there is no guarantee that it won't work on his system just because it didn't work on yours.
it's a 10 min job anyway. he could have tried it by time he posted that message :lolflag:

Please point me to where I said it didn't work on my system...

There was a change in Ubuntu, which appears to have escaped you, from 8.04 to 8.10 which means the instructions for getting USB to work is slightly different for both. So yes, there is a guarantee.

:lolflag::lolflag:

---

### Post by KuroYoma on 2009-02-13
I can't say weather or not the last site works for Hardy Heron but this one does.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

Just skip step 4 unless you feel the Gutsy version would work better but I do now think so.  I tried this on a virtual machine and then started a Virtualbox inside of my Virtual box with usb support.

Hope that means it will work for you.

---

### Post by SLiguykyle on 2009-02-13
> **howefield said:**
> Please point me to where I said it didn't work on my system...

There was a change in Ubuntu, which appears to have escaped you, from 8.04 to 8.10 which means the instructions for getting USB to work is slightly different for both. So yes, there is a guarantee.

:lolflag::lolflag:

the reason i asked is because i am aware of these changes and i was heading off to bed and am going to attempt it today after some more research to see what is the most sure-fire way of getting it done(dont care to have to fix things that might not have to be broken in the first place). not because i dont know what i'm doing.

---

### Post by howefield on 2009-02-13
> **SLiguykyle said:**
> the reason i asked is because i am aware of these changes and i was heading off to bed and am going to attempt it today after some more research to see what is the most sure-fire way of getting it done(dont care to have to fix things that might not have to be broken in the first place). not because i dont know what i'm doing.

My comment was in response to another poster, not you.

---

### Post by itendo on 2009-02-13
+2 for virtual box (one being my imaginary friend)

---

### Post by bapoumba on 2009-02-14
Moved to virtualization.

---

