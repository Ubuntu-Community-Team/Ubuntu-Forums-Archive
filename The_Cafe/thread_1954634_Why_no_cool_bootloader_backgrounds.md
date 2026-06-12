---
title: "Why no cool bootloader backgrounds?"
date: 2012-04-08
forum: The Cafe
---

### Post by Skaperen on 2012-04-08
Why doesn't Ubuntu use cool background images at the bootloader phase?

---

### Post by drs305 on 2012-04-08
The Ubuntu team does modify Grub 2 slightly for Ubuntu, but I suppose you would have to ask the developers why they didn't include a splash image.

Of course, if Ubuntu is your only OS by default you wouldn't see the Grub menu during boot anyway.

The good news is that with the latest versions of Grub 2 it is pretty easy to add a background image of your choosing. Here is a link to a guide I wrote on how to do it:
[Grub Background - Simple Drag & Drop]("http://ubuntuforums.org/showthread.php?t=1718521")

---

### Post by roelforg on 2012-04-08
Short way:
Drop a jpg with the 1024x768 size
run
```

sudo update-grub

```
and it should work, it does for me.

---

### Post by Skaperen on 2012-04-09
> **roelforg said:**
> Short way:
Drop a jpg with the 1024x768 size
run
```

sudo update-grub

```and it should work, it does for me.
Drop it?  In /boot or /boot/grub?  A particular name?

1024x768?  I though the BIOS default video size was 640x480.

---

### Post by Random_Dude on 2012-04-09
> **drs305 said:**
> 
The good news is that with the latest versions of Grub 2 it is pretty easy to add a background image of your choosing. Here is a link to a guide I wrote on how to do it:
[Grub Background - Simple Drag & Drop]("http://ubuntuforums.org/showthread.php?t=1718521")

I never thought about changing the background of Grub, but I tried just to see.
Worked like a charm. Thanks. ;)

---

### Post by drs305 on 2012-04-09
> **Skaperen said:**
> Drop it?  In /boot or /boot/grub?  A particular name?

1024x768?  I though the BIOS default video size was 640x480.

See the link I provided for the details.

---

### Post by grahammechanical on 2012-04-09
If you search the Ubuntu Software Centre for grub2-splashimages, you will find some background images that can be used a background images for Grub.

Whether you will class them as cool or not I cannot say. Although there is a winter scene among them. 

I know that Ubuntu provides a background image for the login screen and wallpaper images. And people moan.

Which just goes to show, that as you can't please everyone, you'd better please yourself.

Regards.

---

### Post by Artemis3 on 2012-04-09
I believe the reason is they didn't like the aspect ratio change in some monitors (eg 640x480 stretched over a 16:9) screen. They have things in place not just for the grub menu (which is seldom seen when there is only 1 OS), but also the loading screen... A shame really, Microsoft doesn't care their windows logo gets stretched or not (but then you can use different backgrounds at different stages, perhaps something with horizontal lines or such).

[quote="Colin Watson"]we wanted to have an Ubuntu logo as well, but there are problems with different aspect ratios between the boot loader and the real system[/quote] See: [http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg](http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg)

---

