---
title: "Problems with radio streams and Rhythmbox"
date: 2013-03-02
forum: Ubuntu Development Version
---

### Post by thotz on 2013-03-02
Has anybody got problems with radio streams from the internet and Rhythmbox?

---

### Post by sgage on 2013-03-02
Yes. This has been an issue for me for quite some time - I posted about it a while back but it didn't go anywhere:

[http://ubuntuforums.org/showthread.php?t=2116694](http://ubuntuforums.org/showthread.php?t=2116694)

 I hope they fix it. I'm using Audacious for the time being.

---

### Post by mc4man on 2013-03-02
> **sgage said:**
> Yes. This has been an issue for me for quite some time - I posted about it a while back but it didn't go anywhere:

[http://ubuntuforums.org/showthread.php?t=2116694](http://ubuntuforums.org/showthread.php?t=2116694)

 I hope they fix it. I'm using Audacious for the time being.

Well they can't fix what they don't know is broken, have you looked for a LP & or upstream bug report or filed one if there isn't?

---

### Post by thotz on 2013-03-02
I have filed a bug: [https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1139760](https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1139760)

---

### Post by Budovi on 2013-03-02
It seems like it is rhytmbox bug, not gstreamer's one, because:
1, other apps using gstreamer work
2, pre-installed radio streams work
3, only added stations do nothing

---

### Post by mc4man on 2013-03-02
Here it seems some stations can be added, some not.
Found some mp3  that work, (most don't), no aac yet, ogg & .asx usually do, flac, though rare, also adds & works ok

Some that are added (to unknown), when clicked on disappear & are placed elsewhere where they may work. An ex. of that is this - goes to a new "radio" category
[http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u](http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u)

Overall seems a bit of a mess & totally unreliable..

---

### Post by thotz on 2013-06-07
Everything should be tracked here: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1153934](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1153934)

Upstream in GNOME: [https://bugzilla.gnome.org/show_bug.cgi?id=695652](https://bugzilla.gnome.org/show_bug.cgi?id=695652)

This bug first occured in Raring and still occurs in Saucy. I have also tested Fedora 19 Beta same problem.

---

### Post by QDR06VV9 on 2013-06-08
> **thotz said:**
> Everything should be tracked here: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1153934](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1153934)

Upstream in GNOME: [https://bugzilla.gnome.org/show_bug.cgi?id=695652](https://bugzilla.gnome.org/show_bug.cgi?id=695652)

This bug first occured in Raring and _still occurs in Saucy_. I have also tested Fedora 19 Beta same problem.

I also can comfirm.
For what its worth AronBeat has mentioned he recevied confirmation from the gstream folks that bug lies with gstreamer?

---

### Post by thotz on 2013-06-10
> **runrickus said:**
> I also can comfirm.
For what its worth AronBeat has mentioned he recevied confirmation from the gstream folks that bug lies with gstreamer?

Currently I need somebody from the Ubuntu Desktop Team. I don't know the skills of every person, I was on IRC and nobody replied me. Maybe I try again.

---

### Post by wgarcia on 2013-06-11
A workaround that works for me is:

1) start the radio stream you want to play
2) look (with "ps -ef | grep gvf" from a command line) for a process called "gvfsd-http"
3) kill that process ("kill -9 <process-number>")

The radio stream starts playing immediately after this. 

In the upstream bug report I was told that a fix was committed (about a month ago) so that gvsfd would not block rhythmbox, so I presume this will land eventually in saucy

---

### Post by mc4man on 2013-06-11
> **wgarcia said:**
> A workaround that works for me is:

1) start the radio stream you want to play
2) look (with "ps -ef | grep gvf" from a command line) for a process called "gvfsd-http"
3) kill that process ("kill -9 <process-number>")

The radio stream starts playing immediately after this. 

In the upstream bug report I was told that a fix was committed (about a month ago) so that gvsfd would not block rhythmbox, so I presume this will land eventually in saucy

The bulk of that commit to totem-pl-parser is in 3.4.5 & makes no difference, gvfsd-http is still an issue. Tested with all the mentioned streams in both reports, with gvfsd-http active no dice, with it not then all streams play in Rb & Videos
(to make easier to test multiple I just mv 'ed /usr/lib/gvfs/gvfsd-http to a .bak

---

### Post by wgarcia on 2013-06-11
To be honest I don't understand exactly what is going on. But, can you please report this back to the upstream bug, or is this issue being considered anywhere else?

---

### Post by mc4man on 2013-06-11
> **wgarcia said:**
> To be honest I don't understand exactly what is going on. But, can you please report this back to the upstream bug, or is this issue being considered anywhere else?
Well the bug on gvfs(http) is still open, that's where it should be fixed, when ?, no clue

---

### Post by nmlferreira on 2013-07-09
From what I've read, it looks like this problem wasn't solved yet.

I have some radio stations added, but most of the ones I like don't work.
Under properties it clearly says there are missing plugins to Gstreamer.
Any idea what those plugins are and how can I find them?

Thanks.

---

### Post by mc4man on 2013-07-09
> **nmlferreira said:**
> From what I've read, it looks like this problem wasn't solved yet.

I have some radio stations added, but most of the ones I like don't work.
Under properties it clearly says there are missing plugins to Gstreamer.
Any idea what those plugins are and how can I find them?

Thanks.

Maybe post a link to a non working one

as far as the upstream totem-plparser 'fix', I've tested it in raring & does nothing to fix this (at least in Ubuntu

---

### Post by thotz on 2013-09-29
They have fixed the bug in git: [https://bugzilla.gnome.org/show_bug.cgi?id=695652#c44](https://bugzilla.gnome.org/show_bug.cgi?id=695652#c44)

---

### Post by mc4man on 2013-09-29
> **thotz said:**
> They have fixed the bug in git: [https://bugzilla.gnome.org/show_bug.cgi?id=695652#c44](https://bugzilla.gnome.org/show_bug.cgi?id=695652#c44)

Tried the current libsoup git master here - now that *does* work to fix. 
When you see it in Debian/Ubuntu who knows, hopefully in 14.04 before release

---

### Post by richardsdma on 2013-09-30
i really don't know why this push for rhythmbox and empathy, they are the crappiest apps on the ubuntu environment. 
don't bother with rhythmbox, use clementine or even audacious. 
what a shame!

---

### Post by tophatandy on 2013-10-02
Looks like there was an update to fix this that was [committed]("https://bugs.launchpad.net/ubuntu/+source/libsoup/+bug/1153934"). I have no idea how long until this reaches the users in the form of an update (when the next release is). Anyone have an idea?

---

### Post by richardsdma on 2013-10-03
as i told you man.....just dump the apps that are crappy. 
for me, rhythmbox always has an issue......
i use clementine for one and a half year and i never had an issue (on linux or windows). 
you also can use VLC, SMplayer. very good apps!

---

### Post by thotz on 2013-10-03
> **richardsdma said:**
> as i told you man.....just dump the apps that are crappy. 
for me, rhythmbox always has an issue......
i use clementine for one and a half year and i never had an issue (on linux or windows). 
you also can use VLC, SMplayer. very good apps!

I completely disagree: I think there are too less people in the team, that care about bugs in the shipped packages. Only using another product is not the best idea, there are many Rhythmbox users out there. It would be better to fix the bug before release.

---

### Post by richardsdma on 2013-10-03
it would be better, yeah.....but that won't happen. 
RB has a lot of users because it came by default in ubuntu/gnome.....otherwise, the number of users would be count on fingers off one hand. 
the same <snip> is happening with empathy versus pidgin. 
i have a message for all the ubuntu users: 
try as much as you can to use only cross platform apps, they are a much better quality.

---

### Post by tophatandy on 2013-10-03
Saw something come in the form of a gfvs update this morning. Still waiting for a libsoup update though. Kinda is a bummer it took this long to isolate and fix a bug for such a large project. :\

---

### Post by wgarcia on 2013-10-04
This was an "upstream" fix, that is it was solved for the whole Linux community and not only for Ubuntu. So now a process has to be followed until the fix lands in Ubuntu. Please correct me if I don't describe it well: First it has to go to Debian, and for that it has to follow its own process. Once it is in Debian it has to arrive to Ubuntu, as a new version of libsoup, which will not happen until the next release, since the Debian freeze was met long ago for the current development release.

So in my opinion Ubuntu developers have nothing to do now with the fix not landing sooner here. The delay on fixing this cannot be attributed either to Ubuntu, this was affecting the whole Linux ecosystem.

---

### Post by mc4man on 2013-10-26
This should be fixed in trusty with libsoup2.4-2.44.1 
As far as saucy probably not though it appears 2.4-2.44.1 would work fine
(there is sometimes a short window where some new dev version packages can be installed in prev. release if inclined to try.

Otherwise have a saucy libsoup build scheduled in [an RB ppa]("https://launchpad.net/~mc3man/+archive/rbaudiocd-fix"), will have to test once built though should be ok

---

### Post by k.pagkalos on 2013-10-30
> **wgarcia said:**
> A workaround that works for me is:

1) start the radio stream you want to play
2) look (with "ps -ef | grep gvf" from a command line) for a process called "gvfsd-http"
3) kill that process ("kill -9 <process-number>")

The radio stream starts playing immediately after this. 

In the upstream bug report I was told that a fix was committed (about a month ago) so that gvsfd would not block rhythmbox, so I presume this will land eventually in saucy


The bug seems to be there still in my up-to-date Ubuntu 13.10 default Rhythmbox.

To effectively do what the above post recommends without "looking", you can open a terminal window and issue:

                 
 **kill -9 `ps -ef | grep gvfsd-http|head -1|awk '{print $2;}'`**

---

### Post by mc4man on 2013-10-30
> **k.pagkalos said:**
> The bug seems to be there still in my up-to-date Ubuntu 13.10 default Rhythmbox.

To effectively do what the above post recommends without "looking", you can open a terminal window and issue:

                 
 **kill -9 `ps -ef | grep gvfsd-http|head -1|awk '{print $2;}'`**
And it will be unless there is an update to libsoup in 13.10 which the odds are slim to none 
(- works fine here in 13.10 with new libsoup & obviously ok in 14.04

---

