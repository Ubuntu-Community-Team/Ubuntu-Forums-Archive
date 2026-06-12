---
title: "Petition: Mozilla &amp; Canonical fix HTML5 video NOW"
date: 2014-02-26
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2014-02-26
UPDATE:  this situation can only be resolved if canonical and mozilla put some effort into finding a solution for it... I ask everyone to mail and nag mozilla and canonical until they act.


 Fact:  Unlike their windows/android versions (which ship with built in h.264 support), the linux version of firefox relies upon gstreamer0.10-ffmpeg's ability to decode h.264 videos (~95% of all html5 videos).

 As it stands, gstreamer0.10-ffmpeg is no longer available in ubuntu14.04/debian7.

Gstreamer0.10-ffmpeg's instalation is still possible, yes... but it does force the user to either compile from source or add external ppa's. It also requires the user to resolve several technical issues like dependency problems/etc.

 
  We hereby request Mozilla to add, once and for all, native h.264 support to the linux version of Firefox (like they have done for their windows/android/osx versions) and not depend in external packages for h.264 decoding. 
 
 OR in extremis

 Canonical must make the FFmpeg 2.1.3 package easily available in ubuntu's software center and Mozilla needs to update firefox's gstreamer support to work with this current version.
 

  It is indeed a sad state of affairs, when one can enjoy flash-free html5 video viewing in windows but not on linux systems. 


[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=729203#410](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=729203#410)







_____________________________________________________________________________________________________________________________________________________________________________________________

EDITED: original post

I have tried installing through the software center and apt getting in the terminal

"There isn&#8217;t a software package called &#8220;gstreamer0.10-ffmpeg&#8221; in your current software sources."

Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gstreamer0.10-ffmpeg' has no installation candidate




 I have both universe and multiverse enabled.

 Without gstreamer I can't get youtube videos to play above 360p


edited  to add this:  when installing vlc 2.1.2-2build1 it creates no  icons or shows up in right click context menus, you can only launch it  from the terminal.

---

### Post by kostkon on 2014-02-26
It isn't available anymore for 0.10 it seems and its replacement in 1.0 if I'm not mistaken is [gstreamer1.0-libav]("http://packages.ubuntu.com/trusty/gstreamer1.0-libav").

So if you were planning to use it in a script you could just use gst 1.0 instead.

---

### Post by kostkon on 2014-02-26
> **nomenkultur said:**
>  Without gstreamer I can't get youtube videos to play above 360p
Adobe flash plugin does not depend on gst. Do you use some other software to play youtube videos?

---

### Post by nomenkultur on 2014-02-26
I don't use flash.

In order to play html5 hd videos on firefox you must have gstreamer0.10-ffmpeg

 I can't seem to find gstreamer1.0-ffmpeg or gstreamer0.10-ffmpeg

 kind of worried, does this mean tere's no h.264 support in ubuntu? what if I pay for that specific codec is there a way?


 edit: my gfx chip has paid for the right to use h.264 codecs, this is really a scumbag move by mozilla/google to ship h.264 codecs in firefox/chromium windows and not ship them in linux versions

 f... typical

---

### Post by mc4man on 2014-02-26
I would think the best solution would be for FF to support gst-1.x
Did a little fool around & did get html5 support in FF in 14.04 but I have to wonder if there is a good reason why Ubuntu has chosen not to provide the 0.10 plugin??

Either - 
the plugin can't work with current libav
or it can but there is some security flaw with the 0.10 plugin
 Out of curiosity, did you try using saucy's 0.10-ffmpeg plugin? (I didn't, went another direction with the plugin using internal supplied libav
If the reason is that it can't work with current libav libs then I'll provide a link to 0.10 ffmpeg package for trusty if desired, have in a ppa

---

### Post by nomenkultur on 2014-02-27
Mcman I have no idea if FFox 30 does or does not support gstreamer ffmpeg 1.0 as I don't have access to it (ffmpeg, I have ffox30)...
 I believe it does as in about:config they have the flag for gstreamer.

All I know for sure is that gstreamer-libav is useless as neither FFOX or chromium accept it to decode html5 hd videos. Why this pos even exists is beyond me (probably from the mind that brought you iceweasels).

  debian decided to use libav instead of gst-ffmpeg and it's a horrible mess, I was not affected by this in 12.04 or 13.04 but I am now...

 Hopefully someone can get Gstreamer 1.0 ffmpeg to ubuntu quickly as it's ridiculous that one can only remain flash free on windows and not ubuntu.

 even debian is backtracking and apparently they are going to use ffmpeg again, here's a file I found hope someone manages to make it work on ubuntu:

[URL="https://bugs.debian.org/cgi-bin/bugreport.cgi?msg=410;filename=ffmpeg_2.1.3-1.debian.tar.xz;att=1;bug=729203"]https://bugs.debian.org/cgi-bin/bugreport.cgi?msg=410;filename=ffmpeg_2.1.3-1.debian.tar.xz;att=1;bug=729203
[/URL]

---

### Post by mc4man on 2014-02-27
This has nothing to do with libav vs fffmpeg. As I mentioned the most likely reason the plugin isn't provided is it isn't compatible with current libav shared lib in 14.04
Even though the plugin is named 'ffmpeg' in saucy it uses libav, not ffmpeg, that is & was the choice of Gstreamer, not Debian or Ubuntu

So in that case the only way to provide the 0.10 plugin would be to use the gstreamer provided libav in the plugin's soure, something that Debian/Ubuntu don't do.
(they use the system libs, & likely would be unwilling to change that policy, you could try a bug report & see what shakes out.

Here for the gstreamer1.0-libav plugin I'm currently using a libav embedded build for various unrelated reasons, atm it's also slightly superior to the Ubuntu repo version though if Ubuntu goes to the next libav version this cycle then it wouldn't be. (the reason I built it wasn't for the bug fixes it contains, something else of no importance in this thread.

In any event if you wish to try a 0.10 'ffmpeg' gstreamer plugin for 14.04 it's here for a little while, this ppa isn't permanent. If I think it's good & without issue will move to a more permanent ppa at some point (the ppa also has the gstreamer1.0-libav plugin with libav embedded.

[https://launchpad.net/~mc3man/+archive/testing](https://launchpad.net/~mc3man/+archive/testing)
Changes to the source are available here, done to allow building - 
[https://launchpad.net/~mc3man/+archive/testing/+files/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1%7Etrusty_0.10.13-5ubuntu1%7Etrusty2.diff.gz](https://launchpad.net/~mc3man/+archive/testing/+files/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1%7Etrusty_0.10.13-5ubuntu1%7Etrusty2.diff.gz)

As you can see in screen it has no dependency to system libav libraries
In short tests here it works fine in YT  once FF is set up for html5, personally see no advantage to html5 over flash but that doesn't really matter

---

### Post by Yellow Pasque on 2014-02-28
Firefox gst1.0 support is (finally) coming.
[https://bugzilla.mozilla.org/show_bug.cgi?id=806917](https://bugzilla.mozilla.org/show_bug.cgi?id=806917)

---

### Post by Gavin77 on 2014-02-28
You can install the saucy version from [http://packages.ubuntu.com/saucy/gstreamer0.10-ffmpeg](http://packages.ubuntu.com/saucy/gstreamer0.10-ffmpeg)
It works fine for me.

---

### Post by mc4man on 2014-02-28
> **Gavin77 said:**
> You can install the saucy version from [http://packages.ubuntu.com/saucy/gstreamer0.10-ffmpeg](http://packages.ubuntu.com/saucy/gstreamer0.10-ffmpeg)
It works fine for me.
I had asked the Op to check that, I guess he didn't...
If in fact the saucy  package works in 14.04 then there is no issue with compat on the libav shared libs. In that case any concerned user should file a bug on why no trusty build
As far as the current nightly ppa FF 30 it still doesn't appear to support gst-1.x, possibly that is coming shortly??

---

### Post by Yellow Pasque on 2014-02-28
> In that case any concerned user should file a bug on why no trusty build
It's already been done: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556)

Also, here's why it was removed: [https://bugs.launchpad.net/ubuntu/+source/ffmpeg-php/+bug/1253071](https://bugs.launchpad.net/ubuntu/+source/ffmpeg-php/+bug/1253071)

---

### Post by Hazzabin on 2014-02-28
Thank you mc4man, your ppa solved my issues which was quite different to the op's

---

### Post by nomenkultur on 2014-03-01
"I had asked the Op to check that, I guess he didn't..."

 I neglected this issue once I solved it, didn't mean to:

 Saucy ffmpeg package does indeed work with 14.04. 

 Furthermore FF30 has the gstreamer flag enabled by default ... so h.264 based html5 videos play and play well  (canonical should look into making ffmpeg 0.10 or 1.0 available in trusty repos)


 libav is useless.

 
 Now, and this should give you all pause to think, I am able to enjoy HD html5 videos in numerous sites, from vimeo to rt, but in youtube...

 in youtube they keep playing most videos in 360p

 some, very few, let you change to 720, the great majority keep their 360p resolution

 
[h=3]What does this browser support?[/h]   
[LIST]
[*]       [IMG]http://s.ytimg.com/yts/img/pixel-vfl3z5WfW.gif[/IMG]   
                       HTMLVideoElement     
 


[*]       [IMG]http://s.ytimg.com/yts/img/pixel-vfl3z5WfW.gif[/IMG]   
                       H.264     
 


[*]       [IMG]http://s.ytimg.com/yts/img/pixel-vfl3z5WfW.gif[/IMG]   
                       WebM VP8     
 

[/LIST]



 turns out google came up with a thing called 

                      Media Source Extensions


   

 fairly recently, I believe, a couple of months ago I was able to watch all html5 videos in whatever resolution I desired.

 I would say this feels like a shady tactic by google to push their chrome browser

---

### Post by Yellow Pasque on 2014-03-01
> **nomenkultur said:**
> (canonical should look into making ffmpeg 0.10 or 1.0 available in trusty repos) ...  libav is useless.

Again, it is not the fact that libav or gstreamer1.0-libav is "useless." Programs that use gstreamer1.0 and use gstreamer1.0-libav can play the video formats you're referring to.

The problem is that firefox has been very slow to move to gstreamer1.0, and it may or may not have been enabled in the build you're using (link to the FF ppa you're using if you want us to look at build log).

---

### Post by QDR06VV9 on 2014-03-01
Thanks mc4man for the PPA!
Working good here!;)

---

### Post by mc4man on 2014-03-01
Todays nightly FF30 build seems to be good to go with gstreamer1.0-libav
Edit: - actually it ^ doesn't..

Is there anything else that needs the 0.10 ffmpeg plugin??

---

### Post by Yellow Pasque on 2014-03-01
Doug, as you may know, I run Debian sid(uction). I also use debmultimedia repo, which substitutes ffmpeg for libav, and it offers gstreamer0.10-ffmpeg package.

Here's a quick list of packages dependent on it:
Depends: toonloop, foobnix, landell, miro, betaradio, flumotion
Recommends: snappy, morituri, pidgin-sipe, exaile, gnash-common, gnome-subtitles, kde-telepathy-call-ui
Suggests: subtitleeditor, pitivi, soundconverter, guayadeque

---

### Post by mc4man on 2014-03-01
> **Temüjin said:**
> Doug, as you may know, I run Debian sid(uction). I also use debmultimedia repo, which substitutes ffmpeg for libav, and it offers gstreamer0.10-ffmpeg package.

Here's a quick list of packages dependent on it:
Depends: toonloop, foobnix, landell, miro, betaradio, flumotion
Recommends: snappy, morituri, pidgin-sipe, exaile, gnash-common, gnome-subtitles, kde-telepathy-call-ui
Suggests: subtitleeditor, pitivi, soundconverter, guayadeque

Took a quick look there, what they're doing with gstreamer0.10-ffmpeg is the same I did here - build off of the included source,  not the system libs.
(most likely the included libav as the inc. ffmpeg is incomplete

---

### Post by nomenkultur on 2014-03-02
libav with firefox 28.0~b2+build1-0ubuntu2, that is now shipping with trusty, does not work.

libav with ffox30 from nightly.mozilla.org  does not work.

ffmpeg0.10 works with both, would like to try ffmpeg 1.0

 hence why I called it useless

---

### Post by mc4man on 2014-03-02
> **nomenkultur said:**
> libav with firefox 28.0~b2+build1-0ubuntu2, that is now shipping with trusty, does not work.

libav with ffox30 from nightly.mozilla.org  does not work.

ffmpeg0.10 works with both, would like to try ffmpeg 1.0

 hence why I called it useless
I rechecked & FF 30 from daily ppa does not use gst-1.x (forgot to log out after removing 0.10 plugin

So until such time as it does just use the 0.10 plugin
There is no "ffmpeg 1.0"  plugin & the 0.10 plugin uses libav so not "useless"

---

### Post by nomenkultur on 2014-03-09
update:

 it no longer lets you install gstreamer0.10 

 "dependency is not satisfiable  libavcodec 53  libavcodec 53 "


 am I missing something or does this pretty much kill hmtl5 videos???

---

### Post by Gavin77 on 2014-03-09
I noticed that last night. I removed gstreamer0.10-ffmpeg because I was getting crashes with vlc (I don't think it's actually related though) and couldn't reinstall it afterwards as the dependencies have been removed from the repo.  When trying youtube.com/html5 I don't have h.264 decoding available anymore.

---

### Post by mc4man on 2014-03-09
> **Gavin77 said:**
> I noticed that last night. I removed gstreamer0.10-ffmpeg because I was getting crashes with vlc (I don't think it's actually related though) and couldn't reinstall it afterwards as the dependencies have been removed from the repo.  When trying youtube.com/html5 I don't have h.264 decoding available anymore.

choices - 
Wait till FF supports gst1.x
Try deb multimedia package
Build your own package, configure not to use system libs
Use the test ppa I put up, post # 7

---

### Post by nomenkultur on 2014-03-09
if it wasn't for your ppa I would no longer be able to use ubuntu...

 I hope canonical realizes the seriousness of the lack of (as it stands) h.264 support in firefox/chromium

---

### Post by mc4man on 2014-03-09
The main issue from Ubuntu's side is that while the 0.10 package could be usable if libavcodec53, ect. were in trusty repos, (which they could be as different name),  it's quite likely that it cannot be built or easily built.
To do that there would need to be 2 versions of the -dev packages & that's not going to happen or can't happen  
(They are simply named libavcodec-dev, ect., not libavcodec54-dev, ect.

So really the ultimate solution has to come from FF & or Ubuntu's FF builds

To note - 
as that is just a temp ppa I'll probably move the package to this currently empty ppa, (maybe
[https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

If so then I'd also include some or all of the media related packages I've been creating in my personal trusty proposed paa (not recommended to use as some are quite 'personal', nothing is properly described, & always slight possibility that a package there deps on trusty -proposed
[https://launchpad.net/~mc3man/+archive/trusty-prop](https://launchpad.net/~mc3man/+archive/trusty-prop)

If I do decide to maintain a trusty media ppa then any suggestions to improve existing or add additional would be welcome

---

### Post by ricardisimo on 2014-05-05
Anything and everything remotely connected to avconv or ffmpeg (including this and Audacity, among others) has become a nightmare under "Trusty". Tell me this: can I spare myself a lot of heartache by downgrading to Saucy, or migrating to Fedora? Because I'm not seeing any pluses to 14.04.

---

### Post by cariboo on 2014-05-05
Seeing Trusty has been released, and this has nothing to do with Utoplc. Thread closed.

---

