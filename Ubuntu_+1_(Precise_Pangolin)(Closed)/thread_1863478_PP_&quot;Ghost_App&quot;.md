---
title: "PP &quot;Ghost App&quot;"
date: 2011-10-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-17
PP "Ghost App":

- Launch Expo
- While expo is showing your desktops, click on any app in your launcher. 

The app will not show in any viewport. Yet, it is running. You can pidof it, you can see it with alt+tab, etc. But you can't find it or switch to it.
(in fact, it is on the last viewport you had active as a ghost app: it steal focus, etc): you just won't see it.

To show it: Click on app in launcher again. Its options open in panel. Click any menu on panel.

Regards,
Effenberg

---

### Post by ventrical on 2011-10-18
Wow.. thats a weird one.

It will hide behind  open firefox. Not be there when you try to move the window but when you minimize ff it will pop-up out of nowhere.

---

### Post by ventrical on 2011-10-19
Ghost app Demo

[http://www.youtube.com/watch?v=yu9INAnIhgY](http://www.youtube.com/watch?v=yu9INAnIhgY)

---

### Post by effenberg0x0 on 2011-10-19
Thanks for confirming Ventrical. I will report it then. 

What do you think would be the best behavior:
- Launcher icons should be disabled when Expo is showing viewports.
- Launcher can be enabled, but applications must be able to recognize the selected Expo viewport as the active desktop.

---

### Post by ventrical on 2011-10-19
The second recommend. Actually the expo&options with compiz works excellent in Ocelot. Honestly, Unity is not really a bother to me anymore since they have fine-tuned it. It just keeps getting better and better :)

thanks.

---

### Post by mc4man on 2011-10-19
Don't see the ghost at all, any app opened is always on top.
(using latest compiz & unity-4.24
The 'issue' with focus is a little bit limiting - apps will either start in WS 1 if no Ws has an open window with focus, 
Or they always open in the Ws where a window does have focus
So the limiting thing is you can't 'focus' on a Desktop, only a window on a Desktop (no big deal really

The bigger issue here is that if you use Expo enough or in a certain way windows can slide in position, sometimes slightly off their current Desktop. That can affect raising a window from the launcher when back out of Expo

---

