---
title: "Randomly changing wallpaper in Precise? No more?"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mmasroorali on 2012-04-06
Dear All,
In the 11.10, the screen saver was withdrawn. 

As an alternative, I liked the wallpapers which could be made to change at random. Now in Precise we got a new set of wallpapers, which was nice. But at the same time, it looks like that the feature to change the wallpaper at random has been withdrawn.

Is there a way I can make the wallpapers to change at random?

Any suggestion will be appreciated.

---

### Post by cariboo on 2012-04-06
There has never been a utility installed by default that changes wallpapers randomly. That being said, if you right click on the desktop, and select Change Desktop Background, you will see a bunch of wallpaper thumbnails, youl should see that one has a clock face on it, select that one, and it will cycle automagically through the available desktop backgrounds.

---

### Post by zombifier25 on 2012-04-06
You can manually do so yourself (create .xml slideshow, hack gsettings to use the slideshow, blabla) but your life would be easier if you use Wallch to change your wallpaper.
```
sudo apt-get install wallch
```

---

### Post by mmasroorali on 2012-04-06
> **zombifier25 said:**
> You can manually do so yourself (create .xml slideshow, hack gsettings to use the slideshow, blabla) but your life would be easier if you use Wallch to change your wallpaper.
```
sudo apt-get install wallch
```

Thanks. Wallch looked exciting at first, but it appears that you need to keep it running like some kind of player. 

I am going to resort to the method pointed out by cariboo907.

---

### Post by grahammechanical on 2012-04-06
Another way to do it is through System Settings>Appearence.

This feature has been available in 12.04 from the beginning. You will notice that when you select what I call the wallpaper slideshow the login screen background image reverts to the default Ubuntu background image.

We get a login background image that matches the desktop background image only if the desktop background image is static. That's life! 

Regards.

---

### Post by mmasroorali on 2012-04-06
> **cariboo907 said:**
> There has never been a utility installed by default that changes wallpapers randomly. That being said, if you right click on the desktop, and select Change Desktop Background, you will see a bunch of wallpaper thumbnails, youl should see that one has a clock face on it, select that one, and it will cycle automagically through the available desktop backgrounds.

I did setup with an image with clock face. Please see the attached image. But my desktop background remains static with this one. This remains like this even after several logouts/logins and reboots.

In 11.10, with the same setting, my desktop background used to change every ten minutes or something like that.

Am I missing something here?

---

### Post by eulu on 2012-04-06
wallch is pretty cool thanks for the tip... it crashes hard when trying to use the folder monitor feature, but they'll probably fix that eventually..

---

### Post by cariboo on 2012-04-06
> **mmasroorali said:**
> I did setup with an image with clock face. Please see the attached image. But my desktop background remains static with this one. This remains like this even after several logouts/logins and reboots.

In 11.10, with the same setting, my desktop background used to change every ten minutes or something like that.

Am I missing something here?

I tried that one, it didn't work for me either, I think I recall seeing a bug about it, I'll try to see if I can find it.

---

### Post by jbicha on 2012-04-06
The Ubuntu community wallpaper slideshow changes on the half-hour.

---

### Post by rburkartjo on 2012-04-07
since upgraded to 12.04 been using wallch when logged in unity and works great. i have it set to autostart. however in xfce it doesnt work and you have to use desktopnova.

---

### Post by mmasroorali on 2012-04-13
> **cariboo907 said:**
> I tried that one, it didn't work for me either, I think I recall seeing a bug about it, I'll try to see if I can find it.

It works, when another clock faced background is chosen.

Really strange.

---

### Post by curiousapprentice on 2012-04-14
Im using Wallch on Ubuntu 11.10. It might work on Ubuntu 12.04 too. Give it a try. apt://wallch

---

