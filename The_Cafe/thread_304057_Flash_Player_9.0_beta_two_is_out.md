---
title: "Flash Player 9.0 beta two is out"
date: 2006-11-21
forum: The Cafe
---

### Post by TheRingmaster on 2006-11-21
yes the second beta of the beloved flash player is out now. what are your thoughts. [Penguin.SWF: Beta II: The Audio Fix]("http://blogs.adobe.com/penguin.swf/2006/11/beta_ii_the_audio_fix.html")

---

### Post by Onyros on 2006-11-21
:frown: It still doesn't work with Opera :(

---

### Post by Rotarychainsaw on 2006-11-21
Hey how do I know I installed it right? I typed about:plugins in firefox and it says Flash 9.0 d78. I had beta 1 but forgot to look at the version before I updated it. I'm pretty sure I put it in the right place, but just making sure.

---

### Post by beerorkid on 2006-11-21
[download tarball here](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)

Just extract libflashplayer.so, and throw it in ~/.mozilla/firefox/plugins/ to install for only yourself, or as root, extract it to /usr/lib/firefox/plugins/ to install systemwide.

fixed an issue where flash would kill firefox on certian websites for me.

---

### Post by Ramses de Norre on 2006-11-21
Looks like it's working here, the first beta was a disaster though.

---

### Post by PriceChild on 2006-11-21
Beta1 worked perfectly for me... Noticing no change with this version.

I've renamed the thread for clarity

---

### Post by victorche on 2006-11-21
> Updated: November 20, 2006

A prerelease build of Flash Player 9 Update for the Linux platform is available. Flash Player 9 Update for Linux currently does not include full-screen mode and complete SSL support (SSL support is currently available in the Linux Plugin but not the Linux Standalone Player). The current Linux build is 9.0.21.78.

Download:
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

---

### Post by PriceChild on 2006-11-21
*thread merged*

---

### Post by victorche on 2006-11-21
> **PriceChild said:**
> *thread merged*

Ah, sorry for that ;]

---

### Post by Abild on 2006-11-21
I still have audio problems. Sometimes in the middle of playing a movie the audio and video stops and a small section of the audio starts to run in a loop. (Sounds a bit like a CD with scratches) The problem does not occur as frequent as with the first beta, but it's still a problem.

/me wants working gnash NOW!

---

### Post by TheRingmaster on 2006-11-21
> **Abild said:**
> I still have audio problems. Sometimes in the middle of playing a movie the audio and video stops and a small section of the audio starts to run in a loop. (Sounds a bit like a CD with scratches) The problem does not occur as frequent as with the first beta, but it's still a problem.

/me wants working gnash NOW!
post a bug report.
[Adobe - Adobe Flash Player 9 feedback form]("http://www.adobe.com/cfusion/mmform/index.cfm?name=fp_beta_feedback")

---

### Post by Ninorcjw on 2006-11-21
I downloaded that file but when i try to extract to /usr/lib/firefox/plugins/  it says "You don't have the right permissions to extract archives in the folder /usr/lib/firefox/plugins/ " just wondering how to get around this

---

### Post by PriceChild on 2006-11-21
Extract it to a your home folder. Then
```
sudo cp <<name of file>> /usr/lib/firefox/plugins/
```
Alternatively you could read the readme included in the file to find out where to put it in your own home directory, not requiring sudo rights.

---

### Post by TheRingmaster on 2006-11-21
> **Ninorcjw said:**
> I downloaded that file but when i try to extract to /usr/lib/firefox/plugins/  it says "You don't have the right permissions to extract archives in the folder /usr/lib/firefox/plugins/ " just wondering how to get around this
> sudo nautilus

use this code to get nautilus is sudo mode and then copy and paste the file in.

---

### Post by coder_ on 2006-11-21
It works perfectly!!!! :D  Finally!  In sync video+audio too!
Wow! What a fantastic day!  I just got Mplayer plugin working too!  Yeehaw!

---

### Post by SirYes on 2006-11-21
> **Rotarychainsaw said:**
> Hey how do I know I installed it right? I typed about:plugins in firefox and it says Flash 9.0 d78. I had beta 1 but forgot to look at the version before I updated it. I'm pretty sure I put it in the right place, but just making sure.
For Flash 9 Beta 1 the identifier displayed in [FONT="Courier New"]about[/FONT][FONT="Courier New"]:[/FONT][FONT="Courier New"]plugins[/FONT] was:

Shockwave Flash 9.0 d55

Looks like you got it right :)

---

### Post by Rotarychainsaw on 2006-11-21
woot

---

### Post by PriceChild on 2006-11-22
> **TheRingmaster said:**
> ```
sudo nautilus
```use this code to get nautilus is sudo mode and then copy and paste the file in.This should be ```
gksudo nautilus
```Please be EXTREMELY careful with a root terminal.

[COLOR=Red]Open it, use it for what you need it for then close it immediately![/COLOR]

---

### Post by TheRingmaster on 2006-11-22
> **PriceChild said:**
> This should be ```
gksudo nautilus
```Please be EXTREMELY careful with a root terminal.

[COLOR=Red]Open it, use it for what you need it for then close it immediately![/COLOR]
no it is just sudo nautilus. I do it all the time and it works.

---

### Post by Gustav on 2006-11-22
> **TheRingmaster said:**
> no it is just sudo nautilus. I do it all the time and it works.

Using sudo with graphical apps works most times. But sometimes it doesn't work and things can get really ugly (messing up your .ICEauthority file so that you can't login any longer).

My advise is using gksudo as much as possible.

---

### Post by bailout on 2006-11-22
> **Onyros said:**
> :frown: It still doesn't work with Opera :(

What problems are you having? I haven't tried either beta for long but using beta 1 I watched a google vis and went to another site that needed flash, both successfully with Opera.

I just copied the .so file to the Opera plugins directory (click Help . About Opera, for the plugins address) and told it to rescan for plugins. I think it rescans every time you start Opera.

---

### Post by PriceChild on 2006-11-22
> **TheRingmaster said:**
> no it is just sudo nautilus. I do it all the time and it works.Its your computer.... [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) may be a good read.

---

### Post by Daedalus on 2006-11-22
DEBs for Dapper & Edgy:

[http://esnips.com/doc/5b262b1e-5f82-4a29-b1cc-4d03a922e312/flashplugin-nonfree.deb](http://esnips.com/doc/5b262b1e-5f82-4a29-b1cc-4d03a922e312/flashplugin-nonfree.deb)
[http://esnips.com/doc/455cc26f-ec14-427c-b117-9fba634d1b45/flashplayer-nonfree.deb](http://esnips.com/doc/455cc26f-ec14-427c-b117-9fba634d1b45/flashplayer-nonfree.deb)

---

### Post by IYY on 2006-11-22
This new beta works very well for sites like YouTube.

---

### Post by TheRingmaster on 2006-11-22
good read indeed!

---

### Post by bodycoach2 on 2006-11-22
Follow the instructions on this page:
[http://www.ehomeupgrade.com/entry/3164/the_easy_way]("http://www.ehomeupgrade.com/entry/3164/the_easy_way")

The original links in the article go to the same labs site, with beta two. Just follow the same instructions.

Worked for me, and fixed things up good.

> **Rotarychainsaw said:**
> Hey how do I know I installed it right? I typed about:plugins in firefox and it says Flash 9.0 d78. I had beta 1 but forgot to look at the version before I updated it. I'm pretty sure I put it in the right place, but just making sure.

---

### Post by mikerduffy on 2006-11-24
> **beerorkid said:**
> [download tarball here](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)

Just extract libflashplayer.so, and throw it in ~/.mozilla/firefox/plugins/ to install for only yourself, or as root, extract it to /usr/lib/firefox/plugins/ to install systemwide.

fixed an issue where flash would kill firefox on certian websites for me.
I downloaded the tarball, extracted the file "libflashplayer.so", created the  plugins folder @ ~/.mozilla/firefox/, and I placed "libflashplayer.so" in ~/.mozilla/firefox/plugins/

When I run firefox, I go to about:plugins, and it says:
```
No plug-ins are installed
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org. 
```

I look at ~/.mozilla/firefox/pluginreg.dat and I see the following:

```
Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]

```Do I have to add something to the section after "[PLUGINS]"?

I am running kubuntu 6.10 on an amd64 laptop.

---

### Post by LexAevum on 2006-11-24
> Do I have to add something to the section after "[PLUGINS]"?

I am running kubuntu 6.10 on an amd64 laptop.
I had this problem. It's my own fault for not installing FFox to the default location. Bummer. Check your launcher properties to figure out where it's finding ffox and then go there +/plugins and drop the .so in there.

My problem is that I have it all working and about:plugins shows "Shockwave Flash 9.0 d78" but every time I try to view a video on Myspace I get the "upgrade to flash 9" page.](*,) 
Anyone else have/fix this issue?

---

### Post by mikerduffy on 2006-12-03
> **mikerduffy said:**
> I downloaded the tarball, extracted the file "libflashplayer.so", created the  plugins folder @ ~/.mozilla/firefox/, and I placed "libflashplayer.so" in ~/.mozilla/firefox/plugins/

When I run firefox, I go to about:plugins, and it says:
```
No plug-ins are installed
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org. 
```

I look at ~/.mozilla/firefox/pluginreg.dat and I see the following:

```
Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]

```Do I have to add something to the section after "[PLUGINS]"?

I am running kubuntu 6.10 on an amd64 laptop.

It turns out that I couldn't use Flash because the plugin **does not work in 64 bit**.
I used [this HOWTO]("http://www.ubuntuforums.org/showthread.php?p=1174435") to install Flock in 32 bit (no sense having 2 Firefoxes), and it works perfectly.

So now I have 64 bit Firefox and 32 bit Flock, which is mildly confusing.

---

### Post by mjukr on 2006-12-03
Holy cow... from a fresh build of Edgy, I just went to a site that required Flash, and the "click here to install plug-in" in Firefox actually worked!

That's awesome! Getting Flash installed has *never* been this easy!!! :p My jaw is still on the floor...

P.S. OK, so it did crash Firefox until I set my video resolution to 24-bit color (instaed of the default xorg 16-bit...but it was still pretty easy!)

---

### Post by xopher on 2006-12-03
> It turns out that I couldn't use Flash because the plugin does not work in 64 bit.

I installed nspluginwrapper instead of an all new 32-bit browser, works like a charm too. :)

Check out this post:

[http://www.ubuntuforums.org/showpost.php?p=1792581&postcount=27](http://www.ubuntuforums.org/showpost.php?p=1792581&postcount=27)

And the quick how to in the thread:

[http://www.ubuntuforums.org/showthread.php?t=277077](http://www.ubuntuforums.org/showthread.php?t=277077)

---

### Post by rev_b on 2006-12-03
Both flash 9 betas eventually crash my brownsers (opera and FF 2), making then use 100% CPU. Had to kill firefox-bin process with syetem monitor.

Back to 7.0 and all is well. Any ideas?

---

### Post by rev_b on 2006-12-03
Anyway, while flash 9 isn't final, or a workaround for this crash is found, I created a script file for quickly changing between flash 7 and 9.

```
#! /bin/bash
cp ~/.mozilla/plugins/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so.bak2
cp ~/.mozilla/plugins/libflashplayer.so.bak ~/.mozilla/plugins/libflashplayer.so
mv ~/.mozilla/plugins/libflashplayer.so.bak2 ~/.mozilla/plugins/libflashplayer.so.bak
```

I'm sure it can be done with one line, but this is actually the first script I do, so take it easy :cool: 

I put flash 7 lib as libflashplayer.so and flash 9 as libflashplayer.so.bak, exiting browser and executing script interchanges them. It works for Opera too, as it looks for the flash plugin in mozilla folder.

---

### Post by Ramses de Norre on 2006-12-03
Flash 9 made it into the backports repo yesterday! It's working flawlessly here.

---

### Post by rev_b on 2006-12-03
I installed it from synaptic also and found no diferences.

---

### Post by maniacmusician on 2006-12-03
keeps crashing opera. but beta 1 did this also. It only happens  once in a while, so I don't really care...

---

### Post by kikuman on 2006-12-04
> **bailout said:**
> What problems are you having? I haven't tried either beta for long but using beta 1 I watched a google vis and went to another site that needed flash, both successfully with Opera.

I just copied the .so file to the Opera plugins directory (click Help . About Opera, for the plugins address) and told it to rescan for plugins. I think it rescans every time you start Opera.
Thanks, that works :KS

---

### Post by Colonel Kilkenny on 2006-12-05
Opera just released new weekly build which should fix the problems with flash 9 beta (or at least some problems with flash 9 beta).

Remember that password handling in new weeklies is improved and if you install new weekly you cannot get your wand-data back in case you want afterwards install a previous version (so backup the original wand.dat-file located in ~/.opera/)

[http://my.opera.com/desktopteam](http://my.opera.com/desktopteam)

---

