---
title: "Adobe Flash Player 10 BETA released!"
date: 2008-05-15
forum: The Cafe
---

### Post by Kosimo on 2008-05-15
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Hello guys, as you can see, Adobe has released the first beta of 10th series, and yes, is available for linux.. 
Damn, I really hope that even if is a beta, works a bit better in hardy and pulse audio. Let's give it a try!

Good luck!

[B]
EDIT:   How-to Update to Flash Player 10 Beta:[/B] (For final version check Edit4)

First remove your current flash player from Synaptic:

Then download and unpack the package, then: > sudo mv path/to/flash/libflashplayer.so /etc/alternatives

Now let's link it: > sudo ln -s /etc/alternatives/libflashplayer.so /usr/lib/xulrunner-addons/plugins/

**Edit2**: On July 2 Adobe published a new Beta, with Namely Wmode and V4L2 support and performance improvements

**Edit3**: September 14: New release candidate "Astro" 10.0.12.10

**Edit4**: October 15:  Final version available 10.0.12.36

**Edit5**: November 17:  Flash Player 10 Alpha 64 Bit Linux released!  [Download Here]("http://labs.adobe.com/technologies/flashplayer10/")
 
The easiest and quicker way to install Flash Player is downloading the official (first time ever) Flash .deb for ubuntu 8.04+. It is also possible to add the new official apt-get repository in order to keep using always the latest version.

---

### Post by Kosimo on 2008-05-15
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by kesman on 2008-05-15
Nice, nice! Where'd you hear about this? I didn't notice anything on any site :P I've heard something about Adobe opening flashplayer's source in some time, is that true?

---

### Post by Swarms on 2008-05-15
64 bit version pretty please!

---

### Post by soxs on 2008-05-15
Unless adobe will produce a 64bit version, it makes no diffrence for me at all.
For installing, well, adobe says you must first delete any old flashplugin before installing, but how to install.. I have no clue. I guess copying would be fine, but in that case you will have to know _where_ to copy those files (I do not know).

Edit: No, adobe will not open flasplyer source, but flash documentation.

[www.phoronix.com](www.phoronix.com)

---

### Post by schtufbox on 2008-05-15
Still useless in fullscreen! (still, that could change as it finsishes beta..just for now, it's still no good in fullscreen)

---

### Post by Sef on 2008-05-15
Moved to Community Cafe.

---

### Post by kpkeerthi on 2008-05-15
The .so file should be copied to /usr/lib/firefox/plugins folder. Restart firefox.

---

### Post by ELD on 2008-05-15
Can anyone tell me if it works better than flash 9 at all? The crashes with pulseaudio are fracking annoying.

---

### Post by dixon on 2008-05-15
> **schtufbox said:**
> Still useless in fullscreen! (still, that could change as it finsishes beta..just for now, it's still no good in fullscreen)
Are you using compiz?

> For Linux, the hardware acceleration feature will not work if you are using a compositing window manager (compits).  In this case, Flash Player 10 Beta will always fall back to software.  If you would like to test Flash Player 10 Beta on Linux, please disable your compositing window manager.

---

### Post by oedipuss on 2008-05-15
> **kpkeerthi said:**
> The .so file should be copied to /usr/lib/firefox/plugins folder. Restart firefox.

For hardy I think its better to move it to /usr/lib/flashplugin-nonfree which is where /etc/alternatives links to. Browsers then can link to a generic file in alternatives which can switch from flash to gnash to swfdec easily. (Oh, and keep the original file v9 there, just rename it to something obvious such as .so.version9) 

Seems somewhat the same so far.. Youtube fullscreen is just as choppy as before, but veoh seemed to be doing better. 
I'll try it with pulseaudio next, see if it works/crashes .

Edit: ha that was easy -_- It crashed just as readily as v9 with libflashsupport installed, with the 2nd video I opened. So I guess no pulseaudio yet.

---

### Post by dixon on 2008-05-15
Another interessting quote
> Adobe has even upped the Linux ante with a new installer specially tailored for Ubuntu users.

---

### Post by djdrdewey on 2008-05-15
just downloaded it, i uninstalled v. 9, and im gonna attempt to install it the same way as you would in 9. (im using 64 bit btw, i hope it works!!!)

---

### Post by oedipuss on 2008-05-15
> 
Adobe has even upped the Linux ante with a new installer specially tailored for Ubuntu users. 


Ah, so an installer "tailored for ubuntu", but no standard deb, which is really an installer tailored for ubuntu.

Are they allowing redistribution now, at least?
By the way, the dropdown menus behind flash bug is still there :P  Ok that might be hard to fix, but I'd expect at least something out of a new major release, even if it's beta.

---

### Post by Colonel Kilkenny on 2008-05-15
With a little bit testing I'd say this thing is working better than 9r124. Little bit of problems with zoom in youtube (zoom out / show all after zoom in doesn't actually show all and full screen isn't exactly full screen (quite near though)).

Although I'm not going to install this over flashplugin-nonfree I guess I'll be dumping 9r124 for now. Browsers can use it from somewhere else.

---

### Post by fs3rp4 on 2008-05-15
To me it's working better than version 9. The use of CPU is very low now when I play videos and until now is very stable...

---

### Post by forrestcupp on 2008-05-15
Awesome!  Remember how long it took us to get version 9 for Linux?  We had a very long wait after all of the websites had already switched to the newer version.  And we never even got a version 8.  So Flash was mostly useless to us back then.

I'm thankful that this time around they're developing for Linux at the same time.

---

### Post by OffHand on 2008-05-15
> **Kosimo said:**
> [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Hello guys, as you can see, Adobe has released the first beta of 10th series, and yes, is available for linux.. 
Damn, I really hope that even if is a beta, works a bit better in hardy and pulse audio. Let's give it a try!

But, question is: Now that Firefox has Ubufox and flash player has been installed automatically, how can I install this beta?
Just copying the flash.so plugin into Mozilla's directory in /home?

Thanks, and good luck!

I would make a symbolic link to the real file...

---

### Post by SunnyRabbiera on 2008-05-15
> **forrestcupp said:**
> Awesome!  Remember how long it took us to get version 9 for Linux?  We had a very long wait after all of the websites had already switched to the newer version.  And we never even got a version 8.  So Flash was mostly useless to us back then.

I'm thankful that this time around they're developing for Linux at the same time.

well with the ubuntu installer it seems that adobe is waking up to us, though I hope they make an easy installer for other linux versions.

---

### Post by sixstorm on 2008-05-15
> **dixon said:**
> Another interessting quote

Where the hell is this installer at?  I ran the installer in terminal, but it asks where FF is installed.  I tell it "usr/lib/mozilla" but it says "/Desktop/flash_player/usr/lib/mozilla not found".  WTF?

---

### Post by stevoo on 2008-05-15
> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 b218

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Well i have installed it .... 

All you need to do is go into you firefox-3.0b5 directory in plugins and remove the .so from there
Then find the package extract it and run the installer using sh.

That should install flash 10. 

But still no audio from pulse :( I was hoping for some audio :(
Hopefully flash will be added in the reps so it will be automatically upgraded soon.

---

### Post by maniacmusician on 2008-05-15
> **sixstorm said:**
> Where the hell is this installer at?  I ran the installer in terminal, but it asks where FF is installed.  I tell it "usr/lib/mozilla" but it says "/Desktop/flash_player/usr/lib/mozilla not found".  WTF?
you forgot the / in front of usr. if you just type in usr/lib/mozilla, it's going to append that to whatever directory you are in.

---

### Post by Kosimo on 2008-05-15
Can someone make a SIMPLE how to, and so I'll edit the first post to help everybody to test this new release?

Thank you guys

---

### Post by fs3rp4 on 2008-05-15
> **sixstorm said:**
> Where the hell is this installer at?  I ran the installer in terminal, but it asks where FF is installed.  I tell it "usr/lib/mozilla" but it says "/Desktop/flash_player/usr/lib/mozilla not found".  WTF?

If you're using Hardy:

You should install in /usr/lib/firefox-3.0b5

---

### Post by Mazza558 on 2008-05-15
Just tried it, working fine in Gutsy.

One REALLY REALLY annoying thing is that they STILL haven't fixed transparency in Flash.

---

### Post by vasilis34 on 2008-05-15
Has anyone tried this on the 64bit version of Hardy? My idea was trying to copy the new .so file in the place of the file /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so but it didn't work.
I really have no clue on the way that npwrapper works, so if anyone could suggest something I would be grateful.

---

### Post by mech7 on 2008-05-15
does wmode transparant finally works ?

---

### Post by cdean on 2008-05-15
> **vasilis34 said:**
> Has anyone tried this on the 64bit version of Hardy? My idea was trying to copy the new .so file in the place of the file /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so but it didn't work.
I really have no clue on the way that npwrapper works, so if anyone could suggest something I would be grateful.

I used npwrapper on the new libflashplayer.so and placed it in that directory, but it did not load into Firefox. Perhaps npwrapper might need to be updated to support this new version.

---

### Post by sloggerkhan on 2008-05-15
well, I've givent his a go, but even with compiz disabled it still uses CPU rendering...

Could this have to do with how it's detecting compiz?

---

### Post by FuturePilot on 2008-05-15
Why won't the hardware acceleration work with Compiz? I hope they fix that seeing how popular Compiz is.

> **Mazza558 said:**
> 

One REALLY REALLY annoying thing is that they STILL haven't fixed transparency in Flash.

*sigh* I wonder if they will ever fix that.....

---

### Post by zachtib on 2008-05-15
> **FuturePilot said:**
> Why won't the hardware acceleration work with Compiz? I hope they fix that seeing how popular Compiz is.



*sigh* I wonder if they will ever fix that.....

I agree, compiz support and 64bit support would make flashplayer 10 a great release

---

### Post by somecallmechief on 2008-05-15
Does anyone have a link to this magical deb package, or am I missing something?  I don't see any option to download a Debian version of Flash from Adobe's site, and a few minutes of Googling hasn't yielded any better results.

Anyone with success on Hardy amd64?

-scmc

---

### Post by FuturePilot on 2008-05-15
Well, I just tested it and the CPU usage is definitely down. However video playback is still crap. Lots of tearing still. :(

---

### Post by qazwsx on 2008-05-15
nspluginwrapper is still CPU hog.
Not so big problem on my machine.

Flash player itself runs lot nicer.
In 64bit just install it by using nspluginwrapper as sudo/root.
nspluginwrapper -l
lists your installed plugins
-r removes
-i installs new one. Use /full/path/to/libflashplayer.so

---

### Post by Zorael on 2008-05-15
...

Lack of 64-bit support. It's enough to pop a vein.
[quote=Adobe]"Adobe is not currently providing a 64-bit version of Flash Player 10." On the bright side he went on to say, "we will evaluate that requirement, which has been requested before, for inclusion in possible future releases based on customer demand."[/quote]
I don't get it. Are they hoping 64-bit installations are a fad that'll eventually fade away?

And that "bright side" note can be basically boiled down to "lawl, this way we haven't made any promises *and* you can't call us out on it either, since we're '*evaluating* it'."

---

### Post by FuturePilot on 2008-05-15
> **Zorael said:**
> ...

Lack of 64-bit support. It's enough to pop a vein.

I don't get it. Are they hoping 64-bit installations are a fad that'll eventually fade away?

And that "bright side" note can be basically boiled down to "lawl, this way we haven't made any promises *and* you can't call us out on it either, since we're '*evaluating* it'."

I believe by no means that 64bit is a fad. 64bit is the future. 32bit will become obsolete one day. It's people like Adobe and the computer stores who sell 64bit computers with 32bit OSs on them that are slowing things down.

---

### Post by sloggerkhan on 2008-05-15
I think the issue with compiz has more to do with the DRI problem than anything to do with adobe in particular.

---

### Post by FuturePilot on 2008-05-15
DRI problem? :confused:

---

### Post by Kosimo on 2008-05-15
Guys... I'm still on my way to installing it... Unsuccessfully :( 

I tried almost everything: Moving the plugin flash.so inside /home/.Mozilla/Plugins,    /etc/lib/Firefox/Plugins...  But doesn't works?

Can anybody please tell me how can I install this new beta on Hardy?

Thanks!

---

### Post by Xbehave on 2008-05-15
> **Kosimo said:**
> Can someone make a SIMPLE how to, and so I'll edit the first post to help everybody to test this new release?

Thank you guys

1) download it from the website (preferably to /tmp
2) tar -xf flashplayer10_install_linux_051508.tar.gz    
3) cd install_flash_player_10_linux/
4a)to install to your user account run ./flashplayer-installer
4b)to install as root, afaik the installer wont work so uninstal flash (if it was installed manually sudo rm /usr/lib/mozilla/plugins/flashplayer.so
5b)sudo cp ./flashplayer.so /usr/lib/mozilla/plugins/
6) restart firefox

or as code (user)
```
cd /tmp/
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz 
tar -xf flashplayer10_install_linux_051508.tar.gz
./install_flash_player_10_linux/flashplayer-installer

```
(everybody)
```

cd /tmp/
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz 
tar -xf flashplayer10_install_linux_051508.tar.gz
sudo rm /usr/lib/mozilla/plugins/flashplayer.so
sudo cp ./install_flash_player_10_linux/flashplayer.so /usr/lib/mozilla/plugins/ 
```

---

### Post by vasilis34 on 2008-05-15
Thx qazwsx! I didn't see any big difference from the previous version. Maybe it's a bit less cpu consuming and I think firefox responds a bit faster on sites with a lot of flash ads, but nothing to be impressed. Despite that it's pretty much the same including video quality.
I am really looking forward to the day that flash in linux will have the same quality as in windows. I can't say though that I am very optimistic about it :(.

---

### Post by FuturePilot on 2008-05-15
If you have the flashplugin-nonfree package installed, remove it. Extract the libflashplayer.so from the tar.gz archive and move it to /etc/alternatives
```
sudo mv path/to/flash/libflashplayer.so /etc/alternatives
```
Then link it into /usr/lib/xulrunner-addons/plugins/
```
sudo ln -s /etc/alternatives/libflashplayer.so /usr/lib/xulrunner-addons/plugins/
```
Just remember that if you decide to go back to version 9 to remove libflashplayer.so from /etc/alternatives and remove the link from /usr/lib/xulrunner-addons/plugins

---

### Post by SunnyRabbiera on 2008-05-15
Me I wont be using it till its out of beta...

---

### Post by scottmuz on 2008-05-15
This is definately an improvement. My daughter uses a web site 
EducationCity.com which has lots of flash games. Flash 9 on my 
my 6 year old PC couldn't cope with many of the games. My CPU was maxing
out. Just tried a few
of the most CPU intensive games with the Flash 10 beta and it is definately and improvement.

---

### Post by Curtisc on 2008-05-15
Seems to be a bit better - I get ~30% CPU instead of 50% when watching videos.  Still can't do the on-the-fly resizing at break.com, but I'm glad to see things are getting better.

vasilis34 - unless you really like flash ads, check out the flashblock extension.  It prevents any flash from running unless you explicitly tell it to.

---

### Post by HumanAnarchist on 2008-05-15
Got it working on my 64 bit Hardy, but I'm dissapointed of no video for linux 2 support (vl2) with webcams That sucks for sites like [www.stickam.com](www.stickam.com)

---

### Post by swoll1980 on 2008-05-15
> **soxs said:**
> Unless adobe will produce a 64bit version, it makes no diffrence for me at all.
For installing, well, adobe says you must first delete any old flashplugin before installing, but how to install.. I have no clue. I guess copying would be fine, but in that case you will have to know _where_ to copy those files (I do not know).

Edit: No, adobe will not open flasplyer source, but flash documentation.

[www.phoronix.com](www.phoronix.com)

unpack it and put the .so in /usr/lib/firefox-addons/plugins you will have to use sudo and the mv command or gksu nautilus

---

### Post by madjr on 2008-05-15
ok so we report these bugs or stick with the ones already reported?

see my sign

---

### Post by cdean on 2008-05-15
> **HumanAnarchist said:**
> Got it working on my 64 bit Hardy, but I'm dissapointed of no video for linux 2 support (vl2) with webcams That sucks for sites like [www.stickam.com](www.stickam.com)

Could you give a step-by-step of what you did to get it working? I seem to be unable to get it working.

---

### Post by ubuntu-freak on 2008-05-15
> **FuturePilot said:**
> Why won't the hardware acceleration work with Compiz? I hope they fix that seeing how popular Compiz is.

 
Yes, that makes no sense to me. Composite is OpenGL accelerated.
 
Nathan

---

### Post by Half-Left on 2008-05-15
> **FuturePilot said:**
> Why won't the hardware acceleration work with Compiz? I hope they fix that seeing how popular Compiz is.



*sigh* I wonder if they will ever fix that.....

It does, thats why the screen redirect option is on by default now.

---

### Post by FuturePilot on 2008-05-15
> **Half-Left said:**
> It does, thats why the screen redirect option is on by default now.

Not according to Adobe
> For Linux, the hardware acceleration feature will not work if you are using a compositing window manager (compits).  In this case, Flash Player 10 Beta will always fall back to software.  If you would like to test Flash Player 10 Beta on Linux, please disable your compositing window manager.
[http://labs.adobe.com/technologies/flashplayer10/releasenotes.html#known]("http://labs.adobe.com/technologies/flashplayer10/releasenotes.html#known")

---

### Post by oedipuss on 2008-05-15
> 
compits


compits ?? :lol:

Also, am I the only one who thinks it's annoying how they mention ubuntu by name, and still provide no deb ? It makes no sense.

---

### Post by cdean on 2008-05-15
I wrote a quick mini-HOWTO on my blog when I got it working.

[http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/](http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/)

All I had to do--and, mind you, I'm on amd64--was copy the packaged libflashplayer.so to /usr/lib/flashplugin-nonfree and run **sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so**.

---

### Post by HumanAnarchist on 2008-05-15
> **cdean said:**
> Could you give a step-by-step of what you did to get it working? I seem to be unable to get it working.

```

locate libflashplayer.so
cd /usr/lib/flashplugin-nonfree/
sudo mv libflashplayer.so libflashplayer.so.9
sudo mv /home/fredrik/libflashplayer.so .

```

Restart firefox3 and it was working :)

---

### Post by alessandro_ufms on 2008-05-15
I've been installed this new version and the keyboard in flash games stop working.

---

### Post by mister_k81 on 2008-05-16
> **cdean said:**
> I wrote a quick mini-HOWTO on my blog when I got it working.

[http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/](http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/)

All I had to do--and, mind you, I'm on amd64--was copy the packaged libflashplayer.so to /usr/lib/flashplugin-nonfree and run **sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so**.

Thanks. I followed your how to and got it working just fine. There is definitely an improvement over how much CPU it uses. On my older machine, Firefox 3 beta 5 usually hovers at 10-15% while  viewing web pages and then spikes up to 90% running any video on Youtube. Which is horrible, especially compared to the performance that flash on Windows gets on this same PC. 

The Flash player 10 beta has improved things a bit, now it runs at about 65-70% CPU usage on Youtube. It did crash on me once however...

---

### Post by ELD on 2008-05-16
Well hopefuly this will get the pulseaudio devs to hurry up a bit with fixing whatever the problem with audio crashing with flash.

---

### Post by k99goran on 2008-05-16
Nice. Flash doesn't crash anymore when I view videos. :)

---

### Post by Colonel Kilkenny on 2008-05-16
> **ELD said:**
> Well hopefuly this will get the pulseaudio devs to hurry up a bit with fixing whatever the problem with audio crashing with flash.

Is it even sure that the problem is in Pulseaudio? At least Opera isn't affected... I don't know what's the situation with Konqueror.

edit. The plugin crashes every now and then with Opera, maybe that's pulseaudios fault...

---

### Post by cbudden on 2008-05-16
Does anyone know a way to spoof the version number of the new flash player.  Some parts of the bbc website ([http://news.bbc.co.uk/1/hi/business/7404085.stm](http://news.bbc.co.uk/1/hi/business/7404085.stm)) where there is embedded video won't play because it doesn't think that the new version is supported.

---

### Post by damoxc on 2008-05-16
I compiled the latest libflashsupport from git this morning and stuck it in my ppa. Seems to have reduced the crashes (don't think I've had one yet and I did some heavy youtube browsing as a test).

```
deb http://ppa.launchpad.net/damoxc/ubuntu hardy main
deb-src http://ppa.launchpad.net/damoxc/ubuntu hardy main
```

---

### Post by priyank_bolia on 2008-05-16
I tried to install the adobe flash player and faced the same problem, so I wrote some instructions on how to install at:
[http://priyank.co.in/readarticle.php?article_id=21]("http://priyank.co.in/readarticle.php?article_id=21")

---

### Post by schtufbox on 2008-05-16
> **damoxc said:**
> I compiled the latest libflashsupport from git this morning and stuck it in my ppa. Seems to have reduced the crashes (don't think I've had one yet and I did some heavy youtube browsing as a test).

```
deb http://ppa.launchpad.net/damoxc/ubuntu hardy main
deb-src http://ppa.launchpad.net/damoxc/ubuntu hardy main
```
works fine without libflashsupport here

---

### Post by CarpKing on 2008-05-16
> **reassuringlyoffensive said:**
> Yes, that makes no sense to me. Composite is OpenGL accelerated.
 
Nathan

Hardware acceleration uses DRI, which can causes flickering and other strangeness with composite (due to not being redirected).  This varies by card and driver and will be fixed with DRI2.  

It seems that Adobe has opted to disable hardware acceleration in the presence of Compiz in order to avoid this.

---

### Post by damoxc on 2008-05-16
> **schtufbox said:**
> works fine without libflashsupport here

Try playing music through rhythmbox/banshee, and then try and get sound out of it. it didn't work for me at least, which ever one stated first would block the soundcard. And with libflashsupport it was very unstable (hence why it was removed from hardy).

---

### Post by miguelitu on 2008-05-17
> **cdean said:**
> I wrote a quick mini-HOWTO on my blog when I got it working.

[http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/](http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/)

All I had to do--and, mind you, I'm on amd64--was copy the packaged libflashplayer.so to /usr/lib/flashplugin-nonfree and run **sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so**.

thnaks!

just followed your howto on my hardy 64

for now, it seems like a improvement to me

---

### Post by mech7 on 2008-05-17
Mmmm just tested it why did they still not fix the wmode transparent... grrrr:mad:

---

### Post by odinfromvalhalla on 2008-05-17
> **mech7 said:**
> does wmode transparant finally works ?

Wmode seems to finally work.

i wrote a small step by step tutorial on [how to install flash player 10 on ubuntu using nspluginwrapper]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

URL: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

---

### Post by FuturePilot on 2008-05-17
> **odinfromvalhalla said:**
> Wmode seems to finally work.

i wrote a small step by step tutorial on [how to install flash player 10 on ubuntu using nspluginwrapper]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

URL: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

Not for me it doesn't. :confused:

---

### Post by mech7 on 2008-05-18
yeah for me it doesn't work either :confused:

---

### Post by odinfromvalhalla on 2008-05-18
I have got it wrong last evening. Wmode DOES NOT WORK :(

here is a trick that sorts the wmode issue in linux (for web developers at least:P) [http://blog.marcoos.com/2006/07/21/html-div-above-a-flash-animation-on-linux-its-possible/](http://blog.marcoos.com/2006/07/21/html-div-above-a-flash-animation-on-linux-its-possible/)

---

### Post by schtufbox on 2008-05-18
> **CarpKing said:**
> Hardware acceleration uses DRI, which can causes flickering and other strangeness with composite (due to not being redirected).  This varies by card and driver and will be fixed with DRI2.  

It seems that Adobe has opted to disable hardware acceleration in the presence of Compiz in order to avoid this.

I tried an experiment. i did metacity --replace in terminal  then started firefox, went to youtube, clicked on a video. Then I typed compiz --replace  and then made the youtube vid fullscreen.
It worked perfectly with no dropped frames unlike normal ..so I guess the nVidia drivers aren't affected by flickering.  I wonder if there is some way to prevent flashplayer from detecting compiz? It obviously only detects it if it's active when flash starts, as my little test proves. If there was some way to disable it checking for compiz I'd be happy :D

---

### Post by mrgnash on 2008-05-18
> **cdean said:**
> I wrote a quick mini-HOWTO on my blog when I got it working.

[http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/](http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/)

All I had to do--and, mind you, I'm on amd64--was copy the packaged libflashplayer.so to /usr/lib/flashplugin-nonfree and run **sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so**.

I followed this tutorial and it worked perfectly for me (AMD64).

---

### Post by mech7 on 2008-05-18
> **odinfromvalhalla said:**
> I have got it wrong last evening. Wmode DOES NOT WORK :(

here is a trick that sorts the wmode issue in linux (for web developers at least:P) [http://blog.marcoos.com/2006/07/21/html-div-above-a-flash-animation-on-linux-its-possible/](http://blog.marcoos.com/2006/07/21/html-div-above-a-flash-animation-on-linux-its-possible/)


awwwww :( its a pretty ugly hack.. iframes, javascript :(

---

### Post by bash on 2008-07-03
Adobe has just released a new beta of their Flashplayer 10. This one actually contains some rather nice new features: Namely Wmode and V4L2 support. Sadely there's still no 64-bit support.

Read the announcement here (spiked with quite a bit of sarcasm):

[http://blogs.adobe.com/penguin.swf/2008/07/turkish_localization_also_wmod_1.html](http://blogs.adobe.com/penguin.swf/2008/07/turkish_localization_also_wmod_1.html)

Grab the Beta here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by mech7 on 2008-07-03
:guitar:WMODE Finally... i thought it would never come :D

---

### Post by Kosimo on 2008-07-03
There is a new Beta version that has been released today!

Get it here! [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by Colonel Kilkenny on 2008-07-03
> **mech7 said:**
> :guitar:WMODE Finally... i thought it would never come :D

Too bad it's totally broken :)

Okay, it works in 32bit Firefox but 64bit is apparently totally broken.
In Opera 64bit it kind of works, no idea about 32bit Opera.

---

### Post by ELD on 2008-07-03
> **Kosimo said:**
> There is a new Beta version that has been released today!

Get it here! [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Good news, anyone got a guide on how to properly install it?

---

### Post by Kosimo on 2008-07-03
> **ELD said:**
> Good news, anyone got a guide on how to properly install it?

Follow the first post instructions on this thread.

---

### Post by robertchahine on 2008-07-03
> **ELD said:**
> Good news, anyone got a guide on how to properly install it?
simply extract the .tar.gz package, then press Alt+F2, browse for the file extracted, and run it in terminal.This will install the plugin

---

### Post by LaRoza on 2008-07-03
Working fine in Opera 9.50 so far...

---

### Post by vishzilla on 2008-07-03
i tried it. some flash content were flickering a lot. probably wait for the final release

---

### Post by robertchahine on 2008-07-03
or i think you can download the .RPM package, and transform it to debian (.deb) with the alian command in the terminal then you could install it properly

---

### Post by LaRoza on 2008-07-03
> **robertchahine said:**
> or i think you can download the .RPM package, and transform it to debian (.deb) with the alian command in the terminal then you could install it properly

It really isn't hard, it is a single file moved to a single directory.

---

### Post by ELD on 2008-07-03
Yeah i figured that out when i downloaded the package haha.

Although the installer said this:
> 
NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


?

---

### Post by mech7 on 2008-07-03
> **Colonel Kilkenny said:**
> Too bad it's totally broken :)

Okay, it works in 32bit Firefox but 64bit is apparently totally broken.
In Opera 64bit it kind of works, no idea about 32bit Opera.

Well it's not that big a deal yet.. 64 bit applications are good because you can assign more then 4 GB of ram to it... but for a browser it's a bit of an overkill :)

---

### Post by Colonel Kilkenny on 2008-07-03
> **mech7 said:**
> Well it's not that big a deal yet.. 64 bit applications are good because you can assign more then 4 GB of ram to it... but for a browser it's a bit of an overkill :)

Try telling that to a person who installs 64-bit OS because his/her system is 64bit and cannot get flash to work. 
For a "normal" user, that's instant byebye Ubuntu. :)

---

### Post by mech7 on 2008-07-03
> **Colonel Kilkenny said:**
> Try telling that to a person who installs 64-bit OS because his/her system is 64bit and cannot get flash to work. 
For a "normal" user, that's instant byebye Ubuntu. :)

Well... with ubuntu i only tried 32 bit to be honest.. with XP i run x64 and 32 bit software runs normally on it... is this different with ubuntu ?

---

### Post by geoken on 2008-07-03
> **Colonel Kilkenny said:**
> Try telling that to a person who installs 64-bit OS because his/her system is 64bit and cannot get flash to work. 
For a "normal" user, that's instant byebye Ubuntu. :)

If you're going to appeal to a "normal" user, you should make it easier to install 32bit apps. For example, Vista 64 runs a 32 bit Windows Media Player to ensure full codec compatibility.

---

### Post by LaRoza on 2008-07-03
> **geoken said:**
> If you're going to appeal to a "normal" user, you should make it easier to install 32bit apps. For example, Vista 64 runs a 32 bit Windows Media Player to ensure full codec compatibility.

They do. Adobe doesn't.

---

### Post by loell on 2008-07-03
heh, no need for flashcam for v4l2 webcam users! :guitar:

---

### Post by mech7 on 2008-07-03
> **LaRoza said:**
> They do. Adobe doesn't.

Adobe does.. as flash runs fine in 32 bit browser.. no Quicktime that is a **** in 64 bit on windows :(

---

### Post by cdean on 2008-07-03
I've got a [Flash mini-howto up on my blog](http://cad.cx/blog/2008/05/15/adobe-releases-flash-10-beta-for-windows-mac-os-x-and-linux/).

It goes like this:

Extract the archive and **cd** into the directory into which you extracted it.
**sudo cp libflashplayer.so /usr/lib/flashplugin-nonfree** if you want it for all users on the system
**cp libflashplayer.so ~/.mozilla/plugins** if you want it for just your user or you don't have root access

That's it, unless you're a 64-bit user such as myself, in which case you need to run **sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so**

Sorry, folks, there's not a way to do it graphically, unless you hit alt+f2 and do **gksudo nautilus /usr/lib/flashplugin-nonfree** and drop libflashplayer.so into that, then do the above command for 64-bit users, replacing sudo with gksudo.

---

### Post by PRGUY85 on 2008-07-03
Everything works fine except ESPN.com which runs extremely slow now.

---

### Post by zachtib on 2008-07-03
Is hardware acceleration with Compiz enabled supported yet?

---

### Post by FuturePilot on 2008-07-03
WMode Transparency! :o

Finally after all these **years** :|

---

### Post by spanella47 on 2008-07-03
i'm using a ppa version but it removes libflashsupport which solves the audio problems with pulse audio. So of course if i start flash now while some other audio program is open, there's no audio in flash. Otherwise audio works fine.

is anyone else having trouble with audio?

---

### Post by ubuntu-freak on 2008-07-03
For any 32/64-bit Hardy Heron users who are still having problems installing the beta, here is an extract from my how-to:



**[COLOR="DarkRed"]UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY[/COLOR]**

**[COLOR="DarkRed"]Note:[/COLOR]** You can safely install the Ubuntu package (flashplugin-nonfree) over the top of this manual installation method at a later date, I've tested it several times. The method used below will install the plugin into the same directory the Ubuntu package does, with the same symlinks and can be overwritten cleanly.

Install the Flash plugin manually by downloading the tar archive of [Adobe Flash Player v10 beta](http://labs.adobe.com/downloads/flashplayer10.html). Simply open the tar archive, then find the file named "libflashplayer.so and place it on your desktop. Next, execute this command in the terminal:

**[COLOR="DarkRed"]32-Bit Ubuntu Family Users Only:[/COLOR]**

**[COLOR="DarkRed"]Edit:[/COLOR]** If you don't have the Ubuntu package installed, skip the first command and perhaps the "sudo mkdir" command as well:

**sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so**

You may now restart your web browser and use the plugin.

**[COLOR="DarkRed"]64-Bit Ubuntu Family Users Only:[/COLOR]**

**[COLOR="DarkRed"]Edit:[/COLOR]** If you don't have the Ubuntu package installed, skip the first command and perhaps the "sudo mkdir" command as well:

**sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so && sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so && sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so**

You may now restart your web browser and use the plugin.

---

### Post by SilverDragon on 2008-07-03
Thanks for the guide reassuringlyoffensive.

How would I check to see what version of flash I have installed? For example, to get an output like this?

```

Shockwave Flash

File name: libflashplayer.so
Shockwave Flash 10.0 b218

MIME Type Description Suffixes Enabled
application/x-shockwave-flash Shockwave Flash swf Yes
application/futuresplash FutureSplash Player spl Yes 
```

I didn't see anything when I went to about: plugins within Firefox. (I spaced : plugins, because it made a smiley face and I'm not sure how to disable it)

---

### Post by ubuntu-freak on 2008-07-03
> **SilverDragon said:**
> Thanks for the guide reassuringlyoffensive.

How would I check to see what version of flash I have installed? For example, to get an output like this?

```

Shockwave Flash

File name: libflashplayer.so
Shockwave Flash 10.0 b218

MIME Type Description Suffixes Enabled
application/x-shockwave-flash Shockwave Flash swf Yes
application/futuresplash FutureSplash Player spl Yes 
```

I didn't see anything when I went to about: plugins within Firefox. (I spaced : plugins, because it made a smiley face and I'm not sure how to disable it)

 
Thanks, you're welcome.
 
I'm not sure to be honest, never tried it. I do know that right-clicking on Flash content let's you check which version you have though.
 
P.S. To stop the emoticon appearing, enclose it with [no parse][/noparse]

---

### Post by mister_k81 on 2008-07-03
The latest Beta runs a lot worse than Beta 1 did for me. It seems to be even more CPU intensive than Flash 9. :???:
 
 Does anybody know where I can still find the first Beta? I made the mistake of not backing it up before I overwrote it with Beta 2. Adobe Labs doesn't have it on their site anymore.

---

### Post by spanella47 on 2008-07-03
theres a PPA that has Beta 1 still
[https://launchpad.net/~gnomefreak/+archive](https://launchpad.net/~gnomefreak/+archive)

---

### Post by mrgnash on 2008-07-03
It seems to crash/bug-out a whole lot less than the first beta, but I am experiencing video tearing which is something I've never encountered before with Flash (although I am aware that many other people have).

---

### Post by keiichidono on 2008-07-03
> **spanella47 said:**
> i'm using a ppa version but it removes libflashsupport which solves the audio problems with pulse audio. So of course if i start flash now while some other audio program is open, there's no audio in flash. Otherwise audio works fine.

is anyone else having trouble with audio?
I have that same problem, it's not too big for me though but it's still kind of a problem. =\
> **mrgnash said:**
> It seems to crash/bug-out a whole lot less than the first beta, but I am experiencing video tearing which is something I've never encountered before with Flash (although I am aware that many other people have).
Welcome to the world, I've always experienced tearing, even in Flash 9. Seems to be a lot better in Flash 10 now though.

---

### Post by mister_k81 on 2008-07-04
> **spanella47 said:**
> theres a PPA that has Beta 1 still
[https://launchpad.net/~gnomefreak/+archive](https://launchpad.net/~gnomefreak/+archive)

Thanks :)

---

### Post by mister_k81 on 2008-07-05
> **mister_k81 said:**
> Thanks :)

Ok, Maybe I spoke a little too soon here when I wrote this. :???: I didn't get a change to check out the link until now, and I'm not sure what I am suppose to do here. I downloaded the flashplugin-nonfree_10.0.1.218ubuntu1~8.04~mt_i386.deb file, and it seems to give me a dependency error. Am I downloading the right one? :S

Nevermind, I found beta 1 here: [http://repo.fedoramd.org/3rdparty/?C=N;O=D](http://repo.fedoramd.org/3rdparty/?C=N;O=D) . But thanks anyway.

---

### Post by spanella47 on 2008-07-05
> **mister_k81 said:**
> Ok, Maybe I spoke a little too soon here when I wrote this. :???: I didn't get a change to check out the link until now, and I'm not sure what I am suppose to do here. I downloaded the flashplugin-nonfree_10.0.1.218ubuntu1~8.04~mt_i386.deb file, and it seems to give me a dependency error. Am I downloading the right one? :S

I think the PPA has other packages that it depends on. you'd have to add it to your sources to get the dependencies or figure out and install each one separately. He's also fixed libflashsupport to work with flash 10 giving proper audio. He hasn't updated to Beta 2 yet, but i assume he'll be keeping up with releases as flash 10 develops.

---

### Post by mister_k81 on 2008-07-05
^ OK, I get it now.  I just have to add the following links on the site to the repo sources.list. Even though I don't really need the flash 10 beta from there anymore, thanks for explaining it to me, spanella47.

---

### Post by Kosimo on 2008-08-21
Hey guys, :lolflag:the RC is out...
I'm gonna try now!

---

### Post by gwenn on 2008-08-21
> **Swarms said:**
> 64 bit version pretty please!

There is and running very well!
In the repos'.

---

### Post by FuturePilot on 2008-08-21
> **gwenn said:**
> There is and running very well!
In the repos'.

There is no 64bit version. The one for 64bit in the repos is just the 32bit one, but it uses nspluginwrapper as sort of a compatibility layer. As of now there is no native 64bit version.

---

### Post by racoq on 2008-08-21
> **Kosimo said:**
> Hey guys, :lolflag:the RC is out...
I'm gonna try now!

Good Luck...

I tried it on XUbuntu without success.

Someone made a guide here, although it not worked for me, it may work for someone:

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

---

### Post by Hells_Dark on 2008-08-25
[billou made a deb](http://forum.ubuntu-fr.org/viewtopic.php?id=247129) :

[quote=billou]```
sudo apt-get remove flashplugin-nonfree --purge
sudo apt-get remove libflashsupport --purge
```
[http://nunux-fr.org/files/Adobe-Flash-player-10.0.d569-Hardy.deb](http://nunux-fr.org/files/Adobe-Flash-player-10.0.d569-Hardy.deb)[/quote]

Works well here :)

---

### Post by coolbrook on 2008-08-25
This is good news.  My bug is fixed. :cool:

edit:  Spoke too soon.  Sound stopped working.

---

### Post by Kosimo on 2008-08-27
This totally s****s   In my case Flash Player 10 is stil crashing my Firefox every time that is hardly used.....

Back on 9 :(

---

### Post by z0mbie on 2008-08-27
RC 10 works a lot better, in the sense it doesn't crash Firefox.

---

### Post by Finger78 on 2008-08-28
Any fixes of possible solutions to the Flash 10 crashing Firefox? If not could someone post a how-to on removing 10 (I used Adobe-Flash-player-10.0.d569-Hardy.deb to install it) this and installing 9?

I am completely new to Linux so I need every detail please.

---

### Post by Morty007 on 2008-08-31
I've installed the latest beta and although youtube is fine, metacafe uses up about 50% of my cpu cycles, and I can't view cnn videos at all.

---

### Post by Kosimo on 2008-09-15
Hello.
Today Adobe introduced a new Release candidate called "Astro" 10.0.12.10 witch has many bugfixes.  

This is the changelog:

>     *  Many Linux camera issues have been fixed. Please report any additional issues you encounter.
    * Linux full-screen optimizations have been made. Please report any additional issues you encounter.
    * startDrag() does not work when movie clip is 3D. (216415)
    * LiveCycle WorkSpace cannot log in using Flash Player 10 Beta. (223394) WORKAROUND: Use Flash Player 9.0.124.0.
    * Vector printing on Macs works now!
    * New Text Engine: Vector Printing isn't currently enabled.
    * Custom Filters and Effects:
          o Mac PPC: Color distortions may appear when applying a Shader. ShaderJob returns unexpected values for some Pixel Bender functions.
          o Linux: Shader Jobs may return NaN instead of an expected Number value.
    * Drawing API: Strokes are not visible on paths drawn with drawTriangles or GraphicsTrianglePaths.  The lineShaderStyle is not implemented in Flash Player 10 Beta.
    * Context Menu: The new AS3 Clipboard is currently only working for Mac and Windows. It is not yet working for the Unix players.
    * Uploading images using Photoshop Express does not work with Flash Player 10 Beta.  (1786882)  WORKAROUND: Use Flash Player 9.0.124.0.
    * Dynamic Streaming:
          o A crash when switching between videos of different resolutions has been fixed.
          o A new Play Status event when switching between streams now actually happens: NetStream.Play.TransitionComplete.
    * RTMFP:
          o Changing NetStream.BufferTime on the subscriber side of P2P connection, causes video to stop and possible crash
          o No NetStream onStatus messages received when using NetStream.pause(), NetStream.resume() or NetStream.togglePause() for P2P connection
          o Intermittent crashes/hangs when subscribing/unsubscribing multiple times to P2P NetStream.
          o peerStreams array includes null streams in some cases.
    * Speex:
          o Disconnect and re-connect network on Mac publisher causes sending garbled audio with USB audio devices. (227185)
          o Speex audio may deteriorate when computer is overloaded. (222082)
          o Peer-to-peer Nellymoser may incur in quality degradation when packets are lost. (222469)
          o Soundtransform for Speex does not work in loopback mode
          o Linux-specific issues:
                + Flash Player 10 hangs when subscribing to a live audio stream.  (222283)
                + Linux subscriber receives deteriorated audio for about 20 seconds when switching from Nellymoser to Speex codec. (222306)
                + Linux Subscriber P2P only: When Nellymoser audio is attached, the video plays slowly on the subscriber side. (222851)
    * Video playback issues on PPC Macs have been resolved.


Particularly interesting the point "Linux full screen performance improvements. Everybody knows how bad performance we had 'till now when using full screen videos & apps.


Here the link to download the latest version:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by kef_kf on 2008-09-15
> **Kosimo said:**
> Hello.
Today Adobe introduced a new Release candidate called "Astro" 10.0.12.10 witch corrects many bugfixes.  


thanks for the heads up

---

### Post by Morty007 on 2008-09-15
Can someone post how to install it? I'm a noob.

---

### Post by qazwsx on 2008-09-15
White screen in 64bit Konqueror ](*,)  ](*,) Yes I updated my nspluginwrapper configuration.

Usable Gnash I am waiting for you...

---

### Post by billgoldberg on 2008-09-15
Thanks for mentioning it.

I have instructions on my blog should someone need help installing it.

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

---

### Post by gardara on 2008-09-15
> **Morty007 said:**
> Can someone post how to install it? I'm a noob.


Check the first post of this thread :)

---

### Post by Npl on 2008-09-15
> **gardara said:**
> Check the first post of this thread :)At least for me this wasnt enough on 64-bit Linux as the Release-Candidate has more depencies than the previous betas. I had to manually install some 32-bit libs.

This is how to get it working in Opera:

Download the [flashplayer.tgz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz"), unpack the libflashplayer.so file to your working directory, then move it to the right directory.
```
sudo install -d /usr/lib/flashplugin-nonfree
sudo install -T -m 644 ./libflashplayer.so /usr/lib/flashplugin-nonfree/libflashplayer.so
```

Install [Getlibs]("http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb"). Make sure you have the necessary **32bit Libraries** installed
```
sudo apt-get install ia32-libs

getlibs -p libcurl3 -p libnss3-1d -p libnss3-0d -p libnspr4-0d
```


If you use other browser you additionally need to mess around with ndiswrapper or however that bloody thing is called.

---

### Post by Morty007 on 2008-09-15
Yay, got it installed. Thanks to Bill. I was hoping in would solve my high cpu use when I go to this ebay page [http://cgi.ebay.com/NEW-WII-GAME-CONSOLE-SYSTEM-PLAY-MARIO-KART-2-WHEEL-FIT_W0QQitemZ130254517270QQcmdZViewItem?hash=item130254517270&_trkparms=72%3A1163|39%3A1|66%3A2|65%3A12|240%3A1308&_trksid=p3911.c0.m14](http://cgi.ebay.com/NEW-WII-GAME-CONSOLE-SYSTEM-PLAY-MARIO-KART-2-WHEEL-FIT_W0QQitemZ130254517270QQcmdZViewItem?hash=item130254517270&_trkparms=72%3A1163|39%3A1|66%3A2|65%3A12|240%3A1308&_trksid=p3911.c0.m14)

but no luck. Whenever I scroll down to the green flash content it shoots up sky high.

---

### Post by mister_k81 on 2008-09-15
Well, so far so good. The first Release candidate kept seg-faulting like mad, and the beta before that was a CPU hog. The only luck I've had up to this point was with the first Flash 10 beta that came out back in May, and I have been using that since. 

I haven't noticed any issues with this one yet, it seems to be working pretty well :) . I also noticed that my CPU usage on many flash sites have improved somewhat.

---

### Post by redseventyseven on 2008-09-16
Oh dear, I seem to have a bit of a problem!

I had the older release candidate installed and working fine on my (32-bit) system, and uninstalled it to put on the new one. I followed the instructions on the Adobe website - [http://labs.adobe.com/technologies/flashplayer10/releasenotes.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html#install) - and it didn't work. Then I followed Bill Goldberg's instructions - [http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/) -(which I'd used to install the earlier RC) to the letter, and still it didn't work. Youtube still tells me I don't have flash player installed, for instance.

A few more details: The flashplayer.so appears in the ~/.mozilla/plugins directory. So no apparent problems there. The symlinks are all set up correctly (as per Bill Goldberg's instructions). I use Linux Mint rather than Ubuntu - is that likely to cause problems?

I'm leaving this for now because I have to go and work instead of fiddling with this - but if anyone has any advice they could share before I come back to this I'd be very grateful!

---

### Post by wroobel on 2008-09-16
redseventyseven, I have the same problem with my Kubuntu 8.04.

edit: OK. I found solution. This build needs 3 another libs, so I made 3 new symlinks:
```
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
```
It work for me now.

---

### Post by redseventyseven on 2008-09-16
Thanks!

I will try this when I get home and let you know if it helps me too.

---

### Post by redseventyseven on 2008-09-16
I can confirm that these extra symlinks have done the trick. Thanks!

---

### Post by Morty007 on 2008-09-16
So are these:

```
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
```


in additon to these:

```
sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so 
```   ?

I'm following whats on this page [http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

---

### Post by billgoldberg on 2008-09-17
> **Morty007 said:**
> So are these:

```
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
```


in additon to these:

```
sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so 
```   ?

I'm following whats on this page [http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

Yes.

I'll add them to the site also. 

--

I didn't had to use those simlinks to get the new one working, just to let you know.

---

### Post by loopeando on 2008-09-17
I followed the instructions given [here]("http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/") but it's not working correctly.

For example flash overlaps or doesn't load correctly.

Anyone else with this issue?

---

### Post by Morty007 on 2008-09-17
Can Bill or someone help me? I still get crashes, but maybe I didn't do it right. I manually deleted the .so file in home/mozilla/plugins.

I then completely removed the flash in synaptic. Here is my output. 

```
marc@marc-desktop ~ $ sudo apt-get remove libflash-mozplugin libflashsupport flashplugin-nonfree
[sudo] password for marc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash-mozplugin is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1 xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marc@marc-desktop ~ $ sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
ln: creating symbolic link `/usr/lib/libssl3.so': File exists
marc@marc-desktop ~ $ sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
ln: creating symbolic link `/usr/lib/libnss3.so': File exists
marc@marc-desktop ~ $ sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
ln: creating symbolic link `/usr/lib/libnspr4.so': File exists
marc@marc-desktop ~ $ sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
ln: creating symbolic link `/usr/lib/libsmime3.so': File exists
marc@marc-desktop ~ $ sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
ln: creating symbolic link `/usr/lib/libplds4.so': File exists
marc@marc-desktop ~ $ sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
ln: creating symbolic link `/usr/lib/libplc4.so': File exists
marc@marc-desktop ~ $ cd /tmp
marc@marc-desktop /tmp $ wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
--16:35:58--  http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
           => `flashplayer10_install_linux_091508.tar.gz'
Resolving download.macromedia.com... 72.247.203.191
Connecting to download.macromedia.com|72.247.203.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,958,529 (3.8M) [application/x-gzip]

100%[====================================>] 3,958,529    575.83K/s    ETA 00:00

16:36:05 (560.33 KB/s) - `flashplayer10_install_linux_091508.tar.gz' saved [3958529/3958529]

marc@marc-desktop /tmp $ tar -zxvf flashplayer10_install_linux_091508.tar.gz
install_flash_player_10_linux/
install_flash_player_10_linux/flashplayer-installer
install_flash_player_10_linux/libflashplayer.so
marc@marc-desktop /tmp $ cd install_flash_player_10_linux
marc@marc-desktop /tmp/install_flash_player_10_linux $ ./flashplayer-installer

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 10 for Linux

Adobe Flash Player 10 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 10 will be installed in your home directory.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 10 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Mozilla installation directory  = /home/marc/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): 


```

---

### Post by Morty007 on 2008-09-19
Is anyone in the wonderful community able to help me sort this out?

---

### Post by Cifra on 2008-09-25
There's a RC out. Must I really compile the source or is there a .deb for ubuntu?

---

### Post by mikewhatever on 2008-09-25
> **Cifra said:**
> There's a RC out. Must I really compile the source or is there a .deb for ubuntu?

No, don't think there is a deb, but, since tar.gz package is a binary, you don't need to compile it. Download the package, unpack it, cd to the directory and run the installer.

---

### Post by binbash on 2008-09-26
linking does the trick, thanks

---

### Post by Kosimo on 2008-10-15
Guys, final version is out. Check it out here:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)


Have a look to your current version here:

[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

---

### Post by stmiller on 2008-10-15
And Adobe is providing a .deb of the latest flash 10. How about that?

---

### Post by Kosimo on 2008-10-15
> **stmiller said:**
> And Adobe is providing a .deb of the latest flash 10. How about that?

Yes.
Is in the first post. You can download a .deb or use the official apt-get repository to keep using always the latest version.

---

### Post by Swarms on 2008-10-15
Its great how much their support for Ubuntu has grown, I just wish they would support 64 bit anytime soon. :)

---

### Post by lefen on 2008-10-15
> **stmiller said:**
> And Adobe is providing a .deb of the latest flash 10. How about that?

So presumably, you just have to download the deb and install it to automagically remove+replace your current version of flash?

---

### Post by FuturePilot on 2008-10-15
> **lefen said:**
> So presumably, you just have to download the deb and install it to automagically remove+replace your current version of flash?

No. You will have to manually remove the old version first.

---

### Post by Kosimo on 2008-10-15
> **FuturePilot said:**
> No. You will have to manually remove the old version first.

Is not needed. 
Just updated by installing the latest .deb

---

### Post by Morty007 on 2008-10-15
Ok, so is the high cpu usage bug finally gone!?

---

### Post by yabbadabbadont on 2008-10-15
> **Morty007 said:**
> Ok, so is the high cpu usage bug finally gone!?

Not on my machine it isn't...  the intro video on the main flashplayer page pegs my CPU at 99% the entire time it is running.  Ugh.

---

### Post by Morty007 on 2008-10-16
If that's the case then we need to go back on the adobe forums and complain. :mad:

---

### Post by jfg69 on 2008-10-17
CAn someone tell me if this would be the latest version?

```
jfg69@jfg69-desktop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: amd64
Version: 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2

```

What is "really9.0.124"? is it version spoofing?

---

### Post by jocose on 2008-10-17
I tried to update from 9 to 10 using the backports repo, but it appeared to download version 9 when I purged 9 and tried downloading 10, and issuing an "about:plugins" from within Firefox showed version 9.

I purged it, downloaded/installed the version 10 deb from Adobe's site, checked the version number in "about:plugins" again from within Firefox and it now shows version 10.

I see many improvements in version 10, less crashes and less unstable behavior which plagued me on a daily basis in version 9.

---

### Post by billgoldberg on 2008-10-17
I don't know why but flash 10 in Ubuntu Hardy performs much worse then Flash 10 on Intrepid beta.

Although, thinking about it it's most likely the ATI drivers.

---

### Post by Footer on 2008-10-17
Anyone know when Flash Player 10 will be available in the repositories for Hardy?  Is it already in Intrepid?  According to this article, it's been officially released now as of 10/15/08:

[INDENT][http://www.desktoplinux.com/news/NS3225467354.html](http://www.desktoplinux.com/news/NS3225467354.html)[/INDENT]

Thanks.

---

### Post by Sealbhach on 2008-10-17
> **Footer said:**
> Anyone know when Flash Player 10 will be available in the repositories for Hardy?  Is it already in Intrepid?  According to this article, it's been officially released now as of 10/15/08:

[INDENT][http://www.desktoplinux.com/news/NS3225467354.html](http://www.desktoplinux.com/news/NS3225467354.html)[/INDENT]

Thanks.

If you want it now, you can get a deb file from the Adobe website.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

It's for 32 bit only. If you need 64 bit there's an easy way to get it if you look at earlier in this thread.


.

---

### Post by Footer on 2008-10-18
> **Sealbhach said:**
> If you want it now, you can get a deb file from the Adobe website.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

It's for 32 bit only. If you need 64 bit there's an easy way to get it if you look at earlier in this thread.


.

Well, I know I can go get it now from Adobe but that isn't what I'm after.  I was wondering if anyone knows if/when it will be available in the Ubuntu repositories for Hardy and if it is already in the Intrepid beta repositories (I'm not running Intrepid yet but would consider it if Adobe Player Flash 10 is there).  Also, I am running 64 bit and I went back a few pages but really don't want to do manual installs for this.  Version 9 has been working pretty well (I used to get white screens all the time where Flash should be) which is why I'd rather upgrade from repositories now that it's final.

Thanks for the reply!

:)

---

### Post by Sealbhach on 2008-10-18
> **Footer said:**
>  Intrepid yet but would consider it if Adobe Player Flash 10 is there).  Also, I am running 64 bit and I went back a few pages but really don't want to do manual installs for this.  Version 9 has been working pretty well (I used to get white screens all the time where Flash should be) which is why I'd rather upgrade from repositories now that it's final.

Thanks for the reply!

:)

Have a look at this site here. It's very quick and easy - just copy one line into the terminal and press enter.

[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)


It works flawlessly for most people. Obviously, if you're not sure, don't. But I recommend it.



.

---

### Post by chemist109 on 2008-10-18
I'm getting VERY high CPU utilization with the current Flashplayer 10 plugin (.deb obtained from Adobe web site).  Anyone else have this problem?

I'm back to version 9 (sigh) :(

---

### Post by deadite66 on 2008-10-18
disappointed with flash 10, slow fullscreen and high cpu.
shame joost is now flash based and i can't watch fullscreen.

---

### Post by Kosimo on 2008-11-17
Flash Player 10 Alpha for 64 Linux is finally released:


[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)



64 Bit users! Please give it a try and let us know! ;)

---

### Post by odinfromvalhalla on 2008-11-17
I have put together a small tutorial on [how to install the native flash player 10 64bit plugin for linux. ]("http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html")

---

### Post by Toadmund on 2008-11-17
Unfortunately, your tutorial is useless because the commands are obscured by the side menu bar.

One could see it in View->Page source, though.

You should fix that.

---

### Post by Kosimo on 2008-11-18
> **Toadmund said:**
> Unfortunately, your tutorial is useless because the commands are obscured by the side menu bar.

One could see it in View->Page source, though.

You should fix that.

What???? I see them perfectly

---

### Post by odinfromvalhalla on 2008-11-18
i updated the post with a link to the shell script, so that people that have issues with viewing the page can just download and execute the script.

---

