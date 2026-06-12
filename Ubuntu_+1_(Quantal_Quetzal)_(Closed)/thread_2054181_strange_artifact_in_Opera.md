---
title: "strange artifact in Opera"
date: 2012-09-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ronacc on 2012-09-06
I have been getting a strange artifact when I close a tab in opera , the tab window closes but the tab remains in the tab bar with hash marks , see SS . this has been happening for awhile now and occurs both with the current opera and opera-next ( the dev version ) . also both in unity and gnome-shell.

---

### Post by GreatDanton on 2012-09-06
I have the same problem. It was described here:  [http://ubuntuforums.org/showpost.php?p=12205837&postcount=3](http://ubuntuforums.org/showpost.php?p=12205837&postcount=3)
However I think there is still no solution for this.

Regards.

---

### Post by ronacc on 2012-09-06
thanks for the link I missed that thread .

---

### Post by VinDSL on 2012-09-06
Maybe it's theme related?!?!?!?

I'm running an older theme in Opera-Next, and have never had this prob.

I just opened & closed several tabs and... nothing.

Also, I run my tabs on the bottom of the browser.  Perhaps that's the difference.

---

### Post by ronacc on 2012-09-06
its definitely theme related . 1st I moved my tab bar to the bottom , no change , then I downloaded a couple of new themes and tried them , the artifact was gone so I changed back to opera unix skin ( the default ) and it was back so I tried opera standard and it had the artifact also , back to the new ones and its gone . so both the themes that come packaged with opera have the artifact but not ones that you install later . Maybe it has something to do with the way the included themes are installed , software center barfed during the install ( after it was completed ) .

---

### Post by GreatDanton on 2012-09-08
I just tried new themes, and yes the artifact is gone. But there is also no upper bar (where the close, minimize, maximize buttons should be), however there are new buttons on the right side. When I resize it to 50% of the screen I cannot move it around (unless I hold alt key), and that is pretty annoying. The standard Unix theme contains the upper bar, but it also contains artifact =).

Regards.

---

### Post by mc4man on 2012-09-08
> **GreatDanton said:**
> I just tried new themes, and yes the artifact is gone. But there is also no upper bar (where the close, minimize, maximize buttons should be), however there are new buttons on the right side. When I resize it to 50% of the screen I cannot move it around (unless I hold alt key), and that is pretty annoying. The standard Unix theme contains the upper bar, but it also contains artifact =).

Regards.
If you want your normal window deco back r. click up at the top > show border

---

### Post by GreatDanton on 2012-09-08
Thank you. That solved this problem.

---

### Post by PaulW2U on 2012-09-28
It seems that this problem only affects Ubuntu. 

Both Opera and Opera-Next display fine here using the default theme in Kubuntu, Lubuntu and Xubuntu.

---

### Post by PaulW2U on 2012-10-01
> **GreatDanton said:**
> Thank you. That solved this problem.

More of a work around really. :rolleyes:

Apparently this problem is known to the Opera developers, bug DSK-374856. They won't release Opera 12.10 until this problem has been fixed. 

See [http://my.opera.com/community/forums/topic.dml?id=1539692](http://my.opera.com/community/forums/topic.dml?id=1539692) on the Opera forums.

---

### Post by PaulW2U on 2012-10-11
This bug has still not been fixed in Opera but [http://my.opera.com/ruario/blog/2012/10/02/problems-running-12-10-on-12-10](http://my.opera.com/ruario/blog/2012/10/02/problems-running-12-10-on-12-10) shows that the Opera developers are aware of a number of problems affecting their 12.10 release. This bug might raise a number of queries on the forums next week  when Ubuntu 12.10 is released and users start upgrading.

Putting [opera:config#Dialog%20Toolkit](opera:config#Dialog%20Toolkit) in Opera's address bar and setting option 4 makes Opera use its own toolkit. A temporary work around until Opera fix their Gtk3 styling bug. No need to download alternative themes.

This configuration change should also fix the problem for Kubuntu/KDE users like myself who are finding that Opera 12.10 regularly crashes when attempting to save downloaded files.

---

### Post by VinDSL on 2012-10-11
> **PaulW2U said:**
> Putting [opera:config#Dialog%20Toolkit](opera:config#Dialog%20Toolkit) in Opera's address bar and setting option 4 makes Opera use its own toolkit.
I'm not sure, but I think it made Paul Ryan look better, too...  :)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-11-oct-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-oct-2012-3.png")[/INDENT]

---

