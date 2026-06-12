---
title: "Lightdm wallpaper switcher"
date: 2012-02-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sffvba[e0rt on 2012-02-04
Sorry if this is a obvious thing I am overlooking.  My log in wallpaper is still the default and not my wallpaper I selected once I am logged in (AFAIK the wallpaper is supposed to match each other).

Is user intervention required to make this happen and if, where?


Cheers
404

---

### Post by lolpenguin on 2012-02-04
It's not working for me either. Maybe it hasn't been implemented yet?

---

### Post by Harry33 on 2012-02-04
The easiest way and the best way in order to avoid it changing back after each update of LightDM is to rename your personal background image to warty-final-ubuntu.png.
Then copy (replacing the original one) it to this folder:
/usr/share/backgrounds/

---

### Post by sffvba[e0rt on 2012-02-04
> **Harry33 said:**
> The easiest way and the best way in order to avoid it changing back after each update of LightDM is to rename your personal background image to warty-final-ubuntu.png.
Then copy (replacing the original one) it to this folder:
/usr/share/backgrounds/

There are many ways of setting it, was just wondering why the supposed automated update that is totted to be in 12.04 right now wasn't working for me...


404

---

### Post by bluenova on 2012-02-04
It's working for me and has been for several days. I didn't activate it, it just works. Check the permissions for the image, I believe Other needs to be able to view it for lightdm to see it.

---

### Post by sffvba[e0rt on 2012-02-04
> **bluenova said:**
> It's working for me and has been for several days. I didn't activate it, it just works. Check the permissions for the image, I believe Other needs to be able to view it for lightdm to see it.

Gave other access and no change, thanks for the suggestion.


404

---

### Post by MacUntu on 2012-02-04
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934)

---

### Post by grahammechanical on 2012-02-04
As far as I can tell it only works on a static wallpaper selection. It does not work if the slide show is activated. We just select a background wallpaper and then it becomes the background for the LightDM log in screen.

Other users can set different background wallpapers and when they click on their username the background will quickly change.

Regards.

---

### Post by mc4man on 2012-02-04
There could be sveral reasons why a chosen image isn't shown, inc the linked report.
I've had no issue w/ any image placed in ~/Pictures though could create trouble on purpose
So if it seems stuffed up one could try - 

First open ~/Pictures & make sure the **actual** image being used/to be used is in there.

Then browse to ~/.cache/wallpapers & clear out any stored images

If ~/.cache/gnome-control-center exists clear it out though if it was me I'd outright delete the folder itself, don't think it's being used anymore - see screen, no longer there

Open up the 'Change Desktop ...', switch to any image from 'Wallpapers', after it loads then open 'Pictures Folder' from the dropdown & (re)select your desired image.

---

### Post by sffvba[e0rt on 2012-02-04
> **MacUntu said:**
> [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934)

Thanks MacUntu... I think you hit the nail on the head :)


404

---

