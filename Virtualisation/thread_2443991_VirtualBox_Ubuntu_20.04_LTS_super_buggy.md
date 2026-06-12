---
title: "VirtualBox Ubuntu 20.04 LTS super buggy"
date: 2020-05-23
forum: Virtualisation
---

### Post by asoftwrengrithink on 2020-05-23
[COLOR=#141414][FONT=&quot]Hi, I downloaded the Ubuntu 20.04 .iso for VirtualBox because I'm on Windows 10 64bit (work laptop). I really love the look & feel of the new 20.04 Ubuntu, my only issue is the Guest Additions doesn't allow me to copy and paste between host and guest OS and drag 'N drop doesn't work either.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Also, when I watch youtube videos or anything with audio, the audio stutters and video seems laggy. It really seems buggy as hell. Not sure if this is a virtual box issue, or something with my Ubuntu installation. Can anyone provide any insight?[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]This is my first-time using Linux (Ubuntu) as my main OS (albeit a VM) but despite the buggy-crap, I would really love it to be my daily driver...[/FONT][/COLOR]

---

### Post by howefield on 2020-05-23
Thread moved to the "*Virtualisation*" forum.

---

### Post by Morbius1 on 2020-05-23
What version of VirtualBox?

[Linux guest: shared clipboard doesn't work (on fresh VirtualBox-6.1.4-136177) => fixed in 6.1.6]("https://www.virtualbox.org/ticket/19336")

---

### Post by ajgreeny on 2020-05-23
Have you added your user in the guest Ubuntu-20.04 system to the vboxsf group?
That is a requirement for shared folders to work in a Linux guest.

I am now using VBox-6.1.8 with several Linux distro guests and can share files and drag/drop with no difficulty.

---

### Post by asoftwrengrithink on 2020-05-27
> **Morbius1 said:**
> What version of VirtualBox?

[Linux guest: shared clipboard doesn't work (on fresh VirtualBox-6.1.4-136177) => fixed in 6.1.6]("https://www.virtualbox.org/ticket/19336")

I'm on 6.1.8

---

### Post by asoftwrengrithink on 2020-05-27
> **ajgreeny said:**
> Have you added your user in the guest Ubuntu-20.04 system to the vboxsf group?
That is a requirement for shared folders to work in a Linux guest.

I am now using VBox-6.1.8 with several Linux distro guests and can share files and drag/drop with no difficulty.

Yes, I just did. But Copy&Paste never even worked, so the shared folder/drag&drop I don't think is my issue (both aren't working).

I'll try installing guest additions again but something tells me it won't make a difference. 

Would it matter that I'm on a work computer that is managed by my company (Windows 10 64bit) and has an encrypted harddrive? I'm a software engineer tho, so its a pretty good spec'd out laptop and I believe I have admin access on mostly everything. I don't see why something would be disabling me copy& paste ability on a VM as an Software Engineer.....

---

### Post by ping-wu on 2020-05-29
I also bumped into this problem; it "seems" that you can now only copy and paste (or drag and drop) files from the shared folder.

---

### Post by ajgreeny on 2020-05-29
> **ping-wu said:**
> I also bumped into this problem; it "seems" that you can now only copy and paste (or drag and drop) files from the shared folder.
That is precisely what I would have expected and why there is an option to choose the shared folder in the VM settings.
Did you expect something different?

---

### Post by asoftwrengrithink on 2020-05-29
> **ajgreeny said:**
> That is precisely what I would have expected and why there is an option to choose the shared folder in the VM settings.
Did you expect something different?

I'm not an avid user of VMs or Ubuntu but have used it before and decided to get back into it seem I have been using Linux at work now.

I precisely remember being able to copy & paste from my Windows Host to the Ubuntu VM terminal, for example.

I added the shared folder and was able to drag & drop a txt file there, but I don't see why they removed the feature of copy & pasting because the whole point is being able to copy from the Host machine into the terminal I would imagine.......

---

### Post by ajgreeny on 2020-05-29
Have you made sure that bidirectional is the setting in ***Shared clipboard*** and ***Drag & Drop*** from the General settings -> Advanced tab?

It is all working as I expect in my VMs.

---

### Post by ping-wu on 2020-05-30
From the VirtualBox forum, it seems that the copy and paste function is working in 6.1.8 now. This most recent version is not in the Focal repository yet.  Maybe wait another week?

---

