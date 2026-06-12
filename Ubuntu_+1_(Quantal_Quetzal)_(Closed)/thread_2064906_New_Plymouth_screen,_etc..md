---
title: "New Plymouth screen, etc."
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sgage on 2012-09-30
With the latest updates, I picked up some new boot stuff. The grub menu is on a nice blue background, and instead of the traveling dots on a purple background, I'm getting a sort of pulsing version of the default Gnome wallpaper. Pretty nice! :KS

---

### Post by Stinger on 2012-09-30
Yes , Jeremy has been [updating the code]("https://code.launchpad.net/~ubuntu-gnome-dev") ;)

---

### Post by celluloid on 2012-09-30
> **Stinger said:**
> Yes , Jeremy has been [updating the code]("https://code.launchpad.net/~ubuntu-gnome-dev") ;)

Is it possible to get this stuff via PPA? I do not have the Gnombuntu distro installed, just installed gnome-shell over the top of standard.

---

### Post by jbicha on 2012-09-30
I didn't do the plymouth work; that was Everaldo and Tim. Thank them if you see them!

celluloid, you won't get exactly the same experience that way, but if you want the new plymouth theme, it's plymouth-theme-ubuntu-gnome-logo and plymouth-theme-ubuntu-gnome-text.

---

### Post by Starks on 2012-09-30
Is there a Gnobuntu meta package for Ubuntu?

It's ubuntu-gnome-desktop right?

---

### Post by Stinger on 2012-10-01
> **jbicha said:**
> I didn't do the plymouth work; that was Everaldo and Tim. Thank them if you see them!
Woopsie.. Credit goes where credit is due ;)
Thank's to Everaldo and Tim, good work. 
Could be an idea to add some sort of progress indicator too, you know, a spinner or line of dot's maybe.

BTW did any of you try [Bodhi]("http://www.bodhilinux.com/") ? It has a really cool plymouth theme, a moving cloud of leaves, a fresh breeze. Do yourselves a favor and try it. =P~

---

### Post by jbicha on 2012-10-01
I didn't think a spinner of a line of dots looked good overlaid on the wallpaper. Plus those dots are pretty useless on Ubuntu as they just indicate that something is happening, not that you're 33% done booting or anything. We already cover the "something is happening" by fading brighter and darker.

---

### Post by Stinger on 2012-10-01
@jbicha
I'll settle for that.
Just brainstorming ;)

---

### Post by Stinger on 2012-10-02
Have a look at this one:
**[Gnome System Startup Screens Designs]("http://worldofgnome.org/gnome-system-startup-screens-designs/")**

This could be cool to have as startup-screen, fits gdm and Gnome-Shell perfectly :D

---

### Post by x-shaney-x on 2012-10-02
I find it strange just looking at a background, even though it's pulsating it sort of looks like something is missing.
Trouble is, on ubuntu I have found the boot process has always been flaky, screen flipping between splash and black screen and on Intel the splash screen only pops up for a couple of seconds right at the end most of the time, which makes a progress bar useless.

I've been playing with fedora the past day or two and noticed such a difference, the splash appears directly after grub and stays there all the way to gdm.
But anyway, droning on a bit but I reckon it needs a logo at least?

---

### Post by Stinger on 2012-10-02
@x-shaney-x
Yeah.. I hate to admit it, but Fedora seems to have a much better grip on the graphics. 

> Trouble is, on ubuntu I have found the boot process has always been flaky, screen flipping between splash and black screen and on Intel the splash screen only pops up for a couple of seconds right at the end most of the time, which makes a progress bar useless.

I have exactly the same issues when booting, Radeon HD 4670.:-?

---

### Post by x-shaney-x on 2012-10-02
^lol  Are you related to the new unity shopping lens?  :o)

---

### Post by Mr.JJ on 2012-10-02
I did not yet get the new plymouth and grub themes. I wonder if it is added to the default repo or one of the ricotz repos. Anyone else do not see those changes, yet? 

On the otherhand, the existing plymouth works okay for me. There is still a split second flickering towards the end, but it stays on through out the process. (mobility) radeon HD 46something with the default drivers. I agree, fedora is better here and also faster (with systemd).

---

### Post by Stinger on 2012-10-02
@Mr.JJ
Are you using the [Ubuntu-Gnome-Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/") ? Else you won't get it ;)

---

### Post by Mr.JJ on 2012-10-02
> **Stinger said:**
> @Mr.JJ
Are you using the [Ubuntu-Gnome-Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/") ? Else you won't get it ;)

I am. Upgraded completely etc. Tried using the main/UK servers.

(Unless, doing dist-upgrade moves me back to the original. But I have ubuntu-gnome-desktop installed and updated and none of the unity* installed)

Edit: ```
ubuntu-gnome-default-settings is already the newest version.
ubuntu-gnome-desktop is already the newest version.  

```  I can manually install the themes, ```
plymouth-theme-ubuntu-logo is already the newest version. 
plymouth-theme-ubuntu-text is already the newest version. 
 The following NEW packages will be installed 
   plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text 
```There is something missing, for sure!

---

