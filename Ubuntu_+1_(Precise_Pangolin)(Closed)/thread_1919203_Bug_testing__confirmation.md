---
title: "Bug testing / confirmation"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-02-02
If an application is opened, but part of it is placed outside it's viewport, clicking  the app on the Launcher Bar won't auto-switch to that viewport.

Example: 
1.Open Gedit on viewport 2/1 (x,y). 
2.Move Gedit window down, enough to make its status bar be placed off the current viewport and inside viewport 2/2.
3.Switch to viewport 1/1
4.Click on Gedit's Launcher Bar icon. 

Behavior: Nothing happens
Expected Behavior: It should auto-switch to viewport 2/1, where Gedit (most of it!) is.

If anyone else confirms, I'll report and post the launchpad bug #id here.

Regards,
Effenberg

---

### Post by ventrical on 2012-02-02
Do you mean Unity 3D I presume?

edit .. If you mean "workspace switcher" you have to double click (gedit) in the launcher and it works.

edit .. also  it will not switch to that veiwport but the edge of the gedit screen will overlay 1/1 when you click it once in launcher.

so if thats a bug .. yes..

---

### Post by effenberg0x0 on 2012-02-02
> **ventrical said:**
> Do you mean Unity 3D I presume?

edit .. If you mean "workspace switcher" you have to double click (gedit) in the launcher and it works.

edit .. also  it will not switch to that veiwport but the edge of the gedit screen will overlay 1/1 when you click it once in launcher.

so if thats a bug .. yes..

3D, yes.
Hmm, not for me :(

---

### Post by balloons on 2012-02-02
I can't seem to duplicate this.. It's working as expected for me.

---

### Post by ventrical on 2012-02-02
> **effenberg0x0 said:**
> If an application is opened, but part of it is placed outside it's viewport, clicking  the app on the Launcher Bar won't auto-switch to that viewport.

Example: 
1.Open Gedit on viewport 2/1 (x,y). 
2.Move Gedit window down, enough to make its status bar be placed off the current viewport and inside viewport 2/2.
3.Switch to viewport 1/1
4.Click on Gedit's Launcher Bar icon. 

Behavior: Nothing happens
Expected Behavior: It should auto-switch to viewport 2/1, where Gedit (most of it!) is.

If anyone else confirms, I'll report and post the launchpad bug #id here.

Regards,
Effenberg


 This is my general setup .

---

### Post by kaldor on 2012-02-02
Confirmed here with the Unity 5.2 PPA.

---

### Post by ventrical on 2012-02-02
I tried 2X2 settings but no go with bug.

---

### Post by effenberg0x0 on 2012-02-02
It's weird. I have verified that 3 of my 5.2 installs have this bug and one hasn't. I guess I'll have to diff them.

---

### Post by cariboo on 2012-02-02
I can confirm the problem on the system I'm using at the moment. I don't have the problem on my netbook, but then all applications run in full screen mode, so they don't intrude into the next view port.

---

### Post by effenberg0x0 on 2012-02-02
Thanks Cariboo907

I have verified that I still get it on a clean install of Alpha 2, on more than 1 machine, so I'll proceed to a bug report.

Regards,
Effenberg

**EDIT: **Reported at [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/)**925761**

---

