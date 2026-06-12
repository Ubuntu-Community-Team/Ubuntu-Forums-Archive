---
title: "Why are nVIDIA drivers for Windows so H-U-G-E compared to Linux?"
date: 2009-10-18
forum: The Cafe
---

### Post by edin9 on 2009-10-18
Linux = 21.6 MB.  Windows Vista = 99.8 MB.  I know the Windows drivers cover DirectX as well but damn! In the past the Vista driver has been up to 120 MB +. What gives?

---

### Post by dragos240 on 2009-10-18
Perhaps it's because Linux uses dependencies. Windows software comes bundled with everything needed to make it work.

---

### Post by praveesh on 2009-10-18
Windows drivers has graphical user interface

---

### Post by deancasino on 2009-10-18
So strange this hasn't occurred to me before

---

### Post by edin9 on 2009-10-18
> **praveesh said:**
> Windows drivers has graphical user interface

 Ummm, so does Linux. It's called nvidia-settings.... 
EDIT; Do you mean a graphical installer?

---

### Post by Dr. C on 2009-10-19
It could be the size is needed to support HDCP in Windows.

---

### Post by RiceMonster on 2009-10-19
Check to see if you're just looking at just the kernel module or the utilities as well (such as nvidia settings)

> **dragos240 said:**
> Perhaps it's because Linux uses dependencies. Windows software comes bundled with everything needed to make it work.

I don't think that's the reason. It's a kernel module, so all it depends on is the kernel. Obviously you need the x server to make use of it as well.

---

### Post by Npl on 2009-10-19
on windows it comes with Direct3D, [PhysX software/driver]("http://en.wikipedia.org/wiki/PhysX") and additionally you have drivers for more models bundled in one (covers the models you have 2 seperate linux drivers for).

---

### Post by Skripka on 2009-10-19
> **RiceMonster said:**
> Check to see if you're just looking at just the kernel module or the utilities as well (such as nvidia settings)



I don't think that's the reason. It's a kernel module, so all it depends on is the kernel. Obviously you need the x server to make use of it as well.

Pacman sez that nvidia-utils eat up 33MB of installed space, Nvidia 185.** eats up 12MB installed space...

---

### Post by LowSky on 2009-10-19
I just check and I was suprised in the size differnce, but it thought it has to be the fact that Linux cannot utilize HDCP and DirectX.

But for comparison I took a look at ATI drivers is 113MB for Windows 7, and about 94MB for Linux  which isn't a huge difference..


Now I have no idea why Nvidia's is som much smaller, maybe because it isn't a graphic install?

---

### Post by Perfect Storm on 2009-10-19
> **Npl said:**
> on windows it comes with Direct3D, [PhysX software/driver]("http://en.wikipedia.org/wiki/PhysX") and additionally you have drivers for more models bundled in one (covers the models you have 2 seperate linux drivers for).

AFAIK, linux nvidia driver comes with physX. The game Shadowground lets the user use their physX (which my card support).

---

### Post by NCLI on 2009-10-19
> **LowSky said:**
> I just check and I was suprised in the size differnce, but it thought it has to be the fact that Linux cannot utilize HDCP and DirectX.

But for comparison I took a look at ATI drivers is 113MB for Windows 7, and about 94MB for Linux  which isn't a huge difference..


Now I have no idea why Nvidia's is som much smaller, maybe because it isn't a graphic install?
No way, a graphical installer doesn't take up more than 5MB, and that's extreme.

---

