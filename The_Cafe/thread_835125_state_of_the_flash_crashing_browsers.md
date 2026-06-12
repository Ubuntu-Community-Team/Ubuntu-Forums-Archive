---
title: "state of the flash crashing browsers"
date: 2008-06-20
forum: The Cafe
---

### Post by ELD on 2008-06-20
I am just wondering about the state of the bug the causes flash to crash web browsers with audio support on?

Has any work been done on it yet?

---

### Post by th3james on 2008-06-20
Yeah, I'll bump this, its a complete PITA! having to close every audio app if i want to go on youtube.

The problem lies with the fact that flash is developed by Adobe, so no-one except them can bug fix it, and they've made it pretty apparent they don't care about Linux users.

Such a pain that this closed proprietary format has become so popular on the supposedly 'open' internet. Hopefully the open source players swfdec and gnash will become usable soon!

Edit: Just done some quick googling, seems installing libflashsupport makes it work better (although still not flawlessly!)

```
sudo apt-get install libflashsupport
```

---

### Post by ELD on 2008-06-20
I tried using free flash alternatives and half the time they didn't work at all, and most sites i visit frequently use flash, as annoying as it is :(

Libflashsupport is the lib that enabled sound for flash :P, that is what crashes it, without that installed no crashes, but also no sound.

---

### Post by angloscot on 2008-06-20
> **th3james said:**
> Yeah, I'll bump this, its a complete PITA! having to close every audio app if i want to go on youtube.

The problem lies with the fact that flash is developed by Adobe, so no-one except them can bug fix it, and they've made it pretty apparent they don't care about Linux users.

Such a pain that this closed proprietary format has become so popular on the supposedly 'open' internet. Hopefully the open source players swfdec and gnash will become usable soon!

Edit: Just done some quick googling, seems installing libflashsupport makes it work better (although still not flawlessly!)

```
sudo apt-get install libflashsupport
```

wow, that's good code! I've gone from very poor flash service to A.O.K. Thanks!

---

### Post by thedon_1 on 2008-06-20
My firefox frequently crashes when going to youtube e.t.c

Wasn't there a beta of the new flash released? Would that help?

---

### Post by Ub1476 on 2008-06-20
Is it just me who has Flash working alright?

And I have to use ndpluginwrapper since I'm using 64-bit Firefox on amd64.. 

I get multiply sound outputs (both from Audacious, Youtube etc), and my browser never crash. Sometimes it wont show the flash content though, but then I just close the browser and open it again.

---

### Post by samjh on 2008-06-20
> **Ub1476 said:**
> Is it just me who has Flash working alright?

And I have to use ndpluginwrapper since I'm using 64-bit Firefox on amd64.. 

I get multiply sound outputs (both from Audacious, Youtube etc), and my browser never crash. Sometimes it wont show the flash content though, but then I just close the browser and open it again.

I've got it working fine too, without libflashsupport.  However, I've installed it just to see if it makes any difference.

Like you, my only problem with Flash is that sometimes the Flash content doesn't appear.

---

### Post by SupaSonic on 2008-06-20
I've done 
```
sudo apt-get remove pulseaudio libflashsupport
```
and since then no flash issues with sound. But it hangs opera and firefox regularly.

---

### Post by Extreme Coder on 2008-06-20
Well, I'm not too mad at Adobe, since they're doing this:
[http://www.phoronix.com/scan.php?page=news_item&px=NjQ1Mg](http://www.phoronix.com/scan.php?page=news_item&px=NjQ1Mg)

---

### Post by geoken on 2008-06-20
I don't get it. Everyone and their grandmother complains about what a horrible idea it was to include pulse audio in 8.04 and as long as the app experiencing difficulty is open source it's perfectly acceptable to place all blame on pulse audio itself, but the second a closed source app has the same issues no one looks at pulse audio as the potential problem and all blame goes to Adobe.

For the record, I've gone back to ALSA and haven't had flash crash my browser once in the several weeks since I've done it. It's also subsequently returned functionality to various open source music creation apps as well as seemingly reduced the amount of crashes in Pitivi.

---

### Post by th3james on 2008-06-20
> **Extreme Coder said:**
> Well, I'm not too mad at Adobe, since they're doing this:
[http://www.phoronix.com/scan.php?page=news_item&px=NjQ1Mg](http://www.phoronix.com/scan.php?page=news_item&px=NjQ1Mg)

Wow, I missed that, good news i guess (although an open source flash player from adobe would be nice... unlikely though)

---

### Post by Barrucadu on 2008-06-20
I'm using ALSA, Opera, and the latest flash plugin and can listen to music fine while using a flash app involving music. It's probably worth mentioning that although I'm using Arch instead of Ubuntu, I had no problems with flash on Ubuntu either.

---

### Post by FFighter on 2008-06-20
Firefox 3 final with Flash Player 10 still eventually crashes and this is really annoying.

---

### Post by RavUn on 2008-06-20
Is this why I haven't been able to listen to music through flash any longer?  I upgraded to 8.04 ubuntu (not knowing it upgraded firefox) and now I cannot play songs through various sites I regularly visit.  I'm pretty disappointed... everything was fine before the upgrade.  I can't use most of my add-ons either.

---

### Post by CautionaryX on 2008-06-20
Most add-on developers haven't made them compatible with FF3 yet. Just have to wait I guess.

---

### Post by dmizer on 2008-06-20
> **Ub1476 said:**
> Is it just me who has Flash working alright?

And I have to use ndpluginwrapper since I'm using 64-bit Firefox on amd64.. 

I get multiply sound outputs (both from Audacious, Youtube etc), and my browser never crash. Sometimes it wont show the flash content though, but then I just close the browser and open it again.

nope, you're not alone. i have zero problems with flash or audio from multiple devices, streaming from the internet or otherwise.  i can even play flash interactive games, which used to cause me lots of problems.  using 8.04, flash 9.0 r124

i vaguely recall having some problems early on though, and apparently i fixed it by going with alsa instead of pulse audio.

you'll probably get helpful information by starting firefox from the command line.  that way, when it crashes you'll get error messages.

---

### Post by original_jamingrit on 2008-06-20
I have a buddy on Ubuntu 8.10 64-bit, he's using swfdec.  He told me that watching youtube, swfdec would periodically cause firefox to hang or freeze.  Now he's using kazehakese instead of firefox, and he says he doesn't have that problem at all anymore.  I haven't investigated much, but there might be something to suggest that kazehakese handles plugin crashes gracefully.  Anyone else experience this?

---

### Post by ice60 on 2008-06-20
> **Extreme Coder said:**
> Well, I'm not too mad at Adobe, since they're doing this:
[http://www.phoronix.com/scan.php?page=news_item&px=NjQ1Mg](http://www.phoronix.com/scan.php?page=news_item&px=NjQ1Mg)
i thought the reason they did that was to compete in the phone market, or with silverlight, or what ever it is. i remember reading they had no other option. maybe someone else will know, i can't remember now.

i have no problems with flash on opera and firefox. although, i have it disabled by default, but on the sites i use it it works fine - youtube etc. i don't have pulseaudio.

---

### Post by amishphysicist on 2008-06-20
For me, it's google reader + flash.  Kills my firefox every time.  So bad I have to restart before firefox will even launch again.  

I just got done fixing my xorg.conf after a failed attempt at setting my display depth to 24, since that was supposed to fix it.  Unfortunately, it just broke all my display properties and made me a sad panda. Well, sad at least.

---

### Post by jrusso2 on 2008-06-20
I am not having any problem with flash causing crashes on any distro I am running.  Of course I am still on Gutsy, Mandriva, and Debian so I don't have Hardy or anything with the dreaded pulse audio.

---

### Post by Exsecrabilus on 2008-06-20
> **original_jamingrit said:**
> I have a buddy on Ubuntu 8.10 64-bit, he's using swfdec.  He told me that watching youtube, swfdec would periodically cause firefox to hang or freeze.  Now he's using kazehakese instead of firefox, and he says he doesn't have that problem at all anymore.  I haven't investigated much, but there might be something to suggest that kazehakese handles plugin crashes gracefully.  Anyone else experience this?
8.10????? You mean pre-alpha?????

---

### Post by Happy_Man on 2008-06-20
There's an awesome guide over at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) that has done wonders for me. Flash went from being the reason I would avoid sites like YouTube to being rock-solid, with all the benefits of PulseAudio. Definitely give it a shot.

---

### Post by Exsecrabilus on 2008-06-20
> **Happy_Man said:**
> There's an awesome guide over at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) that has done wonders for me. Flash went from being the reason I would avoid sites like YouTube to being rock-solid, with all the benefits of PulseAudio. Definitely give it a shot.
All my problems.....solved. :)

---

### Post by Polygon on 2008-06-21
> **geoken said:**
> I don't get it. Everyone and their grandmother complains about what a horrible idea it was to include pulse audio in 8.04 and as long as the app experiencing difficulty is open source it's perfectly acceptable to place all blame on pulse audio itself, but the second a closed source app has the same issues no one looks at pulse audio as the potential problem and all blame goes to Adobe.

For the record, I've gone back to ALSA and haven't had flash crash my browser once in the several weeks since I've done it. It's also subsequently returned functionality to various open source music creation apps as well as seemingly reduced the amount of crashes in Pitivi.

yes pulse audio is really shaky, but it will get better, and the benefits of pulseaudio will show themselfs in the long run. Once everything starts supporting it, then you will never see again 'unable to initialize i/o!" (im looking at you audacity). hopefully things like commercial video games and various plugins and programs will be able to have audio working out of the box, regardless of what soundserver they use (alsa, oss, etc)

---

### Post by ELD on 2008-06-21
> **Happy_Man said:**
> There's an awesome guide over at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) that has done wonders for me. Flash went from being the reason I would avoid sites like YouTube to being rock-solid, with all the benefits of PulseAudio. Definitely give it a shot.

I have tried the guide, and will report back in a day or two and see how it fares.

---

### Post by quanumphaze on 2008-06-21
> **Happy_Man said:**
> There's an awesome guide over at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) that has done wonders for me. Flash went from being the reason I would avoid sites like YouTube to being rock-solid, with all the benefits of PulseAudio. Definitely give it a shot.

+1

This was the guide that fixed it for me, no flash problems since. I'm surprised it wasn't mentioned earlier in this thread.
Firefox 3 still randomly stalls on me by itself though.

---

### Post by OZFive on 2008-06-21
I did not see that about Pulse Audio but I seem to have solved my issues by doing two things.  First gettin rid of all my Falsh crap via Synaptic and using the guide on this page here to make sure it was al gone and then reinstall it.
[http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)


The becasue I found it still a bit buggy I upgraded to Flash 10.  Instructions also from Ubuntu Unleashed...
[http://www.ubuntu-unleashed.com/2008/05/howto-install-flash-player-10-astro.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-flash-player-10-astro.html)

I have not had a crash since :D

---

### Post by mustang on 2008-06-21
It stopped happening to me after Hardy.

---

### Post by eeemart on 2008-06-21
i just can not seem to fix my problem. :(

every solution either makes it a whole lot worse, or it stays the same. i've tried so many things, i forgot what i have and have not done to my firefox! haha. maybe that's my problem now.

---

### Post by Hells_Dark on 2008-06-21
> **mustang said:**
> It stopped happening to me after Hardy.
+1

**Zero** crash.

---

### Post by Linuxratty on 2008-06-21
> **Ub1476 said:**
> Is it just me who has Flash working alright?


 Mine crashes about half the time...So mine is mostly working right.

---

### Post by Fedz on 2008-06-21
Ubuntu/8.04, FF3 and FlashPlayer10 - no problems with heavy YouTube and other various flash sites usage here :-)

---

### Post by cardinals_fan on 2008-06-21
No problems with 64-bit Opera on Arch or 32-bit Opera on Slackware.

---

### Post by geoken on 2008-06-21
> **Polygon said:**
> yes pulse audio is really shaky, but it will get better, and the benefits of pulseaudio will show themselfs in the long run. Once everything starts supporting it,

Sorry if it came off like I was slamming PulseAudio, I wasn't. I was just upset because people always try and blame the 'evil' closed source app, even in instances where the issue is obviously attributable to a larger, known issue with a piece of open source software.

---

### Post by madjr on 2008-06-21
> **geoken said:**
> Sorry if it came off like I was slamming PulseAudio, I wasn't. I was just upset because people always try and blame the 'evil' closed source app, even in instances where the issue is obviously attributable to a larger, known issue with a piece of open source software.

look at my sign

the fault is of that "**'evil' closed source**" app's **bad linux port**.

---

### Post by geoken on 2008-06-21
> **madjr said:**
> look at my sign

the fault is of that "**'evil' closed source**" app's **bad linux port**.

How can you say that considering that every single person in here who has disabled pulse audio is reporting no problems?

---

### Post by ELD on 2008-06-22
I used the guide ealier on in this thread and it has finally fixed firefox crashing more than half the time on flash content.

Also note it never happend before pulseaudio, stop blaming adobe for something that is not actually their problem.

---

### Post by dmizer on 2008-06-22
> **ELD said:**
> I used the guide ealier on in this thread and it has finally fixed firefox crashing more than half the time on flash content.

Also note it never happend before pulseaudio, stop blaming adobe for something that is not actually their problem.

it's not working well with pulse audio because the closed source flash cannot be adapted by the community to work with the pulse audio system.  And, pulse audio cannot know how to interface with flash because (again) flash is closed source.

so yes, it is the closed source app's fault.

edit:
same thing happened (for the same reasons) when linux moved from ESD to alsa.

---

### Post by steveneddy on 2008-06-22
Ubuntu 8.04 64 bit

FF3

Never any Flash issues. I watch Flash on You Tube and many other sites all the time, one after the other and I don't seem to have any issues with crashing.

---

### Post by Mateo on 2008-06-22
It's reproduceable with me.  If I don't pause a flash video before closing the tab, it usually will crash the browser. Even if I do pause the video before closing a tab it still sometimes crashes the browser.

---

### Post by doorknob60 on 2008-06-22
I don't use Pulseaudio, never had any problems :)

---

### Post by Mateo on 2008-06-22
how do i turn pulseaudio off?

---

### Post by dmizer on 2008-06-22
> **Mateo said:**
> how do i turn pulseaudio off?

the answer is posted back on page three, here: [http://ubuntuforums.org/showpost.php?p=5229644&postcount=22](http://ubuntuforums.org/showpost.php?p=5229644&postcount=22)

---

### Post by Mateo on 2008-06-22
nah, i'll just do sudo apt-get remove pulseaudio.  i don't need per-application volume control anyways.

---

### Post by dmizer on 2008-06-22
> **Mateo said:**
> nah, i'll just do sudo apt-get remove pulseaudio.  i don't need per-application volume control anyways.

you may want to reconsider that.  removing pulseaudo will probably remove the ubuntu-desktop metapackage which will prevent you from getting update notifications, and may also prevent you from getting some updates.

---

### Post by ELD on 2008-06-23
> **dmizer said:**
> it's not working well with pulse audio because the closed source flash cannot be adapted by the community to work with the pulse audio system.  And, pulse audio cannot know how to interface with flash because (again) flash is closed source.

so yes, it is the closed source app's fault.

edit:
same thing happened (for the same reasons) when linux moved from ESD to alsa.

So because a company wants to keep their source closed we should instantly blame them then should we? Not everything should be open sourced you know.

---

### Post by Barrucadu on 2008-06-23
I am now using PulseAudio and Flash works perfectly :D

---

### Post by dmizer on 2008-06-23
> **ELD said:**
> So because a company wants to keep their source closed we should instantly blame them then should we? Not everything should be open sourced you know.

i think you've misunderstood me.  i have no problem with closed source software. there are plenty of good reasons for closed software.

but when you have a piece of software that's as essential to the web experience as flash, you expect it to be as cross platform as a browser.  how are the developers of new and improved sound support suppose to work around this lack of information?

sound developers have two choices.  they can say screw flash and develop improved sound support, and make people like you unreasonably angry.  or they can halt development as a result of a single closed source browser plugin, whereby alienating the growing linux sound mixing community.

the lack of advanced sound capability in linux is one of the biggest valid complaints that linux users have.  how can there be improvement if development stands mired in alsa because adobe won't dedicate resources to supporting new and better sound capabilities in linux?

there are really only a few ways around this. open up your software to the community, devote more resources to the open source community, or release specifications for it.

---

### Post by OffHand on 2008-06-23
> **ELD said:**
> I am just wondering about the state of the bug the causes flash to crash web browsers with audio support on?

Has any work been done on it yet?

You can give flash 10 beta a try. Seems to be fixed in 10.

---

### Post by geoken on 2008-06-23
> **dmizer said:**
> 


sound developers have two choices.  they can say screw flash and develop improved sound support, and make people like you unreasonably angry.  or they can halt development as a result of a single closed source browser plugin, whereby alienating the growing linux sound mixing community.

the lack of advanced sound capability in linux is one of the biggest valid complaints that linux users have.  how can there be improvement if development stands mired in alsa because adobe won't dedicate resources to supporting new and better sound capabilities in linux?

there are really only a few ways around this. open up your software to the community, devote more resources to the open source community, or release specifications for it.

Adobe has given resources to it. Flash 10 supports it. Also, the fact that there are methods to fix it by patching pulseAudio seems to point the finger at pulseAudio. 

As for answering your question in a broader sense, the way to move forward is to maintain some sort of backward compatability. If you have to break backward compatability then you shouldn't blame individual developers provided they fix things in a timely manner. If the features are implemented in a wide scale before the afformentioned 'timely manner' then the blame falls on the party responsible for implementing those features. 

Adobe has fixed the issue in their current builds so I don't understand how they are to blame?

---

### Post by ELD on 2008-06-24
Well since using the guide posted earlier to date i have had 1 crash which i can't remember if was flash related or not, so i have gone back to using ubuntu full time instead of windows :)

---

### Post by dmizer on 2008-06-24
> **geoken said:**
> Adobe has given resources to it. Flash 10 supports it. Also, the fact that there are methods to fix it by patching pulseAudio seems to point the finger at pulseAudio. 
i'm aware of this, and actually credit where credit is due, it does appear as though adobe is making strides to correct this dreadful state of affairs with flash.  the bugs are naturally pulsaudio problems but those bugs are not the only thing that's causing incompatibility with flash.

> **geoken said:**
> As for answering your question in a broader sense, the way to move forward is to maintain some sort of backward compatability. If you have to break backward compatability then you shouldn't blame individual developers provided they fix things in a timely manner. If the features are implemented in a wide scale before the afformentioned 'timely manner' then the blame falls on the party responsible for implementing those features.
how are you suppose to provide backwards compatibility when you don't even know what was done to make alsa compatible with flash in the first place?

> **geoken said:**
> Adobe has fixed the issue in their current builds so I don't understand how they are to blame?
fixed builds are still in testing, and not considered ready to replace the current implementation.

---

### Post by ELD on 2008-06-24
> **dmizer said:**
> i'm aware of this, and actually credit where credit is due, it does appear as though adobe is making strides to correct this dreadful state of affairs with flash.  the bugs are naturally pulsaudio problems but those bugs are not the only thing that's causing incompatibility with flash.


how are you suppose to provide backwards compatibility when you don't even know what was done to make alsa compatible with flash in the first place?


fixed builds are still in testing, and not considered ready to replace the current implementation.

To be honest they should come out of testing, i am using them now, garunteed it would make more than most people happier.

---

