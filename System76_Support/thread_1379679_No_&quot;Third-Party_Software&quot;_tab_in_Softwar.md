---
title: "No &quot;Third-Party Software&quot; tab in Software Sources on my starling"
date: 2010-01-12
forum: System76 Support
---

### Post by black_ice=cream on 2010-01-12
in an attempt to fix my wireless after upgrading to 9.10, AFTER THEY FIXED IT, I went to System > Software Sources like the knowledge base said, but there is NO tab marked "Third-Party Software" it just says "Other Software". And on the knowledge base it says to check the box with some URL next to it. That's not there?! What do I do?!?!?!?!?!?!?!

---

### Post by byStanderone on 2010-01-12
...not sure if i got your situation right, anyway, if that is a third party software, you will have to add the URL in your software sources before anything else...unless you have downloaded the package from the site manually. or perhaps a review of the steps you've taken would unveil something that u missed.

---

### Post by bvandev on 2010-01-13
Have you checked the items in the Other Software listed as "disabled on upgrade to Karmic"?  The terminology may be a little different, but one of those should be the System76 repository.  If you choose each one and select "edit", it should show you the url.  Then just change the comment to something you will understand in the future.

Hope this helps.

---

### Post by thomasaaron on 2010-01-13
The "Other Software" tab is the correct one. But here is what you need to do...

1. Go to [http://planet76.com/repositories](http://planet76.com/repositories) and download the 2.4.4 version of the System76 driver. It will be the 2nd link from the bottom.

2. Go to your Downloads folder and double-click the driver package to install it. Follow the subsequent prompts.

3. Go to System > System76 Driver and click the Restore tab and the Restore button. This will set up everything in your Software Sources correctly and should fix your wireless as well.

Let me know if you need help.

---

### Post by black_ice=cream on 2010-01-13
hey System76, I did that. well, I've been waiting for the restore for a really, really long time, it's going now I haven't killed it yet, but it kind of seems like it's never going to finish... it just says "Factory setting are being restored." I don't know how long this is supposed  to take but...

**EDIT** - It has been going for over 3 hours now, so I killed it. Then, I happened to check the "software sources" thing and the box w/ the URL was there and checked! So I decided to follow the next step on the knowledge base which is, go to System > Admin. > System76 Driver and then click the install driver tab and the install button. Well, I'm waiting... seems that it's the same as the restore... just loading for endless amounts of time and not doing anything...

---

### Post by thomasaaron on 2010-01-14
[LIST]
[*]Kill the driver.
[*]Establish a wired internet connection.
[*]Open a terminal (Accessories > Terminal).
[*]Run this command (and accept all defaults)...
```
sudo apt-get install grub-pc
```
[*]Reboot your computer.
[*]Re-run the driver.
[/LIST]

Did that fix it?

---

### Post by black_ice=cream on 2010-01-14
**yes!!!** Okay, I ran that command, choose all defaults, rebooted, ran the driver (it worked), rebooted, installed 2 updates in my update manager, rebooted and, yay, my orange wireless light is on!! wow, System76 is amazing. Do you know how long it would've taken to get that info from dell support?!?!?!??!?! Thanks so much people at System76. You guys are truly amazing. :D

---

### Post by porlaizquierda on 2010-03-21
i just want to say that i had the exact same problem from an otherwise perfect upgrade to 9.10. i did exactly what system 76 said and now my wireless is back up. it took no time! everyone there is awesome!

---

