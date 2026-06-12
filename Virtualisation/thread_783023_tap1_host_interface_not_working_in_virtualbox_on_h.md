---
title: "tap1 host interface not working in virtualbox on hardy"
date: 2008-05-05
forum: Virtualisation
---

### Post by MasterSushi on 2008-05-05
I used VirtualBox using a host interface connection called tap1 in 7.10.

I upgraded (actually a fresh install) over the weekend to Hardy (64 bit) and installed the latest 64 bit version of VirtualBox since I saw there is a new version. 

I setup the tap1 connection following these directions:

[https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")

I believe the tap1 connection is working (but I am not 100% sure how to verify it.)

For my VirtualBox connection I have selected host-interface and typed in tap1. However, OS boots up it is unable to get an IP Address. (it is XP)

I am not sure if the issue is the new VirtualBox version or if it is a Hardy issue.

Any assistance would be greatly appreciated.

---

### Post by seamuso on 2008-05-05
if you're using the pcnet adapter + host interface + vbox 1.6, you may be running into this ..

[Ubuntu 8.04 host interface broke after 1.6 upgrade](http://forums.virtualbox.org/viewtopic.php?t=6092)

---

### Post by MasterSushi on 2008-05-06
It looks like VirtualBox has corrected this issue in the SVN version. 1.6.1

Now I just need to wait for them to create a .deb of the latest build and I think this issue will be resolved for me.

[http://forums.virtualbox.org/viewtopic.php?t=6092]("http://forums.virtualbox.org/viewtopic.php?t=6092")

---

### Post by Calash on 2008-05-06
Loading the Intel drivers fixed it for me, but I am glad they are fixing it up in the next version.

---

### Post by MasterSushi on 2008-05-06
I thought I had tried the intel driver and didn't have any success. I just tried it again and now my tap1 connection is working. Interesting. Maybe I hadn't tried the intel adapter previously.

So, I have mine working now as well. Thanks for letting me know the intel adapter was working for you, I don't think I would have tried it since I thought I had already done that.

---

### Post by seamuso on 2008-05-06
I had to restart my networking a couple of times for the taps to start working. Funny thing, the pcnet fast III works correctly in my opensolaris install but the intel doesn't .. vica versa for my XP vm .. go figure ... :lolflag:

---

