---
title: "Problem with Unity Tweak Tool"
date: 2014-02-16
forum: Ubuntu Development Version
---

### Post by jerrynewt on 2014-02-16
Tried opening the Unity Tweak Tool but was advised the following Schema is missing "com.canonical.notify-osd", and to install needed packages. Any ideas where to start ??
Running fresh install of 14.04 with apt-get update, upgrade and dist-upgrade as of ten minutes ago.

---

### Post by cariboo on 2014-02-17
What packages, did it tell you install?

---

### Post by jerrynewt on 2014-02-17
That is all the message said. No reference to what packages to install.

---

### Post by PJs Ronin on 2014-02-17
Try searching in Synaptic for notify-osd.   If notify-osd is not installed, install.   Or from CLI: ```
sudo apt-get install notify-osd
```

---

### Post by fjgaude on 2014-02-18
Notice you are on 13.10... Tweak never worked on 13.10, at least not for me. It was working on 14.04 up until a day or so ago. Not now. I trust the guys will fix it at least for 14.04, but hopefully for everything since 12.04.

---

### Post by xc3RnbFO8P on 2014-02-18
Here is a bugreport [https://bugs.launchpad.net/ubuntu/+source/unity-tweak-tool/+bug/1281464]("https://bugs.launchpad.net/ubuntu/+source/unity-tweak-tool/+bug/1281464")

---

### Post by fjgaude on 2014-02-19
I'm sure it will be fixed in a timely manner!

---

### Post by Mateusz Stachowski on 2014-02-19
There is also this bug report [https://bugs.launchpad.net/unity-tweak-tool/+bug/1281467](https://bugs.launchpad.net/unity-tweak-tool/+bug/1281467)

---

### Post by rrnbtter on 2014-02-20
Greetings,
I have been sending bug reports on this utility. There is a new PPA plus a downloadable .deb file version 0.0.7. The new version did not work on my system but you may have some success. It has had both positive and negative reports. I used Gdebi to install the .deb. Gdebi will notify of a earlier version which you can override.
PPA location : [https://launchpad.net/~freyja-dev/+archive/unity-tweak-tool-daily](https://launchpad.net/~freyja-dev/+archive/unity-tweak-tool-daily)

---

### Post by Alan F on 2014-02-21
Version 0.0.6ubuntu1 available now in the repos resolves the crash that prevented unity-tweak-tool 0.0.6 from running but at least 2 bugs with it remain

1  The launcher icons can only be reduced to 32 pixels whereas in System Settings these can be reduced to 16 pixels
2  The Windows Controls left/right setting has no effect.

---

### Post by rrnbtter on 2014-02-21
Greetings,
Well, I finally got this working!


sudo apt-get purge unity-tweak-tool
remove ppa if installed in repository
delete the contents of "var/cache/apt/archives/"
sudo apt-get update
sudo apt-get dist-upgrade
install unity-tweak-tool from Software Center

Works fine except with bugs listed in post #10

---

### Post by xc3RnbFO8P on 2014-02-23
Working after last update.

[[img]http://farm6.staticflickr.com/5483/12731720223_55ae8f4eb7_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12731720223/)
[Screenshot from 2014-02-23 23:30:03](http://www.flickr.com/photos/96052779@N07/12731720223/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by jerrynewt on 2014-02-24
Followed your instructions, but still get message saying "com.canonical.desktop.interface" Schema is not installed, and to install the necessary packages. Still no joy. Just did update and dist-upgrade thirty minutes ago.

---

### Post by kaweka on 2014-12-13
Hi guys, it's December '14, nearly one year after jerrynewt first report and the problem still present on fresh Ubuntu and UTT installation.
What's the current status? The bug reports referred to in this thread do not address exact the problem here, in both cases at least slight 
deviation from the report here.
Why is the Ubuntu world so crazy? I mean the Apps Center is provided in OS gui anyhow all are managing their software 
by apt-get. Or yet worser as here in this thread a procedure with a mix of apt-get and Ubunt Apps Center usage.

I decided to got rid of UTT.

---

### Post by cariboo on 2014-12-13
What does this have to do with Vivid?

---

### Post by Vesnog on 2015-01-03
> **kaweka said:**
> Hi guys, it's December '14, nearly one year after jerrynewt first report and the problem still present on fresh Ubuntu and UTT installation.
What's the current status? The bug reports referred to in this thread do not address exact the problem here, in both cases at least slight 
deviation from the report here.
Why is the Ubuntu world so crazy? I mean the Apps Center is provided in OS gui anyhow all are managing their software 
by apt-get. Or yet worser as here in this thread a procedure with a mix of apt-get and Ubunt Apps Center usage.

I decided to got rid of UTT.

The problem persists with the **UTT **from the default repository, you can use the following **PPA **to have a working(at least partially) UTT:

[HTML]https://launchpad.net/~freyja-dev/+archive/ubuntu/unity-tweak-tool-daily
[/HTML]

Do as follows to remove the previous UTT together with its configurations files and then install the new version available throught the PPA described above:

```
sudo apt-get purge unity-tweak-tool
sudo add-apt-repository ppa:freyja-dev/unity-tweak-tool-daily
sudo apt-get update
sudo apt-get install unity-tweak-tool
```

After these steps I got it working, and it seemed to work fine apart from changing desktop icons(placing trash bin etc. on desktop). Hope this helps with your case, let us know if you try it.

---

### Post by zika on 2015-01-04
> **cariboo907 said:**
> What does this have to do with Vivid?Nothing since PPA mentioned (in HTML-code-tags ?) does not even have Utopic branch, let alone Vivid... ;)

---

### Post by cariboo on 2015-01-04
> **zika said:**
> Nothing since PPA mentioned (in HTML-code-tags ?) does not even have Utopic branch, let alone Vivid... ;)

That's what I thought. Thread closed as it has nothing to do with Vivid testing or dicussion.

---

