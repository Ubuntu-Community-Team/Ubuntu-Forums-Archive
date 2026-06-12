---
title: "Fully fledged media player"
date: 2007-12-15
forum: Ubuntu Brainstorm
---

### Post by davbren on 2007-12-15
Hey I was pondering the other day why there is no fully fledged media player for linux. There are some very good music players and some very good video players but there really isn't anything that comes close to software like wmp... or winamp... or even itunes. Songbird tries but it hasn't quite got there.

any ideas?

---

### Post by scxtt on 2007-12-15
what do you think is missing (from any or all of them)?

---

### Post by davbren on 2007-12-15
Well if im not mistaken (which I probably am lol) with say rhythmbox, there is no video support. That would be great if there was. I'm not sure I see the point in having rhythmbox *and* totem for instance. why not have both, together, and fully integrated in a nice gui...

---

### Post by adityakavoor on 2007-12-15
banshee and exaile are itunes alternatives ..
for video U can consider vlc player

---

### Post by davbren on 2007-12-15
Yh i know of these. I'm a big fan of VLC too I use it alot, but still i would rather a media player that played more than one medium...

---

### Post by ronacc on 2007-12-15
I use banshee for audio and VLC for video and I do not feel at all deprived ,

---

### Post by davbren on 2007-12-15
hmmm, maybe im just odd then lol. I just feel that the media players are unfinished if they don't incorporate video...

---

### Post by ronacc on 2007-12-15
I don't think you are odd at all . Many people prefer "one size fits all " apps , others of us prefer one app for one job, ubutnu is a "big tent".

---

### Post by cardinals_fan on 2007-12-15
VLC has played everything I've thrown at it - not just video.

---

### Post by SunnyRabbiera on 2007-12-15
eh the options are kid of small here, but totem does a good job as it handles both video and audio, but nothing much like WMP in the terms you mean

---

### Post by DM was on fire! on 2007-12-15
Weeelll...if you're lucky enough with the install, you can use Windows Media Player with Wine. I was able to install it, but it unfortunately won't load. :(
Otherwise, TOtem with the w32codecs installed.

---

### Post by scxtt on 2007-12-15
totem plays all of my media (mostly audio right now - ogg/mp3/wma) and i've played DVD's w/ it in the past ...

also, VLC is a GREAT media player, i can even make it look like WMP ...

i don't really see a strong argument here.

---

### Post by tiachopvutru on 2007-12-15
No, I refused VLC unless it can play softsub properly. Mplayer player and its frontend SMPlayer work fine for me. Granted I had to add into ~/.mplayer/config

ass="yes"
embeddedfonts="yes"
fontconfig="yes"

for right-looking softsub but that's it. I prefer it over VLC ... And I'm pretty sure some people prefer the default player too...

---

### Post by hanzomon4 on 2007-12-15
I think what I miss from video players is the ability to have your videos cataloged like your music in audio players such as rhythmbox. I really liked how I could do this to a point with itunes.

---

### Post by DizzyTech on 2007-12-15
No, this is how it's supposed to work.  You want to listen to music?  Launch Rhythmbox, double click on a song.  You want to see a video?  Click on Places, go to Videos.  Double click a file there.

---

### Post by zekopeko on 2007-12-15
one app for multimedia with library would be nice. and nice looking

---

### Post by OCTOG3N on 2007-12-15
> **DizzyTech said:**
> No, this is how it's supposed to work.  You want to listen to music?  Launch Rhythmbox, double click on a song.  You want to see a video?  Click on Places, go to Videos.  Double click a file there.

so remind me how I manage my video library and  sync it to ipod with video playlists? I thought so. And I mean SYNC a library not add videos one by one. I use itunes on XP because it syncs everything I need to my ipod and manages it to access on my computer. I think this is the kind of thing the poster was looking for.

---

### Post by hanzomon4 on 2007-12-16
I just found out that bmpx does video

---

### Post by scxtt on 2007-12-16
> **OCTOG3N said:**
> so remind me how I manage my video library and  sync it to ipod with video playlists? I thought so. And I mean SYNC a library not add videos one by one. I use itunes on XP because it syncs everything I need to my ipod and manages it to access on my computer. I think this is the kind of thing the poster was looking for.i don't think i should be surprised/impressed that apple can write software to sync to its hardware ...

---

### Post by Nonno Bassotto on 2007-12-16
You have different needs for music and video, so using different applications makes sense.

For instance you will hardly need a library to manage your videos, but it is a fundamental tool for music.

I like Rhythmbox (or Listen, or Exaile) + Totem

---

### Post by sawjew on 2007-12-16
I've just been playing around with Songbird and it looks like it may do the job eventually.  It's still under development at the moment but it definitely has potential.

I have been looking for an all-in-one media player too as that is one thing I miss from Windows.

---

### Post by CarpKing on 2007-12-17
> **Nonno Bassotto said:**
> You have different needs for music and video, so using different applications makes sense.

For instance you will hardly need a library to manage your videos, but it is a fundamental tool for music.

I like Rhythmbox (or Listen, or Exaile) + Totem

That's how I work too, but it would be nice to have a library plugin or something for Totem.  And since Rhythmbox already has a visualization plugin, it might be nice if it had a plugin to catalog and play videos as well, for people who are into that sort of thing.

---

### Post by rockin_goliath on 2007-12-18
Instead of incorporating video directly into Rhythmbox, I think having some sort of Totem plugin for Rhythmbox. This plugin would just give Totem the ability to catalog video files in it's library (and someway for the user to differentiate between music and video, probably in the left pane, such as having "music" and "video" as subdirectories of "library") and when a video file is selected, it's just opened in Totem.

---

### Post by coolen on 2007-12-20
I must say, I do see the appeal of video libraries. I think a library plugin for Totem would be perfect for this. I've always felt like Totem, while it suited my needs fine, was a weak substitute for WMP (compared to iTunes, though, anything rocks).

I could just launch Totem, then browse all video across my entire filesystem, decide what I'm in the mood for, and spend the day watching clips of Hugh Laurie.

Tracker support would be able to accomplish this beautifully. Hopefully, this sort of functionality can work its way into more applications.

---

### Post by davbren on 2007-12-20
Is there a possiblity of merging say totem and rhythmbox?, I think it would be such a good addition to Ubuntu...

---

### Post by smartboyathome on 2007-12-20
> **davbren said:**
> Is there a possiblity of merging say totem and rhythmbox?, I think it would be such a good addition to Ubuntu...

Not in Hardy (since it is an LTS, and that is bound to have many bugs), but maybe Hardy+1. :)

---

### Post by coolen on 2007-12-20
I seriously doubt they'll merge. They each have their own purpose, and their own place. I think this is just something Totem lacks.

---

### Post by RyanKage on 2007-12-21
Yeah... I've been looking for a complete (iTunes-like) media player for Linux (I'm on Ubuntu) for a couple of straight days now (with absolutely no luck)... I'm a huge Audio/Video podcast watcher/listener, music, and video fanatic. I would love it if there was a program that incorporated everything into one, just like how iTunes does it. That way I could get my (HD) video podcasts all updated automatically and audio podcasts, as well as getting my video(s) and TV shows up as well, oh and listening to my music in a nice organized way (a lot like how Rythmbox is but with all the extra video support). Meh, if I knew how to use Python and whatever else to create such an experience, I would love to start an open-source project on this. Sorry for the long response lol.

---

### Post by davbren on 2007-12-21
I would also be prepared to create something but my knowledge of python is non-existent... I might be able to create some kind of design if someone is willing to program it...

---

### Post by RyanKage on 2007-12-21
I would love to help, but like I said... I'm in the same boat as you lol. Heh, maybe I should take some college classes about this (if they have any where I'm going that is).

---

### Post by k99goran on 2007-12-22
Personally I have never liked the idea of a universal video/audio player, mainly because songs and videos are treated differently.
Music tend to be well organized (artist-album-song), and songs tend to be short which makes playlists more central to playback. I usually play music by starting the music player and then selecting a track/album from the playlist.
Videos on the other hand tend to be less organized, and they tend to be longer. I usually play movies by double-clicking on the file which opens up the video player.
And as such I would never use iTunes as my default video player as I need it to start up quickly (preferably instantly).

---

### Post by RyanKage on 2007-12-22
Hm. The reason why I enjoyed using iTunes on Windows (I have never owned a Mac) is that it was so easy just to manage EVERYTHING on it. With iTunes I could easily add any audio and video podcast feed I wanted, all of my music, all of my TV shows (in the correct directory), all of my audiobooks (again in the correct directory), and of course all of my movies (and yet again!! in the correct directory). I feel this would be so much easier than using 3 different freaking apps just to do what I want to do.. And that's: listen to audio podcasts and have them automatically updated within the player (sure I can do that with Rythmbox but what about Video??), watch the video podcasts within the same player, manage my music collection, and movies and tv shows oh damn that sounds too much like iTunes... Lol. But that's probably the easiest media player to use that's out there. Heh sorry for the long post yet again haha.

---

### Post by coolen on 2007-12-23
I can certainly see the appeal of that...although hopefully any Linux-based application could do it without the hideous bloat of iTunes.

In any case, we all use computers differently. I probably wouldn't have much use for such a program, and would be happy to use two different programs to handle video and audio seperately (in fact, I'd enjoy the distinction), but there's definitely a use case for it.

---

### Post by k99goran on 2007-12-23
Another problem is that the best music player is not necessarily the best video player, and vice versa. I guess this is the same argument as Konqueror vs Dolphin, the swiss army knife approach vs the specialized application approach.

---

### Post by mike_g on 2007-12-23
I love VLC player; it plays just about anything and thats all I care about.

---

### Post by ikt on 2007-12-23
I play a lot of music videos so I prefer having an application like Winamp which plays both music and videos.

I do use VLC a lot but for some reason I feel the media players on Linux compared to Windows Media Player and Itunes and Winamp are definately lacking.

It almost feels like a similar situation to before Deluge torrent, before Deluge came along the quality of Torrent Clients on linux was not on par with what to expect.

---

### Post by ikt on 2007-12-24
> **ikt said:**
> I play a lot of music videos so I prefer having an application like Winamp which plays both music and videos.

I do use VLC a lot but for some reason I feel the media players on Linux compared to Windows Media Player and Itunes and Winamp are definately lacking.

It almost feels like a similar situation to before Deluge torrent, before Deluge came along the quality of Torrent Clients on linux was not on par with what to expect.

To quote my own post again, VLC version 0.9.0 has a new and improved playlist feature and is looking really good so far. :KS

---

### Post by Vaelrith on 2007-12-26
I would love to have a play all media player.

I would more like something similar to WMP11.  When I used windows I loved that program despite it was kinda slow/typical windows.  I liked the way it organized the music collection, then easily switch over to viewing videos.  Everything in one program was nice.

That was my only dissapointment with linux.  However, I don't plan on going back to windows just because of a media player.  I think it could be done pretty easily although I don't know anything about programming.  Maybe a Rhythmbox plugin that would add a video view which was powered by totem.

---

### Post by davbren on 2007-12-27
Well thats exactly how I felt! It was a major disappointment when I switched. I can't be that hard to do. If I had a RAD tool I could probably manage one. But I have no clue of the RAD tools available. I would use Kylix but I don't know how to get it to work in Ubuntu. I might do a virtual Suse machine so I can get Kylix working... what do you think?

---

### Post by pmj on 2007-12-27
A all-in-one solution is rarely the best at any one thing, but that's been said already.

What's worse is that such all-in-one players make it more cumbersome to handle your media as you can't control music and video separately. If you are playing music and want to watch a video, doing so would cause the music to stop, and when you're done with the video you would have to find the same album again, and the right position within the right song, in order to continue listening, and if the video forced you to change the volume you would have to change that back again. Separate applications would allow you to listen to music and watch a video at the same time if you wanted to do that, or control the volume for each independently, pause the music when you want to watch a video and then simply resume playing music when the video is over, and pause a video you were watching if you want to play music for a while without losing your position in the movie, and there would be no delays and no hassle caused by switching between these two tasks.

All-in-one media players are more complicated and more difficult to use than separate applications, and are capable of far less. Go ahead and make one if you want, but I wouldn't count on one being default in Ubuntu or any other sane OS, because they're simply a bad idea.

---

### Post by davbren on 2007-12-27
I'm never said that the separate apps *shouldnt* exist, of course they should. Linux is about choice and I should be able to choose an all-in-one app.

---

### Post by mangar on 2007-12-27
If you're looking for a media center, what about mythTv or freevo?

---

### Post by davbren on 2007-12-27
I use mythtv and its fantastic but its not really what I'm looking for i really would like something like wmp11. It may be a bit sluggish but at least everything is there.

---

### Post by Vaelrith on 2007-12-27
> **davbren said:**
> I use mythtv and its fantastic but its not really what I'm looking for i really would like something like wmp11. It may be a bit sluggish but at least everything is there.

I wish there was something just like WMP11 for linux... It's so good, even though it is sluggish.

---

### Post by coolen on 2007-12-27
It all depends on who you are, really. You can't say that an all-in-one solution would always be less useful than separate applications.

An example: I'm listening to my music, just letting it play through, when suddenly *I Want to Break Free* starts playing. I happen to have the video clip to this song, and reckon Freddie Mercury looks damn fine in a dress: I'd tap that.

So, I opt to listen watch the video clip. I switch to the Library view (or perhaps simply start typing in a search box) and find two entries with that name. I choose the video, and enjoy. No need to start a new application, no need to pause or stop the current song, no need to start a new file manager window to navigate to the video clip which, for various reasons, is located far from anything in the Places menu.

---

### Post by davbren on 2007-12-31
Are there any programmers out there that can make this a reality. I really would be helpful with the design of it, even the programming if i could get started on how to make user interfaces. ( I have no clue in linux)

---

### Post by stijngysemans on 2007-12-31
There is a bug request for Rhythmbox that asks for video playback capabilities.
[http://bugzilla.gnome.org/show_bug.cgi?id=363822](http://bugzilla.gnome.org/show_bug.cgi?id=363822)

What you could do is create a GUI on paper or on the computer and a list of features. Some guy maybe can pick this up and start working on this!

---

### Post by Vaelrith on 2008-01-01
> **stijngysemans said:**
> What you could do is create a GUI on paper or on the computer and a list of features. Some guy maybe can pick this up and start working on this!

I've made a quick mock-up, with my ideas on it.  See the attached.  I'll also post it on the bug report link you posted.

---

### Post by Mazza558 on 2008-01-01
If people could merge:

*the simplicity of exaile
*downloading features of Songbird
*online video features of Miro
and the video playback of Totem, this'd be awesome.

---

### Post by coolen on 2008-01-01
I like that mockup. The reflective effect might be doable once the advanced widget effects gain wider acceptance.
I can't help but shake the feeling that this would be better done as a separate application, rather than as part of Rhythmbox, but I do like your mockup.

---

### Post by Vaelrith on 2008-01-01
I like the idea of it just keeping a video library, then when you click it, the video opens in totem.  Kind of like in iTunes, you click a video and it plays the video in a different window using quicktime.  Just to have the library would be nice.

---

### Post by FuturePilot on 2008-01-02
I like this idea as there really is no ultimate media player that can do both video and music. Or at the very least something like Vaelrith said.
> **Vaelrith said:**
> I like the idea of it just keeping a video library, then when you click it, the video opens in totem.  Kind of like in iTunes, you click a video and it plays the video in a different window using quicktime.  Just to have the library would be nice.

---

### Post by GMU_DodgyHodgy on 2008-01-08
One good reason to have a one-in-all media player is for IPod support.  Since Rhythmbox can sync with an Ipod easily and well for music - it would be great if it could handel video and photos so a user could have all their good media iin their IPOD - not just their music. 

Voila - Linux replacement for ITunes.

---

### Post by Kalibur on 2008-01-08
Just curious... when you look in the plugins option under edit menu of rhymbox and Mplayer(totem) there is a check box for Infra red remote control and a configure button!  Has anyone been able to use that feature?:confused:

---

### Post by djbon2112 on 2008-01-09
> **scxtt said:**
> what do you think is missing (from any or all of them)?

I can find NO all-in-one media player (with playlists)/media library like Winamp. There's a player (Audacious) that does the player/playlist function of Winamp, but there's NOTHING which has a similar media library. They're all iTunes like, whos layout I detest.

Is there ANYTHING out there, even a stand-alone media library manager, which resembles Winamp?

---

