---
title: "gdebi, cheese not working 12.04 beta 1"
date: 2012-03-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by azurehi on 2012-03-01
1.  installed gdebi to install download of google talk plugin.  use of gdebi triggers crash of gdebi and bug report.

2.  cheese webcam booth does Not take photos

---

### Post by boswbr25 on 2012-03-02
I am having the same problem in Lubuntu.  I get the error but the package ends up being installed.  Anyways, I think the following link is the fix for this problem.

[http://bazaar.launchpad.net/~gdebidevelopers/gdebi/trunk/revision/415](http://bazaar.launchpad.net/~gdebidevelopers/gdebi/trunk/revision/415)

This is the bug report for the topic if you weren't already brought there.

[https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/917802](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/917802)

My problem is that I have never really worked with a Beta too much before and I do not know how to use this revision now that I have it downloaded.  I know this must be a stupid problem.  Can anyone help?

---

### Post by mc4man on 2012-03-02
> **boswbr25 said:**
> I am having the same problem in Lubuntu.  I get the error but the package ends up being installed. 
My problem is that I have never really worked with a Beta too much before and I do not know how to use this revision now that I have it downloaded.?
You'd need to build & install the source, wouldn't bother 

There will be a gdebi update shortly & in most cases this just caused a crash/report without much or any user consequence.

---

### Post by alphacrucis2 on 2012-03-02
In cheese the countdown occurs but the photo never happens. The take a photo button remains "greyed out". Running cheese from the terminal kicks up this message when attempting to take a photo:

```
** CRITICAL **: cheese_main_window_finish_countdown_callback: assertion `self != NULL' failed
```

---

### Post by zeelink on 2012-03-04
cheese would start but freezez as soon as ca turns on and black screen

---

### Post by cariboo on 2012-03-04
Has anyone created a bug report about the problem with cheese?

---

### Post by alphacrucis2 on 2012-03-04
> **cariboo907 said:**
> Has anyone created a bug report about the problem with cheese?


Yep. There is a launchpad report. The upstream dev requested a backtrace which I believe has been provided. The problem mentioned in this thread by zeelink appears to be unrelated.

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/942238](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/942238)

---

### Post by cariboo on 2012-03-04
> **alphacrucis2 said:**
> Yep. There is a launchpad report. The upstream dev requested a backtrace which I believe has been provided. The problem mentioned in this thread by zeelink appears to be unrelated.

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/942238](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/942238)

Thanks for that, I looked at the thread again, and saw the bug report. Again, I shouldn't make comments until I've finished at least my second cup of coffee in the morning. :) :)

---

