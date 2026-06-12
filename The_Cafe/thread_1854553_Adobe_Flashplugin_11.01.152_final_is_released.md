---
title: "Adobe Flashplugin 11.01.152 final is released"
date: 2011-10-04
forum: The Cafe
---

### Post by Harry33 on 2011-10-04
Adobe has released now the Flashplugin 11.0.1.152 final.
It is available for both 32-bit and native 64-bit architectures.

Here:
[http://www.adobe.com/products/flashplayer.html](http://www.adobe.com/products/flashplayer.html)

---

### Post by ubupirate on 2011-10-04
Finally. I've been waiting for this to get out of Adobe Labs and into the actual Flash Platform website. :D

One of the best versions to date, especially for Linux users.

---

### Post by paul_in_london on 2011-10-04
Thanks Harry. Yes, already using it on 64 bit. ;)

Hadn't used Chrome/Chromium for a while (I mainly use Firefox).
Upgraded today from Flash 11 RC to Flash 11.0.1.152 and **tvcatchup.com** is still fine with FF/Opera, but in Chromium 15.0.871.0 and Chrome 16.0.899.0 I get sound but no picture at all.

Youtube gives me picture and sound with Chrome/Chromium.

I've tried Chromium's built-in flash plugin as well as disabling that so that Chromium will use the same plugin as FF/Opera.

Chrome 16.0.899.0 doesn't show a built-in flash plugin on the plugins page, only the **/usr/lib/flashplugin-installer/libflashplayer.so** one.

Anyone else in the UK experiencing this?

---

### Post by ZephyrXero on 2011-10-04
Chrome 64-bit does not ship with flash built-in like the 32-bit version. Hopefully that will change soon now that Flash 11 is out.

---

### Post by paul_in_london on 2011-10-04
Have just updated my 32 bit Oneiric install and the latest flash is working as it should on that website (tvcatchup.com) with Chromium 15.0.871.0 so it does seem to be a 64 bit issue.

---

### Post by danielsk on 2011-10-04
Is there any trick to install it?

I followed the Adobe site instruction, it opens in software center, but the instalation that appears is for version 10.3.183.10-0natty1

---

### Post by paul_in_london on 2011-10-05
I installed it yesterday (1x 32 bit install and 1x64 bit install on the same box) by downloading the .tar.gz from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and I was going to suggest you do the same, but that page now shows this on my 32 bit VM:

```
Download Adobe Flash Player
Adobe Flash Player version 10.3.183.10
Your system: Linux 32-bit, Firefox
```

Don't know what that's all about!

---

### Post by philinux on 2011-10-05
64 bit here. Excellent performance on bbc video full screen.

Moved to Cafe.

---

### Post by Gremlinzzz on 2011-10-05
Thanks:popcorn:

---

### Post by werty2010 on 2011-10-05
will this be available through the updates (eventually)?

---

### Post by philinux on 2011-10-05
> **werty2010 said:**
> will this be available through the updates (eventually)?

Should be as it's a final release.

---

### Post by BrokenKingpin on 2011-10-05
Hopefully this updates some of the flash performance issues I have been having. I will wait for the Ubuntu repos to have it.

---

### Post by P1C0 on 2011-10-05
> **danielsk said:**
> Is there any trick to install it?

I followed the Adobe site instruction, it opens in software center, but the instalation that appears is for version 10.3.183.10-0natty1
Well, I installed it like this:

```
$ sudo alien -v --scripts flash-plugin-11.0.1.152-release.x86_64.rpm
$ sudo dpkg -i flash-plugin_11.0.1.152-1_amd64.deb
```Then:
```
$ sudo ln -s /usr/lib64/flash-plugin/libflashplayer.so /usr/lib/firefox-addons/plugins

```If you run Firefox and go to Tools->Add-ons->Plugins you should see both versions of Flash 10.3 and 11.0, but the latter is being used.

I think this method requires manual upgrade of the flash-plugin package over time, meaning that you should download and install latest .deb from Adobe site.

edit://From tech specs I see it requires Mozilla Firefox 4.0 or Google Chrome, but I'm using it on Firefox 3.6.23 currently without issues..

---

### Post by philinux on 2011-10-05
No need to use alien on a rpm.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

There's tar file with the file libflashplayer.so

Just needs to go in .mozilla/plugins

---

### Post by lovinglinux on 2011-10-06
I have updated [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) to install it. Select the Beta option in the Wizard and it will install the final version.

---

### Post by ice60 on 2011-10-06
i tried the download and still ended up with the same 10 version. i enabled the source parter repo too. then added another repo which was supposed to update it and it didn't work. i looked at flashaid and it has 11.0.r1.129 lol. i suppose i'll do it manually :-\

---

### Post by Frogs Hair on 2011-10-06
> **werty2010 said:**
> will this be available through the updates (eventually)?

Flash updates appear pretty quickly in the update manager , especially  if a security update is involved . I was notified by the Flash Aid  Firefox add-on which I used to  install  it  .

---

### Post by alexcckll on 2011-10-07
> **Frogs Hair said:**
> Flash updates appear pretty quickly in the update manager , especially  if a security update is involved . I was notified by the Flash Aid  Firefox add-on which I used to  install  it  .
Accepted the Flash 11 update onto my Lenovo Ideapad S12... however, I was a little concerned that when playing out off Youtube, it's dropped to software video rendering, while still runnign accelerated decoding.  Seems to behave nicely on iPlayer though.

Monitored CPU usage when playing out - it seems to sit between 70-90% most of the time - is thst pretty much expected behaviour on an Atom-based box?  

Should I remove the override script I used with Flash 10.3?  (GPU override) Or will it be best to leave that, and nto worry too much about the software rendering.. as the decoding is the harder bit that it's passed to the GPU?

My Ideapad has an NVIDIA ION on-board.


However, resuming a programme on 4OD which I had started on Flash 10 - didn't want to play ball.

---

### Post by alexcckll on 2011-10-07
We7 is only using 60-75% cpu,load average about 1.9-2.2

---

### Post by BrokenKingpin on 2011-10-07
> **lovinglinux said:**
> I have updated [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) to install it. Select the Beta option in the Wizard and it will install the final version.
Is there a Flash-Aid plugin for Chromium?

---

### Post by lovinglinux on 2011-10-10
> **BrokenKingpin said:**
> Is there a Flash-Aid plugin for Chromium?

Nope. But the extension is essentially a script generator, so if you execute Flash-Aid wizard once in Firefox, Chromium will benefit from the changes as well.

---

### Post by wolfen69 on 2011-10-10
> **P1C0 said:**
> Well, I installed it like this:

```
$ sudo alien -v --scripts flash-plugin-11.0.1.152-release.x86_64.rpm
$ sudo dpkg -i flash-plugin_11.0.1.152-1_amd64.deb
```Then:
```
$ sudo ln -s /usr/lib64/flash-plugin/libflashplayer.so /usr/lib/firefox-addons/plugins

```If you run Firefox and go to Tools->Add-ons->Plugins you should see both versions of Flash 10.3 and 11.0, but the latter is being used.

I think this method requires manual upgrade of the flash-plugin package over time, meaning that you should download and install latest .deb from Adobe site.

edit://From tech specs I see it requires Mozilla Firefox 4.0 or Google Chrome, but I'm using it on Firefox 3.6.23 currently without issues..

Why are you telling people use an rpm and then alien? A mod should remove this post. Serious misinformation.

---

### Post by el_koraco on 2011-10-10
This is an experience form 32 bit Squeeze, but there's no major difference to Ubuntu. I cleaned all the manually installed cruft from the past today, ran the plugin installer from the repos (the one that downloads from the site), and now flash content is running at 20 percent of CPU, most of the load being taken on by the GPU (integrated ATI). This is like Windows, given that the CPU is a single-core weakling. 

Nice job Adobe.

---

