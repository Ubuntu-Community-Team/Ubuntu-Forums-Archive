---
title: "Wine"
date: 2010-08-04
forum: Wine
---

### Post by ujoni08 on 2010-08-04
I've just installed Wine. How do I use it? I can see a wine glass under 'applications', but don't know what to do next. I am aiming to run Garmin Forerunner 405 software, and have found a thread on here that says to install Wine, then install the Windows version of Firefox, then, in Wine, to install the Garmin software. Trouble is, I don't know what 'in Wine' means (i.e. don't know how to be 'in Wine').
Thanks,
Jon

---

### Post by Bertus_Nel on 2010-08-04
Hi

Right click on your application (exe) and select Open with wine windows program loader, that should do the trick.;)

---

### Post by ujoni08 on 2010-08-04
Thanks, but what I need to do is follow these steps, taken from another thread (before I install the Garmin software and run a live update on it):

--------------------------------------------------------------------------------------

 				 				**Re: garmin communicator** 			
 			 			 		   		 		 		After doing a little googling, the only thing I can think of would be to:

1) install wine
2) install the windows version of Firefox in wine
3) install the windows version of garmin communicator in wine.  It should install to the windows Firefox.
4) To do the garmin stuff, navigate using the windows version of Firefox installed in #2 above.

The only garmin experience I have in Linux is doing the updates for my nuvi.  I do them using wine and they work perfectly.

Good Luck.

------------------------------------------------------------------------------

So can someone tell me how to go after step 1 above? Obviously I have the Ubuntu version of Firefox. I don't know how to be 'in wine'. What do I do to open/run it, and what does it look like?

Thanks,

Jon

---

### Post by drewsus on 2010-08-04
> **Bertus_Nel said:**
> Hi

Right click on your application (exe) and select Open with wine windows program loader, that should do the trick.;)

Do what Bertus_Nel said...
And from those steps you listed, replace "*in* wine" with "*with* wine" and it should make more sense to you. 

Once a program has been installed *with* wine, go to your main menu to find the wine menu for launching programs installed *with* wine.

---

### Post by Vaphell on 2010-08-04
download windows installer of firefox from mozilla.com, right-click it, choose 'open with wine', proceed with installation, do the same with your app, done

---

### Post by ujoni08 on 2010-08-04
Thanks for the replies. I am not at that stage yet, as I am unable to download and install Firefox for Windows (which I need to download the Garmin Communicator software). Ubuntu doesn't trust the source, and won't allow it to be executable. Any ideas? BTW I am new to Ubuntu, so replies will need to talk me through processes.
Jon

---

### Post by ujoni08 on 2010-08-04
Vaphell: thanks, I will try that.
Jon

---

### Post by leucippus on 2010-08-04
> **ujoni08 said:**
>  Ubuntu doesn't trust the source, and won't allow it to be executable. Any ideas? BTW I am new to Ubuntu, so replies will need to talk me through processes.
Jon


Try right clicking on the .exe file and view "properties" and check the "permissions" tab and make sure the little box is checked.

---

### Post by ujoni08 on 2010-08-04
I downloaded the Windows version of Firefox, then right-clicked it and chose 'open with Wine Windows programme loader', but it says:
------------------------------------------------------------------------

The file '/home/jonathan/Downloads/Firefox Setup 3.6.8.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

-----------------------------------------------------------------------

Anything I can do?

Jon

---

### Post by ujoni08 on 2010-08-04
Leuccipus, thanks, that worked. I am now going to try to download and install the Garmin software.
Jon

---

### Post by inameiname on 2010-08-04
This isn't really the point of this thread, but why would you install Firefox's window version under Wine in a Linux distribution, when the Firefox's Linux version works just fine? Now, I understand in regards to installing Internet Explorer, though I never need it, but Firefox? Of course, I read that the Garmin Software requires it. Never heard of that.

---

### Post by Vaphell on 2010-08-04
if the Garmin Software is windows only and it expects to hook into windows firefox, there is nothing you can do - linux ff doesn't exist in its world. Yes, it doesn't make any sense for the ff plugin not to be OS agnostic, but apparently that's the case here as quick googling shows.

---

### Post by inameiname on 2010-08-04
Yeah, I figured that. I don't know what Garmin software is so guess that should be my first thing to research before actually posting. :P

---

### Post by dardack on 2010-08-05
> **inameiname said:**
> This isn't really the point of this thread, but why would you install Firefox's window version under Wine in a Linux distribution, when the Firefox's Linux version works just fine? Now, I understand in regards to installing Internet Explorer, though I never need it, but Firefox? Of course, I read that the Garmin Software requires it. Never heard of that.

Also, I hear FF windows version is faster in wine then FF linux version native.  Personally I use chromium.

---

### Post by inameiname on 2010-08-05
Really? I don't really notice a difference in speed between the Windows and Linux versions in tests but perhaps. It also depends on the number of add-ons people have as well. Nonetheless, for speed, I just use Opera as it's the fastest alive right now.

---

