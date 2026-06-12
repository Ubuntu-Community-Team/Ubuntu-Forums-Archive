---
title: "Virtualbox vs VMware?  Whats lighter on the system?"
date: 2007-10-24
forum: Virtualisation
---

### Post by RichTJ99 on 2007-10-24
Hi,

I am looking to run some windows apps in Ubuntu.  Which one of these two will be easier on system resources & when the software isnt running, there is no footprint?

Thanks,
Rich

---

### Post by reza81 on 2007-10-24
Virtualbox is easyer to install than VMware. It got more features than VMware. & VMware costs a lot of mony! Virtualbox is free.

I say go with Virtualbox. ( & don't forget to checkout the seamless feature ;) )

---

### Post by PartisanEntity on 2007-10-24
VB is lighter on the system.

reza81: VMWare is free for personal use.

---

### Post by steve.horsley on 2007-10-24
VirtualBox is only free for personal use, too. But personal use includes using at work as long as you install it yourself and don't use it as a server to others - very reasonable, I thought.

---

### Post by n3tfury on 2007-10-24
> **reza81 said:**
> Virtualbox is easyer to install than VMware. It got more features than VMware. & VMware costs a lot of mony! Virtualbox is free.

I say go with Virtualbox. ( & don't forget to checkout the seamless feature ;) )

good job answering his question....


i agree with partisan though, virtualbox seems more response and lighter than vmware, although i have no hard data to back up that claim - only what i've tested on my system.

---

### Post by reza81 on 2007-10-24
I didn't know virtualbox was **only** free for personal use. Sorry, my bad!

---

### Post by Zipster90 on 2007-10-25
Virtualbox is a much smaller program, as well as a lot faster than VMware. 

I'm running Windows XP Pro on Virtualbox and I'm very happy with the speed.

I like to call it:

*I Can't Beleive It's Not Native! (TM)*

---

### Post by digitalbenji on 2007-10-25
VMWare Server is free, more mature than VirtualBox, and has a much simpler installation considering the level of complexity it offers right out of the box.  If you need to do special networking tasks, you will find that VMWare Server is much easier to use, and has a GUI for things that VirtualBox does not.  I found VBox to be buggy, and not fully mature.  Neither is light on resources, but I think VMWare is lighter personally, it certainly seems to be more responsive IMO.

---

### Post by steve.horsley on 2007-10-25
I must correct my earlier mail. VirtualBox is available in 2 versions. There is a full-featured one which is free for personal use but chargeable for commercial use, and this is the one I had in mind in my earlier mail. This is the version that is downloadable in .deb and .rpm formats.

A second fully free GPL version has a few desirable features like USB and rdesktop support missing. Off the top of my head, I think this is only downloadable in source code - presumably expecting to be incorporated into distros.

---

### Post by Shazaam on 2007-10-25
Each program has their own pros and cons. Try both to find one that works best for you.

Small tip:
When you allocate memory for your virtual machine you shouldn't allocate the same amount as your actual physical memory.
Example=
1gig physical, allocate 512 or less virtual.

I have even found that Win98 runs FASTER with only 128megs allocated and I have 2gigs physical memory installed. Strange.

---

### Post by sawjew on 2007-10-25
> **steve.horsley said:**
> 
A second fully free GPL version has a few desirable features like USB and rdesktop support missing. Off the top of my head, I think this is only downloadable in source code - presumably expecting to be incorporated into distros.

Virtualbox OSE is in the Gutsy repositories just ```
sudo apt-get install virtualbox-ose
```

---

