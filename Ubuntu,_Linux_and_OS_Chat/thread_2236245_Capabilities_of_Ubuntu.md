---
title: "Capabilities of Ubuntu"
date: 2014-07-25
forum: Ubuntu, Linux and OS Chat
---

### Post by anon_private on 2014-07-25
Can Ubuntu (12.04.2) manage flash videos, mp4, mp3, gif, jpeg, png
Are there graphics editors available
Can TOR be installed

Is there a list of packages

Thanks

---

### Post by Bucky Ball on 2014-07-25
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. Please refer to the first link in my thread. Please research before posting. Thanks. For instance:

[https://duckduckgo.com/?q=graphics+editors+ubuntu](https://duckduckgo.com/?q=graphics+editors+ubuntu)

Tor, always check the repositories first. Software Centre. It's right there.

If you want a better look at the available packages, install Synaptic Package Manager (synaptic), if you haven't already got it installed.

Not sure how you intend to stay on 12.04.2 because it is at 12.04.4 and .5 shortly. Unless you are not going to update you are going there too. If you are still there, you are running a system that hasn't got the latest updates. But we are going in circles.

---

### Post by uRock on 2014-07-25
Yes, yes, and yes. 

I use all of those file formats on a regular basis.

I use GIMP for editing images. [http://www.gimp.org/](http://www.gimp.org/) GIMP can be installed easily via the Ubuntu Software Center.

I've downloaded and extracted TOR for use. Just download from [here]("https://www.torproject.org/projects/torbrowser.html.en"), extract it within the home directory, then start TOR using the following command in a terminal,```
./tor-browser_en-US/start-tor-browser
```

[Ubuntu Package Listings]("http://packages.ubuntu.com/")

I'd recommend ubuntu 14.04 over 12.04. You won't have to worry about upgrading until April 2019.

---

### Post by Bucky Ball on 2014-07-25
Tor is in the repositories. Unless there is a specific version you want/need there is no need to install manually.

PS: You summed it up a lot better than me, uRock. Cheers. ;)

---

### Post by uRock on 2014-07-25
> **Bucky Ball said:**
> Tor is in the repositories. Unless there is a specific version you want/need there is no need to install manually.

PS: You summed it up a lot better than me, uRock. Cheers. ;)

I started downloading it out of habit, due to their releasing a new version for Windows on a regular basis. :guitar:

---

### Post by stalkingwolf on 2014-07-26
for simple editing there is Pinta.  (think photo deluxe business edition)

---

### Post by Rob Sayer on 2014-07-31
Largely what the above said.  There are some support issues.  For example Google Chrome has more up to date flash support because they have an agreement with Adobe.  I actually use Chrome (not chromium) because I really dislike the newest firefox releases but support is also an issue.

Gimp is another example.  It'll be just fine for most people but it's not suitable for professionals who will publish their work.  The digital printers used by publishers use a proprietary file format that is not supported in linux and I don't expect this to change any time soon.  Also, Pantone color support is also a proprietary format unavailable in linux.  A friend of mine is a comic artist and this is the only reason he uses windows rather than linux.  Some people like him *need* Photoshop.

I've found the selection of video editors in linux to be a lot better than I expected.  There are some very good NLEs that are only available for linux like openshot and kdenlive.

However, when you're talking about .flv or .mp4 video remember those are just *containers*, which is different from video *formats*.  Most any non proprietary video format up to h.264 is quite well supported in linux, though you won't have any more luck with files from a PVR in linux than any other OS.  But I think it'll be a while until h.265 video has good support in open source software.  Same in Windows actually.

All of this type of thing is the only reason I still have one remaining windows 7 partition.  Though the only thing I really need it for is ripping a DVD to a VIDEO_TS folder.  There aren't any open source dvd rippers that can handle the newer DVD encryption schemes.  WINE isn't all that reliable for running windows apps in linux.

One thing mentioned I'd stress is to stick to the standard repos if at all possible.  I don't install from an external ppa unless I *really* want the software ... ie. it does something I can't do otherwise .... and I'm sure it's a safe source.  External ppa = ubuntu/Canonical does not support it.

The thing is, linux/ubuntu is quite stable and reliable (though there's oftemn more configuration involved than windows).  However, you can certainly make it unstable, and using unsupported ppas is a very good way to do so.

---

### Post by andrew.46 on 2014-09-19
> **Rob Sayer said:**
> .But I think it'll be a while until h.265 video has good support in open source software. 

*Widespread* support is certainly still lacking but both encoding and decoding are supported in the very newest FFmpeg and vlc, solid playback available from MPlayer and its associated guis such as SMPlayer...

---

