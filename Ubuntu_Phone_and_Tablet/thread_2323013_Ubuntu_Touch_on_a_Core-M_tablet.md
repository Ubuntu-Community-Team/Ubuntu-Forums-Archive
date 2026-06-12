---
title: "Ubuntu Touch on a Core-M tablet"
date: 2016-05-02
forum: Ubuntu Phone and Tablet
---

### Post by jicha on 2016-05-02
I have a tablet with keyboard dock Cube i7 Stylus. I use it as small laptop with Kubuntu.

To be able to also use it as a tablet, I tried to install Unity 8. I followed this guide: [URL="http://www.omgubuntu.co.uk/2016/04/ubuntu-16-04-unity-8-desktop-progress-video"]http://www.omgubuntu.co.uk/2016/04/ubuntu-16-04-unity-8-desktop-progress-video 
[/URL]
Now if I try to start the Unity 8 session the screen goes black and after a few seconds it returns back to SDDM. Could it be that I need to switch to LightDM to be able to boot into Unity 8? How can I find out, what's going on?

---

### Post by krusty8 on 2016-05-09
I think, yes you should probably switch to lightdm. 

As far as findind out whats going on, poke through logfiles in /var/log, ~/.cache and .xsession-errors .

Curious to see how far you get!

---

