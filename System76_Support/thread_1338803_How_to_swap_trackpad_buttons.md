---
title: "How to swap trackpad buttons?"
date: 2009-11-26
forum: System76 Support
---

### Post by NathanZal on 2009-11-26
I've been having fun for the last few days moving into my new panp6. Everything is working fine except I've been unable to discover how to reverse the trackpad buttons. I'm left handed. The mouse configuration screen has a "left handed" option, which works perfectly. On my old IBM Thinkpad R40 running Ubuntu 9.04 selecting this option also reversed the trackpad buttons; not so on my Pangolin in Ubuntu 9.10.

I've seen a lot in the forums about trackpads, and have tried some of the utilities like gpointing-device-settings and synclient without any success.

Anyone know of a simple method to reverse the buttons?

By the way, I do like the new keyboard a lot, but it will take some getting used to. It seems that my right hand keeps wandering into the weeds...

Thanks for your time!

Nathan
----
Love and hate are horns on the same goat -- "The Vikings," 1956

---

### Post by thomasaaron on 2009-11-27
Did you try System > Prefs > Mouse > Mouse-Orientation?

---

### Post by NathanZal on 2009-11-27
Thanks for your reply. Yes, as I explained in my post, I did that, and it works perfectly _for the mouse_ but has no effect on the trackpad.


All the best,

Nathan

---

### Post by thomasaaron on 2009-11-27
Indeed you did! Sorry about that.

I've had someone else report that they couldn't create a left-handed configuration with synclient.

I'm working at home today (a four-day weekend ;) ), but we can run some tests in the shop over the next week or two to see if we can figure something out.

---

### Post by NathanZal on 2009-11-27
Thanks!

---

### Post by NathanZal on 2009-11-29
I found a solution that works for me. I would rather be able to do this at a lower level in the system, but this gets the job done. My system is a PanP6; your mileage may vary.

Open "System -> Preferences -> Startup Applications"
Click "Add"
Set "Name" to something descriptive, like "Swap Trackpad Buttons"
Set "Command" to this:

/usr/bin/xinput set-button-map "SynPS/2 Synaptics TouchPad" 3 2 1 4 5 6 7 8 9 10 11 12

Set "Comment" to anything you like, such as "Left handed touchpad buttons"
Click "Save"
Click "Close"
Logout and then back in again.
Voila, left-handed trackpad buttons.

I hope that this information helps someone else.

Cheers,

Nathan

---

