---
title: "Problems Installing in Oracle VM VirtualBox"
date: 2019-08-09
forum: Virtualisation
---

### Post by RSmith9512 on 2019-08-09
Hi,

I'm new here and new to Linux in general. If this post is in the wrong place, I apologize. Anyway, I have been trying to install Linux distros in a virtual machine (Oracle VM VirtualBox) and I have been unsuccesful 100% of the time. Yeah, I know.. yikes, right? I have watched plenty of YouTube tutorials and I am doing everything exactly as they do, but still it does not work. I have the latest version of VirtualBox and the latest distro of Ubuntu. Any ideas as to what I am doing wrong? I'll provide an image of what I get after starting the virtual machine. That image of what appears to be a keyboard = human inside of a circle is all I ever get. Hitting any key inside of the vm does nothing.


 [ATTACH=CONFIG]283767[/ATTACH]

---

### Post by Dennis N on 2019-08-09
That's the beginning screen of the installer without the text content displaying. I've occasionally seen that too. Click inside the vm window and press F1 key and that may move it along.

---

### Post by wildmanne39 on 2019-08-09
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by guiverc on 2019-08-09
When you first see that keyboard-in-rectangle & person-in-circle icon, you can press a key (quickly) and a menu will show.  If you haven't already verified the download of the ISO, there is a menu item here to 'check disc for defects' (the disc it's talking about is your install media, or the ISO itself in virtualbox).  If it's invalid (ie. download was imperfect) you'll be wasting your time going further, so it's cheap insurance in my opinion.

---

### Post by lammert-nijhof on 2019-08-18
Do you run a 32-bit processor or 32-bits Windows? If not, remove the PAE/NX selection from the Processor Tab of the System definition.

---

