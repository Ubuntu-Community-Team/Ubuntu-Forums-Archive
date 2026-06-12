---
title: "Kernel Updates - 8.04"
date: 2008-12-16
forum: System76 Support
---

### Post by theTOman on 2008-12-16
From 2-6-24.22 to 2-6-24.23 on 8.04.1, a LTS version!!!

(yes, a Long Time Support version - one that is suppose to be STABLE!)

Trouble... AGAIN!

This time, the nvidia driver is GONE!

I am really getting upset at these updates - WHY? WHY???

WHY are they pushing updates that mess-up a perfectly working system?

I am considering disabling updates FOREVER - I am fed-up with having to fight - with 3 machines - every time there is a kernel update...

Will anyone petition with me to send Ubuntu a request to STOP pushing kernel updates that break systems?

---

### Post by thomasaaron on 2008-12-16
Since we're corresponding via email on this one, I'll stick to providing email support. As your question here seems to be...

> Will anyone petition with me to send Ubuntu a request to STOP pushing kernel updates that break systems? 

---

### Post by jdb on 2008-12-16
[QUOTE=

Will anyone petition with me to send Ubuntu a request to STOP pushing kernel updates that break systems?[/QUOTE]

I have those kind of problems with the Daru2.
They pushed a kernel that broke power management.

I'd sign that petition.

jdb

---

### Post by albinootje on 2008-12-16
> **theTOman said:**
> From 2-6-24.22 to 2-6-24.23 on 8.04.1, a LTS version!!!

(yes, a Long Time Support version - one that is suppose to be STABLE!)

Trouble... AGAIN!

This time, the nvidia driver is GONE!

> 
Will anyone petition with me to send Ubuntu a request to STOP pushing kernel updates that break systems?

You might as well :

1) start a petition asking Nvidia company to open source their drivers with a license that is compatible with GPL, and therefore can be included with a kernel-release.

2) sudo apt-get install dkms
and see whether that helps

---

### Post by theTOman on 2008-12-17
Now, the strange thing is that I have 8.04 on two other machines: A Pangolin and a desktop (Acer). And the kernel updates never popped-up! So I went in Update Manager, forced a "Check"... No updates whatsoever!

Is it possible that the update was faulty and that they pulled it off as soon as they realized it...??

---

### Post by albinootje on 2008-12-17
> **theTOman said:**
> Now, the strange thing is that I have 8.04 on two other machines: A Pangolin and a desktop (Acer). And the kernel updates never popped-up! So I went in Update Manager, forced a "Check"... No updates whatsoever!

Just wondering. Did you use a 8.04 or 8.04.1 installation cdrom ?
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by theTOman on 2008-12-17
It seems very likely that this was a Canonical error...

There was another kernel update this morning... Same kernel too! But now, along with it, the "backports", the nvidia-glx-new, etc...

I applied it, rebooted and TADADA! It's fine!

I guess Canonical pushed the new kernel too soon yesterday morning and removed it as soon as they realized it. Because, yesterday evening, I checked for updates, both on my wife's Pangolin and on my Acer desktop (both running 8.04) and there was NO updates (and I did force a "Check" in the Update Manager to make sure...)

So, anyways, it's all good now. Thanks for putting up with my whining!

Have a great Holiday Season, Ubuntu Brothers & Sisters!!!

---

