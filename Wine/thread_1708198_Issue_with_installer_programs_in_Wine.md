---
title: "Issue with installer programs in Wine"
date: 2011-03-16
forum: Wine
---

### Post by Clessy on 2011-03-16
Hi everyone. I got wine setup and it works on for single .exe files for simplistic programs.

Now i've checked the compatibility list before installing something and i'm still having an odd issue with a game called Ys Oath of Felgahna. The game is rated as platinum on compatibility.


The issue is when I go to install it. The install opens fine. However the options window for the installer is always behind the background wallpaper of the installer.

If I tab on wine It will show the 2 windows. However if i try to focus on the installer and not the background picture for the install it will show nothing on screen.

The buttons still work on my keyboard but im going through the installer completely blind which means I cant choose where its installing too. This is a huge issue for me as I only have a 8GB SSD so there is no room to install it on the internal drive. Im trying to install it to a 8GB sd card instead.

Any ideas guys?

Btw I made another one of these topics in general help, sorry I didn't look well enough that topic can be deleted.

---

### Post by kn0w-b1nary on 2011-03-16
What version of wine are you using?

It might help if you tell wine to create a virtual desktop with your screen dimensions.

---

### Post by Clessy on 2011-03-16
W/e the latest version of wine is in the repository for apt get.

I can just pull up the wine configure and run a virtual desktop?

Anyone off hand know the divisions this would be.

I use a net book using the default gnome ubuntu interface.

Whats the screen size of everything right of the menu bar on the left hand side and everything below the toolbar on the top of the screen?

1024x600.


[img]http://img.uptodown.net/screen/ubuntu/bigthumb/ubuntu-netbook-edition---1.jpeg.jpeg[/img]

That interface.

---

### Post by kn0w-b1nary on 2011-03-16
Wine>Configure Wine>Graphics then check the box: "Emulate a virtual desktop." Then insert the size of you desktop or smaller.

---

### Post by Clessy on 2011-03-16
Cool beans when I get home hopefully this helps me out.

Another unrelated issue. Is there anyway for me to mount a iso/cdi/ disk image type file under wine?

---

### Post by Tweak42 on 2011-03-16
> **Clessy said:**
> Cool beans when I get home hopefully this helps me out.

Another unrelated issue. Is there anyway for me to mount a iso/cdi/ disk image type file under wine?

You need to mount the image file to the file system (ex: /media/diskimage ) then the files will show up in that directory.  Then go into winecfg, "Drives" tab, and assign a drive letter to that path.

I know you can mount iso's (google mount iso linux), but I'm not sure about other formats.

---

### Post by Clessy on 2011-03-16
Some things about linux are such a pain in the *** while others are so great.

Using the file in a window mode allows the installer to work properly however the next issue I have is harder.

1) I need Japanese language support under wine for windows.

2) The installer gives me an error message. Since its in Japanese I without the Japanese language support I cant read it. However it looks like its saying the selectable drive im using is now a choice.

( Issue number 2 solved. I got it mounted by using wine config. Now how the **** do I run anything off it. I get segmentation error! )

I was wondering is the reason its saying this is because im trying to install to a usb drive which isnt part of wines virtual OS. 

Is there a way to mount that whole usb drive as sd card under wines virtual OS. If not I might have to bite the bullet and go back to windows due to me simply not having enough space on the disk to use ubuntu.

Thanks guys.

---

### Post by Dlambert on 2011-03-17
Copy the contents, if its possible.

---

### Post by Clessy on 2011-03-17
> **Dlambert said:**
> Copy the contents, if its possible.
I've already got the installer to work and I installed it to the sd card. I used wineconfig to make the SD card as another drive.

Whenever I try to run anything off the sd card it doesnt work.

---

### Post by Dlambert on 2011-03-25
SD cards are generally slow, i would never attempt to install anything off an Sd

---

