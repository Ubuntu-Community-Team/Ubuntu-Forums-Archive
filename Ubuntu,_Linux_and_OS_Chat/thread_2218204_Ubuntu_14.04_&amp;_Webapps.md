---
title: "Ubuntu 14.04 &amp; Webapps"
date: 2014-04-19
forum: Ubuntu, Linux and OS Chat
---

### Post by artdesirer on 2014-04-19
What happened to Webapps in Ubuntu 14.04?
Neither Firefox & Chromium nor Browser support unity functions; in other words, websites does not suggest to install their webapp (e.g. gmail).
Those webapps on Software Center does not work properly after installing...

---

### Post by arm-c on 2014-04-22
Typically work for me.  I'd recommend that you do a "clean" install.

What you will notice is that the new apps use the Unity Web Browser, so some issues with flash integration and yahoo saying the browser is not fully supported.

---

### Post by artdesirer on 2014-04-22
> **arm-c said:**
> Typically work for me.  I'd recommend that you do a "clean" install.

What you will notice is that the new apps use the Unity Web Browser, so some issues with flash integration and yahoo saying the browser is not fully supported.
OK, firefox didn't asked me to install webapp because I reinstall it, and unity integration with firefox addon was probably removed.
Now firefox asks to install webapps, but it seems no unity functions are working. E.g. gmail webapp doesn't show folders and unread messages counter.
I did a clean install 2 times. No luck.

Also, tried to show a notification using this script:
[PHP]<script>function unityReady() {
  // Integrate with Unity!
  Unity.Notification.showNotification("Attention", "Lorem ipsum dolor sit amet");
}
var Unity = external.getUnityObject(1.0);


Unity.init({name: "Unity Web Tutorial",
            iconUrl: "http://www.ubuntu.com/tutorialIcon.png",
            onInit: unityReady});
</script>


<button onclick='Unity.Notification.showNotification("Attention", "Lorem ipsum dolor sit amet");'>Notification</button>[/PHP]

---

### Post by artdesirer on 2014-04-22
Did you try to install gmail app and see if it shows notifications, folders & counter in the hud on Ubuntu 14.04?

---

### Post by mandarvaze on 2014-04-24
I've installed Google Calendar Webapp - Seems to be working fine.
not tested notifications yet

---

### Post by lcwyche2 on 2014-04-24
I clean installed 14.04. As mentioned above, I am having trouble with Adobe. Every time 
I use 14.04 with Chromium the apps demand that I install the latest version of Flash Player.

I install and re-install using software Centre and Package Manager. Makes no difference.

What can I do?

Thanks

Laurence

---

### Post by craig10x on 2014-04-24
Switch to Chrome...it has built in pepperflash (which has the latest version of adobe flash) when you use chromium you are using the rather outdated old flash from ubuntu restricted extras that is no longer updated in linux by adobe...They have an agreement with Google to always provide the latest version in chrome...Go to the google chrome website, download the deb file and open and install in the ubuntu software center...
Pepperflash can be added to Chromium but it has to be done manually...it's easier just to use Chrome which has it built in by default :D

---

### Post by monkeybrain20122 on 2014-04-24
They work. Too bad because I actually hate them, the thread just reminds me to get rid of them. :)

---

### Post by monkeybrain20122 on 2014-04-24
> **craig10x said:**
> Switch to Chrome...it has built in pepperflash (which has the latest version of adobe flash) when you use chromium you are using the rather outdated old flash from ubuntu restricted extras that is no longer updated in linux by adobe...They have an agreement with Google to always provide the latest version in chrome...Go to the google chrome website, download the deb file and open and install in the ubuntu software center...
Pepperflash can be added to Chromium but it has to be done manually...it's easier just to use Chrome which has it built in by default :D

Chromium uses pepperflash too. Mozilla-flashplugin no longer works on chromium 34.

BTW, 95% of the websites don't care about 'up to date' flash. On this hp netbook 'outdated flash' does vdpau acceleration and 720p videos on Youtube uses maybe 5% cpu on each core. "Up to date flash" uses about 80%. :) I can count on one hand common sites that would require up to date flash to work, excluding drm streaming for which pepper-flash doesn't work either.Pepper-flash is rather over-rated. 

But Chrome actually has one big advantage over FF that somehow Chrome fans don't mention, it works better than FF with html5 because of hardware acceleration. On the same hp netbook vimeo is smooth on Chrome but completely unwatchable on Firefox unless I use a greasemonkey script to play videos in mplayer..hardware decoding for html5 depends on graphic driver and may need to be turned on manually in Chrome, but as far as I know Firefox doesn't support it at all. 

Edited: Since gstreamer-0.1-ffmpeg is removed from Trusty's repo at this point FF actually would not work on most html5 streaming sites at all because of the absence of h264 support. You actually need to use a ppa for FF to play html5 (heard it will be fixed in FF30..)

---

### Post by craig10x on 2014-04-24
Yeah, i just checked my plug ins on chrome and there is some kind of module that is able to play the html5's (both video and audio)...the adobe flash plug in is still on there but i disable it because i think it conflicts with pepper and causes higher temps...when i disable the old flash plug in and just run with pepper, my temps are lower...

Oh, the module is called: Widevine Content Decryption Module

---

### Post by monkeybrain20122 on 2014-04-24
> **craig10x said:**
> 

Oh, the module is called: Widevine Content Decryption Module

Widivine is actually for flash
[http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html](http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html)

> Widevine  is a browser plugin designed for viewing premium video content, used by  websites such as HBO Go, Cinemax and many others. It is currently fully  supported only on Windows and Mac OS X. On Linux, Widevine is bundled  with Chrome browser but it's not largely used by websites as it's only  compatible with a single browser. 

With the pipelight plugin Widivine is fully supported on system flash (provided the streaming site doesn't require fiash version > 11.2 of course)

---

### Post by lcwyche2 on 2014-04-25
> **craig10x said:**
> Switch to Chrome...it has built in pepperflash (which has the latest version of adobe flash) when you use chromium you are using the rather outdated old flash from ubuntu restricted extras that is no longer updated in linux by adobe...They have an agreement with Google to always provide the latest version in chrome...Go to the google chrome website, download the deb file and open and install in the ubuntu software center...
Pepperflash can be added to Chromium but it has to be done manually...it's easier just to use Chrome which has it built in by default :D

Hi! Thanks for your help. I tried to manually install Pepperflash but with no result.
Installing Chrome fixed the problem, but 'install in the ubuntu software center' I didn't understand at all.

One last problem. I am offered, in the system tray, two layouts for the keyboard. Both are English - US.
Nothing wrong with that, of course, but here in England I am going to need a pound sign eventually!

Laurence

---

### Post by artdesirer on 2014-04-25
Google Calendar doesn't have a webapp.

---

### Post by craig10x on 2014-04-25
I just meant that the deb file could be downloaded and then you right click it and it uses ubuntu software center to install it...not that ubuntu software center has chrome in it's repos...it doesn't of course (only chromium which is the open source version)...but of course, one can also install a deb using gdebi program as well...i have used both myself...

While it has been mentioned that pepperflash can be installed in chromium, it can be a bit "tricky" as you discovered, so simply downloading Chrome itself is an easy solution since it already has it! ;)
In addition two other things that come with Chrome is a nifty built in pdf reader if you want to read pdf files from websites without actually downloading to your hard drive (but can save it to the drive as an option of course...by right clicking the file) AND it also adds a PPA to your software sources, so you always receive the latest updated Chrome as soon as it is released (comes in to your software updater)...

---

### Post by artdesirer on 2014-04-25
and hey, people, it's not a thread about flash player; Create a new thread instead.
p.s. for Chromium, you need to install flash.

---

