---
title: "Exporting animations from Pencil animation program"
date: 2009-04-30
forum: Ubuntu Studio
---

### Post by higashi on 2009-04-30
I tried to use Pencil in Intrepid, but it was very buggy. After my upgrade to jaunty, i was pleased to see that it was working perfectly fine.

I did a little test animation and everything was going well... that is, until i tried to export it.

First, i tried as .mov . That didn't work. The dialog box came up, i clicked ok, and then it closed. I got no file saved on my computer.

Next, i tried .swf , This time, it just closed. didnt save anything. it was just gone.

.mov and .swf seem to be the only options i have since i want to have sounds in my animations, so i wouldnt be able to save them as jpeg or anything.

Is there any way to fix this problem?

---

### Post by Stochastic on 2009-04-30
Both of these issues have been reported on both Launchpad.net and Pencil's sourceforge bug tracker:

SWF: [https://bugs.launchpad.net/ubuntu/+source/pencil/+bug/351880](https://bugs.launchpad.net/ubuntu/+source/pencil/+bug/351880)
[http://sourceforge.net/tracker/index.php?func=detail&aid=2722411&group_id=155770&atid=797133](http://sourceforge.net/tracker/index.php?func=detail&aid=2722411&group_id=155770&atid=797133)

MOV: [https://bugs.launchpad.net/ubuntu/+source/pencil/+bug/351868](https://bugs.launchpad.net/ubuntu/+source/pencil/+bug/351868)
[http://sourceforge.net/tracker/index.php?func=detail&aid=2722437&group_id=155770&atid=797133](http://sourceforge.net/tracker/index.php?func=detail&aid=2722437&group_id=155770&atid=797133)

It was because of these bugs that Pencil was not included into Ubuntu Studio's Graphics meta package.  It's a shame because it's a quality program.

Theoretically, you could export the animation to a series of still images then put them back together with another program like stopmotion.  Here's a thread that details some of those possible apps: [http://ubuntuforums.org/showthread.php?t=1054541](http://ubuntuforums.org/showthread.php?t=1054541)  Though that's quite a bit of work to export your animation.

---

### Post by higashi on 2009-05-05
Thank you.
I hope pencil is fixed soon. It really is an amazing program

---

### Post by kenagcaoili on 2012-02-11
Hopefully this helps somebody.

Bug still exists.

Pencil 0.4.4b

Export as image sequence.

Import to OpenShot as image sequence.
Export to whatever you want.

---

