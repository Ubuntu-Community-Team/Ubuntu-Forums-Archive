---
title: "Inkscape 1.0.1 in UbuntuStudio 20.04"
date: 2020-11-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Nosphky on 2020-11-28
Around a couple of weeks' ago, if I recall correctly, an Inkscape upgrade arrived through the Ubuntu updates and that took me to Inkscape 1.0.1.  Since that time, I get frequent occurrences of instability when working on existing files. This shows as distorted displays from time to time with subsequent recovery. Sometimes I get apparent computer lockups. I've had three of these lockups. When it occurs, all I can do is move the cursor with the mouse. Nothing else on the machine or keyboard works and I have to wait around 5 minutes before normal operation can be resumed.

I've been using Inkscape for more than 5 - 6 years with never a problem. A couple of years or so ago, Inkscape changed the images' dpi from 90 to 96dpi but that never gave any problem.

I've downgraded to version 0.92.5 and not had any further problems since. I hope it stays that way.

Has anybody else noticed any problems on Ubuntu with the latest Inkscape upgrade?

---

### Post by CatKiller on 2020-11-28
> **Nosphky said:**
> Around a couple of weeks' ago, if I recall correctly, an Inkscape upgrade arrived through the Ubuntu updates and that took me to Inkscape 1.0.1. 

Ubuntu doesn't do that: packages don't get updated to new versions, but get security and bug fixes backported, with very few exceptions. Inkscape isn't one of those exceptions. That suggests that you were either using a PPA or you installed the snap version. 

> Sometimes I get apparent computer lockups. I've had three of these lockups. When it occurs, all I can do is move the cursor with the mouse. Nothing else on the machine or keyboard works and I have to wait around 5 minutes before normal operation can be resumed. 

Those are classic out-of-memory symptoms.

---

### Post by DuckHook on 2020-11-28
> **CatKiller said:**
> …That suggests that you were either using a PPA or you installed the snap version.
&#8593;+1
Snap version is, indeed, 1.0.1. Repo version is 0.92.5
@Nosphky
Snaps have caused me problems on other packages too. I stick with repo versions whenever they are available.
> Those are classic out-of-memory symptoms.
&#8593;Again +1
@Nosphky
What amount of RAM do you have, and do you have option to increase it? Graphics apps are notoriously memory&#8209;intensive and the big three (GIMP, Inkscape & Scribus) especially so. If you increase your RAM, you may be able to use the newer snap version (if so desired).

---

### Post by ajgreeny on 2020-11-28
There is a PPA for inkscape at [https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable?field.series_filter=focal](https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable?field.series_filter=focal) which has version 1.0.1.
I've not used it but it might be worth trying.

---

### Post by Nosphky on 2020-11-28
Thanks for your replies: Catkiller, DuckHook, ajgreeny.  You jogged my memory - I do use a PPA for Inkscape and have done so since a long time. (the list of PPA's is not in the same place in Settings Manager in US 20.04 and it took me a moment or two to confirm).

So it must have been an update in the PPA - and I've been working in 0.92.5 for over ten hours without any problem since I downgraded back to that version.

I agree that the apparent lockups sound like a classic case of memory shortage. I have 32gigs of RAM and if I remember well, I think there are a couple of spare slots on the motherboard but I've never had memory problems in the past 5 or 6 years and I do a lot of stuff in Gimp, Inkscape, and some of the video editors.

I'll have to have a check and see what added features v1.0.1 offered over and above 0.92.5. I must say that I didn't notice any advantages to me in the work that I do on Inkscape so I'm happy enough with 0.92.5

---

### Post by DuckHook on 2020-11-28
> **Nosphky said:**
> I have 32gigs of RAM
32 Gigs?!

Your RAM is **not** the problem then. Not unless you routinely manipulate gargantuan graphics like this one: [https://www.spacetelescope.org/images/heic1502a/](https://www.spacetelescope.org/images/heic1502a/)

Even then, 32 GB will easily handle numerous such images.
> I'll have to have a check and see what added features v1.0.1 offered over and above 0.92.5. I must say that I didn't notice any advantages to me in the work that I do on Inkscape so I'm happy enough with 0.92.5
I like the KISS principle when it comes to production work. Perhaps you may want to experiment on a VM, but keep your base install clean and simple. While you are at it, you may wish to re-assess any other PPA, in keeping with that same KISS principle.

---

### Post by CatKiller on 2020-11-28
> **DuckHook said:**
> 32 Gigs?!

Your RAM is **not** the problem then.
Could be. Memory leak, or memory leak elsewhere exacerbated by a large edit history, or large files, in Inkscape. Easy enough to monitor.

---

### Post by DuckHook on 2020-11-28
> **CatKiller said:**
> …Easy enough to monitor.
Very true, this.

I was responding to OP's implied query that it might be necessary to populate his remaining memory slots with more RAM. In my opinion, this is an unnecessary expense and won't solve a memory leak problem anyway. Also, if he is maxing out memory due to massive edit caches, etc, this would likely have also occurred under the older version.

@Nosphky

CatKiller is quite right: your symptoms could point to memory leak or other memory issue. Given that you are happy with an older version of Inkscape, my advice is still to to stick with 0.92.5 (which is the one native to Focal anyway) and leave well enough alone. You could try running 1.0.1 within a VM of Groovy (Ubuntu 20.10) to which it is native. See if the same problems crop up. Please be forwarned that running intensive graphic manipulation apps like Inkscape inside a VM can be a slow and gruelling exercise which make them fundmentally impractical.

---

### Post by Nosphky on 2020-11-29
My Inkscape .svg files are not very large. In fact, I'd say they are pretty small - mostly around 50kb, largest 120kb. I have LO Writer files with embedded graphics that are much larger, of the order of 4 to 5 MB.

I can't exclude that my US system has some random problem but Inkscape 0.92.5 works fine for me and that's where I'm staying for image creation.

Curiously, though, I've been using UbuntuStudio since 14.04 LTS and I've seen some things happen with 20.04 that surprised me. I've used Sigil for ebook work for several years, originally building my own copy because it wasn't in the distro. With 20.04, Sigil is included but it takes 32 seconds for the first instance to appear on screen after launch. Further instances take 25 seconds. Almost all other applications are pretty well instantaneous - even launching LO suite for the first time each day takes only a couple of seconds.

I always make a clean install of a new os and 20.04 was no exception.  After about 3 weeks of using 20.04, I realised that I had never seen the screensaver come into operation so I had a little time to investigate and found over several days that although the xscreensaver process had been correctly started and running, it never kicked the screensaver to display. In the automatic start-up processes, I saw that the distro was calling xscreensaver via a script. Looking at that script made me think that it was also connected with the power manager. Power management is of more interest to a laptop operator than for a desktop machine, so I arranged for start-up to call xscreensaver directly. Never had any more problems with the screen saver.

Maybe the devs put laptops before desk-tops these days. Probably a logical thing to do.

Curiously, though, if I ever wish to see what beautiful image is displaying with the screensaver, calling the settings manager > screensaver takes also about 25 seconds to display.  

So the screensaver settings manager and Sigil are the only 2 applications I've found so far which take such a time to start. This is hardly the mark of a random problem since it is systematic with these 2 apps. But once started, they run perfectly so I just live with it.

Another curiosity is the blueman app. My machine gets freshly booted up each day. Around 80% of the days, there is an error message in the middle of the screen inviting me to send in a report. This error message concerns the blueman app and a file that cannot be found where expected. I checked, and the file is where it should be. In any case, Bluetooth works correctly so it is possible a question of timing.

---

