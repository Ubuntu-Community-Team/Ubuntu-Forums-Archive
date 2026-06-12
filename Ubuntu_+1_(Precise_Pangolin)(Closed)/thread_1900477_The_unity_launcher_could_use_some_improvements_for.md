---
title: "The unity launcher could use some improvements for multitasking"
date: 2011-12-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by madjr on 2011-12-26
detailed the current problem and added a few suggestions here:

[https://bugs.launchpad.net/unity/+bug/908811](https://bugs.launchpad.net/unity/+bug/908811)

---

### Post by seeker5528 on 2011-12-26
Calling the launcher window switching 'unaccessible' in relation to a wish that has nothing to do with accessability probably doesn't help the cause any.

And while it may fit the dictionary definition of several "more than two less than many", I don't think calling 3 clicks 'several' helps the cause any either.

I would like to see a Docky style list of windows though, but personally I would prefer it to be on the right click menu.

If something is to be shown while hovering, I would prefer the Windows 7 style thumbnails in the foreground when hovering over the dock icon, full screen previews in the background when mousing over the thumbnails.

Later, Seeker

---

### Post by madjr on 2011-12-27
is not an imaginary problem like it sounds in your comment, so if its not affecting you that would be another story (just like this [global menu bug]("https://bugs.launchpad.net/unity/+bug/682788") affects some people and not others). The fix suggested is just that a suggestion (which another person came up with), so the bug is open for anyone to propose their ideas, and the devs can fix it in any way they find best.

Also this worsening my [RSI]("http://en.wikipedia.org/wiki/Repetitive_strain_injury") is not imaginary.

---

### Post by effenberg0x0 on 2011-12-27
I have developed [CTS]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CDUQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FCarpal_tunnel_syndrome&ei=lgP6TtCVN4yWtwek9t3QBg&usg=AFQjCNFVahUsNlRaWFNkS8JE7OOpWFnIYA&sig2=ioataPnQ287d6UMiyHjIFg") when I was 17 years (PC + Piano), so RSI is something I take seriously. I *have to* use a proper chair and table, with proper adjustments, watch my posture, use a special keyboard, one specific model of trackball mouse, etc, and avoid repetitive movements as much as possible in the 16 hours/day I spent on the PC if I want to continue to have a career... 

I like Exposé, in the sense that the effect pleases me, but considering the health aspects / goals (reducing movement as much as possible), I agree that having a W7-like *option* (meaning it should be configurable and not mandatory) to switch between multiple instances / windows of a same program would be of great help to me.

So I +1'ed there. This one and, hopefully, some changes to the global menu in the future would help me a lot. However, given that accessibility configs, such as increasing size / changing color of the mouse pointer, were simply removed (thus making the use of Ubuntu very hard or impossible for the visually impaired) and don't seem to be a priority, I have no hope of having any positive feedback in this report.

Regards,
Effenberg

**EDIT: **Just thinking loud here: It would be a fun project to capture the list of opened windows via something like wmctrl, apply some regexp, etc and update / sed the quicklists in .desktop files dynamically. Quicklists titles can easily be the captured titles of the opened windows for that program. Clicking the quicklist can use wmctrl to raise that window. Sounds very doable as a cool script. Or just edit unity source and do it like it's supposed to be done... not so fun. :P

---

### Post by ventrical on 2011-12-28
> **madjr said:**
> is not an imaginary problem like it sounds in your comment, so if its not affecting you that would be another story (just like this [global menu bug]("https://bugs.launchpad.net/unity/+bug/682788") affects some people and not others). The fix suggested is just that a suggestion (which another person came up with), so the bug is open for anyone to propose their ideas, and the devs can fix it in any way they find best.

Also this worsening my [RSI]("http://en.wikipedia.org/wiki/Repetitive_strain_injury") is not imaginary.

The GNOME 3 DE and even Unity can realy ramp up the cause and instances of RSI. Compiz is not helping much either these days as there is still this intermittent 'bungie' effect every now and again that makes it a real pain in the a$$ trying to drag windows and icons on the DT.

  I really hope that  in the next 3 months this can all be ironed out effectively.  If not, I have been watching some of the thread  about GNOME Classic megathread and I have a manchine set up for that, however  I am confident that a lot of these bugs, real or no-real , will be worked on.

---

### Post by ventrical on 2011-12-28
> **effenberg0x0 said:**
> I have developed [CTS]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CDUQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FCarpal_tunnel_syndrome&ei=lgP6TtCVN4yWtwek9t3QBg&usg=AFQjCNFVahUsNlRaWFNkS8JE7OOpWFnIYA&sig2=ioataPnQ287d6UMiyHjIFg") when I was 17 years (PC + Piano), so RSI is something I take seriously. I *have to* use a proper chair and table, with proper adjustments, watch my posture, use a special keyboard, one specific model of trackball mouse, etc, and avoid repetitive movements as much as possible in the 16 hours/day I spent on the PC if I want to continue to have a career... 

I like Exposé, in the sense that the effect pleases me, but considering the health aspects / goals (reducing movement as much as possible), I agree that having a W7-like *option* (meaning it should be configurable and not mandatory) to switch between multiple instances / windows of a same program would be of great help to me.

So I +1'ed there. This one and, hopefully, some changes to the global menu in the future would help me a lot. However, given that accessibility configs, such as increasing size / changing color of the mouse pointer, were simply removed (thus making the use of Ubuntu very hard or impossible for the visually impaired) and don't seem to be a priority, I have no hope of having any positive feedback in this report.

Regards,
Effenberg

**EDIT: **Just thinking loud here: It would be a fun project to capture the list of opened windows via something like wmctrl, apply some regexp, etc and update / sed the quicklists in .desktop files dynamically. Quicklists titles can easily be the captured titles of the opened windows for that program. Clicking the quicklist can use wmctrl to raise that window. Sounds very doable as a cool script. Or just edit unity source and do it like it's supposed to be done... not so fun. :P

  UP where I live we are called the CTS capital of Canada :)

  Thanks for sharing what you did , especially about  visual impairment. I am a hardware tech )another by trade) and during the decade of the 90's PCs were really expensive . etc.. so a lot of people would have these borked 386SXs MoBOs go on the blink. Most often it was a 'plinked' CPU leg or other VLSI chip that let go from a cold solder joint or thermal creeping.  So I would take out my 'lens' and track these broken connections down and resolder them. Sort of like micro-surgery :)  It saved a lot of people a lot of money but really strained my eyes and took some toll.

  Maveric  had a nice look as does Lucid with zoom.

---

### Post by seeker5528 on 2011-12-28
> **madjr said:**
> is not an imaginary problem like it sounds in your comment

I have my own occasional issues with repetitive stress, and I don't doubt that if you added up the 2 extra clicks over the course of a day that there would be times when it sounded like a lot of clicks.

But...

A: It's spread out over time.

B: It doesn't always take 3 clicks, so it won't always be 2 extra clicks, sometimes it will be 1 or 2 clicks total.

C: Sometimes you will click on a window in the background to switch to it or use 'Alt'+'Tab'.

D: How much time do you actually spend switching applications, compared to all the other things you do where the mouse button or wheel gets used.

Repetitive stress doesn't prevent you from accessing the task switching features and can be compensated for with alternative input devices.

That's not to say repetitive stress shouldn't be taken into account in the interface design, but if you compare it to blindness where there may be issues that actually prevent access, it seems pretty minor.

As for as the core developers go, there is a need to prioritize.

Has anybody created a patch and tried to get it accepted? If not is there somebody that is able to that is willing to?

If such a feature is created and not accepted by the core Unity developers, could it be provided as an independently installable feature or would it have to actually be integrated in the dock?

If none of that happens, you can run Docky with the Unity desktop.

Later, Seeker

---

### Post by Derek Karpinski on 2011-12-29
> **seeker5528 said:**
> if something is to be shown while hovering, i would prefer the windows 7 style thumbnails in the foreground when hovering over the dock icon, full screen previews in the background when mousing over the thumbnails.

yeeeeeeesssssssssssssssssssssssss plz! :d

---

### Post by MarjaE on 2011-12-29
> **seeker5528 said:**
> C: Sometimes you will click on a window in the background to switch to it or use 'Alt'+'Tab'.

If the window has maximized itself, you can't just click on another in the background.

If you can't type left-handed, the alt-tab combination requires contorting the right arm.

> D: How much time do you actually spend switching applications, compared to all the other things you do where the mouse button or wheel gets used.It's very useful when comparing two documents, images, etc. I use other mouse clicks more often, but I _never_ use the wheel. Took some work to unlearn the scroll-wheel habit, but worth it, because the scroll wheel gave me severe tendon pain. I also use Gnome 2.

> Repetitive stress doesn't prevent you from accessing the task switching features and can be compensated for with alternative input devices.Except when the proposed alternative input devices aggravate repetitive stress.

---

