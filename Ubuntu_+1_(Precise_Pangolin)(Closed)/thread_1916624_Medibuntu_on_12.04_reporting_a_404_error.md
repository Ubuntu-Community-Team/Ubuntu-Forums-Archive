---
title: "Medibuntu on 12.04 reporting a 404 error"
date: 2012-01-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fballem on 2012-01-28
When I execute the following in a terminal:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

I am getting a 404 (not found) error. Could someone please tell me if the medibuntu repositories are getting updated.

Please note that I am running 12.04, which I know is in development, so it is reasonable to expect the odd problem.

Thanks,

---

### Post by bluexrider on 2012-01-28
Switch to a different mirror and try again

---

### Post by mdhollis on 2012-01-28
What if you edit the source to oneiric?

---

### Post by fballem on 2012-01-28
Wouldn't the oneric versions of the programs cause a problem with the precise installation?

---

### Post by mdhollis on 2012-01-28
I haven't had any issue.  I hear what your saying but 11.10 and 12.04 are both gtk3 so..............

---

### Post by fballem on 2012-01-28
I'll wait for a little bit and try again. If not, then I may install the oneric.

How would I edit my command to install oneric in case I decide to try it?

Thanks,

---

### Post by mdhollis on 2012-01-28
I usually use synaptic to edit repositories.  I'm not sure how you would do it via the terminal......

In synaptic,  settings -> repositories

---

### Post by mc4man on 2012-01-28
What is it that you want from medibuntu? Only a few of the packages will be installable on 12.04, for those you could just as well dl directly & install with gdebi
[http://packages.medibuntu.org/oneiric/index.html](http://packages.medibuntu.org/oneiric/index.html)

---

### Post by mdhollis on 2012-01-28
> **mc4man said:**
> What is it that you want from medibuntu? Only a few of the packages will be installable on 12.04, for those you could just as well dl directly & install with gdebi
[http://packages.medibuntu.org/oneiric/index.html](http://packages.medibuntu.org/oneiric/index.html)

I would listen to mc4man.............lol!

---

### Post by fballem on 2012-01-28
Thanks - I will. I am looking for the w64codecs and the microsoft fonts. I also want skype, even though it is the crap version.

---

### Post by zika on 2012-01-28
> **mdhollis said:**
> I usually use synaptic to edit repositories.  I'm not sure how you would do it via the terminal......

In synaptic,  settings -> repositories```
sudo nano /etc/apt/sources.list.d/medibuntu.list
```to make it look like:
```
:~$ cat /etc/apt/sources.list.d/medibuntu.list
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ oneiric free non-free
# deb http://packages.medibuntu.org/ precise free non-free
# deb-src http://packages.medibuntu.org/ precise free non-free
```

---

### Post by coffeecat on 2012-01-28
> **fballem said:**
> I am looking for the w64codecs and the microsoft fonts.

For microsoft fonts, you don't need medibuntu. The package ttf-mscorefonts-installer is in the multiverse repository. Multiverse should be enabled already for you.

---

### Post by mc4man on 2012-01-28
> **fballem said:**
> Thanks - I will. I am looking for the w64codecs and the microsoft fonts. I also want skype, even though it is the crap version.

w64codecs is a tiny hair above completely worthless, contains 3 or files, two of which are handled thru libav (the FFmpeg breakaway that Debian is now using), the other quite obscure.

Edit- actually I'd call completely worthless
> ~/Downloads/w64codecs_20071007-0medibuntu2_amd64/usr/lib/codecs$ ls
cook.so  drvc.so  sipr.so


---

### Post by dino99 on 2012-01-28
medibuntu is quite useless nowadays and is only set on stable release. Note that Precise have moved to multiarch, so medibuntu is a old story now.

---

### Post by cariboo on 2012-01-28
The only thing I get from Medibuntu is libdvdcss2, and I use the script in usr/share/doc/libdvdread4 to install it. Vobcopy still needs the library.

---

### Post by mc4man on 2012-01-28
At PP release or there-abouts Medibuntu can also provide aac encoding thru libavcodecXX which due to licensing is not in the ubuntu proper.

Side note -  Ubuntu/Debian, which is using the the Libav version of 'FFmpeg' will now be advising use of 'avconv <whatever>' instead of 'ffmpeg <whatever> though continues for a bit to accept the ffmpeg command & will present a somewhat misleading/untrue message (a bit childish perhaps

> $ ffmpeg
ffmpeg version 0.8-4:0.8-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Jan 24 2012 07:22:02 with gcc 4.6.2
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).


---

### Post by mr_pouit on 2012-01-29
For development releases, Medibuntu's repositories aren't usually available before the feature freeze…

> **dino99 said:**
> Note that Precise have moved to multiarch, so medibuntu is a old story now.

Uh? Medibuntu and multiarch are completely unrelated.

---

### Post by fballem on 2012-01-30
> **cariboo907 said:**
> The only thing I get from Medibuntu is libdvdcss2, and I use the script in usr/share/doc/libdvdread4 to install it. Vobcopy still needs the library.

So how do I get the libdvdcss2 without Medibuntu? Does the script still exist (and still install it) if Medibuntu is not there. I think I need that library to play DVDs.

---

### Post by zika on 2012-01-30
> **fballem said:**
> So how do I get the libdvdcss2 without Medibuntu? Does the script still exist (and still install it) if Medibuntu is not there. I think I need that library to play DVDs.I've wrote to You how to enable Oneiric branch from Medinutnu in Precise...
Package You're looking for is in Medibuntu, Oneiric branch: [http://packages.medibuntu.org/oneiric/libdvdcss2.html](http://packages.medibuntu.org/oneiric/libdvdcss2.html)
You always can DL it and install using whatever method You prefer gdebi, dpkg, SoftwareCenter... Pick Your favorite...
No sweat...
(As I can see You're on Natty...?)

---

### Post by cariboo on 2012-01-30
> **fballem said:**
> So how do I get the libdvdcss2 without Medibuntu? Does the script still exist (and still install it) if Medibuntu is not there. I think I need that library to play DVDs.

You can go directly to the [Medibuntu]("http://packages.medibuntu.org/oneiric/index.html") website and download libdvdcss2 for Oneiric, it works as expected.

---

### Post by fballem on 2012-01-31
> **zika said:**
> I've wrote to You how to enable Oneiric branch from Medinutnu in Precise...
Package You're looking for is in Medibuntu, Oneiric branch: [http://packages.medibuntu.org/oneiric/libdvdcss2.html](http://packages.medibuntu.org/oneiric/libdvdcss2.html)
You always can DL it and install using whatever method You prefer gdebi, dpkg, SoftwareCenter... Pick Your favorite...
No sweat...
(As I can see You're on Natty...?)

Thanks for reminding me that I needed to update my profile.

---

### Post by VMC on 2012-03-07
> **cariboo907 said:**
> The only thing I get from Medibuntu is libdvdcss2, and I use the script in usr/share/doc/libdvdread4 to install it. Vobcopy still needs the library.

Thanks. This is exactly what I use. vobcopy & libdvdread. 
that css shell file works. I missed it somehow on first go around.

---

