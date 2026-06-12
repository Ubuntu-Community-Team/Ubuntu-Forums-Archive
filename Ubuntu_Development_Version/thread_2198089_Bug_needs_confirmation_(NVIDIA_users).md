---
title: "Bug needs confirmation (NVIDIA users)"
date: 2014-01-06
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-01-06
In this screenshot ([http://img4.picload.org/image/lgdpawp/2014_01_04_02_37.png](http://img4.picload.org/image/lgdpawp/2014_01_04_02_37.png)) the 2 buttons "Save Changes"/Reload and "Update Rule"/Cancel are merged. The bug seems to appear in every version that contains the new "Applications Profile" menu (but this one was tested with nvidia-settings 331.20-0ubuntu6 on LXDE.

I have posted this to the customer support of NVIDIA (even with this screenshot) and they say they can't reproduce this. If you test this it would also be important to know the desktop environment.

---

### Post by Ian_Worrall on 2014-01-07
I see the same, but hovering over each option shows that they are separate buttons.

---

### Post by cariboo on 2014-01-07
Using Unity here, I see the same as Ian_Worrall.

---

### Post by mc4man on 2014-01-07
On ubuntu session with ambiance it's fine here

---

### Post by Sworddragon on 2014-01-07
> **Ian_Worrall said:**
> I see the same, but hovering over each option shows that they are separate buttons.

Yes, on hovering they work as seperate buttons.


> **mc4man said:**
> On ubuntu session with ambiance it's fine here

Ah, your screenshots show why the NVIDIA customer support maybe can't reproduce this. But your screenshots also show that the buttons do have still different styles (which causes this bug on other themes).

---

### Post by mc4man on 2014-01-07
What do you mean by  "the buttons do have still different styles"?

---

### Post by Sworddragon on 2014-01-07
In your first screenshot compare "Save Changes"/Reload with Help/Quit :P

---

### Post by Cavsfan on 2014-01-07
Good here with Flashback Compiz.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-01-07110518.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-01-07110518.php")

---

### Post by Ian_Worrall on 2014-01-07
> **Cavsfan said:**
> Good here with Flashback Compiz.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-01-07110518.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-01-07110518.php")

Nope. You've got the same thing we're seeing.
Do what Sworddragon said above.

I wonder if the two windows are using different widget libraries?

---

### Post by mc4man on 2014-01-07
> **Ian_Worrall said:**
> 
I wonder if the two windows are using different widget libraries?
nvidia-settings source is available, maybe check out nvidia-settings-331.20/src/gtk+-2.x/

---

### Post by Sworddragon on 2014-01-07
Basically the "Save Changes"/Reload buttons are currently the same as "Add Rule", "Delete Rule", etc. but with the difference that their background layer (the "big button" - which is invisible on some themes as the screenshots here show) isn't horizontally stretched as above. So there are 3 possible solutions: Either the buttons should be the same like Help/Quit, the background layer could be stretched or simply all the these background layers could be removed.

---

### Post by Sworddragon on 2014-01-17
The customer support of NVIDIA couldn't repdroduce this so I have now created a ticket on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1270084](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1270084)

---

