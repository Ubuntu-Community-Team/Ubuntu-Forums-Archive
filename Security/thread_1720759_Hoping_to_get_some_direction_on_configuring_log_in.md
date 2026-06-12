---
title: "Hoping to get some direction on configuring log in"
date: 2011-04-03
forum: Security
---

### Post by ClientAlive on 2011-04-03
Hi guys,

Hope I'm in the right place. I'm pretty new to Linux and I was hoping to get some guidance on setting up my user account a certain way. I am reading books to learn more in general but this is something specific I would like to take care of soon.

I happen to be running Natty (Ubuntu 11.04) alpha 3. Please, please, I've already had the discussion about running an alpha as a newbie several times and I am resolved to stay on this path (I do have my reasons and I think they are good ones).

So here is the thing:

After I installed Ubuntu I had an issue where after about 5 min (about the time the screen saver would kick in) I would have to log back in again. I got some help with that and it is no longer an issue - however, now I never have to log back in after the first time at startup, and this does not seem good to me in certain situations/ environments.

Here is what I would like to do:

I would like to find a way to keep things as they are when I am at home or somewhere else that I trust the environment I'm in but add to that a configuration where after a certain (small) period of time you are required to log in again. I would also like to have that attached to/ assigned to a (hot key?) (fast key?) that would allow me to toggle back and forth. One of the F keys that aren't in use would be nice. Or, if all the F keys are used, Perhaps something like ctrl+F(n), ctrl+alt+F(n), ctrl+shift+F(n) (one of those combos but prefferably the first in the list if I had to go that route).

Is there any way to do this?

Thanks in advance. Sorry if I've posted in the wrong area. I just wanted to be sure I get the right advice.

Sincerely,
Jake

Note: when I say "F(n)" I guess I'm thinking in math terms where n stands for some number.

Thanks
:)

---

### Post by Dave_L on 2011-04-04
When you say "log in", do you mean that the screen is locked and you have to type your password to unlock it?  Or you do literally mean "log in"?

---

### Post by ClientAlive on 2011-04-04
I think what was going on (before) is the screen was "locking" as you  say. What I observed is: when you log in to begin with you first select a user then  you are presented with the field to enter the password (at this log in stage there is also a small amount of additional processing to boot the rest of the way).

Before  correcting the situation I mentioned in my first post (where I had to keep entering my password after a short idle time), it was such that when I returned there was no selecting a user first, only the  field for entering the password. Very close to how it is at log in but not identical. This situation of having to enter my password to unlock the screen has been fixed but I am still left with something to be desired. (As it stands right now I only enter my password when I start or re-start the computer and will not be required to give it again no matter how long the computer sits idle).

I know that in my first post I described what I would like to do a little differently than what I am about to describe in the following paragraph. In the course of thinking about this I have realized there may be a much simpler solution - and one that is actually superior. I think you will know better, but here it is:

It occurred to me that there may already be something in the o/s that can be clicked on (or a code that can be run in terminal) that just locks the screen right there on the spot. Not sure how I got this idea of "configuring" in my head; but, if a shortcut is not already in place, maybe the answer is as simple as assigning a hshortcut to that function (to locking the screen). Assigning a keyboard key/ shortcut would make it very convenient for me to lock the screen when I wished. I do have some preferences in mind for which key or combination of keys to assign (if necessary). All of them involve 'one of' the F keys along the top most row of the keyboard (F1, F2, F3, etc) in some way.

If the scenario described in the paragraph above is not already available - I wonder if it wouldn't be too difficult to set it up?

Thank you so very much for your patience with me. I know I haven't been as clear as I could be.

Jake

---

### Post by wilee-nilee on 2011-04-04
To get started there is a lock screen applet in the add to panel, right click the panel to get there.

The screen saver has a timer to lock your set up as well.

---

### Post by Dave_L on 2011-04-04
Also, the keyboard shortcut Ctrl-Alt-L will immediately lock the screen.

I think that immediate locking, rather than a timeout, is better for the situation you describe (leaving the computer unattended in an untrusted environment).

---

### Post by ClientAlive on 2011-04-04
Problem solved. Ctrl+Alt+L is perfect. I guess I could have just asked: 'is there a shortcut for locking the screen?' Would have been a lot less work for all of us. Just that I wasn't aware of the terminology. Lol.

Thanks so much fellas.

Sincerely,
Jake

---

