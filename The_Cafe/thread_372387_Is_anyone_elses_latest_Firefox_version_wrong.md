---
title: "Is anyone elses latest Firefox version wrong?"
date: 2007-02-28
forum: The Cafe
---

### Post by v8YKxgHe on 2007-02-28
Hey,

I just got updates for Firefox, to update to 2.0.0.2 ... but when I went to Help->About I get this:

[IMG]http://img132.imageshack.us/img132/125/firefoxaboutfh7.png[/IMG]

It says both 2.0.0.2 and 2.0.0.1 ... anyone else got this??

 (didn't know where to post this, sorry if it wrong place)

---

### Post by flossgeek on 2007-02-28
Nothing to worry about...

---

### Post by Johan! on 2007-02-28
The about screen on my installation is different.

How did you install Firefox?

---

### Post by BLTicklemonster on 2007-02-28
I hate the "close tab" buttons on the newest version of firefox. Used to be it was always on the right hand side of the screen, now it's with the tab. I keep closing the wrong tabs. Is there a way to customize this to put it back to the old way? 

(OT, sorry)

---

### Post by yabbadabbadont on 2007-02-28
> **BLTicklemonster said:**
> I hate the "close tab" buttons on the newest version of firefox. Used to be it was always on the right hand side of the screen, now it's with the tab. I keep closing the wrong tabs. Is there a way to customize this to put it back to the old way? 

(OT, sorry)

Install Tab Mix Plus extension.  That, and single window mode are why I did.

---

### Post by OrangeCrate on 2007-02-28
^^, In **about:config**, look for **browser.tabs.closeButtons**. Change the value to 3. This value will give you a single close tab button at the right end of the tab bar, as it was in 1.5.

---

### Post by v8YKxgHe on 2007-02-28
Ahhhhh I know what it was. I was playing around with the "general.useragent.override" I think it was setting in "about:config" and I had set it back to "2.0.0.1" so that meant Firefox would always report as 2.0.0.1 and of course when it updated, the override useragent thingy would replace it with 2.0.0.1 instead of 2.0.0.2!

---

