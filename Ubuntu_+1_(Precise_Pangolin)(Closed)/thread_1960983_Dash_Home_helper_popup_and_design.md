---
title: "Dash Home helper popup and design"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Ender985 on 2012-04-18
It's a minor issue, but maybe it can be fixed easily. Whenever I mouse over the Dash Home button, a little helper info pops up with the rather uninformative message "Dash Home", which is fine if you are just hovering over the icons to see what they are.

However if you then press the button and jump to the keyboard to search for something in the Dash, then the four first characters you type are completely covered by that very popup message. And given the aswome job the Dash makes at finding things, 4 letters are usually more than enough, so that in 95% of my searches I have zero visual feedback on whatever I'm typing.

This could be solved by making the popup disappear whenever the mouse clicks the button; hopefully it's an easy thing to fix. Or maybe I'm the only one suffering from that problem/bothered by it.

---

### Post by mcellius on 2012-04-18
You're right: it's a small thing, yet it ought to be fixed.  I've run into the same issue.

---

### Post by mc4man on 2012-04-18
The tooltip should disappear immediately when clicking the icon & does so here.(edit: but not in current unity-5.10


But 'hanging' tooltips is something that can happen from time to time though I've not had it be persistent, more a somewhat random occurrence.

---

### Post by grahammechanical on 2012-04-18
Why use the mouse?

You want to use the keyboard, do you not? Then

Press the super key and the Dash will open and you can begin typing. No tool tip present.

Of course you could click the dash and then move the mouse pointer slightly as you move your right hand to the keyboard.

No problems with this on my part.

Tool tips are supposed to remain in place whilst the mouse pointer is over the Launcher so that the tool tips change as you move the pointer up and down the Launcher icons. It the same way auto-hide is disabled all the while the mouse pointer is over the launcher.

All this was tested weeks ago before Unity 5.2, 5.4, 5.6, 5.8 and 5.10 were brought into 12.04. The time for noticing things like this is long gone.

Regards.

---

### Post by mc4man on 2012-04-18
Actually Ender985 you are correct - when checking out before I was on an install with unity reverted to 5.8 where the tooltip does disappear when clicking on Dash

unity-5.10/nux-2.10 introduced this & a bug should be filed on if not already  

(either the testing for 5.10 missed this or it was found & not fixed or not considered an issue

---

### Post by Ender985 on 2012-04-18
> **mc4man said:**
> Actually Ender985 you are correct - when checking out before I was on an install with unity reverted to 5.8 where the tooltip does disappear when clicking on Dash

unity-5.10/nux-2.10 introduced this & a bug should be filed on if not already  

(either the testing for 5.10 missed this or it was found & not fixed or not considered an issue

It has been acting like this for me since I installed the pangolin beta, and I switched from 10.04 so I had no previous experiences with older Dash versions. Glad to hear that was fixed in the previous versions so it probably is just a regression, I'll search for a bug report and if missing will fill one myself.

And @grahammechanical, I know I can just use the super key, but since there is a mouse launcher I figured out I could also use the mouse for it. Since there is no way to search for applications with the mouse, you (almost) always need to use the keyboard next, so this problem is going to be encountered by anyone using the mouse+keyboard combination. Since you don't expect to have to move your mouse out of the button after clicking it in order to see what you are typing.

---

