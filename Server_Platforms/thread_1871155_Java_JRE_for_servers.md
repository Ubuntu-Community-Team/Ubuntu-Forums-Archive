---
title: "Java JRE for servers?"
date: 2011-10-28
forum: Server Platforms
---

### Post by mattlach on 2011-10-28
Hey,

So I am installing some software to my server (64bit 11.10) that requires a 32bit java JRE in order to function.

I thought this would just be a matter of running the following command:

"sudo apt-get install openjdk-7-jre"

but this package seems to depend on A LOT of stuff I really don't want, like X11-common, GTK libs, asound, etc. etc.

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  ca-certificates-java default-jre default-jre-headless defoma fontconfig
  hicolor-icon-theme icedtea-6-jre-cacao icedtea-6-jre-jamvm
  icedtea-7-jre-jamvm icedtea-netx java-common libaccess-bridge-java
  libaccess-bridge-java-jni libasound2 libasyncns0 libatk1.0-0 libatk1.0-data
  libdatrie1 libflac8 libfontenc1 libgdk-pixbuf2.0-0 libgif4 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjasper1 libjpeg62 libjson0 liblcms1
  liblcms2-2 libnspr4 libnss3 libnss3-1d libogg0 libpango1.0-0 libpulse0
  libsndfile1 libthai-data libthai0 libtiff4 libvorbis0a libvorbisenc2
  libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6
  libxinerama1 libxrandr2 libxtst6 openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib openjdk-7-jre-headless openjdk-7-jre-lib shared-mime-info
  ttf-dejavu-extra tzdata-java x-ttcidfont-conf x11-common xfonts-encodings
  xfonts-utils
Suggested packages:
  defoma-doc psfontmgr libfont-freetype-perl equivs libasound2-plugins
  libasound2-python librsvg2-common gvfs libjasper-runtime liblcms-utils
  liblcms2-utils ttf-japanese-gothic ttf-japanese-mincho ttf-thryomanes
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp pulseaudio icedtea-plugin libnss-mdns sun-java6-fonts
  ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho
  ttf-wqy-microhei ttf-wqy-zenhei ttf-indic-fonts-core ttf-telugu-fonts
  ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts icedtea6-plugin
The following NEW packages will be installed:
  ca-certificates-java default-jre default-jre-headless defoma fontconfig
  hicolor-icon-theme icedtea-6-jre-cacao icedtea-6-jre-jamvm
  icedtea-7-jre-jamvm icedtea-netx java-common libaccess-bridge-java
  libaccess-bridge-java-jni libasound2 libasyncns0 libatk1.0-0 libatk1.0-data
  libdatrie1 libflac8 libfontenc1 libgdk-pixbuf2.0-0 libgif4 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libjasper1 libjpeg62 libjson0 liblcms1
  liblcms2-2 libnspr4 libnss3 libnss3-1d libogg0 libpango1.0-0 libpulse0
  libsndfile1 libthai-data libthai0 libtiff4 libvorbis0a libvorbisenc2
  libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6
  libxinerama1 libxrandr2 libxtst6 openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib
  shared-mime-info ttf-dejavu-extra tzdata-java x-ttcidfont-conf x11-common
  xfonts-encodings xfonts-utils
0 upgraded, 65 newly installed, 0 to remove and 0 not upgraded.
Need to get 79.2 MB of archives.
After this operation, 228 MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

What is the best way to get a JRE running on my server without pulling in all this junk I don't want running on it?

Much appreciated.

--Matt

---

### Post by lykwydchykyn on 2011-10-28
I think installing openjdk-7-jre-headless will get rid of most of those dependencies.  As far as supporting 32 bit on a 64 bit machine, I'm still really confused about the new multiarch thing myself.

---

### Post by mattlach on 2011-10-28
> **lykwydchykyn said:**
> I think installing openjdk-7-jre-headless will get rid of most of those dependencies.  As far as supporting 32 bit on a 64 bit machine, I'm still really confused about the new multiarch thing myself.

Excellent.   That did it.

It seems I need ia32-libs as well.

I can't seem to find a headless version of this.   Do you know if there is one?

---

### Post by lykwydchykyn on 2011-10-28
> **mattlach said:**
> Excellent.   That did it.

It seems I need ia32-libs as well.

I can't seem to find a headless version of this.   Do you know if there is one?

That's what I'm still struggling with myself. There used to be a separate ia32 compatibility package, but multiarch is supposed to do away with that. 

I asked how to get 32bit java on 64bit ubuntu here a few days ago, but didn't get an answer.  I suppose you can just download java 7 from Oracle and manually extract it, but I haven't tried that yet; I just kept my Natty packages for now.

---

### Post by mattlach on 2011-10-28
> **lykwydchykyn said:**
> That's what I'm still struggling with myself. There used to be a separate ia32 compatibility package, but multiarch is supposed to do away with that. 

I asked how to get 32bit java on 64bit ubuntu here a few days ago, but didn't get an answer.  I suppose you can just download java 7 from Oracle and manually extract it, but I haven't tried that yet; I just kept my Natty packages for now.

Well,   I just started executing the software I need to run, and noting down what it complained about when crashing.

Thus far I have installed the following packages:
libc-i386
lib32gcc1

Now its complaining about NatvieIO, which - based on my googling - appears to be a java issue.   I guess this means the 64bit openjdk-7-jre didn't do the trick.   There does not look to be a 32bit JRE in the repositories to replace it with.

[This site](http://www.ubuntugeek.com/install-jre-on-ubuntu-11-10-oneiric.html) appears to have a desription on how to do it (at least I presume sun-java6-jre is 32 bit), but I have no idea who roberto ferram is, or if it is save to add his repository...

*edit:*
It appears he is someone named Roberto Ferramosca, and is somewhat active in the linux community.

I still do not like trusting third party repositories...

---

### Post by bandyo on 2011-10-28
I want to install 32bit sun java on 64bit 11.10 Ubuntu as well. 

So far I haven't found the right command. It looks like the ia32 package is not there any more. I have got the PPA and 64bit sun java working, but how do I get 32bit java?

Thanks

Bandyo

---

