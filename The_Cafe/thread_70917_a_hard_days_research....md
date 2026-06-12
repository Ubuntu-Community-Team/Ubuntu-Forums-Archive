---
title: "a hard days research..."
date: 2005-10-01
forum: The Cafe
---

### Post by urbandryad on 2005-10-01
I've downloaded files, and debian files, and all sorts of stuff that has been suggested for newbies on this page.

I've saved every last bit of text information relevant to said files, and pages that I've been referred to for installing programs.

Tonight...Gonna try to get Audacity running on my computer..without using synaptic. I'm crossing my fingers and praying for luck. That all will go well.

Oh, I saw the PERFECT book for me in the bookstore that I couldn't buy cause it was over $50 Canadian. The Ultimate Linux Bible. ^^ Urp. I WAANTED it. But I didn't know wether it was relevant to Ubuntu. Would the Debian Bible be better? Ahem.

Gonna also try to install EasyUbuntu. I've already got Debins. Now lets hope I can figure out how to get SUDO working with terminal from every help file I've  saved or this will be a short app install attempt indeed. XD

(well, that is, unless debins turns out to work after all)

---

### Post by urbandryad on 2005-10-02
hmm, no replies whatsoever.


I got Easy Ubuntu to install, though I think most of the support stuff DIDN'T install cause I don't have the internet. I need a vorbis codec if I want to convert my MP3's with audio converter, and the debian file I tried to install with debins was broken, so I need to figure out what to do, I don't have Breezy, don't need breezy, and the person doing Audacity is updating the bug only for the BREEZY version. Which sucks.

So I need an audio program OTHER THAN AUDACITY thats in a .deb format I can put on my computer to rip my CDs and play music. ^^ Sigh. I could stick with the default though.

Where do I find the vorbis codec? What about the MP3 codec? Can I install them without the net?

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=urbandryad]
So I need an audio program OTHER THAN AUDACITY thats in a .deb format I can put on my computer to rip my CDs and play music. ^^ Sigh. I could stick with the default though.
[/QUOTE]

Sound juicer, which was installed by default on my box, rips CDs to oggs and plays them.

If you need MP3 support, the only way is to download the software. Be it realplayer (the legal Linux mp3 player) or gstreamer-mad.

---

### Post by urbandryad on 2005-10-02
[QUOTE=poofyhairguy]Sound juicer, which was installed by default on my box, rips CDs to oggs and plays them.
If you need MP3 support, the only way is to download the software. Be it realplayer (the legal Linux mp3 player) or gstreamer-mad.[/QUOTE]


does realplayer support iPods?

Where do I get gstreamer-mad and how do I install it?

---

### Post by 23meg on 2005-10-02
for ipod support, get gtkpod by typing "sudo apt-get install gtkpod".

---

### Post by urbandryad on 2005-10-02
is gtkpod already a package on the system or is it on the net? I should put in my signiture that I can't connect to the internet with my Linux system.

^^;

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=urbandryad]does realplayer support iPods?
Where do I get gstreamer-mad and how do I install it?[/QUOTE]

Honestly if you want iPod support the only Linux program that does the job good enough for me is Amarok. But that is a KDE program, so it would be a slice of heck to install it without internet access.

There is also GTKPod, it works but is a little harder to set up. Since you lack internet, it will be the easiest choice:

[http://packages.ubuntu.com/hoary/sound/gtkpod](http://packages.ubuntu.com/hoary/sound/gtkpod)

[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad)

to install both things, you have to download each deb file and the packages that depend on that file (and the packages that depend on that file) and install them with:

sudo dpkg -i debfilename.deb

I must ask....if you lack interent access how do you plan to download and install anything? 

If I was you, and I lacked internet access, I wouldn't use Ubuntu. Mepis is a free (cept for shipping) OS that has MP3 and iPod support out of the box:

[http://store.mepis.com/home.php](http://store.mepis.com/home.php)

just some food for thought. Ubuntu really shines only with internet access.

---

