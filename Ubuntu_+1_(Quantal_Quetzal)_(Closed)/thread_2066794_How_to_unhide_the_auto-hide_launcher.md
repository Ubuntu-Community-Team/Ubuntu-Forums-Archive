---
title: "How to unhide the auto-hide launcher?"
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sacridex on 2012-10-05
Hello,

with the new nvidia driver 304.51-0ubuntu1, the launcher wont appear, from autohide anymore. You have to hold "Super' to make it appear.

EDIT: The same happens on Ubuntu 12.04 too with that driver.

---

### Post by funicorn on 2012-10-05
Since upgrade to Unity 6.60, launcher cannot be unhidden anymore. I'm using Nvidia card. Anyone else suffers from this ? Any idea how to fix ?

---

### Post by alphacrucis2 on 2012-10-05
> **funicorn said:**
> Since upgrade to Unity 6.60, launcher cannot be unhidden anymore. I'm using Nvidia card. Anyone else suffers from this ? Any idea how to fix ?

I think the latest nvidia blob is the cause of this problem.

---

### Post by alphacrucis2 on 2012-10-05
> **sacridex said:**
> Hello,

with the new nvidia driver 304.51-0ubuntu1, the launcher wont appear, from autohide anymore. You have to hold "Super' to make it appear.

EDIT: The same happens on Ubuntu 12.04 too with that driver.

Yes. I encountered this issue after updating nvidia under 12.04 via xswat ppa.

---

### Post by funicorn on 2012-10-05
So you are suggesting  304.43 works fine. That's wired, since just yesterday the official repository pushed the newest nvidia-current 304.51. Why did they do that ?

---

### Post by cariboo on 2012-10-05
Merged similar threads.

---

### Post by mc4man on 2012-10-05
Well both the .48 & .51 ones are in the repos

Anyway this should return the unhiding of launcher with the .51
```

sudo nano  /etc/X11/xorg.conf
```

```
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "ConstrainCursor" "no"  
EndSection
```

c&p above, ctrl+o, enter, ctrl+x, restart

---

### Post by cariboo on 2012-10-05
Thanks mc4man, that worked for me.

---

### Post by Cavsfan on 2012-10-05
Not sure if I was affected. I had been using Classic Gnome installed from Software Center.
But, didn't want to take any chances so I did as **mc4man** suggested and Unity looks good not hiding the Unity bar.
Thanks :)

---

### Post by funicorn on 2012-10-05
So this means nvidia driver cannot get the actual size of the display. That's funny.

---

### Post by mc4man on 2012-10-05
> **funicorn said:**
> So this means nvidia driver cannot get the actual size of the display. That's funny.
Nothing to do with ^
> Option "ConstrainCursor" "boolean"

    When this option is enabled, the mouse cursor will be constrained to the region of the desktop that is visible within the union of all displays' panning domains in the current MetaMode. When it is disabled, it may be possible to move the cursor to regions of the X screen that are not visible on any display.

    Note that if this would make display's panning domain is inaccessible (in other words, if the union of all panning domains is disjoint), then the cursor will not be constrained, so that it is still possible to move the cursor to each display.

Default: on, if the X server supports it. The cursor will be constrained to the panning domain of each monitor, when possible.


The changelog does mention a bug fix for panning that possibly has created this which will no doubt be fixed

>  Fixed a bug that prevented panning from working correctly
      after a modeswitch on some X servers with support for
      cursor constraining.

---

### Post by alphacrucis2 on 2012-10-05
> **mc4man said:**
> Well both the .48 & .51 ones are in the repos

Anyway this should return the unhiding of launcher with the .51
```

sudo nano  /etc/X11/xorg.conf
```

```
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "ConstrainCursor" "no"  
EndSection
```

c&p above, ctrl+o, enter, ctrl+x, restart

Thanks mc4man. Adding

```
Option     "ConstrainCursor" "no"
```

to the xorg.conf Device section worked for me.

---

### Post by Prowlcat on 2012-10-05
Bug report #1060511 covers this.

---

### Post by 3vi1 on 2012-10-05
Thx Prowlcat.  I came here to see if anyone knew of an existing bug when I experienced the same.  I'll go mark it as affecting me right now.

Edit:  [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1060511](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1060511)

---

### Post by mc4man on 2012-10-06
current bug on is actually here - 
[https://bugs.launchpad.net/unity/+bug/1057000](https://bugs.launchpad.net/unity/+bug/1057000)

Fix released by for the moment reverting back to the .43

---

### Post by funicorn on 2012-10-06
> When it is disabled, it may be possible to move the cursor to regions of the X screen that are not visible on any display.
I have only one display and the visible region is the whole region of X screen. Hence it  doesn't matter this option is disabled or not, if xserver correctly recognizes X screen size. However  this options does matter now, I have good reason to suspect xserver fails to do that.

---

### Post by Prowlcat on 2012-10-08
This is now fixed with both .48 and .51, Unity comes out of hiding as it should.

---

### Post by Cavsfan on 2012-10-08
304.51 definitely works better on my system.  With 304.43 Compiz crashed at nearly every bootup. Had to logout and back it to fix it.
I uninstalled nvidia-current and installed nvidia-current-updates. It got an error and didn't install some dependant files.
Fixed that with Synaptic.  
:guitar:

---

### Post by funicorn on 2012-10-08
@Prolcat, do you mean the bug is fixed by NVIDIA or by Unity ? 

> **Prowlcat said:**
> This is now fixed with both .48 and .51, Unity comes out of hiding as it should.

---

### Post by Cavsfan on 2012-10-08
Wait a minute... I have been using Gnome Classic but, when I logged into Unity and had the bar hide, it still did not show up for me.
When I did a mouse over on the left just a line barely appeared, no Unity bar though. 
But, I am happy with Gnome classic and 304.51 works well with that.

If you wish to unhide the auto-hide Unity launcher I would not be quick to jump on 304.51.

---

### Post by mc4man on 2012-10-08
> **funicorn said:**
> @Prolcat, do you mean the bug is fixed by NVIDIA or by Unity ?

Nothing as changed or been 'fixed', anywhere.
There are 3 choices now
current (.43
updates (.51 - still breaks on auto-hide for those affected
experimental (.48

The only thing people should keep in mind - if switching it's better to do in synaptic & match nvidia-settings package to nvidia package

---

### Post by Cavsfan on 2012-10-08
+1 on using Synaptic. Neither version works better for the Unity launcher or Compiz.
I still have to logout sometimes a couple of times to get Compiz not to break at bootup.

Hopefully Nvidia will either offer another version or fix 304.51...

---

### Post by Bluebearbevis on 2012-10-09
Thank you everyone,

I was using the super button hoping for an nvidia update.  Didn't know it would be so simple to correct the problem myself after proper instruction from my peers.  Working great again on a System76 Pangolin Performance panp6.  Can I delete the backup file?

Richard

---

