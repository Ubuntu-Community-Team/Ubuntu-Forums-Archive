---
title: "Windows 98 crashed on virtual box"
date: 2007-06-27
forum: Virtualisation
---

### Post by purplearcanist on 2007-06-27
I just ran virtualbox, and used it to install windows 98.  It was fine until the second part of the installation, where it rebooted, and now when I start it up, it looks like this:

---

### Post by Seisen on 2007-06-27
It might not support what graphics card you have set for VirtualBox try changing that and see if it helps.

---

### Post by purplearcanist on 2007-06-27
> **Seisen said:**
> It might not support what graphics card you have set for VirtualBox try changing that and see if it helps.

Can someone please tell me how to change the graphics card on VirtualBox?

---

### Post by Seisen on 2007-06-27
I guess you can't change them I thought you could. Well I recommend going to the Virtual Box forums and asking this question. I'm sure somebody there has either had the same problem or know how to fix it.

[http://forums.virtualbox.org/]("http://forums.virtualbox.org/")

---

### Post by glombus on 2008-01-22
I had the same issue recently. 

I Increased the graphics memory allotted in VirtualBox and the issue resolved itself.

Just go into the settings for that virtual machine and drag the slider to the right.  I had to allocate 32MB, not sure why this resolved the issue, but since doing this my Win98 install has worked with no issues.

---

### Post by alraz on 2009-09-14
Try disabling VT-x/AMD-V

I had a very similar problem with windows 98 not booting after restarting for the second part of the install process

---

### Post by RealG187 on 2009-09-17
I have had issues running Windows 98 in Vbox as well...

---

