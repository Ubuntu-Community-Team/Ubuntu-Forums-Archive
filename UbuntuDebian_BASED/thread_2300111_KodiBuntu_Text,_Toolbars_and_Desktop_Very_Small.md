---
title: "KodiBuntu Text, Toolbars and Desktop Very Small"
date: 2015-10-23
forum: Ubuntu/Debian BASED
---

### Post by 7.62Gaust on 2015-10-23
Hello,  After doing a fresh install of KodiBuntu all the text and tool bars are extremely small.   The tool bars at the bottom of the screen, Google Chrome, and any other window are also very small and I can not read any text unless I'm very close to the TV. The computer is hooked up to a HD TV at 1920 x 1080 @ 60Hz. Is there a way to increase the overall size of the text and toolbars?  Please let me know if you need any further information. 

Kodibuntu: Fully upgraded
LG 55" HDTV 1920 x 1080 @ 60Hz
HP e9230f
Intel Core 2 Quad Core Q8400
8Gb DDR3 Ram
GeForce GT440

---

### Post by ajgreeny on 2015-10-23
In XFCE which I use in Xubuntu I can change the fonts DPI settings in the desktop appearance settings.  The default is 96-DPI in *ubuntu OSs and changing that to, for example 110, will enlarge fonts, but I don't know how to change toolbars other than in panel settings, and I have no idea how to do it on different DEs.

---

### Post by 7.62Gaust on 2015-10-23
I've tried looking for a way to change the DPI in the menu and in the Nvidia settings but have not found anything.  Another problem I am having is the mouse cursor flashes and disappears all the time. I doubt the two are related but if anyone knows a fix let me know.  Thanks!

---

### Post by joshwiker14 on 2015-10-23
Please verify the Resolution and dpi, using nvidia-settings, and post their values here.
I have attached a picture which should clearly show where to find these settings.

If the resolution is greater than your tv, the tv is probably scaling everything down, making everything look small.

---

### Post by 7.62Gaust on 2015-10-23
The resolution is 42x42 dpi, dimensions: 1920 x 1080 pixels, and the resolution in XServerDIsplayConfiguration is set to auto.  I tried to change the settings in the XServer, clicked apply, but nothing changed, and it stays at auto.

---

### Post by joshwiker14 on 2015-10-23
In this case, It seems the dpi setting is causing the problem. (probably set from the televisions edid, or just guessed)

In order to change the DPI settings for nvidia, you will have to use a xorg.conf file.
This command will generate a nvidia-compatible xorg.conf in /etc/X11/xorg.conf , and put in the option to ignore the dpi setting from the edid.
> sudo nvidia-xconfig --no-use-edid-dpi

However, you will have to manually put in the dpi you want to use. 
So fire up your favorite text-editor and open /etc/X11/xorg.conf as root:
for example:
> sudo nano /etc/X11/xorg.conf

And in the "Screen" section, insert
>     Option         "DPI" "96 x 96"

for example, here is an excerpt from mine:
> Section "Screen"
Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "DPI" "96 x 96"
    Option         "NoLogo" "True"
    Option         "UseEdidDpi" "False"

And if your using nano, use ctrl+x to save, type yes at the confirmation prompt, and press enter to confirm the file location.

And finally, to apply these settings, completely log out, and these new settings should be visible!

If you want more information about xorg.conf, its man page is an excellent resource.
[http://www.x.org/archive/X11R7.7/doc/man/man5/xorg.conf.5.xhtml](http://www.x.org/archive/X11R7.7/doc/man/man5/xorg.conf.5.xhtml)

There is a list of other available options for xorg.conf at [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-b.html), which includes options specific to nvidia's proprietary drivers.

---

### Post by 7.62Gaust on 2015-10-25
That fixed the desktop.  After trying the dpi at 96 x 96 I increased it to 120 x 120 and it's even better.  Thank you so much!

---

