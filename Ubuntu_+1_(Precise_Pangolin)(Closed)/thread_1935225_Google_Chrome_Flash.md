---
title: "Google Chrome Flash"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by clifford junior on 2012-03-03
Sorry to post this here, but I don't know whether this is specific to 12.04 or a common problem. I searched and couldn't find anything on it. I'm running 12.04 Beta

If I try and play flash (eg. YouTube) in Google Chrome on 12.04, it plays but with no sound and at what I would describe as double speed and choppy. This problem does not occur in Firefox.

Does anyone else experience this problem and/or know how to resolve it?

Thanks.

---

### Post by paul_in_london on 2012-03-03
> **clifford junior said:**
> Sorry to post this here, but I don't know whether this is specific to 12.04 or a common problem. I searched and couldn't find anything on it. I'm running 12.04 Beta

If I try and play flash (eg. YouTube) in Google Chrome on 12.04, it plays but with no sound and at what I would describe as double speed and choppy. This problem does not occur in Firefox.

Does anyone else experience this problem and/or know how to resolve it?

Thanks.

Which versions of Chrome/Flash are you using?

I'm using Adobe Flash 11.2.202.221 (11.2 RC1 64 bit) from here:

[http://labs.adobe.com/downloads/flashplayer11-2.html](http://labs.adobe.com/downloads/flashplayer11-2.html)

These 64 bit versions of Chrome and Chromium are working normally for me with Flash 11.2 RC1:

```
paul@precise-64:~$ apt-cache policy google-chrome-unstable
google-chrome-unstable:
  Installed: 19.0.1055.1-r123982
  Candidate: 19.0.1055.1-r123982
```

```
paul@precise-64:~$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 18.0.997.0~svn20120105r116462-0ubuntu1~ucd1
  Candidate: 18.0.997.0~svn20120105r116462-0ubuntu1~ucd1
```

I've had problems before though with Chrome/Chromium earlier in the 12.04 release cycle where I was only getting sound (no picture) when trying to play flash content.

---

### Post by clifford junior on 2012-03-04
Hi

I'm using the same version of chrome as you and have uninstalled and reinstalled flash player but I have no luck.

The problem occurs in both chrome and chromium. Its really annoying as I can't get it to work.

One thing I want to clarify is whether updating flash makes a difference as I was under the impression chrome uses its own flash player and when I look in opt/chrome there is a file called pepperflash.

This would make sense as Firefox is working .

---

### Post by clifford junior on 2012-03-04
Could flash and the built in chrome flash be interfering with each other?

---

### Post by zuti on 2012-03-04
I noticed the same problem with Chrome 19.0.1055.1-r123982. Before all media played by the browser had a problem with choppiness/speed (html5 video, ogg, mp3) yet flash worked ok, but this release flipped the problem upside down. I can get flash content to play ok sometimes, but mostly not. Though I do get audio too (which is also fast and choppy). 

I'd say this isn't a 12.04 problem since it happened on 11.10 for me when updating to the said version of Chrome. It actually got a little better with 12.04 (very, very little:)

---

### Post by paul_in_london on 2012-03-04
> **clifford junior said:**
> Could flash and the built in chrome flash be interfering with each other?

I just checked and in Chrome I actually had both flash plugin versions enabled so I disabled the built-in version and flash still works ok here:

```
[B][COLOR="Red"]Flash (2 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202[/COLOR][/B]
Name:	Shockwave Flash
Description:	Shockwave Flash 11.2 r31
Version:	11.2.31.109
**[COLOR="Red"]Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so[/COLOR]**
[B][COLOR="Red"]Type:	PPAPI (out-of-process)
 	 Enable[/COLOR][/B]
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
[B][COLOR="Red"]Version:	11.2 r202
Location:	/usr/lib/adobe-flashplugin/libflashplayer.so
Type:	NPAPI
 	 Disable[/COLOR][/B]
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Disable   Always allowed
```

Maybe **[COLOR="Red"]iron v17.0.1000.0[/COLOR]** would work for you?

[https://www.srware.net/forum/viewtopic.php?f=17&t=3290&sid=0550a4ec131785de3d06d0c4080d23a3](https://www.srware.net/forum/viewtopic.php?f=17&t=3290&sid=0550a4ec131785de3d06d0c4080d23a3)

---

### Post by zuti on 2012-03-04
> **paul_in_london said:**
> I just checked and in Chrome I actually had both flash plugin versions enabled so I disabled the built-in version and flash still works ok here

Well I'll be... I had to try that too. After disabling the built-in Flash all the problems went away. This is after 5-10 minutes of testing (will probably break as soon as I post this message:). So at least for me these problems are related to the flash plugin provided with the latest dev Chrome.

---

### Post by clifford junior on 2012-03-04
> **zuti said:**
> Well I'll be... I had to try that too. After disabling the built-in Flash all the problems went away. This is after 5-10 minutes of testing (will probably break as soon as I post this message:). So at least for me these problems are related to the flash plugin provided with the latest dev Chrome.

it does kind of make sense as Firefox is working fine.

could you please tell me how to disable chromes built in pepperflash?

---

### Post by clifford junior on 2012-03-04
OK I managed to find the plugins within chrome and disabled both pepper and then flash and left the other but I still have the problems with both variations.

It seems as if I can't use chrome if i need to use flash, which is **** basically.

---

### Post by xebian on 2012-03-04
> **clifford junior said:**
> OK I managed to find the plugins within chrome and disabled both pepper and then flash and left the other but I still have the problems with both variations.

It seems as if I can't use chrome if i need to use flash, which is **** basically.

Am not sure if you are aware you are using UNSTABLE version.

..
paul@precise-64:~$ apt-cache policy google-chrome-unstable
google-chrome-unstable:
  Installed: 19.0.1055.1-r123982
  Candidate: 19.0.1055.1-r123982

..

The STABLE version is 17 and the 64-bit has no Flash built-in.

---

### Post by clifford junior on 2012-03-04
Hi I tried the stable version first and had the same problems. I thought updating to the newest version might remedy it.

---

### Post by clifford junior on 2012-03-04
I just downgraded to the stable version of chrome and flash is working. its really strange as i was using this version when the problem was first encountered. pretty confusing.

at least we know that the built in pepperflash (in the unstable version) is not working as it should be, for me anyhow.

confusing.

---

### Post by paul_in_london on 2012-03-04
> **clifford junior said:**
> I just downgraded to the stable version of chrome and flash is working. its really strange as i was using this version when the problem was first encountered. pretty confusing.

at least we know that the built in pepperflash (in the unstable version) is not working as it should be, for me anyhow.

confusing.

So when you were using google-chrome-unstable (19.0.1055.1-r123982) you tried both flash plugins with the other one disabled? There are some glitches with the pepper plugin, but the standard flash plugin seems to work properly here.

---

### Post by clifford junior on 2012-03-04
> **paul_in_london said:**
> So when you were using google-chrome-unstable (19.0.1055.1-r123982) you tried both flash plugins with the other one disabled? There are some glitches with the pepper plugin, but the standard flash plugin seems to work properly here.

Yeah I tried both individually and made sure I did a restart in between and had the same problem. I don't understand what's going on as I had the sane problem with version 17 but now its totally fine.

---

### Post by clifford junior on 2012-03-04
Also the volume level reset problem I posted about has also resolved itself since I took of version 19. Something is drastically wrong with that on my system.

---

### Post by paul_in_london on 2012-03-04
> **clifford junior said:**
> Yeah I tried both individually and made sure I did a restart in between and had the same problem. I don't understand what's going on as I had the sane problem with version 17 but now its totally fine.

Strange. Have you tried chromium?

```
paul@precise-64:~$ apt-cache policy chromium-browser
chromium-browser:
  [B][COLOR="Red"]Installed: 18.0.997.0~svn20120105r116462-0ubuntu1~ucd1
  Candidate: 18.0.997.0~svn20120105r116462-0ubuntu1~ucd1[/COLOR][/B]
```

On my system I'm just using the standard flashplugin with chromium:

```
[B][COLOR="Red"]Flash (2 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/adobe-flashplugin/libflashplayer.so
Type:	NPAPI
 	 Disable[/COLOR][/B]
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
[B][COLOR="Red"]Name:	Shockwave Flash
Version:	11.0 r1
Location:	/usr/lib/chromium-browser/plugins/libflashplayer.so.11rc1
Type:	NPAPI
 	 Enable[/COLOR][/B]
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
```

which also works ok here. Chromium's built-in flash isn't the pepper plugin though. I don't remember changing the path to that or the name, but maybe I did at some point.

There's still no precise channel for the chromium daily ppa yet:

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by pingi on 2012-03-09
Hello,

My problem is that whether I install Chromium from Ubuntu repository or Google Chrome directly from Google, none of them come with built-in flash that is supposed to be where (I ran about:plugins command).

And I have no idea what's the cause of that. My OS is 64-bit.

Does anyone have any clues on what is going on?

**EDIT:**

OK, it seems that the answer is that because my system is 64-bit. Bummer...

But it appears that x64 support is already in place though:

[http://codereview.chromium.org/9431007](http://codereview.chromium.org/9431007)

So, I installed current dev version 19.0.1061.1 and the flash plugin is there. However this build is not usable yet with YouTube, for me, as there was some kind of white overlay over the whole browser window when playing videos and sound was choppy.

---

