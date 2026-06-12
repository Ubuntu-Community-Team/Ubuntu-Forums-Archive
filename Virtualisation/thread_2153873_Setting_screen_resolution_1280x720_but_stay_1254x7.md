---
title: "Setting screen resolution 1280x720 but stay 1254x759, why?"
date: 2013-06-12
forum: Virtualisation
---

### Post by cub on 2013-06-12
I would like to use Virtualbox to do tutorials and record these in 720p. It would be quite nice if my screen then was exactly 1280x720. According to the Virtualbox manual this is possible through doing (on the host):
```
VBoxManage setextradata global GUI/MaxGuestResolution 1280,720
```
and it sort of sets the window size however it end up as 1254x759. When I check the Display and resolution it also says 1254x759.

I have not been able to find anything about this issue and wonder how can make my Vbox 1280x720 without dragging the window around and hope for the best?

I have installed the guest addons and have set video memory to 128 MB.

---

### Post by cub on 2013-06-13
It seems the command didn't do anything after all. I tried to change to other settings but it was still 1254x759. So I can manually drag the window and narrow it down, but that seems like an messy way to do it.

---

