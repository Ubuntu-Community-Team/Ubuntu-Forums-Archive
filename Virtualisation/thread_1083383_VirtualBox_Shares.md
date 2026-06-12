---
title: "VirtualBox Shares"
date: 2009-02-28
forum: Virtualisation
---

### Post by FraggedLocust on 2009-02-28
I've set up a Windows XP VM and would like to get shares working, but they seem to not do anything.

I set up a folder from ubuntu(host) where I placed drivers for my laptop in windows(guest), I've installed Guest Additions and enabled sharing on Linux, and added the folder in VirtualBox. I linked to the share in Windows using a shortcut, but when I try to open it, nothing happens.

When the share is missing from the virtualBox list, the broken shortcut message pops up pretty fast.

---

### Post by lykwydchykyn on 2009-02-28
Are you following some kind of howto here?  This seems a lot more complicated then it needs to be.  It's been a while since I set this up, but it seems like I just picked a folder in virtualbox and then just mapped a drive.

Also, am I understanding you correctly that you're wanting to install drivers for your native hardware on a VM?

---

### Post by FraggedLocust on 2009-02-28
Yeah, I guess that can be skipped. I just wanted my VM to handle the internet so I can use course material for college (which is published in MS Office 2007). I'm not quite sure how well Impress 3 handles pptx.

I see. that works much better.
I guess I can just save the course stuff to the share.

---

### Post by lykwydchykyn on 2009-02-28
> **FraggedLocust said:**
> Yeah, I guess that can be skipped. I just wanted my VM to handle the internet so I can use course material for college (which is published in MS Office 2007). I'm not quite sure how well Impress 3 handles pptx.

IME internet has been working out of the box with winxp and virtualbox.  The native hardware drivers won't do you any good, because the VM is only seeing virtualized hardware.  Have you installed the guest additions?

---

### Post by FraggedLocust on 2009-02-28
> **lykwydchykyn said:**
> IME internet has been working out of the box with winxp and virtualbox.  The native hardware drivers won't do you any good, because the VM is only seeing virtualized hardware.  Have you installed the guest additions?
How would I configure that?
Yes, I do.

---

### Post by lykwydchykyn on 2009-02-28
Yes you do what?

---

### Post by FraggedLocust on 2009-02-28
Sorry, I have the Guest Additions installed. at least, it shows the virtualBox server in Networking and the icon in the taskbar.

---

### Post by thisllub on 2009-03-01
Maybe you have a permissions problem with the shared folder

---

