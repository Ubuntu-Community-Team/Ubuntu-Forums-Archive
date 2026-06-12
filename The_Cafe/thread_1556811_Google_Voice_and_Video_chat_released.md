---
title: "Google Voice and Video chat released"
date: 2010-08-19
forum: The Cafe
---

### Post by Tristan Schmelcher on 2010-08-19
FYI, Google released voice and video chat for Linux today. [http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html](http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html)

---

### Post by Tristan Schmelcher on 2010-08-19
FYI, Google released voice and video chat for Linux today. [http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html](http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html)

---

### Post by Tristan Schmelcher on 2010-08-19
FYI, Google released voice and video chat for Linux today. [http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html](http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html)

---

### Post by MCVenom on 2010-08-19
> **Tristan Schmelcher said:**
> FYI, Google released voice and video chat for Linux today. [http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html](http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html)
Thanks for bringing the news Tristan, but please remember:

1. Bumping rather old threads is discouraged

2. You don't have to post this in every thread on the subject, the best thing to have done was to start a new thread.

Not trying to be a jerk, just keep that in mind. :P

---

### Post by fragos on 2010-08-19
Thanks for sharing Tristan. I've just downloaded and installed. Can't wait to have an opportunity to try it.

---

### Post by Tristan Schmelcher on 2010-08-19
Sorry, just wanted to make sure anyone subscribed to the old threads heard the news. I'll keep in mind your advice for next time.

---

### Post by Dustin2128 on 2010-08-19
> **Tristan Schmelcher said:**
> FYI, Google released voice and video chat for Linux today. [http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html](http://gmailblog.blogspot.com/2010/08/use-linux-now-you-can-video-chat-too.html)
necromancy... where did you even find this thread? Where does anyone find 2-5 year old threads to post to for that matter?

---

### Post by whiskeylover on 2010-08-19
> **Dustin2128 said:**
> necromancy... where did you even find this thread? Where does anyone find 2-5 year old threads to post to for that matter?

He found a bunch of threads on the same subjects and necromanced all of them.

---

### Post by Sef on 2010-08-20
Moved one more to this thread.

---

### Post by Exilant on 2010-08-20
That seems to be i386 only, at least i can't seem to get an 64-bit version, so still no video chat in linux for me :(

---

### Post by jrusso2 on 2010-08-20
I only see .deb packages not all Linux is based on Debian.

---

### Post by MCVenom on 2010-08-20
> **jrusso2 said:**
> I only see .deb packages not all Linux is based on Debian.
Alien. :P

Also, the top three posts are all the same... Can someone clean it up? :P

---

### Post by samalex on 2010-08-20
Cool... but unfortunately my webcam died in my laptop a couple of weeks ago.  I could send it back in for warranty repair, but honestly I'd rather not part with my laptop for that long since I use it daily.  I'll probably just invest in a USB webcam that I can clip to the monitor which would be better anyway since the webcam points at my heck and chest with the way I angle it on my desk.  

Sam

---

### Post by doorknob60 on 2010-08-20
When I click download, it gives my an amd64 deb. So good, it supports 32 and 64 bit, that's the important part :) Getting around the fact that it's deb is very easy (deb2targz, etc.). I'm sure somebody will make an AUR package for that soon, don't think it'll be me this time though (all my friends use Skype).

---

### Post by hotweiss on 2010-08-20
Ironically, it doesn't work with Google's Chrome browser:(

---

### Post by Exilant on 2010-08-20
Depending on the browser id string, i can get the x64 package. however, it doesn't seem to work, although it installs fine, in all browsers I tested I got
"Unfortunately, we do not yet have voice and video chat available for your operating system."

(tested in chromium (from the ppa:chromium-daily/dev), firefox and konqueror)

---

### Post by fragos on 2010-08-20
I'm running Chrome 6.0.472.36 beta on Ubuntu 32 bit OS. I installed the deb and after terminating and restarting Chrome, Gmail Settings recognizes my system as supporting video chat. Now all I need is someone to try it with.

---

### Post by Exilant on 2010-08-20
lucky you! tell us if it worked :)

---

### Post by NCLI on 2010-08-20
> **doorknob60 said:**
> When I click download, it gives my an amd64 deb. So good, it supports 32 and 64 bit, that's the important part :) Getting around the fact that it's deb is very easy (deb2targz, etc.). I'm sure somebody will make an AUR package for that soon, don't think it'll be me this time though (all my friends use Skype).
Google says they'll be releasing an RPM version soonish.

---

### Post by Dustin2128 on 2010-08-20
> **BlackOtaku said:**
> Alien. :P

I'll test it out later today and let everyone know how it goes on non-debian based systems.

---

### Post by LuxeSaber on 2010-08-21
I have had success installing the .deb and had to reboot to get it working. My only issue at this point is that the audio only works one-way. Video works from both ends, and I can hear the audio from the other person, but they can not hear my audio.

In windows I have no issues with my webcam, in fact my microphone works perfectly. The only issue I have is one-way audio. Anyone else having this issue or is it just me?

Ubuntu 10.04
UVC Winbook webcam

---

### Post by samijam on 2010-08-21
I've just installed 32-bit Chrome on 64-bit Ubuntu(because I want flash to work right) and I'd also like to try this new video chat plugin.  I have confirmed that it is in fact a 32-bit Chrome that I'm using by:

sam@sam:~$ file /opt/google/chrome/chrome
/opt/google/chrome/chrome: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped


However when I try to download this plugin from google it is downloading google-talkplugin_current_amd64.deb

I'm assuming this is due to the useragent string reporting 64-bit, but shouldn't it report the architecture of the browser and not the system?

---

### Post by noelvh on 2010-08-22
Well I saw this on the OMG blog, ran out and tested it. All I can say is it WORKS!.
I have old web cams and to get skype to work I have to jump through hoops, while waring a tin foil hat, and holding a coat hanger in each hand. Well not really but I have to run skype with a code in font of the command. This installed and worked. I am running an older IBM T43 with ati R x300, compiz running full out, 2gb ram. There was a bit of lag in full screen on my window but not the fare end window. I think that is compiz, causing the lag, but I saw the same with skype. When I ran skype I would hit the compiz icon and turn compiz off.

Noel

---

### Post by Exilant on 2010-08-22
regarding the architecture issue: downloading the package and listing its contents gives you a
file /etc/cron.daily/google-talkplugin,

which is something I really don't like in my packages, it contains a reference to a debian repository

"deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main"

unfortunately that is non-browsable, but it might help finding the right package.

Apart from that, it doesn't work for me. the plugin shows up in firefoxes plugin list, but google talk does behave as without the plugin.

edit reason: had for some reason written half the reply in german, sorry.

---

### Post by PGScooter on 2010-08-24
great! works well for me on lucid 64-bit on chromium and firefox. no configuration necessary. I think I did have to restart my computer though.

---

### Post by gradinaruvasile on 2010-08-24
> **hotweiss said:**
> Ironically, it doesn't work with Google's Chrome browser:(

It does for me.

---

### Post by gnothi on 2010-08-25
> **LuxeSaber said:**
> I have had success installing the .deb and had to reboot to get it working. My only issue at this point is that the audio only works one-way. Video works from both ends, and I can hear the audio from the other person, but they can not hear my audio.

In windows I have no issues with my webcam, in fact my microphone works perfectly. The only issue I have is one-way audio. Anyone else having this issue or is it just me?

Ubuntu 10.04
UVC Winbook webcam

I experienced a similar audio problem when I plugged my headset into the connectors located at the **front** of my desktop PC. I resolved the problem by setting my Ubuntu **sound preferences** to use Microphone 2 (instead of Microphone 1, which is the **rear** connector on my PC).

Also make sure that your mic isn't muted in sound preferences, and that its volume setting isn't too low (or too high, which amplifies line noise).

I haven't yet got the plugin to work in Firefox 3.6.8 on 64-bit Karmic (with 32-bit libs), but it's okay with [_Chromium_](https://launchpad.net/~chromium-daily/+archive/stable).

---

### Post by Tristan Schmelcher on 2010-08-25
FYI, anyone experiencing problems should post on the Google help forums at [http://www.google.com/support/forum/p/chat/label?lid=18819d87e4369fa5&hl=en](http://www.google.com/support/forum/p/chat/label?lid=18819d87e4369fa5&hl=en) so that Google engineers can respond.

---

### Post by gnothi on 2010-08-26
The Google plugin isn't recognised at all by my Firefox 3.6.8, while it works okay with the Chromium 5.0 and [_Epiphany_](http://projects.gnome.org/epiphany/) 2.28 browsers. This is the case for both my whitebox desktop PC with 64-bit Ubuntu Karmic, plus my HP laptop with dual-boot of 64-bit Lucid and Karmic. Each has Flash version 10.1.82.76 and Java 6 Update 20.

My Firefox is from a [_Mozilla_](http://www.mozilla.com/firefox/firefox.html) tarball download, installed in my /opt folder -- not the version(s) from Ubuntu's software respositories.

I called my cell phone and a land-line to configure this Gmail feature, so it's strictly an audio exercise thus far, using just a headset.


Desktop: AMD Athlon 64 X2 5200+ CPU, GeForce 8400GS video with nVidia 256.44 drivers.
Laptop: Intel Core 2 Duo P7370 CPU, Radeon HD4330 video with ATI Catalyst 10.7 and 10.8 drivers.

---

### Post by samalex on 2010-08-26
Worked here using Firefox on 64-bit 10.04, but I only tested the audio since my webcam is dead.  I'd rather have an external one anyway, so when I get one I'll test the webcam part.

What I liked is I'm already using Google Voice with my cell-phone, so calling someone from my Gmail account shows my Google phone number in the Caller ID.  So back to a single number for everything which is neat. I need to see if I can configure Google voice to call me in Chat first if I'm on, then jump to Cell if I don't answer.

Neat stuff Google!  

Sam

---

### Post by treesurf on 2010-08-26
You can configure Google voice to call you on both your phone and in Chat.  Then just pick up whichever one you like.  It's in the Google Voice phone settings.

It's working well for me on Google Chrome.  I like it, just click a phone number on a webpage and I'm on the phone on my computer.

---

### Post by Tristan Schmelcher on 2010-08-26
@gnothi Your Mozilla tarball in /opt probably doesn't know where to look on your hard drive for plugins. google-talkplugin symlinks its plugins to /usr/lib/mozilla/plugins/, so you probably have to symlink them to /opt/<whatever>/plugins/ too.

---

### Post by gnothi on 2010-08-27
> **Tristan Schmelcher said:**
> @gnothi Your Mozilla tarball in /opt probably doesn't know where to look on your hard drive for plugins. google-talkplugin symlinks its plugins to /usr/lib/mozilla/plugins/, so you probably have to symlink them to /opt/<whatever>/plugins/ too.

I'm aware of that sort of thing, from getting the Flash plugin to work. I got into the practice of manually downloading and installing Firefox and Flash in order to have the latest versions regardless of whatever is available in the Linux distro repositories.

Firefox and [_Swiftfox_](http://getswiftfox.com/), both installed from tarballs, *fail* to see the Google plugins, regardless of where the symlinks reside. Symlinks to the Flash plugin work. I ensure that plugin symlinks reside in the following folders ...

/opt/firefox/plugins
/opt/swiftfox/plugins
/usr/lib/mozilla/plugins
/usr/lib/firefox/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-3.6.8/plugins
/usr/lib/xulrunner/plugins
/usr/lib/xulrunner-addons/plugins
/usr/lib/xulrunner-1.9.1.9/plugins
~/.mozilla/plugins

No Google videophone joy for Firefox.

For this Gmail feature, Epiphany is an acceptable alternative, but I'd prefer Firefox.

---

### Post by Tristan Schmelcher on 2010-08-27
Hmm, perhaps you are using a 32-bit version of Firefox? [http://www.google.com/support/forum/p/chat/thread?tid=14dc84273223eaa5&hl=en](http://www.google.com/support/forum/p/chat/thread?tid=14dc84273223eaa5&hl=en)

---

### Post by gnothi on 2010-08-27
> **Tristan Schmelcher said:**
> Hmm, perhaps you are using a 32-bit version of Firefox? [http://www.google.com/support/forum/p/chat/thread?tid=14dc84273223eaa5&hl=en](http://www.google.com/support/forum/p/chat/thread?tid=14dc84273223eaa5&hl=en)

With symlinks to the plugin files for **i386** (extracted from Google's [_DEB package_](http://dl.google.com/linux/direct/google-talkplugin_current_i386.deb)), Firefox won't start up at all. It identifies the plugin as being 64-bit, and the browser seemingly ignores the 32-bit file names (which are **libnpgoogletalk32.so** and **libnpgtpo3dautoplugin32.so** in my **/opt/google/talkplugin** folder).

With i386 plugins, and invoked from Terminal on 64-bit Karmic, the following messages are produced by Firefox (and Swiftfox), which then **aborts**:
```
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
Inconsistency detected by ld.so: dl-open.c: 643: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!
```


With only **amd64** package symlinks, the following messages are spouted by Firefox/Swiftfox, which then runs okay but doesn't load the plugins:
```
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
```


Is it possible that Firefox is lazily accessing an internal cache which retains the 64-bit plugin code, rather than loading anew from the 32-bit plugin file?

---

### Post by Tristan Schmelcher on 2010-08-27
I think it is loading the 32-bit plugins after all, but that _dl_debug_initialize message is caused by the loader determining that one of the required shared libraries is missing. Try running "ldd" on the 32-bit plugins to see which libraries are "not found". Then use getlibs to download their 32-bit versions. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by gradinaruvasile on 2010-08-27
Guys, the plugin packages has a lib folder with 2 additional .so in it:

libCg.so - 7.5 MB
libCgGL.so - 325 KB

I assume they too are used. Also there is a 4.6 MB file  - GoogleTalkPlugin that is executable in the root folder of the plugin. So it might be something more complex than flash or the likes.

For me it worked on Chrome and Firefox with no problems OOTB. Even Opera detected the plugins but for some reason cant use them.
I use Debian Squeeze 32-bit.

---

### Post by Tristan Schmelcher on 2010-08-27
Oh right, you'd need the 32-bit versions of libCgGL and libCg too.

GoogleTalkPlugin is already 32-bit tho, even in the 64-bit package.

---

### Post by fragos on 2010-08-27
I run 32 bit Ubuntu and my Google Talk plugin doesn't indicate 32 or 64. It's as follows:

/opt/google/talkplugin/libnpgoogletalk.so
/usr/lib/firefox/plugins/libnpgoogletalk.so
/usr/lib/iceape/plugins/libnpgoogletalk.so
/usr/lib/iceweasel/plugins/libnpgoogletalk.so
/usr/lib/midbrowser/plugins/libnpgoogletalk.so
/usr/lib/mozilla/plugins/libnpgoogletalk.so
/usr/lib/xulrunner/plugins/libnpgoogletalk.so
/usr/lib/xulrunner-addons/plugins/libnpgoogletalk.so

---

### Post by gnothi on 2010-08-27
> **Tristan Schmelcher said:**
> I think it is loading the 32-bit plugins after all, but that _dl_debug_initialize message is caused by the loader determining that one of the required shared libraries is missing. Try running "ldd" on the 32-bit plugins to see which libraries are "not found". Then use getlibs to download their 32-bit versions. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

That all amounts to crossing the *"more trouble than it's worth"* line for me.

Whenever I need the GoogleTalkPlugin feature, I'll fire up Epiphany or Chromium.

Thanks for your insightful comments here.

---

### Post by MasterNetra on 2010-08-27
> **gnothi said:**
> With symlinks to the plugin files for **i386** (extracted from Google's [_DEB package_](http://dl.google.com/linux/direct/google-talkplugin_current_i386.deb)), Firefox won't start up at all. It identifies the plugin as being 64-bit, and the browser seemingly ignores the 32-bit file names (which are **libnpgoogletalk32.so** and **libnpgtpo3dautoplugin32.so** in my **/opt/google/talkplugin** folder).

With i386 plugins, and invoked from Terminal on 64-bit Karmic, the following messages are produced by Firefox (and Swiftfox), which then **aborts**:
```
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
Inconsistency detected by ld.so: dl-open.c: 643: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!
```


With only **amd64** package symlinks, the following messages are spouted by Firefox/Swiftfox, which then runs okay but doesn't load the plugins:
```
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgoogletalk64.so [/opt/google/talkplugin/libnpgoogletalk64.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /opt/google/talkplugin/libnpgtpo3dautoplugin.so [/opt/google/talkplugin/libnpgtpo3dautoplugin.so: wrong ELF class: ELFCLASS64]
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
```


Is it possible that Firefox is lazily accessing an internal cache which retains the 64-bit plugin code, rather than loading anew from the 32-bit plugin file?

You could remove the Tarball version of firefox and re-install firefox from ppa:mozillateam/firefox-stable ? It maybe 32bit but at least it works?

---

### Post by Rocket J Squirrel on 2010-08-27
I got the plugin to work in Chrome. I can dial a number, I can hear them, but they can't hear me. I'm using a bitty Acer Aspire One netbook with built-in microphone, but it doesn't make any difference whether I select Microphone 1 or Microphone 2 with System > Preferences > Sound, they can't hear me. 

I'd get a USB headset to try, but I don't have any confidence that I could make it work.

---

### Post by pwnst*r on 2010-08-27
Works awesome on my Ubuntu desktop install and just as well on my Mint9 usb persistant install.

Awesome work, Google.

---

### Post by Rocket J Squirrel on 2010-08-27
> **Rocket J Squirrel said:**
> I got the plugin to work in Chrome. I can dial a number, I can hear them, but they can't hear me. I'm using a bitty Acer Aspire One netbook with built-in microphone, but it doesn't make any difference whether I select Microphone 1 or Microphone 2 with System > Preferences > Sound, they can't hear me.

Turns out it's not a hardware problem. The microphones work, I can hear my voice echo back to me out of the laptop's speakers, faintly, when I talk into the mic, like the echo you get with a funky connection. But no voice gets to the phone I'm connected to. 

Interestingly, when I use System > Preferences > Sound > Input to switch between Mic 1 and Mic 2, I can hear a "pop" in the phone's earpiece, and when I change the mic gain setting I can hear the mic preamp background hiss go up and down, so it's like everything but the voice itself is getting sent to the phone. 

I think it's a plugin problem. I'm gonna test it in Firefox . . . hang on . . . nope, same result.

---

### Post by fragos on 2010-08-27
You need to make sure the volume for the mike is set high enough. The GUI is a little confusing but running alsamixer may give you a more understandable view. There's more than one setting for mike source so check all the levels in alsamixer. R/L arrow selects the source, U/D arrow sets volume and M toggles mute (note that the 00 display is mute off and MM is muted)

---

### Post by Rocket J Squirrel on 2010-08-28
Hey Fragos -- nice head of hair, there buddy!

The mic volume control sliders seem pretty simple to figure out -- min/max and when you slide it all the way to min, the "mute" box automatically ticks, so I don't think there's a problem with that. 

And as I said, when I slide the gain control to "max" I can hear the mic preamp hiss increase in the connected phone. 

Finally, when I speak directly into the laptop's mic, I can hear an echo of my voice in the laptop's speaker from, presumably, the phone connection, but can't hear the voice in the phone.

---

### Post by fragos on 2010-08-28
Thanks Rocket -- I lucked out in the hair department. I still haven't actually made a voice or video call but did notice Gmail--Settings--Chat--Verify your settings and fiddled with that a bit. In the test my video didn't work although running the test turned off the LED on my Logitech webcam. I can hear my mike through the speakers but that works the same as not running the test and last the test sound doesn't play. The only thing that seems to work is that Gmail sees the plugin. Here my about:version output:

Google Chrome	6.0.472.51 (Official Build 57639) beta
WebKit	534.3
V8	2.2.24.18
User Agent	Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.3 (KHTML, like Gecko) Chrome/6.0.472.51 Safari/534.3
Command Line	 /opt/google/chrome/google-chrome

About: plugins shows:

Google Talk Plugin (2 files)
Version: 1.4.1.0

We're both in the same boat and I'm not sure what to try next although my use of Chrome beta instead of stable might be my issue.

---

### Post by LuxeSaber on 2010-08-30
> **gnothi said:**
> I experienced a similar audio problem when I plugged my headset into the connectors located at the **front** of my desktop PC. I resolved the problem by setting my Ubuntu **sound preferences** to use Microphone 2 (instead of Microphone 1, which is the **rear** connector on my PC).

Also make sure that your mic isn't muted in sound preferences, and that its volume setting isn't too low (or too high, which amplifies line noise).

I haven't yet got the plugin to work in Firefox 3.6.8 on 64-bit Karmic (with 32-bit libs), but it's okay with [_Chromium_](https://launchpad.net/~chromium-daily/+archive/stable).

_Thank you_ for the *excellent* tip!~ :P
That was indeed my problem; went to _Sound Preferences_ and changed to the correct microphone. Everything works ***_perfectly_*** for me now. Using 32-bit Ubuntu 10.04
_Thanks_ again **gnothi**

---

