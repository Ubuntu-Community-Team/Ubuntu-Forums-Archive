---
title: "Silverlight"
date: 2010-04-03
forum: The Cafe
---

### Post by Frogs Hair on 2010-04-03
Hi,
I decided to listen to my local rock station on ubuntu only to find out they require silverlight in order to listen . Silverlight is compatible with Firefox , but I don't want to download a 42mb program to listen to radio. I hope this isn't a trend.

---

### Post by Ioky on 2010-04-04
Totally Funny.... Need a Close Source software in order to listen to some show about Open Source....

Maybe that is really funny. A lot of Online Ratio station actually only use things like mms:/ for their streaming. And I haven't find a good way to get mms:/ working under Linux. I really needed, but I just don't know how to get it to work... 

You are not the only one...

---

### Post by quinnten83 on 2010-04-04
you can't find the streamaddress and open it in your regular musicplayer?

---

### Post by juancarlospaco on 2010-04-04
html5

---

### Post by phibxr on 2010-04-04
> **Ioky said:**
> Totally Funny.... Need a Close Source software in order to listen to some show about Open Source....

Maybe that is really funny. A lot of Online Ratio station actually only use things like mms:/ for their streaming. And I haven't find a good way to get mms:/ working under Linux. I really needed, but I just don't know how to get it to work... 

You are not the only one...

Try opening those networked URLs in VLC media player.

```
$ sudo apt-get install vlc
```

---

### Post by Dayofswords on 2010-04-04
> **Ioky said:**
> Totally Funny.... Need a Close Source software in order to listen to some show about Open Source....

Maybe that is really funny. A lot of Online Ratio station actually only use things like mms:/ for their streaming. And I haven't find a good way to get mms:/ working under Linux. I really needed, but I just don't know how to get it to work... 

You are not the only one...

he just said rock station =p

tell me the station, i want to see if i can get the stream

---

### Post by Frogs Hair on 2010-04-04
[www.wapl.com](www.wapl.com)

---

### Post by zekopeko on 2010-04-04
> **Frogs Hair said:**
> Hi,
I decided to listen to my local rock station on ubuntu only to find out they require silverlight in order to listen . Silverlight is compatible with Firefox , but I don't want to download a 42mb program to listen to radio. I hope this isn't a trend.

Here try this: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

It's 3.6mb of FOSS goodness for the 32bit version.

EDIT: On the other hand when I click on the Listen Live link it uses Flash to stream.

---

### Post by MasterNetra on 2010-04-04
mplayer is in Ubuntu's repos by default just download it and install the firefox plugin afterwards install moonlight and its mozilla plugin. The version in repo will get the player to appear at least. (You may need the getdeb app repo for the mozilla plugin)

Update: Lucid seems to have moonlight 2.2 in its repo, gonna try to get it to work on there.

---

### Post by zekopeko on 2010-04-04
> **MasterNetra said:**
> mplayer is installed in Ubuntu by default just download and install the firefox plugin afterwards install moonlight and its mozilla plugin. The version in repo will get the player to appear at least.

Mplayer isn't installed by default. And I don't know why you actually need Silverlight to stream on that site since their player uses Flash for streaming.

---

### Post by MasterNetra on 2010-04-04
> **zekopeko said:**
> Mplayer isn't installed by default. And I don't know why you actually need Silverlight to stream on that site since their player uses Flash for streaming.

yea noticed that with lucid my bad. Corrected the post. And they must be using some combination of silverlight and flash.

Update: Got it playing on Lucid with VLC + plugin, restricted extras, and moonlight 2.2.
Downside is no controls. but the music plays.

**2nd Update:** ***Got it working for karmic!*** You can have the mplayer and its mozilla plugin installed if you want but vlc + its mozilla plugin does the job too. Additionally go to [http://www.go-mono.com/moonlight/download.aspx](http://www.go-mono.com/moonlight/download.aspx) to install moonlight 2.2. Besure to remove the moonlight 1.x from repo or they will most likely conflict and cause firefox to crash! Also make sure you have flash (can get it from the repo of course). With all that you will be asked to download and install some moonlight codecs when you go to the player, do so and refresh the player's page and you should be good to go.

I've experienced some audio hiccups but that's most likely from buffering.

---

### Post by MasterNetra on 2010-04-04
Also on lucid after removing moonlight 2.2 that's in it's repo and installed the one from [http://www.go-mono.com/moonlight/download.aspx](http://www.go-mono.com/moonlight/download.aspx) the player worked just as well as it does in karmic...less audio hiccups actually. Lesson learned: stay away from the moonlight thats in ubuntu's repo.

---

### Post by Frogs Hair on 2010-04-04
> **zekopeko said:**
> Here try this: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

It's 3.6mb of FOSS goodness for the 32bit version.

EDIT: On the other hand when I click on the Listen Live link it uses Flash to stream.

Tried moonlight 64 for 9.10 X86 64 and it is currently  not compatible . Thanks Anyway Here are my current plug-ins

---

### Post by zekopeko on 2010-04-04
> **Frogs Hair said:**
> Tried moonlight 64 for 9.10 X86 64 and it is currently  not compatible . Thanks Anyway Here are my current plug-ins

Hmmm.... I still don't understand why you need Moonlight. 

[http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WAPLFM](http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WAPLFM)

If you click the above link it opens another window with a Flash player that plays music from the station.

---

### Post by Uncle Spellbinder on 2010-04-04
To be honest, I've yet to navigate to a page that requires Silverlight. :-k

---

### Post by phrostbyte on 2010-04-04
> **zekopeko said:**
> Here try this: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

It's 3.6mb of FOSS goodness for the 32bit version.

EDIT: On the other hand when I click on the Listen Live link it uses Flash to stream.

It seems to 'use' Silverlight, but doesn't 'use it' for much more then to check you have it installed. :lolflag:

EDIT: It actually *is* using Silverlight for the ad spammer thing. It also uses a ton of JavaScript. What a mess of a web app. :p

---

### Post by praveenthivari on 2010-04-04
> **zekopeko said:**
> Here try this: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

It's 3.6mb of FOSS goodness for the 32bit version.

EDIT: On the other hand when I click on the Listen Live link it uses Flash to stream.

As said in this tru moon-light

---

### Post by Frogs Hair on 2010-04-04
> **zekopeko said:**
> Hmmm.... I still don't understand why you need Moonlight. 

[http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WAPLFM](http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WAPLFM)

If you click the above link it opens another window with a Flash player that plays music from the station.

I got it ! Last night It could not find a compatible plug in when it offered to search for one.
I tried again and it found g streamer and it now it works . The link in the red print is for a paid service. Thanks

---

### Post by MasterNetra on 2010-04-05
> **zekopeko said:**
> Hmmm.... I still don't understand why you need Moonlight. 

[http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WAPLFM](http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WAPLFM)

If you click the above link it opens another window with a Flash player that plays music from the station.

It wouldn't load for me without moonlight at least not from the link wapl provides. but meh.

---

### Post by Frogs Hair on 2010-04-05
> **MasterNetra said:**
> It wouldn't load for me without moonlight at least not from the link wapl provides. but meh.

Thanks G Streamer works fine.

---

### Post by birkopf on 2011-08-23
This is off-topic, but it might help. I use (I mean I'm addicted to)  radiotray. It's in official repos. You can use latest version via PPA and add your radio station. It's very lightweight and probably will go around silverlight problem nicely...

---

### Post by Frogs Hair on 2011-08-23
> **birkopf said:**
> This is off-topic, but it might help. I use (I mean I'm addicted to)  radiotray. It's in official repos. You can use latest version via PPA and add your radio station. It's very lightweight and probably will go around silverlight problem nicely...

This was solved with a Gstreamer plug-in and the radio station in question now uses a flash based application . Thank you anyway .

---

