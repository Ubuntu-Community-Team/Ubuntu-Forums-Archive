---
title: "[SOLVED] Continual Search?"
date: 2007-10-06
forum: Ubuntuzilla
---

### Post by carltonb on 2007-10-06
I just installed using the directions provided. 

When I started TB my folders and address book showed


When I start TB I get a single beep. TB opens. But when I place the cursor in the left folder pane it continually shows it is processing something. No emails are displayed

What should I check and what other information do you need.
Carltonb

---

### Post by nanotube on 2007-10-06
> **carltonb said:**
> I just installed using the directions provided. 

When I started TB my folders and address book showed


When I start TB I get a single beep. TB opens. But when I place the cursor in the left folder pane it continually shows it is processing something. No emails are displayed

What should I check and what other information do you need.
Carltonb

my first guess may be that you have some corruption or incompatibility in your profile. maybe an incompatible extension?

try running thunderbird in safe mode:
```
/opt/thunderbird/thunderbird -safe-mode
```

this will start tb without any extensions enabled.

and also see this thread for general tips for troubleshooting problems with extensions:
[http://ubuntuforums.org/showthread.php?t=546438](http://ubuntuforums.org/showthread.php?t=546438)

---

### Post by carltonb on 2007-10-07
I tried what was suggested first with safe mode. Nothing.
Created new profile. Worked correctly. So now I knew it was in my transfer of windows profile to new profile.

I created a new default user. Copied one file (groups of files) and tested after each addition. This method worked fine and I am up and running. When I tried to do the whole windows user profile it crashed. But installed a little at a time and worked fine.

Thanks for the help.
carltonb

---

### Post by nanotube on 2007-10-07
cool, glad it worked! 
these "profile problems" seem to be somewhat common. i wonder if tb shouldn't be better at detecting them and prompting the user with a detailed message... maybe it's a bug to be filed. :)

---

