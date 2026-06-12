---
title: "Hulu player for Linux"
date: 2009-10-09
forum: System76 Support
---

### Post by Lee_Machine on 2009-10-09
The video streaming web site hulu.com has released their desktop player for Linux, with officially supporting Ubuntu, and Fedora. 

I testing it out with Ubuntu 9.10, and Linux Mint 7. The program worked just fine on both. 

In both cases I had to manually tell it where to find the flash player plug-in. That just takes adding it in its config file under ~/.huludesktop

I was surprised to find that the program supports LIRC, and the documentation for adding it to your .lircrc config file is well documented.  

Anywho just though I'd share :P

[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

---

### Post by Lee_Machine on 2009-10-09
Oh, and also in the same documentation for using LIRC it pretty much says when using 64bit Linux you will want to use the native 64bit flash player....Adobe needs to get a final version of that out :P

---

### Post by Temposs on 2009-10-09
I've downloaded it, but I can't make it find my flash. I put in the location in the appropriate place in the config file, but it doesn't seem to care...

```

[flash]
flash_location = /usr/lib/flashplugin-installer/libflashplayer.so

```

---

### Post by compholio on 2009-10-09
> **Temposs said:**
> I've downloaded it, but I can't make it find my flash. I put in the location in the appropriate place in the config file, but it doesn't seem to care...

```

[flash]
flash_location = /usr/lib/flashplugin-installer/libflashplayer.so

```

I'm going to guess that you're running 64-bit Ubuntu and a 32-bit flashplayer, try changing the flash_location to:
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

---

### Post by Temposs on 2009-10-09
That worked perfectly. Thanks for the troubleshooting :-)

---

### Post by compholio on 2009-10-09
> **Temposs said:**
> That worked perfectly. Thanks for the troubleshooting :-)

No problem, glad it worked.

---

### Post by hambone79 on 2009-10-09
I downloaded and installed it without any issues, but I personally think it runs kind of sluggish. Compared to Boxee, it is not as smooth moving back and forth between menus and the videos get choppy at times. Other than that, its a pretty nice client.

---

### Post by eddietours on 2009-10-09
thanks guys l was going nuts trying to get the Hulu going :)

---

### Post by z0mbie on 2009-10-09
Really cool, trying it out.

---

### Post by samalex on 2009-10-10
Hi all,

I saw that Hulu Desktop was out for Linux earlier in the week and installed it.  It's nice, but it's jerky in lots of places.  I also wish Adobe would hurry up with the 64-bit version of Flash for Linux because I've had no luck with the alpha version.  I may try it with Hulu Desktop though just incase it does work better... though I've still not been able to get the 64-bit version to work with Firefox.

But all and all it's nice...  and much easier then trying to navigate their website.

Sam

---

### Post by Jazzy_Jeff on 2009-10-11
I installed Hulu Desktop yesterday and it has run flawlessly. No jerks or anything. I am glad to see them supporting Linux.

---

### Post by samalex on 2009-10-11
> **Jazzy_Jeff said:**
> I installed Hulu Desktop yesterday and it has run flawlessly. No jerks or anything. I am glad to see them supporting Linux.

Are you using the 64-bit alpha version of Flash or the 32-bit version with the wrapper?  I may try to download the 64-bit version just for Hulu Desktop in hopes that it fixes the jerky playback.  

Update: I downloaded the Alpha 64-bit version of Flash from Adobe's website and tried to point Hulu Desktop at it, but as with Firefox I'm getting "Segmentation fault" whenever it tries to load.  Does anyone have any suggestions on how to get past this?  At first I thought it was Firefox, but now I'm pretty sure the problem is with 64-bit Flash.

Thanks --

Sam

---

### Post by gamerchick02 on 2009-10-13
I'm running this as well.  I found that it's jerky, but I turned the "Quality" down to "Medium" and it seems to be a heck of a lot cleaner.

I'm loving it right now... I've got it on a second monitor and I can do other things on my laptop and have a video on the other monitor!  It's great.  Increases my productivity.

Amy

---

### Post by e.m.fields on 2009-10-15
Samalex:

> **samalex said:**
> Are you using the 64-bit alpha version of Flash or the 32-bit version with the wrapper?  I may try to download the 64-bit version just for Hulu Desktop in hopes that it fixes the jerky playback.  

Update: I downloaded the Alpha 64-bit version of Flash from Adobe's website and tried to point Hulu Desktop at it, but as with Firefox I'm getting "Segmentation fault" whenever it tries to load.  Does anyone have any suggestions on how to get past this?  At first I thought it was Firefox, but now I'm pretty sure the problem is with 64-bit Flash.


Same here.  I installed Hulu desktop player on Jaunty x64 using the 32-bit Flash player with nswrapper.  It worked, but choppy as usual.  I installed the 64-bit player thinking it might be better, but it just crashes immediately.  So - 
> now I'm pretty sure the problem is with 64-bit Flash.

+1 for this conclusion.

Anyone have a lead on a solution? 
THANKS

---

### Post by theZoid on 2009-10-16
> **Jazzy_Jeff said:**
> I installed Hulu Desktop yesterday and it has run flawlessly. No jerks or anything. I am glad to see them supporting Linux.

Just notice Version 9.04 just came out.....very nice indeed.

---

### Post by Cresho on 2009-10-16
> **samalex said:**
> Are you using the 64-bit alpha version of Flash or the 32-bit version with the wrapper?  I may try to download the 64-bit version just for Hulu Desktop in hopes that it fixes the jerky playback.  

Update: I downloaded the Alpha 64-bit version of Flash from Adobe's website and tried to point Hulu Desktop at it, but as with Firefox I'm getting "Segmentation fault" whenever it tries to load.  Does anyone have any suggestions on how to get past this?  At first I thought it was Firefox, but now I'm pretty sure the problem is with 64-bit Flash.

Thanks --

Sam

im using the 32bit flash with nds what ever wrapper and it runs better than the native 64bit flash.  no jerking but in youtube, i need to hit refresh on the button when the video does not play but i hear sound.  then it works.  seems that youtube is the only one showing this slight problem.

---

### Post by theZoid on 2009-10-16
> **Cresho said:**
> im using the 32bit flash with nds what ever wrapper and it runs better than the native 64bit flash.  no jerking but in youtube, i need to hit refresh on the button when the video does not play but i hear sound.  then it works.  seems that youtube is the only one showing this slight problem.

I'm also using the 32 bit flash with wrapper...haven't tried the 64 bit with Karmic, but I can say I don't get any jerkiness except for a flash when changing the window size.  HW in sig also.

---

### Post by e.m.fields on 2009-10-16
> **Cresho said:**
> im using the 32bit flash with nds what ever wrapper and it runs better than the native 64bit flash.  no jerking but in youtube, i need to hit refresh on the button when the video does not play but i hear sound.  then it works.  seems that youtube is the only one showing this slight problem.


So it's sounding like there's no real reason to use the 64-bit flash, then.  Am I correct?  **Can anyone confirm any noticeable positive difference in performance upgrading to the the 64-bit flash?** (Or can anyone confirm from personal experience that there's definitely none?)

---

### Post by Lee_Machine on 2009-10-16
Hulu player aside, there is a huge difference in performance when running flash videos natively in 64bit. These numbers are not exact, but when using 32bit flash, the wrapper takes about 20% of my CPU cycles, sometime a lot more. Try playing a flash based game, and see what happens to your CPU. 

The 64bit eliminates that.

---

### Post by e.m.fields on 2009-10-16
Thanks for the response, Lee.
That's good news, (sort of...) because it was slow as balls on my own box using 32-bit flash trying to watch any decent-quality fullscreen video.  So, I'm hoping that there's a solution to this crashing bug; if the 64-bit driver is actually a little better, maybe I can actually get some use out of Hulu now.  =P

Thanks

---

### Post by sloggerkhan on 2009-10-16
I tried it and it runs REALLY REALLY damn slow.

---

### Post by Thelasko on 2009-10-16
> **sloggerkhan said:**
> I tried it and it runs REALLY REALLY damn slow.

I thought so too, but when I tried using it today it told me a new version was available.  When I installed the new version it was much faster.

---

### Post by thomasaaron on 2009-10-16
Someone said something earlier to lowering the quality... maybe to medium. Did you try that?

---

### Post by samalex on 2009-10-16
> **Thelasko said:**
> I thought so too, but when I tried using it today it told me a new version was available.  When I installed the new version it was much faster.

Last night I noticed the update was available, and I to installed it.  With the upgraded version the flicker I had on the menus was gone and playback is MUCH smoother on my panP5.  Full screen video still stutters occasionally, but 95% of what I watched was very smooth.  Also this is with the 32-bit version of Flash using the wrapper, so I can only imagine how fast it'll run when Flash has the 64-bit version working.

Sam

---

### Post by theZoid on 2009-10-17
> **thomasaaron said:**
> Someone said something earlier to lowering the quality... maybe to medium. Did you try that?

I run mine on high, but hardware will make up for other problems sometimes.

---

### Post by penguininja on 2009-10-31
> **samalex said:**
> Update: I downloaded the Alpha 64-bit version of Flash from Adobe's website and tried to point Hulu Desktop at it, but as with Firefox I'm getting "Segmentation fault" whenever it tries to load.  Does anyone have any suggestions on how to get past this?  At first I thought it was Firefox, but now I'm pretty sure the problem is with 64-bit Flash.


I am experiencing the same behavior, segfaults when I try to play anything in Hulu both with the desktop player and in Firefox.  I'm using the alpha 64 bit flash with 64 bit Karmic 9.10 on a Macbook 2,1.  Other sites, such as Youtube, seem to work fine with the 64 bit flashplayer.  I would just go back to the 32 bit version, but I was experiencing the "can't interact with flash" issue described here: [http://ubuntuforums.org/showthread.php?t=1283533](http://ubuntuforums.org/showthread.php?t=1283533)

Any thoughts on troubleshooting the segfault issue?  I have uninstalled flashplugin-installer, but is there something else that may be causing a conflict?  Or perhaps this is just an issue with the alpha release I'll have to wait for Adobe to fix.

Thanks!

---

### Post by Thelasko on 2009-11-01
> **penguininja said:**
> Or perhaps this is just an issue with the alpha release I'll have to wait for Adobe to fix.

I am using the Alpha release for 64-bit flash on Hardy and it works fine.  I don't think it's an issue with 64-bit flash.

What version of Hulu player are you using?  A more recent version was released that has many bugs fixed.  The latest version is 0.9.4.

---

### Post by ctsdownloads on 2009-11-01
I run Hulu video on my flat screen TV - meaning no cable TV. It uses a VGA cable that I connect to the PC. Now the real question for me was whether to use a browser, hulu desktop or Boxee? After trying all three, Boxee blows them all out of the water on quality.

Each video screen size can be set mid-play. Also, assuming you logged into hulu and set things to hi-def by default, Boxee will use your Firefox settings to remember this and play some really nice quality video. I used to have DirecTv HD - cannot tell the difference between it and Hulu on the big screen. Only downside with Boxee is the lack of volume control in the software for Flash media. This is fixed with external speakers that have a remote...so I don't have to get up. ;) Yes, you can install Boxee on 9.10 32bit...but if memory serves me, I had to use [Ubuntu Package Search]("http://packages.ubuntu.com/") to track down some older packages from 9.04. Seems that it was asking for each thing, was not a big deal to install. I installed via apt-get, then wrote down the missing items for tracking down.

Works AWESOMELY on even an older 802.11G connection.

Disclaimer: While I am using a System 76 PC to do this, it is NOT running 64bit Ubuntu. If you wish to, I recommend the beta 64bit driver instead of the ndiswrapper headache. [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

---

### Post by samalex on 2009-11-02
> **ctsdownloads said:**
> 
Disclaimer: While I am using a System 76 PC to do this, it is NOT running 64bit Ubuntu. If you wish to, I recommend the beta 64bit driver instead of the ndiswrapper headache. [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

Unfortunately like many I'm getting a Segmentation Fault error with the 64-bit Alpha version of Flash.  Under Firefox 3.5 I can get Youtube to work, but about any other site, including Hulu (through FF or Hulu Desktop) I get the Segmentation Fault error.  For this my only option is to run the ndiswrapper which sucks but it works.

Adobe has said they will release Flash 10.1 next year for all operating systems at the same time, so I assume it won't be until then that Linux gets a good, stable version of Flash 10.

Sam


Sam

---

### Post by ctsdownloads on 2009-11-02
> **samalex said:**
> Unfortunately like many I'm getting a Segmentation Fault error with the 64-bit Alpha version of Flash.  Under Firefox 3.5 I can get Youtube to work, but about any other site, including Hulu (through FF or Hulu Desktop) I get the Segmentation Fault error.  For this my only option is to run the ndiswrapper which sucks but it works.

Adobe has said they will release Flash 10.1 next year for all operating systems at the same time, so **I assume it won't be until then that Linux gets a good, stable version of Flash 10.**



Flash 32bit is *quite* stable. I run it all day long without fail, on multiple PCs ranging 8.04 to 9.10 Ubuntu, Intel, NVIDIA and ATI video cards. It is 64bit Flash that is in dire need of CPR. ;)

I am running Ustream right now, while also using [WebcamStudio]("http://www.ws4gl.org/") (Java) and Banshee streaming Live.Twit.tv - my CPU usage is 55%...could not be happier.

---

### Post by samalex on 2009-11-02
> **ctsdownloads said:**
> Flash 32bit is *quite* stable. I run it all day long without fail, on multiple PCs ranging 8.04 to 9.10 Ubuntu, Intel, NVIDIA and ATI video cards. It is 64bit Flash that is in dire need of CPR. ;)

I am running Ustream right now, while also using [WebcamStudio]("http://www.ws4gl.org/") (Java) and Banshee streaming Live.Twit.tv - my CPU usage is 55%...could not be happier.

Are you using 32-bit or 64-bit Ubuntu?  I've heard that the 32-bit Flash does run well under 32-bit Linux, so I'm debating on whether or not I want to load 32-bit Ubuntu 9.10 on my laptop.  It'll just suck since I have 4 gigs of RAM and I think the 32-bit only uses 3 Gigs tops. I may try to setup dual booting between the 32-bit and 64-bit versions though, but again that's a PITA.

Decisions Decisions...

Actually do all the System76 drivers from their repositories work under 32-bit Ubuntu?  Just curious.

Sam

---

### Post by Thelasko on 2009-11-02
> **samalex said:**
> It'll just suck since I have 4 gigs of RAM and I think the 32-bit only uses 3 Gigs tops.

I think it's 4 gigs tops with 32-bit.

---

### Post by ctsdownloads on 2009-11-02
> **samalex said:**
> Are you using 32-bit or 64-bit Ubuntu?  I've heard that the 32-bit Flash does run well under 32-bit Linux, so I'm debating on whether or not I want to load 32-bit Ubuntu 9.10 on my laptop.  It'll just suck since I have 4 gigs of RAM and I think the 32-bit only uses 3 Gigs tops. I may try to setup dual booting between the 32-bit and 64-bit versions though, but again that's a PITA.

Decisions Decisions...

Actually do all the System76 drivers from their repositories work under 32-bit Ubuntu?  Just curious.

Sam

Yes, I use 32bit exclusively due to Flash being an ongoing headache. It was not a good match for me. And yes, 32bit Ubuntu works fine with up to 4 gigs of RAM. :)

That said, the System76 driver **is 64bit only**. For me, my System76 notebook and desktop run fine without it, so it was not a loss for me personally.

---

### Post by Thelasko on 2009-11-03
> **ctsdownloads said:**
> Yes, I use 32bit exclusively due to Flash being an ongoing headache.

I haven't had any problems with 64-bit flash for quite some time.  Seems like results may vary.

---

### Post by ctsdownloads on 2009-11-03
> **Thelasko said:**
> I haven't had any problems with 64-bit flash for quite some time.  Seems like results may vary.

I am all about path of least resistance. If it's working for ya, awesome. I'd agree that the results vary depending on a number of factors. I have had nothing but heartache with it on Intel and AMD systems. Others still, have had it working like a champ. For me, it's been more of a "chimp" than a champ. :P

If you are able to keep nspluginwrapper from crashing, then you may have a winner. I on the other hand, cannot make that claim. ;)

---

### Post by thomasaaron on 2009-11-04
Some folks are getting good results by running this command (32-bit Flash / nsplugginwrapper users only)...

sudo apt-get install libadns1

(Reboot may be necessary.)

---

### Post by samalex on 2009-11-04
> **thomasaaron said:**
> Some folks are getting good results by running this command (32-bit Flash / nsplugginwrapper users only)...

sudo apt-get install libadns1

(Reboot may be necessary.)

Thomas,

Run this on 64-bit Ubuntu running Flash 32-bit via the wrapper?  I'll try this after work, but what does it do?

Sam

---

### Post by thomasaaron on 2009-11-04
Correct.

I believe it is supposed to fix some sound and crashing issues. It worked for one of our techs. But it doesn't seem to work for others. It's worth a try. Easy to uninstall if it doesn't help.

---

### Post by robobot on 2009-11-04
Regarding the segfault issue:

This only happens when using the 64-bit flash plugin on the stock kernel for 9.10. It works fine on custom kernels or in different versions of Ubuntu, or at least it does for me.

---

### Post by samalex on 2009-11-04
> **thomasaaron said:**
> Correct.

I believe it is supposed to fix some sound and crashing issues. It worked for one of our techs. But it doesn't seem to work for others. It's worth a try. Easy to uninstall if it doesn't help.

Hmm, looks like I already have it installed...  

Sam

---

### Post by adamn on 2009-11-12
So, I'm really new to Linux. How do I edit the ~/.huludesktop config file in order to point it where to me flash plugin. I know where my flash plugin is, but I don't know what ~/.huludesktop is, where it is, or what it is. I don't even know where programs are installed to in ubuntu, much less where to find their config files.

Someone want to throw me a bone here?

Thanks

---

### Post by compholio on 2009-11-12
> **adamn said:**
> So, I'm really new to Linux. How do I edit the ~/.huludesktop config file in order to point it where to me flash plugin. I know where my flash plugin is, but I don't know what ~/.huludesktop is, where it is, or what it is. I don't even know where programs are installed to in ubuntu, much less where to find their config files.

Someone want to throw me a bone here?

Thanks

"~/" means "the home folder" (/home/<username>).  Also, any files that start with a period are hidden.  So if you open a text editor (such as "gedit": Accessories | gedit Text Editor) and then try to open the file you will not see it unless you right click on the file list and select "Show Hidden Files."  However, there are a lot of hidden files so it can be difficult to find the file you are looking for.  The easiest way around this is to type the name of the file directly in the "Location" box, you can do this either by typing "~/.huludesktop", "/home/<username>/.huludesktop", or if you are in your home folder already you can enter ".huludesktop".  If you've already run huludesktop once then the file should already exist, so when you hit "enter" it will open it.

---

### Post by ManMythLegend on 2009-11-16
I have been having much trouble with Flash since I installed Karmic. Specifically, HuluDesktop refuses to start due to "Segmentation Fault" Error ONLY after having run Firefox. 

Also, in a possibly related issue, Firefox flash videos are sometimes unclickable, specifically in YouTube; the click animation happens (ie. button goes down, comes up on click release) but the video does not begin to play.

I've uninstalled and reinstalled Flash more times than i can count.

Of course, i run 64 bit Ubuntu

---

### Post by thomasaaron on 2009-11-17
sudo apt-get install libadns1 

...should fix the clickability problem. Not sure if it will fix the others.

---

### Post by vraicovi on 2009-11-18
I haven't tried the Hulu client yet, but I stumbled across your thread looking for others with the 64-bit segmentation fault.  On a lark, I ran Firefox as root and low and behold, no more segmentation fault.  Must be a rights issue, no?

---

### Post by thomasaaron on 2009-11-18
Hmmm... it certainly sounds like it. Have you tried re-installing Firefox from your primary (administrative) account to see if that fixes it.

---

### Post by vraicovi on 2009-11-19
I re-installed Firefox with no success. Still throws a segmentation fault, but works fine using sudo.  I discovered another oddity after my first post, Youtube won't load and embedded videos show up blank.  Not sure if it's related, but I'm going down that rabbit hole now...

---

### Post by chunnel on 2009-11-20
I'm having some minor issues with Flash in Ubuntu 9.10.  When clicking on play on a video in Motor Trend, it won't play.  But if I right click the video and open it in You Tube, I can play it and maximize it.

In Hulu, when running it directly on Hulu.com, I nothing happens when I click on 480 dpi or volume or maximize.  But it will work when running the Hulu player on the computer.  But that has less available options for videos.

Any ideas?

---

### Post by e.m.fields on 2009-11-20
> **vraicovi said:**
> I re-installed Firefox with no success. Still throws a segmentation fault, but works fine using sudo.  I discovered another oddity after my first post, Youtube won't load and embedded videos show up blank.  Not sure if it's related, but I'm going down that rabbit hole now...

So just chmod -R 700 /usr/*/firefox, right?

---

### Post by 3Miro on 2009-11-20
For me hulu player gives a segmentation fault with the adobe 64-bit libflash.so, however, it runs with npwrapper.libflash.so (both pointed to the right place). I own the 64-bit version and it is in my folder.

This was happening on both Ubuntu and Kubuntu 9.10.

It is not a problem for me (32-bit works fine), however, I do think that it may be impossible to get hulu + 64-bit flash at this point.

---

### Post by dca on 2009-11-20
Hulu worked fine for me on 64bit with the flash that's installed in the 'ubuntu-restricted-extras' meta-package in the repo and the hulu 64bit client from their website...  Don't know how the System76 machines are built...

---

### Post by 3Miro on 2009-11-20
> **thomasaaron said:**
> sudo apt-get install libadns1 

...should fix the clickability problem. Not sure if it will fix the others.

```
***@***:~$ sudo apt-get install libadns1
[sudo] password for ***: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libadns1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
***@***:~$ 

```

I cannot pause/fast forward YouTube videos. I tried reinstalling the library, also with and without it, no luck. I am running ubuntu karmic 9.10 on panp4n.

I reinstalled the system76 driver and rebooted the system, it is working fine now. It was probably suspend hibernate thing.

---

### Post by 3Miro on 2009-11-20
Worked for 2 minutes and then it doesn't work anymore.

I can skip to a place and pause, but only for a couple of videos, then it stopped responding.

---

### Post by 3Miro on 2009-11-20
Both the generic kernel and a custom one do not help. Running firefox as root doesn't help. Galeon plays the video, but still cannot interact with it.

Youtube in Totem and Hula player work just fine.

---

### Post by 3Miro on 2009-11-20
Found the answer, but will post later. It was a conflict between 64-bit and 32-bit, one plays youtube and the other one hulu.

---

### Post by jonno on 2009-12-03
> **vraicovi said:**
> I re-installed Firefox with no success. Still throws a segmentation fault, but works fine using sudo.

This is true with Hulu Desktop for me.
Starts fine when .huludesktop points to:
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Won't start when .huludesktop points to:
/home/jonno/.mozilla/plugins/libflashplayer.so
Starts fine when run as root and .huludesktop points to:
/home/jonno/.mozilla/plugins/libflashplayer.so

Permissions are currently:
-rwxr-xr-x 1 root root /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
-rwxr-xr-x 1 jonno jonno /home/jonno/.mozilla/plugins/libflashplayer.so
-rwxr-xr-x 1 root root /usr/bin/huludesktop

Would it help to change permissions?

---

### Post by palenekim on 2009-12-28
> **3Miro wrote,**
Found the answer, but will post later. It was a conflict between 64-bit and 32-bit, one plays youtube and the other one hulu.
 
I found the means to resolve the problem for my computer (intel t5500 1.66 ghz 2gb RAM) with Karmic (64-bit) freshly downloaded (which works fine btw). Though, I do not have a System 76 setup this link helped me very much: [http://ubuntuforums.org/showthread.php?t=1358591&highlight=hulu+problems](http://ubuntuforums.org/showthread.php?t=1358591&highlight=hulu+problems). As long as you follow the installation process exactly, there shouldn't be a problem (assuming you have the proper OS and browser that allows it to work). The reason I posted this here is because when I "googled" the problem, this forum section was the first link that popped up. After investigating the forum I found the proper link.

---

### Post by rewyllys on 2011-05-27
> **Lee_Machine said:**
> The video streaming web site hulu.com has released their desktop player for Linux, with officially supporting Ubuntu, and Fedora. 

I testing it out with Ubuntu 9.10, and Linux Mint 7. The program worked just fine on both. 

In both cases I had to manually tell it where to find the flash player plug-in. That just takes adding it in its config file under ~/.huludesktop

I was surprised to find that the program supports LIRC, and the documentation for adding it to your .lircrc config file is well documented.  

Anywho just though I'd share :P

[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)
Thanks, Lee_Machine.  Your tip still works in 2011.  I'm using 11.04, and it has just solved my problem with Hulu.:p

---

### Post by jay214128 on 2012-04-01
I have been successfully using Hulu desktop no ubuntu 10.04 LTS and 11.10.  Recently there has been some system update that now causes Hulu desktop to crash (segfault) on both 10.04 and 11.10.  Backtrace follows:

(gdb) run
Starting program: /usr/bin/huludesktop 
[Thread debugging using libthread_db enabled]
[New Thread 0x7fffebcbe700 (LWP 2265)]
[New Thread 0x7fffeb4bd700 (LWP 2266)]
[New Thread 0x7fffeacbc700 (LWP 2267)]
[New Thread 0x7fffea4bb700 (LWP 2268)]
[New Thread 0x7fffe9cba700 (LWP 2269)]
[New Thread 0x7fffe94b9700 (LWP 2270)]
[New Thread 0x7fffe8cb8700 (LWP 2271)]
[New Thread 0x7fffe84b7700 (LWP 2272)]
[New Thread 0x7fffe32b9700 (LWP 2273)]

(huludesktop:2259): Gdk-WARNING **: gdk_window_new(): parent is destroyed


(huludesktop:2259): Gdk-CRITICAL **: gdk_drawable_get_display: assertion `GDK_IS_DRAWABLE (drawable)' failed

(huludesktop:2259): Gdk-CRITICAL **: gdk_x11_get_xatom_by_name_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(huludesktop:2259): Gdk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

(huludesktop:2259): Gdk-CRITICAL **: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff50b84c8 in XChangeProperty () from /usr/lib/libX11.so.6
(gdb) bt
#0  0x00007ffff50b84c8 in XChangeProperty () from /usr/lib/libX11.so.6
#1  0x00007ffff7a8d474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#2  0x00007ffff792b499 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#3  0x00007ffff663a5de in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#4  0x00007ffff664de61 in ?? () from /usr/lib/libgobject-2.0.so.0
#5  0x00007ffff664fa76 in g_signal_emit_valist ()
   from /usr/lib/libgobject-2.0.so.0
#6  0x00007ffff6650033 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#7  0x00007ffff7a1a797 in gtk_widget_realize ()
   from /usr/lib/libgtk-x11-2.0.so.0
#8  0x00007ffff7a2b375 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#9  0x00007ffff663a5de in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#10 0x00007ffff664de61 in ?? () from /usr/lib/libgobject-2.0.so.0
#11 0x00007ffff664fa76 in g_signal_emit_valist ()
   from /usr/lib/libgobject-2.0.so.0
#12 0x00007ffff6650033 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#13 0x00007ffff7a1b74b in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x00007fffeeb1329a in ?? ()
   from /usr/lib/adobe-flashplugin/libflashplayer.so
#15 0x00007fffeeb1cddf in ?? ()
   from /usr/lib/adobe-flashplugin/libflashplayer.so
#16 0x000000000040819a in ?? ()
#17 0x0000000000407f2a in ?? ()
#18 0x00007ffff78fd188 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x00007ffff663a5de in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#20 0x00007ffff664e598 in ?? () from /usr/lib/libgobject-2.0.so.0
#21 0x00007ffff664f8b9 in g_signal_emit_valist ()
   from /usr/lib/libgobject-2.0.so.0
#22 0x00007ffff6650033 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#23 0x00007ffff7a140cf in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#24 0x00007ffff78f6965 in gtk_main_do_event ()
   from /usr/lib/libgtk-x11-2.0.so.0
#25 0x00007ffff756a86c in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#26 0x00007ffff726e8c2 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#27 0x00007ffff7272748 in ?? () from /lib/libglib-2.0.so.0
#28 0x00007ffff72728fc in g_main_context_iteration ()
   from /lib/libglib-2.0.so.0
#29 0x00007ffff78f6a71 in gtk_main_iteration ()
   from /usr/lib/libgtk-x11-2.0.so.0
#30 0x00007fffeeb1462b in ?? ()
   from /usr/lib/adobe-flashplugin/libflashplayer.so
#31 0x00007ffff726f09b in ?? () from /lib/libglib-2.0.so.0
#32 0x00007ffff726e8c2 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#33 0x00007ffff7272748 in ?? () from /lib/libglib-2.0.so.0
#34 0x00007ffff7272c55 in g_main_loop_run () from /lib/libglib-2.0.so.0
#35 0x00007ffff78f6bc7 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#36 0x000000000040989e in ?? ()
#37 0x00007ffff6aafc4d in __libc_start_main () from /lib/libc.so.6
#38 0x0000000000406f29 in ?? ()
#39 0x00007fffffffe3a8 in ?? ()
#40 0x000000000000001c in ?? ()
#41 0x0000000000000001 in ?? ()
#42 0x00007fffffffe652 in ?? ()
#43 0x0000000000000000 in ?? ()

I've contacted hulu labs, but just got the boiler plate response.  It seems to me that everyone using Hulu desktop on ubuntu should be seeing this problem.

---

### Post by tersogar on 2012-04-02
Same crash on Ubuntu 12.04.:confused:

---

### Post by isantop on 2012-04-02
We can't really provide support for the Hulu desktop player. I would recommend simply using the website. It appears to work much better. 

If you really want to use the desktop client, you should check with Hulu's support to see if this is a known issue and to report a bug.

---

### Post by compholio on 2012-04-05
> **jay214128 said:**
> I have been successfully using Hulu desktop no ubuntu 10.04 LTS and 11.10.  Recently there has been some system update that now causes Hulu desktop to crash (segfault) on both 10.04 and 11.10.  Backtrace follows:
...
I've contacted hulu labs, but just got the boiler plate response.  It seems to me that everyone using Hulu desktop on ubuntu should be seeing this problem.

Are you using 32-bit or 64-bit?  I haven't had any problems with the desktop player in some time, but I can possibly help you investigate the problem.

---

### Post by Lemuriano on 2012-04-05
Same problem here. Have to use the website whitch is more stable.

---

### Post by jay214128 on 2012-04-06
I'm using 64-bit.  I found a discussion of this issue on the hulu forum, and it is apparently a known issue.  The work around is to install a local copy of an older Adobe flash player plugin (libflashplayer.so) and change the 'flash_location' in the ~.huludesktop file to find it.  This has fixed the problem on each of my systems.  This solution results in the older version of flash player being used only for huludesktop, while the browser can continue to use the most recent version.

---

### Post by l92man on 2012-04-16
This appears to potentially be related to the flashplugin-installer package rather than hulu desktop.

Huludesktop works with:

ii  flashplugin-installer                        11.1.102.63                      Adobe Flash Player plugin installer

But does not work with:

ii  flashplugin-installer                         11.2.202.228                     Adobe Flash Player plugin installer

This was the only package I updated and two systems I have went from working to not working with just this package change.

---

