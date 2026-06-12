---
title: "Touchpad scrolling not working in windows with system scroll bars"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by treesurf on 2012-04-23
Somewhere in the midst of recent updates I have started having an issue with touchpad vertical scrolling.  In windows with the old style scrollbars (Chrome, OpenOffice, Adobe Reader, etc)vertical scrolling still works fine.  However, in windows with the system scrollbars (are they called "overlay scrollbars"?), such as Nautilus, vertical scrolling no longer works.

Anyone else having this problem?  Should I report this as a bug?

Hardware: Lenovo Ideapad Y550

---

### Post by mc4man on 2012-04-23
Possibly this bug - the degree affected seems to vary by actual hardware
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/983910](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/983910)

To test you could try downgrading xserver-xorg-input-synaptics to the 1.5.99.902-0ubuntu4 version

It may be in your /var/cache/apt/archives, if so maybe you can force a downgrade thru synaptic
or get here, pick arch under "Builds"
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu4](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu4)

(to downgrade on the .deb itself  use

sudo dpkg -i /path/to/package

Ex.
 sudo dpkg -i /home/doug/Downloads/xserver-xorg-input-synaptics_1.5.99.902-0ubuntu4_amd64.deb

---

### Post by treesurf on 2012-04-23
Thanks, I've added my comments to that bug.  If I have some time I'll give a try with the synpatics downgrade.

---

### Post by mc4man on 2012-04-23
It is worth doing the downgrade to actually see if this is your problem, I believe all in that bug have seen the prior version fix the issue.

Edit: just to note - the 5 version does improve coasting over the 4 version, so if it's worth having if not causing issue

---

### Post by dwhite on 2012-04-23
I had the same or similar problem with the overlay scrollbars and my touchpad (the scrollbars would appear as my cursor got near the edge of the window but would disappear before my cursor could move over them)  but with an update last week they started to work perfectly, I mentioned it in a post two days ago so it was a recent update that had the fix for me, I can't tell you what part of the update was the fix only that the overlay scrollbars are working now.

---

### Post by treesurf on 2012-04-23
That is a different issue, I think.  I can grab the handles of the scrollbars just fine with the cursor.  What is not working is the vertical scrolling feature of the touchpad itself.

---

