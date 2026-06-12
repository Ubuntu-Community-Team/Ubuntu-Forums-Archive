---
title: "Jaunty Desktop RC and EEEpc 900A"
date: 2009-04-20
forum: Testimonials &amp; Experiences
---

### Post by thechansen on 2009-04-20
I went with the standard desktop install of Jaunty and my experience was positive, MOSTLY.  Everything worked out of the box and it worked well.  Very quick and very stable.  Except possibly the third most important item on a netbook, the touchpad (keyboard and monitor being 1st and 2nd).  While yes we finally have access to the touchpad tab in the mouse pref window, the drives are crap.  On a device with such a tiny touch pad lifting your finger to continue scrolling the cursor is frequent.  The only problem with that is the cursor simply rockets across the screen once you reapply your finger to the pad, it's almost like using a Wacom tablet and less than ideal on a surface that small.  So it's either EasyPeasy 1 with the much hated tap to click, or Jaunty with the spastic mouse.  For now it's EP 1 because at least I can control the cursor.

Ideally I would like the touchpad to operate like my Macbook's: 
1) the cursor is independent from the location you place your meathook down and movement originates from where you place your finger. I suppose that isn't the most elegant way to phrase it but having used Apple laptops for about 7 years now, I'm kinda spoiled by the touchpad on them.  Surprisingly the eee touchpad is close except for the size and the way ubuntu handles certain aspects of it.
2) No tap to click,  I don't know who decided this is a good feature to include on laptops, I have never left it on for longer than 5 minutes.
3) two finger scroll.

For the record: running on an eee pc 900a, 4 gb best buy cheapy model.  Installed with ext4, journaled and no swap.  NBR was added later due to issues getting live USB to work (tried the RC and 2 different daily images).  Tried editing fdis, hal, and xorg, with zero success and then found [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/355326](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/355326)

as I said on the launchpad it seems we were using generic synaptics drivers before (8.10), from what I gathered by running xinput list and dmesg and now we are using elantech drivers that seem like they need a little more time in the oven.  If only we could combine the smoothness from synaptic drivers with the tap and multitouch controls from the elantech drivers....

---

### Post by wolfen69 on 2009-04-20
have you tried [Eeebuntu]("http://www.eeebuntu.org/")? it is made specifically for the eeepc. there is also [EasyPeasy]("http://www.geteasypeasy.com/"). good luck.

---

### Post by thechansen on 2009-04-20
First thing I did when I got the 900a was throw easy peasy on there :)  As of right now it comes down to who has the least broken touchpad (jumpy mouse vs tap to click annoyance), and Easy Peasy 1.0 is the best.  I'm driving across the country on the 27th, so having the use of the touchpad key (no room for using an external mouse). Jaunty just felt superior in speed and stability so I would prefer to use.

---

### Post by thechansen on 2009-04-20
further investigation has found that it is indeed a driver issue and that some arch linux users have solved the problem by patching the kernal with some new elantech drivers.  I need to reload jaunty to investigate.
[http://bbs.archlinux.org/viewtopic.php?id=66529](http://bbs.archlinux.org/viewtopic.php?id=66529)


EDIT:
Boom.  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33)  this has worked for me.  Basically I can run Jaunty now, and use the trackpad semi normally.  It's more of a bandage then a fix but, it seems to be working much much better for me.  Of course, by going this route, I no longer have access to touchpad settings in the mouse pref window, but I'm going to enable SHMconfig and see how that works.

---

### Post by NTolerance on 2009-04-25
The above posted fix works well with Jaunty final and the 900A touchpad.

---

