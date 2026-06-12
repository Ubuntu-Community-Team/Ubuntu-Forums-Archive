---
title: "How do I stop the pencil from fading in GIMP"
date: 2011-05-14
forum: The Cafe
---

### Post by Lucradia on 2011-05-14
When using a tablet to draw straight lines? (Using SHIFT Key)

---

### Post by Lucradia on 2011-05-16
Guess no one knows?

---

### Post by Dry Lips on 2011-05-16
I haven't got a tablet myself, but when you select “pencil” there is a box
named “fade out” under “Brush dynamics”. Doesn't unticking this box work?

P.S. If you had posted this thread under “Art and Design” you would have 
gotten beans for it. This is after all a support question, so there is no reason
to post this here in the cafe. ;)

---

### Post by Lucradia on 2011-05-16
> **Dry Lips said:**
> I haven't got a tablet myself, but when you select “pencil” there is a box
named “fade out” under “Brush dynamics”. Doesn't unticking this box work?

Nope.

---

### Post by Bandit on 2011-05-16
I have a tablet, but forgot if there is a way to stop it. 
Normally when I want to keep a line drawn consistent I would use the paint brush at very small setting. 

Have you tried playing around with the brush dynamics for the pencil?

---

### Post by leviathan8 on 2011-05-16
It is your finger that is faulty! :P

---

### Post by Dry Lips on 2011-05-16
**a)** Have you tried sketching in another program, in order to find out 
whether or not this is an issue with the tablet or with your Gimp-settings?

**b)** Perhaps it's a good idea to have a look at the documentation regarding
tablets as well..?

[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

**c)** Finally, could one of the **mods please move this thread** to an appropriate
category? (Art and Design?) In that way it won't get lost here in the café, 
and other people could later benefit from this thread.

---

### Post by Lucradia on 2011-05-16
> **Dry Lips said:**
> **a)** Have you tried sketching in another program, in order to find out 
whether or not this is an issue with the tablet or with your Gimp-settings?

It's probably GIMP. GIMP forces one of the tablet pen buttons to be enabled as right-click, even though the tablet settings itself say that button is disabled. Adding GIMP to the program list in the WACOM Control Panel will not help. **This is on Windows**, I'm not using Linux to use the tablet, so part b is not applicable.

> **Bandit said:**
> I have a tablet, but forgot if there is a way to stop it. 
Normally when I want to keep a line drawn consistent I would use the paint brush at very small setting.

That's not going to help, pencil is already at 1px size.

---

### Post by mcduck on 2011-05-16
In the Tool dialog open the Brush Dynamics-dropdown and disable the Pressure/Opacity check mark.

(The suggested Fade out-option is not related to tablets, it fades the line out regardless of if you have a pen or if you are using a mouse, simply based on the line's length)

---

### Post by Lucradia on 2011-05-16
> **mcduck said:**
> In the Tool dialog open the Brush Dynamics-dropdown and disable the Pressure/Opacity check mark.

(The suggested Fade out-option is not related to tablets, it fades the line out regardless of if you have a pen or if you are using a mouse, simply based on the line's length)

It only happens on tablets, and it's already unchecked.

---

### Post by Bandit on 2011-05-16
Hey Luc, I am gonna grab my tablet out and see what it does for me. If you havent already figured it out by the time I do. :-)

EDIT:
Hey Luc,
You dont have FADEOUT checked by any chance do you?
I am using a Kanvus Life106 and mine doesnt fade out unless fadeout is checked..

---

### Post by Lucradia on 2011-05-16
> **Bandit said:**
> Hey Luc, I am gonna grab my tablet out and see what it does for me. If you havent already figured it out by the time I do. :-)

EDIT:
Hey Luc,
You dont have FADEOUT checked by any chance do you?
I am using a Kanvus Life106 and mine doesnt fade out unless fadeout is checked..

As I said, no, it isn't checked.

---

### Post by mcduck on 2011-05-16
> **Lucradia said:**
> It only happens on tablets, and it's already unchecked.

Yes, the option I talked about (and showed in my screenshot) *will* only affect tablets.

Two different options, one *in* brush dynamics, one *under* it. The one in brush dynamics (Pressure/Opacity) is the one that controls how pen pressure affects the opacity, while the one under it (Fade out) automatically fades out the opacity regardless of what the pen pressure is (or if you even use a pen&tablet).

Do you have both those unchecked? Is any other brush dynamic setting enabled?

---

### Post by Bandit on 2011-05-16
> **Lucradia said:**
> As I said, no, it isn't checked.
Got me then. Must be a bug or something between GIMP and your tablet.
Mine works fine? :-?

---

### Post by Lucradia on 2011-05-16
Intuos4 Large, and yes, both checkboxes are unchecked :|

I don't do it often enough for a bug report, but what REALLY grinds my gears is that GIMP Forces the right-click on the pen buttons, when WACOM Settings says otherwise.

---

### Post by mcduck on 2011-05-16
> **Lucradia said:**
> Intuos4 Large, and yes, both checkboxes are unchecked :|

I don't do it often enough for a bug report, but what REALLY grinds my gears is that GIMP Forces the right-click on the pen buttons, when WACOM Settings says otherwise.

Probably that's related to your specific tablet as well, like the pen pressure thing must be, since I'm not having either one of those problems (using Intuos3 A6).

---

### Post by Bandit on 2011-05-16
> **mcduck said:**
> Probably that's related to your specific tablet as well, like the pen pressure thing must be, since I'm not having either one of those problems (using Intuos3 A6).

Ditto


Also mine actually works better under Linux then it does under windows.

---

