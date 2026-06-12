---
title: "mouse pausing in center of dual screen"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bacardiandwatermelon on 2012-03-02
Hey guys, tried searching but didn't find much. My mouse pauses when switching screen slowly, didn't have this issue with Oneric. Anyone had this issue/feature?

---

### Post by go7Ul1ai on 2012-03-02
This is a feature that was introduced in the Unity 5.2 update.

"Multi-monitor support
You will now see launchers on each of your monitor, and when you scroll across a monitor, you should feel some resistance in order to allow for you to use the launcher on that screen."

Source: [http://www.theorangenotebook.com/2012/01/unity-52-whats-new-and-call-for-testing.html](http://www.theorangenotebook.com/2012/01/unity-52-whats-new-and-call-for-testing.html)

---

### Post by Nick Payne on 2012-03-03
> This is a feature that was introduced in the Unity 5.2 update.

"Multi-monitor support
You will now see launchers on each of your monitor, and when you scroll across a monitor, you should feel some resistance in order to allow for you to use the launcher on that screen."
This is pointless when moving the mouse pointer from the left-hand to the right-hand monitor. The launcher doesn't appear but the pointer still hangs up. The pause is only useful when the mouse pointer is already on the RH screen.

---

### Post by skewty on 2012-03-05
Anyone have the bug# for this?

---

### Post by kancava on 2012-04-18
I had this same problem and discovered a bit of a workaround...

Go to CompizConfig Setttings Manager. It is not installed by default so you may have to install it first.

Open "Ubuntu Unity Plugin" in the "Desktop" section.

Go to the "Experimental" tab.

Change the "Edge Stop Velocity" option to 1.

It still stops the mouse if it's moving really slowly but it's much better than it was!

Hope that helps :)

---

### Post by kancava on 2012-04-19
I've just noticed there is now a "Sticky edges" switch in the Ubuntu "Displays" settings which can turn this off. I don't know whether it has just been added or if I just missed it before!

---

### Post by Scotchligo on 2012-04-26
> **kancava said:**
> I had this same problem and discovered a bit of a workaround...

Go to CompizConfig Setttings Manager. It is not installed by default so you may have to install it first.

Open "Ubuntu Unity Plugin" in the "Desktop" section.

Go to the "Experimental" tab.

Change the "Edge Stop Velocity" option to 1.

It still stops the mouse if it's moving really slowly but it's much better than it was!

Hope that helps :)

This works.  Thank you.

---

### Post by Ghil on 2012-04-26
Removing the sticky edges features completely stops the resistance.

---

