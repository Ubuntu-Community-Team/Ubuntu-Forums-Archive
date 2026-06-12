---
title: "does adding these codecs make me unsafe ?"
date: 2019-08-10
forum: Security
---

### Post by jedi123 on 2019-08-10
Hi I addded some codecs andI just want toknwo whether it makes me unsafe in any way ? 

wasn't there a problem with vlc using old codecs that caused a vulnerability  ?


 
 
 sudo apt install  chromium-codecs-ffmpeg-extra gstreamer1.0-fluendo-mp3 gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly lame libavcodec-extra libdvdread4

---

### Post by Shibblet on 2019-08-12
> **jedi123 said:**
> Hi I addded some codecs andI just want toknwo whether it makes me unsafe in any way ? 

wasn't there a problem with vlc using old codecs that caused a vulnerability  ?


 
 
 sudo apt install  chromium-codecs-ffmpeg-extra gstreamer1.0-fluendo-mp3 gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly lame libavcodec-extra libdvdread4

I don't think they're "unsafe."  They're just not "free" or "open source" software.  That's why they are not included by default.

---

### Post by helicase on 2019-08-12
libdvdread4 is not a codec; it's used to decrypt DVDs. It may be illegal in some countries:
[https://wiki.videolan.org/Frequently_Asked_Questions/#Is_libdvdcss_legal.3F](https://wiki.videolan.org/Frequently_Asked_Questions/#Is_libdvdcss_legal.3F)

---

### Post by uRock on 2019-08-12
> **helicase said:**
> libdvdread4 is not a codec; it's used to decrypt DVDs. It may be illegal in some countries:
[https://wiki.videolan.org/Frequently_Asked_Questions/#Is_libdvdcss_legal.3F](https://wiki.videolan.org/Frequently_Asked_Questions/#Is_libdvdcss_legal.3F)

aka codecs to the average user. Encryption itself is supposedly illegal to share with certain countries.

@OP I have yet to see a case where a system has been compromised with those softwares.

---

### Post by Frogs Hair on 2019-08-12
> [COLOR=#000000]*may be illegal in some countries*[/COLOR]

Those who provide the packages are not lawyers so it is up to the end user to abide by the laws in their own country or not. I've never experienced a compromised or broken system by installing codec packages. They are also non-free as stated in post 2.

---

### Post by SeijiSensei on 2019-08-13
In the US "circumvention" of software protections for copyrighted material is illegal under the Digital Millennium Copyright Act. 

>  The DMCA prohibits circumventing access-control measures. 17 U.S.C. § 1201(a)(1). For example, if you cannot watch a particular copyrighted DVD on your laptop because of an encryption system, the DMCA makes it unlawful for you to bypass this access-control measure. 

[http://www.dmlp.org/legal-guide/circumventing-copyright-controls](http://www.dmlp.org/legal-guide/circumventing-copyright-controls)

As a practical matter, no one will prosecute you for watching a movie on your computer using libdvdread4.

That said, this thread is bumping up against the [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules").

---

### Post by Frogs Hair on 2019-08-13
The OP is a question regarding system vulnerabilities related to installing codecs and not about violating TOS or EULA in various countries.

---

### Post by SeijiSensei on 2019-08-13
Thanks!

BTW, I've always preferred the combination of SMPlayer and mpv over any other media player.  No other codecs needed for most anything you would want to play.

```
sudo apt install smplayer mpv
```

---

### Post by cruzer001 on 2019-08-13
I think the codecs in the ubuntu repositories are older at times but always receive security updates.  Not a worry IMO.

I show chromium/ffmpeg codecs already installed, must be part of the restricted-extra package.  I do have the browser installed, maybe that brought it in.  I have not yet installed any "M" media players on this one, so not the reason.

There are several nice players that are built on mplayer and there is talk of mplayer being discontinued.  I wonder what that will do to M base players and their security.

---

### Post by uRock on 2019-08-13
VLC has always done the trick for me. It has been my go to player for years.

---

### Post by SeijiSensei on 2019-08-14
> **cruzer001 said:**
> 
There are several nice players that are built on mplayer and there is talk of mplayer being discontinued.  I wonder what that will do to M base players and their security.

I believe mpv is the main successor to mplayer. It's in current development.

> mpv is a fork of mplayer2 and MPlayer. It shares some features with the former projects while introducing many more. 

[https://mpv.io/](https://mpv.io/)

---

### Post by cruzer001 on 2019-08-14
Nothing wrong with MPV, I dare say its the better choice :)

---

