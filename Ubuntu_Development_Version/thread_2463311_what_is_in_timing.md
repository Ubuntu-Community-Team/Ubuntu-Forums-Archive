---
title: "what is in timing ?"
date: 2021-06-08
forum: Ubuntu Development Version
---

### Post by anneranch on 2021-06-08
AFTER clean install and TODAY's  update of latest 21. I am still curious why I am experiencing slower than molasses in winter boot. 
Fore example 
My  firmware EFI is set to display the FIRST screen during the boot 
-the screen  which allows direct access to EFI setup- to 5 seconds.
I do not have a stop watch but it is near 30 seconds before next screen - the grub menu - appears
grub is set to 10 second , before it runs selection - the one with asterisk attached. 
It does "timeout " correctly. 
Next comes series of screens - in about 5 seconds (!) intervals 
and if the OS selected  is optioned to  OUT  "no flash" I get progress output in abut 3 seconds before first real OS 
screen. This timing did not change from older OS version.

The desktop shows accessible folders in noticeable delay , then applications icons - again notable delay. 
Even executing standard applications - in "new window"  has noticeable delay. 

Now this  is something not worth writing home about, but the OS name selected is very fitting - when the next release runs normal speed t change the name / image to gazelle.

---

### Post by dddman on 2021-06-08
Hello

Is this a help request or a rant?  

You posted in general help but all I see is a rant.

If your moving back to windows don't forget to mark your thread as solved.

Have a nice day

---

### Post by ajgreeny on 2021-06-08
I assume by 21.1 as you mention in your post that you mean version 21.10 which has not been released yet and will not be until October this year.

At present it is very much a development version and not for general use; if you install it and run it as your working version you will have to accept many potential problems, some of which may turn out to be impossible to solve except by a reinstallation of a newer .iso image.

It is impossible to say why your boot process is slow but it may help if you show the output of ***systemd-analyze blame*** though it will be difficult to tell you these problems will not happen again; there are, after all, over 4 months to go before that version is finally teleased

---

### Post by ajgreeny on 2021-06-08
*Thread moved to **Ubuntu Development Version**.* which is more appropriate and a better fit.

---

### Post by grahammechanical on 2021-06-09
I understand that both Ubuntu 21.04 and 21.10 default to using a Wayland compositor in preferrence to the X-server. Any seeming delay in rendering of the screen after login could be down to differences between the way the X-server and Wayland compositors work.

I, myself have noticed that when I login to a Wayland session there is a delay in the appearance of icons in the launcher that is not there when I login to a X-server session.

I have also noticed that in order to reduce the time taken to get to a login screen services are still loading as I login and continue after login. My simple dual core CPU struggles to do so many things at once. Everything is relative. For timing to have any relevance there needs to be a comparison made.

Regards

---

### Post by anneranch on 2021-06-09
> **grahammechanical said:**
> I understand that both Ubuntu 21.04 and 21.10 default to using a Wayland compositor in preferrence to the X-server. Any seeming delay in rendering of the screen after login could be down to differences between the way the X-server and Wayland compositors work.

I, myself have noticed that when I login to a Wayland session there is a delay in the appearance of icons in the launcher that is not there when I login to a X-server session.

I have also noticed that in order to reduce the time taken to get to a login screen services are still loading as I login and continue after login. My simple dual core CPU struggles to do so many things at once. Everything is relative. For timing to have any relevance there needs to be a comparison made.

Regards
Finally a decent response.
To alleviate any misconception  about the purpose of my post  - rant or asking question- let me start over I ONE STEP AT THE TIME.

When I turn the power on - after plugging my PC in - I get FIRST screen containing 
motherboard vendors logo and 
few lines of text allowing me to access the firmware setup

That is set - in firmware setup - to timeout in 5 seconds.
( Has not changed from version 14 ) 

IT DOES NOT timeout in 5 seconds., but it takes over 30 seconds !

What that got to do with OS ?

It used ( 16 ) work as instructed.

PS Multi-core CPU seem to be challenge to latest Ubuntu version.(COMMENT)

---

### Post by ajgreeny on 2021-06-09
It would appear that all the delays you are seeing happen before Ubuntu has even started to boot from grub but is more related to your UEFI setup, though I'm not even sure about that so, as I asked you in my last post, please show us the output of command ***systemd-analyze blame*** and we might be able to help you more.

I still suspect that this may be a problem of the version you are using being very much in development and not yet released but the more info we have from the command I show the better able we should be to help.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by VMC on 2021-06-09
> **anneranch said:**
> ...

That is set - in firmware setup - to timeout in 5 seconds.
( Has not changed from version 14 ) 

IT DOES NOT timeout in 5 seconds., but it takes over 30 seconds !

What that got to do with OS ?

It used ( 16 ) work as instructed.

PS Multi-core CPU seem to be challenge to latest Ubuntu version.(COMMENT)

"What that got to do with OS ?" Your right, nothing to do with OS
"It used ( 16 ) work as instructed." Unsure what this means?
"PS Multi-core CPU seem to be challenge to latest Ubuntu version". Multi-core should not be affected. Mine isn't.

Do you see the seconds tick-off at the bottom of the screen? What does it show in the beginning; 30 and counting?

As far as Wayland is concerned, it takes my multi-core i5, 30 seconds for the left hand dock to fully populate. Not only that, but each program I open takes several seconds for it a appear on the dock. So I removed the dock.

Here is a bug report regarding Wayland and the dock . Please "me too" it.
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-dashtodock/+bug/1900907](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-dashtodock/+bug/1900907)

---

### Post by QIII on 2021-06-09
@anneranch

I would like to re-iterate that if you are running 21.10, Impish Idri, then you are running a ***development version*** that has not been released yet.  Development versions are fraught with problems and often broken while the developers test and recompile.  They are not intended for daily use and should only be used by those who are willing to take part in testing development.  Please calm down and take that into consideration.

If you want a stable version, the most recent LTS release is 20.04.

---

### Post by anneranch on 2021-06-10
This is unconfirmed rumor but it appears that UEFI setting for " hot keys access " (firmware) to setup timeout  on  boot  appears to be related to NUMBER OF BOOT SETTING 
If there is only ONE Setting  "ubuntu "  and the option is set 2 seconds it will take approximately 2 seconds  for boot process to go to the next screen. After  next hard drive - next boot option - is added the timeout appears to be around 4 seconds etc. same after next HDD is added - additional 2 seconds are added to the timeout. . 
Makes absolutely no sense , but that the way it works. 
I am too scared to update EFI firmware....

---

### Post by VMC on 2021-06-11
The above statement doesn't make much sense, especially "This is unconfirmed rumor" part.
What's the output of ```
sudo efibootmgr
```

Also I would agree for you to use the latest LSB branch.

---

