---
title: "Going back to Flash 9"
date: 2009-08-09
forum: System76 Support
---

### Post by samalex on 2009-08-09
Hi,

When I got my PanP laptop a few days ago I noticed Flash didn't work, so I followed the System76 instructions to install Flash 10.  Doing this caused Firefox to close instantly on any Flash site, so I removed Flash and nwrapper (sp?) through Synaptic and reinstalled the ones that looked to come from the Ubuntu repositories.  Doing this allowed Flash sites to work, but some are really jerky specifically those on the Playhouse Disney site.

I right-clicked on a Flash video in hopes to change some settings, and it shows I still have Flash 10, which is Alpha I think.  

So can someone give pointers on what to uninstall and reinstall to downgrade to Flash 9 which is hopefully more stable?  Just checking.

Thanks,

Sam

---

### Post by samalex on 2009-08-09
Hey guys ...

Just a quick update, in Firefox under about:plugins here's what I have for Flash:
Shockwave Flash
File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 r32

And under Synaptic I have these installed related to Flash:
flashplugin-installer - 10.0.32.18ubuntu0.9.04.1

Do I have the most stable Flash plugin installed?  Now I'm having problems getting any Flash to work, whether Hulu, Youtube, etc.  Is it common to have issues with Flash?  Just checking... If need be I can install the one from the Adobe website, but how do I uninstall everthing that's installed?  With me starting a Biology class in two weeks where the labs are online via Flash I need to have a reliable Flash player.

Also and I don't know if this is Flash or something else, but I'm finding some pages just don't load correctly, for example [http://www.youtube.com/trailers](http://www.youtube.com/trailers) the center of the page where I assume the guts of the page should be is blank.  This may not be Flash, but can anyone else load this?

Another update..  Hulu and Youtube playing full screen is so jumpy it's not watchable.  I've updated to Firefox 3.5 using [these instructions]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html"), but it has the same effect with unwatchable full screen video and pages not loading correctly.  

Any ideas??  This is a showstopper for me if I can't resolve this.  Thanks ...

Sam

---

### Post by marshmallow1304 on 2009-08-09
Try the [64-bit version]("http://labs.adobe.com/downloads/flashplayer10.html") from the Adobe site.  First remove any flash packages, then copy libflashplayer.so from the Adobe download to ~/.mozilla/plugins/

---

### Post by jordansc on 2009-08-09
Here are the instructions supplied by Tom that worked well for me:

> 1. Shut down Firefox

2. Run the following commands from a terminal...

sudo apt-get remove flashplugin-*
sudo apt-get remove nspluginwrapper

3. Click the link at the very bottom of this page...
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
...to download the latest 64-bit Flash plugin. Save it to your Desktop and extract it to your Desktop.
Drag libflashplayer.so from the extracted folder onto your Desktop.

4. Run these commands from the terminal...
mkdir -p .mozilla/plugins
mv ~/Desktop/libflashplayer.so .mozilla/plugins

5. Restart Firefox


---

### Post by samalex on 2009-08-10
> Here are the instructions supplied by Tom that worked well for me:

I've tried these instructions, but after installing upon loading any Flash page (specifically tested Hulu and YouTube), Firefox just closes with no warning or error.  I had to remove the plugin and reinstall Flash from the repositories to get it working again.

As for the blah with Flash, last night I uninstalled Flash and Firefox through Synaptic and reinstalled, and now things are working better.  YouTube and Hulu both load good and Hulu thus far is playing full screen with only an occasional jitter, but it's plenty watchable.  I'm not sure what happened before or what was out of kilter.  The only thing that hoses Flash is going to uStream... any uStream video I guess crashes Flash and I have to close and reopen Firefox to get Flash to work again on any site.  

I did just read that the Alpha 64-bit version of Flash for Linux does not support the webcam yet, so I'll keep testing with the version that's in the Ubuntu repositories to see if I can get uStream or Stickam to work.  Flash does pick-up my camera through settings, so I'm keeping my fingers crossed :)

Sam

---

### Post by thomasaaron on 2009-08-10
If you decide you want to get flash 10 running, please run firefox from a terminal...

```
firefox
```

...and go to a flash page to crash it and let's see what errors it throws. I know that's not a problem across the board, so it may just be some conflict you have going on...

---

### Post by Ed.Corcoran on 2009-09-20
I've been trying out the most recent alpha of Flash 64, and I get the same errors listed here. I tried installing it back when I first got my Wild Dog, and was having trouble with that version to. Anyway, I've been experimenting with different flashes, as the one from the repos doesn't work consistently for me.

When Flash 64 crashes, the only thing that Firefox spits out at the terminal is "Segmentation Fault", which doesn't help much.

---

### Post by samalex on 2009-09-20
> **Ed.Corcoran said:**
> I've been trying out the most recent alpha of Flash 64, and I get the same errors listed here. I tried installing it back when I first got my Wild Dog, and was having trouble with that version to. Anyway, I've been experimenting with different flashes, as the one from the repos doesn't work consistently for me.

When Flash 64 crashes, the only thing that Firefox spits out at the terminal is "Segmentation Fault", which doesn't help much.

The "Segmentation Fault" error is exactly what I kept getting, so I just gave up and stuck with Flash 9.  The wrapper is buggy at times but it seems to work well.  I'll test 64-bit Flash 10 again when it's finally released or possible a beta or release candidate.

Sam

---

