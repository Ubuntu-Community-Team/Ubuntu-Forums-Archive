---
title: "Pulseaudio woes"
date: 2009-12-24
forum: System76 Support
---

### Post by Derath on 2009-12-24
PANP4N

I'll probably reinstall this weekend, until then if anyone has suggestions or an "Ah Hah!" moment, please reply and let me know what to try next. The story so far:

So I finally did my upgrade to 9.10 this past week, only to find that most of my sound system is now busted...seems there's issues with pulseaudio only allowing one app to use the sound system, unlike what it's supposed to do (mix several apps through to the sound system). And let's not even get into what happens when using Wine, I have seens some really odd behavior, but nothing like this (in one app, the background music and environmental sounds do not work, but the integrated voice chat does?!?!?!?). :-(

While I am a KDE user, I do keep a gnome desktop lingering around on my systems for some of the apps (gedit, and a few others), as well as being able to walk users through the menus (over the phone or net). For gnome users, this has got to be a huge annoyance. Here are some of the things I have done:

First: "Well, I'll just roll-back" Attempt to roll back the driver, this didn't work since synaptic won't allow it in the first place, but as I was about to force with dpkg, I realized that the upgrade also removed hal to replace with udev, and since the packages were written for hal, I didn't think this would work at all.

Second: "Google is my friend", found a write-up where someone had success by deleting the ~/.pulseaudio/ and .pulsecookie, and adding themselves to the audio group. This worked pretty well, for the first app I ran (incidentally a Wine app where the sound was garbled beforehand), after that, the problem resurfaced; so this means I need to do it each and everytime. :confused:

Third: "Okay, there has to be updates SOMEWHERE!" Seems that the latest in the repos (0.9.19) has the bug in it, and pulse's website has latest as 0.9.21, Okay, pull down the source; .configure, make, sudo make install... Interesting, now I keep getting errors about not finding libpulsecore.0.9.21.so... copy/paste and drop it into /usr/lib, still not finding it. <sigh> Googling again comes up with some write-ups that give ppa's and suggests upgrading alsa AND pulse, so I run through those. Now pulse give version 0.9.21; test run: Amarok plays good, start up firefox and pull up a video, huh? I can still hear the mp3, but I can't hear the video. Okay, so we can only have one app taking the sound outputs again. ](*,)

Now: I'm tired of fighting with this, downloading 9.10 kubuntu, and going to do a clean install (minus my home directory, which I may just delete the .gnom* and .kd* folders to clean all that up. Sucks that I'm going to have to recollect passwords from some people for the 15 wireless networks I use.

And I'm not expecting Tom to reply, considering what day it is, but if you want to Tom, I'm not going to complain! ):P

---

### Post by jdb on 2009-12-24
> **Derath said:**
> Sucks that I'm going to have to recollect passwords from some people for the 15 wireless networks I use.

That's one of the reasons I use an un-encrypted keyring.
If it's not encrypted it has the following features:
1) You can read it & write it with any editor.
2) You are never asked for a keyring password.

No one else can read it or change it unless they are logged in as you or as root.

It will be un-encrypted if you don't supply it a login the first
time it pops up.

If it's already encrypted & you don't want it that way:
```
sudo rm ~/.gnome2/login.keyring
```
You will lose all the remembered passwords and it will ask you for
a new keyring password the next time it pops up.
If you don't give it one it will build an un-encrypted keyring.

jdb

---

### Post by Derath on 2009-12-24
Good point, I believe it'll be kwallet on the next go-around though :) Either way, I just noticed asound was updated tonight, might have to give it another shot tomorrow night or something.

---

### Post by thomasaaron on 2009-12-26
Sorry, my wife wouldn't let me answer any forum posts or emails on Christmas. :confused:

The upgrade to 9.10 has been as bad (if not worse) than the upgrade to 9.04.

I'm guessing that you've re-installed by now?

---

### Post by Derath on 2009-12-27
Actually, I haven't yet, and it looks like things have worked out... the posting about the PPA's Alsa actually had an update thrown down the pipe on Christmas Eve (version 1.0.21+dfsg-3ubuntu1~ricotz1) and libasound2 (1.0.22-0ubuntu1~ricotz1) seems to have fixed it, so I'll be the first to admit, it wasn't Pulse, it was Alsa itself... Here's the article I found: [http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html]("http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html")

Once I added that and the Pulse repo from the same ppa, I received a few updates, was still broke, but right after I posted this post as well as my blog post (and I'm talking within an hour or two of my postings) there was an update for Alsa to .22, I didn't get a chance to test until last night though, hence why I haven't posted until now.

I don't think it'd be great policy to encourage customers to use an unstable PPA, but it might be worth looking into for a "quick fix".

---

