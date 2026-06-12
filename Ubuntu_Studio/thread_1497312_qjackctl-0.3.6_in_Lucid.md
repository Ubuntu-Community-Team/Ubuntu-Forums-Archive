---
title: "qjackctl-0.3.6 in Lucid"
date: 2010-05-30
forum: Ubuntu Studio
---

### Post by Scott L on 2010-05-30
Ubuntu Studio 10.04 Lucid Lynx currently includes qjackctl-0.3.4 which includes two bugs; one rather problematic and the other just annoying.  Therefore, I have built qjackctl-0.3.6 in my PPA.   But first let's explain the bugs a bit.

** port rename bug **
The first bug is that qjackctl will ignore port name changes, and to me is rather impactful:
[https://bugs.launchpad.net/ubuntu/+source/qjackctl/+bug/490436](https://bugs.launchpad.net/ubuntu/+source/qjackctl/+bug/490436)

To witness the bug: start jack, start ardour, create a new track, rename the track in ardour, try to connect your input to renamed track via qjackctl connections...you can't, because the new track name is not there and the old one is.  Refresh will not help.

** no close buttons **
The second bug, and not quite as dramatic, is the loss of close buttons on child windows:
[https://bugs.launchpad.net/ubuntu/+source/qjackctl/+bug/447793](https://bugs.launchpad.net/ubuntu/+source/qjackctl/+bug/447793)

To witness this bug:  all child windows for qjackctl, i.e. connections, setup, etc, will only have two buttons, minimize and maximize.


If you would like to update qjackctl you can do so from my PPA.  You can find it here:  [https://launchpad.net/~slavender/+archive/lucid]("https://launchpad.net/%7Eslavender/+archive/lucid")

Add this to your sources:  ppa:slavender/lucid

Reload your sources and you should be able to update!

Please let me know if you have any questions or comments.

ScottL

P.S. I plan to get this into -backports and into -proposed as well so that when Ubuntu Studio Lucid is rebuilt for 10.04.1 it will be included.  Therefore, I may need help from users who use this update to comment in a bug report.

---

