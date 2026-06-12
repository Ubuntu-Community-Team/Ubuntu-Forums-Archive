---
title: "Virtual Guest Additions install issues on Ubuntu 18.04 LTS VB 6.0.14"
date: 2019-12-21
forum: Virtualisation
---

### Post by penright2 on 2019-12-21
VirtualBox 6.0.14 host is running on Windows 10. 
Ubuntu 18.04 LTS is the guest.

I can install Ubuntu from the CD. The issue starts when I try to make the clipboard work. After turning on the bidirectional on both clipboard and drag and drop I install the guest tools. When I install the X11 it says something needs to be installed and once all this is done, not sure which step, then the guest will not boot. Sorry I can be more specific, I thought I copied the screen messages, but now I cant find them. This is the second time. I wanted to ask real quick if there are any know issues. If nothing off the top of any one head, my next step is to wipe the VM. Start over, for the third time, and be more intentional in testing between steps and keeping messages. Also taking snapshots so once I find the broken point I can rewind for more tests.

Here is the promised information. Sorry I have to do screenshots because I can not Copy and Paste. :D
So then I install the missing file and the virtualbox-guest-x11. Then when I booted the VM will not respond to the mouse. I turned off bidirectional for the clipboard and it still did not work. I had to revert back to the snapshot and it works.

---

### Post by penright2 on 2019-12-21
Playing around I may have stumbled onto my issue. Before I mark this a the answer, someone might comment if it sounds right or did I just get lucky.
What seems to have fixed it was installing from the guest addition ISO.

First, I found a post that got me to the right spot  [http://download.virtualbox.org/virtualbox/6.0.14/](http://download.virtualbox.org/virtualbox/6.0.14/)

Also I had to mount it via the cdrom, allow the linux version of autorun to run. So far so good.

Most of the instructions was using apt-get to do the install and for me the ISO is what worked.

---

