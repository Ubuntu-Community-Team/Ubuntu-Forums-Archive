---
title: "Eurosport on Ubuntu"
date: 2009-11-01
forum: The Cafe
---

### Post by GreenDance on 2009-11-01
Hi, I would like to watch [Eurosport Player]("http://video.eurosport.co.uk/eurosport-player/subscription.shtml") on Ubuntu 9.10, but the player doesn't load, I've tried installing VLC but the Eurosport Player still wont load,

---

### Post by Pasdar on 2009-11-01
It loads for me... have you installed the restricted extras and w32codecs?

---

### Post by GreenDance on 2009-11-01
> **Pasdar said:**
> It loads for me... have you installed the restricted extras and w32codecs?

no, how do i install them please?

---

### Post by speedwell68 on 2009-11-01
> **GreenDance said:**
> no, how do i install them please?

```
sudo apt-get install ubuntu-restricted-extras
```

and

```
sudo apt-get install w32codecs
```

---

### Post by Pasdar on 2009-11-01
w32codecs are not in the Ubuntu repositories (legal reasons). Install the package, "ubuntu-restricted-extras" and follow the following steps for w32codecs:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-9-10-karmic.html)

---

### Post by speedwell68 on 2009-11-01
> **Pasdar said:**
> w32codecs are not in the Ubuntu repositories (legal reasons). Install the package, "ubuntu-restricted-extras" and follow the following steps for w32codecs:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-9-10-karmic.html)

Good point I forgot that I had to add the medibuntu repository.

---

### Post by GreenDance on 2009-11-01
Strange, it still isn't working for me

---

### Post by GreenDance on 2009-11-01
I would really like to watch eurosport :)

*bump*

---

### Post by Pasdar on 2009-11-01
> **GreenDance said:**
> I would really like to watch eurosport :)

*bump*

How about you type the following commands in terminal:
```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
```

In Ubuntu:
```
sudo apt-get install gnome-mplayer gecko-mediaplayer
```

or Kubuntu:
```
sudo apt-get install kmplayer gecko-mediaplayer
```

You should close/restart your browser.

---

### Post by GreenDance on 2009-11-02
> **Pasdar said:**
> How about you type the following commands in terminal:
```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
```

In Ubuntu:
```
sudo apt-get install gnome-mplayer gecko-mediaplayer
```

or Kubuntu:
```
sudo apt-get install kmplayer gecko-mediaplayer
```

You should close/restart your browser.

Hi, I've followed the steps, now when I go to the eurosport website firefox crashes :(

---

### Post by Pasdar on 2009-11-02
> **GreenDance said:**
> Hi, I've followed the steps, now when I go to the eurosport website firefox crashes :(
Yesterday I tried it in Chromium, but now I tried it in firefox to see... and that crashes for me to. Do you have any other browsers? Either way, you can undo what you did by uninstalling,

```
sudo apt-get remove gnome-mplayer gecko-mediaplayer
```

And how about you only try VLC and its plugin:

```
sudo apt-get install vlc mozilla-plugin-vlc
```

btw if these codes are confusing to you or whatever you can also install the packages via synaptic installer... whichever is easier for you... commands are just easier because your can install/uninstall many things together...

---

### Post by GreenDance on 2009-11-02
> **Pasdar said:**
> Yesterday I tried it in Chromium, but now I tried it in firefox to see... and that crashes for me to. Do you have any other browsers? Either way, you can undo what you did by uninstalling,

```
sudo apt-get remove gnome-mplayer gecko-mediaplayer
```

And how about you only try VLC and its plugin:

```
sudo apt-get install vlc mozilla-plugin-vlc
```

btw if these codes are confusing to you or whatever you can also install the packages via synaptic installer... whichever is easier for you... commands are just easier because your can install/uninstall many things together...

hi, i'm running on a fresh install of U9.10, I've installed VLC & it's plugin and still the eurosport player isn't working.

---

### Post by Pasdar on 2009-11-02
> **GreenDance said:**
> hi, i'm running on a fresh install of U9.10, I've installed VLC & it's plugin and still the eurosport player isn't working.
very strange, did you again install the w32codecs and the ubuntu restricted extras?

---

### Post by GreenDance on 2009-11-02
> **Pasdar said:**
> very strange, did you again install the w32codecs and the ubuntu restricted extras?

command line says their already installed

---

### Post by Pasdar on 2009-11-02
Could you give me a link again to a video.. the link in your first post is not available... you could also right click, check source of the page to grab a direct link to the video and play that in VLC, that always works.

---

### Post by GreenDance on 2009-11-02
I've reinstalled Ubuntu 9.10, and VLC, the URL from the eurosport website, mms://vodstream.eurosport.com/nogeo/test/test.wmv works in VLC, the default player on firefox seems to be totem, maybe their is a bug somewhere?

---

### Post by GreenDance on 2009-11-02
I've spent an hour fiddling around with settings and still doesn't work through firefox, so plugins for firefox must be buggy

---

### Post by GreenDance on 2009-11-04
Does anyone have any suggestions please?

---

### Post by elqbenzo on 2010-03-29
solution: you have to "spoof" = change the User-Agent header your browser uses from "Mozilla" to "Internet Explorer 6"; worked for me (this is because JavaScript code on the Eurosport pages check the browser string and refuses to work with Mozillas)

---

### Post by Swagman on 2010-03-29
I'm using a raw live usb of 64 bit Lucid with restricted extras and flash installed and your link works perfectly (apart from no sound but that's a known lucid bug(dummy output))

The prefs in Firefox have not been altered in any way so you certainly don't need to spoof any other browser.

[** ScreenGrab**]( http://www.upload3r.com/serve/290310/1269858382.png)

---

### Post by scouser73 on 2010-03-29
> **Swagman said:**
> I'm using a raw live usb of 64 bit Lucid with restricted extras and flash installed and your link works perfectly (apart from no sound but that's a known lucid bug(dummy output))

The prefs in Firefox have not been altered in any way so you certainly don't need to spoof any other browser.

[** ScreenGrab**]( http://www.upload3r.com/serve/290310/1269858382.png)

I've just looked on the Eurosport website, and the volume is automatically set to mute, but can be turned up by the viewer.

---

### Post by Dagama on 2010-05-21
If, for some reason, you can't get the plugin to work, you can find the stream itself in the page source: 


[LIST=1]
[*]Log in to the Eurosport player site, and go to some channel. Set the resolution you want.
[*]View the page source, and search for the term: objectPlayer+='<param  name="URL" value="
[*]Copy the part between the " ". It is fairly long, and the start should look something like: mms://livestream-player.eurosport.com/nogeo/console......
[*]Stream through a media player
[LIST=1]
[*]If you want to start it through the terminal you need to change the part with _! to _\!
[/LIST]
 
[/LIST]
Translated from [http://happymtb.org/forum/read.php/1/1126840](http://happymtb.org/forum/read.php/1/1126840)

---

### Post by Tricast on 2010-05-23
I found this tutorial and script for opening eurosport player mms streams in your preferred video player, [http://www.m0sand.com/henningms/?p=58](http://www.m0sand.com/henningms/?p=58).

With some simple modifications like adding a wildcard and changing location (.com to .se), i now with a single extra mouse click can open all streams (live and archive) with my beloved vlc player.

See added screenshot where new link appears.

---

