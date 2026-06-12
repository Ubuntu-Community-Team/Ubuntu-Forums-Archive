---
title: "Installed 12.10, crashed via compiz -&gt; &quot;Failed to load session ububtu&quot; HELP!"
date: 2013-02-04
forum: Tennessee Team - US
---

### Post by levicalebblack on 2013-02-04
So I installed 12.10 on a friends laptop, raving about how awesome unix based systems were. Im working on this HP Pavillion dv7.  Compiz kept crashing and messing up the desktop stuff. Two days ago I tried to set up her printer and compiz crashed,I Was about to try to remove compiz and after running  'Sudo purge-compiz" or something close to that, Gnome kina went ballistic and so I decided to just restart and now i cant get an ubuntu session to load. I can get all the way to the user login in screen. Then it just says "Failed to load session Ububtu.' I saw similar threads with similar issues with 11.04 but have no clue how to recover this install because she put tons of pictures on it, that I now have to save. I can get to a GRUB command line but that's about it right now. I have GNU GRUB version2.00-7ububtu11 on a system running Ububtu 12.10. How can i fix this issue? I am not familiar at all with a grub command line or anything and even after researching this cant figure out how to not screw this up! lol. The last time i used Ubuntu it was at 10.04 so I am a bit lost now. Thanks for any help!

---

### Post by ChrisTownsend on 2013-02-20
Hi levicalebblack,

I'm not sure if you're still having issues, but here is something for you to try if you still need help.

It sounds like you removed compiz which is a pretty bad thing to do.  This is the software that renders the screen for the Unity desktop.  You'll need to get compiz re-installed on the system.  To do this, do the following:

1) When at the login prompt, hit Alt+F1 and you should be at a text-based login prompt.
2) Login with the username/password combo set up for the laptop.
3) When logged in type, "sudo apt-get install compiz" (without quotes).  Type the users password when prompted.
4) Say yes to allow it to install the software.
5) After it installs, enter "sudo reboot".

After the reboot, you will hopefully be able to log in to the desktop.

As far as the compiz crash goes, have you tried sending in the bug report when the crash occurs?  If not, please try to submit the bug report as entering crashes and bugs will make Ubuntu a better OS.

Let us know how it's going.

Cheers,
Chris

---

