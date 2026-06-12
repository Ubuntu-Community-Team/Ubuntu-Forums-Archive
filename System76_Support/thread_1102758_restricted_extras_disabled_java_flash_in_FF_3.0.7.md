---
title: "restricted extras disabled java flash in FF 3.0.7"
date: 2009-03-22
forum: System76 Support
---

### Post by dreemeeper on 2009-03-22
hello
i'm somewhat new to ubuntu, and even newer to my gazelle ultra (gazu1)
i was reading here:
([http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)) because i wanted to install skype, and decided to add the restricted extras. 
i used synaptic though, because the add remove in applications said there was a conflict. so synaptic removed libavcodec51, then installed the restricted extras:
cabextract (1.2-3)
freepats (20060219-1)
gsfonts-x11 (0.20ubuntu1)
gstreamer0.10-plugins-bad (0.10.8-1)
gstreamer0.10-plugins-bad-multiverse (0.10.6-1ubuntu1)
gstreamer0.10-plugins-ugly-multiverse (0.10.7-2)
libavcodec-unstripped-51 (3:0.svn20080206-12ubuntu3+unstripped5)
libcdaudio1 (0.99.12p2-5)
libdc1394-22 (2.0.2-1)
libfaac0 (1.26-0.1ubuntu2)
libfaad0 (2.6.1-3.1)
libfftw3-3 (3.1.2-3.1ubuntu1)
libfreebob0 (1.0.11-0ubuntu1)
libgmyth0 (1:0.7.1-1)
libiptcdata0 (1.0.2+libtool01-2)
libjack0 (0.109.2-3ubuntu1)
libmjpegtools0c2a (1:1.8.0-0.2ubuntu5)
libmms0 (0.4-2)
libmp3lame0 (3.98-0.0)
libneon27-gnutls (0.28.2-2build1)
libofa0 (0.9.3-3)
libquicktime1 (2:1.0.2+debian-2build2)
libsoundtouch1c2 (1.3.1-2)
libswscale0 (3:0.svn20080206-12ubuntu3.1)
libwildmidi0 (0.2.2-2)
libx264-59 (1:0.svn20080408-0.0ubuntu1)
libxvidcore4 (2:1.1.2-0.1ubuntu3)
msttcorefonts (2.5)
odbcinst1debian1 (2.2.11-16build2)
sun-java6-bin (6-10-0ubuntu2)
sun-java6-jre (6-10-0ubuntu2)
ubuntu-restricted-extras (25)
unixodbc (2.2.11-16build2)
unrar (1:3.8.2-1)
xutils-dev (1:7.4+3)

before i did this, all flash and java seemed to work fine in firefox. now, neither of them work. before i proceed to blindly remove and add various flash and java plugins, i figured i would ask here for a little guidance or clarification.

also,for some reason my built in mike wont record in the default sound reorder app. is there a way to check the mike, or do i need an extra driver? btw- i did install the systm76 driver, and updated all system updates.

---

### Post by jjacobs2 on 2009-03-22
For the mic, did you go into volume controls and increase the microphone and/or capture levels to full?  Just be careful you don't get a bad echo in skype by doing both, it seems on some audio cards the correct one to adjust is switched but with intel audio it was the capture that needed to be raised on mine.

I don't think the removed libavcodec package is a problem as an unstripped one was installed.  The ubuntu version is limited intentionally because of licensing requirements for some codecs.

In firefox try going to preferences, applications, java web start application and see what it's using.  On mine it uses openJDK web start.

---

### Post by dreemeeper on 2009-03-22
> **jjacobs2 said:**
> For the mic, did you go into volume controls and increase the microphone and/or capture levels to full?  Just be careful you don't get a bad echo in skype by doing both, it seems on some audio cards the correct one to adjust is switched but with intel audio it was the capture that needed to be raised on mine.

I don't think the removed libavcodec package is a problem as an unstripped one was installed.  The ubuntu version is limited intentionally because of licensing requirements for some codecs.

In firefox try going to preferences, applications, java web start application and see what it's using.  On mine it uses openJDK web start.
i went into volume controls and turned all options on, and raised all the sliders, and the microphone is working fine now.
as far as my java/flash, after reading your post, i checked my firefox java appliction and there was none. so i re-installed all the jdk java packages:
```
sudo apt-get install --reinstall icedtea6-plugin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib

```
then restarted, and all seems well
the restricted extras must have changed something...
so both problems are now resolved,
thank you for your help

---

### Post by thomasaaron on 2009-03-23
OK. The reason you got the original conflict is that you can only have one package management program open at a time. If you have synaptic package manager open, for instance, you won't be able to run apt-get commands from the terminal or use Applications > Add/Remove Software.

---

