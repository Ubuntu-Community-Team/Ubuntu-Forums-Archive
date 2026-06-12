---
title: "amaroK 1.3 released!"
date: 2005-08-15
forum: Requests
---

### Post by foxy123 on 2005-08-15
Any chance to see it backported any time soon? I am looking forward to it...

> The amaroK Development Team is very proud to clear version 1.3 of the popular audio player for takeoff. After four months of focused work, we feel that this release has again substantially improved on amaroK. We hope you enjoy amaroK 1.3's greater usability, exciting new features and many bugfixes.
Highlights:

    * Wikipedia artist lookup, a revolutionary feature providing information from the free online encyclopedia.
    * Redesigned sidebar, with improved look-and-feel.
    * Automatic download of scripts and themes with KNewStuff.
    * HelixPlayer engine.
    * New Playlist Browser, powerful and easy to use.
    * Cue file sheet support.
    * Dynamic playlist mode.
    * PostgreSQL database support.
    * Much extended DCOP scripting interface.
    * Multiple analyzer visualizations for the playlist window.
    * Podcast support, including live streaming and download capability.
    * Crossfading for the xine audio backend.

---

### Post by jamo on 2005-08-15
[QUOTE=foxy123]Any chance to see it backported any time soon? I am looking forward to it...[/QUOTE]
 please please please

---

### Post by thechitowncubs on 2005-08-15
ditto

---

### Post by ElVirolo on 2005-08-15
Yes, please package it ! It is such a wonderful application !

---

### Post by drizek on 2005-08-15
[QUOTE=ElVirolo]Yes, please package it ! It is such a wonderful application ![/QUOTE]
 errr... ditto

---

### Post by dbd on 2005-08-15
[QUOTE=thechitowncubs]ditto[/QUOTE]

ditto :)

---

### Post by PeP on 2005-08-15
a.deb is available here:
[http://ubuntuforums.org/showthread.php?p=303426#post303426](http://ubuntuforums.org/showthread.php?p=303426#post303426)

---

### Post by drizek on 2005-08-15
[QUOTE=PeP]a.deb is available here:
[http://ubuntuforums.org/showthread.php?p=303426#post303426](http://ubuntuforums.org/showthread.php?p=303426#post303426)[/QUOTE]
 thanks

---

### Post by shanghaipi on 2005-08-16
backport backport backport

---

### Post by diwakergupta on 2005-08-18
[QUOTE=shanghaipi]backport backport backport[/QUOTE]
 backport masters, come on!

---

### Post by kiddo on 2005-08-18
Don't forget about the "read more" link. There are LOTS of more important stuff too.

**Changes from Version 1.3-beta3:**

     **Features**

 
[list]
[*] The tyranny of deleting covers every 90 days is over. Instead, amaroK now       automatically downloads the covers every 80 days to comply with       Amazon.com requirements. 
[/list] **Changes**

 
[list]
[*] Removed 'Apply' button from dynamic config, all config options are now       hot! (Automatically applied on alteration)
[*] Minimum score changed from 1 to 0. ([BR 107944]("http://bugs.kde.org/show_bug.cgi?id=107944"))
[*] Playlist item lengths now shown with hours when necessary. 
[/list] **Bugfixes**

 
[list]
[*] M3U playlists would be broken after editing. ([BR 109774]("http://bugs.kde.org/show_bug.cgi?id=109774"))
[*] When there's no artist tag, don't show tons of unrelated songs and       albums in Context Browser. ([BR 110319]("http://bugs.kde.org/show_bug.cgi?id=110319"))
[*] Advertisements were showing up in Lyrics Tab for some songs.
[*] When editing tags in Playlist Window, only try to write the new tag if       it's different from the old one. ([BR 110299]("http://bugs.kde.org/show_bug.cgi?id=110299"))
[*] Changes to the score in the Edit Track Information dialog should only be       applied after clicking on the "Save and Close" button.
[*] When only the score is changed, amaroK shouldn't complain if the file is       read-only. ([BR 109054]("http://bugs.kde.org/show_bug.cgi?id=109054"))
[*] Mark/Unmark as compilation wouldn't work with SQLite. ([BR 109275]("http://bugs.kde.org/show_bug.cgi?id=109275"))
[*] Album Covers whose name or artist contained "'" wouldn't show up when       fetched from Amazon. ([BR 109700]("http://bugs.kde.org/show_bug.cgi?id=109700"))
[*] Edit Track Information dialog wouldn't update collection database if       filename contained non latin1 characters. Patch by Andrey Yasniy       <  [email="yasniy@gmail.com"]yasniy@gmail.com[/email]This email address is being protected from spam bots, you need Javascript enabled to view it> ([BR 110030]("http://bugs.kde.org/show_bug.cgi?id=110030"))
[*] SmartPlaylist category created in the PlaylistBrowser once the       collection has been built for the first time.
[*] Refresh the context browser as appropriate when editing tags. ([BR 108884]("http://bugs.kde.org/show_bug.cgi?id=108884"))
[*] Cover image shown if track has no title.
[*] Statusbar cancel button will terminate a podcast download.
[*] Don't show multiple popup messages when retrieving podcast information.
[*] Don't crash when adding podcasts. ([BR 109982]("http://bugs.kde.org/show_bug.cgi?id=109982"))
[*] Tracks with urls containg apostrophes would not cache lyrics.
[*] PostgreSQL compile problem ([BR 110033]("http://bugs.kde.org/show_bug.cgi?id=110033")) 
[/list]

---

### Post by Kuolio on 2005-08-18
yea, this would be cool to get in the backports asap!

---

### Post by praecantator on 2005-08-20
Please?  'twould be lovely...  :)

---

### Post by Mubis on 2005-08-21
Yes! Please backport amarok 1.3  [-o<

---

### Post by Sarojin on 2005-08-22
```

 ____  _     _____    _    ____  _____
|  _ \| |   | ____|  / \  / ___|| ____|
| |_) | |   |  _|   / _ \ \___ \|  _|
|  __/| |___| |___ / ___ \ ___) | |___
|_|   |_____|_____/_/   \_\____/|_____|
  Make my amaroK "with no relish"

```

---

### Post by foxy123 on 2005-08-23
well, all my attepts to install amarok 1.3 from the other threads failed :( as I understand it may not be in Breezy... what does it mean for us?

---

### Post by sbassett on 2005-08-25
I'm still throwing mmy vote in, amarok rocks.

---

### Post by jdong on 2005-08-29
Doesn't Kubuntu's update repositories have this? If not, then by all means I'll take a look.

---

### Post by frido on 2005-08-31
For people looking for packages that are working with Ubuntu's default KDE 3.4.0, maybe you want to take a look at [my weblog](http://frroo.blogspot.com/2005/08/amarok-13-musicbrainz-on-k-ubuntu.html) for some unofficial packages.

You'll also find a working libtunepimp version (for the otherwise broken MusicBrainz functionality in amarok, but this is Ubuntu specific). libtunepimp had to be recompiled with libmad0 (mp3) support, which is not the case by default. So you probably want to install these too if you want to use MusicBrainz.

---

### Post by oldblue on 2005-09-01
First off, THANK YOU for the packages.  Amarok, however, failed to load initially.  It said amarokapp was not in my path (I'm using Gnome as my default environment, maybe that has something to do with it).  Amarokapp is located at /usr/lib/amarok/amarokapp, so I just symlinked it to /usr/bin/amarokapp as a quick fix.  

Again, thank you for your packages.

EDIT -- Correction, I should say I symlinked /usr/bin/amarokapp to /usr/lib/amarok/amarokapp  :)

---

### Post by haakon on 2005-09-02
I also had the PATH problem. Temporary fix was to add /usr/lib/amarok to PATH, suppose I'll settle for a symlink for the longer term.

---

### Post by frido on 2005-09-02
Thanks for the feedback.  You're right, I had that problem too once, then I added a symlink in /usr/local/bin/amarokapp to /usr/lib/amarok/amarokapp.  That's probably why I didn't notice it.

Strange thing is that the amarokapp path of the official package (1.2.3) is also  /usr/lib/amarok, but maybe a link is created in post-install:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=amarokapp&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=amarokapp&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386)

Anyway, I'll try to get this fixed so it would work after install without manually creating the link... it may be confusing for some people.

EDIT: should be fixed now...

---

### Post by ossi on 2005-09-02
Is there any fixed date when the new version will be in standard-repositories? Does anybody know about ipod shuffle integration?? Could not find something in the Amarok blog.  greets

---

### Post by frido on 2005-09-04
Maybe you should take a look on the amaroK forum, there are topics about the ipod shuffle...  [Like this one.](http://amarok.kde.org/component/option,com_simpleboard/Itemid,/func,view/catid,11/id,7779/#7779)

---

### Post by ossi on 2005-09-05
Thx. I found this very interesting. Might have a closer (and longer) look next time.  O:)

---

### Post by geearf on 2005-09-08
1.3.1 out, please a repos for this :)

---

### Post by jdong on 2005-09-08
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=amarok](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=amarok)

It looks like Breezy won't get it... As soon as breezy+1 repos are open, I'll push for the version bump, and add it to official breezy-backports.

---

### Post by geearf on 2005-09-09
Ok thanks for the information,

---

### Post by UbuWu on 2005-09-16
Great news, a special exception to the freeze has been made and Amarok 1.3.1 is now in Breezy!!!

From the mailing list:
> Hi All,

Am Dienstag, den 06.09.2005, 21:52 +0100 schrieb Tiago Pinto:
> will amarok be packaged in its lastest version to breezy?

You can all say "Thank You, Mark, that you listen to the community" and
actually say "Thank You, Matt, that you gave your >>OK<< for breaking
the freeze" only for amarok_1.3.1-0ubuntu1 which should be available
latest in a couple of hours in Breezy.

My thanks are going to Mark and Matt for their "Ok, we do it" and to all
the testers from #kubuntu-devel@freenode.net (mitsushiko to mention, I
gave him a hard time ;), Riddell who saw some really little mistakes in
the first try)

Regards, have fun :)

---

### Post by geearf on 2005-09-16
Good thing, thanks a lot

---

### Post by Seth on 2005-09-16
[QUOTE=geearf]Good thing, thanks a lot[/QUOTE]
 Happiness. Time to apt-get upgrade my breezy install...

---

### Post by UbuWu on 2005-09-17
So now the question is: will it be backported to hoary? (not that I want it, already running breezy, but there are probably quite some people who will be running hoary for some time to come... although I wonder if they would be interested in the newest version of a program if they don't upgrade to the newest Ubuntu version...)

---

### Post by foxy123 on 2005-09-18
please note that 1.3.1 does not have alsasink support. They will restore it in 1.3.2.

---

### Post by ogami1972 on 2005-10-10
i'm using the gstreamer alsasink in 1.3.1- i just had to specify my device (hw:0,0 for me)

---

### Post by geearf on 2005-10-11
1.3.3 released, I hope someone can get its hand on a good deb soon :p

---

### Post by taavi on 2005-10-21
[QUOTE=geearf]1.3.3 released, I hope someone can get its hand on a good deb soon :p[/QUOTE]Is there deb available for 1.3.3. I'm want "Favourite albums" instead of "Favourite songs" in Context;)

---

### Post by John.Michael.Kane on 2005-10-21
in synaptic it's listed as 2:1.3.1 dont know if this is final code.

---

### Post by foxy123 on 2005-10-22
the latest is 1.3.3. It requires libtag 1.4, while Breezy has 1.3 something. So I could not compile it. I am quite reluctant to update manually libtag, so am waiting for new vesion in repos.

---

### Post by superm1 on 2005-10-23
My one holdback in switching from gentoo to ubuntu on my desktop is this amarok ipod bug.  I currently use amarok 1.3.3 in gentoo, and it works great.  On my laptop i have ubuntu with amarok 1.3.1 and it crashes when doing a transfer to my ipod.

---

### Post by foxy123 on 2005-10-24
I have compiled TagLib 1.4 as taglib and it co-exists with Ubuntu vesion which is libtag :) SO I have amarok 1.3.3 which looks more stable.

---

### Post by stoeptegel on 2005-10-25
1.3.5 now on kubuntu.org :)
(thanks guys, you rock!)

---

### Post by foxy123 on 2005-10-26
[QUOTE=stoeptegel]1.3.5 now on kubuntu.org :)
(thanks guys, you rock!)[/QUOTE]
is it in repositories?

---

### Post by stoeptegel on 2005-10-26
Nope they are here: [http://www.kubuntu.org/announcements/amarok-1.3.5.php](http://www.kubuntu.org/announcements/amarok-1.3.5.php)  They work fine here.

---

### Post by realbt on 2005-10-26
And unless I'm crazy, hoary packages are here: [http://kubuntu.org/packages/amarok-1.3.5/hoary/](http://kubuntu.org/packages/amarok-1.3.5/hoary/). I haven't tried it yet though...

---

### Post by escobar on 2005-11-05
I know this is old for everyone here but I can't find the proper way to install it on Kubuntu Hoary. I grabbed the debs from:

[http://kubuntu.org/packages/amarok-1.3.5/hoary/](http://kubuntu.org/packages/amarok-1.3.5/hoary/)

NONE will install due to dependecy issues. Is there a walkthrough or anything available?

---

### Post by escobar on 2005-11-07
[QUOTE=escobar]I know this is old for everyone here but I can't find the proper way to install it on Kubuntu Hoary. I grabbed the debs from:

[http://kubuntu.org/packages/amarok-1.3.5/hoary/](http://kubuntu.org/packages/amarok-1.3.5/hoary/)

NONE will install due to dependecy issues. Is there a walkthrough or anything available?[/QUOTE]

*bump*

---

### Post by tikal26 on 2005-11-07
escobar:
I thought that I had the same problem. I unistalled it and the dowloaded the file. then I installed the engine by right clicking on it it has a depackage deb option and then I got a dependency error mesage. I did the same for the amarok package and then went to synaptic and fixed all borken packages and the new amarok was there 1.3.5 I really don't know what happende but it worked. Or you can try this
[http://olwin.free.fr/serendipity/](http://olwin.free.fr/serendipity/)
easy ubuntu it automaticall installes it for you plus a bunch of other nice stuff

---

### Post by escobar on 2005-11-08
[QUOTE=tikal26]escobar:
I thought that I had the same problem. I unistalled it and the dowloaded the file. then I installed the engine by right clicking on it it has a depackage deb option and then I got a dependency error mesage. I did the same for the amarok package and then went to synaptic and fixed all borken packages and the new amarok was there 1.3.5 I really don't know what happende but it worked. Or you can try this
[http://olwin.free.fr/serendipity/](http://olwin.free.fr/serendipity/)
easy ubuntu it automaticall installes it for you plus a bunch of other nice stuff[/QUOTE]

I'm not sure if I follow your instructions. You installed what engine by right clicking it? Also, none of te broken packages I had could be fixed so I had to remove them. Using that link you provided is there a way just install Amarok and nothing else? Thanks.

---

### Post by tikal26 on 2005-11-08
escobar:
when you right click on it you get an option to depackage a debian package. If that does not work you can try the mailing list sometimes when I can't get an answer I use the mailing list that way everyone can see it. I don't know if that asnwer you question but I am in school right now and I can't remeber exactly waht I did. I'll post detail direction when I get back to my home computer. I actually wrote them down.

---

### Post by escobar on 2005-11-08
[QUOTE=tikal26]escobar:
when you right click on it you get an option to depackage a debian package. If that does not work you can try the mailing list sometimes when I can't get an answer I use the mailing list that way everyone can see it. I don't know if that asnwer you question but I am in school right now and I can't remeber exactly waht I did. I'll post detail direction when I get back to my home computer. I actually wrote them down.[/QUOTE]


Would be much appreciated. Thanks.

---

### Post by geearf on 2005-11-08
1.3.6 out

---

### Post by tikal26 on 2005-11-08
escobar 
here is  a snapshot of what I mean by righclick on the package. I think that I had to do the amarok package first and then the gstreamer. hope that it helps

---

### Post by escobar on 2005-11-09
[QUOTE=tikal26]escobar 
here is  a snapshot of what I mean by righclick on the package. I think that I had to do the amarok package first and then the gstreamer. hope that it helps[/QUOTE]

Can anyone confirm this is cool, even though I'm using Hoary?

---

### Post by CartOOn on 2005-11-14
The problem is : amarok depends on gstreamer engine, which depends on amarok, which....

To avoid the problem, the packages need to be installed together at the same time. My advice, type this in a command line window :

*sudo dpkg -i amarok_1.3.5-0ubuntu0.1_i386.deb amarok-gstreamer_1.3.5-0ubuntu0.1_i386.deb*

I've done so on my computer and I'm now running amarok 1.3.5 :)

---

### Post by jdong on 2005-11-14
[QUOTE=escobar]Can anyone confirm this is cool, even though I'm using Hoary?[/QUOTE]

**NO**, absolutely not... that's just asking for trouble. Binary packages are **very specific** to distribution version, so it's not too possible to run these packages on different systems. Especially since Hoary->Breezy marks an incompatible compiler upgrade (3.3 to 4.0).

Forcing the package to install on Hoary is a pretty bad idea. Don't try it!

---

### Post by tikal26 on 2005-11-14
I meant that he should use the hoary packages. there are hoary packages available also.

---

### Post by jdong on 2005-11-14
oh ok, ignore long warning then :)

---

