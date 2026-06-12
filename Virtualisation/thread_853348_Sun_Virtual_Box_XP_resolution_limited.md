---
title: "Sun Virtual Box XP resolution limited"
date: 2008-07-08
forum: Virtualisation
---

### Post by kneewax on 2008-07-08
Hey Guys,

I've been using Vbox for about 6 months now.  After a reinstall of Ubuntu I installed the latest version of Vbox on my Ubuntu laptop (A Fujitsu-Siemens Amilo Pro v8010) and imported my old virtual machines from a backup.

Now I can only get 800 x 600 resolution out of XP Pro in the Vbox, when the same machine was displaying at 1024 x 768 in the older innotek version of the software. I have updated to the latest guest additions too.

Is anyone else having this problem?

ta

---

### Post by tighem on 2008-07-09
Try increasing the video memory in the VM and installing client additions if they are not already installed.

---

### Post by Masoris on 2008-07-10
That's a bug. Read this: [http://www.virtualbox.org/ticket/1689](http://www.virtualbox.org/ticket/1689)

---

### Post by kneewax on 2008-07-10
Thanks guys, yes the manual fix worked.  Interesting the manula says Vbox will not allow guest OSs to display larger than the host screen resolution.  Not sure this is true, I only wanted Vbox to display at the same resolution.

Either way the fix 

```

VBoxManage setextradata global GUI/MaxGuestResolution any

```

fixed it and allows any resolution to be selected.

---

