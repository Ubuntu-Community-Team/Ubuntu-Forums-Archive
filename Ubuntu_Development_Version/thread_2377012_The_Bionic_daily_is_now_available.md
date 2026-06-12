---
title: "The Bionic daily is now available"
date: 2017-11-08
forum: Ubuntu Development Version
---

### Post by corradoventu on 2017-11-08
The Bionic daily is now available: [http://cdimage.ubuntu.com/ubuntu/daily-live/20171108/](http://cdimage.ubuntu.com/ubuntu/daily-live/20171108/)
edit: installed ... it works ok.

---

### Post by VMC on 2017-11-08
Didn't think it would appear until Jan. Now wait for xubuntu bionic daily.

---

### Post by flocculant on 2017-11-08
> **VMC said:**
> Didn't think it would appear until Jan. Now wait for xubuntu bionic daily.

I just enabled it - should build early AM UTC assuming no issues.

---

### Post by ajgreeny on 2017-11-08
I've just zsynced it from the site using the artful ISO as the seed file (62.4% was the same as artful so not a very large a download) and installed it in VBox-5.1.30.

All looking good at the moment though I have the same lack of transparency in the dock as others have seen; spoils the look but still works fine.

---

### Post by VMC on 2017-11-08
> **flocculant said:**
> I just enabled it - should build early AM UTC assuming no issues.
Great. Thanks!

---

### Post by ajgreeny on 2017-11-09
Having logged in to an xorg session last night I have now lost the option at the login screen to go back to a standard Ubuntu (wayland) session; there is no cog wheel to change the session type.
Anybody else seen this?

EDIT:
I did not say in post #4 that this installation is a VM in VBox 5.1.30 and I last night enabled 3D acceleration in the VM settings.
This is probably the reason behind the loss of the session change cog; I have now disabled 3D acceleration in the Display section of the VM settings, the cog reappeared, and am now back into a wayland session.
This change has also removed a glitch in the terminal display, which with 3D enabled, lost all response to the window, with neither keyboard or mouse having any effect on the terminal; all is now OK again.

---

### Post by ventrical on 2017-11-09
> **ajgreeny said:**
> Having logged in to an xorg session last night I have now lost the option at the login screen to go back to a standard Ubuntu (wayland) session; there is no cog wheel to change the session type.
Anybody else seen this?

EDIT:
I did not say in post #4 that this installation is a VM in VBox 5.1.30 and I last night enabled 3D acceleration in the VM settings.
This is probably the reason behind the loss of the session change cog; I have now disabled 3D acceleration in the Display section of the VM settings, the cog reappeared, and am now back into a wayland session.
This change has also removed a glitch in the terminal display, which with 3D enabled, lost all response to the window, with neither keyboard or mouse having any effect on the terminal; all is now OK again.

Thanks for sharing that. I always say a tester will get two different results when using a VM :)

---

### Post by ajgreeny on 2017-11-09
I normally never use 3D acceleration I'm my VMs, but always try to see if things work as they should but so far it always has a detrimental effect on at least one display property of my many and varied VMs.

---

### Post by linuxyogi on 2017-11-09
Just finished installing 18.04. Working great.

---

