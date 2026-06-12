---
title: "Resizing Windows"
date: 2012-07-16
forum: The Cafe
---

### Post by rg4w on 2012-07-16
How easy is it for you to resize windows in Ubuntu?

Most of the new users I help support note that it's much harder to find the grippable edge of the window for resizing it than on Mac or Windows, and indeed I feel the same.

I understand many here prefer the Alt+Middle Mouse shortcut, but what exactly does "Middle Mouse" mean to a new user with a standard two-button input device?

Moreover, shortcuts are alternatives to direct interaction, not replacements.

Why not just have a larger grippable region at the window's edge?

Your thoughts will be appreciated, helpful in guiding a proposal for the Unity design discussion list if enough others here also feel this is an area ripe for refinement.

---

### Post by sffvba[e0rt on 2012-07-16
*Thread moved to **The Community Cafe**.*

Doesn't sound like a Testimonial to me?


404

---

### Post by Grenage on 2012-07-16
I think scrollbars would have to be lightyears ahead on the irritability scale; I have no problem resizing.

---

### Post by vasa1 on 2012-07-16
I have problems resizing. And I don't want to install ccsm just to use the "love handles".

Scrollbars can be another thread ;)

---

### Post by ajgreeny on 2012-07-16
I agree that resizing is difficult in Ubuntu 12.04 as a result of the incredibly narrow window borders, and these are no doubt set by the theme.  Regrettably theme installation is nowhere as easy now as it was, or if it is, I've missed some obvious? way to do it.

To make things easier, try grabbing the bottom right corner of windows, which I have always found easier than the sides or bottom/top edges.  I don't use Ubuntu 12.04 much at the moment, and when I do it is the Classic gnome fallback that I use, not unity, so forgive me if that does not work as it always has done in the past.

---

### Post by drmrgd on 2012-07-16
Not sure if this is helpful to you or not, but I found that if you hold the alt key and the right mouse button, you can resize the active window by dragging the mouse around.  This is much, much easier than finding the 2px x 2px area that is designated for window resizing by default.

---

### Post by vasa1 on 2012-07-16
> **drmrgd said:**
> Not sure if this is helpful to you or not, but I found that if you hold the alt key and the right mouse button, you can resize the active window by dragging the mouse around.  This is much, much easier than finding the 2px x 2px area that is designated for window resizing by default.
True !!!

---

### Post by epikvision on 2012-07-16
Before I realized (just now) that alt+middlemouse was an ingenious way of resizing windows, I normally did this by dragging on the corners of the window. I drag the bottom right corner often when necessity calls.

If I feel lazy, I simply do ctrl+super+left or right, as it takes up half the screen for me.

---

### Post by Copper Bezel on 2012-07-16
I can't respond except as a rant. 

Ubuntu solved this problem in 11.04 with the universal resize grip. They then turned the handle from an aesthetic deficit to an asset in 11.10. Then it disappeared in 12.04, back to the old system where only windows that specifically include resize handles have them and everything else depends on dragging vanishingly thin borders to resize.

I liked the thin borders. I *still* like the thin borders. There's no sense wasting UI space on fat, ugly borders that do nothing but resize windows. The grip offered a reasonable alternative; if you read left-to-right, then you're likely to resize windows that way, too, so a handle on the lower right corner just makes sense.

Of course, there's always the MT handles, and they're fine if you're using Unity and have a trackpad, and don't mind not having middle click, and are comfortable with a completely non-intuitive and ugly method for resizing windows. Peachy. 

Personally, I'm using Shell, where the situation is slightly worse (because Gnome apparently hasn't acknowledged that they have a problem yet,) I do use middle click, and I want the damned handles back. The sloppy handling of resizing means that it's impossible to resize a window to the full height of the screen (you can get close, but there's always a gap, maybe 1px, just enough to be irritating. Of course, you can snap left and right, which is a great feature (and I'm ever thankful to Microsoft for coming up with it,) but then you have no control over the width. The saving grace must be that it's damned easy to accidentally grab edges and resize them by accident, which also doesn't happen if all resizing happens from resize grip.

So, effing resize grips. Six months to a year was exactly enough time to make the feature indispensable. Whoever's responsible for the regression really needs to be slapped with a ripe fish.

Edit: Oh, and the gripping area isn't 2px. It's like 5 or something - under Mutter, you can actually set it in dconf. But it extends *outward from* the window, which is why it's impossible to drag a window edge fully to the edge of the screen.

---

### Post by drmrgd on 2012-07-16
> **Copper Bezel said:**
> 
<snip>

Edit: Oh, and the gripping area isn't 2px. It's like 5 or something - under Mutter, you can actually set it in dconf. But it extends *outward from* the window, which is why it's impossible to drag a window edge fully to the edge of the screen.

</snip>


I was just being sarcastic about 2px (I really had no idea).  The fact that it's actually 5px is hillarious!  Before I learned the middle-click trick (which appears to be right click in KDE for some reason), I almost needed two hands just to resize windows.  Then again, I do drink a lot of coffee :D

---

### Post by rg4w on 2012-07-17
> **drmrgd said:**
> Before I learned the middle-click trick (which appears to be right click in KDE for some reason), I almost needed two hands just to resize windows.
This issue came to mind as I was answering the question from a potential new user.  This person is a long-time Mac user, but her needs are modest and it's hard to for her to justify spending US$1k on a machine just to do email and the web.  But she's not a fan of Windows, so she was willing to give Ubuntu a try.

In most respects it works well for her, but when it came to resizing windows it was as hard for her as it was for me before I modded my metacity theme files.

We bought up the shortcut overlay, but then she asked "What's a 'Middle Mouse'"?  When I explained that one needs to hold down the Alt key while simultaneously pressing both the left and right trackpad buttons, she laughed and said, "Do I then use my foot to move the pointer?"

"How do I resize windows?" is not a question I see in Mac or Win forums, but I see it here almost monthly it seems.

At a minimum, the nomenclature in the shortcuts overlay could benefit from refinement, since very few users have a three-button mouse so "Middle Mouse" is meaningless to the uninitiated.

But more importantly, shortcuts are alternatives to features, not replacements.

Why do you suppose we see this question here as often as we do, and why do you suppose the Ubuntu audience learns shortcuts so much faster than their Mac or Win counterparts?

If we're serious about growing Ubuntu's audience, these small things will become increasingly important.

---

### Post by samwyse on 2012-07-17
> **drmrgd said:**
> I was just being sarcastic about 2px (I really had no idea).  The fact that it's actually 5px is hillarious!  Before I learned the middle-click trick (which appears to be right click in KDE for some reason), I almost needed two hands just to resize windows.  Then again, I do drink a lot of coffee :D

Actually it used to be right click in every window manager ever made. Gnome (Metacity) decided to be different. 

Oh, and I hate the 2px borders that 99% of themes seem to have. I guess it looks good, but I like usability.

---

### Post by Copper Bezel on 2012-07-17
Seriously, though, why did the Mac-style resize grips go away? They're just a sensible solution. They don't take up *any* useful space. I mean, I'd be okay with the DE not imposing them so long as every GTK application ever built had the sense to include them in the first place. = )

---

### Post by thaitang on 2012-08-03
> **drmrgd said:**
> Not sure if this is helpful to you or not, but I found that if you hold the alt key and the right mouse button, you can resize the active window by dragging the mouse around.  This is much, much easier than finding the 2px x 2px area that is designated for window resizing by default.
I came looking for a solution to once again easily resize windows, and I found it. This works good for me.

cheers,
tt

---

### Post by Linuxratty on 2012-08-03
> **ajgreeny said:**
> 
To make things easier, try grabbing the bottom right corner of windows, which I have always found easier than the sides or bottom/top edges.  I don't use Ubuntu 12.04 much at the moment, and when I do it is the Classic gnome fallback that I use, not unity, so forgive me if that does not work as it always has done in the past.

Using Fallback as well,and yes,this works well.
 You can resize windows in the Gimp the same way.

For the life of me I don't get this :"Let's save space" nonsense. I'm using a 23 inch monitor and I have more space than you can shake a stick at!

---

### Post by ksanger on 2012-08-03
Having to touch the keyboard to resize windows sucks.  

I could repeat that but hopefully I don't need too.

I hate unity for this.  Hope it gets fixed.  ALT makes me angry every time I have to stop and grab the keyboard.

---

### Post by rg4w on 2012-08-04
> **ksanger said:**
> Having to touch the keyboard to resize windows sucks.  

I could repeat that but hopefully I don't need too.

I hate unity for this.  Hope it gets fixed.  ALT makes me angry every time I have to stop and grab the keyboard.
As long as we're moving toward visual simplicity at the cost of utility, why not take a cue from the MacBook Wheel?:
[http://www.theonion.com/video/apple-introduces-revolutionary-new-laptop-with-no,14299/](http://www.theonion.com/video/apple-introduces-revolutionary-new-laptop-with-no,14299/)

:)

---

### Post by vasa1 on 2012-08-04
> **rg4w said:**
> ... the MacBook Wheel?...

Just a rectangle with very rounded corners.

---

### Post by mick62 on 2013-02-16
My proposal:

The programmers of the windows manager should provide an option in the settings. 
When this option is enabled, a stripe around the active window (the part which shows a shadow on the underlying windows) is considered as belonging to the border of the active window.

---

### Post by MadmanRB on 2013-02-16
This is a non issue in KDE :D

---

### Post by jdieter on 2013-05-23
Dear LORD I struggle to resize using these stupid tiny borders! Is there no easy way to make the window edges bigger? This is absolutely the most ANNOYING thing! I want to go back to windows. I thought the stupid "launch" bar was bad, but got used to it. But I cannot atnd how I struggle every day trying to resize a stupid wndow.

---

### Post by Copper Bezel on 2013-05-23
I think Ubuntu is depending pretty heavily on window snapping on the one side and the multi-touch tap for the resize handles on the other. Arguably, neither of those things is *fixing* the problem, but trying to futz around it. Compiz doesn't allow an option for increasing the resize area, although it's still always possible to just use a different UI theme instead that provides thicker borders. (Of course, this does mean a small cost in screen real estate, which is why Ubuntu uses the slim borders.)

I still miss having no window borders at all but having all windows provide a resize grip in the bottom right corner. That seemed like a very sensible solution in - what was that, 11.04?

---

### Post by montag dp on 2013-05-23
I don't get it.  Why can't they just make the grippable region wider?  In Gnome it extends off the window by ~20 pixels or so.

---

### Post by Triblaze on 2013-05-24
On my current theme, resizing is pretty easy, there's a good bit of room to grab, because windows have little borders all the way around them. I seem to remember it being harder on the default though.

> **ajgreeny said:**
> I agree that resizing is difficult in Ubuntu 12.04 as a result of the incredibly narrow window borders, and these are no doubt set by the theme.  Regrettably theme installation is nowhere as easy now as it was, or if it is, I've missed some obvious? way to do it.

With Unity, most themes that I get online can easily be installed by copying their folder to either .themes in your home directory, or system wide with {sudo cp -r filepath /usr/share/themes}. Using themes from these folders is odd with only the default system tools, but something like Ubuntu Tweak, Tweak Tool, or Unsettings will have a theme section where you can set it.

---

### Post by vladster on 2013-05-25
Its frustrating

---

