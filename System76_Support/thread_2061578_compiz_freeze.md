---
title: "compiz freeze"
date: 2012-09-22
forum: System76 Support
---

### Post by even5 on 2012-09-22
I see a compiz freeze (compiz cpu goes to 100%) whenever I log in using the "ubuntu" (i.e., unity 3D) window manager selection, and open a file with an editor.   I usually do this using vi in an xterm window, but I've checked out gedit with the same result.  I think it would be interesting to use unity 3D, so I'd like to find a solution.

This is the sort of compiz freeze/hang where the mouse can be moved, but nothing can be selected, and the (kernel) is still reading keyboard keypresses.

I am using a lemur ultra (lemu4).  Since some people are using unity 3D with no problem, I have to believe it is something particular about my installation or my hardware.  I reinstalled ubuntu 12.04.1, and did only a small amount of reconfiguration  before testing for the freeze -- which it promptly did.  The changes I made (using ubuntu 2D) before testing were

     1)  I allowed system updates to get started
     2)  I swapped the ctl and caps-lock keys (for my habits)
     3)  I restored my home directory from before the reinstall -- tailoring shell functions 
           and setting command line editing via vi keys.
     4)  I added another user name to the system
     5)  I re-established /etc/hosts for convenience on the local network
     6)  I logged out and selected unity 3D ("ubuntu")
     7)  vi was still working, but unity 3D cube rotation features were not yet active -- I installed[INDENT]compizconfig-settings-manager, 
                     compiz-fusion-plugins-extra, 
                     compiz-fusion-plugins-main
[/INDENT]and enabled Viewport Switcher, and finally ran "compiz --replace" to finally enable the 3D cube rotation.

I then opened a file with vi in a terminal window, and compiz immediately  hung.

I believe one problem must be in compiz (which hangs), but there may be an underlying problem due to the graphics support on the lemu4 (since not everyone is having this problem).   I haven't figured out which driver that is, though I think it is from Intel; I would be happy to do some testing, but haven't managed to build compiz yet, let alone the possibly suspect graphics support.   Any suggestions to get this working will be appreciated.

I can recover from the freeze by using ctl-alt-F1 to get to tty1, where I can kill the hung compiz (kill -9 pid) and restart using a service request to lightdm.  That is less than satisfactory, particularly if I ever want to write to a disk file :-)

---

### Post by Ubun2to on 2012-09-24
What kernel do you have?
```
uname -a
```
There was an old problem with the Intel HD graphics drivers that caused random freezes.

---

### Post by even5 on 2012-09-24
> **Ubun2to said:**
> What kernel do you have?
```
uname -a
```There was an old problem with the Intel HD graphics drivers that caused random freezes.

$ uname -a
Linux Doriath 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by even5 on 2012-09-24
> **even5 said:**
> $ uname -a
Linux Doriath 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ uname -a
Linux Doriath 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I think the kernel was updated since I reinstalled; it was the 12.04.1 kernel at the time of the test.  According to the grub.cfg menu entry, it was 'Ubuntu, with Linux 3.2.0-29-generic'.

---

### Post by Ubun2to on 2012-09-24
> **even5 said:**
> $ uname -a
Linux Doriath 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I think the kernel was updated since I reinstalled; it was the 12.04.1 kernel at the time of the test.  According to the grub.cfg menu entry, it was 'Ubuntu, with Linux 3.2.0-29-generic'.

Well, the kernel is recent enough that the graphics drivers are not the problem.

---

### Post by isantop on 2012-09-26
> **even5 said:**
> $ uname -a
Linux Doriath 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I think the kernel was updated since I reinstalled; it was the 12.04.1 kernel at the time of the test.  According to the grub.cfg menu entry, it was 'Ubuntu, with Linux 3.2.0-29-generic'.

Can you try swapping Ctrl and Caps Lock back? We've seen numerous issues with this configuration, and I wouldn't put it past it to be causing your problem too.

---

### Post by even5 on 2012-09-27
> **isantop said:**
> Can you try swapping Ctrl and Caps Lock back? We've seen numerous issues with this configuration, and I wouldn't put it past it to be causing your problem too.

I turned off the caps-lock -- ctl key swap, and tried "Ubuntu" (Unity 3D) again.  I verified that the cube rotation was present.  I then used "vi" to try to open a file and immediately found compiz frozen (100% of a cpu).

---

### Post by isantop on 2012-09-27
> **even5 said:**
> I turned off the caps-lock -- ctl key swap, and tried "Ubuntu" (Unity 3D) again.  I verified that the cube rotation was present.  I then used "vi" to try to open a file and immediately found compiz frozen (100% of a cpu).

Okay, I think that your custom compiz settings are causing problems. Go ahead and run this command to reset compiz to defaults:

```
unity --reset
```

Unity isn't designed to work well with some plugins like the 3D cube. While changing the settings of default active plug-ins won't usually cause problems, activating or removing different plugins will often cause stability issues.

---

### Post by even5 on 2012-10-01
> **isantop said:**
> Okay, I think that your custom compiz settings are causing problems. Go ahead and run this command to reset compiz to defaults:

```
unity --reset
```Unity isn't designed to work well with some plugins like the 3D cube. While changing the settings of default active plug-ins won't usually cause problems, activating or removing different plugins will often cause stability issues.

That works in terms of having unity working, using an editor, and seeing no compiz freezes.  I had not understood that the desktop cube rotation was not reliable.

But I was curious, so I disabled the wall, then turned on desktop cube.  At this point I lost the keyboard keypresses to take me to other desktops, but the editor still worked.  No hang, no freeze.  I changed the desktop to 4 in a row, instead of 2x2.

Then I turned on desktop cube rotate.  Now I had keyboard keypresses taking me around the 4 desktops.  The editor (vi) still worked.  What's going on?  None of the previous problems.

Ah.  One new problem:  the auto-hide of the launcher on the left:  I didn't find any mouse movements that triggered the launcher to be shown again.  What is causing that?!

Well, for the moment, my original problem has disappeared.  Thanks for the "unity --reset" suggestion.

---

### Post by even5 on 2012-10-02
A set of system updates were loaded, and I rebooted.  Now I seem to have everything working -- including the launcher auto-hide.  I will cross my fingers and hope for the best :-)

---

