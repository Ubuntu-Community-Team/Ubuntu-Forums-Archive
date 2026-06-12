---
title: "Non-Free Virtual Box Available for 12.04"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-04-03
Appears to have been made available just today. That's all. Don't forget that we're using the PAE Kernel.

---

### Post by neu5eeCh on 2012-04-03
And don't forget. If you decide to use the non-free version, in one of those *Ubuntu-knows-best *moves that just makes a part-time geek want to shove his keyboard right up... never mind.

You'll have to download the *User Groups *app. It's not included in Unity/Ubuntu. From there, run users-admin and add yourself to lp, users, and vboxusers.

---

### Post by balloons on 2012-04-03
I'll bite :-) What does the non-free version offer? What am I missing for running vbox-ose?

---

### Post by jfernyhough on 2012-04-03
Is there any difference any more? I thought they'd done away with two versions and instead put the non-free content into the extension pack?

(

For those wondering, the Oracle version is here: [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

You can also add it as a software source: 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

)

---

### Post by jfernyhough on 2012-04-03
> **guitara said:**
> I'll bite :-) What does the non-free version offer? What am I missing for running vbox-ose?The extension pack adds stuff like USB2 support so you can connect devices directly to the VM (which can be handy). I think it has extra networking bits too? (as far as I know I only need the USB bits).

edit:
Description:  
  USB 2.0 Host Controller, VirtualBox RDP, PXE ROM with E1000 support.

---

### Post by neu5eeCh on 2012-04-03
> **jfernyhough said:**
> The extension pack adds stuff like USB2...

Exactly. I need the USB functionality for the scanner and microphone (even though the scanner now works on the linux side). It's still useful.

---

### Post by xyzzyman on 2012-04-03
> **VTPoet said:**
> And don't forget. If you decide to use the non-free version, in one of those *Ubuntu-knows-best *moves that just makes a part-time geek want to shove his keyboard right up... never mind.

You'll have to download the *User Groups *app. It's not included in Unity/Ubuntu. From there, run users-admin and add yourself to lp, users, and vboxusers.

VirtualBox non-free is one of the first ppa's I add and install on every ubuntu install and it's always set up vboxusers for me... I did have one install that kept losing it and I kept having to re-add the vboxusers group from the CLI but that install of 11.10 had alot of weird issues from me poking it too hard with my stick.

---

### Post by neu5eeCh on 2012-04-03
> **xyzzyman said:**
> VirtualBox non-free is one of the first ppa's I add and install on every ubuntu install and it's always set up vboxusers for me... I did have one install that kept losing it and I kept having to re-add the vboxusers group from the CLI but that install of 11.10 had alot of weird issues from me poking it too hard with my stick.

Which PPA do you use?

---

### Post by xyzzyman on 2012-04-03
> **VTPoet said:**
> Which PPA do you use?

Oh sorry. I keep using PPA & Repository as one in the same. I just have been adding the repository that's on [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) since 10.10 (Mostly on 11.04 and 11.10 though), and until 2 or 3 days ago when they silenty added precise, I was just pointing it to oneiric...

It definitely has been adding the vboxusers group, as it's there and my user account has been added to it, even on my fresh 12.04 that I installed late last week. And I know that it complains especially about USB devices if it isn't. I think it was probably an issue awhile ago that they've since resolved for the non-free version.

---

### Post by QIII on 2012-04-03
New Precise repo from VirtualBox works nice.  Updated source and updated package.  Update the guest additions and go.

All seems well.

---

