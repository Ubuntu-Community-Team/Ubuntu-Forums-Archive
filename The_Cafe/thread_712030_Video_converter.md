---
title: "Video converter"
date: 2008-03-01
forum: The Cafe
---

### Post by rasmus91 on 2008-03-01
Hey.

I am the owner of a PSP. as many (properly everybody) knows, the video files it can play are named .mp4... I'll make it short: does any of you guys know a video converter for Linux (Ubuntu) that can convert from DVD movies to .mp4 file formats?

(i already tried in windows.... it told me i had to download an additional package, i did so, and then it just told me that it couldn't read the files on the DVD.... PS: the DVD is my own original)

---

### Post by -Phi- on 2008-03-01
I don't know if iPod video is the same as PSP video, but I used this wiki article: [https://help.ubuntu.com/community/iPodVideo](https://help.ubuntu.com/community/iPodVideo) to install ffmpeg (for another use entirely), and it might work for your uses too? The wiki also has a link to something about DVD rips and encoding which might be helpful.

Good Luck!

- Phi

---

### Post by xc3RnbFO8P on 2008-03-01
You can use Avidemux:

Auto PSP (H 264)

Be sure you got all codec installed

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by HermanAB on 2008-03-01
Avidemux + restricted codecs.

---

### Post by rasmus91 on 2008-03-01
aft6er i installed it i cant open it.... where how should i do? (there is no launcher app... :()

---

### Post by xc3RnbFO8P on 2008-03-01
Avidemux? How did you install it?

---

### Post by lingnoi on 2008-03-01
applications -> add/remove and search for Avidemux  :roll:

---

### Post by xc3RnbFO8P on 2008-03-02
Try this:

[http://www.getdeb.net/release.php?id=2178]("http://www.getdeb.net/release.php?id=2178")

---

### Post by buildid on 2008-03-02
In case you are in need of an conversion tool , there is an killer script online :

[http://h264enc.sourceforge.net/index.html]("http://h264enc.sourceforge.net/index.html")

this script can convert to :

 ivp -----> Apple iPod Video Profile (iVP) preset
            ihqvp ---> Apple iPod High-Quality Video Profile (iHQVP) preset
            ipvp ----> Apple iPhone Video Profile (iPVP) preset
            iphqvp --> Apple iPhone High-Quality Video Profile (iPHQVP) preset
            avp -----> AppleTV Video Profile (AVP) preset
            ahqvp ---> AppleTV High-Quality Video Profile (AHQVP) preset
            nkvp ----> Nokia S60 Video Profile (NKVP) preset
            nkhqvp --> Nokia S60 High-Quality Video Profile (NKHQVP) preset
            pspvp ---> Sony PSP Video Profile (PSPVP) preset
            psphqvp -> Sony PSP High-Quality Video Profile (PSPHQVP) preset
            ps3vp ---> Sony PS3 Video Profile (PS3VP) preset
            ps3hqvp -> Sony PS3 High-Quality Video Profile (PS3HQVP) preset
            zvp -----> MS Zune Video Profile (ZVP) preset
            zhqvp ---> MS Zune High-Quality Video Profile (ZHQVP) preset
            xvp -----> MS XBOX 360 Video Profile (XVP) preset
            xhqvp ---> MS XBOX 360 High-Quality Video Profile (XHQVP) preset


iam using the ipod settings for my nano and this well give me an working file for my ipod nano with video .

so you can convert an :

DVD to MP4
ISO to MP4
Video_TS folder to MP4
avi file to MP4

I have done all and it does work .......

---

### Post by marcusfurius on 2008-03-03
For whatever reason, legal or otherwise, Ubuntu comes with a cut down feature restricted version of ffmpeg which cannot, for example, convert videos to iPod or Sony PSP formats. You can, however, download a fixed version of ffmpeg for ubuntu at [http://www.marcus-furius.com/?p=5](http://www.marcus-furius.com/?p=5). 
This has been compiled with all the extra codecs needed for iPod and PSP. You can then use the simple video converter wizard available from [http://www.marcus-furius.com//?page_id=6](http://www.marcus-furius.com//?page_id=6) to convert your videos. All you need to do is supply the wizard with the name of your source file, the name you wish to give your output and whether you wish to convert to iPod, PSP or mobile phone format.

---

### Post by billgoldberg on 2008-03-03
Winff can convert dvd's to psp xvid

winff can be downloaded here:

[http://biggmatt.com/winff/downloads/winff-version-0.33.html](http://biggmatt.com/winff/downloads/winff-version-0.33.html)

(it's a .deb package)

---

### Post by _Phil on 2008-03-04
I use PSPVC (PSP Video Converter)
its very usefull, you can select from different profiles, queue movies to convert etc. 

[http://prdownloads.sourceforge.net/pspvc/pspvc-install-0.3.tar.gz?download](http://prdownloads.sourceforge.net/pspvc/pspvc-install-0.3.tar.gz?download)


cheers
phil

---

### Post by blackhole82 on 2008-03-06
> **Ringi said:**
> You can use Avidemux:

Auto PSP (H 264)

Be sure you got all codec installed

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I tried using the Avidemux and the AutoPSP version, and it says PSP(broken) for the format.  When it gets done converting the file will not play on my PSP.

---

### Post by xc3RnbFO8P on 2008-03-08
> **blackhole82 said:**
> I tried using the Avidemux and the AutoPSP version, and it says PSP(broken) for the format.  When it gets done converting the file will not play on my PSP.

Did you install the latest Avidemux:

[http://www.getdeb.net/release.php?id=2178]("http://www.getdeb.net/release.php?id=2178")

---

### Post by thomasyen on 2008-03-09
Hello,
This is my first time using Avidemux, and I was wondering how to configure it so that I can use it to convert videos for my iPod. Can anyone help?

---

### Post by thomasyen on 2008-03-14
bump

---

### Post by xc3RnbFO8P on 2008-03-14
Did you install the latest [Avidemux]("http://www.getdeb.net/release.php?id=2178")?

In Avidemux open file, then choose Ipod(mpeg4) in AUTO > target type (320/240)> source aspect ratio (1/1, 4/3, 16/9)> destination aspect ratio(what ever you like 1/1, 4/3, 16/9)> ok
Save.

Then try if it works, I don't own a Ipod so I don't know.

---

### Post by dunkgreen on 2008-03-24
You could use AcidRip to rip the DVD and then use the wizard in VLC to convert it to the format you need.  Not fancy, but it works.

---

### Post by Bigneil on 2008-12-04
I have been reading this thread with interest because i want to encode a DVD to an AVI so that is takes up less space on the hard disk. i copied the movie originally with DVD shrink in windows xp. will avidemux do the job?

---

### Post by JoKeR123 on 2010-03-23
I used Arista Transcoder. Worked just fine, and it was easy to use.
If you have 9.10, you can search for "PSP" in the Ubuntu Software Center.
You can even rip from DVD to any other format you want.
Try it...

---

### Post by laffinet on 2010-03-23
Surprised nobody has mentioned handbrake so far:

[http://handbrake.fr/]("http://handbrake.fr/")

---

### Post by tobemem on 2010-04-28
>          Surprised nobody has mentioned handbrake so far:And ANDREW neither! OK, I'm its author and one of the few people that know it, but I think it could be useful to someone else:

[http://tobemem.memebot.com]("http://tobemem.memebot.com/")

---

### Post by hursto75 on 2010-04-28
Love Handbrake, used it to convert all of my videos (305 so far) to play on my PS3. Handbrake is multithreaded so it will use all of my processors and you can que up jobs. Great tool.

---

### Post by hursto75 on 2010-04-28
As a matter of fact check out My [ps3 home theater]("http://crackednoodle.com/2009/12/home-theater-with-the-ps3/").

---

### Post by jeffdacosta on 2010-04-28
Thanks for the information, very useful, just one question, here you can converter from AVI to MP4 format?.

---

### Post by tobemem on 2010-04-29
Try [MP4Box]("http://gpac.sourceforge.net/doc_mp4box.php#conversion") from gpac package.

---

### Post by jerenept on 2010-04-29
> **laffinet said:**
> Surprised nobody has mentioned handbrake so far:

[http://handbrake.fr/]("http://handbrake.fr/")

I second that! HandBrake is a great dvd converter-fast and high quality

---

### Post by handy on 2010-04-29
& the most recent version of Handbrake has enabled the ability to create soft subtitle tracks, which is a major breakthrough from having them hard coded into the vid & so being unable to turn them off.

Handbrake is brilliant!

---

### Post by tobemem on 2010-05-09
> & the most recent version of Handbrake has enabled the ability to create soft subtitle tracks, which is a major breakthrough from having them hard coded into the vid & so being unable to turn them off.Also ANDREW can do that, since 2005...

I really don't know why I started this pro ANDREW campaign from nowhere :)
Anyway, if you are not scared by command line (interactive mode available):

[http://tobemem.memebot.com/](http://tobemem.memebot.com/)

---

### Post by chinoygio1 on 2010-05-20
Is there also an application in  psp that you can play .rmvb file?

---

