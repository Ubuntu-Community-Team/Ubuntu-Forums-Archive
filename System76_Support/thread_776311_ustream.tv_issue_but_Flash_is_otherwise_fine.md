---
title: "ustream.tv issue but Flash is otherwise fine"
date: 2008-04-30
forum: System76 Support
---

### Post by ctsdownloads on 2008-04-30
Need to understand something as clearly, this is not a Heron issue. Brand new  Gazelle Value. Tested on both wireless and wired connections.

ustream.tv will not show up. Basically, the page loads fine, however the connection to the broadcasts is giving me 

> "Disconnected, please wait while I reconnect".

from within the video streams themselves. Youtube is fine however, and I am using libflashplayer.so from the Ubuntu Heron repos. Works fine on Heron 32bit, fails on 64bit Heron - any thoughts?

PulseAudio is picking up the audio streams from the PulseVolume manager, and sound works fine on all other Flash video/audio. This appears to be an issue with ustream and 64bit Ubuntu Heron, just need to verify this with other 64bit users before passing this on to their devs.

Just need 64bit users to go to [http://ustream.tv](http://ustream.tv) and let me know if it is working for you.

---

### Post by ctsdownloads on 2008-04-30
Seriously, this is annoying, can anyone with Flash installed using Ubuntu 64bit please browse to the page please and let me know if the live streams are working for them?

[http://ustream.tv](http://ustream.tv)

---

### Post by crichell on 2008-04-30
[http://ustream.tv](http://ustream.tv) is working for me under Hardy 64 bit.  Do you have libflashsupport installed? If so try removing that package.

---

### Post by ctsdownloads on 2008-04-30
> **crichell said:**
> [http://ustream.tv](http://ustream.tv) is working for me under Hardy 64 bit.  Do you have libflashsupport installed? If so try removing that package.

One of the first things I checked for. It is soooo wild, as I tested this on another notebook with the same stuff installed (Ubuntu Heron 32bit). The only difference is Compiz Fusion is running on this notebook. It's all on the same network and if you are able to see it, then it must be something I have installed. Here is the screen capture in the attachment below.

Really thrown on this one, could it be Compiz Fusion? It is the only variable outside of the ufw in use. And even then, I triple checked that the appropriate ports were open and even forced an uninstall for further testing. So it is not the network setting at fault here. This is tested with the same tested streams running live on another notebook and I also stopped viewing with the working notebook, restarted the browser to make sure it was not a network issue from that angle as well.

Also, the provided chat rooms give me the same error and even the prerecorded shows fail to play. Again, Flash in Firefox on Youtube, etc all works really well. Justin.tv works fine, too and I have used [http://www.ustream.tv/streamtest/](http://www.ustream.tv/streamtest/) to no avail. The only thing failing is access to port 6667, which has been white listed seven ways from Sunday on ufw and my router. Seriously this is not an issue with any other Ubuntu box in my home...

I even removed and then reinstalled Flash the old fashion way - no go. Thoughts? Every other similair service works fine on this notebook and even weirder, ustream works fine on other Heron powered appliances.

---

### Post by ctsdownloads on 2008-04-30
slightly off topic, I figured out the fix to the bad 100% CPU lockup with the latest "update" for Flash. It's your nspluginwrapper package, which allows flash to work well for 64bit Ubuntu. Uninstall the newer package:

sudo apt-get remove nspluginwrapper

Reinstall the attached package which is the previous version that actually works. Does nothing for ustream.tv not working on this notebook, but at least YouTube is not eating my CPU alive anymore.

You will be prompted to install Flash again on a Flash enabled sites, btw.

---

### Post by ctsdownloads on 2008-05-01
> **crichell said:**
> [http://ustream.tv](http://ustream.tv) is working for me under Hardy 64 bit.  Do you have libflashsupport installed? If so try removing that package.

Really stuck on this, triple checked, that is definitely not installed on this Heron notebook. I have tested it on two other Heron 32bit boxes, wired and wireless, it is not connecting. See [linked image]("http://ubuntuforums.org/showpost.php?p=4849171&postcount=4") in post above.

---

### Post by ctsdownloads on 2008-06-06
And I am back, still confused as to why I am the only Ubuntu user who is dealing with this. Fresh install, youtube, Justin.tv, etc all work just fine. Again,* brand new 64 bit Ubuntu install*, all the latest updates and system76 driver installed and run/ran/used - really have a hard time understanding why I cannot connect here? Clearly, this is not an Ubuntu issue specifically.

My other 32bit 8.04 machines connect to ustream.tv fine, btw, so it is not as ufw or router issue.

Running with my new Gazelle Value, purchased roughly a month ago. :confused:

Flash 9,0,124,0 installed
Ubuntu Heron 64bit with system 76 installed and activated.
Firefox 3 Beta 5

---

### Post by OldTimeTech on 2008-06-25
Your not the only 64 bit on a laptop that is not working on Ustream, I have the same problem and my flash works every where else...I would like to know if it's Ustream itself or something in Hardy?

---

### Post by thomasaaron on 2008-06-25
I can replicate this problem in the shop. I'm only able to get sporadic successful playback by increasing the buffering in the ustream player.

It's probably a bug in Flash.

---

### Post by OldTimeTech on 2008-06-25
I tried to increase the buffering, but it doesn't seem to hold, each time I go back to it, the buffering has decreased down to 0 again.

At some point ctsdownloads said he got and update notice from System 76...I think he meant the company, and it fixed his problem...wish I knew what that upgrade was about.

---

### Post by thomasaaron on 2008-06-26
I don't think we put out an upgrade to fix ustream. Yes, ustream resets the buffer. But that's about the only workaround we have for this one.

---

### Post by OldTimeTech on 2008-08-28
Thanks Thomasaaron, I didn't realize you had answered this.

Will just not enjoy Ustream ;)

---

### Post by madhi19 on 2009-05-20
Bump
Did anybody found a solution for that problem?

---

### Post by thomasaaron on 2009-05-21
Not that I'm aware of. However, have you tried it in Jaunty 64-bit?

---

### Post by moyam01 on 2009-05-28
Tested with Jaunty 64 bit, still a no go

---

### Post by cprofitt on 2009-09-28
Wondering if anyone found a solution -- I tested and Windows / OS X has no issues.

---

### Post by ctsdownloads on 2009-09-29
> **cprofitt said:**
> Wondering if anyone found a solution -- I tested and Windows / OS X has no issues.

Yes and no. No as we are not going to see 64bit Ubuntu playing nice with Ustream until [Adobe's alpha for 64bit Flash]("http://labs.adobe.com/downloads/flashplayer10.html") allows us to enable webcams/mics under Flash. 

But the alpha does work great for YouTube though. That and you need to remove all instances of Flash first, though. This includes nspluginwrapper.

------------

Because I broadcast to Ustream with my webcam, I took my System76 notebook and loaded it up with 32bit Ubuntu. Works like a treat and the dual-core action still runs as if I had two CPUs.

Works great, could not be happier. Sometimes the best way to overcome something is just to walk around it. ;)

---

### Post by samalex on 2009-09-29
I ran into this with uStream.tv, stickam.com, and other sites that use the webcam where Flash just seemed to hose-up.  One of my goals when I ordered my PanP5 was to stream using these sites, but the 64-bit alpha version of Flash doesn't support webcams (which I still can't get 64-bit Flash to work anyway) and neither does the wrapper for the 32-bit version.  For me getting this working isn't worth downgrading to the 32-bit version of Ubuntu since everything else works, but it is quite frustrating.

If I could get the webcam to be picked-up through Virtualbox I might try the 32-bit version of Ubuntu or even Windows there, but thus far I can't get VirtualBox to see the webcam at all.

I do hope they come-out with a stable version of Flash for 64-bit Linux, but until then I'll stick with the Flash wrapper which has issues but at least works... most of the time anyway.

Take care --

Sam

---

### Post by ctsdownloads on 2009-09-29
> **samalex said:**
> I ran into this with uStream.tv, stickam.com, and other sites that use the webcam where Flash just seemed to hose-up.  One of my goals when I ordered my PanP5 was to stream using these sites, but the 64-bit alpha version of Flash doesn't support webcams (which I still can't get 64-bit Flash to work anyway) and neither does the wrapper for the 32-bit version.  For me getting this working isn't worth downgrading to the 32-bit version of Ubuntu since everything else works, but it is quite frustrating.

If I could get the webcam to be picked-up through Virtualbox I might try the 32-bit version of Ubuntu or even Windows there, but thus far I can't get VirtualBox to see the webcam at all.

I do hope they come-out with a stable version of Flash for 64-bit Linux, but until then I'll stick with the Flash wrapper which has issues but at least works... most of the time anyway.

Take care --

Sam

Honestly, it is super doable just dual-partitioning both 64 & 32 bit Ubuntu versions. I mean, if going with 64 bit is that critical for you. Honestly, unless you are doing intensive video editing, you are not likely to notice any difference. Again, 32 bit runs great and works REALLY well with Ustream. But if you need 64 bit for something unusual that does better with 64 bit vs 32, another partition is going to yield vastly better results over VirtualBox based on my experiences. :)

Just my two cents.

---

### Post by samalex on 2009-09-30
> **ctsdownloads said:**
> Honestly, it is super doable just dual-partitioning both 64 & 32 bit Ubuntu versions. I mean, if going with 64 bit is that critical for you. Honestly, unless you are doing intensive video editing, you are not likely to notice any difference. Again, 32 bit runs great and works REALLY well with Ustream. But if you need 64 bit for something unusual that does better with 64 bit vs 32, another partition is going to yield vastly better results over VirtualBox based on my experiences. :)

Just my two cents.

It's not worth the time for me to setup a dual-boot system just for this.  Streaming video through uStream/Stickam is more of a geewiz thing so I'm fine waiting for it to work with what I have.

I may post another tread though asking about the pro's and con's of running 32-bit or 64-bit Ubuntu on the PanP5 because this isn't the first time I've ran into this problem.  I don't want to hijack the thread though, so I won't bother with this here.

Take care --

Sam

---

### Post by ctsdownloads on 2009-09-30
> **samalex said:**
> It's not worth the time for me to setup a dual-boot system just for this.  Streaming video through uStream/Stickam is more of a geewiz thing so I'm fine waiting for it to work with what I have.

I may post another tread though asking about the pro's and con's of running 32-bit or 64-bit Ubuntu on the PanP5 because this isn't the first time I've ran into this problem.  I don't want to hijack the thread though, so I won't bother with this here.

Take care --

Sam

I can understand that. For most people, it is more for fun than function, depending on what is being done with is. Unless you are running a "show", it is not that critical.

If this is the case, the 64bit alpha does work really well if a webcam is not a big deal for ya. 

As for the differences between 32 & 64 bit, outside of the usual benchmarks, I found that certain things are a bit faster. Installing or compiling software, video/audio rendering, stuff like that. Short of this, based on my experiences with 64bit Linux, that's about it but I am sure Tom can fill you in with other advantages.

:)

---

### Post by GrimStalker on 2009-12-12
I have ubuntu 9.10 64bit

I found the solution 

go to your addons in firefox and install TV-FOX 1.4.0


then my ustream just started working.

hope this help!

---

### Post by samalex on 2009-12-14
> **GrimStalker said:**
> I have ubuntu 9.10 64bit

I found the solution 

go to your addons in firefox and install TV-FOX 1.4.0


then my ustream just started working.

hope this help!


It's been a while since I posted in this thread, and since then I've upgraded to Firefox 3.5 and ustream works to play videos about 90% of the time, but I've never been able to get streaming video to work.  Does this TV-FOX add-on fix the problem with the webcam and flash???  If so then I'll definitely check it out.  Thanks!

Edit: Also wanted to note that I'm still running 64-bit Ubuntu 9.10 shipped with my system with 32-bit Flash going through the wrapper.  

Sam

---

### Post by smkoberg on 2009-12-27
I've also been having trouble with this and other flash based webcam web apps.

I can watch live streams that are broadcast via ustream. All Youtube videos work fine. So far, every web based media player (video/audio) work fine.  

My issue is when trying to a) broadcast on ustream, b) upload video to YouTube/Facebook via webcam.

My camera works under guvcview so I know my system recognises the camera. The camera also works through skype.

--edit--
Also found this webcam test online
[flash webcam test]("http://oldes.multimedia.cz/swf/mx-webcam.html")
Not sure how this may help with some of the issues posted above, but my camera works in this environment.

---

### Post by samalex on 2009-12-29
> **smkoberg said:**
> I've also been having trouble with this and other flash based webcam web apps.

I can watch live streams that are broadcast via ustream. All Youtube videos work fine. So far, every web based media player (video/audio) work fine.  

My issue is when trying to a) broadcast on ustream, b) upload video to YouTube/Facebook via webcam.

My camera works under guvcview so I know my system recognises the camera. The camera also works through skype.

--edit--
Also found this webcam test online
[flash webcam test]("http://oldes.multimedia.cz/swf/mx-webcam.html")
Not sure how this may help with some of the issues posted above, but my camera works in this environment.

I never did try the Fox-TV plugin someone suggested, but from what I've read the webcam features of Flash do not work when using the wrapper with 32-bit Flash on 64-bit Linux.  I can view ustream and stickam videos, but I can't broadcast.  This isn't any fault of the webcam, but rather Flash just doesn't support it using the wrapper or in the Alpha 64-bit Flash for Linux.  I think the only way to get this working is to run 32-bit Linux with the native 32-bit Flash plugin.  If anyone has been able to broadcast video through Flash-enabled sites like ustream or stickam on 64-bit Linux, I'd love to know how :)

Thanks,

Sam

---

### Post by nowhere@cox.net on 2010-01-04
It's something wrong with Ustream. Check out this site:
[http://escale.net/mundo/]("http://escale.net/mundo/")

Streaming using Flash works fine there and I'm using the 32bit wrapper. I did have to toggle to Metacity to get the "Flash settings" box to allow clicks (all other clicky stuff works fine in Flash btw...).

I hate Flash...

---

### Post by nowhere@cox.net on 2010-01-05
I was able to get Ustream.tv working although not 100% reliable. 
[LIST]
[*]I installed the latest 64bit alpha flash plugin from adobe: [http://labs.adobe.com/downloads/flashplayer10_64bit.html]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")
[*]Went to Macromedia site to force always allow use of camera and mic to ustream.tv [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html")
[*]Enabled audio input from webcam mic (System/Preferences/Sound/Input
[*]Launched ustream.tv and it works.
[/LIST]

One problem seems to be that audio is very low. I go to input audio preferences on System/Preferences/Sound/Input and we I reload, video isn't working. Unplug and replug the camera and video is working but audio is low again.

---

### Post by samalex on 2010-01-05
> **nowhere@cox.net said:**
> I was able to get Ustream.tv working although not 100% reliable. 
[LIST]
[*]I installed the latest 64bit alpha flash plugin from adobe: [http://labs.adobe.com/downloads/flashplayer10_64bit.html]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")
[*]Went to Macromedia site to force always allow use of camera and mic to ustream.tv [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html")
[*]Enabled audio input from webcam mic (System/Preferences/Sound/Input
[*]Launched ustream.tv and it works.
[/LIST]

One problem seems to be that audio is very low. I go to input audio preferences on System/Preferences/Sound/Input and we I reload, video isn't working. Unplug and replug the camera and video is working but audio is low again.

Thanks for the update... I've never been able to get the Alpha 64-bit Flash to work on my system, I just get Segmentation Fault in Firefox when it hits any Flash enabled pages.  But with it still being buggy I'll probably stick with the wrapper until it's officially released which should be this year sometime.

Take care,

Sam

---

### Post by leviduncan1 on 2010-01-15
After reading all the posts in this section I decided to try another browser. I installed Galeon Web browser from the Ubuntu Software Center. Logged into Ustream and was able to broadcast. The only other thing I did prior to the install was go to the macromedia flash manager and enabled ustream... Hope this helps!:D

---

### Post by samalex on 2010-01-15
> **leviduncan1 said:**
> After reading all the posts in this section I decided to try another browser. I installed Galeon Web browser from the Ubuntu Software Center. Logged into Ustream and was able to broadcast. The only other thing I did prior to the install was go to the macromedia flash manager and enabled ustream... Hope this helps!:D

Actually indirectly your comment got me going...  I did download Galeon, but it still didn't work. I didn't think about setting UStream to Always Allow in the Flash Settings Manager.

From the Flash Settings Manager I cleared out all URL's in the camera tab, opened UStream and started broadcasting, which didn't work.  Going back into Flash Settings Manager it then had 4 URL's listed in the webcam tab, so I set all to Always Allow.  This did it... now when I try to Broadcast through UStream it works but is buggy.

If I adjust the Framerate or any settings in the Advanced section, the video freezes and I have to close and reopen Firefox to get video back.  Likewise if I stop the stream and go back in, it won't work... I have to once more close and reopen Firefox.  

I tested with Stickam and it worked as well.

Below are the URL's I have set to Always Allow in the Adobe Flash Player Settings Manager under the Webcam tab:
player.stickam.com
[www.ustream.tv](www.ustream.tv)
redir.adap.tv
cdn1.ustream.tv
flash.quantserve.com
core.videoegg.com

So I think the problem was UStream nor Stickam were asking for permissions, and even though I had Always Ask set, the window to ask never came-up.  When I tested with the Webcam Flash test sites the Ask window always appeared, but not for Ustream or Stickam.

Anyway, this is neat!  Not that I'll be broadcasting that much, but I'm glad it's working.

And in-case I haven't mentioned it already, this is using the latest Alpha 64-bit Flash Plugin with Firefox 3.5.7 (Shiretoko) on Ubuntu Desktop 9.04... and on my PanP5 :)  

One more thing, I haven't tested audio, so I don't know how well that works.  I have headphones plugged into my laptop now, but I'll test it later and post an update.

Take care, and happy broadcasting!

Sam

---

### Post by bcschmerker on 2012-06-24
I found a SERIOUS issue with UStream® Television, as of June 2012:  Running Adobe® Flash 10.3.183.20 (manually installed using Flash-Aid) and Kernel 3.0.0.*, I found that my system always misbehaves on the UStream® home page: 
```
http://www.ustream.tv/
```
The entire X Video System is affected, as it cycles the video to monitor every 10 seconds and the cursor is usable only every other "on" time; eventually the system locks up with a blank screen.  (In contrast, my Asus® CM1630-06 as upgraded, running Microsoft® Windows® 7.0.8001 (MultiProcessor Kernel 6.1.7601), operates normally on the same Web site.)  Cannot trace what in the UStream® code is causing LinUX boxes to malfunction as I just described.  To date, I have not had similar misbrehavior at any other Website.

---

### Post by isantop on 2012-06-25
> **bcschmerker said:**
> I found a SERIOUS issue with UStream® Television, as of June 2012:  Running Adobe® Flash 10.3.183.20 (manually installed using Flash-Aid) and Kernel 3.0.0.*, I found that my system always misbehaves on the UStream® home page: 
```
http://www.ustream.tv/
```
The entire X Video System is affected, as it cycles the video to monitor every 10 seconds and the cursor is usable only every other "on" time; eventually the system locks up with a blank screen.  (In contrast, my Asus® CM1630-06 as upgraded, running Microsoft® Windows® 7.0.8001 (MultiProcessor Kernel 6.1.7601), operates normally on the same Web site.)  Cannot trace what in the UStream® code is causing LinUX boxes to malfunction as I just described.  To date, I have not had similar misbrehavior at any other Website.

It looks like you may be on an out-of-date version of Ubuntu. I would try upgrading to 12.04 to ensure that you have the latest software running. That could be causing your problems.

---

### Post by bcschmerker on 2012-09-15
> **bcschmerker said:**
> I found a SERIOUS issue with UStream® Television, as of June 2012:  Running Adobe® Flash 10.3.183.20 (manually installed using Flash-Aid) and Kernel 3.0.0.*, I found that my system always misbehaves on the UStream® home page....
**Update:**  The critical problem I encountered in 10.04.4-LTS is nonexistent in 12.04.1-LTS.  Apparently X has been improved along with the balance of Ubuntu®.

---

