---
title: "Does everyones firefox 3 crash on flash sites?"
date: 2008-07-16
forum: The Cafe
---

### Post by Jareth on 2008-07-16
Is this just a problem with a few people or is it everyone?
I'm trying to find a solution and I think I'll just downgrade to firefox 2 provided it is stable.
I heard that it had something to do with pulseaudio, like a few other things. So would downgrading it fix it? I just want firefox to stop closing on sites like youtube and such.

---

### Post by Tom--d on 2008-07-16
Thats Flash being Flash. Not Firefox's fault.

---

### Post by NilsE on 2008-07-16
Firefox 2 crashes on flash sites also just not as much. Actually, when it does it freezes and needs to be forced out.

Try going into Synaptic and remove flashplugin-nonfree and then reinstall it.

If libflashsupport is still installed remove it. 

If you lose your sound in flash the find the various posts on this forum about flash sound.

---

### Post by Le-Froid on 2008-07-16
Happens to me all the time. On every single flash site..Have to use lynx to go to certain sites :(

---

### Post by finer recliner on 2008-07-16
the instructions here fixed the problem for me (hardy heron w/ firefox 3.0):

[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

---

### Post by paul101 on 2008-07-16
i haven't had any problems with ubuntu and flash sites :confused:

---

### Post by tuxxy on 2008-07-16
I cant say it does, what sort of sites specifically if you mean Youtube there could be another problem...

---

### Post by Jareth on 2008-07-16
The sound has been ok.
I go to youtube for example and just as it starts the video it will close firefox the first time. When I reopen it and restore the session it will go straight to the video and play it fine. Then it will play a few more videos no problem but then after a while it will close again.


Kind of annoying.

---

### Post by zmjjmz on 2008-07-16
A good idea would be to use FlashBlock so that you have to activate flash first.

---

### Post by Jareth on 2008-07-16
Yeah, hadn't thought of flashblock and I used to use it all the time.
I'll try that other fix first and if its the same flashblock will probably sort it.

---

### Post by NilsE on 2008-07-16
> **Jareth said:**
> The sound has been ok.
I go to youtube for example and just as it starts the video it will close firefox the first time. When I reopen it and restore the session it will go straight to the video and play it fine. Then it will play a few more videos no problem but then after a while it will close again.


Kind of annoying.Did you try my suggestion above? It will probably fix it and not make it worse.

---

### Post by LaRoza on 2008-07-16
I use Opera :-) and Flash 10.

If Flash does cause a problem (rare), I can easily block it. I don't need to add things to my browser to make it work.

---

### Post by ghindo on 2008-07-16
Maybe try Gnash?

---

### Post by rune0077 on 2008-07-16
I haven't experienced any crashes, but sometimes Firefox won't load the flash-video and I have to hit reload (sometimes a few times) for it to load probably.

---

### Post by Jareth on 2008-07-16
I followed finer recliners link and it looks about the same as removing and reinstalling libflashsupport with a few other things too.
I just did it and watched a few vids, so far so good. I'll have to see how it goes as it could kick me out at any minute but it 'feels' like it is behaving better.
I don't mind the occasional crash as I know what computers are like.

But trying to watch flash vids or stumbling on a site with flash was getting ridiculous.

---

### Post by init1 on 2008-07-16
Yeah, FF3 still crashes due to Flash but not as often as Iceweasel in Debian Etch.

---

### Post by speedwell68 on 2008-07-16
Used to have loads of Flash problems in FF under Edgy, Fiesty and Gutsy.  But with Hardy and FF2 and latterly FF3 it has been sweet as a nut.

---

### Post by bp1509 on 2008-07-16
> **paul101 said:**
> i haven't had any problems with ubuntu and flash sites :confused:

same here.

---

### Post by keiichidono on 2008-07-16
Check out the Flash fixing section of [this]("http://ubuntuforums.org/showthread.php?t=766683") guide. Use Flash 10 beta 2 and you should be pretty fine. I used to have the same problems. Now my only problem is that PusleAudio can't play more than one audio source and playing Flash and afterwards trying to play audio freezes the program and forces me to restart to get the functionality back.

---

### Post by tuxxy on 2008-07-16
The flash-nonfree should play fine, there is definitely a problem somewhere.

---

### Post by Blahblah54 on 2008-07-16
Yeah, I've had this problem pop up quite a bit on youtube and hulu. Tried out the fixes in here and haven't had any crashes so far, so hopefully that fixed it.

---

### Post by picpak on 2008-07-16
It only happens to me on last.fm. How about anyone else?

---

### Post by tuebinger on 2008-07-16
It's been happening to me pretty much every day, epecially on eBay -- but also on other sites.  My system will totallly lock up.  I've stopped using Firefox for the most part and am mostly using Opera for my browsing, but I may try some of these fixes in this thread to try to fix the problem since I still need Firefox for some things.

---

### Post by kool_kat_os on 2008-07-16
sometimes....

---

### Post by Ishimaru Chiaki on 2008-07-16
My Firefox used to crash only from time to time, and then on June 29, it decided to crash every 5 minutes.  I got a record of 12 crashes during the same day.  It got at the point that I began to try other browsers : Epiphany, then Iceweasel I'm still using.

Firefox didn't crash only on pages with Flash, it was crashing even when I'm on a simple HTML page with no web app or script, and even when I'm upstairs.

An example : I'm browsing on ubuntu-fr.org then Mom calls me for dishwasher job.  I minimize the Fx window then I go upstairs.  15 minutes later, I get back to my PC and I see the Fx bar at the bottom has gone.

I would like to have this problem solved because I was using extensions (Web Developer, etc.) before I change browser, and I haven't tried to import the extensions for Iceweasel.

---

### Post by L815 on 2008-07-16
When I used libflashsupport, mine crashed often.
When flash 10 beta was released through backports (without libflashsupport installed), some random websites would crash every visit.

Now since the latest updates, everything seems to be OK, even those sites which crashed before.

---

### Post by NilsE on 2008-07-17
> **L815 said:**
> Now since the latest updates, everything seems to be OK, even those sites which crashed before.
The latest updates reverted flash back to version 9 without libflashsupport.  Version 10 Beta 2 causes crashes on opening some sites but very few. Version 10 Beta 1 is the most stable release and I have been on it for awhile with no crashes plus it fixes the menu under flash problem and is quicker.

So, the best option is either version 9 or version 10 Beta 1 without libflashsupport.

---

### Post by the_darkside_986 on 2008-07-17
Ubuntu Hardy x86-64 w/ Flash 10 and FF3 here and no problems yet :)

---

### Post by Masoris on 2008-07-17
Adobe flash 9 = Random crash
Adobe flash 10 beta = Random crash
Gnash = No sound + many buggy
Swfdec = No sound + manual start to play

That random crash make me on panic. :lolflag:
So I use flash on Windows XP in my Virtualbox. :lolflag:

---

### Post by QuiescentWonder on 2008-07-17
This makes me not want to use Ubuntu.

Someone needs to make a thread where the first post is all the information about why it happens, and includes all ways known to fix this problem. Firefox crashes 2 or 3 times a day for me. It's EXTREMELY annoying. :mad:

---

### Post by SuperSonic4 on 2008-07-17
My firefox doesn't crash with flash installed now. It's never crashed for me in Kubuntu but that could be because of updates at the same time

---

### Post by QuiescentWonder on 2008-07-17
Has anyone tried this? Apparently it's been a problem since April: [http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

EDIT: Nevermind, this doesn't fix jack s***. It's just a workaround that disables flash, and apparently somehow increases it's CPU usage at the same time. That's what I've gotten out of the comments anyway.

See here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

---

### Post by BigSilly on 2008-07-17
Yeah, mine crashes. It's not all the time, but I'd say two out of three times a Flash video will crash the browser. It's a right pain in the proverbial, and the only downside to FF3. Is there any kind of fix on the way, or are we looking at a "let's pretend it doesn't exist" attitude from Mozilla?

---

### Post by the_darkside_986 on 2008-07-17
The problematic code is of Adobe Flash, but they are dealing with a difficult and poorly documented NPAPI toolkit for writing Mozilla plugins so it is fortunate we have anything from them at all.

I mean, is there a single clear example anywhere on the web of how to write a plugin that displays "Hello world" in a rectangle on a page...?

---

### Post by nick09 on 2008-07-17
No. But the flash problem is adobe's problem.

---

### Post by peter_babeone on 2008-07-18
> **L815 said:**
> When I used libflashsupport, mine crashed often.
When flash 10 beta was released through backports (without libflashsupport installed), some random websites would crash every visit.

Now since the latest updates, everything seems to be OK, even those sites which crashed before.

I have the same problem with libflashsupport. FF3 crashes very often when I use flash.

---

### Post by ferd on 2008-07-18
Occasionally, but I have 10 installed. My current problem is with the MBUSA.com site which indicates it has loaded to 100% but nothing else appears on the display. This may be a first day glitch so I will try again tomorrow.

---

### Post by YaroMan86 on 2008-07-18
Ever since I went FF3 and F10, I've had little problems like that with flash anymore. On occasion Flash won't LOAD, but eh. A quick restart of firefox clears that up.

---

### Post by bruce89 on 2008-07-18
> Does everyones firefox 3 crash on flash sites?

Of course, Adobe's Flash is very badly written, this is why it's not available on x86_64.

---

### Post by henriquemaia on 2008-07-19
> **finer recliner said:**
> the instructions here fixed the problem for me (hardy heron w/ firefox 3.0):

[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

Thanks, that did it. I was getting really annoyed with the endless crashing on Firefox these last few days. :KS

---

### Post by dizee on 2008-07-19
i use opera but still have trouble with flash occasionally. if for example i try to click forward to a particular point on a flash video, every so often it crashes, freezing the whole browser. i tried installing flash 10 directly from the adobe site but that was even worse performance-wise.

---

### Post by adityakavoor on 2008-07-19
I have no probs. FF3 rocks

---

### Post by Scruffynerf on 2008-07-19
Random crashes with flash, versions 9 and the beta 10.

It will also take out any browser based on Gecko.

Opera just locks up.

---

### Post by stinger30au on 2008-07-19
i can play the file and set audio/video and it crashed about every 2nd movie

---

### Post by Jareth on 2008-07-19
Just to give an update, the flash has been behaving itself since that fix so I'm happy I don't have to swap from firefox.

This was the link that fixed it.

[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)


Not sure about the other probs with firefox. This was only regarding flash problems.

Thanks to everyone, as usual.:guitar:

---

### Post by IusedTObeSOMEONEelse on 2008-07-19
[FONT="Comic Sans MS"]**Works great for me!**[/FONT]

---

### Post by peter_babeone on 2008-07-19
I found a solution, maybe it can help you.

Follow the link: [http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)
but 

> sudo apt-get remove --purge flashplugin-nonfree

download adobe flashplayer and install it.

> wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

tar xvf install_flash_player_9_linux.tar.gz

cp install_flash_player_9_linux/libflashplayer.so .mozilla/plugins


and uninstall libflashsupport

> sudo apt-get remove --purge libflashsupport

From now on, you just can't use firefox3 to hear music at the same time with amarok, etc.

It will work :popcorn:

---

### Post by ACGarib on 2008-07-19
I did parts A and B here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It removes libflashsupport so no more crashes AND it lets you listen to sound from both flash and another program at the same time.

I did it a few weeks ago and I haven't experienced a crash since. Before, it used to be every other youtube video.

By the way, does flash 10 seem extremely slow compared to flash 9 on certain websites? It eats up 100% of one of my cores and xorg eats up most of the other, bringing my computer to a crawl. last.fm is one of them.

---

### Post by gletob on 2008-07-19
> **paul101 said:**
> i haven't had any problems with ubuntu and flash sites :confused:
yeah I'm watching youtube in the other tab

---

### Post by peter_babeone on 2008-07-20
> **ACGarib said:**
> I did parts A and B here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It removes libflashsupport so no more crashes AND it lets you listen to sound from both flash and another program at the same time.

I did it a few weeks ago and I haven't experienced a crash since. Before, it used to be every other youtube video.

By the way, does flash 10 seem extremely slow compared to flash 9 on certain websites? It eats up 100% of one of my cores and xorg eats up most of the other, bringing my computer to a crawl. last.fm is one of them.

I'm now using the lastest version von Firefox 3.01[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/) and it doesn't work for me if I use libflashsupport for firefox and amarok together

For many sites like youtube it seems to be fine with libflashsupport, but not all for example [www.imeem.com/](www.imeem.com/)

---

### Post by mdsmedia on 2008-07-20
> **LaRoza said:**
> I use Opera :-) and Flash 10.

If Flash does cause a problem (rare), I can easily block it. I don't need to add things to my browser to make it work.No, just like everything works in Windows. Gimme a break!!

---

### Post by ACGarib on 2008-07-20
The guide that I recommended has changed since I followed it: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Part B used to install flash 10 beta2 and uninstall libflashsupport and in conjunction with part A, flash stopped crashing on most sites. There are however some sites that always instantly crash flash + firefox for some reason.

The other thing that part A of this guide fixed for me was pulseaudio crashing when I paused music for more than 15 minutes or so. 

It seems that the current part b of the guide is the most stable option available. Instead of flash+firefox crashing, only flash crashes. Just reload the page to get flash up again.

---

### Post by peter_babeone on 2008-07-20
> **ACGarib said:**
> The guide that I recommended has changed since I followed it: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Part B used to install flash 10 beta2 and uninstall libflashsupport and in conjunction with part A, flash stopped crashing on most sites. There are however some sites that always instantly crash flash + firefox for some reason.

The other thing that part A of this guide fixed for me was pulseaudio crashing when I paused music for more than 15 minutes or so. 

It seems that the current part b of the guide is the most stable option available. Instead of flash+firefox crashing, only flash crashes. Just reload the page to get flash up again.

It worked like a charm, thanks for your help :lolflag:

---

### Post by keiichidono on 2008-07-20
Thanks for the link, I want to ask how I can fix the flash problem I've been having there. I also may install Xubuntu over Ubuntu on a friends laptop to circumvent problems.

---

### Post by cardinals_fan on 2008-07-20
> **mdsmedia said:**
> No, just like everything works in Windows. Gimme a break!!
What does Windows have to do with Opera working with Flash?

---

### Post by frabcus on 2008-08-05
I use Epiphany, and couldn't get rid of this Flash crash, even with PulseAudio uninstalled, until I remembered it didn't happen when I ran Firefox 2.

I purged the firefox-3.0 package, installed firefox-2, restarted Epiphany. Since then everything is fine.

If it is a bug in Flash per se, it is a very strange one given it only happens in Firefox 3, not in Firefox 2 or Opera. I suspect it is a bug in Firefox 3. Worth testing with epiphany-webkit too as another data point.

---

### Post by BigSilly on 2008-08-05
I am absolutely sick of Flash with Firefox to be honest. It's a real pain when it just decides to shut all your browser tabs down when you're downloading something. I've tried using Opera, which seems to be fine for the most part, and hasn't crashed on me. But I do prefer to use FF.

Strangely though, yesterday I decided to install KDE4 alongside Gnome on my current Hardy install. As of yet I've not yet seen Flash crash FF3 in KDE4. It may happen yet, but so far nothing.

Also, I was surprised to hear of some Windows users who were getting the same Flash crash there too. So it's not just Linux by the sound of it.

---

### Post by jocose on 2008-08-07
@Jareth:
"So would downgrading it fix it?"

[color=red]**Uninstalling pulseaudio worked for me.**[/color]

The firefox and epiphany crashes were getting so bad, I decided to take the advice of a user posting in a pulseaudio titled thread and uninstall most of the pulseaudio packages.

I uninstalled all of the pulseaudio packages except for the following two because they wanted to remove other programs too:

libpulse0
vlc-plugin-pulse

Prior to uninstalling pulseaudio, I had set my sound settings all for ALSA, but pulseaudio was still loaded. I disabled pulseaudio in sessions but pulseaudio was still loaded upon reboot.

[color=blue]Now, since I **uninstalled pulseaudio**, I haven't noticed *any* crashes![/color] I wasn't using pulseaudio anyway, so why have it running? I had tried ALL of the suggested fixes, read Launchpad bugs threads, tried Flash 10, tried Firefox 2 AND 3 and both kept crashing. It seemed like once in awhile with a Firefox update in 2 and 3, it wouldn't crash as often, but along came a FF update and it was back to crashing.

This worked for me! [color=blue]**Goodbye Pulseaudio, HELLO more stable Firefox with Flash!**[/color] I'm sure I'll still have the crash now and then because of Flash, but nothing like I was experiencing when Pulseaudio was installed. I have users using the current Flash plugin 9, and some using the beta Flash plugin 10, the problem is solved for all of us.

:KS:KS:KS:KS:KS

GOODBYE Pulseaudio!

---

### Post by OutOfReach on 2008-08-07
> **BigSilly said:**
> I am absolutely sick of Flash with Firefox to be honest. It's a real pain when it just decides to shut all your browser tabs down when you're downloading something. I've tried using Opera, which seems to be fine for the most part, and hasn't crashed on me. But I do prefer to use FF.

Strangely though, yesterday I decided to install KDE4 alongside Gnome on my current Hardy install. As of yet I've not yet seen Flash crash FF3 in KDE4. It may happen yet, but so far nothing.

Also, I was surprised to hear of some Windows users who were getting the same Flash crash there too. So it's not just Linux by the sound of it.

I absolutely hate those kind of Flash crashes, like you said especially when I'm downloading something, specifically a large file, I have to start over again. :/ I hope and pray that one day these things will get fixed.[-o<

---

### Post by Delever on 2008-08-07
Sometimes, it does not load completely. No more than that.

Ubuntu 8.04 64-bit, nVidia, pulseaudio

---

