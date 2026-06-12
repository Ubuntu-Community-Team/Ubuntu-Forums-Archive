---
title: "When is Banshee 1.4 supposed to come out?"
date: 2008-09-19
forum: The Cafe
---

### Post by heddleston on 2008-09-19
i looked at their slides from GUADEC 2008 and it said that 1.4 would be coming in Sept. Im really geeked about the release b/c it'll have Gnome Do support. Any ideas?

---

### Post by treris on 2008-09-29
> **heddleston said:**
> i looked at their slides from GUADEC 2008 and it said that 1.4 would be coming in Sept. Im really geeked about the release b/c it'll have Gnome Do support. Any ideas?

AFAIK it was supposed to come out in September, but it being September 30th by now it might not happen. I have no doubt though that de dev's are working on getting it out the door.

In the meantime I'm using the unstable banshee from the banshee unstable ppa, which works very well for me. 

I don't use Gnome DO and couldn't tell you whether the unstable version (Banshee 1.3.1) supports it.

---

### Post by treris on 2008-10-10
Apparently Banshee 1.4 is only due out in November, they have now even put a calender online showing the various dates.

A bit more patience then, ah well, patience is a virtue I suppose...

btw kudos for the banshee team for all their hard work, I'm sure the 1.4 release is gonna be awesome, even more so than 1.2!

Edit: forgot to insert the link to the banshee development calender
[http://banshee-project.org/about/calendar/](http://banshee-project.org/about/calendar/)

---

### Post by heddleston on 2008-10-12
thanks for the updates!

---

### Post by mrgnash on 2008-10-12
I can't wait :) For some reason, Banshee 1.2.1 has become very unstable for me since upgrading to Ibex.

---

### Post by czescik on 2008-10-13
does anyone know why banshee doesnt refresh media colection. It still shosw mp3 wich are deleted from disk

---

### Post by treris on 2008-10-16
> **czescik said:**
> does anyone know why banshee doesnt refresh media colection. It still shosw mp3 wich are deleted from disk

AFAIK banshee does not automatically refresh the media collection (unfortunately) but you can update your media collection through 'Extra' -> 'Rescan Media Library'.
Just make sure you have the correct folder set up in your preferences otherwise Banshee will start to scan your entire /home.

The good thing about not making Banshee automatically update your media collection is of course that this way Banshee will not have to check your entire media library everytime it starts. That should save a lot of time when starting Banshee, I guess...

PS for the life of me I can't remember whether the rescan media library option is available in the current stable release, if it's not, then either update to the unstable release or wait about a month until 1.4 comes out

---

### Post by treris on 2008-10-16
> **mrgnash said:**
> I can't wait :) For some reason, Banshee 1.2.1 has become very unstable for me since upgrading to Ibex.

Have you tried updating to the unstable version? Currently Banshee 1.3.2 is available through the unstable ppa.

Have a look here:
[https://launchpad.net/~banshee-unstable-team/+archive](https://launchpad.net/~banshee-unstable-team/+archive)

To get everything working you'll have to add both the stable ppa and the unstable ppa to your repositories list, for ibex that'll be:

deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

and 

deb [http://ppa.launchpad.net/banshee-unstable-team/ubuntu](http://ppa.launchpad.net/banshee-unstable-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-unstable-team/ubuntu](http://ppa.launchpad.net/banshee-unstable-team/ubuntu) intrepid main

---

### Post by tr4nce on 2008-11-02
Treris, Banshee 1.3.3 from the Hyperair's PPA is very unstable. You can't even enter into the "preferences" dialog without a seg fault... Have you got the same problem?

I mean, I know what unstable is, but not being able to switch songs it's kinda a setback from the current stable release! Are they rewriting the code or it's just a fault of Intrepid Ibex .deb?

---

### Post by treris on 2008-11-02
Hi Tr4nce,

Yes I did have the same problem with the 1.3.3 package from the ppa, so badly that I had to downgrade to 1.3.2 to 'fix' it. But it now seems to be fixed with the 1.3.3-2 package that came out earlier today. 

Try upgrading to that version and see if your problems are solved. If not try downgrading to the 1.3.2 package that worked previously. Easiest way to do that is to uninstall the current banshee package and then install the 1.3.2 package still available here:
[https://launchpad.net/%7Ebanshee-unstable-team/+archive/+files/banshee_1.3.2-0+hardy2_i386.deb](https://launchpad.net/%7Ebanshee-unstable-team/+archive/+files/banshee_1.3.2-0+hardy2_i386.deb)

Apparently there was a flaw in the previous 1.3.3 package and according to the changes file that was fixed now. Here's the information I found:
[http://launchpadlibrarian.net/19196945/banshee_1.3.3-1~intrepid1_1.3.3-2~intrepid1.diff.gz](http://launchpadlibrarian.net/19196945/banshee_1.3.3-1~intrepid1_1.3.3-2~intrepid1.diff.gz)

Hope the new update solves your problems!

---

### Post by tr4nce on 2008-11-03
Thank! I'll try it tonight... 

I got a question... I am lost currently lost with the roadmap of changes from stable to unstable (haven't read the latest changelog my bet :)), do you know  if it's now possible to import coverart from embedded tag instead of the currently "download from amazon.com" system?

---

### Post by treris on 2008-11-03
I must admit I'm not entirely sure what you mean, but I can tell you that if you want to ensure that a particular piece of albumart is used for a particular song you can place that image into the song's directory using a filename like "folder.jpg".

So far that has always worked for me. I have not been able to select a piece of albumart from within banshee itself.

I hope that answers your question. If not, could you explain to me one more time what you mean exactly?

---

### Post by bash on 2008-11-03
Anyone know what will be new/changed/fixed between 1.2 and 1.4?

---

### Post by treris on 2008-11-03
Don't know exactly what the changes will be, but here's a list of things that changed between the 1.2 series and the 1.3 series. The 1.3 series are the development series for the 1.4 series so they should be some kind of indication

[http://download.banshee-project.org/banshee/banshee-1-1.3.0.news](http://download.banshee-project.org/banshee/banshee-1-1.3.0.news)

These are the notes related to the current 1.3.3 (unstable) release:

[http://download.banshee-project.org/banshee/banshee-1-1.3.3.news](http://download.banshee-project.org/banshee/banshee-1-1.3.3.news)

And I suppose we'll know more in a week when 1.4.0 is supposed to be released.

For me personally the most significant change has been that banshee now remembers the sorting of my playlists so I don't have to re-sort my playlists everytime I start banshee. But that of course is very personal.

---

### Post by tr4nce on 2008-11-03
Yeah! Banshee 1.3.3 working OK here! No more bugs in the released version by hyperair at Launchpad's PPAs

First impression: Solid as rock but more memory eater than the 1.2.1 stable branch release. Confirmed the import of cover art from the albums from id3tags!

Thanks for the advise treris! More comments soon! :guitar:

---

### Post by szale9001 on 2008-11-03
Can i ask how you got it working?? Everytime I try and install it I get "broken package" because the version of libmono-zeroconf in the repo is 0.7.6 and banshee requires 0.8.0. Where can i find a newer libmono-zeroconf??

PS - I have intrepid (upgraded install)

---

### Post by ScottyDelicious on 2008-11-04
> **szale9001 said:**
> Can i ask how you got it working?? Everytime I try and install it I get "broken package" because the version of libmono-zeroconf in the repo is 0.7.6 and banshee requires 0.8.0. Where can i find a newer libmono-zeroconf??

PS - I have intrepid (upgraded install)

You can grab an Intrepid deb here:
[https://launchpad.net/%7Ebanshee-team/+archive/+files/libmono-zeroconf1.0-cil_0.8.0-1~intrepid1_all.deb](https://launchpad.net/%7Ebanshee-team/+archive/+files/libmono-zeroconf1.0-cil_0.8.0-1~intrepid1_all.deb)

install that, then, if you have the banshee-project PPA's in your software sources, you can upgrade to 1.3.3 from the Ubuntu Update Manager.

---

### Post by szale9001 on 2008-11-05
Thanks a lot. One more question, is it just my comp, or are we still not able to manually reorder playlists?? I tried dragging and dropping songs, and nothing. Is this feature not built in yet, or is their something wrong with my comp??

---

### Post by ad_267 on 2008-11-05
I hope they're working on speed and stability. Rhythmbox is so much faster, I can't use Banshee because it's annoyingly slow.

Another minor annoying thing is that if I select an artist in the browser and type, nothing happens. In Rhythmbox it will go to the artist name I type.

I'll keep an eye on Banshee, but stick with Rhythmbox for now.

---

### Post by treris on 2008-11-06
> I hope they're working on speed and stability. Rhythmbox is so much faster, I can't use Banshee because it's annoyingly slow.

Another minor annoying thing is that if I select an artist in the browser and type, nothing happens. In Rhythmbox it will go to the artist name I type.

For me it's just the other way around, I found rhythmbox to be very slow and not very stable (not as bad as exaile though!). What do you mean that when you type in a name nothing happens. If I'm in the media library and I type a name in the search box in the top right of the screen I immediately go to that artist or track title or anything that resembles that which I typed.

> I tried dragging and dropping songs, and nothing. Is this feature not built in yet, or is their something wrong with my comp??

I rarely use playlists, I justs have everything sitting in the media library, but I suppose that playlists adhere to the sorting you've set up for them, for instance my media library is sorted according to file location and indeed I'm not able to manually move tracks.
I am, however, able to manually reorder the tracks in the 'play queue', but I'm not sure if that's what you're looking for.

---

### Post by ad_267 on 2008-11-06
I mean if I enable the browser, so I have a list of Artists and a List of Albums, I can't search only in that list. With most Gnome application, eg Nautilus and Rhythmbox I'd expect to be able to click in a list to focus and begin typing to go to the next item that begins with that letter. I'm just being picky with that though!

I guess I'll have to try the new version and see if it's faster on my computer. I'm only using 1.2.1 from the repositories.

---

### Post by Zeedok on 2008-11-09
The banshee website says that version 1.4 was released on the [7th November]("http://banshee-project.org/download/#ubuntu") and that it can be installed from the universe repository, but as far as I can tell, the repo has not been updated (I have 1.2.1 installed).

Does anyone know when the repo will have the 1.4 version (I'm hoping it will resolve some iPod issues I have had with the current version)?

---

### Post by fluteflute on 2008-11-09
Intrepid will probably never have 1.4 (except perhaps in backports). Whilst 1.4 has been released it hasn't yet been fully announced (i.e. on the homepage).

It should find its way into the Banshee PPA:
[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

BTW changelog says:
> - Playlists and video not synced to iPod shuffle devices
- Improved performance for adding/removing songs from iPods


---

### Post by phenest on 2008-11-09
I tried installing 1.4 but, although it ./configure ok, it will not make. So I tried 1.3.2 and that installed but, now I get an error
> Problem with Player Engine

Player engine Banshee.MediaEngine.NullPlayerEngine is in the NotReady State

Even if I reinstall 1.2.1, I get the same error.

Can someone help me either fix 1.2.1 or either of the development versions?

---

### Post by treris on 2008-11-09
> Can someone help me either fix 1.2.1 or either of the development versions? 

What I would probably do is uninstall everything from banshee, then add the ppa's to your repository sources and install from there. Including the unstable ppa's should get you 1.3.3 and I suppose that when 1.4.0 is officially announced by the banshee team it'll also show up in the stable ppa's quite soon afterwards. 1.2 and 1.2.1 did anyway.

I must admit that I'm probably a very lazy linux user in that I almost never, if at all, compile anything at all, I just wait until it enters the repo's or I can get a deb from somewhere....

---

### Post by wildman4god on 2008-11-09
I have a question about a bug, I currently have version 1.2 installed and when I go into my video library and click on a video, it goes to now playing with sound but no video, i have to leave now playing and come back and then I have video, did they fix that bug in 1.4?

---

### Post by tbroderick on 2008-11-09
> **wildman4god said:**
> I have a question about a bug, I currently have version 1.2 installed and when I go into my video library and click on a video, it goes to now playing with sound but no video, i have to leave now playing and come back and then I have video, did they fix that bug in 1.4?

Did you file a bug report?

---

### Post by wildman4god on 2008-11-09
No I don't always have unrestricted internet (I attend Job Corps and our internet filter policy is very wierd, don't ask) I just assumed everyone was having the same bug so they would file one.

---

### Post by FuturePilot on 2008-11-10
Fresh out of the build queues. :D
[https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive")

---

### Post by perfectska04@hotmail.com on 2008-11-10
> **FuturePilot said:**
> Fresh out of the build queues. :D
[https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive")

Awesome. Anyone know the complete changelog? The Banshee homepage hasn't been updated yet, even though the release's been out for a while.

---

### Post by treris on 2008-11-10
I've been kinda waiting on a full changelog as well, I've noticed some changes obviously, but I'm sure I've missed most of them.

Weird that the website seems not to be updated for a while now, just some links to download 1.4.0, but that's it.

---

### Post by FuturePilot on 2008-11-10
> **treris said:**
> I've been kinda waiting on a full changelog as well, I've noticed some changes obviously, but I'm sure I've missed most of them.

Weird that the website seems not to be updated for a while now, just some links to download 1.4.0, but that's it.

Yeah, I've been wondering about the Banshee site. It still says 1.2. Odd. :?

---

### Post by Changturkey on 2008-11-11
[http://banshee-project.org/download/](http://banshee-project.org/download/)

On Distrowatch it says that 1.4.1 is already out.

---

### Post by BOBSONATOR on 2008-11-11
the .deb from ppa is telling me that libmono-zeroconf-1.0-cil is not met, and its clearly installed in my synaptic

EDIT: wow, i feel stupid
> **ScottyDelicious said:**
> You can grab an Intrepid deb here:
[https://launchpad.net/%7Ebanshee-team/+archive/+files/libmono-zeroconf1.0-cil_0.8.0-1~intrepid1_all.deb](https://launchpad.net/%7Ebanshee-team/+archive/+files/libmono-zeroconf1.0-cil_0.8.0-1~intrepid1_all.deb)

install that, then, if you have the banshee-project PPA's in your software sources, you can upgrade to 1.3.3 from the Ubuntu Update Manager.

Thanks!

---

### Post by ACMiller on 2008-11-11
Has anyone had any luck installing Banshee 1.4 in Hardy from the PPA? I just get this: 
> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main banshee 1.2.1-3~hardy4
  404 Not Found
Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/pool/main/b/banshee/banshee_1.2.1-3~hardy4_i386.deb](http://ppa.launchpad.net/banshee-team/ubuntu/pool/main/b/banshee/banshee_1.2.1-3~hardy4_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Seems strange that it's trying to install banshee_1.2.1-3~hardy4_i386.deb and not 1.4

Any help would be great
Thanks

---

### Post by FuturePilot on 2008-11-11
> **ACMiller said:**
> Has anyone had any luck installing Banshee 1.4 in Hardy from the PPA? I just get this: 

Seems strange that it's trying to install banshee_1.2.1-3~hardy4_i386.deb and not 1.4

Any help would be great
Thanks

Under System>Administration>Software Sources, under the Third Party Software tab, find the Banshee repo and click Edit. Make sure it says "intrepid" and not "hardy" Then click Close and then Reload.

---

### Post by ACMiller on 2008-11-11
Thanks for the quick reply!
Unfortunately I'm on hardy, and changing the repo to the intrepid one means I have unmet dependancies (libmono-zeroconf-1.0-cil, which in turn requires libmono-system2.0-cil...). Is there a problem with the hardy repo (or is it not updated yet?)

---

### Post by FuturePilot on 2008-11-11
> **ACMiller said:**
> Thanks for the quick reply!
Unfortunately I'm on hardy, and changing the repo to the intrepid one means I have unmet dependancies (libmono-zeroconf-1.0-cil, which in turn requires libmono-system2.0-cil...). Is there a problem with the hardy repo (or is it not updated yet?)

Oh I'm sorry, I kind of misread your post and I thought you were on Intrepid. You can change it back to hardy.

---

### Post by ACMiller on 2008-11-11
No worries, thanks anyway!

---

### Post by Technoviking on 2008-11-13
The PPA is working for me, and I'm loving Banshee 1.4.
:guitar:

---

### Post by ounas on 2008-11-14
> **FuturePilot said:**
> Fresh out of the build queues. :D
[https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive")

What more can I say but a big Thanks

:guitar:

---

### Post by heddleston on 2008-11-17
so i got 1.4, but now theres a problem. anytime i plug in my mp3 player, banshee immediately crashes. any ideas on what to do there?

---

### Post by treris on 2008-11-17
> **heddleston said:**
> so i got 1.4, but now theres a problem. anytime i plug in my mp3 player, banshee immediately crashes. any ideas on what to do there?

Two things come to mind when I read your message.
First off I'm wondering whether banshee is your default application for handling mediaplayers? You can look this up through the nautilus preferences. Does Banshee stop crashing when you change this to for instance 'Ask everytime'?
Secondly I've had banshee crash on me once after installation when there were no songs yet in banshee's media library, could you import some files there and see if the bug persists?

Both of these are of course workarounds, but if it takes care of business than you probably won't mind.

---

### Post by heddleston on 2008-12-03
neither workaround did anything. anyone else having this problem?

---

