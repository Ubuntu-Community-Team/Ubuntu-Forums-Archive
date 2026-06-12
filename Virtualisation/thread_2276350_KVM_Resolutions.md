---
title: "KVM Resolutions"
date: 2015-05-01
forum: Virtualisation
---

### Post by motobeats on 2015-05-01
When I create a new KVM (have tried 14.04 and 15.04) using virt-install from an iso I only get a single display resolution (800x600) available (connecting with both RealVNC and NoMachine). Default video setting in the domain xml is cirrus. When I switch to vga (virsh edit (domain)) and restart, more resolution options appear. 

So I created a new KVM with --video=vga off the bat and the result was the same, only one resolution available. So I changed the domain setting to "cirrus" and now I have 6 settings.

Why does changing the video setting in the domain xml seem to result in more resolution settings?

---

### Post by Doug S on 2015-05-01
> **motobeats said:**
> Why does changing the video setting in the domain xml seem to result in more resolution settings?For me it doesn't. With Cirrus I always get 6 resolutions; I have never used vga before , but seem to get only 1; for vmvga (which is all I ever use) I get 23 screen resolutions.

By the way cirrus does not work work me, and never has. The [terminal window and some menus are all messed up]("http://ubuntuforums.org/showthread.php?t=2266245&highlight=cirrus+vmvga").

Edit: Correction: cirrus seems to work for me now. I still will not use it, because it doesn't offer the resolution I want.

---

### Post by motobeats on 2015-05-02
Wow, vmvga is the way to go. Way more selections including the one I was looking for (1920x1080).

EDIT: The above was after I changed the 15.04 KVM. I went back and made the same change to a 14.04 KVM install and in add to adding screen resolutions it corrected the poor quality of the display, specifically the nearly unreadable terminal window (as linked to in Doug S' post).

---

