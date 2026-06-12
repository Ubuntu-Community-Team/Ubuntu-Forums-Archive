---
title: "Please include Umplayer in the repos"
date: 2011-06-28
forum: The Cafe
---

### Post by linuxyogi on 2011-06-28
Hi,

I am not sure if this is the correct place for a feature request.

Please include Umplayer [http://www.umplayer.com/](http://www.umplayer.com/)  in the repos. The reason I like it so much is that it can stream from youtube.

I rarely install anything outside the Ubuntu repos. 

Theoretically totem can do that too but the last time I checked this feature was not working (bug). 


[http://www.umplayer.com/](http://www.umplayer.com/)


Any news about when mplayer2 will be included ? I am having trouble playing videos 

[http://ubuntuforums.org/showthread.php?t=1790983](http://ubuntuforums.org/showthread.php?t=1790983). Please start reading from #5. 

[FONT=Arial][I][B]Read the attachment. ^^
[/B][/I][/FONT]

---

### Post by LowSky on 2011-06-28
Not really the place to post this.

new ideas should be posted here:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by Bandit on 2011-06-28
Its a frontend/gui for mplayer. I am installing as I post this and will try it out.


EDIT:

This thing looks pretty nice. I am gonna try ti tout for a while.

---

### Post by linuxyogi on 2011-06-28
> **LowSky said:**
> Not really the place to post this.

new ideas should be posted here:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

I just created an account at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) but there its written 

> Are you requesting a new package to be included in Ubuntu? Brainstorm is **not** the right place for it! See the new package request guide. 
And this [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages) is pretty complicated.

---

### Post by Bandit on 2011-07-04
I have been using UMPlayer for the past 5 days now and I really like this players interface. Its very professional looking, feature rich, easy to use and very flexible. Also since its base is MPlayer its fast and rock solid.

I am all for this being in the repos or even as a Totem replacement.

---

### Post by linuxyogi on 2011-07-04
I have installed it too :D Flash seems to be  terribly buggy in Natty. My PC hangs at least once everyday watching youtube.

Minitube is buggy too.

Umplayer is the best alternative IMO.

But the audio equalizer is problematic in both Umplayer & Smplayer. None of them work in realtime (like in vlc). You need to click apply for the changes to take effect. The video controls work fine.

---

### Post by Lucradia on 2011-07-04
Submit an issue to launchpad under the ubuntu listing, or ubuntu-team's bugs, etc.

I had to submit an issue to xfce-meta or whatever for xubuntu to include something, and it took a few months to do.

Also, the program must have at LEAST ONE stable version (IE: parole, 0.2.0) to be included.

The program also must not have any propietary parts (IE: VLC cannot be included.)

---

### Post by GWBouge on 2011-07-04
[Looks like Web Upd8 has a PPA for it]("http://www.webupd8.org/2011/06/umplayer-ppa.html"), which is good, although not the official repo's.

Just checked it out, seems pretty good, but I've got a few annoyances right off the bat:

[LIST]
[*] Video from my TV card is pretty choppy.  VLC stutters once every few minutes to a half hour or so, with umplayer it's just choppy.  (Note:  I'm just capturing from a satellite box, not using the tuner)
[*] When loading with a directory with an amount of music in it (ex: 'umplayer /my/music/dir/' where /my/music/dir has ~1000 songs), it takes a LONG time to load.  Ok, not an eternity, but a good 2 or 3 minutes.
[*] Am I just blind right now, or is there no way to play on 'Shuffle'?
[*] The toolbars are a pain.  Just my opinion.
[/LIST]

On the great side, it seems to search/play Youtube well, although I've never had any issues with Minitube or with flash by just going to the website.  Also, it actually remembers that I want 5.1 sound, where VLC keeps going back to stereo (which is pretty much the only place VLC tweaks me).

That said, I really wouldn't mind seeing it in the Ubuntu repo's, and I'll probably keep it installed and see how the updates roll and what gets worked out.  But for now, it's going to stay VLC + Audacious.  Choices rule.

---

### Post by doas777 on 2011-07-04
> **Bandit said:**
> I have been using UMPlayer for the past 5 days now and I really like this players interface. Its very professional looking, feature rich, easy to use and very flexible. Also since its base is MPlayer its fast and rock solid.

I am all for this being in the repos or even as a Totem replacement.
how does it stack up against smplayer?

---

### Post by johnnybelfast on 2011-07-04
looks promising

---

### Post by beew on 2011-07-04
> **doas777 said:**
> how does it stack up against smplayer?


Better. It is an enhanced fork of Smplayer actually.

---

### Post by beew on 2011-07-04
I don't care if they put it in the official repo. Installing from PPA is just fine by me. I wouldn't install it from the official repo anyway even if it is in there. I hate being stuck with a crippled version that never gets updated and gets no bug fixes. (actually Umplayer 0.95 has a bug, it freezes if you play local files in full screen using mplayer-mt as its backend,--whereas stock mplayer from repo and mplayer2 were fine, this was fixed in an update to 0.97. If I install it from repo it will be broken for 1.5 years)

---

### Post by linuxyogi on 2011-07-04
> **beew said:**
> actually Umplayer 0.95 has a bug, it freezes if you play local files in full screen using mplayer-mt as its backend,--whereas stock mplayer from repo and mplayer2 were fine, this was fixed in an update to 0.97.

Their official web site is offering 0.95.  [http://www.umplayer.com/download/](http://www.umplayer.com/download/)
So, they didn't upload the latest version on their web site while its available via an unofficial ppa ? If that's the case then its really disappointing.

They have uploaded ver 0.97 for windows & not for Linux.[-(

---

### Post by beew on 2011-07-04
> **linuxyogi said:**
> Their official web site is offering 0.95.  [http://www.umplayer.com/download/](http://www.umplayer.com/download/)
So, they didn't upload the latest version on their web site while its available via an unofficial ppa ? If that's the case then its really disappointing.

They have uploaded ver 0.97 for windows & not for Linux.[-(

I have upgraded to 0.97  more than a week ago by installing from the webupd8 ppa. :)

---

### Post by linuxyogi on 2011-07-04
> **beew said:**
> I have upgraded to 0.97 by installing from the webupd8 ppa.

I know that .... I read. But not maintaining the official site with up to date version is really uncool IMHO.

---

### Post by Lucradia on 2011-07-04
> **beew said:**
> Better. It is an enhanced fork of Smplayer actually.

does it still need QT? Or did someone finally make smplayer in gtk form?

I don't like any other mplayer front-ends than smplayer (due to not allowing you to add to play list; and repeat button, etc.)

---

### Post by Bandit on 2011-07-04
Its still using QT. Thats the only real downside to it. Not that QT is bad, I love QT. But this prohibits it being on the live CD due to space and needing QT libs. But no reason not to be in the repos.

---

### Post by jerenept on 2011-07-04
> **Lucradia said:**
> does it still need QT?** Or did someone finally make smplayer in gtk form?**

I don't like any other mplayer front-ends than smplayer (due to not allowing you to add to play list; and repeat button, etc.)

Gnome MPlayer?

---

### Post by Lucradia on 2011-07-04
> **jerenept said:**
> Gnome MPlayer?

I mean without any gnome depends. GTK doesn't need gnome depends, but some devs like to throw them in anyway.

Does gnome mplayer have forever repeat, and doesn't add to a playlist when you open the file?

---

### Post by linuxyogi on 2011-07-04
> **Lucradia said:**
> 
Does gnome mplayer have forever repeat, and doesn't add to a playlist when you open the file?

Gnome-Mplayer's playlist has a loop feature. It does add the file(s) to the playlist when you open the file.

---

### Post by Lucradia on 2011-07-04
> **linuxyogi said:**
> It does add the file(s) to the playlist when you open the file.

No thanks, totem it is. (Or parole)

---

### Post by linuxyogi on 2011-07-04
> **Lucradia said:**
> No thanks, totem it is. (Or parole)

Okay, but what's wrong with files getting added to the playlist ? Didn't understand.

---

### Post by Lucradia on 2011-07-04
> **linuxyogi said:**
> Okay, but what's wrong with files getting added to the playlist ? Didn't understand.

I only play one file at a time, and loop it a lot for quite some time, so I'd rather that my files I open replace the entire playlist when opened.

---

### Post by Bandit on 2011-07-04
> **Lucradia said:**
> I only play one file at a time, and loop it a lot for quite some time, so I'd rather that my files I open replace the entire playlist when opened.

UMPlayer lets you turn that option on or off. Its under Prefereces->Playlist

Just make sure your files are also set to Open UMPlayer and not to Enque in UMPlayer.

---

### Post by beew on 2011-07-04
> **Lucradia said:**
> No thanks, totem it is. (Or parole)


Totem stutters and dies with hd videos adn so does parole. mplayer works a lot better than these if you install the right version (either mplayer-mt or mplayer2)

---

### Post by linuxyogi on 2011-07-05
> **Lucradia said:**
> I only play one file at a time, and loop it a lot for quite some time, so I'd rather that my files I open replace the entire playlist when opened.

Gnome Mplayer too can do what yo want 

[IMG]http://dl.dropbox.com/u/30630174/gnmplayer.png[/IMG]

---

### Post by doas777 on 2011-07-05
> **jerenept said:**
> Gnome MPlayer?
do you mean the old gmplayer package? I never liked the gui much. was twichy, to put it nicely, and would not allow me to browse to network-based resources. I've used smplayer for some time, and find it to be one of the better players for dense content.

---

### Post by linuxyogi on 2011-07-05
> **doas777 said:**
> do you mean the old gmplayer package? I never liked the gui much. was twichy, to put it nicely, and would not allow me to browse to network-based resources. I've used smplayer for some time, and find it to be one of the better players for dense content.

Look at #26. That's Gnome Mplayer 

```
sudo apt-get install gnome-mplayer
```

[http://code.google.com/p/gnome-mplayer/](http://code.google.com/p/gnome-mplayer/)

---

### Post by cariboo on 2011-07-05
Create a feature request bug on [Launchpad]("https://bugs.launchpad.net"), Brainstorm only gets looked at just before UDS, so it may be some time before someone sees the idea.

---

### Post by linuxyogi on 2011-07-05
> **cariboo907 said:**
> Create a feature request bug on [Launchpad]("https://bugs.launchpad.net"), Brainstorm only gets looked at just before UDS, so it may be some time before someone sees the idea.

Hi,

I just created a Launchpad account. 

How do I create a "feature request bug" ?

---

### Post by Elfy on 2011-07-05
[https://bugs.launchpad.net/ubuntu/+filebug?no-redirect&field.tag=needs-packaging](https://bugs.launchpad.net/ubuntu/+filebug?no-redirect&field.tag=needs-packaging)

As far as I can see that'll create the bug with the correct tag.

Then [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages/ExamplePackageRequest](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages/ExamplePackageRequest)

---

### Post by linuxyogi on 2011-07-05
> **forestpiskie said:**
> [https://bugs.launchpad.net/ubuntu/+filebug?no-redirect&field.tag=needs-packaging](https://bugs.launchpad.net/ubuntu/+filebug?no-redirect&field.tag=needs-packaging)



I have created a bug report with the correct tag but ......  

> **forestpiskie said:**
> 

As far as I can see that'll create the bug with the correct tag.

Then [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages/ExamplePackageRequest](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages/ExamplePackageRequest)

Didn't read that before creating the report  & hence an amateur looking report. 

But I guess its doable

[https://bugs.launchpad.net/ubuntu/+bug/805816](https://bugs.launchpad.net/ubuntu/+bug/805816)

SORRY. :-# [URL="http://www.youtube.com/watch?v=zA32ikd9B34"]Click 
[/URL]

---

### Post by Lucradia on 2011-07-05
Not sure why ubuntu itself has no meta package for gnome, etc. Guessing that's because -meta packages for the overall GUI system (IE: xubuntu-meta) aren't needed for the Ubuntu project? I see ubuntustudio-meta though.

Otherwise, I'd suggest adding the -meta **package** to your bug too, since you only have the project in the bug, which I've never been able to report a bug on before (Always said I must use apport, or something, which I could never figure out how to use.)

---

### Post by Perfect Storm on 2011-07-05
> **linuxyogi said:**
> Look at #26. That's Gnome Mplayer 

```
sudo apt-get install gnome-mplayer
```

[http://code.google.com/p/gnome-mplayer/](http://code.google.com/p/gnome-mplayer/)

Though the latest is 1.0.4, in repo 1.0.2. I haven't found any PPA for it.
But if people don't mind compiling it: [http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/](http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/)
either use mplayer, mplayer-mt or mplayer2. In the guide it is shown with mplayer daily development version.

---

### Post by jerenept on 2011-07-05
> **Lucradia said:**
> Not sure why ubuntu itself has no meta package for gnome, etc. Guessing that's because -meta packages for the overall GUI system (IE: xubuntu-meta) aren't needed for the Ubuntu project? I see ubuntustudio-meta though.

Otherwise, I'd suggest adding the -meta **package** to your bug too, since you only have the project in the bug, which I've never been able to report a bug on before (Always said I must use apport, or something, which I could never figure out how to use.)

Metapackage for Gnome is [ubuntu-desktop]("apt://ubuntu-desktop")

---

### Post by Lucradia on 2011-07-05
> **jerenept said:**
> Metapackage for Gnome is [ubuntu-desktop]("apt://ubuntu-desktop")

Oh yeah, I forgot about that -_-

yeah, might want to add that too, just in case the overall project is removed from your bug, or marked as invalid.

---

### Post by linuxyogi on 2011-07-05
> **Lucradia said:**
> Oh yeah, I forgot about that -_-

yeah, might want to add that too, just in case the overall project is removed from your bug, or marked as invalid.

[IMG]http://dl.dropbox.com/u/30630174/Screenshot-1.png[/IMG]

Add ubuntu-desktop to the tag list  ? 

When I typed "ubuntu-"     only ubuntu-unr  appeared as suggestion.

---

### Post by Lucradia on 2011-07-05
> **linuxyogi said:**
> [IMG]http://dl.dropbox.com/u/30630174/Screenshot-1.png[/IMG]

Add ubuntu-desktop to the tag list  ? 

When I typed "ubuntu-"     only ubuntu-unr  appeared as suggestion.

No, as an affected package. << A note. The devs may mark it as invalid, but they may look at your bug more, and it may get to more people.

I never leave out any packages, even if it gets marked as invalid as a package. The ubuntu-desktop package is used to include directly into the ubuntu ISO itself.

---

### Post by linuxyogi on 2011-07-07
> **Artificial Intelligence said:**
> Though the latest is 1.0.4, in repo 1.0.2. I haven't found any PPA for it.
But if people don't mind compiling it: [http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/](http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/)
either use mplayer, mplayer-mt or mplayer2. In the guide it is shown with mplayer daily development version.

Done :D  Thanks

---

### Post by linuxyogi on 2011-08-06
There is no irc channel for Umplayer.

Gnome-Mplayer has one but there's nobody talking.
 
^^^:confused:

I wanted to know how to subscribe to mailing lists of Gnome Mplayer & Umplayer. 

I want to get notified when un updated ver is available.

Never done that before. How do I do that ?

---

### Post by mbz99 on 2011-08-06
I see a good positive point from my side, and that an exclusive feature for smplayer and umplayer, I can read subtitles on the black area below the video. No famous player like vlc, totem support this feature.

---

### Post by beew on 2011-08-06
> **Artificial Intelligence said:**
> Though the latest is 1.0.4, in repo 1.0.2. I haven't found any PPA for it.
But if people don't mind compiling it: [http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/](http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/)
either use mplayer, mplayer-mt or mplayer2. In the guide it is shown with mplayer daily development version.

You get the latest here
[https://launchpad.net/~ed10vi86/+archive/tst]("https://launchpad.net/%7Eed10vi86/+archive/tst")

---

### Post by beew on 2011-08-06
Has anyone succeeded in using dvd menus with any frontend for mplayer?

---

### Post by lovinglinux on 2011-08-06
> **beew said:**
> Has anyone succeeded in using dvd menus with any frontend for mplayer?

I have been using on SMplayer, but it is very buggy. Sometimes it only displays a grey rectangle over the menus. However, as far as I remember, it worked well with the last movie I watched.

---

### Post by Bandit on 2011-08-06
I am confused, its 440am here.. Whats going on?:confused:

---

### Post by Bandit on 2011-08-06
> **beew said:**
> Has anyone succeeded in using dvd menus with any frontend for mplayer?

Yes I do.. But every now and then you may run into one that flakey about working just right.

---

