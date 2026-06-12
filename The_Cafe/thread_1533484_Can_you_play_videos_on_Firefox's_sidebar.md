---
title: "Can you play videos on Firefox's sidebar?"
date: 2010-07-18
forum: The Cafe
---

### Post by lovinglinux on 2010-07-18
I need some help from as many Ubuntu and Windows users as possible.

I'm currently developing a Firefox extension that needs to play a video on the sidebar. It seems something is wrong with my Firefox version or my OS, since videos don't play in the sidebar.

So if you could make a test on your machine would help a lot. If you have Windows on a dual-boot, then testing on it would be also very helpful. I only have it on a VM.

First visit a web site with a video. It can be any type of video. Then bookmark the page. Then right-click on the bookmark, select "Properties" and then tick the option "Load this bookmark in the sidebar". Then click the bookmark again. The page will be loaded in the sidebar.

Please let me know if the video works for you and also specify:

[LIST]
[*]OS
[*]Firefox version
[*]Type of video
[*]Video card brand
[*]Desktop Environment (Gnome, KDE...)
[/LIST]

Thank you very much in advance.

---

### Post by doorknob60 on 2010-07-18
Woah I didn't know Firefox had a sidebar :O

And yes, it works.

OS: Arch Linux x86_64
Firefox version: 4.0b1
Type of Video: Youtube (Flash)

---

### Post by TheWeakSleep on 2010-07-18
Yes, it works :)
OS: Ubuntu 10.04
FF: 3.6.8pre
Video: Youtube (flash)

hope that helps!

---

### Post by lovinglinux on 2010-07-18
> **doorknob60 said:**
> Woah I didn't know Firefox had a sidebar :O

I can't live without it :)

> **doorknob60 said:**
> And yes, it works.

OS: Arch Linux x86_64
Firefox version: 4.0b1
Type of Video: Youtube (Flash)

> **TheWeakSleep said:**
> Yes, it works :)
OS: Ubuntu 10.04
FF: 3.6.8pre
Video: Youtube (flash)

hope that helps!

Thanks that helps a lot. Would you mind posting what video card brand you have and also if you are using Gnome, KDE or something else? I have added those to the list, so I can pinpoint the source of the problem (seems the problem is on my end).

Also could you test with a video that is not flash?

---

### Post by TheWeakSleep on 2010-07-18
First of all, I'm using GNOME. Second, I'm on my netbook at the moment so im using integrated graphics. Intel GMA 950 I think? also.. I can't even think of where to find non-flash video. point me in the right direction?:D

---

### Post by lovinglinux on 2010-07-18
> **TheWeakSleep said:**
> First of all, I'm using GNOME. Second, I'm on my netbook at the moment so im using integrated graphics. Intel GMA 950 I think? also.. I can't even think of where to find non-flash video. point me in the right direction?:D

Never mind. I figure it out. It seems NoScript blocks the content in the sidebar, but doesn't have the ability to add the placeholder, so you can't unblock the video. So it appears to be stuck.

Thanks a lot for your help.

---

### Post by TheWeakSleep on 2010-07-18
I'm glad you figured it out :D

---

