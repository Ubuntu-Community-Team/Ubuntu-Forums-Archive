---
title: "Why am I limited to 800x600 resolution in AQEMU with Ubuntu distros?"
date: 2018-06-27
forum: Virtualisation
---

### Post by Rytron on 2018-06-27
Hi.

I use AQEMU. I install mostly Debian distros and I can get a comfortable resolution of 1024x768 - I can get higher but find that resolution fine.

Solus also worked without issue with 1024x768.

Whenever I try any Ubuntu distros - I can get many resolutions in the live session but once I install the distro - I'm stuck with 800x600 which is just too small.

Is there a remedy?

Thanks.

---

### Post by TheFu on 2018-06-28
I've not had this issue, but how much video RAM did you allocate to the VM and which video driver did you choose?

---

### Post by Rytron on 2018-06-29
> **TheFu said:**
> I've not had this issue, but how much video RAM did you allocate to the VM and which video driver did you choose?

Hi TheFu.

For all my vms I chose 'Default'. Here's the other options (attached image).

---

### Post by TheFu on 2018-06-29
Can't tell for sure and I don't use aqemu, I use virt-manager ... but QXL is the high-performance video driver to use.  If you use QXL, you'll need the correct "viewer". The "Display" tab might have something useful on it too?

On other virtual machines that display desktops, the amount of video ram for a text-only setup is 9MB.  For a desktop, 128MB is normal.  That was my thought with posting anything in this thread.

---

### Post by Rytron on 2018-06-29
I'm curious as to why Debian and Solus (and probably more distros are not stuck at 800*600 res after install).

Attached are the 3 display tab options.

---

### Post by TheFu on 2018-06-29
Sorry. No clue. 

I use virt-manager to setup VMs, but x2go when I need remote desktops. QXL remote desktops should perform very well, but I had issues with the keyboard mappings, probably a personal issue. Most of my VMs are non-GUI.  My desktop settings under virt-manager:


Tried to add an attachment with an image. Don't think it worked.

Hopefully someone who uses aqemu will see the post and help out.

---

### Post by Rytron on 2018-06-29
I used the qxl option as advised. As seen in the screenshot - there's loads of screen resolutions to choose. It defaulted to 1024x768. There's a weird issue with the cursor but that's no big deal.

---

### Post by TheFu on 2018-06-29
Seems solved to me. Please mark the thread as solved to help others in the community.

I suspect it is because many of the Ubuntu flavors demand direct GPU access and whatever the default emulated GPU provided under aqemu isn't up to that task.  That is just my guess. It might be completely wrong.

---

### Post by Rytron on 2018-06-30
The 'Cirrus CLGD 5446' & 'VMWare Video Card' options also gave many resolutions - without the mouse cursor issue. I will stick with Cirrus. :-)

---

