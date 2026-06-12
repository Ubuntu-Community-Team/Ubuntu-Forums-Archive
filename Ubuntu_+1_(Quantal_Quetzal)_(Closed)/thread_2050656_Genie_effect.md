---
title: "Genie effect?"
date: 2012-08-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by x-shaney-x on 2012-08-31
I was playing around with the daily today and one thing I noticed was an OS X style "Genie" effect when restoring a minimized app.
I know this has been in compiz forever but I'm suprised to see it in Unity.
Is this a mistake or new behaviour?  If new, why only on restore and not on minimize?
And is it likely to cause problems with Apple?

---

### Post by dino99 on 2012-08-31
Does not know what it is, so a screenshot is welcomed

---

### Post by mc4man on 2012-08-31
Mistake?, who knows.
When this bug was being fixed whoever wrote the commit, (Ugo Riboni) set the default for UnMinimize Animation to 
```
+            <default>
+              <value>animation:Magic Lamp</value>
+            </default>
```

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1036739](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1036739)

Maybe that's what he had, dunno

---

### Post by GreatDanton on 2012-08-31
I noticed the same thing, but since I'd like to have responsive and very fast system I disabled that effect.

---

### Post by GreatDanton on 2012-09-01
@dino99: look at this link for screenshot and also animation: [http://www.webupd8.org/2012/09/unity-640-lands-in-ubuntu-quantal.html?m=1](http://www.webupd8.org/2012/09/unity-640-lands-in-ubuntu-quantal.html?m=1)

Regards.

---

### Post by thotz on 2012-09-01
I don't like it :(

---

### Post by x-shaney-x on 2012-09-04
I never had email notifications from this thread so didn't realise anyone had replied.
As said above, the screen shot and gif of the effect can be seen in that webupd8 article.

I don't like it much either, especially when it looks so out of place.
Minimize and restore should have the same effect and I hope it is just a simple error.

---

### Post by mc4man on 2012-09-04
Was noticed (how could it not be..) & fixed though not yet released
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1040455](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1040455)

---

