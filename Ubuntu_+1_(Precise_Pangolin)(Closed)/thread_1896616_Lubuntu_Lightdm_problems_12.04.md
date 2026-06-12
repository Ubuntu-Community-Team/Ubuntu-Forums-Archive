---
title: "Lubuntu Lightdm problems 12.04"
date: 2011-12-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MrGreen on 2011-12-17
I am testing Lubuntu 12.04, had problems soon after install with lightdm not working.

Switched to slim did not seem to help

Tried to use dpkg to switch back to lightdm [installed]

Now get error that slim is not default log in manager.

Need to find a way to remove slim completely from system. 

And find where slim is being launched?

---

### Post by grahammechanical on 2011-12-17
I tell you at the start that I have no experience with lubuntu. What do you mean that LightDM is not working? What exactly is it not doing?

When I was testing the standard Ubuntu 11.10 development release which first use LightDM I could not log in. I had to replace LightDM with GnomeDM (GDM) until the problem was fixed.

This meant stopping stopping LightDM, installing GDM and the starting GDM. Then to get back to LightDM I had to stop GDM and start LightDM.

Obviously, lubuntu is not using GDM but, I guess, something called slim is used instead.

I do not know if any of this helps you but I think that to get the solution to your first problem you will need to explain exactly what that problem was. Saying "it was not working" does not give any clue as to what is wrong. People here need clues.

Another thing, there is a special section of this forum called Ubuntu+1 (Precise Pangolin) where those testing 12.04 give and get advice on issues with 12.04. That is the section you should be asking this question in. It was where I found the answer to my Ubuntu+1 (Oneiric Ocelot 12.04) login problem.

Regards.

---

### Post by philinux on 2011-12-17
Moved to Precise testing forum.

---

### Post by MrGreen on 2011-12-17
I do not get log in screen with lightdm at all...

Have to Crtl + Alt + F1 to get to a console and then run startx

I tried to run slim but that had problems too so wanted to switch back and try lightdm again

Going to see if I can find any errors that may be of some more help

---

### Post by MrGreen on 2011-12-17
I have installed xserver-xephyr and running test-mode seems to work...

Hopefully will sort problem

---

