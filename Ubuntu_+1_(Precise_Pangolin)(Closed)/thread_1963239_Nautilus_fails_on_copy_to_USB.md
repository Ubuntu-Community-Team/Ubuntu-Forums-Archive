---
title: "Nautilus fails on copy to USB"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-04-22
When copying a file to USB stick, the progress dialog never closes.
The progress bar goes all the way to the end and the full size of the file IS copied but the dialog won't even manually close and the progress bar still shows on the launcher icon.

If I then "safely remove" the stick, the icon disappears from the launcher but the stick is still flashing like mad.

The desktop is then very unresponsive and if I try logging out or shutting down, I get a box saying nautilus is still trying to complete the file operation.

---

### Post by hakermania on 2012-04-22
Well, maybe nautilus is trying to complete the file operation. have you waited long enough (3-4 mins after the progressbar has gone to the end)?

---

### Post by sanderj on 2012-04-22
> **x-shaney-x said:**
> When copying a file to USB stick, the progress dialog never closes.
The progress bar goes all the way to the end and the full size of the file IS copied but the dialog won't even manually close and the progress bar still shows on the launcher icon.

If I then "safely remove" the stick, the icon disappears from the launcher but the stick is still flashing like mad.

The desktop is then very unresponsive and if I try logging out or shutting down, I get a box saying nautilus is still trying to complete the file operation.

Does a command line "cp" perform any better?

---

### Post by Antman on 2012-04-22
I have had this issue with the beta iso, but the problem has since been corrected on the more current builds. While testing Precise Pangolin (or any Ubuntu version), I never keep alpha or beta builds on my pc for too long; I always do periodic fresh installs from an updated [daily live iso]("http://cdimages.ubuntu.com/daily-live/") (helps me with lingering problems). 

Is your PC fully updated? Try testing this functionality with the current daily live iso (which is *virtually* final code now) and see if it works.

---

### Post by x-shaney-x on 2012-04-22
My current install is a beta 2, fully up to date.

It doesn't happen if I use "cp", only when using nautilus.
Regarding waiting, the first time it happened I had left it over half an hour.
The file sizes have varied from a few megabytes up to 1.2GB.

---

### Post by x-shaney-x on 2012-04-22
Installed from a daily iso this afternoon and before changing anything, installing anything or touching the default install in any way I tried copying a file to USB.

Tried several ways:

Right-click copy and past resulted in the mentioned issue.

Dragging from one window to another, both by left-click dragging and middle-click > drag > copy also gave the problem.

Using dual pane mode and dragging from one pane to another also gave the problem.

Interestingly, once the progress bar got stuck at the end, I tried copying another file and the first file then finished copying but the second one then stuck at the end.
Tried copying yet another file and the second one then finished and the third stuck.

When copying 2 files at the same time, the first one to finish does complete but the second one sticks.
If a file sticks and I copy a tiny file, such as a text file a few kb big, both files complete copying and copying tiny files on their own also complete the process.

---

### Post by lancest on 2012-04-22
Try Ext formated drive- if you want perfection.

---

### Post by x-shaney-x on 2012-04-22
I don't need perfection, just things working as they should would be enough :)

Just trying to work out if it is something only effecting me or not.
I have tried it with another USB stick tonight to check and it happened with that too.

Regarding Ext, I have been copying some films from my computer to USB to plug into the Xbox to watch on the main TV.
Doubt the Xbox will recognise Ext.

---

### Post by lancest on 2012-04-22
Using Fat USB drives has never been a perfect situation for me on Linux.

Hanging during copying is nothing new.
(same thing happened to me last week - it just stopped)

My 500 GB Hard Drive is formatted for Ext & it's very fast.
 
 An easy choice for performance- not universally compatible though.

---

### Post by Antman on 2012-04-22
As a test, I just got finished copying 6 video files totaling **6.7gb** to my 8gig Sandisk usb flash stick and it completed without a problem. The usb flash is formatted Fat32.

---

### Post by x-shaney-x on 2012-04-22
@ Antman

That would certainly suggest it is a problem my end, though I have no issues copying in Windows or Dolphin in Kubuntu 12.04.

I will try running nautilus in a terminal when copying to see if it highlights anything (I should have already thought of that though).

<EDIT>
Nautilus in terminal doesn't output anything.  Any idea of any logs anywhere I can check?

---

### Post by lancest on 2012-04-22
> **Antman said:**
> As a test, I just got finished copying 6 video files totaling **6.7gb** to my 8gig Sandisk usb flash stick and it completed without a problem. The usb flash is formatted Fat32.

Good news.

---

