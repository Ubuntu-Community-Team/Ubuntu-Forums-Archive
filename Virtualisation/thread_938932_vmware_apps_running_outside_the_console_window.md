---
title: "vmware apps running outside the console window"
date: 2008-10-05
forum: Virtualisation
---

### Post by go_beep_yourself on 2008-10-05
I found this picture of apps running outside of the virtual machine. They appear to be running native in the host OS. Is this possible in Linux also? How can it be done?

[IMG]http://www.vmware.com/files/images/screens_fusion/f2/multimon_unity_twoscreens_lg.jpg[/IMG]

---

### Post by veloce on 2008-10-05
I'm almost tempted to go out and buy a mac.

---

### Post by fjgaude on 2008-10-05
I'm not sure what I'm looking at, double screens, two monitors, or something faked?

Here's my usual working screen with WinXP, apps, on top with access to Ubuntu by clicking the icons.

---

### Post by Greyed on 2008-10-05
It is possible with VBox, it is called seamless mode.  It only works for Windows guests.  I would surmise that something similar is possible with VMWare.

---

### Post by fjgaude on 2008-10-05
In VMware I haven't found what would be called seamless mode... what I showed is about it, and I like the way it is.

---

### Post by veloce on 2008-10-05
> **fjgaude said:**
> In VMware I haven't found what would be called seamless mode... what I showed is about it, and I like the way it is.

If you look at the original post you will notice that it is running on a mac.  So it is VMWare Fusion.  I hear that VMWare workstation has some of the features of fusion but don't know if it has this one.

VMware Server definitely doesn't!

---

### Post by go_beep_yourself on 2008-10-06
> **Greyed said:**
> It is possible with VBox, it is called seamless mode.  It only works for Windows guests.  I would surmise that something similar is possible with VMWare.

I do prefer VMWare Server 1.7 over 2.0 and Vbox. Any ideas how this can be done with VMWare?

---

### Post by lazyart on 2008-10-07
It's called Unity, and it's [on the way]("http://www.dabcc.com/article.aspx?id=6715") for Workstation.  Don't know if they will give it away in Server...

EDIT: Almost forgot... you can kinda do it [this way]("https://help.ubuntu.com/community/SeamlessVirtualization").  The windows act a bit quirky as I recall, but it does work.

---

### Post by go_beep_yourself on 2008-10-08
> **lazyart said:**
> It's called Unity, and it's [on the way]("http://www.dabcc.com/article.aspx?id=6715") for Workstation.  Don't know if they will give it away in Server...

EDIT: Almost forgot... you can kinda do it [this way]("https://help.ubuntu.com/community/SeamlessVirtualization").  The windows act a bit quirky as I recall, but it does work.

How can we know when it comes to Workstation?

---

### Post by bastafidli on 2008-10-09
What you are looking for is this
[URL="http://ubuntuforums.org/showthread.php?t=863567"]
http://ubuntuforums.org/showthread.php?t=863567[/URL]

---

### Post by go_beep_yourself on 2008-12-08
I got Unity to work with VMware Workstation 6.5!

[[IMG]http://img224.imageshack.us/img224/4778/unityum3.th.png[/IMG]](http://img224.imageshack.us/my.php?image=unityum3.png)

---

### Post by d2globalinc on 2008-12-11
We now no longer sell Windows as the primary OS on any new system, we use a customized Ubuntu Installation for all our clients, and then run Windows APPS under XP using VMware Workstation 6.5 w/ UNITY (Seamless Windows).

Workstation Original Video: [http://www.youtube.com/watch?v=1DWzuIreDGA](http://www.youtube.com/watch?v=1DWzuIreDGA)

Attached pictures of windows apps (Adobe CS4 Flash, Fireworks, Word 2003, Excel 2003, IE, Firefox for Windows) w/ Ubuntu Apps (Swiftweasel, etc)

Best of both worlds, until we no longer need windows ;)

Enjoy!

Shane Menshik
D2 GLOBAL INC
[http://www.d2global.com](http://www.d2global.com)

---

