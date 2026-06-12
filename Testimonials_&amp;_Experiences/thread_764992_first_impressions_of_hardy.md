---
title: "first impressions of hardy"
date: 2008-04-24
forum: Testimonials &amp; Experiences
---

### Post by jasonwatkins on 2008-04-24
the main problem i'm having is that it's just weird getting used to ubuntu again after having used mint for so long :)

i can't seem to get floola working at the moment which is a pain as I swear by that for my ipod.

xmms won't install either - i know it's obsolete but i like it and don't want anything like amarok because i just want a small and simple music player.

---

### Post by jasonwatkins on 2008-04-24
oh, and some of the websites i go to don't store the cookies properly - even though i've saved the passwords, i still have to login each time - even though my cookies are set to be kept until expiry.

---

### Post by Ub1476 on 2008-04-24
You can use Audacious as an replacement for XMMS. ;)

---

### Post by Dark Aspect on 2008-04-24
> **jasonwatkins said:**
> oh, and some of the websites i go to don't store the cookies properly - even though i've saved the passwords, i still have to login each time - even though my cookies are set to be kept until expiry.

Thats probably due the fact they used a beta version of firefox with the LTS.I had nothing but problems when I installed the beta on gutsy.Once I install Ubuntu 8.04 I am going to see if there is an older firefox package in the repositories.

I think I might have tried an earlier beta though,so firefox on 8.04 might not be so bad IDK.

---

### Post by Mandor on 2008-04-24
Try mpd + sontata for a simple and functional player. Try a cli frontend for even simpler one.

---

### Post by Eisenwinter on 2008-04-24
So far, it's faster than Gutsy for me.

Installation was a breeze, took less than 15 minutes from the time I entered the CD into the tray after burning it in Gutsy, and the time I rebooted after Hardy was fully installed.

---

### Post by jasonwatkins on 2008-04-24
i'm actually finding it quicker than Mint since i've been using it.

i do think i might have to put this beta version of firefox to one side though, maybe until it's released.

---

### Post by jasonwatkins on 2008-04-24
> **Ub1476 said:**
> You can use Audacious as an replacement for XMMS. ;)

just sorted that out - thanks.  it's perfect, just what i want.  now if i could just find a winamp skin for it :D

---

### Post by Eisenwinter on 2008-04-24
I believe I found a pretty big bug.

Before leaving Gutsy, I burned a DVD with all my newest music on it, and some software, which I was going to bring along with me onto Hardy.

After I burned the DVD in Gutsy, I loaded it, to make sure it was burned properly, and everything's in order.

in Hardy, when I try to load it, I get nothing.

I can't access the cdrom device at all.

---

### Post by jasonwatkins on 2008-04-24
doesn't sound like a bug - maybe a mounting problem ??

i'm getting annoyed because floola simply refuses to run at all - i've even downloaded it from the floola site, created a launcher and everything and you double click and nothing .. grrrrrrrrrrrrr

---

### Post by Eisenwinter on 2008-04-24
yeah, I had to mount /dev/scd0.
all is fine now.

---

### Post by andhar on 2008-04-24
Don't really see too much of a difference.

---

### Post by jasonwatkins on 2008-04-24
> **andhar said:**
> Don't really see too much of a difference.

yeah you're probably right - it's not massively different from the last time I used ubuntu (gutsy i think) but the performance, for me, has improved.

---

### Post by pelle.k on 2008-04-24
> i'm getting annoyed because floola simply refuses to run at all - i've even downloaded it from the floola site, created a launcher and everything and you double click and nothing .. grrrrrrrrrrrrr
[http://www.getdeb.net/app/Floola](http://www.getdeb.net/app/Floola)

---

### Post by hessiess on 2008-04-24
live cd > internet dusnt work, install > still dusnt work

---

### Post by Bungo Pony on 2008-04-24
> You can use Audacious as an replacement for XMMS.

I find Audacious to be lousy for extremely large MP3 collections. XMMS is fairly light, does what I want it to, is problem-free, and it supports different skins. Absolutely perfect for my usage. If it won't install in Hardy, that's a problem for me.

---

### Post by jasonwatkins on 2008-04-24
> **pelle.k said:**
> [http://www.getdeb.net/app/Floola](http://www.getdeb.net/app/Floola)

see i'd already checked getdeb and downloaded version 2.92 and it didn't work, but i didn't realise the hardy-compatible version was there.

anyway that works fine now, thanks.

i'm finding a few problems with firefox though - i've ditched the beta release of V3 and gone back to V2, but i can't install any addons or themes, and some sites are STILL not setting cookies correctly.

i'm wondering if i should try a complete removal of all things firefox and re-install V2 from scratch - i only really uninstalled firefox 3 in synaptic.

---

### Post by jasonwatkins on 2008-04-24
well i did a complete removal of all things firefox, rebooted and re-installed firefox V2 and now nothing installs at all - themes, addons - nothing.

anyone got any ideas ?

on the error log i get this ..

> 
Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

that was trying to install a random theme - which is completely compatible.

and when i try and install foxytunes i get these

> Warning: Error in parsing value for property 'display'.  Declaration dropped.
Source File: [http://www.google.co.uk/search?q=foxytunes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=foxytunes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
Line: 1

Warning: Error in parsing value for property 'cursor'.  Declaration dropped.
Source File: [http://www.google.co.uk/search?q=foxytunes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=foxytunes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
Line: 1

Warning: Error in parsing value for property 'font'.  Declaration dropped.
Source File: [http://static.foxytunes.com/l/styles/main.v2.css](http://static.foxytunes.com/l/styles/main.v2.css)
Line: 106

Warning: Error in parsing value for property 'font'.  Declaration dropped.
Source File: [http://static.foxytunes.com/l/styles/main.v2.css](http://static.foxytunes.com/l/styles/main.v2.css)
Line: 106

Warning: Use of captureEvents() is deprecated, see bug 330494.
Source File: [http://www.foxytunes.com/firefox/download/](http://www.foxytunes.com/firefox/download/)
Line: 0

Warning: Use of releaseEvents() is deprecated, see bug 330494.
Source File: [http://www.foxytunes.com/firefox/download/](http://www.foxytunes.com/firefox/download/)
Line: 0

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

---

### Post by screaminj3sus on 2008-04-24
Hardy is GREAT. I have tried MANY MANY distros before I got my new gaming pc this year which is running vista, so I haven't really used linux since then. But I installed this on a  spare drive on my brothers compaq and it is great. Hardware detection on all of my computers is finally great. Sound, screen resolution all working out of the box is something I had never experienced with linux. All I had to do was install the nvidia drivers and restricted extras. Never have I had such a painless install.

It also runs fast and stable as hell and firefox 3 runs MUCH better on linux than 2 did and it looks great integrated with gnome.

Kudos to the ubuntu team.

---

### Post by owenll on 2008-04-24
> **screaminj3sus said:**
> Hardy is GREAT...

Kudos to the ubuntu team.

+1

---

### Post by ExpatPaul on 2008-04-24
After a completely clean install, it's looking good. 

So far the only issue I've had is that my firefox theme isn't compatible with Firefox 3.0. If that is the only problem I have then I will remain a very happy bunny.

---

### Post by Ultra Magnus on 2008-04-24
Oh yea! Just finished downloading Gutsy and having a look around - one annoyance, my wireless card still doesn't work properly but nevermind.

Unfortunately won't get a chance to install it until Monday though - dammit. - So have to wait and see how it compares to past releases.

Edit - Hmmm... Can't seem to find xgl in the repos on the live cd, and I need this to run compiz (dam ati graphics card) does anyone else know anything about this?

---

### Post by bashveank on 2008-04-24
It's better than Gutsy, but could probably use some polish; pulseaudio is set up weird, there are two different kinds of authentication windows,  "access denied" windows are thrown when a gksu should be thrown, etc...

---

### Post by m15hun on 2008-04-24
My first impressions are that it's good.

I was expecting more of a change graphically but it seems to run well.

---

### Post by jasonwatkins on 2008-04-24
> **Bungo Pony said:**
> I find Audacious to be lousy for extremely large MP3 collections. XMMS is fairly light, does what I want it to, is problem-free, and it supports different skins. Absolutely perfect for my usage. If it won't install in Hardy, that's a problem for me.

I have an extremely large MP3 collection - 3880 at last count and at the moment I am finding Audacious very easy to use and totally in line with what I want.

The only downside is that it's not supported in FoxyTunes.

---

### Post by Ozor Mox on 2008-04-24
My only problem so far has been that on one of my computers that previous versions of Ubuntu have worked fine on, the live CD would not start. I fixed it by starting in safe graphics mode, so not a huge deal, and my other computers run it fine. I'll be doing some installations soon. As for content, I was a bit worried about the Firefox beta, but it seems great so far, very fast and nice looking! The default wallpaper is really cool! They seem to have tidied a few things up too like the menus, all in all seems polished, stable and fast.

---

### Post by TBOL3 on 2008-04-24
Well, I downloaded the liveCD for my desktop (because I hosed it somehow).  It works great, except gparted takes a good 20 minutes to start, and I've had to restart it twice now :( .

I also tried the CD with my laptop.  And to my amazement, compiz works now!  Hopefully blender will to.  :)  But because I have a lot of stuff on my laptop, I'm doing a direct update.  I probably should have waited, because it's running about 30 kbs  (With 3 GB to download).  And my ISP and wireless can handle about a meg a second.  Well, it's be going for about a day... :(

But from what I've seen :) .

---

### Post by SunnyRabbiera on 2008-04-24
yeh so far so good for me on my spare.
My biggest issue is why the heck is the screens and graphics configuration app hidden???
also firefox 3 is having some major issues for me, I downgraded to firefox 2 for the time being.

---

### Post by wolfen69 on 2008-04-24
it doesnt work for me at all. tried both firefoxes and both kept crashing. it screwed up grub so bad it wasnt even funny. extremely buggy for me. reformatting back to gutsy right now as i type. hardy isnt usable for me right now. that's ok, gutsy and mandriva spring work great for me. 

hopefully they'll come out with hardy 8.04.1

---

### Post by wolfen69 on 2008-04-24
> **jasonwatkins said:**
> **I have an extremely large MP3 collection** - 3880 at last count and at the moment I am finding Audacious very easy to use and totally in line with what I want.

The only downside is that it's not supported in FoxyTunes.

will it handle 35,000 songs?

---

### Post by screaminj3sus on 2008-04-24
> **SunnyRabbiera said:**
> yeh so far so good for me on my spare.
My biggest issue is why the heck is the screens and graphics configuration app hidden???
also firefox 3 is having some major issues for me, I downgraded to firefox 2 for the time being.

Yeah is there a console command to open it? I was wondering if they took it out or something.

I personally LOVE that they included ff3. I have MAJOR issues with performance with firefox 2 in linux, it is ridiculous. 3 has worked perfectly. And all the extensions OI use are compatible.

---

### Post by ubuntu-freak on 2008-04-24
I'm noticing more attention to detail (theme-wise) with every release. Hardy 8.04.1 is gonna be a ************* sexy *** distro.
 
Thumbs up to the art team.
 
Nathan

---

### Post by odiseo77 on 2008-04-24
I installed Hardy 64 bit like one hour ago and I'm enjoying it a lot. So far, I've found it very functional (as expected) and beautiful. The only downside is the repositories are slow as hell now, which makes it annoying to download/install packages and finishing setting up the system (well, I guess it's something temporary). Other than that, it's working flawlessly here.

---

### Post by Bungo Pony on 2008-04-24
> I have an extremely large MP3 collection - 3880 at last count and at the moment I am finding Audacious very easy to use and totally in line with what I want.

Audacious takes a good minute or two to load the directories I want to listen to whereas XMMS is almost instant. I don't know about you, but when I want to listen to my music, I want to listen to it today :)

Oh yeah, and UbuntuStudio is downloading as I speak!

---

### Post by ubuntu-freak on 2008-04-24
> **Bungo Pony said:**
> Audacious takes a good minute or two to load the directories I want to listen to whereas XMMS is almost instant. I don't know about you, but when I want to listen to my music, I want to listen to it today :)

Oh yeah, and UbuntuStudio is downloading as I speak!

 
Can Audacious not be set to ignore tag info and thus load the directories quicker?
 
Nathan

---

### Post by Formica45 on 2008-04-24
Installed 8.4 64 bit. Flawless. But it seems that my grafix flicker alot with AMD 800 card with restricted drivers.

---

### Post by AaronMT on 2008-04-24
The only thing I do not like is the overall slowness of Firefox beta 5. Not the loading of pages. Just the scrolling, the window dragging, the page rendering. Opposed to how fast it is on XP and vista. 

I just do not like the scrolling, and window rendering so far in Hardy. It's not as smooth as dragging windows and scrolling windows in XP.

---

### Post by Bungo Pony on 2008-04-24
> Can Audacious not be set to ignore tag info and thus load the directories quicker?

Hey, that's pretty good... I just made it load *slower*! Too slow - I had to kill it.

Sorry, but XMMS just seems to be a much better piece of software :)

---

### Post by bobbybobington on 2008-04-24
The OS itself is awesome, but it seems the repository servers are unresponsive due to heavy traffic. At least it seems to be popular :grin:

---

### Post by the_darkside_986 on 2008-04-24
For me, it has been a miserable experience, worse than Gutsy.

The system startup time is unacceptably slow, launching any new process causes the whole system to lag. Doing nearly anything causing severe lagging. I can almost measure the desktop usage in frames per second, including just typing my username in at the GDM prompt.

Oh well, Gutsy seems to have dropped good CRT support, and so I bought an LCD (saves energy). Maybe my lousy single-core system needs to be replaced with one of those new mult-core AMD processors. (Regardless of speed, I am sick of Intel ripping me off all these years with Celerons :( )

---

### Post by vexorian on 2008-04-24
> **wolfen69 said:**
> it doesnt work for me at all. tried both firefoxes and both kept crashing. it screwed up grub so bad it wasnt even funny. extremely buggy for me. reformatting back to gutsy right now as i type. hardy isnt usable for me right now. that's ok, gutsy and mandriva spring work great for me. 

hopefully they'll come out with hardy 8.04.1

When things are so bad, I got to say that it could be that your iso was corrupt.

This is the reason I always use torrents to download ubuntus, well, the fact that the download is faster on days like this one when everybody wants it, is another reason.


> i'm getting annoyed because floola simply refuses to run at all - i've even downloaded it from the floola site, created a launcher and everything and you double click and nothing .. grrrrrrrrrrrrr
Don't double click, try running it from terminal (open a terminal in floola's folder and type ./floola

99% sure it is a problem with either the GTK version or that think they added to ubuntu for "app protection" I don't remember what it is called. But if you post floola's console output here, someone shall be able to help.

---

### Post by TBOL3 on 2008-04-24
Well, grub still takes a good 1/2 hour to load, plus another 1/2+ to do anything.  And on top of that, the won't install.  Sure, BOTH CDs say that they have no errors, but NEITHER of them work in BOTH of the two CD drives.

I just hope I won't have this problem when my laptop finally finishes downloading those updates...

---

### Post by TBOL3 on 2008-04-24
> **vexorian said:**
> When things are so bad, I got to say that it could be that your iso was corrupt.



So, it may be that.  how big is the .iso supposed to be?

I clock in at 699.1.

---

### Post by vexorian on 2008-04-24
> **TBOL3 said:**
> So, it may be that.  how big is the .iso supposed to be?

I clock in at 699.1.

In the live CD there's an option to check the CD for integrity.

You can also verify the .iso file itself using the md5 hash stuff...

---

### Post by Google Spider on 2008-04-24
> **bobbybobington said:**
> The OS itself is awesome, but it seems the repository servers are unresponsive due to heavy traffic. At least it seems to be popular :grin:

yeah, I had to change the download server to get restricted-extras.

---

### Post by TBOL3 on 2008-04-24
Well, as I said, both CDs in both CD players say they are good CDs, yet neither will install.

---

### Post by wolfen69 on 2008-04-25
> When things are so bad, I got to say that it could be that your iso was corrupt.

This is the reason I always use torrents to download ubuntus, well, the fact that the download is faster on days like this one when everybody wants it, is another reason.
i did do a torrent, and checked the MD5, slow burn, verify and on high quality media. OK? what can i say? it doesnt like my machine. that's funny though, because every other distro works fine. all my stuff is linux compatible out of the box.

---

### Post by Vaelrith on 2008-04-25
I used the Update Manager.  Everything seems fine except for sound is all scratchy and distorted...

---

### Post by LolItsGriff on 2008-04-25
I like it a lot. It's very similiar to windows, as I made the jump literally not even 4 hours ago. It's been enjoyable.
 
though there are still some problems (I wish my mic would work ;___;, etc)

 but overall, it's a lot more.. very user integrated and stuff. I like how I tell my computer to do what I want it to, not it tells me what I want it to do o-o

---

### Post by howlingmadhowie on 2008-04-25
> **jasonwatkins said:**
> well i did a complete removal of all things firefox, rebooted and re-installed firefox V2 and now nothing installs at all - themes, addons - nothing.

anyone got any ideas ?

on the error log i get this ..



that was trying to install a random theme - which is completely compatible.

and when i try and install foxytunes i get these

most of the errors are javascript of css errors on the page you're viewing. the one that could be a clue to the problem is 
> Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938 

can you check what /usr/lib/firefox/components/nsExtensionManager.js says on line 3938?

---

### Post by spamzilla on 2008-04-25
> **SunnyRabbiera said:**
> yeh so far so good for me on my spare.
My biggest issue is why the heck is the screens and graphics configuration app hidden???
also firefox 3 is having some major issues for me, I downgraded to firefox 2 for the time being.

System > pref > main menu

then

other > tick screens and graphics

Don't ask me why this has been hidden :)

---

### Post by Saya on 2008-04-25
> **Vaelrith said:**
> Everything seems fine except for sound is all scratchy and distorted...
Preferences -> Sound -> Devices, change everything to ALSA -> Sounds, uncheck Enable software sound mixing (ESD). Restart or do pulseaudio -k.

---

### Post by SunnyRabbiera on 2008-04-25
> **spamzilla said:**
> System > pref > main menu

then

other > tick screens and graphics

Don't ask me why this has been hidden :)

Yeh I know, but its kind of silly why its hidden

---

### Post by Eisenwinter on 2008-04-25
I tried to install XMMS from source.

it depends on GLIB >= 1.2.2. So I went out and got the source for GLIB 2.14 (no binary version was available).

Configured, compiled, and installed glib 2.14.
But the XMMS installation still says there's a dependency problem, that glib-config is not installed.

/me is confused.

---

### Post by ExpatPaul on 2008-04-25
> **odiseo77 said:**
> The only downside is the repositories are slow as hell now, which makes it annoying to download/install packages and finishing setting up the system (well, I guess it's something temporary).

That could just be down to the number of people who are upgrading and reinstalling stuff at the same time. They were performing fine for me last night.

---

### Post by odiseo77 on 2008-04-25
> **ExpatPaul said:**
> That could just be down to the number of people who are upgrading and reinstalling stuff at the same time. They were performing fine for me last night.

Yes, that's what I thought too. The weird thing is I tried with servers from Venezuela and Argentina, as well as with plain [http://archive.ubuntu.com](http://archive.ubuntu.com) etc, etc, (without the country code), and it was the same (a friend from Argentina told me the servers there are fine for him). Well, I guess I have to wait a little. Going to leave some stuff downloading and then go back to bed, since it's 4:43 am here :)

---

### Post by AdamWill on 2008-04-25
> **Eisenwinter said:**
> I tried to install XMMS from source.

it depends on GLIB >= 1.2.2. So I went out and got the source for GLIB 2.14 (no binary version was available).

Configured, compiled, and installed glib 2.14.
But the XMMS installation still says there's a dependency problem, that glib-config is not installed.

/me is confused.

1.2x and 2.x are completely different series of GTK+ (and glib), they're incompatible. You need to get glib 1.2x.

I'd suspect you'd be better off just using Audacious, which is a modern - GTK+2 - based XMMS clone, and likely available in Ubuntu's repositories. Unless I missed an earlier part of this discussion and Audacious isn't working, or something.

---

### Post by graabein on 2008-04-25
I've only tried the Live CD and as usual it don't recognise my nvidia GeForce 6600GT card and/or my monitor (1600x1200). Max resolution is 1024x768 which I think is pretty lousy. 

I'm uncertain I want to do the upgrade yet because of Firefox 3 beta. I like where my Firefox is now with Adblock Plus and NoScript. 

I don't want to update to version 3 before Add-ons work 100%.

So maybe I'll get Hardy when version 3 final is in the repos.

---

### Post by Saya on 2008-04-25
> **graabein said:**
> I like where my Firefox is now with Adblock Plus and NoScript.
I don't want to update to version 3 before Add-ons work 100%.
Both Adblock Plus and NoScript work with Firefox 3.

---

### Post by Vaelrith on 2008-04-25
> **Saya said:**
> Preferences -> Sound -> Devices, change everything to ALSA -> Sounds, uncheck Enable software sound mixing (ESD). Restart or do pulseaudio -k.

It's still scratchy.  Which is weird.

---

### Post by diplomat.x on 2008-04-25
I deleted gutsy and installed hardy from scratch today. And very frankly, nothing new. But afterall this is an LTS version. Looking forward to 8.10.

---

### Post by BluntBox on 2008-04-25
So far its a downgrade from Gutsy for me. Having some issues with trying to mount 2 of my NTFS IDE drives which worked flawlessly in Gutsy. They both get /dev/sd*# assignments (what happened to IDE drives being hd*#?), but Hardy just refuses to mount them "Failed to access volume '/dev/sdb1': No such file or directory". ******** I say! Thankfully the data on them is still perfectly in tact, as I can read and write to them from Windows.

Other than that, I have frequently had the desktop lock up when pressing the Quit button in the gnome panel System menu. The box with Shutdown, Logout etc sometimes doesn't appear, the mouse can be moved around but nothing can be interacted with and I have to force restart the xserver.

---

### Post by pbpersson on 2008-04-25
> **screaminj3sus said:**
>  Hardware detection on all of my computers is finally great. Sound, screen resolution all working out of the box is something I had never experienced with linux. 

It won't be long until we are all spoiled and that part will be taken for granted.  I can remember a time when you had to recompile the kernel to have it recognize your sound card.  Thank goodness those days are gone forever :)

---

### Post by Az_135r on 2008-04-25
so far so good, i have two  workstations set up, 1 desktop running 64bit, 1 laptop running 32bit

installation:
32bit on laptop - no problems
64bit - failed first installation (cd defect!), then had minor problems configuring X with dual displays, couldnt get $nvidia-settings to get the config right so had to hand code xorg.conf.. and a few other minor issues (accidentally screwed folder permissions!)... but all resolved now :)

performance:
im surprised at some of the comments, because ive found that hardy is much more responsive, and im a quite a heavy user of compiz effects... this is evident on both set ups

also, crossover office appears to be to be much faster, both opening and closing win32 applications (office 2003 etc)... previously there was a substantial lag

migration of applications:
surprising very good, on gutsy 64bit i still had applications with unresolved issues, ie skype & flash!

ive now got skype & flash audio working + volume control on 64bit ubuntu! :)

+ crossover office, vmware, aptana, etc etc all working fine

:guitar:

---

### Post by Kingsley on 2008-04-25
I like the boot and shut down speeds of Hardy. I can't remember if it's my fault or not, but Fedora seems to be much slower in that department. Apt-get is also a bit faster than yum, but I still prefer the latter because of the plugins and advanced features, ie. yum-presto.

There are some things that I find annoying. For instance, having to type 'sudo' before every root task. I prefer to log in as root in the terminal and do all my work from there. I also don't like the way the menu is set up in System > Preferences. It'd be tidier and much less confusing if the preferences menu was broken up into 4 or 5 submenus.

I haven't noticed many changes since Gutsy, but Hardy is nice overall. I'll probably stick with it until Fedora 9 is released next month.

---

### Post by bigbrovar on 2008-04-25
am really enjoying this hardy thing ... my system is more responsive and for the first time i could hibernate and recover in my sony vaio damn! that is cool... but there was a black fly in my hardy ice creme today ... system just frooze and i had to do a reset ... use to have that problem in gutsy .. dont what could have caused it .. on the whole everything is fine and way way better than gutsy

---

### Post by BanskuZ on 2008-04-25
I love it. My monitor was detected finally correctly without hazzle. Everything seemed to work well and it even installed Flash when I visited Youtube.

There was one error thought when I moved some pictures to my computer from my camera. Complained something about "~/Photos" (I think it's because I don't have folder name like that, but "Kuvat"), but it still moved the pictures well.

---

### Post by vexorian on 2008-04-25
> There are some things that I find annoying. For instance, having to type 'sudo' before every root task. I prefer to log in as root in the terminal and do all my work from there
1. open a terminal
2. type sudo -i
3. enjoy

Anyways, I used to do that but after few months I stopped doing so, sudo got the skill that it doesn't *really* require you to input the password every time you want a root task to be done, it looks like as long as you use the same terminal it will remember your password for a while, this period of time is small (which is good) but seems to be long enough to do all the root things I was going to do (which is also good).

---

### Post by kiwited on 2008-04-25
Took me ages to go through the upgrade from gutsy, but that was clearly due to the popularity of this distro. Seems to be quicker and smoother than Gutsy.

It fixed a few problems - Java works again - it stopped working on the upgrade from 7.04 to 7.10 so Google Earth nearly starts. At least it gets past the initialising screen now but just ends up with a black screen. Limewire starts now and I can see video on You Tube, all of which stopped with the upgrade to 7.10.

But......It still cannot work with my video card (ATI Radeon HD2600XT) so no special effects for me. Also does not recognise anything plugged into any USB port (cameras, card readers etc) and does not recognise a built in USB card reader either.

I cannot find the hardware detection function to see if the "missing" bits are there but not mounted or something.

Sounds a bit negative - not intended as it seems sweet, but a couple of annoyances which will have to be sorted.

My system is AMD 64bit 6400+ dual processor, 2 gig RAM and the pesky Radeon card which I wish I had never seen.

Theo

---

### Post by miggols99 on 2008-04-25
> **Kingsley said:**
> I like the boot and shut down speeds of Hardy. I can't remember if it's my fault or not, but Fedora seems to be much slower in that department. Apt-get is also a bit faster than yum, but I still prefer the latter because of the plugins and advanced features, ie. yum-presto.

There are some things that I find annoying. For instance, having to type 'sudo' before every root task. I prefer to log in as root in the terminal and do all my work from there. I also don't like the way the menu is set up in System > Preferences. It'd be tidier and much less confusing if the preferences menu was broken up into 4 or 5 submenus.

I haven't noticed many changes since Gutsy, but Hardy is nice overall. I'll probably stick with it until Fedora 9 is released next month.
I really don't know why people say "I have to put sudo before everything". It's as simple as
```

sudo -i
```
to get into a root terminal instead of "su". If the preferences menu is really annoying you, you could just right click the menu and choose "Edit menu".

---

### Post by K.Mandla on 2008-04-25
Moved to Testimonials and Experiences.

---

### Post by vexorian on 2008-04-26
So far it looks good.

I am just testing the live CD since I am conservative in which relates to upgrading ,need more preparations before trying that. I am actually using the live CD right now.

This is probably the least boot time the  live CD has ever had, it is also nice it asks you for language automatically. 

It is surprising that the live CD actually feels more responsive than my setup. I also like the mild improvements that not a lot of people would notice the first time, it looks like the theme was modified for good.

Another pleasant surprise, the live CD had sound, before I had to wait for the actual installation before getting it.

I initially thought there were network issues, turns out the DNS I was using fell off line (My connection uses static IP and no DCHP)

The visual effects tab allows me to pick compiz effects but just gives me an error message instead of saying that I should install nvidia.

I think it is good for a LTS. Heck, at least network works (unlike gutsy :) )

After the live-cd experience, I feel eager to upgrade, so I guess it is time to work...

---

### Post by Ripfox on 2008-04-28
> **jasonwatkins said:**
> i'm actually finding it quicker than Mint since i've been using it.

i do think i might have to put this beta version of firefox to one side though, maybe until it's released.

Not too hard to do, imho mint is a dog

---

