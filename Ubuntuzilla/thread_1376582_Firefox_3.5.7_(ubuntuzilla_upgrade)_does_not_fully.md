---
title: "Firefox 3.5.7 (ubuntuzilla upgrade) does not fully quit / crashes firefox"
date: 2010-01-09
forum: Ubuntuzilla
---

### Post by noob555 on 2010-01-09
I recently upgraded via ubuntuzilla to firefox 3.5.7 and now, every single time I close Firefox, the program seems to crash without quitting completely.  

First, I receive an error saying that the program will not close and asks me if I want to Force Quite or Wait for it to close on its own.  This has been happening ever since I upgraded to Karmic and if I just wait it usually quits fully after a couple seconds.

Now what happens is this: the window still closes, but if I try to reopen Firefox then I get this error stating that Firefox is *already open* and therefore cannot be opened again.  The only way to get back into Firefox is to restart the entire computer. (Incidentally, this is the same problem that occurs whenever I try to Force Quit Firefox)

This now happens *every* single time I "close" Firefox.

Does anyone know the source of this error?  Or a workaround?

**EDIT: SOLVED.**  DISABLE OR COMPLETELY REMOVE GHOSTERY ADD-ON.  note: creating a new profile will effectively do the same thing, and then some.

---

### Post by nanotube on 2010-01-09
Hi

could be something with your profile

try starting a fresh profile, and see if the problem goes away.

(to do this, start 'firefox -P' to start the firefox profilemanager, create a new profile, start with that profile, and see if there are any problems quitting.)

---

### Post by noob555 on 2010-01-09
Thanks.  I'll give it a try.  I should mention that a couple other people have mentioned this problem and are posting here: [http://ubuntuforums.org/showthread.php?t=1375930&page=2]("http://ubuntuforums.org/showthread.php?t=1375930&page=2")

---

### Post by noob555 on 2010-01-09
oops, posted to wrong place.

---

### Post by nanotube on 2010-01-09
ok, let me know how it goes!

---

### Post by noob555 on 2010-01-09
So the new profile works, even after I re-install my addons, theme, etc.  I'm not sure what this problem is.  Do you know?

p.s. THANK YOU!

---

### Post by nanotube on 2010-01-09
> **noob555 said:**
> So the new profile works, even after I re-install my addons, theme, etc.  I'm not sure what this problem is.  Do you know?


no idea - there's so much cruft hanging around in the average firefox profile, it's impossible to say offhand. the only way to even get close to finding out is to install a firefox built with debug symbols, then run it through a debugger and try to make sense of what's going on at the time of the crash. 

which is what actually may happen, if enough people have this particular problem and someone files a bug and someone who knows what he's doing takes a look at a few debug traces.

but at this point... no, i have to idea :)

> 
p.s. THANK YOU!

you're quite welcome!

---

### Post by noob555 on 2010-01-09
So here's what's truly weird.  After creating the new profile, I went back to the old one in order to figure out all of my bookmarks, etc. in order to copy them over to the new and ... *voila!* ... suddenly the old profile is working perfectly again.  I have now deleted the new profile that I created and am using my original profile again.  

I'm obviously way out of my element here.  But from what I can tell, I have returned to my original settings and yet the original problem does not exist anymore.  Sooo weird.

---

### Post by nanotube on 2010-01-09
heh yea, weird indeed! 

well at least now you know what to do if the problem ever comes back :)

---

### Post by noob555 on 2010-01-09
Whatever works, that's my motto.  Thanks again.

---

### Post by BikeHelmet on 2010-01-10
I've got the same problem - on three OS's. (Win2k, WinXP, Ubuntu)

If I figure out what's causing it, I'll post back. ;)

Edit: Okay, that didn't take long. It's the ghostery addon. Disable it and restart Firefox (plus kill the process), then re-enable it, and the problem goes away.

---

### Post by nanotube on 2010-01-10
bikehelmet: awesome work! :)

---

### Post by nuchdog on 2011-10-30
If you don't have ghostery installed, there are several other reasons this can happen.  The most common is that the permissions to your profile file are wrong.  Check ~/.mozilla/firefox/profiles.ini to make sure that it is read and write enabled for your user.  If not: 

sudo chmod 777 ~/.mozilla/firefox/profiles.ini

---

### Post by Sef on 2011-11-01
Necromancing, so locked.

---

