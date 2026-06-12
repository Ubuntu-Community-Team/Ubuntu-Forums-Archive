---
title: "Ubuntu server Raring Ringtail Digital Picture Frame"
date: 2013-08-21
forum: Server Platforms
---

### Post by jbenn1680 on 2013-08-21
Hello,

I am trying to set up a digital picture frame using ubuntu server version Raring Ringtail.  The laptop I have converted into the picture frame is a old Dell Latitude C840(unsure of spec atm) with only 256MB of Ram.  So far I've spent a few day's on this and cannot figure out the problem.  What I want the DPF (Digital Picture Frame) to do is boot as normal, auto login to user, automatically run feh (and not blank/turn off the screen), with the option for when i hit ESC or a button to boot to fluxbox.

However I can't seem to get past installing Xorg, I'm fairly new to Ubuntu (Linux in general).  I've tried following multiple guides via Google searching but none seem to work out.  The steps I've taken so far are to install
Xorg
Xinit
Xdm
Fluxbox
Feh
samba

at one point everything was working correctly but I messed up configuration somewhere and needed to do a reinstall and now I cannot replicate the working configuration that I had before which mainly consisted of editing the files located in /home/$USER/ i.e. bashrc, xinitrc & xsession.

I have a keyboard/mouse attached to the DPF for the moment but I'm mainly doing all this via ssh or webmin.  
Can anyone help me get this working correctly with minimal frustration?

---

### Post by jbenn1680 on 2013-08-23
I downgraded to 12.04 LTS server version as there was some unknown issue with raring & the laptop. So far I have installed the following packages & they are working correctly:

order of installation -

xorg > xdm > fluxbox > nodm

laptop boots & loads the fluxbox desktop as expected, now however I cannot seem to configure feh to load like I want it to.  Previously the xinitrc & xsession files were located in /home/jim, now they are not located there & I have no idea where the files are that I need to edit.

As stated in the previous post the previous .xinitrc contained:

```
xset -display :0 -dpms
xset -display :0 dpms 0 0 0
xset -display :0 s 0 0
xset -display :0 s noblank
```

As I do not want the screen to turn off or go blank.

.xsession contained:

```
feh -FZrzD30 /home/jim/Pictures
exec startfluxbox

```

which started the feh slideshow but if I hit the ESC or any key I think it started fluxbox.

any guidance/help would be appreciated....

---

