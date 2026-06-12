---
title: "My old gripe about resizing windows"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-14
This is my old gripe about resizing windows in Ubuntu. I still find it hard to do, unintuitive, and something that makes this OS less friendly, less usable and less professional for newcomers.

Here are the screenshots of the areas in QQ and Windows:

[ATTACH]224138[/ATTACH]
[ATTACH]224139[/ATTACH]

In Windows, and at least since Windows 3.1 (this is as far as I have managed to test), the resize areas are located *within* the windows areas and they are symmetrical. In Ubuntu they are placed outside the windows and are asymmetrical.

New users and people that multitask between Windows and Ubuntu will always move their mouse pointer automatically to the the resize areas they have used for two decades and is hardwired in their brains. The way it is set in Ubuntu creates an unnecessary step for new users to adjust.

To save everyone's time, the results of this thread usually are:

**BUG EXISTENCE/RELEVANCE DISCUSSION**
[LIST]
[*]A small percentage of users denies the existence of the problem. (I always suspect these are part of the users that do not run Ubuntu or its Development Releases and just post here for reasons I do not understand);
[*]An equally small percentage of users acknowledge the problem and point me to the same old bug reports;
[*]The remaining larger portion of users acknowledge the bug, but question its relevance, state that it does not affect the OS usability.
[/LIST]

**TECHNICAL DISCUSSION**
[LIST]
[*]Some users mention it has to do with the "invisible" area used by decorations (shadows). I disagree because the behavior is the same if I set the shadows to larger/smaller areas in ccsm / decoration.  

[*]Others affirm it has to do with the move from GTK2 to GTK3, broken theming because of this move or the way UI settings are stored at that cycle (specific keys). I disagree because we've been talking about this bug for at least 5 cycles - it makes no sense for it to not be fixed *because* of something else.
[/LIST]

**USUAL OUTCOME**
[LIST]
[*]I report a bug or reopen the bugs related to it;
[*]After release I receive the LP automated message saying the bug in no longer valid. 
[*]This behavior moves to a new release.
[/LIST]

If anyone else agrees this thing is a bug and that it should be fixed, I'd like to ask you to report this. I have tried many times and I believe my reports about it are automatically disregarded.

**EDIT:** I forgot to mention one thing: There's always an argument about borders widths, no borders, invisible borders and how they are set at /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml. I think this is irrelevant. With or without borders of any type, resizing windows should work well and in a sane way at this point.

Regards,
Effenberg

---

### Post by mc4man on 2012-09-14
And you would like it to be done how? (don't have windows here

Also in addition to the half-dozen or so methods now or in place of them or some of them?

---

### Post by effenberg0x0 on 2012-09-14
> **mc4man said:**
> And you would like it to be done how? (don't have windows here

Hi, 

It would be easier for me to explain the difference if you had a Windows machine around :) 

Anyway, I'll try: In Windows, your mouse pointer turns into the "grab pointer" *inside* the windows, when you are close enough to the borders/corners. And the area you hover to activate the "grab pointer" is equal on all sides and corners - it's symmetrical, it makes more sense.

It is easier to resize windows and easier to learn / adapt that way. It has been like that forever in Windows. As it is right now in Ubuntu, it is not easy to learn or adapt when adopting the OS.

When people move from Windows to Ubuntu, this is something that is really hard to adapt. And since it's not symmetrical, it looks/feels broken/unprofessional to new users.

**EDIT:** It's also unpleasant when you have Ubuntu and Windows side-by-side, if you're using VMs or sharing the mouse via a KVM switch. You have to grab W7 Windows one way and Ubuntu Windows in another way. 

> **mc4man said:**
> 
Also in addition to the half-dozen or so methods now or in place of them or some of them?
I'm not sure I understand you.

Regards,
Effenberg

---

### Post by Sir_Sid on 2012-09-14
I just want to make sure I'm understanding you here, but this boils down to the fact that is weirdly hard to grab the window edge to resize it right? Because I still miss the window edge in ubuntu and I use it on both my main machines. I dont ever recall having this issue when I used or use windows

---

### Post by effenberg0x0 on 2012-09-14
> **Sir_Sid said:**
> I just want to make sure I'm understanding you here, but this boils down to the fact that is weirdly hard to grab the window edge to resize it right? Because I still miss the window edge in ubuntu and I use it on both my main machines. I dont ever recall having this issue when I used or use windows

Precisely. Grabbing windows edges and corners in Ubuntu is harder than it is in Windows because the areas that "activate" the resize mouse cursor are placed in the outer edges of the windows (instead of on the inner edges/inside them), they have varying widths in each window side/corner. It's irrational, asymmetrical - thus not very intuitive.

Regards. 
Effenberg

---

### Post by mc4man on 2012-09-14
That so called "invisible" area only existed in natty (dev I think) for a short time. It was gone I believe in a switch of decorators due to performance issues with that decorator & hasn't reappeared
> I'm not sure I understand you.
I was referring to all the other ways to resize that don't involve 'grabbing' the window edge thru cursor only.

With your subsequent explain not relevant to the issue. (of side/top/bottom grab-able area
(- the right side/ bottom need to be 'outside in' due to the overlay scrollbars which are 'inside out'

---

### Post by effenberg0x0 on 2012-09-14
> **mc4man said:**
> That so called "invisible" area only existed in natty (dev I think) for a short time. It was gone I believe in a switch of decorators due to performance issues with that decorator & hasn't reappeared

I was referring to all the other ways to resize that don't involve 'grabbing' the window edge thru cursor only.

Ah, sorry, I misunderstood you. Of course there are alternative ways, using Unity Grab Handles, etc. I'm totally aware of that.

> **mc4man said:**
> 
With your subsequent explain not relevant to the issue. (of side/top/bottom grab-able area
(- the right side/ bottom need to be 'outside in' due to the overlay scrollbars which are 'inside out'

I have never thought of the right-bottom corner issue being related to overlay scrollbars (I do not use them). Ok, it makes sense that this specific corner needs to have a different area than the others. 

I know you master stuff about Unity and the inner workings of the interface, the settings, theming, etc, so I have to ask you: Where does this choice of outer-edged resize-areas, with different widths between window sides, comes from? Was it ever a design choice? Ex: Grabbing the top is much harder than grabbing the left or right side. Was it ever discussed and decided it was a good alternative? 

Or maybe we have some technical limitation that makes it not doable to have something more or less symmetrical, like a 10px inner-edged resize-area in all sides (except for the bottom-right corner, as you explained)?

Thanks,
Effenberg

---

### Post by mc4man on 2012-09-15
For the most part stopped paying att. when the padding was removed & shadowing was returned to a sane amount
(MS wanted 45px so that's what natty got even though I got the feeling some whose opinion's do matter disagreed

Any way if you remember there was this padding/white box in natty that made resizing easier but that's long gone. 
(I believe there still is <padding ... /> in that metacity .xml but it does nothing or nothing that can be changed
(the only thing I ever change in that file is I remove the 1px border which has no effect on resizing though if increased might help?? (though look ugly

While can see point on consistency myself have no issue with the resize, though can accept some may. Generally here use the bottom right to control all dir. @ once.
Sometimes use the r. click on window deco with arrow keys which can be cycled, used, cycled. (alt+F7 starts the same

For whatever reason don't have issue with edge grab, but again that's beside the point (low quality quick vid attached

As far as 'improving', seems a longshot, would likely need a Design bug confirmed/fix released, then someone would fix someday

---

### Post by dino99 on 2012-09-15
Only adding my 2 cents:

- window borders are so thin: its good, but most of them does not have the bottom right triangle handler, so grabbing and expanding the window size is a real pain.

- note that i also does not like the overlay scrollbar, quite a non sense to me.

So the main question: how to get/set that triangle handler for all the windows ?

---

