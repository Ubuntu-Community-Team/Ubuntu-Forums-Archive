---
title: "What I really want: Linux browsers with real multimedia plugins!"
date: 2005-12-24
forum: The Cafe
---

### Post by JimmyJazz on 2005-12-24
I think some major focus (or prodding) needs to be put into this.  Lets face it the web is more than just HTML these days.

---

### Post by quincyjones on 2006-05-09
[QUOTE=JimmyJazz]I think some major focus (or prodding) needs to be put into this.  Lets face it the web is more than just HTML these days.[/QUOTE]

Ditto that! For me its been Ubuntu's biggest downfall. :rolleyes:

---

### Post by helpme on 2006-05-09
Huh?
Could you be a little more specific?
Mplayerplug-in and in dapper even the totem-xine plugin work fine for me.

---

### Post by Reshin on 2006-05-09
How's about better support for opera? Installing plugins means doing the 'ln -s /mozilla/plugin/folder/ /opera/plugin/folder/' thingie and even then, it´s a pain in the *** to get java to play with it. In fact, I have never gotten it to work. I´m a firefox user, but that's only cuz I can´t get opera to function correctly...:mad:

---

### Post by blueturtl on 2006-05-09
> How's about better support for opera? Installing plugins means doing the 'ln -s /mozilla/plugin/folder/ /opera/plugin/folder/' thingie and even then, it´s a pain in the *** to get java to play with it. In fact, I have never gotten it to work. I´m a firefox user, but that's only cuz I can´t get opera to function correctly...

I got Java working under Opera by simply installing the Runtime Environment off of Java.com. Then I just selected Preferences from the Tools menu. Then I selected Content from the pane on the left. On the right side of the Enable Java checkbox is a button labeled 'Java options'. There I spesified the path to the JRE (I installed under /opt/java/jre/lib/i386).
The media plugins for Mozilla browsers are superior though. mplayerplug-in just rocks.

---

### Post by Reshin on 2006-05-09
[QUOTE=blueturtl]I got Java working under Opera by simply installing the Runtime Environment off of Java.com. Then I just selected Preferences from the Tools menu. Then Content from the submenu and on the right side of the Java checkbox is a button labeled 'Java options'. There I spesified the path to the JRE (I installed under /opt/java/jre/lib/i386).
[/QUOTE]
Did the same thing. Keeps yelling ´invalid path´ to my face :???:

---

### Post by blueturtl on 2006-05-09
Have you tried the obvious:

i) Check that the directory entered into Opera has all letters in the right case
ii) Select a directory that is a bit higher up the tree, like /opt/java/jre/ and let Opera search for the proper path by clicking 'Validate path'

Note that Opera wants the path to the actual JRE folder, not the plug-in folder!
Mozilla plugin folder: /opt/java/jre/plugin/i386/ns7
JRE valid path: /opt/java/jre/lib/i386

---

### Post by DigitalDuality on 2006-05-09
Follow the wiki named "RestrictedFormats" (for FF users) and you should have no problems.

Other than Flash v8 and up, i can view everything on the web just fine.

---

### Post by Bloch on 2006-05-09
> I think some major focus (or prodding) needs to be put into this. Lets face it the web is more than just HTML these days.
ditto

The mplayer is good, but still firefox does not play as great a range as e.g Safari on OS X. 
We all know the explanations about proprietory formats, but the Totem and VLC players can handle all the formats you throw at them, and are in no way deficient w.r.t. the players easily available on windows. The ability to handle embedded formats falls behind.

I can live with it, but a bit of honesty doesn't hurt and might have saved me a lot of time trying to install multimedia plugins on opera (aaaarghh!) and might save some newbie a lot of anxious twiddling when he finds firefox does not play his favourite streaming video.

Flash and java on the other hand should work perfectly on both firefox and opera and are farly easy to install.

---

### Post by helpme on 2006-05-09
[QUOTE=Bloch]ditto

The mplayer is good, but still firefox does not play as great a range as e.g Safari on OS X. 
We all know the explanations about proprietory formats, but the Totem and VLC players can handle all the formats you throw at them, and are in no way deficient w.r.t. the players easily available on windows. The ability to handle embedded formats falls behind.
[/QUOTE]
Excuse me?
Mplayer and mplayerplug-in can handle all the formats Totem and VLC can handle and then some, so I really don't know what you are talking about.

Also, could someone please post some links to sites that don't work?

---

### Post by Kimm on 2006-05-09
Have you installed w32codecs?

I'm using mplayerplug-in in Firefox and it plays anything I throw at it.

---

### Post by ice60 on 2006-05-09
hi, i use Opera and it plays everything for me. however, before i got it working i used a script to download plugin links to my desktop then stream it with a media player. to get the embedded link to appear you just double-click on the page.
[http://userjs.org/scripts/general/enhancements/download-embeds](http://userjs.org/scripts/general/enhancements/download-embeds)

---

### Post by ThirdWorld on 2006-05-09
[QUOTE=helpme]Excuse me?
Mplayer and mplayerplug-in can handle all the formats Totem and VLC can handle and then some, so I really don't know what you are talking about.

Also, could someone please post some links to sites that don't work?[/QUOTE]

they do handle them but they feel kind of lets said ...."experimental?"... you can read some code, ip adresses and other stuff before the video loads and something that said "m-plugin" crappy dude LOL. Also, i cant play .wma video stream... Its like, ok, it play stuff but it feels nerdy and cheap.. i dont know how to explain... LOL :D

---

### Post by nalmeth on 2006-05-09
nerdy and cheap.. 
:confused:
I think mozplugger is slick enough.
I never see these IP's and other addresses.
I see the mplayer-mozilla window were the video is, then I see 
Connecting to Stream
Buffering
Playing
Then I see the video
And I have controls at the bottom of the window.

What more are you asking from linux?

I don't get all the fuss about media streaming.

+90% of the time, it comes down to the person not having the right codecs, then it's like, ok, maybe it work's ok, but I want it to be better.
Great.

Also we never get the links for the sites that don't work.

I will post some though,
nhl.com's highlights work, but they take a little too long to load, and sometimes the 700k stream is a little skippy, until it catches up, and is fine...
Also, to stream the audio feeds, you have to wait a considerable amount of time before it plays (don't give up), then it plays skippy for like 5 minutes, then it is fine.

One area I agree needs to be resolved is with flash-audio.
It works if its the first media you play after rebooting, but otherwise, usually not.
Though with video.google it seems to work all the time?
A little confusing.

---

### Post by briancurtin on 2006-05-09
i made two symbolic links and everything works perfectly. im set to go, i dont know what else you want here...

---

### Post by hanzomon4 on 2006-05-09
Well I have m-plugin installed the w32 codecs I even edited my mplayerplug-in.conf file
and it works sometimes  but on [gamespot.com]("gamespot.com") it will just play the ad then stop.
At [http://www.artic.edu/webspaces/freeradio/index.html]("http://www.artic.edu/webspaces/freeradio/index.html")
it shows up distorted and never plays.
Videos at [bbc.com]("bbc.com")  skip and sound terrible.
It has taken me about 3 months and tons of searching for howtos  to get it this far.
So if any one has it working great please explain how for the rest of us.
here is my mplayerplug-in.conf if it will help.
```
#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
keep-download=1
dload-dir=$/tmp/streams
srate=48000

```
I have tried mozzplugger , VLC , mediaplayerconnectivity, totem gs/xine plugin also

---

### Post by nalmeth on 2006-05-10
I can confirm your problem with gamespot. Stops after the "annoying" ad. You can download the video to your harddrive, but this doesn't solve the streaming problem.

On another note, I must comment that these types of sites drive me crazy. What terrible use of flash for such unneccessary uses. 

I usually send emails to these websites to complain about their overuse of these stupid plug-in's that end up hurting the usability of the site.

You should send them an email saying that their video stops playing after the ad. Maybe they have a solution. They're probably using weird protocol's to pipe in the video after you watch the ad (we can tell what is more important to the site itself can't we?)

Sorry to rant, but these websites drive me insane. I don't like to put my computer through that kind of crap. I know I'm probably missing some good media because of my stance with these sites, but seriously, screw that.

End of Rant, Back to OP's issue

EDIT: Why does your config show you using the xv *and* x11 driver?

---

### Post by hanzomon4 on 2006-05-10
That line #vo=xv,x11 is just an example and it's commented out.
Also I can't just stop using these sites because I'm not the only person using the computer.

I'm find using linux to be a fun, but when my family can't get websites to stream video under linux, but can under windows, it's hard to show them the advantages of using linux. 
I think new users don't mind following the howto and wiki pages to get stuff working but they are really pissed when after jumping through hoops it (what ever it happens to be) still does not work.

Linux is great and getting better and If it can conquer multimedia (it has for the most part) more people will use it and keep using it.

---

### Post by briancurtin on 2006-05-10
[QUOTE=hanzomon4]and it works sometimes  but on [gamespot.com]("gamespot.com") it will just play the ad then stop.[/QUOTE]
that is the entire reason i didnt have flash installed for like 6 months -- half of the ads on the internet cant even START playing, let alone stop at some random time.

---

### Post by hanzomon4 on 2006-05-10
I have the flash videos working okay its just the videos that need to use the mplayer-plugin.

---

### Post by ThirdWorld on 2006-05-10
no video or audio from gamespot.com [-X 

what about a dedicated team that would take care of streaming media on linux? what about an independent 3rd party plugin? a universal plugin that can play quicktime, .wma and flash?

---

### Post by helpme on 2006-05-10
[QUOTE=ThirdWorld]no video or audio from gamespot.com [-X 
[/quote]
I just tried it and gamespot works fine for me with mplayerplug-in on dapper.

[QUOTE=ThirdWorld]
what about a dedicated team that would take care of streaming media on linux? what about an independent 3rd party plugin? a universal plugin that can play quicktime, .wma and flash?[/QUOTE]
You mean like the gstreamer guys and like the mplayer guys?
Seriously, I tried all the sites mentioned and gamespot and bbc worked for me (the bbc even worked though I don't have realplayer installed).
I couldn't try the othe site mentioned as it seems to require registration.

---

### Post by nalmeth on 2006-05-10
@ helpme:
How did you install mplayerplugin on dapper?
I used bumps multimedia script.

I have same thing happen as previous poster on gamespot. 
I'd like to know what you did differently, as there seems to be a couple ways of getting mozilla plugins. 
i.e. the flashplayer in the repos for dapper crashes firefox all the time, but I just installed the old flashplayer-mozilla breezy package, and it works great.

---

### Post by helpme on 2006-05-10
[QUOTE=nalmeth]@ helpme:
How did you install mplayerplugin on dapper?
I used bumps multimedia script.

I have same thing happen as previous poster on gamespot. 
I'd like to know what you did differently, as there seems to be a couple ways of getting mozilla plugins. 
i.e. the flashplayer in the repos for dapper crashes firefox all the time, but I just installed the old flashplayer-mozilla breezy package, and it works great.[/QUOTE]

I simply installed mozilla-mplayer from multiverse (I think it's in multiverse).
As for flash, I used flashplugin-nonfree, also from multiverse.

---

### Post by ThirdWorld on 2006-05-10
[QUOTE=helpme]I simply installed mozilla-mplayer from multiverse (I think it's in multiverse).
As for flash, I used flashplugin-nonfree, also from multiverse.[/QUOTE]


I have  both and the thing did not work... maybe is because im running breezy badger?

---

### Post by B0rsuk on 2006-05-10
For anyone who thinks 'just html' is ugly, or worse - backwards, check out this:

[http://www.csszengarden.com/](http://www.csszengarden.com/)
**Pay special attention to the panel with links, on the right side of the page.** And try out different designs, a lot.

I call flash lovers backwards. You can't do things like this with flash; flash is not nearly as flexible. It's all the same content/html file, you just use different css stylesheets.

---

### Post by hesee on 2006-05-10
[QUOTE=helpme]Also, could someone please post some links to sites that don't work?[/QUOTE]

Here is one, finnish website about icehockey world championship. 
[http://www.yle.fi/urheilu/mm2006/index.html#](http://www.yle.fi/urheilu/mm2006/index.html#)

Click a blue box on the right where is words "Katsele videoita" (=watch videos). And in the mini-site click some links. I couldn't get it working, mplayer itself can show the video, though. But the embedded video play stops before it actually starts. Videos are .wmv so w32codecs are needed. If someone can watch these, would be nice to know your config.

---

### Post by helpme on 2006-05-10
[QUOTE=hesee]Here is one, finnish website about icehockey world championship. 
[http://www.yle.fi/urheilu/mm2006/index.html#](http://www.yle.fi/urheilu/mm2006/index.html#)

Click a blue box on the right where is words "Katsele videoita" (=watch videos). And in the mini-site click some links. I couldn't get it working, mplayer itself can show the video, though. But the embedded video play stops before it actually starts. Videos are .wmv so w32codecs are needed. If someone can watch these, would be nice to know your config.[/QUOTE]
Doesn't work for me with mplayer either.
Using the totem-xine-firefox-plugin from dapper works though.
Weird.

---

### Post by hesee on 2006-05-10
[QUOTE=helpme]Doesn't work for me with mplayer either.
Using the totem-xine-firefox-plugin from dapper works though.
Weird.[/QUOTE]

Hey, nice to know it works at least for dapper. I'm upgrading after 1st june. :cool:

---

### Post by endersshadow on 2006-05-10
The only problem that I have with mplayer-plugin is that it doesn't differentiate between an embedded video and a video file.  Oh, and it doesn't have a "repeat" feature.  This is killer when trying to watch pr0n.

The question you have to ask is whether or not I'm serious :-D

---

### Post by hanzomon4 on 2006-05-10
[QUOTE=ThirdWorld]I have  both and the thing did not work... maybe is because im running breezy badger?[/QUOTE]

I use Dapper and it doesn't work for me

---

### Post by hanzomon4 on 2006-05-10
[QUOTE=helpme]I just tried it and gamespot works fine for me with mplayerplug-in on dapper.

You mean like the gstreamer guys and like the mplayer guys?
Seriously, I tried all the sites mentioned and gamespot and bbc worked for me (the bbc even worked though I don't have realplayer installed).
I couldn't try the othe site mentioned as it seems to require registration.[/QUOTE]

Could you post your mplayerplug-in.conf file. Could you also tell us how you installed the mplayerplug-in, what version, and all that good stuff.
Because I have been to the moon and back trying to get this to work and many sites just do not work.
Try this [link]("http://www.fnewsmagazine.com/2006-may/") it buffers to 99% and then nothing plays

---

### Post by nalmeth on 2006-05-10
The F Newsmagazine link is a .mov file:
**[http://clips1.vimeo.com/video_files/2006/04/05/vimeo.81590.fb198d.mov](http://clips1.vimeo.com/video_files/2006/04/05/vimeo.81590.fb198d.mov)**

I don't see why mplayer couldn't play this.

I know it doesn't solve the mplayer problem, but you should try the Video Download extension in firefox so you can easily download the video's that don't play properly.

It's quite good.

---

