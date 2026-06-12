---
title: "KXStudio - questions / answers"
date: 2011-05-31
forum: Ubuntu Studio
---

### Post by wbm on 2011-05-31
I am running a fresh install of Kubuntu 11.04 and added KXStudio per the instructions on the web site.

I have a few questions:

1. What is Cadence?

2. Is there documentation for Cadence? How to configure it, what all those options and settings mean and do?

3. In KDE based KXStudio, do I need Pulse Audio or can I leave that off?
E.g. Pulse_JACK Bridge leave it stopped?
It appears only my beloved Rhythmbox needs it, and turning it on causes all kinds of weird sound issues. I'd rather switch to Clementine and live a peaceful life ;)

4. What are Catarina, Catia and Claudia? Is that an either or choice or do they all work together?
What is the big picture for those apps please?

5. Every time I log in KDE asks me to "forget" sound devices. Can I make my choices permanent? Somehow it ignores me clicking "Don't ask again".

---

### Post by ken78724 on 2011-06-01
WBM
cannot answer your ?s about the Cs or Jack. Am looking to upgrade tonight from kxstudio 10.04.02 amd 64 working off asusteck 500 gig hd w/4 gigs ram, not the PC described in my signature.

wbm, you may benefit from Alex's message to Janne on the UbuStu support group I frequent - "Ubuntu-Studio-users mailing list
[email]Ubuntu-Studio-users@lists.ubuntu.com[/email]" If one conversation does not apply maybe another will.
On Tuesday 31 of May 2011 02:54:53 Janne Jokitalo wrote: On Tue, May 31, 2011 at 01:54:34AM +0300, Alexandros Bitoulas wrote: Allright guys, I have just fixed the problem...with a trial and error method!
> <snip>
> > When I uninstalled "pavucontrol" ardour launched perfectly!! I also
> > uninstalled with autoremove "libcanberra-gtk-module" and
> > "libcanberra-gtk0" that pavucontrol automatically installed and which
> > might caused the problem in libgtk-x11-2.0.so.0.2400.4, as syslog was
> > informing me whenever I launched ardour   >>> etc., etc., If you want that help go to the site provided.

---

### Post by falkTX on 2011-06-08
> **wbm said:**
> I am running a fresh install of Kubuntu 11.04 and added KXStudio per the instructions on the web site.

I have a few questions:

1. What is Cadence?

Cadence is the new tools developed specially for KXStudio.
Just run it and try it...

> **wbm said:**
> 
2. Is there documentation for Cadence? How to configure it, what all those options and settings mean and do?

Although I've put Cadence installed by default in KXStudio, it's not a finished product.
I'll write some documentation soon, but there are some more important stuff first.

> **wbm said:**
> 
3. In KDE based KXStudio, do I need Pulse Audio or can I leave that off?
E.g. Pulse_JACK Bridge leave it stopped?
It appears only my beloved Rhythmbox needs it, and turning it on causes all kinds of weird sound issues. I'd rather switch to Clementine and live a peaceful life ;)

You can leave pulseaudio off, if you won't use any pulseaudio apps.
Most Gnome apps use pulse though. For clementine, you can set audio output to "jacksink".

> **wbm said:**
> 
4. What are Catarina, Catia and Claudia? Is that an either or choice or do they all work together?
What is the big picture for those apps please?

They are part of Cadence, each app has it's own functionality.
the main "cadence" app explains them a bit, but not much.
like I said, documentation will come later.

> **wbm said:**
> 
5. Every time I log in KDE asks me to "forget" sound devices. Can I make my choices permanent? Somehow it ignores me clicking "Don't ask again".
If you find a way to disable that dialog, let me know.
It's a pain in the *** and I don't know how to disable that (yet).

---

### Post by wbm on 2011-06-09
Thanks :)

Around June 8th 2011 (depending on time zone) a bunch of updates showed up.
Among them were updates to "KXSTudio default settings" (I paraphrase as I can't remember the exact name).

Do we need to run the "KXStudio Welcome" after any of these updates for the new settings to take affect?
If yes, which one, "Basic Reset" or "Force Reset of all settings".
Thanks!

---

### Post by falkTX on 2011-06-09
> **wbm said:**
> Thanks :)

Around June 8th 2011 (depending on time zone) a bunch of updates showed up.
Among them were updates to "KXSTudio default settings" (I paraphrase as I can't remember the exact name).

Do we need to run the "KXStudio Welcome" after any of these updates for the new settings to take affect?
If yes, which one, "Basic Reset" or "Force Reset of all settings".
Thanks!

You don't need to run the welcome wizard again.
If for some reason you did, I would post something in the news first.

These packages are updated when other KXStudio is updated too, since they all come from the same package.
So when I updated kxstudio-welcome or default-settings or scripts, the update brings them all at once.

---

### Post by wbm on 2011-06-09
> **falkTX said:**
> 

If you find a way to disable that dialog, let me know.
It's a pain in the *** and I don't know how to disable that (yet).


I actually did find a way (at a price though)

I could not take it anymore and these different sound settings and various audio devices being enabled/disabled also messed with Jack, general settings and it was a constant battle to re-sync all my settings.

Background:
I use an external Audio interface, the Tascam US122 for ALL my audio in and out.

Solution:
1. During startup I went into the computer BIOS and disabled Audio. On my computer it just says Audio: Enable or Disable. I chose disable.
2. I don't use my USB web cam on that machine anymore.
Now I only have 1 audio device, the Tascam US122.

The price I had to pay:
1. I could not log out, restart or shutdown anymore.
To fix that I had to go into System Settings < System Notification Configuration < Manage Notifications < Player Settings
I changed it to "No Audio output"
Apparently the computer tries to "Beep" right after one choses Logout, restart or shutdown. With the internal sound card disabled it could not do that.

2. I cannot Skype from that machine anymore. Actually I could, if I plug the USB camera in, resetting a bunch of audio settings and it would work. But that's what I was trying to avoid.

3. I also switched various other notifications from "Beep" to "Pop up" just for good measure.

---

### Post by wbm on 2011-06-14
A few weeks later:
Mostly everything works as expected.

2 more issues though:
1. Blender (2.5 SVN) does not start up.
Blender Fullscreen 2.49 and Blender Windowed start up fine

2. Scribus looks horrible
FalkTX, it looks like LibreOffice all black as seen on your web site before the fix. Is there a similar fix for Scribus (v1.3.3.13svn)?

---

### Post by falkTX on 2011-06-14
> **wbm said:**
> A few weeks later:
Mostly everything works as expected.

2 more issues though:
1. Blender (2.5 SVN) does not start up.
Blender Fullscreen 2.49 and Blender Windowed start up fine

2. Scribus looks horrible
FalkTX, it looks like LibreOffice all black as seen on your web site before the fix. Is there a similar fix for Scribus (v1.3.3.13svn)?

The Blender 2.5 package has some install issues (Natty only).
Go to the official blender website and download their own build for now.

Scribus is using the very old Qt3. You can reset the Qt3 colors by editing '~/.qt/qtrc' and comment these lines:
```
[Palette]
#active=#f0f0f0^e#1c1c1c^e#111111^e#9b9b9b^e#222222^e#5e5e5e^e#e6e6e6^e#ffffff^e#f0f0f0^e#070707^e#111111^e#9b9b9b^e#282828^e#ffffff^e#6464e6^e#e664e6
#disabled=#535353^e#181818^e#111111^e#9b9b9b^e#222222^e#5e5e5e^e#4a4a4a^e#ffffff^e#5a5a5a^e#111111^e#111111^e#9b9b9b^e#0e0e0e^e#535353^e#22224a^e#4a224a
#inactive=#f0f0f0^e#1c1c1c^e#111111^e#9b9b9b^e#222222^e#5e5e5e^e#e6e6e6^e#ffffff^e#f0f0f0^e#070707^e#111111^e#9b9b9b^e#282828^e#ffffff^e#6464e6^e#e664e6

```
Still, Scribus will still look bad anyway, due that is using Qt3.

---

### Post by wbm on 2011-06-14
> **falkTX said:**
> The Blender 2.5 package has some install issues (Natty only).
Go to the official blender website and download their own build for now.

Scribus is using the very old Qt3. You can reset the Qt3 colors by editing '~/.qt/qtrc' and comment these lines:
```
[Palette]
#active=#f0f0f0^e#1c1c1c^e#111111^e#9b9b9b^e#222222^e#5e5e5e^e#e6e6e6^e#ffffff^e#f0f0f0^e#070707^e#111111^e#9b9b9b^e#282828^e#ffffff^e#6464e6^e#e664e6
#disabled=#535353^e#181818^e#111111^e#9b9b9b^e#222222^e#5e5e5e^e#4a4a4a^e#ffffff^e#5a5a5a^e#111111^e#111111^e#9b9b9b^e#0e0e0e^e#535353^e#22224a^e#4a224a
#inactive=#f0f0f0^e#1c1c1c^e#111111^e#9b9b9b^e#222222^e#5e5e5e^e#e6e6e6^e#ffffff^e#f0f0f0^e#070707^e#111111^e#9b9b9b^e#282828^e#ffffff^e#6464e6^e#e664e6

```
Still, Scribus will still look bad anyway, due that is using Qt3.

Thank you! Again :)
Blender, I'll give them another month and hope the newer version will show up in the repositories before I "go direct". 
For Scribus, I'll give that a try.
Btw, the newer NG version looks and works great.

---

### Post by isaacj87 on 2011-06-14
I tried the method of using Kubuntu 11.04 as a base and adding the KXStudio repos. Everything installs just fine, but I had some trouble with JACK.

So, I decided to use what works for me. I've been using KXStudio 10.04.2 (the DVD release, which is great). I tried using 10.04.3, but for whatever reason I would get terrible xruns even on my custom RT kernel. 

Are the repositories in the 10.04.2 release still maintained? Also, I remember at some point a non-free repo was added which included software like Renoise and Reaper. Is there any chance I can add and use that in 10.04.2?

Thanks!

---

### Post by falkTX on 2011-06-14
> **wbm said:**
> Btw, the newer NG version looks and works great.

The NG version uses Qt4, so it look just like any other app in the system.

---

### Post by falkTX on 2011-06-14
> **isaacj87 said:**
> I tried the method of using Kubuntu 11.04 as a base and adding the KXStudio repos. Everything installs just fine, but I had some trouble with JACK.

So, I decided to use what works for me. I've been using KXStudio 10.04.2 (the DVD release, which is great). I tried using 10.04.3, but for whatever reason I would get terrible xruns even on my custom RT kernel. 

Are the repositories in the 10.04.2 release still maintained? Also, I remember at some point a non-free repo was added which included software like Renoise and Reaper. Is there any chance I can add and use that in 10.04.2?

Thanks!

You're forgetting that:
KXStudio 10.04.3 = KXStudio 10.04.2 + Updates

The repositories were changed after the 10.04.3 released. The old ones are not maintained anymore.
You'll actually get the new repositories as part of the update...

I'm sure there's a perfectly good reason why you got extra xruns, and you should really try to understand why and "fix" it.
I'm here to help you of course ;)


PS: [New] Complete DVD ISOs should come next month.

---

### Post by isaacj87 on 2011-06-14
> **falkTX said:**
> You're forgetting that:
KXStudio 10.04.3 = KXStudio 10.04.2 + Updates

The repositories were changed after the 10.04.3 released. The old ones are not maintained anymore.
You'll actually get the new repositories as part of the update...

I'm sure there's a perfectly good reason why you got extra xruns, and you should really try to understand why and "fix" it.
I'm here to help you of course ;)


PS: [New] Complete DVD ISOs should come next month.

I'm glad to hear your going to release ISOs again. I figured as much about 10.04.3 and the old Lucid repos, but 10.04.2 was a really solid release. I was spending more time compiling kernels and fixing issues than I was recording music. You probably know better than anyone else how that goes. ;)

I'm actually about to migrate over to my studio comp. I used a tutorial from [http://webcache.googleusercontent.com/search?q=cache:NOyzx4zLiyQJ:www.joegiampaoli.com/blog/%3Fp%3D462+joe+m-audio+fast+track+pro&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a&source=www.google.com]("http://webcache.googleusercontent.com/search?q=cache:NOyzx4zLiyQJ:www.joegiampaoli.com/blog/%3Fp%3D462+joe+m-audio+fast+track+pro&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a&source=www.google.com") to compile a kernel (2.6.31-rt) for my I/O box. I assumed that was the reason I was having difficulties in the new versions of KXStudio. I was getting an overload of xruns. I'll upgrade my system and if there are errors, I'll get some real outputs.

Thanks for the response and all the hard work.

---

### Post by stanlea on 2011-06-14
Two things : (in fact three)

1
I tried the new Carla tool, the concept is nice but actually, it produces glitches and a lot of xruns. I guess it's due to the fact it's a work in progress.

2
I finallly got Reaktor (standalone) working after switching to Alsa instead of Jack in the Wine audio panel. It doesn't changes anything.

3
Why ISOs ? I thought that KX was now a rolling distro ?

---

### Post by falkTX on 2011-06-14
> **isaacj87 said:**
> I'm actually about to migrate over to my studio comp. I used a tutorial from [http://webcache.googleusercontent.com/search?q=cache:NOyzx4zLiyQJ:www.joegiampaoli.com/blog/%3Fp%3D462+joe+m-audio+fast+track+pro&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a&source=www.google.com]("http://webcache.googleusercontent.com/search?q=cache:NOyzx4zLiyQJ:www.joegiampaoli.com/blog/%3Fp%3D462+joe+m-audio+fast+track+pro&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a&source=www.google.com") to compile a kernel (2.6.31-rt) for my I/O box. I assumed that was the reason I was having difficulties in the new versions of KXStudio. I was getting an overload of xruns. I'll upgrade my system and if there are errors, I'll get some real outputs.

This kernel (2.6.31) is getting really old now, so is 2.6.33 too...
*(What are the RT kernel guys doing...?)*

The kernel I recommend to use now is 2.6.38-lowlatency.
The new PPAs have it for Lucid, Maverick and Natty.

---

### Post by falkTX on 2011-06-14
> **stanlea said:**
> Two things : (in fact three)

1
I tried the new Carla tool, the concept is nice but actually, it produces glitches and a lot of xruns. I guess it's due to the fact it's a work in progress.
[QUOTE=stanlea;10939316]
I know that are issues if you use plain Lucid and these tools, due to an old PyQt version (most people use kxstudio-repos, which updates PyQt to a more recent and better version).
The Antialiasing and OpenGL can mess-up the canvas a little, but it should be by default... What specific issues are you talking about?

2
I finallly got Reaktor (standalone) working after switching to Alsa instead of Jack in the Wine audio panel. It doesn't changes anything.
> **stanlea said:**
> 
Using ALSA as audio output can fix the MIDI part (if you use WineASIO for sound),
but any app that doesn't support ASIO will not be able to output sound properly though...

3
Why ISOs ? I thought that KX was now a rolling distro ?[/QUOTE]
It is, but ISOs can avoid, for example, this situation:
 - User wants to install KXStudio, so it has to:
 - Download Ubuntu (700Mb)
 - Install Ubuntu (~20Mins)
 - Upgrade to KXStudio (+500Mb, ~1h)

With an ISO, the user downloads it (~1.5Gb), and installs (~30Mins).
Much faster...

---

### Post by isaacj87 on 2011-06-15
> **isaacj87 said:**
> I'm glad to hear your going to release ISOs again. I figured as much about 10.04.3 and the old Lucid repos, but 10.04.2 was a really solid release. I was spending more time compiling kernels and fixing issues than I was recording music. You probably know better than anyone else how that goes. ;)

I'm actually about to migrate over to my studio comp. I used a tutorial from [http://webcache.googleusercontent.com/search?q=cache:NOyzx4zLiyQJ:www.joegiampaoli.com/blog/%3Fp%3D462+joe+m-audio+fast+track+pro&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a&source=www.google.com]("http://webcache.googleusercontent.com/search?q=cache:NOyzx4zLiyQJ:www.joegiampaoli.com/blog/%3Fp%3D462+joe+m-audio+fast+track+pro&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a&source=www.google.com") to compile a kernel (2.6.31-rt) for my I/O box. I assumed that was the reason I was having difficulties in the new versions of KXStudio. I was getting an overload of xruns. I'll upgrade my system and if there are errors, I'll get some real outputs.

Thanks for the response and all the hard work.

Well, it's official: I have to eat my own words. I started over with Kubuntu 11.04 x86_64 as a base. Installed my M-Audio FTP kernel (.31-rt). Fought and (finally) compiled the latest Nvidia driver (275.09.07) against the kernel. (I had to fix the TTY/Ctrl+Alt+F1-6 terminals). Added the KXstudio repos per instructions and updated. I have to say that everything is working quite smooth. I get only infrequent xruns (mostly when starting apps) at 2.9 ms latency (24bit|44.1KHz)!

A few questions:

1) DSP Load - I understand that this will probably vary depending on the user's hardware, but is it important to keep an eye on the current load? I average about 20-30% when stressing my comp.

2) Cadence - This is my first time using it, so forgive my ignorance. I understand the purpose of the Pulse-JACK bridge, but what exactly does the ALSA Audio Bridge option do? I currently have it set to JACK.

All in all, I am very impressed. You've made it so easy to get audio production in Linux working. I've been a huge fan of KXStudio since its first release and this release only reinforces that. Definitely a bright future for KXStudio. I shouldn't of been so hesitant on jumping to the new release.

On a related note, I've been looking around [here]("http://kxstudio.git.sourceforge.net/git/gitweb.cgi?p=kxstudio/kxstudio;a=summary") and I can't find Cadence. Did you not push it to your Git yet?

P.S. Users getting system lockups or texture corruption (when resizing) on Kubuntu 11.04 with Nvidia cards should update the driver. Driver 275.09.07 fixes the issues with KDE4 and X 1.10.

---

### Post by falkTX on 2011-06-15
> **isaacj87 said:**
> Well, it's official: I have to eat my own words. I started over with Kubuntu 11.04 x86_64 as a base. Installed my M-Audio FTP kernel (.31-rt). Fought and (finally) compiled the latest Nvidia driver (275.09.07) against the kernel. (I had to fix the TTY/Ctrl+Alt+F1-6 terminals). Added the KXstudio repos per instructions and updated. I have to say that everything is working quite smooth. I get only infrequent xruns (mostly when starting apps) at 2.9 ms latency (24bit|44.1KHz)!

A few questions:

1) DSP Load - I understand that this will probably vary depending on the user's hardware, but is it important to keep an eye on the current load? I average about 20-30% when stressing my comp.

2) Cadence - This is my first time using it, so forgive my ignorance. I understand the purpose of the Pulse-JACK bridge, but what exactly does the ALSA Audio Bridge option do? I currently have it set to JACK.

All in all, I am very impressed. You've made it so easy to get audio production in Linux working. I've been a huge fan of KXStudio since its first release and this release only reinforces that. Definitely a bright future for KXStudio. I shouldn't of been so hesitant on jumping to the new release.

On a related note, I've been looking around [here]("http://kxstudio.git.sourceforge.net/git/gitweb.cgi?p=kxstudio/kxstudio;a=summary") and I can't find Cadence. Did you not push it to your Git yet?

P.S. Users getting system lockups or texture corruption (when resizing) on Kubuntu 11.04 with Nvidia cards should update the driver. Driver 275.09.07 fixes the issues with KDE4 and X 1.10.


Hey again,

1 - The lower the JACK buffer size, the higher the cpu, as expected.
If you don't already know, you can do Alt+Shift+F12 to toggle KWin effects on/off.
I know that on Natty sometimes the kde daemon crash and hang the cpu.
If that happens, you'll have to kill it manually (Use Ctrl+Esc, sort by cpu usage, right click and kill)

2 - The ALSA bridge adjust the ~/.asoundrc file. This is used, for example, by Firefox and Flash (Youtube etc).
I'll support custom files some day...


The Cadence code is hosted outside KXStudio, because these tools are not KXStudio specific.
All KXStudio apps info here:
[http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Applications](http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Applications)

For Cadence, the code page is:
[http://repo.or.cz/w/cadence.git](http://repo.or.cz/w/cadence.git)
There's no real website or documentation for it, yet...

---

### Post by isaacj87 on 2011-06-15
> **falkTX said:**
> Hey again,

1 - The lower the JACK buffer size, the higher the cpu, as expected.
If you don't already know, you can do Alt+Shift+F12 to toggle KWin effects on/off.
I know that on Natty sometimes the kde daemon crash and hang the cpu.
If that happens, you'll have to kill it manually (Use Ctrl+Esc, sort by cpu usage, right click and kill)

2 - The ALSA bridge adjust the ~/.asoundrc file. This is used, for example, by Firefox and Flash (Youtube etc).
I'll support custom files some day...


The Cadence code is hosted outside KXStudio, because these tools are not KXStudio specific.
All KXStudio apps info here:
[http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Applications](http://kxstudio.sourceforge.net/mediawiki/index.php/KXStudio:Applications)

For Cadence, the code page is:
[http://repo.or.cz/w/cadence.git](http://repo.or.cz/w/cadence.git)
There's no real website or documentation for it, yet...

Thanks for the tips. I've added my Nvidia card to rtirq at a higher priority. It seems to be working okay. I love eye-candy, so unless I run into terrible problems, I leave them on.

I pulled a copy of Cadence from your Git. I ran 'make' but the build failed. The INSTALL file instructions are missing a build-dep:
```
qt4-dev-tools
```

After I installed that I was good to go. On a slightly off-topic note, have you checked out Github? AFAIK, it's free, public hosting (with some paid options as well). The web interface is very pleasant to use and easy to read. I think you can have as many repos as you want as well. You can see my github here: [https://github.com/isaacj87]("https://github.com/isaacj87")

---

### Post by falkTX on 2011-06-15
> **isaacj87 said:**
> Thanks for the tips. I've added my Nvidia card to rtirq at a higher priority. It seems to be working okay. I love eye-candy, so unless I run into terrible problems, I leave them on.

I pulled a copy of Cadence from your Git. I ran 'make' but the build failed. The INSTALL file instructions are missing a build-dep:
```
qt4-dev-tools
```

After I installed that I was good to go. On a slightly off-topic note, have you checked out Github? AFAIK, it's free, public hosting (with some paid options as well). The web interface is very pleasant to use and easy to read. I think you can have as many repos as you want as well. You can see my github here: [https://github.com/isaacj87]("https://github.com/isaacj87")

I thought about gitub but most of the projects I care about (jack2 and ladish) use repo.or.cz, so I used this.

GitHub can sometimes be complicated (try downloading a tarball of a specific, not master, branch).

Anyway, thanks for the suggestions.

---

### Post by akavir on 2011-06-15
If you want the rundown on these apps, I just did a review this past weekend on my 'Linux In Review' blog, it details the cadence apps and more with YouTube video.  Check it out at [http://i2productions.com/lir](http://i2productions.com/lir). I do reviews on distro, and specificly audio distros and software.

---

### Post by stanlea on 2011-06-16
I want to insist a little about Carla. My system is up to date with all the KX repos on. When I load any plugin with Carla (lv2, dssi, lapsda, vst), I get a lot of xruns, midi out of sync et crackles. I don't understand why. Is there something I can test or log ?

---

### Post by falkTX on 2011-06-16
> **stanlea said:**
> I want to insist a little about Carla. My system is up to date with all the KX repos on. When I load any plugin with Carla (lv2, dssi, lapsda, vst), I get a lot of xruns, midi out of sync et crackles. I don't understand why. Is there something I can test or log ?

Carla is due to a rework (not rewrite) very soon (already started for LADSPA), so any current tests are useless (the app is about to change).

xruns probably happen because the GUI is written in python, and I need a better mechanism to handle the audio backend <-> GUI callbacks.

Carla is the app that it's gonna take a lot of time before is ready even for simple usage, so don't waste too much time with it right now...

---

### Post by stanlea on 2011-06-18
Thanks for the info on Carla falkTX. Hem... and if you could change the name to Lisa, Carmen or any other, it wouldn't remind me of our french first lady. :D I'll deal with Jost if I really need a vst. Not a big deal.

Another question : is there a way, in Claudia, to add manually an entry in the app list shown when I hit shift F2 ?

---

### Post by falkTX on 2011-06-18
> **stanlea said:**
> Thanks for the info on Carla falkTX. Hem... and if you could change the name to Lisa, Carmen or any other, it wouldn't remind me of our french first lady. :D I'll deal with Jost if I really need a vst. Not a big deal.
Hm... even if I change the name to Lisa or Carmen, what guarantees do I have someone will not complain about his mother's name...?

> **stanlea said:**
> Another question : is there a way, in Claudia, to add manually an entry in the app list shown when I hit shift F2 ?

Yes, Claudia uses the same database as 'Klaudia', just get the source and look at src/database.py
(apt-get source claudia [or klaudia])

I'm happy to receive requests on this. What app(s) are you thinking about?

---

### Post by stanlea on 2011-06-18
At first glance, Ardour 3, Minicomputer, din, synthofnoise, the CLAM suite.

---

### Post by stanlea on 2011-06-19
Another issue : with le "last" updates via synaptic, the KX LV2 meta package is broken due to a conflict between two versions of vocproc. Any possibility to solve the problem ? I can't make force version.

---

### Post by isaacj87 on 2011-06-19
Quick question, I have most of the available VST packages installed from the repos and they don't show up in Festige. I've added '/usr/lib/vst/' to my dir paths, but they still don't show up. What am I doing wrong?

For the record, Addictive Drums is showing up and works fine.

---

### Post by stanlea on 2011-06-19
Festige is for windows natives dll, not for linux vst. 
You can use some hosts like EnergyXT or renoise if you want to use linux vst.
There is also a vst host called jost, unstable but usable if you don't load it too much.

[http://www.anticore.org/jucetice/?page_id=4](http://www.anticore.org/jucetice/?page_id=4)

---

### Post by isaacj87 on 2011-06-19
> **stanlea said:**
> Festige is for windows natives dll, not for linux vst. 
You can use some hosts like EnergyXT or renoise if you want to use linux vst.
There is also a vst host called jost, unstable but usable if you don't load it too much.

[http://www.anticore.org/jucetice/?page_id=4](http://www.anticore.org/jucetice/?page_id=4)

Thanks for the quick reply and tip! I'll have a look at Jost.

---

### Post by falkTX on 2011-06-19
> **stanlea said:**
> Another issue : with le "last" updates via synaptic, the KX LV2 meta package is broken due to a conflict between two versions of vocproc. Any possibility to solve the problem ? I can't make force version.

hey again, can you give me details about your system? (version, architecture, etc)
I'll try to fix this vocproc issue ASAP.


regarding klaudia, ardour3 is already there.
use the database.py file and you can add new apps there.
(I hope the file is easy to understand...)

---

### Post by stanlea on 2011-06-20
> **falkTX said:**
> hey again, can you give me details about your system? (version, architecture, etc)
I'll try to fix this vocproc issue ASAP.


regarding klaudia, ardour3 is already there.
use the database.py file and you can add new apps there.
(I hope the file is easy to understand...)

Natty Ubuntu studio 64 bits + KX repos
the kxstudio-meta-audio-plugins-lv2 appears broken

under synaptic, searching vocproc gives :

installed : vocproc 0.2-1build1 (which comes from repos natty/universe) : when I try to uninstall it, synaptic wants to uninstall 

kxstudio-meta-all
kxstudio-meta-audio-plugins
kxstudio-meta-audio-plugins-lv2

non installed (and cannot be forced) : vocproc-lv2 0.2-0ubuntu1~natty1 (from LP-PPA-kxstudio-team/natty

I think the 2 versions share the same info. But I can't do any update atm.


For claudia, no problem, I'll edit the database.py.

---

### Post by falkTX on 2011-06-20
> **stanlea said:**
> Natty Ubuntu studio 64 bits + KX repos
the kxstudio-meta-audio-plugins-lv2 appears broken

under synaptic, searching vocproc gives :

installed : vocproc 0.2-1build1 (which comes from repos natty/universe) : when I try to uninstall it, synaptic wants to uninstall 

kxstudio-meta-all
kxstudio-meta-audio-plugins
kxstudio-meta-audio-plugins-lv2

non installed (and cannot be forced) : vocproc-lv2 0.2-0ubuntu1~natty1 (from LP-PPA-kxstudio-team/natty

I think the 2 versions share the same info. But I can't do any update atm.


For claudia, no problem, I'll edit the database.py.

This is already fixed, but Ubuntu is now taking a long time to compile the 64bit packages...
An update will get this auto-fixed very soon.
(see the status here - [https://launchpad.net/~kxstudio-team/+archive/ppa/+build/2579091](https://launchpad.net/~kxstudio-team/+archive/ppa/+build/2579091))

I'll be happy to get a patch (or just a new file) for new klaudia/claudia apps.

---

### Post by stanlea on 2011-06-20
> **falkTX said:**
> I'll be happy to get a patch (or just a new file) for new klaudia/claudia apps.

You mean a new package for something not included in the studio ?

---

### Post by falkTX on 2011-06-20
> **stanlea said:**
> You mean a new package for something not included in the studio ?

An existent package that is not referred in the database, example follows.

Current code:
```
# Package || AppName || Type || Binary || Icon || Save || Level || License || Features[ ladspa, dssi, lv2, vst, vst-mode, transport, midi, midi-mode ] || Doc[ doc, website ]
( "ardour", "Ardour", "DAW", "ardour2", "ardour", "Auto", 1, "OpenSource", (1, 0, 1, 0, "", 1, 0, "ALSA"), ("file:///usr/share/kxstudio/docs/FM_Ardour_22Mar10.pdf", "http://www.ardour.org/") ),

```

New app example (in DAW group):
```
( "package-name", "AppName", "DAW", "app-binary", "app-", "Manual", 0, "OpenSource", (1, 0, 0, 0, "", 0, 0, "ALSA"), ("", "http://some-website.here/") ),

```

---

### Post by wbm on 2011-06-21
As I started this thread, forgive me to please ask another new question.
Now that I have the audio part mostly worked out, I started the midi stuff and immediately ran into an odd problem.

When I launch Yoshimi synth, most (not all) patches/instruments/sounds play the wrong notes. E.g. I play a C major scale and I hear something else. E.g. the keys seem to be mapped wrong. Just a very few instrument patches sound "correct". This happens both with the on screen keyboard or a USB midi controller keyboard. Any suggestions?
Thanks!

---

### Post by sgx on 2011-06-21
I would do a complete removal, and verify the sounds are gone, then install a different, older, or newer version, not the same one. 

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

[https://launchpad.net/~autostatic/+archive/ppa/+packages](https://launchpad.net/~autostatic/+archive/ppa/+packages)

and install a2jmidid, and launch that before yoshimi.

Cheers

---

### Post by falkTX on 2011-06-21
> **wbm said:**
> As I started this thread, forgive me to please ask another new question.
Now that I have the audio part mostly worked out, I started the midi stuff and immediately ran into an odd problem.

When I launch Yoshimi synth, most (not all) patches/instruments/sounds play the wrong notes. E.g. I play a C major scale and I hear something else. E.g. the keys seem to be mapped wrong. Just a very few instrument patches sound "correct". This happens both with the on screen keyboard or a USB midi controller keyboard. Any suggestions?
Thanks!

let me just update yoshimi to see if that's gets fixed (maybe it's a known bug?)
Is this yoshimi only, or does ZynAddSubFX behaves like this too?

---

### Post by wbm on 2011-06-21
> **falkTX said:**
> let me just update yoshimi to see if that's gets fixed (maybe it's a known bug?)
Is this yoshimi only, or does ZynAddSubFX behaves like this too?

I don't have ZynAddSubFX installed, but AMSyth works fine.
I think it's Yoshimi. You can check it by going e.g. to the Rhodes bank and using the virtual keyboard.
Number 67 and 68 RhodesPad1 and 2 work fine, but all other ones play their "own" scale when you play e.g. a C major scale keys.
This problem is with most banks/sounds.

PS: this happens on several installs/machines.

---

### Post by wbm on 2011-06-22
@falkTX: it works :) 

I assume you fixed Yoshimi? The 06/22/2011 update of Yoshimi fixed the wrong notes problem and it works now correctly.

Thank you so much. I hope it wasn't too much trouble.

---

### Post by isaacj87 on 2011-06-23
@falkTX

I really like Cadence. I actually prefer using it over qjackctl because it works better. One thing that didn't work was the "Clear Xruns" option in Services --> Jack Server. Opened it up in Qt4 designer and didn't see anything wrong. Looked at the "jack_clear_xruns" function, nope...Turns out it was missing the signal connect!

I added this after line 670 in cadence.py:

```
self.connect(self.act_jack_clear_xruns, SIGNAL("triggered()"), self.jack_clear_xruns)
```

I included a patch, but I don't know how to make proper patches. Hope this is helpful.

EDIT: UF won't let me upload the patch, but it's a one-liner anyways.

---

### Post by stanlea on 2011-06-23
Open Octave Midi canot build because it needs doxygen and KXstudio prevents doxygen to be installed. Any turnaround ?

---

### Post by falkTX on 2011-06-23
> **stanlea said:**
> Open Octave Midi canot build because it needs doxygen and KXstudio prevents doxygen to be installed. Any turnaround ?

Just build it without doxygen for now.

Which version and architecture are you using? (I need to fix this...)

PS: latest OpenOctave is available as oomidi-git, but it crashes with zynaddsubfx-dssi (remove it to clear the crash)

---

### Post by falkTX on 2011-06-23
> **wbm said:**
> @falkTX: it works :) 

I assume you fixed Yoshimi? The 06/22/2011 update of Yoshimi fixed the wrong notes problem and it works now correctly.

Thank you so much. I hope it wasn't too much trouble.

No trouble at all, I just updated the software (the new version seemed to have fix this, I haven't changed anything ;))

BTW, Out of date packages are considered bugs, so this one is double-fixed :P

---

### Post by falkTX on 2011-06-23
> **isaacj87 said:**
> @falkTX

I really like Cadence. I actually prefer using it over qjackctl because it works better. One thing that didn't work was the "Clear Xruns" option in Services --> Jack Server. Opened it up in Qt4 designer and didn't see anything wrong. Looked at the "jack_clear_xruns" function, nope...Turns out it was missing the signal connect!

I added this after line 670 in cadence.py:

```
self.connect(self.act_jack_clear_xruns, SIGNAL("triggered()"), self.jack_clear_xruns)
```

I included a patch, but I don't know how to make proper patches. Hope this is helpful.

EDIT: UF won't let me upload the patch, but it's a one-liner anyways.

Nice found!
I'll update the GIT code later (just re-formatted my pc to keep supporting Lucid, Natty had too much troubles....)

I usually use 'Kompare' to make patches. It's very simple:
1 - create a copy of the old file (usually "samename.orig")
2 - modify the new file as needed
3 - run kompare, and enter the old & new filepaths
4 - hit compare, then save a patch

you can also compare entire folders too

---

### Post by isaacj87 on 2011-06-23
> **falkTX said:**
> Nice found!
I'll update the GIT code later (just re-formatted my pc to keep supporting Lucid, Natty had too much troubles....)

I usually use 'Kompare' to make patches. It's very simple:
1 - create a copy of the old file (usually "samename.orig")
2 - modify the new file as needed
3 - run kompare, and enter the old & new filepaths
4 - hit compare, then save a patch

you can also compare entire folders too

Oh nice! A GUI for making patches...very nice. I'll use that next time. 

I appreciate everything your doing, so, since I use KXstudio tools on a regular basis (and I know some Python), I hope to help out with bug fixes and adding new stuff. Take care.

---

### Post by isaacj87 on 2011-06-24
@falkTX

One feature I've been missing (in both qjackctl & Cadence) is being notified of excessive xruns. For example, when I use Renoise, if I've got my buffer size set to 64, I'll always get crazy xruns. However, if I reconfigure JACK to 256 buffer size, I rarely get any.

I've added 2 new functions to cadence.py that will check if there are 50 or more xruns. If so, a warning dialog notify the user that there are "excessive" xruns. A warning dialog will then ask if the user would like to reconfigure JACK.

Is there any way something like this could be included in Cadence?

Here's my problems with this:

1) There needs to be a user-set option that indicates whether the user wants to be notified.
2) What I considered excessive (50 or more) may not be excessive to someone else.
3) If the user chooses "No" then the xruns will be reset. 
4) Does the user even need to be notified of "excessive" xruns?

I'm planning on trying to add something that will notify the user there has been an occurrence of xruns in the systray icon (like how qjackctl systray icon turns red when xruns happen). Maybe that's all that's needed.

Here are my changes: [http://pastebin.com/C7VHLu5s]("http://pastebin.com/C7VHLu5s")

---

### Post by Pablo_F on 2011-06-24
> One feature I've been missing (in both qjackctl & Cadence) is being notified of excessive xruns

Sorry for chiming in but I wanted to say that I like the idea a lot.

Instead of a general check box to show or not show the message, I am for a check box in the dialog window, disabled by default, reading something of the sort of "never show this message again". 

In general, the message box should be as unintrusive as possible and it should explain in few words what an xrun is and why avoid them (the how would be the icing on the cake).

Thanks for making things easier for beginners.

---

### Post by wbm on 2011-06-24
Thanks again for fixing Yoshimi :)
[I]
For anyone wondering why K9Copy crashes, you will need to instal*l *[/I]*[I]libdvdcss2 from the repositories*.



[/I]

---

### Post by falkTX on 2011-06-28
> **isaacj87 said:**
> @falkTX

One feature I've been missing (in both qjackctl & Cadence) is being notified of excessive xruns. For example, when I use Renoise, if I've got my buffer size set to 64, I'll always get crazy xruns. However, if I reconfigure JACK to 256 buffer size, I rarely get any.

I've added 2 new functions to cadence.py that will check if there are 50 or more xruns. If so, a warning dialog notify the user that there are "excessive" xruns. A warning dialog will then ask if the user would like to reconfigure JACK.

Is there any way something like this could be included in Cadence?

Here's my problems with this:

1) There needs to be a user-set option that indicates whether the user wants to be notified.
2) What I considered excessive (50 or more) may not be excessive to someone else.
3) If the user chooses "No" then the xruns will be reset. 
4) Does the user even need to be notified of "excessive" xruns?

I'm planning on trying to add something that will notify the user there has been an occurrence of xruns in the systray icon (like how qjackctl systray icon turns red when xruns happen). Maybe that's all that's needed.

Here are my changes: [http://pastebin.com/C7VHLu5s]("http://pastebin.com/C7VHLu5s")

Well, I like your enthusiasm, but if you're not going to develop something deep enough, just let me know of the main idea and I'll add it to the TODO.
My main focus right now is 'Carla', which will be partially complete soon (project save & load!)

I'll look into this at some later time.

---

### Post by isaacj87 on 2011-06-28
> **falkTX said:**
> Well, I like your enthusiasm, but if you're not going to develop something deep enough, just let me know of the main idea and I'll add it to the TODO.
My main focus right now is 'Carla', which will be partially complete soon (project save & load!)

I'll look into this at some later time.

If I find time, I want to fully finish it. I'm still learning Python, but eventually, I hope to make significant contributions. :)

The main idea would be to notify the user of xruns and, if they should arise, runaway xruns. Right now, the only way to know there's been an occurrence is to bring up the main window. Qjackctl's system tray icon will turn red when an xrun occurs, something similar in Cadence would be helpful.

---

### Post by falkTX on 2011-07-01
> **isaacj87 said:**
> If I find time, I want to fully finish it. I'm still learning Python, but eventually, I hope to make significant contributions. :)
Cool! I'll be waiting!

> **isaacj87 said:**
> Qjackctl's system tray icon will turn red when an xrun occurs, something similar in Cadence would be helpful.

Note that Cadence doesn't have a single icon yet (the current ones are copied from 'klaudia').
If you used Unity, you would note the xrun count ;)

---

### Post by wbm on 2011-07-11
KXStudio updates question:

KDE 4.6.x is pushing out all these updates, now at 4.6.5 as of today, with 4.7 coming sometime soon.
On KXStudio, I am still at 4.6.2

Do you keep it on purpose at 4.6.2 for KXStudio? Is there a reason that the updates aren't coming (yet).
I would imagine that this might be on purpose for stability reasons, but I I thought I'd ask.
Thanks

---

### Post by falkTX on 2011-07-11
> **wbm said:**
> KXStudio updates question:

KDE 4.6.x is pushing out all these updates, now at 4.6.5 as of today, with 4.7 coming sometime soon.
On KXStudio, I am still at 4.6.2

Do you keep it on purpose at 4.6.2 for KXStudio? Is there a reason that the updates aren't coming (yet).
I would imagine that this might be on purpose for stability reasons, but I I thought I'd ask.
Thanks

Well, default Lucid has 4.5.x, so 4.6.2 is an update already.
Messing with these packages could easily break the system, and I currently don't have the time and resources to do that.
I'm just finishing the last touches for Lucid, but don't expect too much updates for it now.

I prefer to give bigger attention to 11.10 now rather than keep supporting old versions.
With a 2.6.39+ kernel, realtime becomes deprecated, so I think users should consider an upgrade (once 11.10 is released).

Natty has some serious issues, so Lucid is still the best choice right now.
Things will change with 11.10 though.

---

### Post by wbm on 2011-07-11
> **falkTX said:**
> Well, default Lucid has 4.5.x, so 4.6.2 is an update already.
Messing with these packages could easily break the system, and I currently don't have the time and resources to do that.
I'm just finishing the last touches for Lucid, but don't expect too much updates for it now.

I prefer to give bigger attention to 11.10 now rather than keep supporting old versions.
With a 2.6.39+ kernel, realtime becomes deprecated, so I think users should consider an upgrade (once 11.10 is released).

Natty has some serious issues, so Lucid is still the best choice right now.
Things will change with 11.10 though.

Thanks for the reply. Btw, the low latency kernel seems to work just fine. So far I had no need to even bother with the RT kernel.

---

### Post by Thad E Ginathom on 2011-09-14
Not so much a question as...

I was looking for somewhere to say *Thank You!*

KXStudio has probably saved my Audiofire2 firewire interface from the flooded,  next-door plot. 

I just posted a recommendation in another thread [here]("http://ubuntuforums.org/showpost.php?p=11251771&postcount=26"), and if you ever want to spend a half hour laughing at one man's blundering adventure in the world of Ubuntu, Firewire and Music, I recorded it on [this thread]("http://www.hifivision.com/home-theater-pc-htpc-media-pc/19934-ubuntu-firewire-music.html") on the Indian HiFiVision site. It would, of course, be a waste of your valuable, and valued development time.

Cadence is just superb. Thank you for making Jack and Linux Firewire Audio as close to *it-just-works* as it will probably ever get.

---

### Post by falkTX on 2011-09-14
> **Thad E Ginathom said:**
> Not so much a question as...

I was looking for somewhere to say *Thank You!*

KXStudio has probably saved my Audiofire2 firewire interface from the flooded,  next-door plot. 

I just posted a recommendation in another thread [here]("http://ubuntuforums.org/showpost.php?p=11251771&postcount=26"), and if you ever want to spend a half hour laughing at one man's blundering adventure in the world of Ubuntu, Firewire and Music, I recorded it on [this thread]("http://www.hifivision.com/home-theater-pc-htpc-media-pc/19934-ubuntu-firewire-music.html") on the Indian HiFiVision site. It would, of course, be a waste of your valuable, and valued development time.

Cadence is just superb. Thank you for making Jack and Linux Firewire Audio as close to *it-just-works* as it will probably ever get.

Thanks for your nice words!

But, seriously, Cadence is not even half finished.
I've been working on some other projects lately and left Cadence a bit behind, but I'll do some work on it soon.

I'm in no hurry though, one step at a time, fixing up things here and there, and we'll move along nicely.
Sadly the new Desktop Environments are not helping the Linux Audio world at all... but I will have a solution for that too... ;)

---

### Post by Thad E Ginathom on 2011-09-14
Thanks for your quick thanks! 

If there is *yet more to come* in Cadence, then that is very exciting.

I am very happy with the Ubuntu 10.04 interface (including Compiz), and I, for one,  do not intend to upgrade or change to anything that does not allow me to keep it. I don't know how it affects developers, but *Unity* is definitely not for me.

I confess... that I didn't keep the KXS themes, but restored my desktop from my UbuntuTweak backup....

---

### Post by falkTX on 2011-09-14
> **Thad E Ginathom said:**
> Thanks for your quick thanks! 

If there is *yet more to come* in Cadence, then that is very exciting.

I am very happy with the Ubuntu 10.04 interface (including Compiz), and I, for one,  do not intend to upgrade or change to anything that does not allow me to keep it. I don't know how it affects developers, but *Unity* is definitely not for me.

I confess... that I didn't keep the KXS themes, but restored my desktop from my UbuntuTweak backup....

I like the idea behind Unity, but I don't like what's becoming now... :(

Maybe I shouldn't be showing this so soon, but anyway... take a look:
[http://kxstudio.sourceforge.net/tmp/scr026.png](http://kxstudio.sourceforge.net/tmp/scr026.png)
^ This is a mockup!

Take whatever conclusions you want, there's nothing done yet ;)

---

### Post by Thad E Ginathom on 2011-09-14
I can see some interesting things there, but you'll have to forgive me --- I'm stuck with a look that people could be forgiven for mistaking for W2K (Big blush!) although the windowing look and feel is refined  a bit with compiz/emerald. My two panels, top and bottom, work well for information, monitors, etc, a few icons on the desktop, but the seven or eight most used are on the bottom panel ...with the main menu (Oh! Can I ever give up that simple menu idea!) is at bottom left. I love the compiz cube for showing off, but frankly, seldom use it for anything else and it's probably better to switch off compiz when recording.

Freedom should be the name of the game. Let those who want their docks, or their Unity (I call it Fisher-Price design. They make stuff for tiny kids, with big, big knobs and buttons, in case they don't exist in your country), have it, and let those of us who want the basic Menu/Window/Desktop idea stick with it. I guess that it (leaving out certain currently well-known names) dates back to those Xerox Parc guys who made *the* big breakthrough in human interaction with computers

But that is not what this thread is about... Sorry!

I'll be back, on topic, with ... KXStudio - questions / answers :)

---

### Post by Thad E Ginathom on 2011-09-23
(on-topic... a real question :))

Problem with update (System Update) and upgrade (Synaptic) of **wineasio**, occurring on 10.04 and 11.04 installations. 

Details from 10.04 Synaptic:

Installed Version: 0.9.0+git20110613-0ubuntu1~lucid2

Latest Available Version: 0.9.0+git20110613-1kxstudio1

Error:

> W: Failed to fetch [http://kxstudio.sourceforge.net/repo/pool/free/wineasio_0.9.0+git20110613-1kxstudio1_i386.deb](http://kxstudio.sourceforge.net/repo/pool/free/wineasio_0.9.0+git20110613-1kxstudio1_i386.deb)
  Undetermined Error


No problem with other updates.

---

### Post by falkTX on 2011-09-23
> **Thad E Ginathom said:**
> (on-topic... a real question :))

Problem with update (System Update) and upgrade (Synaptic) of **wineasio**, occurring on 10.04 and 11.04 installations. 

Details from 10.04 Synaptic:

Installed Version: 0.9.0+git20110613-0ubuntu1~lucid2

Latest Available Version: 0.9.0+git20110613-1kxstudio1

Error:



No problem with other updates.


Noted. please try again now.

---

### Post by Thad E Ginathom on 2011-09-23
You are *unbelievably fast  *:)

Works fine now in 10.04. 

Heading over to 11.04 now. No further message means it was ok there too

Thanks.

---

### Post by falkTX on 2011-09-23
> **Thad E Ginathom said:**
> You are *unbelievably fast  *:)

Works fine now in 10.04. 

Heading over to 11.04 now. No further message means it was ok there too

Thanks.

I had a similar report on IRC, but I wasn't sure if it wasn't just one man's case.

let me know of any other issues! ;)

---

### Post by Thad E Ginathom on 2011-09-23
*Two* mens' case! 

I just got back from fighting with the Realtek NIC driver problem and compiz 3d with ATI fglrx graphics over on 11.04. I *think* I've won the battles, and it was nice to see not a single Xrun from Jack (even though I wasn't listening to anything) even through all that messing with graphics/drivers I guess I'll be moving from the 10.04 realtime to the 11.04 low-latency soonish.

And the update was fine on 11.04 too.

---

### Post by stanlea on 2011-09-23
Wolpertinger : same problem with 11.04 "cannot fetch...."

---

### Post by stanlea on 2011-09-24
> **stanlea said:**
> Wolpertinger : same problem with 11.04 "cannot fetch...."

Problem solved during the night... and a Klaudia update. Thanks, man.

---

### Post by Thad E Ginathom on 2011-09-26
A wish-list item.

When cadence is started and then "closed" (X) it still runs, but goes to the notification area on the panel.

I want to add it to the start-up programs, so that it runs on login, but it would be nice to have a "start minimised" option so that it *starts* as a panel option.

---

### Post by falkTX on 2011-09-26
> **Thad E Ginathom said:**
> A wish-list item.

When cadence is started and then "closed" (X) it still runs, but goes to the notification area on the panel.

I want to add it to the start-up programs, so that it runs on login, but it would be nice to have a "start minimised" option so that it *starts* as a panel option.

The option is already there, just not documented.

use:
```
cadence --minimized

```

;)

---

### Post by Thad E Ginathom on 2011-09-27
I had a feeling you might say something like that!

Cheers :)

---

### Post by sgx on 2011-09-27
> **falkTX said:**
> The option is already there, just not documented.

use:
```
cadence --minimized

```

;)
Has your distrho project been announced in forums?
That is quite a fine effort to remain under the radar.

[http://sourceforge.net/projects/distrho/](http://sourceforge.net/projects/distrho/)

The TAL collection are great software instruments/fx

Cheers

---

### Post by falkTX on 2011-09-27
> **sgx said:**
> Has your distrho project been announced in forums?
That is quite a fine effort to remain under the radar.

[http://sourceforge.net/projects/distrho/](http://sourceforge.net/projects/distrho/)

The TAL collection are great software instruments/fx

Cheers

Not sure if forums are the best place for it.
I already "advertised" it in the proper places:

[http://kxstudio.sourceforge.net/News](http://kxstudio.sourceforge.net/News)
[http://planet.linuxaudio.org/](http://planet.linuxaudio.org/)
[http://planet.linuxmusicians.com/](http://planet.linuxmusicians.com/)

[http://kunz.corrupt.ch/](http://kunz.corrupt.ch/)
[http://arcticanaudio.webs.com/](http://arcticanaudio.webs.com/)

and others have picked it up:
[http://www.hitsquad.com/Distrho-Linux-Updates-TAL-Arctican/](http://www.hitsquad.com/Distrho-Linux-Updates-TAL-Arctican/)

---

### Post by dontunderstand on 2011-10-04
Hi!

Problem: would like to send flash audio to jack (usb-soundcard).

How do i understand, whats wrong with my adobeflash audio?
(running Maverick + some kx repos, and other ppa-s for newer kernels, firefox and Flash) 

Pulse-jack is working, vlc shows in pulseaudio and sound comes from my usb soundcard.
Youtube audio comes to motherboard audio, and vlc is still only application that pulseaudio sound preferences window shows.


Can i fix it by installing some package from kxstudio repos or conf something?



(Oh, and will we get to try the Linux 3 rt version sometime soon?)

---

### Post by falkTX on 2011-10-04
> **dontunderstand said:**
> Hi!

Problem: would like to send flash audio to jack (usb-soundcard).

How do i understand, whats wrong with my adobeflash audio?
(running Maverick + some kx repos, and other ppa-s for newer kernels, firefox and Flash) 

Pulse-jack is working, vlc shows in pulseaudio and sound comes from my usb soundcard.
Youtube audio comes to motherboard audio, and vlc is still only application that pulseaudio sound preferences window shows.


Can i fix it by installing some package from kxstudio repos or conf something?

Flash does not use pulseaudio, it uses ALSA, so you need to tell ALSA to connect to JACK.

Just create the file '~/.asoundrc' and copy-paste this:
```
pcm.!default {
    type plug
    slave { pcm "jack" }
}

pcm.jack {
    type jack
    playback_ports {
        0 system:playback_1
        1 system:playback_2
    }
    capture_ports {
        0 system:capture_1
        1 system:capture_2
    }
}

ctl.mixer0 {
    type hw
    card 0
}
```

Restart your browser and you should have sound (output to JACK)


> **dontunderstand said:**
> (Oh, and will we get to try the Linux 3 rt version sometime soon?)
No. The current kernels were made by Abogani, I just modified them a bit, and backported the 2.6.38-lowlatency.

3.0+rt is a bit unstable (so I was told), so I don't see the reason why doing it.
I do use 3.0.1+bfs in Arch though, a nice kernel... :)

---

### Post by dontunderstand on 2011-10-04
Flashaudio works now, many thanks!

About rt unstability, i dont know until i try it, i guess.
Would something like on [that](https://aur.archlinux.org/packages.php?ID=51360&detail=1&comments=all) page, be easily converted to ubuntu package?
Testing or broken repo maybe?

---

### Post by falkTX on 2011-10-04
> **dontunderstand said:**
> About rt unstability, i dont know until i try it, i guess.
Would something like on [that](https://aur.archlinux.org/packages.php?ID=51360&detail=1&comments=all) page, be easily converted to ubuntu package?
Testing or broken repo maybe?

You're free to make a debian package for it.

I simply don't have the time for this right now (this is a seriously time-expensive task, plus maintaining...)

---

### Post by stanlea on 2011-10-13
Is it time to move to oneiric ? Unity seems to be a quite heavy desktop, the generic kernel is 3.0, ... shouldn't wait for upgrade ?

---

### Post by falkTX on 2011-10-13
> **stanlea said:**
> Is it time to move to oneiric ? Unity seems to be a quite heavy desktop, the generic kernel is 3.0, ... shouldn't wait for upgrade ?

Only if you want to.
The KXStudio-Team repos had support for Oneiric since Beta-1, so if this was holding you back, it's time to update.

Me, I'm going to Arch now, but still keeping a chroot for Ubuntu stuff.
bye bye Ubuntu, hello Arch!

---

### Post by stanlea on 2011-10-14
> **falkTX said:**
> 

Me, I'm going to Arch now, but still keeping a chroot for Ubuntu stuff.
bye bye Ubuntu, hello Arch!

What are the benefits of using Arch ?

---

### Post by sgx on 2011-10-14
If you own stock in pharmaceutical companies producing headache medicines, pray for Arch to become king of operating systems  :guitar:

In their own words

[https://wiki.archlinux.org/index.php/The_Arch_Way](https://wiki.archlinux.org/index.php/The_Arch_Way)

or the highway, known as rtfm. Buy expensive whiskey for a local power user, and it will be smooth sailing. :P

The userbase has some famous linux users and developers,
so they must be doing something right! :)

---

### Post by Thad E Ginathom on 2011-10-17
Well, virtual machine, here I come --- when I've downloaded an Arch image.

From what I hear, the advantage of Arch is that you can do anything. The disadvantage is that you* have to* do everything.  I wonder if I could ever, ever, achieve my carefully tweaked Gnome-2 desktop, and doubt that I have that much technical competence. But then, in a few releases' time, a carefully-tweaked Gnome-2 desktop may be frustratingly useless in Ubuntu.

---

### Post by Thad E Ginathom on 2011-11-10
Upgrades today!

But, with cadence, what happened to --minimized? ... because it isn't --minimized-ing

is this output, when starting from a terminal, of any use on this?
> 
$  cadence --minimized
/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
QSocketNotifier: Can only be used with threads started with QThread
QSocketNotifier: Can only be used with threads started with QThread
$
 $  uname -a
Linux <machine name> 2.6.38-8-lowlatency #42+all1~natty1-Ubuntu SMP PREEMPT Fri Apr 29 02:26:44 UTC 2011 i686 athlon i386 GNU/Linux
$
About Gnome: Version: 2.32.1
About Cadence: 0.0.12

---

### Post by falkTX on 2011-11-10
> **Thad E Ginathom said:**
> Upgrades today!

But, with cadence, what happened to --minimized? ... because it isn't --minimized-ing

is this output, when starting from a terminal, of any use on this?
About Gnome: Version: 2.32.1
About Cadence: 0.0.12

I did a major rework of the internals and systray is not yet complete, so it can't be "minimized" to tray for now.
A future update will fix this.

---

### Post by Thad E Ginathom on 2011-11-10
In that case, let me just remind you what a popular and useful feature it is.

(with me, at least ;) )

Cheers...

---

### Post by stanlea on 2011-11-11
Hi

Just installed the "latest" updates. Inside Claudia, the shift+F2 command to add apps doesnt work more, so I think the link with the hard coded database is broken. Carla still doesn't work.

I know it's a work in progress, so I'll see later. I can dig with Klaudia.

Thank you for the hard work.

---

### Post by falkTX on 2011-11-11
> **stanlea said:**
> Hi

Just installed the "latest" updates. Inside Claudia, the shift+F2 command to add apps doesnt work more, so I think the link with the hard coded database is broken. Carla still doesn't work.

I know it's a work in progress, so I'll see later. I can dig with Klaudia.

Thank you for the hard work.

Please run those in a terminal, and paste here any error output (preferably the whole dump, after you started the app)

As you said, this is a work in progress (glad you understand!)

---

### Post by Thad E Ginathom on 2011-11-11
Any chance of a few notes as to what has been changed/improved/upgraded?

Whilst a changelog would be nice(hey, so would a manual, but yes, I do understand that, at this time, you are prioritising development over documentation, and that's ok), it doesn't have to be formal in any way.

---

### Post by falkTX on 2011-11-11
> **Thad E Ginathom said:**
> Any chance of a few notes as to what has been changed/improved/upgraded?

Whilst a changelog would be nice(hey, so would a manual, but yes, I do understand that, at this time, you are prioritising development over documentation, and that's ok), it doesn't have to be formal in any way.

Everything on the Cadence code happens here:
[http://repo.or.cz/w/cadence.git/shortlog/refs/heads/master](http://repo.or.cz/w/cadence.git/shortlog/refs/heads/master)

The current PPA version is at 'Forgot to re-add file', so anything up from that is what's coming next, and all below is like a changelog.

---

### Post by stanlea on 2011-11-11
Here we are :

```
claudia
/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
QSocketNotifier: Can only be used with threads started with QThread
QSocketNotifier: Can only be used with threads started with QThread
Unsupported database
```

the command carla produces a segmentation fault (Ubuntu 10.04 64 bits)

---

### Post by Thad E Ginathom on 2011-11-11
> Everything on the Cadence code happens here...

Thanks!

---

### Post by falkTX on 2011-11-11
> **stanlea said:**
> Here we are :

```
claudia
/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
QSocketNotifier: Can only be used with threads started with QThread
QSocketNotifier: Can only be used with threads started with QThread
Unsupported database
```

the command carla produces a segmentation fault (Ubuntu 10.04 64 bits)

Looks like an old database file is messing everything up.

Please delete the Cadence config files:
```
rm ~/.config/Cadence/*
```

And everything should work fine again

---

### Post by stanlea on 2011-11-11
Thanks but how to rebuild the database ? I reinstalled cadence, claudia etc. and now the item "add new" is greyed.

edit : oops, sorry, I dit it changing the settings in Claudia. Works fine now.

---

### Post by falkTX on 2011-11-11
@Thad E Ginathom:

systray (and --minimized) is back.
I couldn't try it on Unity (any gtk3 app is causing 100% cpu on my system), so as usual, report back any issues.

---

### Post by stanlea on 2011-11-12
More on the Carla error (log from Cadence)

 ```
Sat Nov 12 11:29:36 2011: New client 'Carla' with PID 4137
 Sat Nov 12 11:29:36 2011: ERROR: JackEngine::XRun: client = Carla was not run: state = 2
 Sat Nov 12 11:29:36 2011: ERROR: JackEngine::XRun: client = Carla was not run: state = 1
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: Cannot read socket fd = 25 err = Connection reset by peer
 Sat Nov 12 11:29:36 2011: ERROR: NotifyClient fails name = Carla event = 2 val1 = 0 val2 = 0
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 24 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Could not read result
 Sat Nov 12 11:29:36 2011: ERROR: NotifyClient fails name = Carla event = 18 val1 = 0 val2 = 0
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot read socket fd = -1 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: NotifyClient fails name = Carla event = 18 val1 = 1 val2 = 0
 Sat Nov 12 11:29:36 2011: Client 'Carla' with PID 4137 is out

```

---

### Post by Thad E Ginathom on 2011-11-12
> systray (and --minimized) is back.
I couldn't try it on Unity (any gtk3 app is causing 100% cpu on my system), so as usual, report back any issues.That's great: thanks :) Nice to see the new cadence icon up there.

Suggestion: clicking [X] (Close window) should minimise to system tray, not quit the program. No idea if there are "rules" about this. Probably that means coding to take account of those who want to minimise and those that don't. I guess I have to live with it!*

Can't comment on Unity: I'm sticking with Gnome-2. I like my menus and panels!

The *System Update *complained that only a partial update could be done. Checking this out in Synaptic, it looks as if that might be because the update to Carla wants to remove carla-wine. For now, I didn't let it do that. For me, it probably wouldn't matter, and carla is only something I play with, rather than need, but I'm cautious about Ubuntu upgrades that want to remove stuff if they are not upgrading it.



*Or get the habit of clicking mimimise on the tray icon, rather than using the standard window controls. Just realised that.

---

### Post by falkTX on 2011-11-12
> **Thad E Ginathom said:**
> That's great: thanks :) Nice to see the new cadence icon up there.

Suggestion: clicking [X] (Close window) should minimise to system tray, not quit the program. No idea if there are "rules" about this. Probably that means coding to take account of those who want to minimise and those that don't. I guess I have to live with it!*

Can't comment on Unity: I'm sticking with Gnome-2. I like my menus and panels!

The *System Update *complained that only a partial update could be done. Checking this out in Synaptic, it looks as if that might be because the update to Carla wants to remove carla-wine. For now, I didn't let it do that. For me, it probably wouldn't matter, and carla is only something I play with, rather than need, but I'm cautious about Ubuntu upgrades that want to remove stuff if they are not upgrading it.



*Or get the habit of clicking mimimise on the tray icon, rather than using the standard window controls. Just realised that.

Cadence should always minimize to systray on close. Claudia is configurable.
But this may be something with my Gnome2 code (my systray class handles KDE, app-indicator and old X-Embed trays).
Maybe I can just force old behaviour on Gnome2... please post here the output of 'env', ran in a terminal. I'll disable app-indicators for Gnome2 and this should work fine again.

I'm yet to see if carla-wine can work or not, so I've removed the package for now. But I'll do more testing soon.

---

### Post by falkTX on 2011-11-12
> **stanlea said:**
> More on the Carla error (log from Cadence)

 ```
Sat Nov 12 11:29:36 2011: New client 'Carla' with PID 4137
 Sat Nov 12 11:29:36 2011: ERROR: JackEngine::XRun: client = Carla was not run: state = 2
 Sat Nov 12 11:29:36 2011: ERROR: JackEngine::XRun: client = Carla was not run: state = 1
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: JackAudioDriver::ProcessGraphAsync: Process error
 Sat Nov 12 11:29:36 2011: ERROR: Cannot read socket fd = 25 err = Connection reset by peer
 Sat Nov 12 11:29:36 2011: ERROR: NotifyClient fails name = Carla event = 2 val1 = 0 val2 = 0
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 24 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 25 err = Broken pipe
 Sat Nov 12 11:29:36 2011: ERROR: Could not read result
 Sat Nov 12 11:29:36 2011: ERROR: NotifyClient fails name = Carla event = 18 val1 = 0 val2 = 0
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot write socket fd = 4294967295 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: Cannot read socket fd = -1 err = Bad file descriptor
 Sat Nov 12 11:29:36 2011: ERROR: NotifyClient fails name = Carla event = 18 val1 = 1 val2 = 0
 Sat Nov 12 11:29:36 2011: Client 'Carla' with PID 4137 is out

```

This seems to be more of a JACK error rather then Carla, unless you have a *very low* buffer size and Carla can't keep up with it.
Try using a higher JACK buffer size and start Carla again.

---

### Post by Thad E Ginathom on 2011-11-12
> **falkTX said:**
> Cadence should always minimize to systray on close. Claudia is configurable.
But this may be something with my Gnome2 code (my systray class handles KDE, app-indicator and old X-Embed trays).
Maybe I can just force old behaviour on Gnome2... please post here the output of 'env', ran in a terminal. I'll disable app-indicators for Gnome2 and this should work fine again.

I'm yet to see if carla-wine can work or not, so I've removed the package for now. But I'll do more testing soon.
```
$  env
ORBIT_SOCKETDIR=/tmp/orbit-nick
SSH_AGENT_PID=2558
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=9bc8dcf24ed09fda699a883d00000003-1321107387.778402-328311910
WINDOWID=79691807
GNOME_KEYRING_CONTROL=/tmp/keyring-oz90gz
GTK_MODULES=canberra-gtk-module
USER=nick
LS_COLORS=no=00;38;5;244:rs=0:di=00;38;5;33:ln=01;38;5;33:pi=48;5;230;38;5;136;01:so=48;5;230;38;5;136;01:do=48;5;230;38;5;136;01:bd=48;5;230;38;5;244;01:cd=48;5;230;38;5;244;01:or=48;5;235;38;5;160:su=48;5;160;38;5;230:sg=48;5;136;38;5;230:ca=30;41:tw=48;5;64;38;5;230:ow=48;5;235;38;5;33:st=48;5;33;38;5;230:ex=01;38;5;64:*.tar=00;38;5;61:*.tgz=01;38;5;61:*.arj=01;38;5;61:*.taz=01;38;5;61:*.lzh=01;38;5;61:*.lzma=01;38;5;61:*.tlz=01;38;5;61:*.txz=01;38;5;61:*.zip=01;38;5;61:*.z=01;38;5;61:*.Z=01;38;5;61:*.dz=01;38;5;61:*.gz=01;38;5;61:*.lz=01;38;5;61:*.xz=01;38;5;61:*.bz2=01;38;5;61:*.bz=01;38;5;61:*.tbz=01;38;5;61:*.tbz2=01;38;5;61:*.tz=01;38;5;61:*.deb=01;38;5;61:*.rpm=01;38;5;61:*.jar=01;38;5;61:*.rar=01;38;5;61:*.ace=01;38;5;61:*.zoo=01;38;5;61:*.cpio=01;38;5;61:*.7z=01;38;5;61:*.rz=01;38;5;61:*.apk=01;38;5;61:*.jpg=00;38;5;136:*.JPG=00;38;5;136:*.jpeg=00;38;5;136:*.gif=00;38;5;136:*.bmp=00;38;5;136:*.pbm=00;38;5;136:*.pgm=00;38;5;136:*.ppm=00;38;5;136:*.tga=00;38;5;136:*.xbm=00;38;5;136:*.xpm=00;38;5;136:*.tif=00;38;5;136:*.tiff=00;38;5;136:*.png=00;38;5;136:*.svg=00;38;5;136:*.svgz=00;38;5;136:*.mng=00;38;5;136:*.pcx=00;38;5;136:*.dl=00;38;5;136:*.xcf=00;38;5;136:*.xwd=00;38;5;136:*.yuv=00;38;5;136:*.cgm=00;38;5;136:*.emf=00;38;5;136:*.eps=00;38;5;136:*.pdf=01;38;5;245:*.tex=01;38;5;245:*.rdf=01;38;5;245:*.owl=01;38;5;245:*.n3=01;38;5;245:*.tt=01;38;5;245:*.nt=01;38;5;245:*.log=00;38;5;240:*.bak=00;38;5;240:*.aux=00;38;5;240:*.bbl=00;38;5;240:*.blg=00;38;5;240:*.aac=00;38;5;166:*.au=00;38;5;166:*.flac=00;38;5;166:*.mid=00;38;5;166:*.midi=00;38;5;166:*.mka=00;38;5;166:*.mp3=00;38;5;166:*.mpc=00;38;5;166:*.ogg=00;38;5;166:*.ra=00;38;5;166:*.wav=00;38;5;166:*.axa=00;38;5;166:*.oga=00;38;5;166:*.spx=00;38;5;166:*.xspf=00;38;5;166:*.mov=01;38;5;166:*.mpg=01;38;5;166:*.mpeg=01;38;5;166:*.m2v=01;38;5;166:*.mkv=01;38;5;166:*.ogm=01;38;5;166:*.mp4=01;38;5;166:*.m4v=01;38;5;166:*.mp4v=01;38;5;166:*.vob=01;38;5;166:*.qt=01;38;5;166:*.nuv=01;38;5;166:*.wmv=01;38;5;166:*.asf=01;38;5;166:*.rm=01;38;5;166:*.rmvb=01;38;5;166:*.flc=01;38;5;166:*.avi=01;38;5;166:*.fli=01;38;5;166:*.flv=01;38;5;166:*.gl=01;38;5;166:*.axv=01;38;5;166:*.anx=01;38;5;166:*.ogv=01;38;5;166:*.ogx=01;38;5;166:
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
SSH_AUTH_SOCK=/tmp/keyring-oz90gz/ssh
SESSION_MANAGER=local/Peafowl:@/tmp/.ICE-unix/2473,unix/Peafowl:/tmp/.ICE-unix/2473
USERNAME=nick
DEFAULTS_PATH=/usr/share/gconf/gnome-classic.default.path
DSSI_PATH=/usr/lib/dssi:/usr/local/lib/dssi:/usr/lib32/dssi:/home/nick/.dssi
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome-classic:/usr/share/kxstudio/menu/:/etc/xdg/
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/nick/scripts:/home/nick/bin
DESKTOP_SESSION=gnome-classic
LC_MESSAGES=en_IN.UTF-8
PWD=/home/nick
GDM_KEYBOARD_LAYOUT=gb
LANG=en_IN
GDM_LANG=en_IN
MANDATORY_PATH=/usr/share/gconf/gnome-classic.mandatory.path
LV2_PATH=/usr/lib/lv2:/usr/local/lib/lv2:/home/nick/.lv2
GDMSESSION=gnome-classic
SHLVL=1
HOME=/home/nick
LANGUAGE=en_IN:en
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=nick
XDG_DATA_DIRS=/usr/share/gnome-classic:/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-9nigfrGPY8,guid=29a6517e5dcc26093826da680000002e
LESSOPEN=| /usr/bin/lesspipe %s
VST_PATH=/usr/lib/vst:/usr/local/lib/vst:/usr/lib32/vst:/home/nick/.vst
WINDOWPATH=7
DISPLAY=:0.0
LADSPA_PATH=/usr/lib/ladspa:/usr/local/lib/ladspa:/usr/lib32/ladspa:/home/nick/.ladspa
LESSCLOSE=/usr/bin/lesspipe %s %s
HISTTIMEFORMAT=%d/%m/%y %T 
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-nick-xUqIHR/database
_=/usr/bin/env

```Goodness, back in my Unix days, it used to have just a hand ful of lines --- but that was dumb-termnal unix.

I'm really not sure ... but didn't the previous version minimise on [X]? 

**carla...**
(I guess this is a me-too) [COLOR=Blue]
[/COLOR] 
I was doing some elementary playing with this a couple of days back. Now nothing happens when I click carla in cadence/tools. Log output:

 ```
  Sun Nov 13 02:24:13 2011: New client 'Carla' with PID 12989
 Sun Nov 13 02:24:14 2011: ERROR: JackEngine::XRun: client = Carla was not run: state = 2
 Sun Nov 13 02:24:14 2011: ERROR: JackEngine::XRun: client = Carla was not run: state = 1
 Sun Nov 13 02:24:14 2011: ERROR: JackEngine::XRun: client = Carla was not run: state = 1
 Sun Nov 13 02:24:14 2011: ERROR: Cannot read socket fd = 51 err = Connection reset by peer
 Sun Nov 13 02:24:14 2011: ERROR: NotifyClient fails name = Carla event = 2 val1 = 0 val2 = 0
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 50 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 51 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 51 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 51 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 51 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 51 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 51 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = 51 err = Broken pipe
 Sun Nov 13 02:24:14 2011: ERROR: Could not read result
 Sun Nov 13 02:24:14 2011: ERROR: NotifyClient fails name = Carla event = 18 val1 = 0 val2 = 0
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: Cannot write socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: Cannot read socket fd = -1 err = Bad file descriptor
 Sun Nov 13 02:24:14 2011: ERROR: NotifyClient fails name = Carla event = 18 val1 = 1 val2 = 0
 Sun Nov 13 02:24:14 2011: Client 'Carla' with PID 12989 is out
```Terminal, short and sweet...
 ```
$  carla
Segmentation fault

```This is what I was previously doing with jack```

 p, li { white-space: pre-wrap; }  Sat Nov 12 19:46:33 2011: ------------------
 Sat Nov 12 19:46:33 2011: Controller activated. Version 1.9.7 (4236) built on Thu Oct 13 04:12:50 2011
 Sat Nov 12 19:46:34 2011: Loading settings from "/home/nick/.config/jack/conf.xml" using expat_2.0.1 ...
 Sat Nov 12 19:46:34 2011: setting engine option "driver" to value "firewire"
 Sat Nov 12 19:46:34 2011: driver "firewire" selected
 Sat Nov 12 19:46:34 2011: setting engine option "realtime" to value "true"
 Sat Nov 12 19:46:34 2011: setting for driver "firewire" found
 Sat Nov 12 19:46:34 2011: setting driver option "rate" to value "96000"
 Sat Nov 12 19:46:34 2011: setting for driver "net" found
 Sat Nov 12 19:46:34 2011: setting for driver "netone" found
 Sat Nov 12 19:46:34 2011: setting for driver "dummy" found
 Sat Nov 12 19:46:34 2011: setting for driver "alsa" found
 Sat Nov 12 19:46:34 2011: setting driver option "rate" to value "44100"
 Sat Nov 12 19:46:34 2011: setting driver option "nperiods" to value "2"
 Sat Nov 12 19:46:34 2011: setting for driver "loopback" found
 Sat Nov 12 19:46:34 2011: setting for internal "netadapter" found
 Sat Nov 12 19:46:34 2011: setting for internal "audioadapter" found
 Sat Nov 12 19:46:34 2011: setting for internal "netmanager" found
 Sat Nov 12 19:46:34 2011: setting for internal "profiler" found
 Sat Nov 12 19:46:34 2011: Listening for D-Bus messages
 Sat Nov 12 19:46:34 2011: Starting jack server...
 Sat Nov 12 19:46:34 2011: JACK server starting in realtime mode with priority 10
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown_in'
 Sat Nov 12 19:46:37 2011: New client 'firewire_pcm' with PID 0
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown0_in'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown1_in'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown2_in'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown3_in'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown_out'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown0_out'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown1_out'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown2_out'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown3_out'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown4_out'
 Sat Nov 12 19:46:37 2011: graph reorder: new port 'firewire_pcm:001486066bf84d1e_Unknown5_out'
 Sat Nov 12 19:46:42 2011: New client 'cadence' with PID 2682
 Sat Nov 12 21:06:22 2011: New client 'jack_P' with PID 4842
 Sat Nov 12 21:06:22 2011: Connecting 'jack_P:out_000' to 'firewire_pcm:001486066bf84d1e_Unknown_out'
 Sat Nov 12 21:06:22 2011: Connecting 'jack_P:out_001' to 'firewire_pcm:001486066bf84d1e_Unknown0_out'
 Sat Nov 12 21:06:42 2011: Disconnecting 'jack_P:out_000' from 'firewire_pcm:001486066bf84d1e_Unknown_out'
 Sat Nov 12 21:06:42 2011: Disconnecting 'jack_P:out_001' from 'firewire_pcm:001486066bf84d1e_Unknown0_out'
 Sat Nov 12 21:06:42 2011: Client 'jack_P' with PID 4842 is out
 Sun Nov 13 01:24:05 2011: New client 'aqualung' with PID 11471
 Sun Nov 13 01:24:06 2011: Connecting 'aqualung:out_L' to 'firewire_pcm:001486066bf84d1e_Unknown_out'
 Sun Nov 13 01:24:06 2011: Connecting 'aqualung:out_R' to 'firewire_pcm:001486066bf84d1e_Unknown0_out'

```Jack sample rate=9600, buffer size=1024, Periods=3 Cadence claims Latency at 10.6ms. 
I configure to 9600 for recording (digitising vinyl) but had been playing an hour of 44100/16

UPDATE: I did the upgrade. Clicked on carla and it appeared to run. Not sure from the logs that it did any more than show an interface. Then tried it from the terminal, and got the segfault again: back to square one. Bed time.

Will start again from purged logs tomorrow and post if it adds anything.

---

### Post by falkTX on 2011-11-12
@Thad E Ginathom:
Thanks, next update will fix the systray on gnome-classic. I won't hurry this though, as it doesn't seem a major thing.

I'll try to optimize Carla further, I believe the OSC part is causing this...

---

### Post by Thad E Ginathom on 2011-11-13
Ignore... didn't make sense. Posted with insufficient tea intake.

---

### Post by m.lp.ql.m on 2011-12-10
1) falkTX-- thanks so much for your work. Cadence is the only JACK GUI controller that seems to actually get JACK working on my system.

2) Small prob--I have the kxstudio PPAs installed on my Ubuntustudio 11.10 system. I seem to have gotten a recent upgrade for Cadence and Claudia on my system. With this new upgrade, the Claudia "Arrange" Ctrl-G function doesn't work, and is greyed out under the Canvas menu.

Not a big deal, but it does make setting up things easier.

---

### Post by m.lp.ql.m on 2011-12-10
3) When restarting a saved studio in Claudia, the listed apps seem to get doubled-- see pic. [IMG]http://abmtx.users.sonic.net/kxstudioAppDoubling.png[/IMG]

Trying to remove these extra inactive apps gives me a notice that it can't be done because they're not found, and I can't start them because they're already running.

---

### Post by falkTX on 2011-12-11
> **m.lp.ql.m said:**
> 1) falkTX-- thanks so much for your work. Cadence is the only JACK GUI controller that seems to actually get JACK working on my system.

2) Small prob--I have the kxstudio PPAs installed on my Ubuntustudio 11.10 system. I seem to have gotten a recent upgrade for Cadence and Claudia on my system. With this new upgrade, the Claudia "Arrange" Ctrl-G function doesn't work, and is greyed out under the Canvas menu.

Not a big deal, but it does make setting up things easier.

1) Thanks, since you're using KXStudio PPAs, it was expected that KXStudio software would work on it ;)

2) Some previous canvas changes broke it, and I disabled it for the Alpha-1 release. This will be re-introduced at a later time.
It wasn't working very well anyway...

---

### Post by falkTX on 2011-12-11
> **m.lp.ql.m said:**
> 3) When restarting a saved studio in Claudia, the listed apps seem to get doubled-- see pic. [IMG]http://abmtx.users.sonic.net/kxstudioAppDoubling.png[/IMG]

Trying to remove these extra inactive apps gives me a notice that it can't be done because they're not found, and I can't start them because they're already running.

This is a bug, I noticed it before, but it didn't always happen.
So you found out it happens when restarting a studio, thanks (I'll try to get the same behavior here consistently, should not be too hard to fix).
For now, just restart Claudia and it should work fine again.

---

### Post by m.lp.ql.m on 2011-12-17
1)Should we be letting you know of bugs we run into here, or [here]("https://bugs.launchpad.net/~kxstudio-team")? The launchpad site is empty, so I'm kinda unsure.

2)On my system (Ubuntu Studio 11.10 with the KX Studio repos), when I try to add Qtractor via Shift-F2, Qtractor just hangs, the mouse cursor stays busy. When adding via F2, it loads just fine.

3)I want to say I saw this answered elsewhere on the net, but I can't find in right now, so forgive me if I'm being redundant. When I try to install the kxstudio-meta-restricted-extras package, it wants to uninstall seemingly everything else kxstudio related-- many, many music apps from a2jmidid to zynjacku. I don't really *need* this package, I think, but I do like to experiment with different things to be creative, and I wonder what I'm missing. I was able to pick and choose several things from the "recommended" installations OK.

Obrigado!

---

### Post by falkTX on 2011-12-18
> **m.lp.ql.m said:**
> 1)Should we be letting you know of bugs we run into here, or [here]("https://bugs.launchpad.net/~kxstudio-team")? The launchpad site is empty, so I'm kinda unsure.
Bugs go here:
[https://bugs.launchpad.net/kxstudio](https://bugs.launchpad.net/kxstudio)

This link can be get from the KXStudio development page - [http://kxstudio.sourceforge.net/Development](http://kxstudio.sourceforge.net/Development)


> **m.lp.ql.m said:**
> 2)On my system (Ubuntu Studio 11.10 with the KX Studio repos), when I try to add Qtractor via Shift-F2, Qtractor just hangs, the mouse cursor stays busy. When adding via F2, it loads just fine.
I assume you're talking about Claudia?


> **m.lp.ql.m said:**
> 3)I want to say I saw this answered elsewhere on the net, but I can't find in right now, so forgive me if I'm being redundant. When I try to install the kxstudio-meta-restricted-extras package, it wants to uninstall seemingly everything else kxstudio related-- many, many music apps from a2jmidid to zynjacku. I don't really *need* this package, I think, but I do like to experiment with different things to be creative, and I wonder what I'm missing. I was able to pick and choose several things from the "recommended" installations OK.
I need to clarify this. Currently all KXStudio meta-packages are the same for Lucid -> Oneiric (except desktop-unity).
At first I though this would be fine, but Ubuntu seems to change quite a lot from each version, so some metas may be broken.
It's simply impossible for me to test all Ubuntu versions and combinations (32/64bit, extra repos, Mint variation, etc etc)
For this reason I decided, in the near future, to stop supporting old versions and focus on 12.04. I'll be focus on this version for a while, and not update. This will give us a very stable system.
I've wrote it in the news some time ago, [http://kxstudio.sourceforge.net/News](http://kxstudio.sourceforge.net/News) - check the 2nd article

> **m.lp.ql.m said:**
> Obrigado!
De nada!

Sorry if I wasn't very clear on some subjects, I'm sick today... :(

---

### Post by stanlea on 2011-12-19
Suddenly I can't start any app within (or without) Cadence. Jack is started, I checked all my settings, I didn'y install any new software, nor did any update. Any idea about the problem ?

The message is still the same :

```
RemoteVSTClient: all cache files are up-to-date, not running scanner
terminate called after throwing an instance of 'RemotePluginClosedException'

```

---

### Post by falkTX on 2011-12-19
> **stanlea said:**
> Suddenly I can't start any app within (or without) Cadence. Jack is started, I checked all my settings, I didn'y install any new software, nor did any update. Any idea about the problem ?

The message is still the same :

```
RemoteVSTClient: all cache files are up-to-date, not running scanner
terminate called after throwing an instance of 'RemotePluginClosedException'

```

This is about dssi-vst, which seems broken with recent wine versions.

Please uninstall dssi-vst and try again

---

### Post by stanlea on 2011-12-19
> **falkTX said:**
> This is about dssi-vst, which seems broken with recent wine versions.

Please uninstall dssi-vst and try again

Cool ! It worked. Thanks a lot.

---

### Post by m.lp.ql.m on 2011-12-20
> **falkTX said:**
> 

[QUOTE=m.lp.ql.m;11545323]
2)On my system (Ubuntu Studio 11.10 with the KX Studio repos), when I try to add Qtractor via Shift-F2, Qtractor just hangs, the mouse cursor stays busy. When adding via F2, it loads just fine.


I assume you're talking about Claudia?
[/QUOTE]

Yes, in Claudia.

> **falkTX said:**
> 
Sorry if I wasn't very clear on some subjects, I'm sick today... :(

Saúde!

---

### Post by Grone1985 on 2011-12-20
Hey guys,
I've been having problems installing KXStudio on Xubuntu 11.10. I added the repos but it says the packages are broken and cannot be installed. If any of you can help me get this installed I would really appreciate it. Thanks in advance!

---

### Post by falkTX on 2011-12-20
> **Grone1985 said:**
> Hey guys,
I've been having problems installing KXStudio on Xubuntu 11.10. I added the repos but it says the packages are broken and cannot be installed. If any of you can help me get this installed I would really appreciate it. Thanks in advance!

please run this:

```
sudo apt-get update # Update sources
sudo apt-get dist-upgrade -d # Try to force update packages, download only

```

Please post the output of the 2nd command.

thanks

---

### Post by falkTX on 2011-12-20
> **m.lp.ql.m said:**
> Yes, in Claudia.


Just found the bug.

When no jack application with transport is running, BPM is 0.
Claudia is writing configs with BPM 0 (now defaults to 120).
Qtractor doesn't like it...

I'll push an update soon.

---

### Post by Grone1985 on 2011-12-20
> **falkTX said:**
> please run this:

```
sudo apt-get update # Update sources
sudo apt-get dist-upgrade -d # Try to force update packages, download only

```

Please post the output of the 2nd command.

thanks

Thanks for the prompt response. This is the output:

```
negro@negro-RV411:~$ sudo apt-get dist-upgrade -d
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```

It's in spanish but it basically says nothing was or will be installed

---

### Post by falkTX on 2011-12-20
> **Grone1985 said:**
> Thanks for the prompt response. This is the output:

```
negro@negro-RV411:~$ sudo apt-get dist-upgrade -d
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```

It's in spanish but it basically says nothing was or will be installed

You said "but it says the packages are broken and cannot be installed", so which packages can't be installed?

---

### Post by Grone1985 on 2011-12-20
> **falkTX said:**
> You said "but it says the packages are broken and cannot be installed", so which packages can't be installed?

kxstudio-meta-audio
kxstudio-meta-audio-plugins
kxstudio-meta-audio-plugins-dssi
kxstudio-meta-audio-plugins-ladspa
kxstudio-meta-audio-plugins-lv2
kxstudio-meta-audio-plugins-vamp

---

### Post by falkTX on 2011-12-20
> **Grone1985 said:**
> kxstudio-meta-audio
kxstudio-meta-audio-plugins
kxstudio-meta-audio-plugins-dssi
kxstudio-meta-audio-plugins-ladspa
kxstudio-meta-audio-plugins-lv2
kxstudio-meta-audio-plugins-vamp

ok, then let's try a simple one.

post the output of:
```
sudo apt-get -V install kxstudio-meta-audio-plugins-vamp
```

btw, do you have kxstudio-repos installed?

---

### Post by Grone1985 on 2011-12-20
> **falkTX said:**
> ok, then let's try a simple one.

post the output of:
```
sudo apt-get -V install kxstudio-meta-audio-plugins-vamp
```

btw, do you have kxstudio-repos installed?

yes, kxstudio-repos is installed

```
negro@negro-RV411:~$ sudo apt-get -V install kxstudio-meta-audio-plugins-vamp
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
 kxstudio-meta-audio-plugins-vamp : Depende de: match-vamp-plugin pero no es instalable
                                    Depende de: vamp-aubio-plugins pero no es instalable
                                    Depende de: vamp-libxtract-plugins pero no es instalable
                                    Depende de: vamp-onsetsds-plugin pero no es instalable
                                    Depende de: vampy pero no es instalable
E: No se han podido corregir los problemas; ha retenido paquetes rotos.

```

so it says that match-vamp-plugin, vamp-aubio-plugins, vamp-libxtract-plugins, vamp-onsetsds-plugin and vampy are needed but cannot be installed

---

### Post by falkTX on 2011-12-20
> **Grone1985 said:**
> yes, kxstudio-repos is installed

```
negro@negro-RV411:~$ sudo apt-get -V install kxstudio-meta-audio-plugins-vamp
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
 kxstudio-meta-audio-plugins-vamp : Depende de: match-vamp-plugin pero no es instalable
                                    Depende de: vamp-aubio-plugins pero no es instalable
                                    Depende de: vamp-libxtract-plugins pero no es instalable
                                    Depende de: vamp-onsetsds-plugin pero no es instalable
                                    Depende de: vampy pero no es instalable
E: No se han podido corregir los problemas; ha retenido paquetes rotos.

```

so it says that match-vamp-plugin, vamp-aubio-plugins, vamp-libxtract-plugins, vamp-onsetsds-plugin and vampy are needed but cannot be installed

I should had probably asked this before - what OS and version do you use? 32bit or 64bit?

to see what is the packages problem you need to try to install the conflicting one(s). In this last try it reports:
```
 kxstudio-meta-audio-plugins-vamp : Depende de: match-vamp-plugin pero no es instalable
(...)
```

so try:
```
sudo apt-get install match-vamp-plugin
```

---

### Post by Grone1985 on 2011-12-20
> **falkTX said:**
> I should had probably asked this before - what OS and version do you use? 32bit or 64bit?

to see what is the packages problem you need to try to install the conflicting one(s). In this last try it reports:
```
 kxstudio-meta-audio-plugins-vamp : Depende de: match-vamp-plugin pero no es instalable
(...)
```

so try:
```
sudo apt-get install match-vamp-plugin
```

I'm on xubuntu 64bit.

the output says that the package is not available because it's either missing, obsolete or it's available from another source.

---

### Post by falkTX on 2011-12-20
> **Grone1985 said:**
> I'm on xubuntu 64bit.

the output says that the package is not available because it's either missing, obsolete or it's available from another source.

That is not normal... somehow kxstudio-repos got installed but you didn't got the PPAs?

hm, in any case, these final set of commands should fix-up everything:

```
add-apt-repository -y ppa:kxstudio-team/ppa
add-apt-repository -y ppa:kxstudio-team/latest
add-apt-repository -y ppa:kxstudio-team/kxstudio
add-apt-repository -y ppa:kxstudio-team/kernel
add-apt-repository -y ppa:kxstudio-team/games
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by Grone1985 on 2011-12-21
> **falkTX said:**
> That is not normal... somehow kxstudio-repos got installed but you didn't got the PPAs?

hm, in any case, these final set of commands should fix-up everything:

```
add-apt-repository -y ppa:kxstudio-team/ppa
add-apt-repository -y ppa:kxstudio-team/latest
add-apt-repository -y ppa:kxstudio-team/kxstudio
add-apt-repository -y ppa:kxstudio-team/kernel
add-apt-repository -y ppa:kxstudio-team/games
sudo apt-get update
sudo apt-get dist-upgrade

```

Cool, the broken packages are gone. it installed the metapackages without problems.

Thanks!

---

### Post by Grone1985 on 2011-12-22
Hi again, I've installed averything without problems but now I'm having an issue with jack setup. For some reason I have 4 playback ports listed in catia, only playback 3 and 4 work but connections always default to playback 1 and 2 and then have to be manually modified. This happens with every program I've tried and also youtube videos. Is there anyway to fix this permanently? Thanks!

---

### Post by falkTX on 2011-12-22
> **Grone1985 said:**
> Hi again, I've installed averything without problems but now I'm having an issue with jack setup. For some reason I have 4 playback ports listed in catia, only playback 3 and 4 work but connections always default to playback 1 and 2 and then have to be manually modified. This happens with every program I've tried and also youtube videos. Is there anyway to fix this permanently? Thanks!

On the configure jack dialog, do you have multiple devices? If yes, try to select a specific one (like hw0:0 instead of hw0).

I know a quick & dirty way around this, but please try that one^ first.

---

### Post by Grone1985 on 2011-12-22
> **falkTX said:**
> On the configure jack dialog, do you have multiple devices? If yes, try to select a specific one (like hw0:0 instead of hw0).

I know a quick & dirty way around this, but please try that one^ first.

Ok cool, in the same dialog there is an option to set the number of output channels. It was set to default to max (4), that was the problem. All ok now. Thanks again!

---

