---
title: "Random good news for ubuntu."
date: 2008-05-10
forum: The Cafe
---

### Post by Twitch6000 on 2008-05-10
Well one of the people I subscribed to on youtube,got his friend a windows power user to try ubuntu out.Just for some basic everyday things.It went pretty much all well and showed what could be fixed in wine and ubuntu itself.
Watch part one then2,3,and 4.
Link-[http://youtube.com/watch?v=2r_IpeIVq2w&feature=user](http://youtube.com/watch?v=2r_IpeIVq2w&feature=user)

---

### Post by Mr. Picklesworth on 2008-05-10
Gyaargh! Why is Screen & Graphics Still There?!
That's a serious usability issue, and I keep seeing people use it. The program is hidden for a reason. Its functionality has been (hopefully) replaced by the new Screen Resolution preferences. (Which should probably be renamed).

I hope xrandr starts working 99.9% for Intrepid. That would be fun :)


Interesting that he didn't notice Places -> Network in part 2...

I'm thinking a lot of this can be solved by a visible, unobtrusive introduction system. This video is really helpful for showing me what it should contain!

---

### Post by eragon100 on 2008-05-10
It hasn't been replaced by screen resoltion preferences, you can't select a monitor driver there.

After I had installed nvidia driver with restricted I had to select a driver in screens and graphics, because it has been set to generic monitor by restricted. None of my 3d games (nexuiz, northland, savage, ET:QW, and tons more) would work fullscreen, I got an import not supported error from my monitor. If screens and graphics wouldn't exist, I would be forced to still use Gutsy because I wouldn't be able to play games.

So I hope they either solve the nvidia driver installation problem or keep it accesible from the terminal :popcorn:

---

### Post by Mr. Picklesworth on 2008-05-10
I agree, that is very true. I suppose it would help if Screen Resolution was renamed Screens (or anything to reflect how it does more than set the resolution), and Screens & Graphics became "Advanced Screens & Graphics" to reflect that there is another, simpler program which is likely to handle a large number of its use cases.

Disclaimer: I am one of those who sadly can't use the xrandr Screen Resolution tool because NVidia's drivers are terrible. The free drivers can do it, though.

My issue with screens and graphics being there is it makes a lot of changes to xorg.conf, essentially producing a rigid glob that falls apart on the slightest disturbance. Worked before, but now xorg does decent autoconfiguration for displays (assuming half decent drivers), so the changed xorg.conf can only lead over to bad things.

---

### Post by eragon100 on 2008-05-10
Yeah, great autodetection."Detected" my monitor from a al2016w (with is is) into a "generic monitor." *great!*

---

### Post by madjr on 2008-05-11
i guess you guys don't know about **nvidia-settings** ?

---

