---
title: "Democracy Player"
date: 2006-09-11
forum: The Cafe
---

### Post by maniacmusician on 2006-09-11
There hasn't really been a thread on this in a while. A new version just came out. How do you guys feel about it. I'm trying it out right now.

It's browser seems to be kind of slow. And i heard the new version supported google video search but i dont see that. I guess i'll find it in a few mins. Just wanted to put this up in case other people didn't know about it...

uh duh, i should explain it.

Democracy Player is a GTK based video player...basically it subscribes to feeds of sites that host video of all kind. It promotes itself as a kind of "internet TV" player that can play channels for free, and it seems to be a protest against big corporations controlling the majority of media. It looks to be fairly decent. I believe you can download the new version at [www.getdemocracy.com](www.getdemocracy.com)

---

### Post by nalmeth on 2006-09-11
It looks promising, but I concur about the sluggishness. I haven't tried 0.9 yet, however.

---

### Post by maniacmusician on 2006-09-11
> **nalmeth said:**
> It looks promising, but I concur about the sluggishness. I haven't tried 0.9 yet, however.
it's definitely faster than before. or seems so to me.

---

### Post by detgar on 2006-09-11
I tried - and failed - to install it some time ago. Seems like an interesting project, though.

---

### Post by maniacmusician on 2006-09-11
why did you fail to install it?

it's pretty much as simple as going to their site and downloading the .debs.



i had a slight problem with dependencies...mozilla-dev wouldn't install because it had an overlapping directory with nvu-dev. so i just removed nvu-dev and everything was happy.

what was the problem you encountered?

edit: mine suddenly stopped giving me sound. it was working, i went to the bathroom, came back, and it wasnt. odd. if anyone finds a solution let me know. i'm gonna go try stuff.

edit again: it seems that it doesn't properly implement sound from youtube videos. del.icio.us works fine. have yet to try google vid and the others.

edit: sound doesn't work on google video downloads either. i'm a little miffed now. can someone else try it and see if it's global or just me? because like i said del.icio.us worked for me...

---

### Post by detgar on 2006-09-11
This happened some months ago. I downloaded the Ubuntu .debs from the site, then doubleclicked the data deb, then the player deb, and got some error (which I can't remember). Since I wasn't all that anxious to run the app, I just gave up.

I'm running it right now though. No problems with the 0.9 version. And yes, really cool stuff.

Although, what settings does it use when downloading via bittorrent? I have a NAT router with port 5**** being my torrent port, and if DP just tries the 6881-whatever standard ports, it won't run very well. Yet I can't find anything about this in the settings.

---

### Post by maniacmusician on 2006-09-11
...it downloads via bittorrent?


are flash video files working for you? (aka the ones from google and youtube?) are you getting sound with those?

edit: i get low speeds using bittorrent too. and i dont think there's any settings for that

---

### Post by mushroom on 2006-09-11
please...please no more media players...*gasp*...*wheeze*...no mo-- *faints*

---

### Post by maniacmusician on 2006-09-11
hahaha its not really a conventional media player, obviously...it's in-ter-net oriented. those damn flv files won't play sound though.

---

### Post by detgar on 2006-09-11
> **maniacmusician said:**
> ...it downloads via bittorrent?


are flash video files working for you? (aka the ones from google and youtube?) are you getting sound with those?

I haven't tried that yet.

---

### Post by detgar on 2006-09-11
> **maniacmusician said:**
> ...it downloads via bittorrent?
edit: i get low speeds using bittorrent too. and i dont think there's any settings for that

Make sure You've got the incoming ports open. Your bittorrent client is running a server, so remote hosts will need to contact your machine.
That's why it would be nice to be able to change the port settings, so I can have my own preferred ports accepting connections (which would lead to higher speeds).

The standard bittorrent ports are 6881 to 6999, I think. Judging by the lack of options, I'd say DP uses these to accept connections on. But I might as well be entirely wrong.

---

### Post by maniacmusician on 2006-09-11
i don't know which ports are the incoming ones...i have it all set up on azureus, where i use an open port. how do i know which one democracy is using?


ps. could you please try a flash video file either from youtube or google? thanks.

---

### Post by detgar on 2006-09-11
The program just froze while trying to watch flash from google. DP seems to be buggy, I haven't been able to properly download and watch any of three files (1 flash 2 others). 

Anyways, I'm going to bed now, tomorrow I should be able to read docs and stuff, I'll give DP a proper run then.

---

### Post by maniacmusician on 2006-09-11
ok. thanks for trying. 

mine doesnt freeze, just doesnt give me sound. others seemed to work fine.

---

### Post by evolvedlight on 2006-09-12
Hey. I've been using Democracy player for a while now, and love it

First Point. IT IS NOT A MEDIA PLAYER.
The core of democracy player is that you can import RSS feeds of videos, or even RSS's of torrents, and download them from a nice window.

Second Point. It was very buggy, but not so bad now.

But its much quicker than searching for the videos, then downloading them from yahoo etc. The flv video files do not play well in DP, but you can open the downloaded files in MPlayer and they are all good

S

---

### Post by maniacmusician on 2006-09-12
no, i tried playing them in mplayer, but still no sound. and occasionally, it will crash on a video when it is done playing a certain percentage of the video (I would guess at about 95%). this has happened several times. it is still a pretty great project though...just has some bugs to work out.

---

### Post by banjobacon on 2006-09-12
I'm trying it for the first time. The interface seems extremely slow. Is it real GTK, or is it XUL?

Also, why does it require the Mozilla suite instead of Firefox?

---

### Post by odzx on 2006-12-25
i've been having problems with sluggishness of democracy player as well. and for some reason i cant get torrents to download at all.
does anyone know how to make those torrents download, or alternatively suggest a different app that can download a torrent and play it too?

---

### Post by rudlavibizon on 2007-01-14
It looks promising but it's really buggy. I tried changing bittorrent ports but they just stay the same (8500 to 8600 i think). This was until i found out that if i change them by clicking on the arrows instead of typing they remain changed. How stupid is that???...Also some podcasts download but wont play. ](*,)

---

### Post by blackened on 2007-01-14
I used DP for a little bit, and the downloading features worked fine (though the browser was sometimes excruciatingly slow), but I never could get the "Player" portion to work. It would never play anything I downloaded through it, and I was forced to use a separate program to do that. On the bright side, I did find The Show with Ze Frank because of DP.

---

### Post by zugu on 2007-01-15
When I heard about this 'internet tv' thing, I thought that Democracy Player is actually indexing tv stations all over the world that happen to also broadcast over the internet. You have to admit it's misleading. I'd hardly call user video on youtube as internet tv.

As a player, democracy player never impressed me. The interface is cheesy and shiny and glossy. It distracts me.

By comparison, this is the same as with Ubuntu: since switching to it, I have more time to concentrate on my tasks, and less to worry about the operating system (the exact opposite happens when I use KDE or Windows). VLC for the win (yeah, I know it doesn't do internet videos, however, if I want such content I prefer to go directly to youtube/metacafe/etc).

---

