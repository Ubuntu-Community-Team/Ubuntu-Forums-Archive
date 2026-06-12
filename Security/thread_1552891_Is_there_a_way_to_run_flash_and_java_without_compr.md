---
title: "Is there a way to run flash and java without compromising security?"
date: 2010-08-14
forum: Security
---

### Post by Rumpletumbler on 2010-08-14
Is there a way to run flash and java securely? Stupid question I guess. I'd like to use a couple of sites that require them but don't want to open my box up to the bad things that can happen with these. Youtube, Pandora etc. I don't know linux security well and just wonder what the ramifications of this will be?

---

### Post by Nick_Jinn on 2010-08-14
I have personally never had a problem running flash and java in Linux. I am not really sure what the threats are.

---

### Post by kiridude on 2010-08-14
The threats are very limited in Linux as most of the "bad stuff" you refer to is written for windows.

---

### Post by unspawn on 2010-08-14
> **kiridude said:**
> The threats are very limited in Linux as most of the "bad stuff" you refer to is written for windows.
So you'd say [http://www.securityfocus.com/bid/40786](http://www.securityfocus.com/bid/40786), [http://www.securityfocus.com/bid/40759](http://www.securityfocus.com/bid/40759), [http://www.securityfocus.com/bid/40797](http://www.securityfocus.com/bid/40797), [http://www.securityfocus.com/bid/40798](http://www.securityfocus.com/bid/40798), [http://www.securityfocus.com/bid/40793](http://www.securityfocus.com/bid/40793), [http://www.securityfocus.com/bid/40796](http://www.securityfocus.com/bid/40796) and [http://www.securityfocus.com/bid/40806](http://www.securityfocus.com/bid/40806) are not bad, very limited and for ClippyOS only? Nice...
([http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=flash](http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=flash))

---

### Post by bodhi.zazen on 2010-08-14
These threats are cross platform and across browsers.

The best defense is to use noscript and only allow trusted sites.

Adblocking, either adblock plus or a proxy, also helps.

See : [http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by Soul-Sing on 2010-08-14
sun java-->openjdk
flash----->gnash

---

### Post by lovinglinux on 2010-08-14
> **bodhi.zazen said:**
> These threats are cross platform and across browsers.

The best defense is to use noscript and only allow trusted sites.

Adblocking, either adblock plus or a proxy, also helps.

See : [http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

+1

BTW, these days there are critical vulnerabilities with every new flash version. From now on I will assume flash is unsafe and forget about reading security warnings about it on the web.

---

### Post by BigCityCat on 2010-08-14
Why don't you just use noscript with firefox? Then you can choose what to let through.

---

### Post by BigCityCat on 2010-08-14
> **lovinglinux said:**
> +1

BTW, these days there are critical vulnerabilities with every new flash version. From now on I will assume flash is unsafe and forget about reading security warnings about it on the web.

oops sorry. Didn't see it mentioned already.

---

### Post by linux18 on 2010-08-14
noscript
flashblock
openjdk

---

### Post by movieman on 2010-08-14
> **unspawn said:**
> So you'd say ... are not bad, very limited and for ClippyOS only? Nice...

I think the point is that a remote code execution exploit for Windows generally won't run on Linux; that's security by obscurity, but for now there's a much lower threat from Flash on Linux than on Windows. It's possible that there could be a single exploit which would work on all operating systems (e.g. some method of stuffing Javascript into the browser from Flash), but less likely.

Personally I created an Apparmor wrapper which prevents Flash from doing much of anything; not only to prevent exploits, but because it reads a vast amount of stuff that I can't see it having any good use for and apparently tries to write into /var/cache/fontconfig even though it doesn't have permission.

---

### Post by OpSecShellshock on 2010-08-14
Firefox 3.6.8 (at least on Windows) runs plugins as their own process so that if there's a crash it won't kill the whole browser. Not sure how that affects the execution of arbitrary code following an exploit, though. But that's something to remember even in cross-platform applications--the exploit, the arbitrary code, and the payload are all discrete from a risk analysis standpoint, and all of them have to succeed.

NoScript can be configured on a pretty granular level, too, such that even on trusted sites all Flash objects are blocked by default.

---

### Post by Rumpletumbler on 2010-08-14
I have noscript and a few other tools. 

Pandora for instance doesn't work without flash and so you can't disable it. 

I guess I can load it and enable/disable it every time I visit a page I trust that requires it.

Can someone tell me why the red smiley appears to the left of the thread subject line sometimes when I post? 

I don't put it there.

---

### Post by lovinglinux on 2010-08-15
> **Rumpletumbler said:**
> I have noscript and a few other tools. 

Pandora for instance doesn't work without flash and so you can't disable it. 

I guess I can load it and enable/disable it every time I visit a page I trust that requires it.

Can someone tell me why the red smiley appears to the left of the thread subject line sometimes when I post? 

I don't put it there.

NoScript has an option to put placeholders where the flash content is, so all you have to do to play the content you want is click it.

---

### Post by Rumpletumbler on 2010-08-15
Thanks for the help everyone. I'm going to have to learn a lot more about the tools I have installed.

---

### Post by OpSecShellshock on 2010-08-15
The most important thing to learn about the available tools is that they make it so that scripted content doesn't have to be all or nothing. You can set it up so that you only need to allow exactly what you want, enabled on an individual basis. This includes content on sites you've already decided to allow. Open up the options in NoScript and go through all of the tabs. It allows for some pretty detailed control over how your browser renders web content. All of the tabs in the options should also have links to guides on the add-on developer's website. It's pretty cool stuff.

---

### Post by Rumpletumbler on 2010-08-16
If I go to pandora.com I have to allow pandora.com which is fairly obvious. 

Then I have to install flash player, swfdec swf player and gnash swf player. 

After that I don't know what I would need to allow etc. , however, are these plugins safe to install and are they really all necessary to run Pandora?

---

### Post by lovinglinux on 2010-08-16
> **Rumpletumbler said:**
> If I go to pandora.com I have to allow pandora.com which is fairly obvious. 

Then I have to install flash player, swfdec swf player and gnash swf player. 

After that I don't know what I would need to allow etc. , however, are these plugins safe to install and are they really all necessary to run Pandora?

Installing them all will only cause you trouble.

See [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Rumpletumbler on 2010-08-16
But then installing plugins gives the plugin unlimited access to your browsing, correct?

Edit:  It runs this as a script I'm guessing from your flash/firefox tutorial. Then it updates flash as necessary it seems from what I've read. Is that all it does? 

> *sudo apt-get purge lightspark*
*sudo apt-get purge  swfdec-mozilla*
*sudo apt-get purge mozilla-plugin-gnash*
*sudo apt-get purge adobe-flashplugin*
*sudo apt-get purge flashplugin-nonfree*
*sudo apt-get purge flashplugin-installer*
*rm -f $HOME/.mozilla/plugins/*flash*so*
*rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash*
*sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so*
*sudo   rm -f /usr/lib/mozilla/plugins/libflashplayer.so *
*sudo apt-get install  flashplugin-nonfree*
[LEFT]*sudo ln -s  /usr/lib/mozilla/plugins/flashplugin-alternative.so  /usr/lib/firefox-addons/plugins/libflashplayer.so*[/LEFT]


---

### Post by lovinglinux on 2010-08-17
> **Rumpletumbler said:**
> But then installing plugins gives the plugin unlimited access to your browsing, correct?

Edit:  It runs this as a script I'm guessing from your flash/firefox tutorial. Then it updates flash as necessary it seems from what I've read. Is that all it does?

Don't worry about the extension security, it doesn't run anything malicious, otherwise it wouldn't be approved by Mozilla. Besides, it asks for confirmation before running the script and displays the commands that will be executed. It can't do anything without your consent. Nevertheless, what it does is basically what is in the commands above. Additionally, it detects the browser architecture and it can provide updates if Adobe releases new versions that can be downloaded manually only (not the case right now).

If you don't feel comfortable running the extension, you can use that command. It will have the same effect.

---

### Post by Rumpletumbler on 2010-08-17
> **lovinglinux said:**
> If you don't feel comfortable running the extension, you can use that command. It will have the same effect.

I'll give it a go. Making stupid assumptions seem to be part of the learning process for me. Every time I seem to think I understand how something works to a point or am beginning to do so then I find out I lack understanding even on a rudimentary level.

---

### Post by lovinglinux on 2010-08-17
> **Rumpletumbler said:**
> I'll give it a go. Making stupid assumptions seem to be part of the learning process for me. Every time I seem to think I understand how something works to a point or am beginning to do so then I find out I lack understanding even on a rudimentary level.

Don't worry, is part of the learning process and there is nothing wrong about being careful with commands and programs you find on the web. In this case I can vouch for it, because I'm the developer of FLASH-AID.

---

### Post by Lars Noodén on 2010-08-23
Flash, no. 

Java, yes.  

Javascript in a web page, no especially not over IPv4 without DNSSEC.

---

### Post by kiridude on 2010-08-24
> **Lars Noodén said:**
> Flash, no. 

Java, yes.  

Javascript in a web page, no especially not over IPv4 without DNSSEC.

So Lars, does this mean I should not view a video online again (as they are basically all flash)?

---

### Post by Lars Noodén on 2010-08-24
> **kiridude said:**
> So Lars, does this mean I should not view a video online again?

No.  It just means that you should not use Flash, no more no less. There are other container formats and competent/responsible sites offer them. 

Flash is a container format which can contain useful audio or video next to the security holes.  Most of the video claiming to use the Flash is H.264 wrapped in Flash and can be extracted.  Or the sites hosting the Flash offer other containers, even if they are not obvious.  

If you are addicted to videos hosted at sites promoting Flash over Quicktime or MPEG, then your choice is this:  

1) Accept the fact that anyone on the remote server or between you and the remote server can decide to run programs on your machine under your user id.  The corollary to that is to accept the rage from others about that.  

2) Find a script (or write your own) or firefox plugin to find the Ogg, Quicktime or MPEG versions on the video sites.

3) Find a script (or write your own) or firefox plugin to extract the video from Flash and wrap it in a safe container.

---

### Post by lovinglinux on 2010-08-24
> **Lars Noodén said:**
> 3) Find a script (or write your own) or firefox plugin to extract the video from Flash and wrap it in a safe container.

Already did that ;)

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

Unfortunately, works only on a few sites, but YouTube is supported and supporting more sites is on my todo list.

---

### Post by Rumpletumbler on 2010-08-24
> **lovinglinux said:**
> Already did that ;)

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

Unfortunately, works only on a few sites, but YouTube is supported and supporting more sites is on my todo list.

Which plugin and or player works best with your plugin?

I went to try it and it was going to use Movie Player and install gstreamer-bad which I just canceled in favor of seeing what works best before trying it.

So what's the best solution?

---

### Post by lovinglinux on 2010-08-24
> **Rumpletumbler said:**
> Which plugin and or player works best with your plugin?

I went to try it and it was going to use Movie Player and install gstreamer-bad which I just canceled in favor of seeing what works best before trying it.

So what's the best solution?

the extension doesn't use external players, only browser plugins.

For me, the best plugin to use with my extension is gecko-mediaplayer, nevertheless I have also tested with gxine, kaffeine, mozplugger, totem and xine. VLC also works, but is buggy and don't like that plugin.

Some plugins behave differently in regard to buffer cache. If you are using gecko-mplayer, you can set the buffer cache minimum in ~/.mplayer/config, so it will buffer sooner.

```
cache=8192
cache-min=10.0
cache-seek-min=30
```

You might need to adjust the above values to your liking.

---

### Post by Soul-Sing on 2010-08-25
> **lovinglinux said:**
> Already did that ;)

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

Unfortunately, works only on a few sites, but YouTube is supported and supporting more sites is on my todo list.

Nice lovinglinux, thank you. I agree with with Lars Noodén by the way. To put it less mild: adobe flash= malware.

---

### Post by kiridude on 2010-08-25
Thanks for the explanation Lars. When you say,
> Accept the fact that anyone on the remote server or between you and the remote server can decide to run programs on your machine under your user id do you mean someone can run programs only while flash is in use, or they can install stuff on my machine through flash which can run anytime?

Lovinglinux, glad you wrote that add on. Gonna go check it out.

---

### Post by OpSecShellshock on 2010-08-25
> **kiridude said:**
> Thanks for the explanation Lars. When you say,
 do you mean someone can run programs only while flash is in use, or they can install stuff on my machine through flash which can run anytime?

Lovinglinux, glad you wrote that add on. Gonna go check it out.

No, they can't install anything as long as the browser is not run under elevated privileges. I'd imagine that there are ways to approximate "installation" by using flash cookies and/or cached data, but as long as all of that stuff is deleted every time the browser closes there shouldn't be that particular problem. There is potential for other problems, depending on what the flash container is written to do, but most of those have more to do with retrieving data than with planting it.

---

### Post by wacky_sung on 2010-08-25
> **OpSecShellshock said:**
> No, they can't install anything as long as the browser is not run under elevated privileges. I'd imagine that there are ways to approximate "installation" by using flash cookies and/or cached data, but as long as all of that stuff is deleted every time the browser closes there shouldn't be that particular problem. There is potential for other problems, depending on what the flash container is written to do, but most of those have more to do with retrieving data than with planting it.

Yeah i do agree with what you wrote.Most malwares writer usually use cookies such as site / flash to inject exploits/keylogger  into it.

---

### Post by Rumpletumbler on 2010-08-25
> **lovinglinux said:**
> For me, the best plugin to use with my extension is gecko-mediaplayer,

I loaded it and it caches the video and then sits. If I click the play button which is already depressed it will display maybe the first frame of the video and nothing else happens.

Ideas?

---

### Post by lovinglinux on 2010-08-25
> **Rumpletumbler said:**
> I loaded it and it caches the video and then sits. If I click the play button which is already depressed it will display maybe the first frame of the video and nothing else happens.

Ideas?

See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by kiridude on 2010-08-26
Guys, one more question: If I download a .flv video from a site (from my temp folder), is that video a threat also, or is the video only extracted?

---

### Post by Rumpletumbler on 2010-08-28
> **lovinglinux said:**
> See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").

Installed it again and it works, however, there is way too much stuttering going on. Used your cache settings and I can't play anything without a good bit of stutter.

Without it I get occasional stutter but not as much. I see there's about 3000 threads related to stuttering out there. I imagine it may just be my lame box just can't do it.

---

### Post by lovinglinux on 2010-08-28
> **Rumpletumbler said:**
> Installed it again and it works, however, there is way too much stuttering going on. Used your cache settings and I can't play anything without a good bit of stutter.

Without it I get occasional stutter but not as much. I see there's about 3000 threads related to stuttering out there. I imagine it may just be my lame box just can't do it.

Have you tried to pause the video until it buffers more? Do you have the latest proprietary video driver installed?

---

### Post by lovinglinux on 2010-08-28
> **kiridude said:**
> Guys, one more question: If I download a .flv video from a site (from my temp folder), is that video a threat also, or is the video only extracted?

See [http://www.mindedsecurity.com/MSA01110707.html](http://www.mindedsecurity.com/MSA01110707.html)

I don't know if that would affect other players that can play flv files, like gnome-mplayer. As far as I can understand, that vulnerability affects only the flash plugin.

---

### Post by Rumpletumbler on 2010-08-28
> **lovinglinux said:**
> Have you tried to pause the video until it buffers more? Do you have the latest proprietary video driver installed?

I buffer it entirely before playing. 

I have an ATI Radeon 9700 Pro and there's no driver support that I'm aware of. The performance is horrible. 

For instance in Windows which I no longer run in Urban Terror I get 90+ FPS with this card but in Ubuntu it's unplayable at around 17-20 FPS.

---

### Post by wacky_sung on 2010-08-28
> **lovinglinux said:**
> See [http://www.mindedsecurity.com/MSA01110707.html](http://www.mindedsecurity.com/MSA01110707.html)

I don't know if that would affect other players that can play flv files, like gnome-mplayer. As far as I can understand, that vulnerability affects only the flash plugin.

The vulnerability is outdated and the latest version of the current flash player is 10.1.82.76 as for now.

[http://www.mindedsecurity.com/MSA01110707.html](http://www.mindedsecurity.com/MSA01110707.html)
```
Minded Security Labs: Advisory #MSA01110707
Flash Player/Plugin Video file parsing Remote Code Execution



Tested OS:
	       Windows xp sp2 Italian,
	       Windows xp sp2 English
	       Linux Ubuntu 6.10


Tested Flash Versions:
	       Flash Plugin 9.0.28.0 Windows
	       Flash Player 9.0.28.0 Windows
	       Flash Plugin 9.0.31.0 Linux
	       Flash Player 9.0.31.0 Linux

```

Test your flash player [version check]("http://flashbuilder.eu/flash-player-version.html").

---

### Post by lovinglinux on 2010-08-28
> **wacky_sung said:**
> The vulnerability is outdated and the latest version of the current flash player is 10.1.82.76 as for now.

Test your flash player [version check]("http://flashbuilder.eu/flash-player-version.html").

The  version is irrelevant. I have posted that report because kiridude was asking if a downloaded flv could be a security risk. It can. Besides, a critical vulnerability that can cause flash to crash, then execute arbitrary code and take over your machine is discovered in every new flash versions these days. Flash 10.1.82 was released to fix a similar issue in 10.1.63, which was released to fix a similar issue on 10.0.45...and goes on.

---

### Post by OpSecShellshock on 2010-08-28
If a file contains an exploit specifically for Flash, but is instead run in a standalone player that is not Flash, then the exploit shouldn't work. If a media file that was put into the Flash container for cross-platform streaming has instead been completely downloaded to disk and is played outside the browser entirely, then the risk would be even more limited. Note that this is just in general; it's possible, depending on the nature of the file, the exploit, and the arbitrary code, that other players would be affected. If so, it would most likely just crash.

---

### Post by wacky_sung on 2010-08-28
Since flash is exploitable as much as the browser,the solution is either permanent disable it or add apparmor to it.There is always a risk on every software but it is how you wanna take the risk factor and containment to be a fail safe solution.

---

### Post by Lars Noodén on 2010-08-29
> **kiridude said:**
> Thanks for the explanation Lars. When you say,  do you mean someone can run programs only while flash is in use, or they can install stuff on my machine through flash which can run anytime?


Yes, the latter.  Anything you or your browser can do or has access to, Flash has access to.  That alone is enough to give full access to the keyboard and other devices or install programs local to just that account.  If there is a local exploit, then the same can be done for any account on the machine. 

As it was put above, [Adobe Flash = malware](http://www.google.com/search?hl=en&q=flash+vulnerability).  
One of the advantages of Linux has been better security.  
Bringing bad design, goals or thinking from other brands is bad advice and is theoretically [not allowed on the forum](http://ubuntuforums.org/announcement.php?f=339).  

If you are looking to play video, then use a safer container format or strip off the container using one of the tools in the previous post.  

Fortunately, Flash is limited to the commonb but antiquated x86 architecture so if you do not use Intel, AMD, Cyrix, etc, then you are fine in that regard.  But if you let Adobe lock your data (or the data you rely on) into a container that only runs on x86, then by doing so you limit the choices available to the rest of us.

Freedom applies to data, not just software so patronize web sites that respect open formats.  We have both the Internet and the WWW *only* because of open formats.

---

### Post by albandy on 2010-08-29
Use a chroot environment.

This is an example:
[http://www.ubuntu-es.org/node/82182](http://www.ubuntu-es.org/node/82182)

---

### Post by rookcifer on 2010-08-29
> **Lars Noodén said:**
> Freedom applies to data, not just software so patronize web sites that respect open formats.  We have both the Internet and the WWW *only* because of open formats.

Tell that to Canonical who seems to disagree with the sentiment.  After all, they chose the patent encumbered MP3 over Ogg Vorbis for the Ubuntu Music Store. :o

---

### Post by kiridude on 2010-08-29
Lars, thanks for your insight, but this comment seemed a bit out of place:

> Bringing bad design, goals or thinking from other brands is bad advice and is theoretically not allowed on the forum. 

I have done none of the things mentioned in this sentence, and the link you provide has nothing to do with "bad design, goals or thinking from other brands." It is a post about people suggesting commands that damage peoples computers.

Flash is ubiquitous on the net and I (like many others) am looking for a way to view video online securely. To limit myself only to sites that do not use flash would be a HUGE limitation - take YouTube for example.

Luckily, Lovinglinux has offered a solution and I look forward to a solution that can work universally. I will make a donation to lovinglinux.

---

### Post by OpSecShellshock on 2010-08-29
Well the good news is there's movement away from Flash already happening in some spaces. I read somewhere last week that Vimeo has already gone native by default. I tested an embed, and it seemed to work pretty well. Curiously, even though Flash was not used, I still ended up with a "settings.sol" in my .macromedia folder.

---

### Post by lovinglinux on 2010-08-29
> **kiridude said:**
> Luckily, Lovinglinux has offered a solution and I look forward to a solution that can work universally. I will make a donation to lovinglinux.

Thanks. 

The definitive solution could be [WebM]("http://www.webmproject.org/"). Firefox 4 beta already support it, as other recent browsers versions. Nevertheless, performance is not great.

These are CPU usage values on my machine, while playing YouTube videos (not fullscreen):

[LIST]
[*]Flash - 40%
[*]WebM - 35%
[*]FlashVideoReplacer - 14%
[/LIST]

You can sign up for YouTube HTML5 Beta at [http://www.youtube.com/html5](http://www.youtube.com/html5). To get Firefox 4, see [my tutorial]("http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html").

---

### Post by Lars Noodén on 2010-08-30
> **lovinglinux said:**
> 
The definitive solution could be [WebM]("http://www.webmproject.org/"). Firefox 4 beta already support it, as other recent browsers versions. .

Yes.  [Ogg Theora](http://www.h-online.com/open/news/item/Mozilla-defends-Firefox-s-HTML5-support-for-only-Ogg-Theora-video-912003.html) is also an option and has been supported for a while by Firefox and the uptodate browsers.  User communities and software projects support Ogg.  Hardware  vendors have been pre-loading H.264 into their DSPs, for all I can tell from speaking with some phone developers H.264 is a non-technical decision (their owner's unpleasant desire to introduce software patents in Europe).

At this stage, either WebM or Ogg Theora or both are good choices.

---

