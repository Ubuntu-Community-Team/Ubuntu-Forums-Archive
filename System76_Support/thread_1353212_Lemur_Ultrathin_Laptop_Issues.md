---
title: "Lemur Ultrathin Laptop Issues"
date: 2009-12-12
forum: System76 Support
---

### Post by Mark.ST on 2009-12-12
Hello,

I received the Lemur Ultrathin laptop (with Intel SSD 80GB) a few days ago. It's a beautiful and light laptop, but I have the following issues.

If you bought the same laptop and encountered the same problems and/or know how to fix any of them, please let me know.


**1. "Media test failure" when booting up**

When I boot up the machine, the first screen shows something like:

```
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE Rom.
```

[IMG]http://imgur.com/oYoSCl.jpg[/IMG]

What's this and why does this show up? Is this in any way related to one or more of the issues below..?


**2. Skype Doesn't Work Out of the Box**

Although I was told by Thomas@System76 that Skype works out of the box, after I installed
[http://www.skype.com/intl/en/download/skype/linux/choose/]("http://www.skype.com/intl/en/download/skype/linux/choose/")
(Ubuntu 8.10+ 64-bit)
and went to "Options"->"Video Devices", the pull-down menu shows no webcam device.

[IMG]http://imgur.com/mp9RTl.jpg[/IMG]

Did I miss something?

I did the modprobe thing in the following post with no luck. Skype or Cheese still don't see any device.
[http://ubuntuforums.org/showthread.php?t=634393]("http://ubuntuforums.org/showthread.php?t=634393")



**3. One Screw Missing**

This is probably only me, but mine came with a screw missing for the USIM Card Bay Cover so it can be easily opened...
Thomas, if you are reading this, please let me know if you can send me the same screw or tell me if I can buy this kind of thing locally (I live in Canada, btw.)


**4. Fan Noise**

Since I paid extra for Intel SSD, when fan is not on, it's really silent, which is great, but when the fan turns on, it's kind of noisy. And the fan turns on quite often. I don't know if it has to be like that.


I appreciate your help!

---

### Post by marshmallow1304 on 2009-12-12
1) I think this is because netboot is ahead of the hard drive in the boot sequence.  Check the boot order in the BIOS.

2) Is there a hardware toggle for the webcam?  Fn+F10 does it on my Pangolin, but it is not marked.  Check the documentation/welcome manual.

---

### Post by Mark.ST on 2009-12-12
Thanks for your help, marshmallow1304.

For (1), I'll try changing the boot sequence in the BIOS setting and report back the result.


**Is there a hardware toggle for the webcam?**

Not sure.. and Fn+F10 doesn't seem to work..

I forgot to mention that Skype test call doesn't work either. Also tried Sound Recorder. It's not working. So it's not just the camera. Microphone is not recognized either.

I did run the System76 Driver Installer, but Lemur Ultrathin is not even listed in the following Knowledge76 page:

[http://www.knowledge76.com/index.php/Cameras]("http://www.knowledge76.com/index.php/Cameras")

Any help is appreciated.

---

### Post by marshmallow1304 on 2009-12-12
For the microphone, try going to System->Preferences->Sound, Input tab, and setting Connector to Microphone 2 (This assumes you are on Karmic.).

---

### Post by Mark.ST on 2009-12-12
**[..] setting Connector to Microphone 2**

Sound Recorder worked with this setting! Thanks a lot. Now I know at least the mic is not defective :-)

However, Skype test call still fails:

[IMG]http://imgur.com/iBHwnl.png[/IMG]

[IMG]http://imgur.com/8imfrl.png[/IMG]

---

### Post by gordintoronto on 2009-12-12
You should Google the error message.  It might mean there is a loose cable.  That could also account for the missing webcam.  (If Cheese also does not find the webcam.)

If you reboot when the system is warm, does the same error show up?

---

### Post by marshmallow1304 on 2009-12-12
> **Mark.ST said:**
> However, Skype test call still fails:

[IMG]http://imgur.com/iBHwnl.png[/IMG]


Hmm..  My settings look exactly like that except I don't have that box checked.  What happens when you do "Make a test sound"?

---

### Post by Mark.ST on 2009-12-13
Hi,

For the 1st problem about the PXE error, after I changed the BIOS Boot Sequence (I moved the Ethernet item at the top to bottom), the error message went away. Thanks marshmallow1304 and gordintoronto!


In Skype, "make a test sound" works without problems (it makes the same sound as the app launches). 

Test call and webcam still don't work. Unchecked the mixer level checkbox but the result is the same..

---

### Post by Mark.ST on 2009-12-13
Hi,

I'll post the result of **[FONT="Courier New"]dmesg | grep uvcvideo[/FONT]**, if that's of any help:

```
$ dmesg | grep uvcvideo
[16376.568351] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0241)
[16376.568368] uvcvideo: No valid video chain found.
[16376.568399] usbcore: registered new interface driver uvcvideo
[16394.516363] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0241)
[16394.516398] uvcvideo: No valid video chain found.
[16397.484727] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0241)
[16397.484748] uvcvideo: No valid video chain found.
[16413.586033] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0241)
[16413.586067] uvcvideo: No valid video chain found.
$ lsusb | grep 5986:0241
Bus 001 Device 007: ID 5986:0241 Acer, Inc
$ uname -r
2.6.31-16-generic
```

The following conversation talks about the same "no valid video chain" message, and it talks about patching the kernel, which sounds a bit scary to me:
[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg04178.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg04178.html)

Please let me know if there's a simple way to fix this problem. Also let me know if further information is required. Thanks!

---

### Post by thomasaaron on 2009-12-14
**1. "Media test failure" when booting up**

Definitely boot order.

**2. Skype Doesn't Work Out of the Box**

Make sure you've installed Skype (and your other restricted codecs from)...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

On the webcam, run your system76 driver and then reboot. Then Fn-F10 should turn it on.

**3. One Screw Missing**

I've gotten your email on that. We'll get another screw out to you.

**4. Fan Noise**

There isn't really much to adjust there. You could try installing the cpu scaling applets on your upper panel and scaling your cpu down.

---

### Post by Mark.ST on 2009-12-14
**1. "Media test failure" when booting up**

Definitely boot order.

[COLOR="DarkGreen"][INDENT]Thanks. This problem was solved (please see one of my above posts) :-)[/INDENT][/COLOR]


**2. Skype Doesn't Work Out of the Box**

Make sure you've installed Skype (and your other restricted codecs from)...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

On the webcam, run your system76 driver and then reboot. Then Fn-F10 should turn it on.

[COLOR="DarkGreen"][INDENT]Thanks for the link. I ran the 3 commands on top (2 medibuntu and 1 codecs command) and they worked, but when I run **[FONT="Courier New"]apt-get install skype[/FONT]**, I get this:

```
$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate
```

This is after I removed Skype that I installed from the Skype official site. I don't know if the one from apt-get is different from the deb package available on the Skype site, but it sounds like I should use apt-get to install Skype, so let me know how to work around this issue.

Also, as mentioned in one of above posts, I did run System76 Driver Installer and rebooted but camera is not recognized by both Skype and Cheese. Fn+F10 doesn't work either.

[IMG]http://imgur.com/2tq5al.png[/IMG]

Please let me know if further info is required. After I get this working most of my problems are gone.[/INDENT][/COLOR]



**3. One Screw Missing**

I've gotten your email on that. We'll get another screw out to you.

[COLOR="DarkGreen"][INDENT]Great! I'll wait for that and report back when I get it.[/INDENT][/COLOR]



**4. Fan Noise**

There isn't really much to adjust there. You could try installing the cpu scaling applets on your upper panel and scaling your cpu down.

[COLOR="DarkGreen"][INDENT]Ok.. This is not a very good news because the fan keeps running for ~7 minutes after every 7 to 10 minutes of silence (can anyone confirm this?). And when it's on, it's actually a bit noisier than the 3 year old Dell laptop (no SSD) I had before..[/INDENT][/COLOR]

---

### Post by thomasaaron on 2009-12-15
Let's focus on your webcam for now. No sense dealing with Skype until the cam is running.

Go to [http://planet76.com/repositories](http://planet76.com/repositories) and download the latest driver. It will be the second link from the bottom.

Once you get it downloaded, install it. Then go to System > Admin > System76 Driver > Install (tab) > Install (button).

When it's done, reboot.

Then check Fn-F10.

---

### Post by Mark.ST on 2009-12-15
[B]Go to [http://planet76.com/repositories](http://planet76.com/repositories) and download the latest driver. It will be the second link from the bottom.
Once you get it downloaded, install it.[/B]

Thanks for your support.

I downloaded system76-driver-2.4.0.deb (I hope I'm getting the version right), and tried to install it. Here's what I get:

[IMG]http://imgur.com/J4UX2l.png[/IMG]

"*Error: A later version is already installed*"

Please let me know how to proceed.

---

### Post by thomasaaron on 2009-12-16
Let's take this one up via a phone conversation for efficiency's sake. Can you give me a call when you get a chance?

[http://system76.com/article_info.php?articles_id=24](http://system76.com/article_info.php?articles_id=24)

Just call the sales line.

---

### Post by Mark.ST on 2009-12-16
**Let's take this one up via a phone conversation for efficiency's sake. Can you give me a call when you get a chance?**

Well, I tend to miss a lot of things on a phone conversation so I actually prefer this forum (not to mention there may be people with the same or similar problem who are reading this or who later google or search this forum to find this thread).

I don't mind the resolution being slightly slower, as long as you keep answering my questions :-)

If that's ok please tell me the steps I should take. I'll try them and report back the results.

I just read that another model has a similar issue with webcam with the latest driver, after upgrading to Karmic. Could be a Karmic issue?
[http://ubuntuforums.org/showthread.php?t=1356308]("http://ubuntuforums.org/showthread.php?t=1356308")

Anyway, I look forward to your reply.

---

### Post by thomasaaron on 2009-12-17
Fair enough.

What version of the System76 Driver are you using? It should be 2.4.2. An update broke the webcams on Lemurs, and the 2.4.2. drive should fix it. The only way to get it though, if you don't already have it installed, is from me via email.

---

### Post by Mark.ST on 2009-12-17
I clicked the "About" button in "System Information" tab in System76 Driver Installer, and the version seems to be 2.4.1.

Sounds like an update to the driver is available, so I'll email you to ask for the version 2.4.2. Any reason why it's not publicly available (yet)?

---

### Post by thomasaaron on 2009-12-17
Yes. We're still working on adding some other features to it. It should be publicly available soon.

---

### Post by Mark.ST on 2009-12-17
Awesome, after I installed Driver 2.4.2, the cam is working on both Cheese and Skype! Yay :-)

[IMG]http://imgur.com/DCyPxl.png[/IMG]
*BisonCam, NB Pro Recognized*


Now...

Skype test call still fails as I said in below link (with screenshots):
[http://ubuntuforums.org/showpost.php?p=8487933&postcount=5]("http://ubuntuforums.org/showpost.php?p=8487933&postcount=5")

Any idea why it's not working? BTW I installed Skype from the official site again.

---

### Post by jjacobs2 on 2009-12-18
I think you have to install the pulseaudio volume control, do the test call, and setup input devices for the correct microphone and volume while skype is calling.  I still have a problem on my other laptop with skype microphone volume being way too low and I suspect it won't be fixed until lucid.  A quick fix if you have other issues is to try using the older version of skype from before they forced you to use pulseaudio for all 3 devices.

---

### Post by thomasaaron on 2009-12-18
Mark, your mic should not be set to pulseaudio. It should be set to one of the HDA Intel settings. (...within Skype's configuration, that is...)

---

### Post by Mark.ST on 2009-12-18
***Mark, your mic should not be set to pulseaudio. It should be set to one of the HDA Intel settings. (...within Skype's configuration, that is...)***

Ok.., but in Skype Options, PulseAudio seems to be the only thing I can choose. Can you tell me how to change that?

[IMG]http://imgur.com/00058l.png[/IMG]

---

### Post by thomasaaron on 2009-12-18
Hmmmm... the first thing I would try would be removing the version you downloaded from Skype's website and install the medibuntu version via...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

It is optimized for Ubuntu and hopefully will give you different options. If not, we'll figure that out.

---

### Post by marshmallow1304 on 2009-12-18
My Skype is from Medibuntu and it gives me only that one PulseAudio option as well.  However, I am able to make test calls successfully.

---

### Post by Mark.ST on 2009-12-19
Thanks Tom and marshmallow1304.

As I said in below link
[http://ubuntuforums.org/showpost.php?p=8498771&postcount=11]("http://ubuntuforums.org/showpost.php?p=8498771&postcount=11")
I couldn't install Skype using apt-get. I get this error message: "[FONT="Courier New"]E: Package skype has no installation candidate[/FONT]" (detailed message in above link)
If installing this version fixes the problem I'd like to try.

I don't know, if what marshmallow1304 says is correct, is this mic setting with PulseAudio really causing the test call failure problem? I also remember when I was using my older laptop I think the mic was set to PulseAudio, and I could make calls (not always, it failed occasionally for some unknown reasons).
But now Skype test call never works. Not once.

Also, as I said in below link:
[http://ubuntuforums.org/showpost.php?p=8487933&postcount=5]("http://ubuntuforums.org/showpost.php?p=8487933&postcount=5")
Sound Recorder app works so I know the mic is not defective.

Anyway, I appreciate anyone's help on this one. I know there are many Skype for Linux users out there.

---

### Post by marshmallow1304 on 2009-12-19
Well, this isn't the best solution or really even a solution but you might want to try this for a temporary workaround.

```
gksudo gedit /etc/pulse/client.conf
```Change
> ; autospawn = yesto
> autospawn = no
```
killall pulseaudio
```

Now you should be able to select the correct device in Skype.




Doing
```
pulseaudio &
```
will bring pulse back without a restart.

---

### Post by thomasaaron on 2009-12-21
> I couldn't install Skype using apt-get. I get this error message: "E: Package skype has no installation candidate" (detailed message in above link)

I think that's because you are not running the whole tutorial. You've got to install the medibuntu repositories in order for the...

sudo apt-get install skype

...to work.

> I don't know, if what marshmallow1304 says is correct, is this mic setting with PulseAudio really causing the test call failure problem?

Yes. It is correct.

---

### Post by Mark.ST on 2009-12-21
***I think that's because you are not running the whole tutorial.***

Hmm, I think I did run the whole thing.. I removed Skype from Synaptic again and tried the following.
Please see below and tell me what I'm missing..

```
**$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list  --output-document=/etc/apt/sources.list.d/medibuntu.list** 
--2009-12-21 16:49:19--  http://www.medibuntu.org/sources.list.d/karmic.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 272 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 272         --.-K/s   in 0s      

2009-12-21 16:49:20 (11.2 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]

**$ sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update**
[sudo] password for *user*: 
Hit http://planet76.com ./ Release.gpg
Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_CA
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_CA
Ign http://planet76.com ./ Translation-en_CA
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_CA
Get:2 http://ppa.launchpad.net karmic Release [66.0kB]
Hit http://planet76.com ./ Release
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://packages.medibuntu.org karmic/non-free Translation-en_CA
Hit http://packages.medibuntu.org karmic Release
Get:3 http://us.archive.ubuntu.com karmic/main Translation-en_CA [12.0kB]
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_CA
Ign http://security.ubuntu.com karmic-security/universe Translation-en_CA
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com karmic-security Release
Ign http://planet76.com ./ Packages
Hit http://packages.medibuntu.org karmic/free Packages
Hit http://security.ubuntu.com karmic-security/main Packages
Ign http://planet76.com ./ Packages
Get:4 http://us.archive.ubuntu.com karmic/restricted Translation-en_CA [2,799B]
Get:5 http://us.archive.ubuntu.com karmic/universe Translation-en_CA [663B]
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_CA
Get:6 http://us.archive.ubuntu.com karmic-updates Release.gpg [189B]
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://planet76.com ./ Packages
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_CA
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_CA
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_CA
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_CA
Hit http://us.archive.ubuntu.com karmic Release
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Get:7 http://us.archive.ubuntu.com karmic-updates Release [44.1kB]
Get:8 http://ppa.launchpad.net karmic/main Packages [3,422B]
Get:9 http://ppa.launchpad.net karmic/main Sources [1,361B]
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Get:10 http://us.archive.ubuntu.com karmic-updates/main Packages [118kB]
Get:11 http://us.archive.ubuntu.com karmic-updates/restricted Packages [14B]
Get:12 http://us.archive.ubuntu.com karmic-updates/main Sources [37.4kB]
Get:13 http://us.archive.ubuntu.com karmic-updates/restricted Sources [14B]
Get:14 http://us.archive.ubuntu.com karmic-updates/universe Packages [71.1kB]
Get:15 http://us.archive.ubuntu.com karmic-updates/universe Sources [17.2kB]
Get:16 http://us.archive.ubuntu.com karmic-updates/multiverse Packages [6,860B]
Get:17 http://us.archive.ubuntu.com karmic-updates/multiverse Sources [3,831B]
Fetched 385kB in 3s (109kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Hit http://planet76.com ./ Release.gpg
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_CA
Ign http://planet76.com ./ Translation-en_CA
Hit http://us.archive.ubuntu.com karmic Release.gpg
Hit http://us.archive.ubuntu.com karmic/main Translation-en_CA
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_CA
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_CA
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_CA
Ign http://packages.medibuntu.org karmic/non-free Translation-en_CA
Hit http://ppa.launchpad.net karmic Release
Hit http://planet76.com ./ Release
Hit http://us.archive.ubuntu.com karmic/restricted Translation-en_CA
Hit http://us.archive.ubuntu.com karmic/universe Translation-en_CA
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_CA
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_CA
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_CA
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_CA
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_CA
Ign http://security.ubuntu.com karmic-security/universe Translation-en_CA
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com karmic-security Release
Hit http://us.archive.ubuntu.com karmic Release
Hit http://packages.medibuntu.org karmic Release
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://planet76.com ./ Packages
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://packages.medibuntu.org karmic/free Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://planet76.com ./ Packages
Hit http://planet76.com ./ Packages
Reading package lists...

**$ sudo apt-get install skype**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate
```

I appreciate your help.

---

### Post by thomasaaron on 2009-12-22
Well, Mark.

First of all, I owe you an apology. It *appears* they've removed Skype from the Medibuntu repos, and I had no idea. So, sorry for the wild goose chase.

That said, I ran into this exact problem yesterday on another computer, and here is what you need to do to get Skype going.

1. Go to...
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/) 
...and download/install Skype from there. Let me know if you need any help with install it, but you should basically just have to double-click the deb package and follow the prompts. You'll need the 8.10+ 64-bit version.

2. Once it's installed, you will have to follow marshmallow1304's instructions above. That is, run...

```
gksudo gedit /etc/pulse/client.conf
```

And change...
```
; autospawn = yes 
```
...to...
```
; autospawn = no
```

3. Go to System > Prefs > Startup Applications and create a new start-up app. Call it "Pulse Off" and make the command for it...

killall pulseaudio

4. Then reboot. Then start Skype.

5. Now, in Skype's options, you should have several options for Input. You want the one that says something like...

HDA(Intel) (hw0:0)

Then you should be able to make a test call.

---

### Post by Mark.ST on 2009-12-22
Tom, I'm glad you apologized for the situation, but..

(1) Although I could choose "**HDA Intel, ALC272 Analog (hw:0,0)**" after doing what marshmallow1304 mentioned, test call still failed. I also tried all the other HDA Intel options. None worked. Tried unchecking the mixer level check box. Didn't work.

[IMG]http://imgur.com/NdUiul.png[/IMG]
*Skype Setting after disabling pulse*

(2) As marshmallow1304 says, this really isn't a proper solution. For example, after killing pulse, normal stuff like volume control stops working. You know, even if Skype worked with this solution (it didn't), it's not the only application I use. I want other stuff to work too.

Please give me some real solution that (a) actually works and (b) doesn't break anything. Can't you test with Lemur by the way?



**Edit:**
Below is the PulseAudio Volume Control screenshot (this is when Pulse is enabled (i.e. default)). You can see it's receiving sound.

[IMG]http://imgur.com/AMEK4l.png[/IMG]
*PulseAudio Volume Control (pavucontrol) - Microphone 2 is receiving sound*

---

### Post by thomasaaron on 2009-12-23
> As marshmallow1304 says, this really isn't a proper solution. For example, after killing pulse, normal stuff like volume control stops working. You know, even if Skype worked with this solution (it didn't), it's not the only application I use. I want other stuff to work too.

Please give me some real solution that (a) actually works and (b) doesn't break anything. Can't you test with Lemur by the way?

I've requested on of our techs take screenshots of how to get the mic working with Sound Recorder. I've also asked them to test with Skype.

As for Skype, we have no control over that piece of software. They've removed it from the medibuntu repos, and the only version on Skype's website goes back to 8.10. If they've stopped maintaining a version of it that is optimized for Ubuntu, then a work-around may well be the only option we can offer you.

---

### Post by thomasaaron on 2009-12-23
OK, so it appears Skype has been removed from the 64-bit medibuntu repositories, but it is still in the 32-bit repos.

I've attached some screenshots. For the volume control panels, please notice that one is for an external mic, and one is for the internal mic (you can tell which is which by the filenames). There is also a screenshot of Skype's audio settings, which only seem to work in 32-bit.

Please test:
1. If you can record from sound recorder using those volume control settings. (They should work equally well in 32-bit and 64-bit.)

2. If Skype will work using these sound recorder settings plus the above pulseaudio hack. (We've already seen it will not work using the skype settings in the screenshots in 64-bit.)

My shop lemur is currently being tested with a new 32-bit kerel (the PAE kernel, which is 32-bit but has the ability to see 4GB of RAM), and they can't put 64-bit on it just yet.

So, if those sound recorder settings, and the hack will get you through until then, we will investigate it more under 64-bit soon.

---

### Post by Mark.ST on 2009-12-23
***If they've stopped maintaining a version of it that is optimized for Ubuntu, then a work-around may well be the only option we can offer you.***

Well, but the problem is the "work-around" you offered didn't work. You read [my post]("http://ubuntuforums.org/showpost.php?p=8543043&postcount=30"), right? Please tell me if that killing pulse thing worked on your side with Lemur. ("Worked" means you can make Skype calls.)

[B][I]Please test:
1. If you can record from sound recorder using those volume control settings. (They should work equally well in 32-bit and 64-bit.)[/I][/B]

I already said in this thread, twice, that Sound Recorder works with the "Microphone 2" option, thanks to marshmallow1304's advice. Please see:
[http://ubuntuforums.org/showpost.php?p=8487933&postcount=5]("http://ubuntuforums.org/showpost.php?p=8487933&postcount=5")
[http://ubuntuforums.org/showpost.php?p=8527191&postcount=25]("http://ubuntuforums.org/showpost.php?p=8527191&postcount=25")

So, yes, I can record sound with the Sound Recorder app.

Same for test 2. I did change the mic to Microphone 2 and killed pulse and chose Intel HDA setting. Skype didn't work and still doesn't work. And your tech people saw Skype doesn't work on Lemur, right? How can it possibly work on my side?

Please, when you find a proper solution on how to get Skype working on Lemur, post the step-by-step instruction here.


Right now, **Skype does not work out of the box on Lemur Ultrathin, and there's no working work-around yet**. Tom, please confirm.

---

### Post by thomasaaron on 2009-12-23
> You read my post, right?
> ("Worked" means you can make Skype calls.)
> And your tech people saw Skype doesn't work on Lemur, right? How can it possibly work on my side?

I would greatly appreciate it if you wold consider less rude approach to getting support on this forum. Once these threads reach a certain length, they become quite difficult to keep track of, especially considering we receive a huge quantity of sales and support requests daily, and yours is only one of them. But we do our best make sure everything gets answered.

Admittedly, getting this one answered hasn't been as efficient as one would hope, partially because 1) I didn't realize that Skype was no longer available in the 64-bit Ubuntu repos, and 2) because our Lemur currently isn't available for testing this particular 64-bit issue. However, you've been treated with nothing less than courtesy. It would be nice to receive the same treatment.

```
Please tell me if that killing pulse thing worked on your side with Lemur. 
```

As I mentioned, our Lemur is currently being tested with a 32-bit PAE kernel, in which Skype works perfectly with pulseaudio enabled. I won't have a chance to check it with a 64-bit kernel until after the holiday.

---

### Post by Mark.ST on 2009-12-23
> I would greatly appreciate it if you wold consider less rude approach to getting support on this forum. Once these threads reach a certain length, they become quite difficult to keep track of, especially considering we receive a huge quantity of sales and support requests daily, and yours is only one of them. But we do our best make sure everything gets answered.

Admittedly, getting this one answered hasn't been as efficient as one would hope, partially because 1) I didn't realize that Skype was no longer available in the 64-bit Ubuntu repos, and 2) because our Lemur currently isn't available for testing this particular 64-bit issue. However, you've been treated with nothing less than courtesy. It would be nice to receive the same treatment.

Sorry if my response sounded rude. Actually it doesn't sound rude in my taste, but hey, English is not my first language so maybe there are many people offended by this tone of English. Again, sorry, that's not my intention. I tried to make it direct and straightforward.

(*Especially the second one you quoted about Skype calls, that's to make it clear that "worked" does not mean "killall pulseaudio worked without errors", but means "Skype worked (i.e. You can make Skype calls)."*)

But yes, I'm sure it's very hard to keep track of everything in the System76 forum.

But you have to remember that I asked specifically about Skype before purchasing this laptop. Here's our dialog on November 12 (I placed my order on November 26):
> [...]
**(2) Skype. Have you tested if Skype for Linux (latest version) works out of the box (both voice and video chat) without any issues or tweaks whatsoever with your hardware? Skype caused a lot of trouble on my current Dell laptop, so I don't want to buy another laptop until I can confirm this.**

TA: Yes, Skype works fine. You may have to enable your microphone via the sound control panel and make some tweaks *within* Skype's options. But that's about it.
[...]
So I'm a bit disappointed that you said "Yes" without testing if this really works or not. As a customer, I certainly don't want to be treated like this. You could say, "I haven't tested Skype with Lemur but since it seems to be working on other models so it will work fine," then at least it's honest and I wouldn't be that disappointed.

---

### Post by Mark.ST on 2009-12-25
I found the following blog post. Not sure if it works, but I'll look into it.

Skype on 64 bit Ubuntu
[http://oligofren.wordpress.com/2008/03/28/skype-on-64-bit-ubuntu/]("http://oligofren.wordpress.com/2008/03/28/skype-on-64-bit-ubuntu/")

---

### Post by Mark.ST on 2009-12-28
Nope, the above solution didn't work for me - I get the same "Call Failed" message.

---

### Post by thomasaaron on 2009-12-30
I just tested a Lemur with a fresh 64-bit image from our server. Skype works perfectly on it out of the box with no tweaking (other than setting up the right mic and the volume sliders).

Here are screenshots of my set-up. Make sure volume sliders (particularly input sliders are way up).

Edit:
This is with the Skype download from Skype.com for Ubuntu 8.10+.

---

### Post by Mark.ST on 2009-12-30
Great! So you updated the Ubuntu that comes with Lemur, and it sounds like that fixed the Skype/pulse problem.

Where can I download the image for fresh install from your server? Can I install it using a USB flash drive? How do I do that?

---

### Post by thomasaaron on 2009-12-30
> Great! So you updated the Ubuntu that comes with Lemur, and it sounds like that fixed the Skype/pulse problem.

We haven't updated anything since Lemurs started shipping.

> Where can I download the image for fresh install from your server?


You cannot download from our server; it doesn't contain .iso images anyway.


It doesn't appear there is (or was) a skype/pulse problem for the Lemur. 

In previous posts, your screenshot shows you are using the pulseaudio volume control, which you must have installed (as it doesn't come with the base install of Ubuntu or on our systems). My best guess is that either 1) this broke some aspect of skype or pulseaudio; or 2) you don't have that particular volume control set up correctly. 

Skype works out of the box with the standard volume controls (i.e Sound Preferences).

On the chance that the pulseaudio volume control *didn't* break skype or some aspect of pulseaudio, your sliders for Mic2 seem too low. You will notice mine are much higher. This did make a difference in my own testing, but I don't know if that matters on your particular set-up.

You may want to try uninstalling the pulseaudio volume control, and maybe --reinstall pulseaudio. Then try using the setup in my screenshots with standard Sound Preferences tool.

> Can I install it using a USB flash drive? How do I do that?

It's may not be necessary. But if you decide to re-install, here are instructions...

[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

Instead of creating a CD, though, you probably will want to use your current system to create a bootable Ubuntu USB drive (System > Hardware > USB start-up disk creator).

---

### Post by PatrickVogeli on 2009-12-30
hi there,

maybe you could try something. I have an acer 1810tz which, after a standard install, the mic doesn't work. That was fixed installing the alsa-backports package. After that, the mic would work with sound-recorder, but not skype.

Well, in my case, skype was fixed after, in the sound preferences, I set the output ballance only to right or left speaker and then, skype works! It's actually unbelievable, but it does the trick.

Sure it's not that nice, but usable.

---

### Post by Mark.ST on 2009-12-31
[B]We haven't updated anything since Lemurs started shipping.
[...]
It doesn't appear there is (or was) a skype/pulse problem for the Lemur.[/B]

Yes there was/is. It's you who [suggested]("http://ubuntuforums.org/showpost.php?p=8514937&postcount=16") installing the newer driver (since my Lemur came with the [older Driver version 2.4.1]("http://ubuntuforums.org/showpost.php?p=8515422&postcount=17")), and that (at least) [fixed]("http://ubuntuforums.org/showpost.php?p=8517961&postcount=19") the webcam issue. Skype test call issue wasn't fixed though.
So if Lemurs still come with Driver 2.4.1, they will have (at least) webcam issues until they upgrade the driver, which is [not publicly available yet]("http://planet76.com/repositories") (as of Dec 31). But I guess you probably already ship Lemurs with the newer driver (after I notified you about the issue), which is a good thing because less customers waste time.

I feel as though you are trying to give the impression that you were consistent with your answers (which I believe you weren't), rather than really trying to fix the issue a customer is facing and making sure they are satisfied with your products. (Like your attempt to repeat "Skype works out of the box". It didn't, at least on the Lemur I got from you, and you know that.)



**In previous posts, your screenshot shows you are using the pulseaudio volume control, which you must have installed (as it doesn't come with the base install of Ubuntu or on our systems). My best guess is that either 1) this broke some aspect of skype or pulseaudio; or 2) you don't have that particular volume control set up correctly.** 

That's probably not the case. I installed pulseaudio volume control after jjacob2 suggested installing it in one of the previous posts in this thread:

[http://ubuntuforums.org/showpost.php?p=8519118&postcount=20]("http://ubuntuforums.org/showpost.php?p=8519118&postcount=20")

Before that, [Skype test call failed]("http://ubuntuforums.org/showpost.php?p=8487933&postcount=5"). After that/Now, Skype test call still fails. So I guess pulseaudio volume control wasn't the one that broke skype or pulseaudio. It's  obviously broken somewhere though.



**On the chance that the pulseaudio volume control *didn't* break skype or some aspect of pulseaudio, your sliders for Mic2 seem too low. You will notice mine are much higher. This did make a difference in my own testing, but I don't know if that matters on your particular set-up.**

I will try this, but what difference did this make (since you mentioned it)? Before making this high, did Skype test call fail? And changing the sliders for Mic2 fixed the issue? Is that what you mean?

---

### Post by thomasaaron on 2009-12-31
> Yes there was/is. It's you who suggested installing the newer driver (since my Lemur came with the older Driver version 2.4.1), and that (at least) fixed the webcam issue. Skype test call issue wasn't fixed though.

My comment was simply a response to your assertion that we changed something, and that this change is what fixed pulseaudio as it pertains to Skype. Here is your comment verbatim...

> Great! So you updated the Ubuntu that comes with Lemur, and it sounds like that fixed the Skype/pulse problem. 

I was trying to point out that this wasn't the case. We've done nothing whatsoever to tweak skype or pulseaudio, or to address this issue in any way either in our image or our driver. 

It's true that the latest unavailable driver fixes the webcam, which was broken due to an update. But that really has nothing to do with your statement, which is why it didn't occur to me to incorporate that into my answer.

> I feel as though you are trying to give the impression that you were consistent with your answers (which I believe you weren't), rather than really trying to fix the issue a customer is facing and making sure they are satisfied with your products. (Like your attempt to repeat "Skype works out of the box". It didn't, at least on the Lemur I got from you, and you know that.)

I've worked quite hard at fixing the issue for you, despite your confrontational demeanor. In fact, I am of the opinion that Skype/Pulseaudio had no problems when your computer shipped and still don't. 

It is my best estimation that something you installed, or some modification you have made has broken Skype. That's not a slight. I break stuff in Ubuntu on a daily basis.

But to be fair, there is another option. Although it is pretty unlikely, you could have a hardware issue as well. Probably the best way to rule this out would be to re-image and try my screenshots. If that doesn't fix it, we probably should make that assumption.

As for the webcam issue, I thought we handled that quite expediently for you.

> That's probably not the case. I installed pulseaudio volume control after jjacob2 suggested installing it in one of the previous posts in this thread:

[http://ubuntuforums.org/showpost.php...8&postcount=20](http://ubuntuforums.org/showpost.php...8&postcount=20)

Before that, Skype test call failed. After that/Now, Skype test call still fails. So I guess pulseaudio volume control wasn't the one that broke skype or pulseaudio. It's obviously broken somewhere though.

Perhaps it's not the case. But it is my best estimation, given the data I'm able to glean from this thread, of what the problem might be.

I've done my best to provide you with support, but you obviously are too angry and defensive. It would seem that I'm only succeeding in irritating you further, which is something I have no desire to do.

For further support on this... or any other issues... please feel free to contact us directly via email or phone. This is certainly not the tone we are shooting for in our forums.

And I'm terribly sorry this has been a bad experience for you. It certainly hasn't been intentional. I think you'll find precious few threads on this forum with this sort of tone from a customer. Probably none at all. I'm very disappointed about that.

As for this thread... I've given you the fix that should work fine on your system, barring a hardware issue. I'll probably not respond to it anymore, as it obviously is not productive in the slightest.

The last word is yours, my friend. I hope you have a great New Year.

---

### Post by Mark.ST on 2009-12-31
**As for the webcam issue, I thought we handled that quite expediently for you.**

Yes you did, thank you. I think your customer service is quite good, although I think you could improve on certain areas (like putting the latest drivers in the publicly available repositories, documentation for your latest products, etc). Apparently I complained too much, but it doesn't mean your service is bad.

It's sad you won't provide support here because I don't use a certain kind of English (as I said, it's not even my first language), and I'm "far too angry." Sounds like I said "**** you" (*Edit: wow, this word is censored*) or something (I didn't). I know my English is not extremely polite, but it does the job of describing what happened/didn't happen and asking for more information based on that, which I believe is necessary in this kind of technical forums.

Personally when I search for technical problems and solutions to them in technical forums I can't care less about the "tone" of the language written there (read [some]("http://lwn.net/Articles/249460/") of Linus Torvalds' mail archive to see "tone" probably isn't a big issue for technical discussions). It's the instructions/code/settings that matter. They are technical forums after all -- people don't go there to find heart-warming conversations. And one benefit of using forums (as opposed to phone or unpublished email) is people can share technical information with people who had/have the same problem and who potentially know how to fix it.

Apparently this view is not shared by everyone.

I, too, hope you have a great new year.

---

### Post by jdb on 2009-12-31
> **Mark.ST said:**
> Yes you did, thank you. I think your customer service is quite good, although I think you could improve on certain areas (like putting the latest drivers in the publicly available repositories, documentation for your latest products, etc).

All the drivers that System76 develops are in one driver package which is publicly available.

Updates to packages included with Ubuntu come from the Ubuntu depositories.
System76 machines run pretty much unaltered Ubuntu, any changes are
contained in the one system76 drivers package.

> **Mark.ST said:**
> Linus Torvalds' mail archive to see "tone" probably isn't a big issue for technical discussions.

Linus expresses opinions & distributes knowledge, he's not asking for help.

Even (especially) in the most technical forums, tone will make a big difference in how much help you will get.


jdb

---

### Post by Mark.ST on 2009-12-31
**All the drivers that System76 develops are in one driver package which is publicly available.**

I said "latest drivers," and it's not publicly available *yet*. Tom [said]("http://ubuntuforums.org/showpost.php?p=8516688&postcount=18") it will be publicly available soon (after adding "some other features"). I sent email to Tom to receive the driver that fixes the webcam issue (because when I purchased/received Lemur, it didn't work).

I didn't express any opinions here, it's a fact.

---

### Post by Mark.ST on 2009-12-31
Oh, also, Linus does [ask for help]("https://bugzilla.redhat.com/show_bug.cgi?id=439858") on normal stuff that normal people (like you and me) care, not to mention reporting bugs/errors is part of this "distributing knowledge" thing. 

I do agree the number of responses would be different depending on what's written and how it's written. What I said is I *wish* people become more tolerant on the how it's written part. It's a personal opinion, and yours may be different.

---

### Post by savantelite on 2010-01-04
Well Mark let me commend you on being an early adopter. (hands clapping). Because of your strides the Lemur will be that much better for the next customer...Witch is ME!!!   

It isn't here yet, and its won't be my only machine. But it will be super cool looking and will have never had to taste windows. 

But anyways thanks for paving the way. We other Lemur owners appreciate your work. :guitar:

---

### Post by Mark.ST on 2010-01-05
Thanks savantelite. I want to hear more voices like yours :-)

Other than the Skype issue *I* experienced and the fan noise, it's really a nice laptop, and overall I enjoy the Intel SSD performance too (I don't know if you made this upgrade or not). Although Firefox still takes a few seconds to launch the first time, Google Chrome (chromium-browser) starts in a fraction of a second. Fast.

Keyboard could be a bit better. Right now volume-down/up and brightness-down/up keys (that are used in combination with the Fn key) are placed on F5/F6 and F8/F9, respectively, but it's more intuitive and usable to put them on cursor keys, like many other laptops do for good reason. By default. I pressed **Fn + F4** by mistake a few times when I really wanted to press was **Fn + F5** to turn the volume down, and you know what, **Fn + F4** brings the laptop to the sleep mode! Ugh.

[CENTER][IMG]http://imgur.com/ATraZl.jpg[/IMG]
*"Be Silent" Keys*[/CENTER]

There are also almost-universally-useless keys like **SysRq, Num Lk, Scr Lk, Pause, Break** that (almost) nobody can even explain what they do, let alone use them regularly (I know, many other laptops have these silly keys still).

[CENTER][IMG]http://imgur.com/Mj6Xvl.jpg[/IMG]
*We Survived Until 2010*[/CENTER]

Also it would be nice to have an LED indicator for the webcam. Otherwise it's hard to know if the laptop is seeing me or not. But maybe using an app like cameramonitor makes this a non-issue, I don't know.

---

### Post by siabost on 2010-01-07
Hi,

Mark.ST - glad to read that most of your problems with your laptop have been solved.

I live in the U.K. & have recently bought a netbook by a company called Mesh in the U.K.
The netbook has a built-in Bisoncam Pro similar to (if not the same as) the one in Mark.ST's laptop.
The netbook arrived with Ubuntu 9.04 Netbook Remix loaded which I have now upgraded to 9.10 Netbook Remix.

I've had the same problem with my webcam from day-one as Mark.ST along with the same error messages. Having searched high & low I've not found a solution (until now, possibly).

Question is: would installing the System76 driver version 2.4.0 resolve the problem on my "Mesh" built machine? Or V2.4.2, which isn't on the website yet?

Many thanks :)

---

### Post by thomasaaron on 2010-01-07
siabost, 

No. The System76 Driver would not be able to identify the model of your machine to apply patches. And even if it did, there is no guarantee the patches we apply to our lemur would fix your netbook.

---

### Post by siabost on 2010-01-07
Thanks for the quick reply.

Seeing as I seem to have the same webcam as Mark.ST, do you have any idea where I might be able to get the necessary driver/fix?

Have been pretty much searching everywhere (the manufacturer's site included)!

Thanks again.

---

### Post by thomasaaron on 2010-01-07
Shoot me an email (support...at...system76...dot...com) and I'll send you the latest driver. It's a python application, but it contains the code for compiling the webcam driver.

We're unable to provide support for non-System76 machines, but I'll try to get you pointed in the right direction.

---

### Post by siabost on 2010-01-18
Hi thomasaaron,

You will be a busy man, but any joy with my particular Bisoncam problem?

I sent an e-mail as you helpfully requested but it may have got lost. If so let me know here and I'll resend.

Thanks once again.

---

### Post by thomasaaron on 2010-01-18
Hi, Kenny.

Yeah, I see it there. Sorry, I'll reply to it.

---

