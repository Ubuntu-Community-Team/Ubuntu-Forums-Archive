---
title: "Shutdown Clicks"
date: 2021-09-06
forum: Ubuntu Development Version
---

### Post by chrisw63 on 2021-09-06
To shut down Ubuntu 18 LTS using the mouse, you had to click three times.  Ubuntu 20 LTS requires four clicks to shut down properly:  Menu, Power Off / Log Out, then it EXPANDS to let you click Power Off, and then you have to click a confirmation dialog to finally Power Off.  Why are Power Off and Log Out grouped together?  Wouldn't it be common sense to group Lock and Log Out?  Not that I condone anything that requires another click for no reason.  This is not good UX.  And, yes, I know technically I could wait sixty seconds instead of the last click, but why? (See below)  If the next LTS takes 5 clicks, I'm changing distros.

Do I know I can make my own script for shutdown and put it on the  desktop?  Yes, yes I do.  But most first time Linux users Don't, and a  lot of them are being pointed to Ubuntu as their first Linux distro.   This is about UX, not about my knowledge or lack thereof.

How about in Impish Indri we simplify it back to only Three?  The main menu dropdown should have ALL the options separately - no sub-menus or 'expansions'.  Lock, Log Out, Suspend, Restart, Power Off.  Tooltips can alert you to the specifics of each one.  Users new to Linux, for instance, may not know that 'Lock' lets your program(s) keep running.  To shut down, the user clicks Main Menu, Power Off, Confirm (with a Default OK button so you can just hit Enter instead).  Done.

The 60 second log out / shut down delay is antiquated, IMO.  It's a great opportunity for an inattentive employee to miss that last click.  Then someone ill-intentioned 'walks by' before the time-out, clicks Cancel and hacks your company.  It should be deprecated and moved to an option in the system settings - or removed entirely.

---

### Post by mikewhatever on 2021-09-06
Yea, sure, we will, whoever "we" may be, but meanwhile, you need to open a bug report on launchpad.net. 
Posting it here is like preaching to the choir.

---

### Post by grahammechanical on 2021-09-06
The next version of Ubuntu to be released is 21.10. It still has a four click power off process. There is a change from 20.04. We will be able to select Restart with the third click instead of the fourth click. The fourth click still directly produces Cancel or Power off. If we selected Restart then the fourth click will directly produce Cancel or Restart.

If waiting sixty seconds is troubling you just do that fourth click and the option to Cancel will disappear and there is no going back from the choice we have made.

As regards employees, as I tried to explain to my employer regarding Health & Safety, if an employee is not following proper procedures then they need training. The trouble was the ones least likely to follow proper procedures were the management team.

Regards.

---

