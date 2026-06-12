---
title: "can you install an amd driver?"
date: 2014-02-12
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-12
I downloaded and run in terminal and get error about tools

---

### Post by ajgreeny on 2014-02-12
What AMD card have you got?  You may not even need nor be able to use the fglrx driver as many AMD cards are no longer supported by that driver and will use only the radeon open source driver successfully

---

### Post by open2reason on 2014-02-12
Is it possible for you to open a terminal session and run;

sudo update-pciids #optional command, requires internet
lspci -nn | grep VGA

To display your graphic card name and chipset?

Taken from [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by zika on 2014-02-12
There are some prerequisite packages for Catalyst driver as clearly noted on respective site where You've (I assume) DL-ed driver from.
Also You can take a look, as it is proposed on the picture You gave, into /usr/share/ati/fglrx-install.log to see what is missing...
Btw, do not read this message of mine as any kind of encouragement to use proprietary driver...

---

### Post by Yellow Pasque on 2014-02-13
fglrx 8.97 is really old. Are you sure you're in the correct subforum? (this is for people running Ubuntu 14.04 prerelease)

For general instructions on how to install Catalyst manually, see: [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE)

---

### Post by Yellow Pasque on 2014-02-13
[http://ubuntuforums.org/showthread.php?t=2204440](http://ubuntuforums.org/showthread.php?t=2204440)

Oh, and if you're talking about the same card as your last thread (Radeon X1300), then fglrx/Catalyst is not an option for you. Does the default open-source driver not work or something?

---

### Post by felgro on 2014-02-13
> **sdowney717 said:**
> I downloaded and run in terminal and get error about tools

You have to satisfy criteria detailed here and modify it for Trusty -

[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide)

See also -

[http://ubuntuforums.org/showthread.php?t=2204332](http://ubuntuforums.org/showthread.php?t=2204332)

---

### Post by sdowney717 on 2014-02-17
I have another card an HD2600 pro.
I dont think it is supported by fglrx?

---

### Post by sdowney717 on 2014-02-17
I dual boot with win7.
I noticed that youtube was not smooth, so installed the better card, the hd2600 pro.
Then I was thinking how well can it do with 1080p so try this test.
In win7, it is perfect, even with older x1650 card.
In ubuntu, glitchy, pause, hesitates, so thought to ask and see what's up with the amd drivers.

[http://vimeo.com/18345432](http://vimeo.com/18345432)

You can try and see for yourself, curious about your specs and how it plays back for you.

I have very good video on another PC using older nvidia 8400gs, and the nvidia driver, and ubuntu 12.04, and this video is smooth.

Every AMD card i have can not play this video smoothly in ubuntu, but the same cards in windows is perfect.
In windows even with the default win7 non catalyst driver it is smooth. a 2009 dated amd driver is what win7 will load.
Otherwise you can install a legacy AMD driver, still not a recent one, but it is smooth.

Is there any hope ubuntu with amd cards can play this smoothly?

---

### Post by open2reason on 2014-02-18
I played your viemo test video on my amd a4-5000 with ATI/AMD HD 8330, 4GB ram under the latest 12.04.4lts and as you stated it displayed some stuttering & pausing.
I the repeated the process but as soon as the video started playing I paused the playing and this allowed video data to continue downloading into what I expect are buffers or storage areas under hardware or software control.
After allowing say ten seconds of downloading to be stored I then resumed the play function and the video was played without stuttering or pausing.
From this I would suggest that with my combination of hardware and internet line speed my HD 8330 can process data slightly faster than I can suck it into my machine.

Hope this helps.

---

### Post by sdowney717 on 2014-02-18
That is a powerful very recent card.

Are you using the radeon free driver or the binary fglrx?

From my experience, the free radeon driver has never worked well for online video.

I need some 1080p video files to test and will report back how they play with the free radeon driver and an HD2600 PRO video card.

---

### Post by open2reason on 2014-02-18
Am using 14.04 lts with open source tested driver which was installed as default with 14.04 lts

[ATTACH=CONFIG]250465[/ATTACH]

and all seems to work as wished.

Am running on an Acer Aspire xc-105 dual boot 12.04.4 lts & 14.04 lts 

[ATTACH=CONFIG]250466[/ATTACH]

---

### Post by Yellow Pasque on 2014-02-18
> **sdowney717 said:**
> From my experience, the free radeon driver has never worked well for online video
If you're using the Flash plugin to play video, then it's all about how much CPU speed you have.
> an HD2600 PRO video card

Unfortunately, that also offers no video decode acceleration. The code to support the original UVD is written, but it is hung up in AMD's code review: [http://lists.freedesktop.org/archives/dri-devel/2014-January/051584.html](http://lists.freedesktop.org/archives/dri-devel/2014-January/051584.html)

---

### Post by sdowney717 on 2014-02-19
That is interesting.
The HD 2600 pro is still supported by AMD catalyst in windows.
On that link you gave, well old hardware?
I bet many people have old hardware and would like it to work as it should, like it was made to work.

---

### Post by cariboo on 2014-02-19
> **sdowney717 said:**
> That is interesting.
The HD 2600 pro is still supported by AMD catalyst in windows.
On that link you gave, well old hardware?
I bet many people have old hardware and would like it to work as it should, like it was made to work.

The only way that's going to happen, is enough people lobby AMD directly to bring back Linux support for older graphics cards. My personal opinion is that herding cats is probably easier.

---

### Post by VMC on 2014-02-19
> **cariboo907 said:**
> ... My personal opinion is that herding cats is probably easier.Funny response.

I watched the viedo link from the first post, and it played very smoothly. My integrated video info is at the bottom of this post. I'm using Xubuntu, with NVIDIA Driver Version: 304.117

---

### Post by Yellow Pasque on 2014-02-20
> **VMC said:**
> I watched the viedo link from the first post, and it played very smoothly. My integrated video info is at the bottom of this post.

AMD vs. Nvidia -> apples vs. oranges

> The only way that's going to happen, is enough people lobby AMD directly to bring back Linux support for older graphics cards. My personal opinion is that herding cats is probably easier. 

For Catalyst, it's not happening. They support older gens with the open-source driver. Lack of support for cards with UVD is a sore spot.

> On that link you gave, well old hardware?

RadeonHD 2k and 3k series launched in 2007-2008. That's 6-7 years ago, so old hardware indeed...

---

### Post by VMC on 2014-02-20
> **sdowney717 said:**
> I dual boot with win7.
I noticed that youtube was not smooth, so installed the better card, the hd2600 pro.
Then I was thinking how well can it do with 1080p so try this test.
In win7, it is perfect, even with older x1650 card.
In ubuntu, glitchy, pause, hesitates, so thought to ask and see what's up with the amd drivers.

[http://vimeo.com/18345432](http://vimeo.com/18345432)

**You can try and see for yourself, curious about your specs and how it plays back for you.**

I have very good video on another PC using older** nvidia 8400gs, and the nvidia driver**, and ubuntu 12.04, and this video is smooth.

Every AMD card i have can not play this video smoothly in ubuntu, but the same cards in windows is perfect.
In windows even with the default win7 non catalyst driver it is smooth. a 2009 dated amd driver is what win7 will load.
Otherwise you can install a legacy AMD driver, still not a recent one, but it is smooth.

Is there any hope ubuntu with amd cards can play this smoothly?

> **Temüjin said:**
> AMD vs. Nvidia -> apples vs. oranges
...
Not if you consider the above quote.

---

