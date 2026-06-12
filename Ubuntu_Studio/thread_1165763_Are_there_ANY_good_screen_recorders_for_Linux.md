---
title: "Are there ANY good screen recorders for Linux?"
date: 2009-05-21
forum: Ubuntu Studio
---

### Post by JK3mp on 2009-05-21
One constant thing i disliked so far in my linux adventure, ( don't get me wrong i LOVE linux itself 100 percent, just this fact/ or arising problem i hate) is that i have yet to find a WORKING Desktop recorder.... i'v tried, gtk-recordMyDesktop, istanbul, xvidcap and one other i can't thnk of name off top of my head, in both gtkrecord and xvidcap it would LAG while recording full screen or with any desktop effects etc. With istanbul it simply freezes up and won't let me STOP recording... is there really any GOOD linux screen recorder out there ? Also i have another issue with .avi file im trying to compress for upload to facebook (but can't find an app that will compress but keep quality) . Anywho if you have a screen recorder suggestion or think you can fix my problem with any of the screenrecorders i've tried just let me know and i'll throw some details out, any help , suggestions or screencast pointers appreciated. Thanks ahead.

-JK3mp

---

### Post by rylleman on 2009-05-21
try VLC.

---

### Post by Geistanon on 2009-05-21
Seems more likely you don't have the hardware than the recorders are poor quality.

---

### Post by JK3mp on 2009-05-21
Perhaps but im running a pretty good graphics card... possibly Just support on my hardware ? And VLC is a media player not a screen recorder.. (not that i know of perhaps im wrong and there's some plugin or something xD )

Additional note: if you meant use it to view the files i already have... im not having truoble viewing files there just not recording right...the .avi file i was talking about plays fine.. i just need to compress it...

---

### Post by rylleman on 2009-05-21
> **JK3mp said:**
> ...And VLC is a media player not a screen recorder.. (not that i know of perhaps im wrong and there's some plugin or something xD )
...
It's also a screen recorder.
Open VLC. Under the first "Media" menu select "Streaming...", then the Capture Device tab where you select "Desktop" for Capture Mode.
Then in the next menu select file and your preferred format.

---

### Post by JK3mp on 2009-05-22
> **rylleman said:**
> It's also a screen recorder.
Open VLC. Under the first "Media" menu select "Streaming...", then the Capture Device tab where you select "Desktop" for Capture Mode.
Then in the next menu select file and your preferred format.

LoL, i know now, explored it after your last post. But i get same results when effects are turned on..

---

### Post by Tikkyca on 2010-02-15
I have the same problem,when i had xp,i used all screen recorders,and all were working,but wheni swiched to linux ubuntu i tryied all screen recorders like you and none works :(

---

### Post by leonsmith on 2010-02-23
I wouldn't hold my breath. I reported the bugs with Istanbul years ago (right after Hardy Heron came out), and every once in a while I get an email that someone has responded to the thread, but it still locks up, never works. I've tried gtk-recordmydesktop also. You have to use Windows for Screen recording with audio like in webcasts or webinars. Sorry.

---

### Post by AutoStatic on 2010-02-24
Try the one from my PPA. It has sane default settings and JACK support enabled.

[https://launchpad.net/~autostatic/+archive/ppa/+sourcepub/939211/+listing-archive-extra](https://launchpad.net/~autostatic/+archive/ppa/+sourcepub/939211/+listing-archive-extra)

---

### Post by misterbk on 2010-02-27
Are you trying to record a very high resolution?  Attempting to encode and stream 1920x1200 video to disk will always be a difficult prospect.

I know Camtasia for Windows is able to record 1280x1024 fairly smoothly on a powerful machine, but requires a very long encode when you stop recording.  The encode sometimes never finishes depending the length of the video.  (Encode time seems to go up exponentially with video length.)


There may be an alternative method for your Linux demos, if you have access to Windows.  Ubuntu runs very well in Sun's VirtualBox, once the machine environment is set up properly.  (Virtual Video RAM is a big gotcha.)  You could record your demos using Windows, running Ubuntu in VirtualBox.

---

### Post by Gaming4JC on 2010-03-09
I've tried several. Istanbul dies due to Xserver: [https://bugs.launchpad.net/ubuntu/+source/istanbul/+bug/494343](https://bugs.launchpad.net/ubuntu/+source/istanbul/+bug/494343)

CamStudio works fair on Windows, a pitty no one has ever ported it...
and Fraps is imo the best for Windows.

Concerning Ubuntu "recordmydesktop" works quite well excepting that it lags soooo badddd. The reason is it only uses 1 cpu thread, and I have an 8 threaded Core i7 920. If some one rewrites the app for multi-threading we might have something...

---

### Post by ElSlunko on 2010-03-11
The fastest I could get recordmydesktop to record at was 25 FPS. That's pretty smooth but not 30fps smooth.

Edit : Scratch that, I can do 30fps. For some reason totem wouldn't play the file but vlc did.

---

### Post by AutoStatic on 2010-03-12
> **ElSlunko said:**
> For some reason totem wouldn't play the file but vlc did.That's probably because recordMyDesktop doesn't use sane defaults, Totem chokes on the rendered ogv. Did you try the patched version from my PPA?

[http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/)

---

### Post by ElSlunko on 2010-03-12
> **AutoStatic said:**
> That's probably because recordMyDesktop doesn't use sane defaults, Totem chokes on the rendered ogv. Did you try the patched version from my PPA?

[http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/)

Nope. Just used the one in the repos. I have to do a couple of tutorials soon so I'll give yours a whirl as soon as I get started on those projects.

---

### Post by GodLikeCreature on 2010-03-12
My card is nothing special (Intel 82Q35 Express Integrated Graphics Controller), but I can get decent results (50% successful capture ratio at 1024x768 with Compiz ON) recording at somewhat standard resolutions with XvidCap.  As some other poster mentioned, it just goes downhill as soon as you try the high resolutions.  When I do full screen, I get around 20% successful ratio at 1680x1050.  

Having said so, XvidCap was the only application that even worked for me.  After trying alternatives for KDE and GNOME, on top of Ubuntu, Mandriva, Fedora or OpenSUSE, nothing could even come close.

Having said so, when I record videos for tutorials or something like that, I try to work around the problem by slowing down.  It feels kinda silly, but it does compensate a bit the low capturing ratio and makes the videos somewhat watchable.

Good Luck!

---

### Post by ElSlunko on 2010-03-12
Someone mentioned a different front end for gtk-recordmydesktop a while back but I didn't bother to write it down.

---

### Post by AutoStatic on 2010-03-15
gtk-recordMyDesktop is already a front end for recordMyDesktop. Another front end for recordMyDesktop is qt-recordMyDesktop.
But a different front end won't make any difference at all.

---

### Post by chill32 on 2010-04-01
ive tried all of them none of them work

---

### Post by hxcobd on 2010-04-15
I just wanted to bump this because Autostatic's patched Recordmydesktop works like a DREAM.

I could never get the official version to work properly for any videos over 5 seconds in length, but this patched version runs really, really well.

I'm on a 32-bit, 1.2ghz Core2Duo, and having no issues at all capturing at 20 fps (more than enough for webcast tutorials).

Thanks, Autostatic! I recommend everyone try his patched release.

After you download his patched .deb, open Synaptic and download the GTK frontend as well to complete the package. Do NOT download the original Recordmydesktop from the repo, it's old and sucks.

---

### Post by krige on 2010-04-27
> **rylleman said:**
> It's also a screen recorder.
Open VLC. Under the first "Media" menu select "Streaming...", then the Capture Device tab where you select "Desktop" for Capture Mode.
Then in the next menu select file and your preferred format.

I tried that but nothing happens.

Media / Streaming... / Capture Device
    Capture Mode = Desktop
    Desired frame rate = 30
then I press Stream, then Next
    New destination = File (where does it save it???)
then Next, then I press Stream and nothing happens...

---

### Post by mshaik on 2010-04-29
vlc does the same for me too...and gtk-recordmydesktop is ok for 20fps...also, the encoding time for recordmydesktop is like an eternity...

---

### Post by krige on 2010-04-29
I would have liked to have a native Linux application as screen recorder but unfortunately I have found all the available ones lacking some feature or another.

---

### Post by pietro_spina on 2010-04-30
> **hxcobd said:**
> I just wanted to bump this because Autostatic's patched Recordmydesktop works like a DREAM.

I could never get the official version to work properly for any videos over 5 seconds in length, but this patched version runs really, really well.

I'm on a 32-bit, 1.2ghz Core2Duo, and having no issues at all capturing at 20 fps (more than enough for webcast tutorials).

Thanks, Autostatic! I recommend everyone try his patched release.

After you download his patched .deb, open Synaptic and download the GTK frontend as well to complete the package. Do NOT download the original Recordmydesktop from the repo, it's old and sucks.

Would Autostatic share what the changes are to make **sane** settings? I looked at his ppa page and didn't see a changelog.

I see the .diff file but I'm not really capable of making sense of that. (I did open it and take a look though)

Cheers,
P

---

### Post by AutoStatic on 2010-04-30
> **pietro_spina said:**
> Would Autostatic share what the changes are to make **sane** settings? I looked at his ppa page and didn't see a changelog.

I see the .diff file but I'm not really capable of making sense of that. (I did open it and take a look though)Hello pietra_spina, sure! Check [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027)
I've added two patches of which one that contains the sane defaults: [http://launchpadlibrarian.net/38108166/sanity.patch](http://launchpadlibrarian.net/38108166/sanity.patch)

As you can see, these defaults are hardcoded and can't be altered through a configuration file.

---

### Post by wackyslacky on 2010-05-06
> **AutoStatic said:**
> That's probably because recordMyDesktop doesn't use sane defaults, Totem chokes on the rendered ogv. Did you try the patched version from my PPA?

[http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/)

Hi AutoStatic,

Is there a way I could build your RecordMyDesktop files for slackware?

I really need a screen recorder, but RMD only encodes to the 6th cache file, which is about 3/4 of the capture :icon_frown:

---

### Post by AutoStatic on 2010-05-07
Hello wackyslacky, 

patching and compiling recordMyDesktop for a Slackware install goes way beyond the scope of this forum though so I think it's best to try your luck on a dedicated Slackware forum. And unfortunately, you can't use my files, you need an Ubuntu or Debian install for that unless you can **apt-get source** or **dpkg-source -x** my files on a Slackware install. But then again, it's best to ask that on a dedicated forum.

Best,

Jeremy

---

### Post by andrew.46 on 2010-05-08
Hi wacky,

> **wackyslacky said:**
> Is there a way I could build your RecordMyDesktop files for slackware?

A start is [here]("http://slackbuilds.org/result/?search=RecordMyDesktop&sv=13.0"), then add in any patches you want.

All the best,

Andrew

---

### Post by wackyslacky on 2010-05-08
Thanks AutoStatic and Andrew, I will try a slackware forum. I can build my own slackware packages, I have just never patched source code before.

---

### Post by andrew.46 on 2010-05-10
Hi wackyslacky,

> **wackyslacky said:**
> Thanks AutoStatic and Andrew, I will try a slackware forum. I can build my own slackware packages, I have just never patched source code before.

The conventional way is to incorporate the patching within your slackbuild, that is copy the source to TMP, run the patch and then compile. For example I patch the standard slrn installation on Slackware as follows:

```

cd $TMP
rm -rf slrn-$VERSION
cp -r $CWD/slrn-$VERSION $TMP
[B][COLOR="Red"]cd slrn-$VERSION || exit 1

# My patch:
patch -p0 < $CWD/custom_os.patch[/COLOR][/B]

chown -R root:root .
find . \
  \( -perm 777 -o -perm 775 -o -perm 711 -o -perm 555 -o -perm 511 \) \
  -exec chmod 755 {} \; -o \
  \( -perm 666 -o -perm 664 -o -perm 600 -o -perm 444 -o -perm 440 -o -perm 400 \) \
  -exec chmod 644 {} \;
etc etc etc...

```

You can see that the patch sits in the working directory, for your own patch you would need to probably adjust *-pnum*.

All the best,

Andrew

---

### Post by juanimela on 2010-05-17
Recording with 3d effects and high resolution forces a lot of information to be written to the hard disk. No matter how much cpu and ram you have, it's the hard disk speed that counts. You can try a ram disk, so that the temporal files are written onto RAM, not the hard drive.

To create a ram disk

mkdir /tmp/ramdisk; chmod 777 /tmp/ramdisk
mount -t tmpfs -o size=256M tmpfs /tmp/ramdisk/

And then you select /tmp/ramdisk as the work folder for
gtk-recordmydesktop. You can also play with options such as "encode on the fly", frame rate and such. Sorry to crosspost, but this problem has haunted me for some time, and I'm so happy to have found the solution!

---

### Post by daemonraco on 2010-08-06
> **AutoStatic said:**
> That's probably because recordMyDesktop doesn't use sane defaults, Totem chokes on the rendered ogv. Did you try the patched version from my PPA?

[http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/r/recordmydesktop/)
Excelente, this is what I needed.
Do you have any suggestions to conver the ogv file to flv?

thanx!

---

### Post by AutoStatic on 2010-08-06
Try Pitivi but keep in mind your converting from one lossy format to another so quality will degrade a bit.

---

### Post by LuridCinema on 2010-08-07
ffmpeg to the rescue. you can easily capture your desktop using the below ffmpeg command...

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x720 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```

I installed PulseAudio sound Control and got the sound working as well
--------------------------------------------------------------------------------------------------

You can convert ogv to flv w/ ffmpeg by using the below :

```
ffmpeg -i INPUT.ogv -s 1280x720 -sameq -ar 44100 OUTPUT.flv
```

---

### Post by fmcgorenc on 2011-04-05
there is a great screen recorder called "camstudio".
its for windows but its also opensource so someone could port it to linux. here is the link [http://camstudio.org/]("http://camstudio.org/")

---

### Post by fatriff on 2011-05-11
> there is a great screen recorder called "camstudio".
its for windows but its also opensource so someone could port it to linux. here is the link [http://camstudio.org/](http://camstudio.org/)

Yeah OK.. Let us know when you've spent 6 months of your life porting it then :P

KaZam is the only Screen Recorder that works perfecto, it's simple and it records multiple desktops even.. By the way.. You can also use Kdenlive to record your desktop.

[http://whyareyoureadingthisurl.wordpress.com/2010/06/29/introducing-a-screencaster-called-kazam/](http://whyareyoureadingthisurl.wordpress.com/2010/06/29/introducing-a-screencaster-called-kazam/)

Kazam isn't in the repos yet as it's less than a year old but you can add the ppa

deb [http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu](http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu](http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu) maverick main

---

### Post by snowz on 2011-05-12
i would give a vote for **Kazam**. Its **EASY TO USE + HD**

---

### Post by sssseeee on 2012-10-27
Try Kazam.
It's a great screencaster, however you do need to add a repository to use it.

*sudo apt-add-repository ppa*:*kazam-team/stable-series*
[I]sudo apt-get update
sudo apt-get install kazam
[/I]enjoy:guitar:

---

