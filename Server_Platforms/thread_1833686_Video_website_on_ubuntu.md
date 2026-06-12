---
title: "Video website on ubuntu"
date: 2011-08-26
forum: Server Platforms
---

### Post by new_tolinux on 2011-08-26
Hi,

I want to give it a try to get my own youtube-like website running, just for fun and just at home (otherwise I'd have to deal with copyright-issues and that's no option ;)).
I tried a few (like clipbucket, phpmotion, phpdirector) but it seems there's no good tutorial out in the wild about getting things done in ubuntu.
I really don't know where in the process things are going wrong, but I guess it has to do with the conversion packages.

Any ideas where to start, or any ideas about a better alternative?

The machine running it will be my testserver: ubuntu 10.04 desktop edition (with apache/mysql/php already running)

---

### Post by sanderd17 on 2011-08-26
You could use handbrake to convert it to WebM I guess ([https://trac.handbrake.fr/wiki/CLIGuide](https://trac.handbrake.fr/wiki/CLIGuide))

And afterwards use a HTML5 video player like [http://videojs.com/](http://videojs.com/)

I guess you can insure that everybody at home has a compatible browser, so you don't need to mess with flash.

---

### Post by new_tolinux on 2011-08-26
Ok, well, but as I have to do the conversion manually, I guess I'll do that on my 11.04 desktop...

I had a look at handbrake and did setup the PPA-repo, but then I ran into a little problem:
"Package 'libwebkit-1.0-2' has no installation candidate", and more, it's required to install handbrake-gtk

So, for now, I'm back where I started *lol*

---

### Post by sanderd17 on 2011-08-26
> **new_tolinux said:**
> Ok, well, but as I have to do the conversion manually, I guess I'll do that on my 11.04 desktop...

manually? You can upload custom files from a webpage, and you can let PHP run a script on your server to convert it to webM right?

I didn't try that all, but it should be possible.

> 

I had a look at handbrake and did setup the PPA-repo, but then I ran into a little problem:
"Package 'libwebkit-1.0-2' has no installation candidate", and more, it's required to install handbrake-gtk

So, for now, I'm back where I started *lol*
Oops sorry, it seems that handbrake is outdated (or at least their ppa). Another convert program has to be found.

Maybe ffmpeg will be better for you.

---

### Post by new_tolinux on 2011-08-26
> **sanderd17 said:**
> manually? You can upload custom files from a webpage, and you can let PHP run a script on your server to convert it to webM right?

But I guess the problems more or less started out with ffmpeg.

As far as I know, after a lot of googling around, the version shipped with ubuntu is a modified version (version numbers don't match) and it's on a different location as where the existing scripts expected it to be.

That means that I have to write my own video-CMS-system more or less from scratch, since the scripts that I tried are (almost) all encrypted in one way or another.

---

### Post by sanderd17 on 2011-08-26
> **new_tolinux said:**
> But I guess the problems more or less started out with ffmpeg.

As far as I know, after a lot of googling around, the version shipped with ubuntu is a modified version (version numbers don't match) and it's on a different location as where the existing scripts expected it to be.

That means that I have to write my own video-CMS-system more or less from scratch, since the scripts that I tried are (almost) all encrypted in one way or another.

you can base yourself on a customisable CMS like Drupal, and add the convert and play thingies yourself.

---

### Post by new_tolinux on 2011-08-26
Hmmz...
I tried drupal, walked over all the settings, but I can't even get some (probably simple) things working like displaying a menu :(

Although I managed to put another theme in it, that theme made the only test-post that I made disappear.

I don't know, maybe I should just give up on it.....
In the early days I wrote my own programs for DOS, and yet, I can't even get a CMS to do anything :lolflag:

---

### Post by SeijiSensei on 2011-08-26
> **new_tolinux said:**
> I had a look at handbrake and did setup the PPA-repo, but then I ran into a little problem: "Package 'libwebkit-1.0-2' has no installation candidate", and more, it's required to install handbrake-gtk

[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

Is this the PPA you tried?  If not, uninstall the version of handbrake you're running, replace the PPA you used with this one, and try again.

---

### Post by new_tolinux on 2011-08-27
> **SeijiSensei said:**
> https://launchpad.net/~stebbins/+archive/handbrake-snapshots

Is this the PPA you tried? If not, uninstall the version of handbrake you're running, replace the PPA you used with this one, and try again.
Appearently not, my sources.list says
> deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) lucid main
Source: [https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

As where the page you're referring to has these sources:

> deb [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
deb-src [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) YOUR_UBUNTU_VERSION_HERE main

The difference is that you are referring to the daily/unstable builds (snapshots), where I added the stable builds.

---

### Post by radiotehnika on 2011-08-27
[Gallery3 ]("http://gallery.menalto.com/") might be one solution.. It supports also [videos]("http://codex.gallery2.org/Gallery3:Modules:videos").

---

### Post by new_tolinux on 2011-08-28
> **radiotehnika said:**
> [Gallery3 ]("http://gallery.menalto.com/") might be one solution.. It supports also [videos]("http://codex.gallery2.org/Gallery3:Modules:videos").
That looks promising....
I just installed it and played around a bit, and it's actually working :)

It doesn't convert anything by itself, but it seems that I've finally managed to create a flashvideo which is actually watchable quality by using ffmpeg, which I can upload without a problem. The import-module isn't that interesting at the moment since I took the 20mb file limit out of the supplied .htaccess and my php.ini is set to accept 1GB

I just had a little laugh when I played a video: on my ubuntu 11.04 workstation in firefox the flashplayer crashed in full-screen as soon as I moved my mouse.
But on the other hand, on my "old" windows 7 notebook (with firefox) it works perfect, so that isn't a real problem (the viewing will be done mostly by windows-users and I have the original files which I can watch in Ubuntu).

Thanks a lot.

---

