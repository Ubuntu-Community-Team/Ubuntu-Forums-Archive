---
title: "Banshee now with YouTube"
date: 2010-03-09
forum: The Cafe
---

### Post by gnomeuser on 2010-03-09
I figured people might enjoy this. Banshee just got an extension added to git that allows showing related youtube videos in the context pane. I haven't had a chance to play with it yet, mainly because I am to lazy and would rather wait for it to hit the banshee-daily ppa.

[http://git.gnome.org/browse/banshee/commit/?id=079af2acf76ffe55dff94c36a656cec4aeee90ee](http://git.gnome.org/browse/banshee/commit/?id=079af2acf76ffe55dff94c36a656cec4aeee90ee)

A quick video demo can be found further down.

---

### Post by gnomeuser on 2010-03-10
And today [the gapless playback branch was merged](http://git.gnome.org/browse/banshee/commit/?id=40c1006a41bfa920b0d3c534b9f1d6e230ff7866)

---

### Post by SushiR on 2010-03-10
I'm not a banshee fan but the new improvements sound pretty good.

---

### Post by LADmaticCA on 2010-03-10
Awesome! Sounds great, especially the gapless playback. Do you know how to get 1.5.4 on lucid?

---

### Post by gnomeuser on 2010-03-10
You can test this now using the [banshee-daily PPA](https://launchpad.net/~banshee-team/+archive/banshee-daily). Packages are available for Lucid, Karmic, Jaunty and Intrepid. Assume this come with no support what so ever and that there may be bugs. 

Important.
** Take precautions such as backing up your database and other data (~/.config/banshee-1 mainly) and learn to obtain and use ppa-purge. Finally be sure to read and follow the ppa instructions, also bugs should be evaluated before submission upstream. **

I'll record a video of the new features so people can see them, just give me a bit of time to set it up.

Also new is an entry in the edit menu to Open the currently playing song in a folder.

---

### Post by gnomeuser on 2010-03-10
I recorded a quick little demo of the features in question.

[http://thegnomecommentary.blip.tv/](http://thegnomecommentary.blip.tv/)

There is also a [theora file](http://blip.tv/file/get/DavidNielsen-QuickBanshee155FeaturePreview103.ogg) for those that prefer that:

---

### Post by docus on 2010-03-10
I'm really loving Banshee these days - it's such a slick, stable, versatile app, and fast too.  However, I use Arch and unfortunately they haven't yet updated the version of podsleuth in their repo to the new version that allows banshee to detect iPod classics.  So, until then I'm playing around with Quod Libet (brilliant app) and Rhythmbox (also brilliant).

Keep up the good work Banshee devs!

---

### Post by RaZe42 on 2010-03-10
docus you can always use banshee-git from aur

---

### Post by GMU_DodgyHodgy on 2010-03-10
Banshee has evolved into one slick application that I now identify as a symbol of the linux desktop.  

It has a lot of features but also just works and doesn't get in my way.  

I like where this project is going.  

Kudos to all working on this application.

---

### Post by gnomeuser on 2010-03-10
And we are on omg ubuntu.

[http://www.omgubuntu.co.uk/2010/03/quick-look-at-some-new-features-in.html](http://www.omgubuntu.co.uk/2010/03/quick-look-at-some-new-features-in.html)

---

### Post by jpeddicord on 2010-03-10
Out of curiosity, does the gapless branch include the new [ReplayGain patch]("https://bugzilla.gnome.org/show_bug.cgi?id=600072")?

(Edit: judging by [this commit]("http://git.gnome.org/browse/banshee/diff/libbanshee/banshee-player-replaygain.c?id=40c1006a41bfa920b0d3c534b9f1d6e230ff7866") [(and this)]("http://gitorious.org/~raof/banshee/gapless-work/commit/01079472bcc3e99cece8e7a049ff85f44ebf6e5c"), seems it has! :D)

---

### Post by gnomeuser on 2010-03-10
> **jpeddicord said:**
> Out of curiosity, does the gapless branch include the new [ReplayGain patch]("https://bugzilla.gnome.org/show_bug.cgi?id=600072")?

(Edit: judging by [this commit]("http://git.gnome.org/browse/banshee/diff/libbanshee/banshee-player-replaygain.c?id=40c1006a41bfa920b0d3c534b9f1d6e230ff7866"), seems it has! :D)

I believe debate on how to go about fixing regain is on going on the list currently.

---

### Post by docus on 2010-03-10
> **RaZe42 said:**
> docus you can always use banshee-git from aur

Thanks RaZe42, I'll give that a try!

---

