---
title: "Xubuntu won't let me change wallpaper"
date: 2014-04-01
forum: Ubuntu Development Version
---

### Post by frank18 on 2014-04-01
Hi guys: after i installed updates for Xubuntu 14.04 it wont let me change wallpaper!

---

### Post by sandyd on 2014-04-01
**Moved to Ubuntu+1**

---

### Post by frank18 on 2014-04-01
> **frank18 said:**
> Hi guys: after i installed updates for Xubuntu 14.04 it wont let me change wallpaper!

Here a screen shot of the desktop, i don't like the Mouse in the meddle, i liked better the desktop that came with beta1,
i try to get at least a solid color but  have no option,  i hate the Mouse in the center.

---

### Post by Toz on 2014-04-01
> Hi guys: after i installed updates for Xubuntu 14.04 it wont let me change wallpaper! 
How is it not letting you change the wallpaper? Did you change the "Folder" to a folder that has images in it?

---

### Post by egeezer on 2014-04-01
You could also click on the Color spinbox and it will give you a choice of vertical or horizontal gradient.  Choose the colors by clicking on the color blocks shown.  No mouse in any of those!

---

### Post by frank18 on 2014-04-02
> **egeezer said:**
> You could also click on the Color spinbox and it will give you a choice of vertical or horizontal gradient.  Choose the colors by clicking on the color blocks shown.  No mouse in any of those!

If you mean the solid color where you add color to it  i did try that but no avail,i'm not new to this, it must be some type of bug or something, this has never happend to me in any distros. Also i made a new ISO of Ubuntu14.04 Beta2 and is samething.

---

### Post by Elfy on 2014-04-02
the xfcewallpaper is a known issue [https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1297170](https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1297170)

if you're trying to change wallpaper on the livesession - [https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1282227](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1282227)

---

### Post by frank18 on 2014-04-02
> **Elfy said:**
> the xfcewallpaper is a known issue [https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1297170](https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1297170)

if you're trying to change wallpaper on the livesession - [https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1282227](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1282227)

Thanks Elfy; can you please give me specific code or instructions on how to change the OEM wallpaper, i like the color if i can get rid of the mouse icon in the meddle,, i checked the links and i see many bugs of it but i can't make nothing of it, thanks in advance

---

### Post by slickymaster on 2014-04-02
You can easily change your desktop backdrop by navigating to **Main Menu -> Settings Manager -> Desktop**, or alternatively, right clicking your desktop and selecting the **Desktop Settings...** option.
Once the Desktop settings dialog is open, the **Background** tab gives you the options for configuring the look of your desktop background. You can choose to use a single image or multiple images as wallpaper or you can use a color scheme.

To change the image just click the **Folder:** button and navigate to **/usr/share/xfce4/backdrops/** where you'll find a collection of images shipped with Trusty.

---

### Post by slickymaster on 2014-04-02
@frank18

Please bare in mind that you'll have to be running **xfdesktop4 - 4.11.4-1ubuntu2**.

You can see what version you're currently running opening a terminal window and issuing the following command:```
apt-cache policy xfdesktop4
```

---

### Post by frank18 on 2014-04-02
> **slickymaster said:**
> @frank18

Please bare in mind that you'll have to be running **xfdesktop4 - 4.11.4-1ubuntu2**.

You can see what version you're currently running opening a terminal window and issuing the following command:```
apt-cache policy xfdesktop4
```

This is the screen shot of my desktop ln the terminal.

---

### Post by frank18 on 2014-04-02
> **slickymaster said:**
> You can easily change your desktop backdrop by navigating to **Main Menu -> Settings Manager -> Desktop**, or alternatively, right clicking your desktop and selecting the **Desktop Settings...** option.
Once the Desktop settings dialog is open, the **Background** tab gives you the options for configuring the look of your desktop background. You can choose to use a single image or multiple images as wallpaper or you can use a color scheme.

To change the image just click the **Folder:** button and navigate to **/usr/share/xfce4/backdrops/** where you'll find a collection of images shipped with Trusty.

Sorry to say that when i click on folder button i only have Xfce , if you mean i can download a specific wallpaper then get it from the home/downloads but for that i need to download a wall paper from the web site, do you know where i can get a clean wall paper similar to the beta1 desktop,thanks

---

### Post by frank18 on 2014-04-02
> **frank18 said:**
> Sorry to say that when i click on folder button i only have Xfce , if you mean i can download a specific wallpaper then get it from the home/downloads but for that i need to download a wall paper from the web site, do you know where i can get a clean wall paper similar to the beta1 desktop,thanks


Well i solved my issue by downloading some wallpaper from the web site and the result is this.See atach.

---

