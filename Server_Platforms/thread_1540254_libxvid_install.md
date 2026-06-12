---
title: "libxvid install?"
date: 2010-07-27
forum: Server Platforms
---

### Post by fred2028 on 2010-07-27
I'm installing Clip Bucket and a encoder I need is libxvid. I tried installing the Xvid thing from [http://www.andresmontalban.com/how-to-install-clipbucket-requirements-on-redhat-enterprise-5-server-with-cpanel/](http://www.andresmontalban.com/how-to-install-clipbucket-requirements-on-redhat-enterprise-5-server-with-cpanel/) but doesn't work. How do I get the libxvid codec so I can convert AVIs?

---

### Post by Bachstelze on 2010-07-27
```
sudo apt-get install libxvidcore4
```

---

### Post by fred2028 on 2010-07-28
> **Bachstelze said:**
> ```
sudo apt-get install libxvidcore4
```
Just tried that and it says that I already have the newest version. I checked Clip-Bucket's server modules page again in the admin area and it still says libxvid (ffmpeg codec) not installed

---

### Post by FakeOutdoorsman on 2010-07-28
If Clip Bucket is using FFmpeg as an interface to *libxvid* (and you're using the repository FFmpeg), see options B or C in this guide:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by fred2028 on 2010-07-28
> **FakeOutdoorsman said:**
> If Clip Bucket is using FFmpeg as an interface to *libxvid* (and you're using the repository FFmpeg), see options B or C in this guide:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)
OK I actually got everything installed except MP4Box. I tried the tutorials online and I keep getting errors at the installation of
 
```
yum install zlib*
```
 
Says package not found or something ... How can I install MP4Box?

---

### Post by fred2028 on 2010-08-04
> **fred2028 said:**
> OK I actually got everything installed except MP4Box. I tried the tutorials online and I keep getting errors at the installation of
 
```
yum install zlib*
```
 
Says package not found or something ... How can I install MP4Box?
 Bump?

---

### Post by ruffEdgz on 2010-08-04
So I was following the steps from the link [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg]("http://www.andresmontalban.com/how-to-install-clipbucket-requirements-on-redhat-enterprise-5-server-with-cpanel/") and saw the error that you were probably at:
```

./configure &#8211;use-js=no
error: zlib not found on system or in local libs

```
So I installed all these libraries from the Ubuntu repo:
```

aptitude install zlib1g-dbg zlib1g-dev

```
You should have the package "zlib1g" installed on your server but if not, then make sure that is installed as well.

That should help you get past the part you were stuck at.

---

### Post by fred2028 on 2010-08-04
> **ruffEdgz said:**
> So I was following the steps from the link [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg]("http://www.andresmontalban.com/how-to-install-clipbucket-requirements-on-redhat-enterprise-5-server-with-cpanel/") and saw the error that you were probably at:
```

./configure &#8211;use-js=no
error: zlib not found on system or in local libs

```
So I installed all these libraries from the Ubuntu repo:
```

aptitude install zlib1g-dbg zlib1g-dev

```
You should have the package "zlib1g" installed on your server but if not, then make sure that is installed as well.

That should help you get past the part you were stuck at.

Thanks, I tried the aptitude install line and then re-did the MP4BOX section of the link I posted, but I still get the error. Attached is the error. I get it after the line
```
./configure &#8211;use-js=no
```
I believe. Running any of the commands following that line on the site given gives more errors.

---

### Post by fred2028 on 2010-08-04
> **fred2028 said:**
> Thanks, I tried the aptitude install line and then re-did the MP4BOX section of the link I posted, but I still get the error. Attached is the error. I get it after the line
```
./configure –use-js=no
```
I believe. Running any of the commands following that line on the site given gives more errors.

Wow, apparently this is solved with
```
sudo apt-get install gpac
```
SOlved

---

