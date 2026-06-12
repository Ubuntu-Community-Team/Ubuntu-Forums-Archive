---
title: "Amarok: completely bug-free!"
date: 2008-06-01
forum: The Cafe
---

### Post by picpak on 2008-06-01
Or so they say...check this out. I had exited Amarok about half an hour ago. I noticed things were getting sluggish, so I decided to check the System Monitor. Lo and behold:

[[IMG]http://img98.imageshack.us/img98/8629/screenshotwy3.th.png[/IMG]](http://img98.imageshack.us/my.php?image=screenshotwy3.png)

So, uh, I guess I never exited Amarok after all. Eventually Metacity had crashed, so you get to see some system info: I'm using about 763MB of RAM and 330MB of swap. That's over 1GB of memory being used! I'm also using 100% of my CPU. Now that's not entirely Amarok's fault, but look in the taskbar: the System Monitor is the only thing running. (Or, at least, the only thing that should be running: Audacity is in there too.)

Just to clarify: EVERYTHING FROM THE SCROLLBAR UP is amarokapp!

Even after I logged out, Amarok was still using 122MB of memory. Now I know Amarok doesn't develop for Gnome, but bugs like this are completely unacceptable, regardless of what desktop environment you use. Things like this should be fixed before they claim on their homepage that "There are no more bugs in Amarok 1.4".

---

### Post by corney91 on 2008-06-01
Ouch! Is that the (meant-to-be-)stable version, then? I can't say I've heard it described as bug-free, though...

---

### Post by Dixon Bainbridge on 2008-06-01
Amarok is a nice idea, but in practice its just awful. Mine crashes all over the place. Rhythmbox ftw.

---

### Post by picpak on 2008-06-01
> **corney91 said:**
> Ouch! Is that the (meant-to-be-)stable version, then? I can't say I've heard it described as bug-free, though...

Here's the original quote:

> "There are no more bugs in Amarok 1.4.  It is perfect, like a lotus flower.  In fact, we think we may cancel development on Amarok 2.0, as there is no point...you can't improve upon perfection."

In this context it sounds like he's joking, but I think what they're basically saying is that Amarok 1.4 is as good as they want it to be.

But right now, Amarok is freezing while loading my playlist.

/me wishes Exaile had more of Amarok's blingy features

---

### Post by FuturePilot on 2008-06-01
> **picpak said:**
> 

/me wishes Exaile had more of Amarok's blingy features

*hugs Exaile* :)

---

### Post by blueturtl on 2008-06-01
For me, Amarok will consistently crash if I type anything in the search box before it has completed populating the playlist.

Amarok unfortunately seems to be the best there is. Exaile looked ok, but without MySQL all music collection related activities seem pretty slow. Also the player outputs random static every few seconds when playing files, I mean what is up with that?! :confused:

---

### Post by karellen on 2008-06-01
I haven't had these sort of problems with Amarok, whether it's running in Gnome or KDE

---

### Post by Islington on 2008-06-01
is anyone giving songbird a try? I know I am.

---

### Post by picpak on 2008-06-01
> **blueturtl said:**
> For me, Amarok will consistently crash if I type anything in the search box before it has completed populating the playlist.

Same here, and that's when I want to get to the song.

> **blueturtl said:**
> Amarok unfortunately seems to be the best there is. Exaile looked ok, but without MySQL all music collection related activities seem pretty slow.

I know, huh? Searching in Exaile feels like it takes forever. Its database also seemed to screw itself up and tell me I have twice as many files as I actually do. And say it was 2 weeks and 52 hours long...*sigh*...

---

### Post by Joeb454 on 2008-06-01
> **picpak said:**
> /me wishes Exaile had more of Amarok's blingy features

/me thinks somebody has been on IRC too much ;)

---

### Post by Islington on 2008-06-01
> **joeb454 said:**
> /me Thinks Somebody Has Been On Irc Too Much ;)\\:d/

---

### Post by zekopeko on 2008-06-01
banshee anyone? the new i mean. there's a thread on the forums about it.

---

### Post by tdrusk on 2008-06-01
I personally have given up on Amarok. It works okay, but whenever it loads songs to my iPod it messes with the database. It makes my iPod slower. Rhythmbox doesn't do this. 

I am checking out Quod Libet now.

---

### Post by monstermudder78 on 2008-06-01
> **blueturtl said:**
> Also the player outputs random static every few seconds when playing files, I mean what is up with that?! :confused:

You just need to update to the newest version I think.  I had the same problem, and it's well known, I think the fix was an upgrade to a version that isn't in the official repos.

Exaile is where it's at for me!

---

### Post by tdrusk on 2008-06-01
Meh. Quod Libet was fast, but didn't have enough features. 

Back to my Rhythmbox.

---

### Post by picpak on 2008-06-01
Trying to find another media player. Rhythmbox is okay, but it doesn't have nearly everything I want. Here's what I like in Amarok:

[LIST]
[*]Multi-file tag editor with MusicBrainz lookup/Guess tags from filename
[*]File organizer
[*]Tag editing within the player
[*]Crossfade/fading effects
[*]Customizable keyboard shortcuts
[*]Automatic ratings system
[*]OSD popup
[*]Automatically uses folder.jpg cover art. If it's missing, there's a script I use that fetches the cover art and saves it as cover.jpg
[/LIST]

And, of course, things like last.fm, queuing and so on. I know it's a lot to ask, but is there anything for Gnome that can do most of these things? The closest I've found is Listen, but it hasn't been updated in over a year and its interface is ungodly.

---

### Post by SunnyRabbiera on 2008-06-01
> **picpak said:**
> Trying to find another media player. Rhythmbox is okay, but it doesn't have nearly everything I want. Here's what I like in Amarok:

[LIST]
[*]Multi-file tag editor with MusicBrainz lookup/Guess tags from filename
[*]File organizer
[*]Tag editing within the player
[*]Crossfade/fading effects
[*]Customizable keyboard shortcuts
[*]Automatic ratings system
[*]OSD popup
[*]Automatically uses folder.jpg cover art. If it's missing, there's a script I use that fetches the cover art and saves it as cover.jpg
[/LIST]

And, of course, things like last.fm, queuing and so on. I know it's a lot to ask, but is there anything for Gnome that can do most of these things? The closest I've found is Listen, but it hasn't been updated in over a year and its interface is ungodly.


exaile has some of those features.

---

### Post by Islington on 2008-06-01
Players You guys may not have tried out. 

Songbird
Gmusicbrowser

---

### Post by picpak on 2008-06-01
> **SunnyRabbiera said:**
> exaile has some of those features.

Thanks, but I was just talking about it earlier this thread. I may try out the SVN and see if anything's changed.

> Players You guys may not have tried out.

Songbird
Gmusicbrowser

Tried them...heck, I've tried practically all of the major players, but that was quite a while ago. I was wondering if a newcomer has come, or if some of them have had some major changes.

---

### Post by stmiller on 2008-06-01
A lot of Amarok's problems are related to the dependency on Xine for a backend. Amarok 2 will be able to use any backend, such as the more stable Gstreamer backend.

Also you can change the database setting in Amarok to SQLite which should help performance.

---

### Post by Mateo on 2008-06-01
> **zekopeko said:**
> banshee anyone? the new i mean. there's a thread on the forums about it.

i installed the repo version.  doesn't organize my music in any way.  which is weird.  I think it lets you create playlists that hang off of the Library tab.  So you can't browse by artist or album.  Lame.

Currently using bmpx now.  Best combination I've found of features and not crashing.  Listen crashes often, Rhythmbox crashes often, Exaile crashes often.  Quod Libet doesn't crash, and is really good, but there are just a couple of things I don't like about it (such as the way they handle the progress bar).  But Quod Libet does at least have a good plugin system.

---

### Post by picpak on 2008-06-01
> **stmiller said:**
> A lot of Amarok's problems are related to the dependency on Xine for a backend. Amarok 2 will be able to use any backend, such as the more stable Gstreamer backend.

Back in the day Xine used to be my best buddy, but Gstreamer has gotten more and more dependable. I hope Amarok 2 gets stable soon, without being rushed like KDE 4.

> **stmiller said:**
> Also you can change the database setting in Amarok to SQLite which should help performance.

I'm already using SQLite, I believe that's the default.

---

### Post by banjobacon on 2008-06-01
> **Mateo said:**
> i installed the repo version.  doesn't organize my music in any way.  which is weird.  I think it lets you create playlists that hang off of the Library tab.  So you can't browse by artist or album.  Lame.

You probably have to enable the artist/album browser in the View menu or something. If you really want to give Banshee a shot, though, you should try the 1.0 beta. There's an Ubuntu repo for it somewhere.

---

### Post by adityakavoor on 2008-06-01
banshee rocks

---

### Post by uraldinho on 2008-06-01
I use amorok for online radios only. I find it buggy for anything else. 

For mp3s, I use the old style XMMS. I like the winamp like interface of it. 

For videos, etc, Mplayer... 

I uninstall everything else.

---

### Post by John T. Monkey on 2008-06-02
I've started using mp3blaster in a terminal lately. No special features at all, but it uses about 900k (I'm finding Audacious using roughly 20mb, Ryhtmbox using slightly more than that and Amarok abour 30mb). 

I think uts the way forward. Amorok for if i want to show my computer off (while i'm using KDE) Thythmbox to show off if i'm using Gnome...

---

### Post by geoken on 2008-06-02
IMO, if you're a die hard Amarok user who feels other players are lacking Banshee will do nothing for you. Apart from video support, I'm not able to find anything in Banshee which isn't available in rhythmbox.

---

### Post by bigbrovar on 2008-06-02
i use to be addicted to amarok ... even it the crashes and all .. then one day i got sick of it .. and tried to see if i could found a solution to the problem .. i saw a guide on how to use mysql to manage my database on amarok .. and it worked .. for a long time .. then when i upgraded to hardy i tried it again .. things got worse .. i just started my good ol rhythmbox and i have not gone back since ..

---

### Post by Skorzen on 2008-06-02
I once used Amarok but it's kinda heavy for me and then switched to Audacious, that I also like much.

---

### Post by toupeiro on 2008-06-02
> **picpak said:**
> Trying to find another media player. Rhythmbox is okay, but it doesn't have nearly everything I want. Here's what I like in Amarok:

[LIST]
[*]Multi-file tag editor with MusicBrainz lookup/Guess tags from filename
[*]File organizer
[*]Tag editing within the player
[*]Crossfade/fading effects
[*]Customizable keyboard shortcuts
[*]Automatic ratings system
[*]OSD popup
[*]Automatically uses folder.jpg cover art. If it's missing, there's a script I use that fetches the cover art and saves it as cover.jpg
[/LIST]

And, of course, things like last.fm, queuing and so on. I know it's a lot to ask, but is there anything for Gnome that can do most of these things? The closest I've found is Listen, but it hasn't been updated in over a year and its interface is ungodly.

I also like these features.  Along with lyrics fetching, bio/discography fetching, and the script manager of course.  I've not had the problems many people are describing with amarok.  Its support with portable MP3 players is second to none, supports iPod, creative, and a lot of the other big ones that have proprietary filesystems. (Never heard of amarok "slowing down" an mp3 player.)  I've yet to find another media player that does everything Amarok can.  amarokap is resident on my system at 29MB, which I can totally live with considering firefox is pigging out at 105MB just to write this forum response.

---

### Post by corney91 on 2008-06-02
IMO the best media players now are gmusicbrowser, if you like to customize stuff, or Banshee 1.0, which I believe will stop people complain about the lack of iTunes on Linux when the stable version comes out ;)
If you want a fullscreen media centre, then Elisa is awesome:)

---

### Post by Drakkor on 2008-06-29
Why can't Exaile find any album covers ?

---

### Post by lswest on 2008-06-29
> **Drakkor said:**
> Why can't Exaile find any album covers ?

If you installed exaile from the repos it may still be the outdated one which uses an old system to download album art off amazon, since amazon changed their handling of album art a newer release will get album art properly again.

> 
Exaile 0.2.13 released!
2008-04-02 00:06

Today, April 1 2008, Amazon discontinued their ECS version 3.0 in favor of 4.0. This caused album art to stop being collected correctly. Exaile 0.2.13 is an emergency release aimed to fix this problem.

Grab it from the downloads page.
(from their web page)

[this]("http://www.exaile.org/downloads") is what you need to install a newer version.

---

### Post by RebounD11 on 2008-06-29
I've never had troubles with amarok (Gnome or KDE... or any other DE/WM)... except when using the yauap engine. Xine engine works flawlessly since 1.4.7.

---

### Post by geo909 on 2008-06-29
Wanted to try Rythmbox.
Does rythmbox has ratings and keyboard shortcuts for them?
I use that thing a lot in AMarok.

---

### Post by Drakkor on 2008-06-29
Thanks, lswest,but v.2.13 still not working properly, got maybe 4 covers withe the "Albun Art Collector" out of 100s of albums. :(

---

### Post by 23meg on 2008-06-29
[QUOTE=picpak]bugs like this are completely unacceptable[/QUOTE]

[QUOTE=picpak]Things like this should be fixed [/QUOTE]

How do you know it's a genuine bug? Has it been reported and triaged? If not, why not do so instead of ranting in a user forum?

[https://bugs.launchpad.net/ubuntu/+source/amarok](https://bugs.launchpad.net/ubuntu/+source/amarok) (if you installed from the Ubuntu repositories)

[http://bugs.kde.org/](http://bugs.kde.org/) (if you installed from source and can reproduce the problem with the upstream tarballs)

---

### Post by lswest on 2008-06-29
> **Drakkor said:**
> Thanks, lswest,but v.2.13 still not working properly, got maybe 4 covers withe the "Albun Art Collector" out of 100s of albums. :(

Hmm, then I don't know, it's been a while since I used Exaile.  Try running it from the terminal and see if any errors occur when downloading album art?

P.S. thanks for the thanks

---

### Post by banjobacon on 2008-06-29
> **geo909 said:**
> Wanted to try Rythmbox.
Does rythmbox has ratings and keyboard shortcuts for them?
I use that thing a lot in AMarok.

Rhythmbox has ratings, but I don't know about shortcuts.

---

### Post by LookTJ on 2008-06-29
How about MPD?

---

### Post by picpak on 2008-06-29
> **23meg said:**
> How do you know it's a genuine bug? Has it been reported and triaged? If not, why not do so instead of ranting in a user forum?

[https://bugs.launchpad.net/ubuntu/+source/amarok](https://bugs.launchpad.net/ubuntu/+source/amarok) (if you installed from the Ubuntu repositories)

[http://bugs.kde.org/](http://bugs.kde.org/) (if you installed from source and can reproduce the problem with the upstream tarballs)

Ding! Ding! I knew this post would come up. However, I haven't been able to reproduce the bug since. :( I wasted my opportunity.

---

### Post by 23meg on 2008-06-30
And I knew that this would be the reply; it always is. Next time, consider reporting first, ranting later.

---

### Post by barbedsaber on 2008-07-01
if I may say so
BANSHEE FTW! (although, exail, rhythm box, and a few others deserve a mention.)

---

### Post by doorknob60 on 2008-07-01
Wow, I've never had any problems with Amarok. Unless you count it constantly updating the collection (something weird happened when I transefered my home folder to a new computer I guess, worked fine before) EDIT: And of course that was easily fixed by disabling auto rescan collection :) Amarok FTW!

---

