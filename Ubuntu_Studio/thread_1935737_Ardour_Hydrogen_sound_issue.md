---
title: "Ardour Hydrogen sound issue"
date: 2012-03-04
forum: Ubuntu Studio
---

### Post by ocset on 2012-03-04
Hi

I am very new to Ardour and Hydrogen and have been trying to get them to work together. When I start recording in the Ardour, the beat from Hydrogen is heard clearly and gets recorded in the Ardour track successfully. 

When I play it back in Adour, the drum track is very quite and unclear.

Is there a setting somewhere in Ardour or Hydrogen that relates to the recording level between the two apps. All of the other tracks in Ardour are loud and clear

Thanks
O

---

### Post by jejeman on 2012-03-05
There are no special controls for recording beetwen apps.

In hydrogen you monitor/control output level, in Ardour you should see the level of inputsignal, and if you need you can increase it with slider.

Maybe you are sending from hydrogen signal both to playback and ardour, so it doubles during recording and you here it louder.

---

