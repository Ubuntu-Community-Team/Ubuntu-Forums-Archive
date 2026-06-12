---
title: "Virtual Box the Windows not being drawn correctly"
date: 2012-08-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pt123 on 2012-08-21
As you can see from the screenshot, parts of the old windows are still there. It becomes impossible to tell which window you are clicking on.

[ATTACH]222997[/ATTACH]


Using Virtual box 4.1.18
12.10 alpha with the latest updates

---

### Post by Aenima99x on 2012-08-21
I'm using VirtualBox 4.2 with 12.10 and not seeing that issue.

---

### Post by pt123 on 2012-08-21
are you using any additional extensions?

---

### Post by Peter09 on 2012-08-22
I am getting this as well - for the past few weeks. I assumed that it is a problem with my VirtualBox install.

It appears that windows are not being refreshed or cleared properly. Sometimes OLD windows remain (even when the app has gone), often current windows are refreshed every second (slowly)  and the desktop is unusable.

No idea how to fix or debug this.

---

### Post by balloons on 2012-08-22
> **Peter09 said:**
> I am getting this as well - for the past few weeks. I assumed that it is a problem with my VirtualBox install.

It appears that windows are not being refreshed or cleared properly. Sometimes OLD windows remain (even when the app has gone), often current windows are refreshed every second (slowly)  and the desktop is unusable.

No idea how to fix or debug this.

This is a result of the drop of unity 2d.. Running unity with llvmpipe makes things nice again :-) Check out the ppa to see the WIP or wait a few weeks. Beta and post-beta should have resolved this stuff. Checking the 3d acceleration box on your VM may also help right now; provided your hardware handles it.

If you want to confirm, boot the alpha3 livecd.. It shouldn't suffer from these issues, as unity2d still existed.

---

### Post by pt123 on 2012-08-22
> **guitara said:**
>  Checking the 3d acceleration box on your VM may also help right now;
I have that turned on, but Virtualbox only allows for a maximum 128MB for Video Memory.

---

### Post by Peter09 on 2012-08-23
Yes,
and I am still struggling with installing Guest additions - 'no headers found error'

---

