---
title: "Flash 10 is out; Adobe now makes Ubuntu .debs"
date: 2008-10-15
forum: The Cafe
---

### Post by Vadi on 2008-10-15
Yay, Adobe's linux flash download page now offers .debs for Ubuntu: [[img]http://www.ubuntu-pics.de/thumb/4497/screenshot_96_1dT2nI.png[/img]](http://www.ubuntu-pics.de/bild/4497/screenshot_96_1dT2nI.png)

It always bugged me that clueless ubuntu newbies were redirected to a terminal-based script if they had no Flash.

No 64bit version still, but they packed some very impressive features in version 10: [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

[SIZE="5"]Installing Flash 10[/SIZE]

**32bit**: Just save this file and double-click on it to start: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

**64bit**: In the terminal (sorry), paste this code: 

> wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh

([via]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/"))

---

### Post by s.fox on 2008-10-15
Its about time.  I remember all the troubles i had with installing flash...

---

### Post by markp1989 on 2008-10-15
to bad i cannot find a 64bit version on there site

---

### Post by YoungQuiz on 2008-10-15
very niiice

---

### Post by Sealbhach on 2008-10-15
It's coming down at 3.8 Kb/s.

There must be a bit of a scramble to get it!:)


.

---

### Post by Exershio on 2008-10-15
well, it's a step in the right direction for sure. Now we just need to see some reliable x64 flash working and we'll be good to go.

---

### Post by SuperSonic4 on 2008-10-15
How is flash 10 different to flash 9? Since flash 9 works perfectly I am hesistant to uninstall it to upgrade

---

### Post by qazwsx on 2008-10-15
Performance is so much better now.

For 64 bit users tar.gz might better choice ;)

---

### Post by markp1989 on 2008-10-15
> **qazwsx said:**
> Performance is so much better now.

For 64 bit users tar.gz might better choice ;)

the tar.gz doesnt work with 64bit either 

```
mark@markspc:~/Desktop/install_flash_player_10_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

mark@markspc:~/Desktop/install_flash_player_10_linux$ 
```

this is really anoying, i would use flashplugin-nonfree from apt, but it takes 113mb of hd space!



edit: has any one else noticed that the hw requirements on the adobe site are completly different for linux/windows version [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

---

### Post by xpod on 2008-10-15
> this is really anoying, i would use flashplugin-nonfree from apt, but it takes 113mb of hd space!


Surely you have enough space on those HD`s of yours to spare so little?
Or has the torrent slave filled them all up mabey:)

---

### Post by Sealbhach on 2008-10-15
.

---

### Post by paul101 on 2008-10-15
its more fun to install tar.gz 's :razz:

---

### Post by SunnyRabbiera on 2008-10-15
> **SuperSonic4 said:**
> How is flash 10 different to flash 9? Since flash 9 works perfectly I am hesistant to uninstall it to upgrade

Well Flash 10 seems more sturdy and stable then flash 9, it seems faster and it doesnt seem to freeze up firefox.

---

### Post by extruct on 2008-10-15
Yay new flash! Thanks for the news!
Seems like the bug when movies on youtube "lags" in fullscreen gone. Thanks Adobe!

---

### Post by DoDoENT on 2008-10-15
> **Sealbhach said:**
> Normally any 32 bit app will work in 64 bit systems.

You can force it to install:

```
sudo dpkg -i --force architecture install_flash_player_10_linux.deb
```

Well, this doesn't work for me. No flash at all in opera, firefox freezes when opening a site with flash content.

32 bit applications work in 64 bit systems, but 64 bit apps cannot call functions from 32 bit libraries. In our case: firefox (or opera) are 64 bit, and flash is 32 bit.

I've tried with nspluginwrapper but I get this strange error:

```
root@2nd-of-12:/home/dodo/Desktop/install_flash_player_10_linux# nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
*** NSPlugin Viewer  *** ERROR: libnss3.so: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by qazwsx on 2008-10-15
For 64bit
tar.gz might be easier since you have to setup nspluginwrapper for it and as well to test it.

run 
```

nspluginwrapper -l
```

to get list of wrapped plugins + links.

you must remove older libflash paths

```
sudo nspluginwrapper -r "insert path here"
```

install new one

```
sudo nspluginwrapper -i "insert path to libflashplayer.so"
```

[SIZE="4"]You need to use full path!!![/SIZE]

---

### Post by DoDoENT on 2008-10-15
```
/usr/lib/mozilla/plugins/libflashplayer.so
``` looks like a full path to me.

Even more, now after force installing the 32bit deb package, I cannot remove it anymore. apt-get says that it could not find package with that name, it doesn't appear in synaptic, but apt-get install flashplugin-nonfree doesn't work because of package conflict.

---

### Post by Sealbhach on 2008-10-15
> **DoDoENT said:**
> Well, this doesn't work for me. No flash at all in opera, firefox freezes when opening a site with flash content.


Flash didn't work for me after I did that but after I logged out and in again it worked.

Mind you, I did have the beta before this.

This is what it says in about:plugins

```
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12
```

Is that the beta or this new release?


.

---

### Post by cubbybear on 2008-10-15
I just noticed that while in Synaptic it shows the flashplugin-nonfree has the new flash10 version installed, while in Firefox 3's about:plugins still says Shockwave Flash 9.0 r124.  I don't see the older version in Synaptic anymore and Firefox only shows the older version under plugins.  Are both actually installed?  I thought xubuntu-restricted-extras might have also included the older version and wondered if that could have been the discrepency, so I removed that just to check but Firefox still showed the older version.  Has anyone else noticed this?

---

### Post by Sealbhach on 2008-10-15
> **DoDoENT said:**
> ```
/usr/lib/mozilla/plugins/libflashplayer.so
``` looks like a full path to me.

Even more, now after force installing the 32bit deb package, I cannot remove it anymore. apt-get says that it could not find package with that name, it doesn't appear in synaptic, but apt-get install flashplugin-nonfree doesn't work because of package conflict.

Does it find it if you do this:

```
 dpkg -l | grep flash
```

For me it finds:

```
oliver@vaio-laptop:~$ dpkg -l | grep flash
ii  adobe-flashplugin                          10.0.12.36-1hardy1                       Adobe Flash Player plugin version 10
oliver@vaio-laptop:~$ 

```

---

### Post by DoDoENT on 2008-10-15
OK! I've figured out how to remove the package (I should use dpkg instead of apt-get), but installation with nspluginwrapper just doesn't work.

I get this error:
```
root@2nd-of-12:/usr/lib/mozilla/plugins# nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
*** NSPlugin Viewer  *** ERROR: libnss3.so: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

---

### Post by DoDoENT on 2008-10-15
> **Sealbhach said:**
> Flash didn't work for me after I did that but after I logged out and in again it worked.

Mind you, I did have the beta before this.

This is what it says in about:plugins

```
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12
```

Is that the beta or this new release?


.

I've just tried that. No good.

I think I'll have to wait until someone updates the flashplugin-nonfree package in ubuntu repository. :(

---

### Post by qazwsx on 2008-10-15
```
ERROR: libnss3.so
```
So you need to install package
[http://packages.ubuntu.com/hardy/libs/libnss3-1d](http://packages.ubuntu.com/hardy/libs/libnss3-1d)
If tou need it as 32 bit (sorry I have bunch of 32bit libraries installed already) you need extract 32 bit deb archive.

dpkg -x "insert package here"
find that libnss3.so and move it to /lib32

---

### Post by Sealbhach on 2008-10-15
This guy here has a one click install for Flash 10 in 64 bit.

[http://queleimporta.com/en/](http://queleimporta.com/en/)

It can all be done with one command in the terminal using his script. Worked just dandy for me!!!


.

---

### Post by qazwsx on 2008-10-15
That script is better

You need to modify it
lines 33 and 34 should look like this
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
```

```
tar zxvf install_flash_player_10_linux.tar.gz
```

---

### Post by nick09 on 2008-10-15
I'd rather wait for it to be supported in 64 bit, otherwise Flash 9 is working fine for me.

---

### Post by Giant Speck on 2008-10-15
Wow.  Flash 10 is much better than Flash 9.

The first indication of this was launching Pandora radio.  The sound is a lot clearer.

Another indication is on websites that have navigation menus made from Flash, the dropdown menus don't get trapped behind other Flash movies on the website.

---

### Post by vom on 2008-10-15
I cannot get Flash 10 to work.  I did an 'aptitude purge flashplugin-nonfree' and then a 'dpkg -i install_flash_player_10_linux.deb'.

about:\plugins in FF shows nothing.  I checked contents of deb, /etc/alternatives links etc etc.  Everything checks out.

I also tried the .tar.gz manually putting it in the plugins dir, nothing.  

On top of all of this, the file in the .deb from Adobe is a different size than the one in the .tar.gz :(

Can anyone think of anything else that could be happening ?  This is all 32 bit, Hardy etc etc.  I've done my share of messing around with Flash  9 when it was beta - it smells like this plugin .so file is simply bad.  :(

---

### Post by vom on 2008-10-15
I think I figured it out.  I'm running Kubuntu and for whatever reason, there are some libs I dont have (libnss3.so) etc.  Found this out by running ldd on the flashplugin itself.  Now to hunt down libs...

---

### Post by alexcuervo on 2008-10-15
For 64 bit users see *"The easiest way to install Flash 10 on Ubuntu 64 bit"* at [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

---

### Post by Phases on 2008-10-16
Haven't read this whole thread but let me say:

Thank god. I've waited and waited for this since I first started using Ubuntu exclusively 2 months ago. 

This installed quick and easy and fixed the really annoying bug where drop down menus were going behind flash objects. 

I only installed it ten minutes ago but I've been to youtube of course, and my problem sites (ie verizonwireless.com) and so far things are good. 

Phases <-- Happy!

---

### Post by coolbrook on 2008-10-16
Seems that they worked out the kinks.  All of the beta bugs are gone.

---

### Post by Twitch6000 on 2008-10-16
> **Vadi said:**
> Yay, Adobe's linux flash download page now offers .debs for Ubuntu: [[img]http://www.ubuntu-pics.de/thumb/4497/screenshot_96_1dT2nI.png[/img]](http://www.ubuntu-pics.de/bild/4497/screenshot_96_1dT2nI.png)

It always bugged me that clueless ubuntu newbies were redirected to a terminal-based script if they had no Flash.

No 64bit version still, but they packed some very impressive features in version 10: [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)
Great news :D.

Just to note though .debs aren't only for Ubuntu they are for any Debain based distro =].

---

### Post by sloggerkhan on 2008-10-16
I'm kinda curious about why apt and deb are separate options or what they're even trying to denote with that.

Anycase, put it on my work computer and it's much better than the previous version performance wise.

---

### Post by Canis familiaris on 2008-10-16
> **alexcuervo said:**
> For 64 bit users see *"The easiest way to install Flash 10 on Ubuntu 64 bit"* at [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

Thanks. Now for the first time Flash works well in my 64bit Ubuntu with Opera.

---

### Post by Lee_Machine on 2008-10-16
It is about time that the commercial world start developing for Linux! Instead of having separate application Adobe and Mozilla need to collaborate and release something that is easy to develop for, open source, and is a direct competitor to Silverlight.

This way it's all in one suite....that would be sweet! *pun intended*:)

---

### Post by DoDoENT on 2008-10-16
> **alexcuervo said:**
> For 64 bit users see *"The easiest way to install Flash 10 on Ubuntu 64 bit"* at [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

Thanks. Works for me now!

---

### Post by daverich on 2008-10-16
weird it's not showing up any flash at all for me in firefox, 

yet kazakhase(sp?) works fine.

epiphany works fine...

opera works fine....


any ideas?

Kind regards

Dave Rich

---

### Post by daverich on 2008-10-16
hmm.

weird..

it's not that it's not working,- it's just not showing the video animation at [www.youtube.com](www.youtube.com)

Go to play a video and it works.

v odd.

Kind regards

Dave Rich

---

### Post by jespdj on 2008-10-16
> **alexcuervo said:**
> For 64 bit users see *"The easiest way to install Flash 10 on Ubuntu 64 bit"* at [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)
Thanks, that works flawlessly!

My first impression of Flash 10 is good. Flash 9 worked without problems on my system most of the time (occasionally I would just get a gray rectangle instead of the Flash element). One problem I had with Flash 9 is that when playing a YouTube-video full screen, the video was slow and choppy. It looks like Flash 10 plays full-screen videos smoothly and without choppiness.

---

### Post by _Stevie_ on 2008-10-16
The link doesnt work anymore. Seems Adobe took it down.

EDIT: seems a problem with a referer.
Here's the Link:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by Morty007 on 2008-10-16
Is the high CPU usage bug gone now???

---

### Post by Joeb454 on 2008-10-16
I wonder if there's any point in having the APT repo?

---

### Post by Izek on 2008-10-16
> **Morty007 said:**
> Is the high CPU usage bug gone now???

No, Firefox still can take up over 70 CPU on Windows. Haven't tried on Ubuntu since I don't want to get into a mess with x64 right now (since that's what my hardware is.)

Try it out on [Star Ocean: First Departure](http://na.square-enix.com/starocean/firstdeparture/)'s Website to really tax it.

---

### Post by ratmandall on 2008-10-16
Yes finally no more crashes in firefox because of flash, works flawlessly so far :\

---

### Post by _Stevie_ on 2008-10-16
I still have problems with video playback.
Same as in 9.0. The video starts, plays 3 seconds and then
stops. This behaviour repeats itself...

---

### Post by daverich on 2008-10-16
> **Izek said:**
> No, Firefox still can take up over 70 CPU on Windows. Haven't tried on Ubuntu since I don't want to get into a mess with x64 right now (since that's what my hardware is.)

Try it out on [Star Ocean: First Departure](http://na.square-enix.com/starocean/firstdeparture/)'s Website to really tax it.

wow.

that's pretty incredible cpu use showing up here - 70-80% on a core2duo.

definitely something wrong there.

Kind regards

Dave Rich

---

### Post by Falc7 on 2008-10-16
What is the best way to get the newest flash player, the deb file? Will it updates itself automatically?

---

### Post by Swarms on 2008-10-16
> **_Stevie_ said:**
> I still have problems with video playback.
Same as in 9.0. The video starts, plays 3 seconds and then
stops. This behaviour repeats itself...

That is normally a problem if you have tried different solutions for flash playback, if that is the case I don't know the exact list of what items to delete but try to find a howto for cleaning pc for flash, gnash, swf etc.

> **Joeb454 said:**
> I wonder if there's any point in having the APT repo?

Doesn't it give automatic updates?

---

### Post by _Stevie_ on 2008-10-16
> **Swarms said:**
> That is normally a problem if you have tried different solutions for flash playback, if that is the case I don't know the exact list of what items to delete but try to find a howto for cleaning pc for flash, gnash, swf etc.


Ahh that explains it! Yep, I did some audio fixing some time ago.
Thanks for the tip!

---

### Post by toupeiro on 2008-10-16
Ok..  so they give us a deb.  I guess thats great, but as far as I am concerned, no 64-bit support = they still don't get it.  Baby steps, I guess...

It'd be nice if they were as eager to support the Linux community before Microsoft started chucking silverlight at people.  Only then did they begin touting themselves as a "universal" plugin, and seemingly hack together a deb in order to live up to that.  Seems to me that if they were truly universal, we'd have not only had Linux support, but 64 bit support for a while already.  They are reacting to changes in their market and the threat of Microsoft, not because they truly see value in the direction Linux is going, or its userbase, and thats why we only got half of a solution.  Sorry it that seems buzzkill. :)

---

### Post by billgoldberg on 2008-10-16
Even though Intrepid Ibex has been in feature freeze for a while now, will this still make it in the repo's?

---

### Post by cookieofdoom on 2008-10-16
It figures. The .deb file is next to useless since anyone upgrading to Intrepid Ibex will have Flash 10 installed by default. Somehow they managed to not grasp that everyone (Windows and Linux users... not sure about the Mac users) wants 64 bit support.

---

### Post by jespdj on 2008-10-16
> **toupeiro said:**
> Ok..  so they give us a deb.  I guess thats great, but as far as I am concerned, no 64-bit support = they still don't get it.  Baby steps, I guess...
I agree that it's time that Adobe comes out with a native 64-bit version. How hard could that be? If they didn't program it in a seriously screwed up way, they wouldn't have to do much more than compile it for 64-bit. That wouldn't cost them much time and money, would it?!

But fortunately, the 32-bit version is easy to install on a 64-bit system with [this script](http://ubuntuforums.org/showpost.php?p=5974204&postcount=30).

---

### Post by Vadi on 2008-10-16
I think you should take a moment to reflect on what Adobe has to do before calling it stupid. If you bothered to read anything at all, you'll realize that it's far more than simply re-compiling Flash on a 64bit OS. There's a reason why even the open-source java sucks on 64bit still...

I've updated the original post to include 64bit instructions, thanks! They worked for myself even.

---

### Post by cookieofdoom on 2008-10-16
> **Vadi said:**
> I think you should take a moment to reflect on what Adobe has to do before calling it stupid. If you bothered to read anything at all, you'll realize that it's far more than simply re-compiling Flash on a 64bit OS. There's a reason why even the open-source java sucks on 64bit still...

I've updated the original post to include 64bit instructions, thanks! They worked for myself even.

I know what you're saying, it is no small task to make the 64 bit version. At the same time, it's also no small task to add all the features they added to Flash 10. This was the perfect time to go 64 bit, in my opinion. It's not like they don't have the resources to do it.

---

### Post by alexcuervo on 2008-10-16
For 64 bit users see *"The easiest way to install Flash 10 on Ubuntu 64 bits"* at [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

---

### Post by undoIT on 2008-10-16
I hate to be the party pooper, but flash transparency is still not working with Flash 10, at least in 64-bit. I uninstalled the Flash 9 non-free plugin from repos and then installed using the script here:

[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

Works just fine, but still, no transparency :(

---

### Post by undoIT on 2008-10-16
> **undoIT said:**
> I hate to be the party pooper, but flash transparency is still not working with Flash 10, at least in 64-bit.

Wait a minute! I just opened a page to test in Opera 64-bit and transparency is working :D

It looks like Firefox and Epiphany do not support transparency.

---

### Post by tenderone on 2008-10-16
> **Ash R said:**
> Its about time.  I remember all the troubles i had with installing flash...

i will second that :popcorn:

---

### Post by Dragonbite on 2008-10-16
If Firefox comes up with the list of possible Flash plugins to install, will it list Flash 9 or 10?  Does it automatically update or not?  Does anybody know?

---

### Post by hostguy on 2008-10-16
So I did the install and here is what I get with dpkg -l | grep flash:

ii  flashplugin-nonfree                        10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 Adobe Flash Player plugin installer

about:plugins says: 

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

I have completely removed Flash, rebooted, re-installed, rebooted and I still get the same result. What am I missing?

(Hardy 8.04 32-bit)

---

### Post by geoken on 2008-10-16
> **cookieofdoom said:**
> I know what you're saying, it is no small task to make the 64 bit version. At the same time, it's also no small task to add all the features they added to Flash 10. This was the perfect time to go 64 bit, in my opinion. It's not like they don't have the resources to do it.

The features they added to flash 10 already existed in community created AS3 classes. 3d, IK, Improved text, they all exist in multiple free, open source classes. 

Also, Flash 64 has already been shown at conferences.

[http://www.flashmagazine.com/news/detail/64_bit_flash_player_for_linux_in_the_works/]("http://www.flashmagazine.com/news/detail/64_bit_flash_player_for_linux_in_the_works/")

---

### Post by Sealbhach on 2008-10-16
> **undoIT said:**
> Wait a minute! I just opened a page to test in Opera 64-bit and transparency is working :D

It looks like Firefox and Epiphany do not support transparency.

Is there a good page where I can test that?


.

---

### Post by Morty007 on 2008-10-16
I installed it, (I think) and now my menus are fixed on flash sites so they don't get stuck behind the flash, but when I do a right click and about I get the same version  10,0,0,525

Any hints on this?

---

### Post by Morty007 on 2008-10-16
What is going on?  This was on an adobe page for flash [http://labs.adobe.com/technologies/flashplayer10/releasenotes.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html)

# For Linux, Flash Player 10 only supports browsers that are supported by each specific distribution of Linux. There are issues unrelated to Flash Player that can occur if a user installs a browser that is not supported on that Linux distribution. (For example, at the time this was written, Firefox 3 was not officially supported by Ubuntu 7.)
# 3D Effects:

    * Components don’t work properly with 3D Effects.
    * 2.5D or 3D objects do not print correctly to PDF nor to hardware printer. (232562)

# Color Management: The ability to read source profiles is not included in this feature, by design.  Comments or questions can be posted to the Flash Player 10 Forum.
# GPU Compositing and GPU Blitting:

    * Issues may occur with unsupported drivers.
    * Hardware acceleration does not currently optimize the Alpha, Erase, Invert & Subtract blendmodes and vectors for GPU compositing.
    * o **For Linux and Solaris, the hardware acceleration feature will not work if you are using a compositing window manager (compiz). In this case, Flash Player 10 Beta will always fall back to software.** If you would like to test Flash Player 10 Beta on Linux or Solaris, please disable your compositing window manager. (237833)

---

### Post by Izek on 2008-10-16
> **Morty007 said:**
>     * o **For Linux and Solaris, the hardware acceleration feature will not work if you are using a compositing window manager (compiz). In this case, Flash Player 10 Beta will always fall back to software.** _If you would like to test Flash Player 10 Beta on Linux or Solaris, please disable your compositing window manager._ (237833)

Now look at the part in underline.

---

### Post by racoq on 2008-10-16
This latest version of flash is not working with Epiphany (although it works ok in Firefox). I tested both the hardy 2.22 version and Intrepid version 2.24 (gecko backend). That's a shame since i've tested it on firefox, and it is a lot faster :(

---

### Post by Morty007 on 2008-10-16
Yes I read that. I still get high cpu usage with certain sites. This ebay page sends it sky high still. [http://cgi.ebay.com/NEW-DELL-INSPIRON-1525-LAPTOP-NOTEBOOK-WARRANTY-4GB-RAM_W0QQitemZ130261285685QQihZ003QQcategoryZ177QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/NEW-DELL-INSPIRON-1525-LAPTOP-NOTEBOOK-WARRANTY-4GB-RAM_W0QQitemZ130261285685QQihZ003QQcategoryZ177QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by undoIT on 2008-10-16
An unfortunate problem with Flash 10 regardless of OS being used is that it breaks existing flash scripts such as SWFupload and copy to clipboard scripts with the new security changes that seem to be unnecessary. Wordpress and Flickr for example uses Flash + Javascript for uploading images.

More on this here:

[http://www.bit-101.com/blog/?p=1382](http://www.bit-101.com/blog/?p=1382)

---

### Post by oldsoundguy on 2008-10-16
Add to this FireFox now has a Beta of 3.1.  VERY NICE .. but it breaks a bunch of plug-ins right now.

---

### Post by undoIT on 2008-10-16
Another disappointment. CSS dropdown menus still fall behind flash banners when expanded. Two of the major bugs I was hoping would be fixed are still present :(

---

### Post by nss0000 on 2008-10-16
> **Vadi said:**
> Yay, Adobe's linux flash download page now offers .debs for Ubuntu: [[img]http://www.ubuntu-pics.de/thumb/4497/screenshot_96_1dT2nI.png[/img]](http://www.ubuntu-pics.de/bild/4497/screenshot_96_1dT2nI.png)

It always bugged me that clueless ubuntu newbies were redirected to a terminal-based script if they had no Flash.

No 64bit version still, but they packed some very impressive features in version 10: [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

[SIZE="5"]Installing Flash 10[/SIZE]

**32bit**: Just save this file and double-click on it to start: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

**64bit**: In the terminal (sorry), paste this code: 



([via]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/"))



Well that was easy. Thankx

nss0000

---

### Post by Vadi on 2008-10-16
That's the point ;)

---

### Post by grappler on 2008-10-17
Hi

Last weekend I tried several ways to get flash (and free versions) working on a 64bit machine with firefox. The only way I found was to install flashplugin-nonfreebeta. Yesterday I did an automatic upgrade as I usually do and flash stopped working presumably because the official flash 10 was installed. 

At first the flash10 plugin wasn't detected by firefox but after I'd uninstalled and reinstalled using the script from
[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)
firefox stopped asking me to install the flash plugin - but flash is still not working. 

I'm getting this message in /var/log/messages

kernel: [18323.142035] npviewer.bin[7574]: segfault at 3000c rip f67c7846 rsp ffc5f570 error 4

Turning off compiz didn't fix it. Does anyone have a solution?

---

### Post by grappler on 2008-10-17
Let me correct my last post. In fact the new flash plugin works on many sites - just not the ones I tested it on originally! And after a reboot I no longer get the segmentation fault message in /var/log/messages. 

It appears not to work on the Daily Show and the Colbert Report but has worked on all other sites I tried! Were I Macchiavellian I might sense a Republican conspiracy here. :)

---

### Post by Sealbhach on 2008-10-17
Yeah, Daily Show doesn't work for me either.

I got a popup message telling me npviewer.bin had crashed.


.

---

### Post by SunnyRabbiera on 2008-10-17
> **Sealbhach said:**
> Yeah, Daily Show doesn't work for me either.

I got a popup message telling me npviewer.bin had crashed.


.

Comedy central works fine for me with flash 10.

---

### Post by grappler on 2008-10-17
Correction again: I'm still getting this in /var/log/messages:

kernel: [ 1419.687045] npviewer.bin[13147]: segfault at c rip f677c2a3 rsp 
ffce8730 error 4

when I go to the Daily Show.

---

### Post by derfinsterling on 2008-10-19
> **grappler said:**
> It appears not to work on the Daily Show and the Colbert Report but has worked on all other sites I tried! Were I Macchiavellian I might sense a Republican conspiracy here. :)

When I try to run a video on the Colbert Report, flash shuts down for all other sites as well. I only get grey boxes then.

---

### Post by oldsoundguy on 2008-10-19
Think about this:
Problems are appearing for folks at just a few sites .. not all of them.

Now, could it POSSIBLY be that there is an issue with the SITE?

Too often we blame something we installed for a problem we run into at an ON LINE SITE, (I catch myself doing it, too), when the issue is the code written on the site!  (think about sites written for IE and tested with IE only as a prime example!)

Just because someone uses the title of IT and is employed as such, does not make them 100% perfect in operating that site. Failure to properly and completely test code across all platforms is the primary reason for site errors.  Some IT's just don't take the time to cross platform check their work.

---

### Post by Christmas on 2008-10-19
Yeah, but it's still very slow and CPU intensive in both Firefox and Konqueror. Take the [AlienArena](http://icculus.org/alienarena/rpa/aquire.html) homepage for example. Both Fx and Konqueror 100% CPU. By the way, why in the world would an open-source project use Flash for their website?

---

### Post by oldsoundguy on 2008-10-19
because Flash, unlike other systems such as Quicktime, or some crud (whatever it is) from MS, or having to write many lines of code yourself, is universal across all browser platforms.  The music on my website is all done with Flash.  It allows the visitors to yea or nay or control the volume.
Same can be said for video clips.  It is universal across browsers.

It may not be the most elegant of solutions, but the object of embedding is to be able to be seen and heard when the surfer lands. If there is no plug in available for the browser to see/hear the work done on the site, NOBODY SEES/HEARS IT!

---

### Post by grappler on 2008-10-21
In answer to the reply from Oldsoundguy that the issue might be with the sites rather than the software, I'd point out that, at least for me (running Hardy on a 64 bit machine), these sites were working fine with Flash 10 beta, but are not working with Flash 10. I'd say that was due to a change in the software rather than the sites. I still have been unable to get Flash 10 working with a number of sites, including Comedy Central. If anyone has found a workaround for this, I'd appreciate  hearing about it.

---

### Post by undoIT on 2008-10-21
I installed using the script posted on this site and I'm running 64-bit. Just to confirm, Comedy Central does not work and breaks the Flash in all of the other tabs I have open with Firefox after visiting Comedy Central. Time to reboot the browser...

---

### Post by alexcuervo on 2008-10-22
For 64 bit users see "The easiest way to install Flash 10 on Ubuntu 64 bit" at [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/")

---

### Post by DrMega on 2008-10-22
Does anyone know how to make it work on Gutsy (I can't use Hardy because it crashes frequently on my machine). Is it even possible? I tried and it complained about a dependancy (libCairo2), but I checked and it is installed.

> **oldsoundguy said:**
> Just because someone uses the title of IT and is employed as such, does not make them 100% perfect in operating that site. Failure to properly and completely test code across all platforms is the primary reason for site errors.  Some IT's just don't take the time to cross platform check their work.

I work in the industry and have came across very many incompetent, but highly paid "professionals". At our company we test our work thoroughly, each development goes through a minimum of four stages of testing (the developer tests his own work, before submitting it to a tester, the tester then submits its for user acceptance testing then it all goes for final QA testing before release). However many of the companies we have occassionally partnered with for certain projects just rattle out some code and then release it without even seeing if it runs OK.

---

### Post by undoIT on 2008-10-24
I just downloaded the latest ISO for Kubuntu 8.10 64-bit and put it on my secondary laptop.

Installing Flash couldn't have been easier. I went to Adept package manager, searched for "flashplugin". It found the latest version of Flash 10. I chose to install and all related packages were automatically added. Done deal :D

---

### Post by coolbrook on 2008-10-25
> **DrMega said:**
> Does anyone know how to make it work on Gutsy (I can't use Hardy because it crashes frequently on my machine). Is it even possible? I tried and it complained about a dependancy (libCairo2), but I checked and it is installed.

I installed it using the tar.gz file.  Extracted it and then ran ./flashplayer-installer in the created directory. I'm still using Firefox 2 on Gutsy, so I copied the libflashplayer.so file to the mozilla plugin folders.  It works for some things in Flash, like youtube, but other things bring up the old bugs (see: [www.argonauts.ca](www.argonauts.ca))

I guess Adobe doesn't really want to support Ubuntu pre-Hardy.

EDIT:  Just installed Firefox 3.0.3 in Gutsy using the instructions [here](http://www.psychocats.net/ubuntu/firefox) and everything seems ok.

---

### Post by phrostbyte on 2008-10-25
> **undoIT said:**
> I just downloaded the latest ISO for Kubuntu 8.10 64-bit and put it on my secondary laptop.

Installing Flash couldn't have been easier. I went to Adept package manager, searched for "flashplugin". It found the latest version of Flash 10. I chose to install and all related packages were automatically added. Done deal :D

Yeah Intrepid made it a lot easier for 64-bit users. But keep in mind Flash is still 32-bit, so it's not really 'native' per say. Running 32-bit apps while your processor is in 64-bit mode does incur a performance penalty. I can't tell you how big it is though, it might be very little.

---

### Post by ryry46d9 on 2008-10-26
so I went to the [www.macromedia.com/software/flash/about/](www.macromedia.com/software/flash/about/) got flash10 .deb

it uninstalled 9 and installed 10 closed firefox 3.0.3 and went back to that page only to find out it wants 9 again 

I also use "flash chat" 4.X and that site also told me to install flash9 

im running ubuntu 8.04.1 32bit on a amd64 3500+ (64bit was lacking my support for software and I got have 4Gb of ram )  

so im not sure what's really going on but it seams the later builds of 10 are just buggy 

can any one conform less of cpu over head in 10 beta????and or stable if you got lucky to install it 

it seams after a few hours in the flashchat room the proc gets taxed preaty hard

---

### Post by Sugz on 2008-10-26
Hmm i cannot seem to install flash 10 because of a dependency issue with the .Deb
aparrently i dont have cairo2 installed, however my package manager confirms that i do indeed have cairo2 installed. :confused:

---

### Post by Vadi on 2008-10-26
> **Sugz said:**
> Hmm i cannot seem to install flash 10 because of a dependency issue with the .Deb
aparrently i dont have cairo2 installed, however my package manager confirms that i do indeed have cairo2 installed. :confused:

What version of Ubuntu are you on?

---

### Post by Snyper64 on 2008-10-28
Oh wow, this is a major improvement over Flash nine, I can finally use the drop down menus on all of my sites now like Xbox.com and razerzone without out them getting stuck behind other Flash items. Thanks for the link Vadi.

---

### Post by JARGXero on 2008-11-04
2 Questions:

The flashplugin-nonfree package included with Intrepid Ibex is already the latest version of Flash that's downloadable with the Adobe deb, right? 

No need to uninstall the flashplugin-nonfree and install the deb, right?

Thanks in advance!

---

### Post by undoIT on 2008-11-04
> **JARGXero said:**
> 2 Questions:

The flashplugin-nonfree package included with Intrepid Ibex is already the latest version of Flash that's downloadable with the Adobe deb, right? 

No need to uninstall the flashplugin-nonfree and install the deb, right?

Thanks in advance!

1. yep
2. yep

It is a major improvement over flash 9 and couldn't be easier to install in Intrepid :)

---

### Post by kikoman on 2008-11-04
After i installed Intrepid, i got the hardy .deb from adobe website (still got the habit from windows). It works though.

---

### Post by Sugz on 2008-11-04
> **Vadi said:**
> What version of Ubuntu are you on?

Gutsy 7.10.... i hope its not a problem. lets be honest, if it is.. it'll a bloody outrage in my opinion

---

### Post by Vadi on 2008-11-04
It's not an outrage, because the website specifically says 8.04+.

Sorry.

---

### Post by EdThaSlayer on 2008-11-04
My experience with Macromedia Flash Player 10 has been positive most(98%) of the times. There is only one bug with it though, I can't play the flash videos I have loaded 7 or so hours later with proper sound that is. :KS

---

### Post by JARGXero on 2008-11-04
> **undoIT said:**
> 1. yep
2. yep

It is a major improvement over flash 9 and couldn't be easier to install in Intrepid :)

Cool, thanks man!

---

### Post by RED_M on 2008-11-12
Hey, I used the 64-bit instructions in the first post, but I want to try one more option before I stick with this one (seems a bit slow for me). How do I undo the script? (I'm not comfortable with Terminal yet to be sure)

---

### Post by doorknob60 on 2008-11-12
FOr those hesitating to upgradefrom Flash 9, DO IT! I'm using Arch64 and Flash 10 with nspluginwrapper works as good as in Windows (so far). I still wish they would make a x64 plugin, but this is fine.

---

### Post by Vadi on 2008-11-12
> **RED_M said:**
> Hey, I used the 64-bit instructions in the first post, but I want to try one more option before I stick with this one (seems a bit slow for me). How do I undo the script? (I'm not comfortable with Terminal yet to be sure)

Just trying the other option should overwrite this.

---

