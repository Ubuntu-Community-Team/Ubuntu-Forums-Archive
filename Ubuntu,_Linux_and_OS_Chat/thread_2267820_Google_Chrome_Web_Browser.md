---
title: "Google Chrome Web Browser"
date: 2015-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Barsoom88 on 2015-03-04
Is there a Linux distro that has the Google Chrome as the primary web browser? I am switching college that uses Google Chrome as the primary browser.
Thanks in advance!

---

### Post by buzzingrobot on 2015-03-04
Yes, a few, although I can't recall names.  More likely use Chromium, the open-source version of Chrome.

You don't have to change distros to use Chrome: Chrome installation packages for Ubuntu and other distributions are provided by Google: [https://www.google.com/chrome/](https://www.google.com/chrome/)

---

### Post by Barsoom88 on 2015-03-04
I've tried Chromium in Ubuntu 14.04 LTS but it's waaay too glitchy. Even Mint uses FF as the default. I was hoping for GC as an add on app.

---

### Post by buzzingrobot on 2015-03-04
It's available at that link.

---

### Post by kc1di on 2015-03-04
there are two ways there is a ppa you can add [here]("http://www.ubuntuupdates.org/ppa/google_chrome")
or you can download the file from [Google here ]("https://www.google.com/chrome/browser/desktop/")and install it using software center.  
either way works fine and it will be automatically updated after you install it.

---

### Post by monkeybrain20122 on 2015-03-04
Just download and install the .deb file for your architecture (32 or 64 bits)  from Chrome's siteand right click it to install, it will automatically add the Chrome repository, there is no need to add the ppa separately.

---

### Post by Barsoom88 on 2015-03-04
Thank you for all the replies....but I have a nice google chrome logo that refuses to launch.

---

### Post by Frogs Hair on 2015-03-04
Try opening form terminal and report any errors here . If it does open close it and try using the icon again because it could be an initial startup glitch   . 
```
google-chrome
```

---

### Post by lz1dsb on 2015-03-04
I would say that I'm totaly unsatisfied from Chromium and Chrome. A couple of months ago I had them both. After the latest upgrade, my system started crashing... guess what each time either Chrome or Chromium was running. It was totally unacceptable as I use my system to connect remotely from work or from hotels and I need it always on. Since I removed both Chrome and Chromium and started using FF I haven't had any such issues. Maybe it's my system, maybe there's something peculiar of my installation - I don't know, but for now I'm happy without them.

---

### Post by craig10x on 2015-03-04
@1z1dsb: probably something peculiar on your installation...i have been running Google Chrome on all the versions of ubuntu that have come out, and on numerous computers and have never had a single problem at all...in fact, it's stable, very zippy and can't even remember the last time i had any crash with it...it also renders web pages beautifully and using it with my google account makes it so convenient too :)

I will occasionally use fIrefox but Google Chrome is always my main browser (i am talking about Chrome of course...not Chromium)....

---

### Post by Barsoom88 on 2015-03-05
FH here's a part of the code.
```
[3929:3929:0305/053537:ERROR:process_singleton_posix.cc(417)] readlink failed: Permission denied

```

Thanks for your experiences.

---

### Post by vasa1 on 2015-03-05
[http://askubuntu.com/questions/510674/cant-start-chrome-permission-denied](http://askubuntu.com/questions/510674/cant-start-chrome-permission-denied)

& 

[http://ubuntuforums.org/showthread.php?t=2244285&p=13123450#post13123450](http://ubuntuforums.org/showthread.php?t=2244285&p=13123450#post13123450) and the rest of the thread

---

### Post by v3.xx on 2015-03-05
Just wanted to say that there is a optional (stable) firefox.
[ATTACH=CONFIG]260472[/ATTACH]
Works for me :)

---

### Post by Tar_Ni on 2015-03-05
> **Barsoom88 said:**
> Is there a Linux distro that has the Google Chrome as the primary web browser? I am switching college that uses Google Chrome as the primary browser.
Thanks in advance!

I don't recommend Google Chrome but it's rather strange that a college will tell you what browser to use. I mean, you can do pretty much the same things with Firefox or even Internet Explorer for that matter these days.

That being said, if you *must* I would personally suggest Chromium instead. Chromium serves as a basis for Google Chrome. It is fully open source and can be found in the Ubuntu Software Manager. It is basically Chrome, but without the Google branding. Here's how to install flash player: [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

---

### Post by craig10x on 2015-03-05
Chrome is a better way to go then chromium...chromium is like a stripped down version of Chrome...go with the full monty ;)
Tar_Ni has a thing about google and .....so naturally he would prefer a pure open source browser like firefox...

I still feel that Chrome blows firefox out of the water as far as browsers go....automatic timely updates directly from google, superior, up to date flash (pepper flash is built in), better web page rendering great extensions available and if you have a google account and log into when using the browser, then it automatically remembers all the urls, settings, extensions, passwords you have set, the whole works...I love that i could go on someone else's computer or say, do a fresh install of ubuntu, and as soon as i add on Chrome and log into it, it's like i never left it...it remembers everything and saves me a lot of work...

---

### Post by deadflowr on 2015-03-05
To those pointing out Firefox as an option, please note the OP needs to use Google Chrome.
The original post:
> Is there a Linux distro that has the Google Chrome as the primary web browser? I am switching college that uses Google Chrome as the primary browser.
Thanks in advance!


---

### Post by vasa1 on 2015-03-05
> **deadflowr said:**
> To those pointing out Firefox as an option, please note the OP needs to use Google Chrome. ...

Unfortunately, most browser threads end up the same way: people recommend their personal favorites or run down other browsers.

Anyway, OP hasn't been too informative :(

---

### Post by Tar_Ni on 2015-03-06
> **craig10x said:**
> Chrome is a better way to go then chromium...chromium is like a stripped down version of Chrome...go with the full monty

Chromium has pretty much the same features than Chrome, now even the built-in pdf viewer. The only blatant thing that is missing is pepperflash, but that can be easily installed and updated in Ubuntu 14.04 onward.

> **craig10x said:**
> I still feel that Chrome blows firefox out of the water as far as browsers go....automatic timely updates directly from google, superior, up to date flash (pepper flash is built in), better web page rendering great extensions available and if you have a google account and log into when using the browser, then it automatically remembers all the urls, settings, extensions, passwords you have set, the whole works...I love that i could go on someone else's computer or say, do a fresh install of ubuntu, and as soon as i add on Chrome and log into it, it's like i never left it...it remembers everything and saves me a lot of work...

I have both Firefox and Chromium installed in Xubuntu and both are *very* similar in terms of speed. I don't have any issue with page rendering in Firefox either. I honestly don't care about flash player, and I default to HTML5 wherever possible. Flash is a technology of the past. I am looking forward to Shumway. Besides, Firefox has so many more extentions, for just about everything. That really made it's fame and still very much does.

And no, I wouldn't trust Google with all my settings, favorite, urls stocked in the cloud. I much prefer to back up my boomarks and extentions settings on a USB stick along other personal files. I don't use other's people computers for personal stuffs anyway. In all cases, the college student is expected to have his own laptop.

---

### Post by Barsoom88 on 2015-03-08
> **kc1di said:**
> there are two ways there is a ppa you can add [here]("http://www.ubuntuupdates.org/ppa/google_chrome")
or you can download the file from [Google here ]("https://www.google.com/chrome/browser/desktop/")and install it using software center.  
either way works fine and it will be automatically updated after you install it.

Tried installing and uninstalling chrome a few times but nothing soooo I reinstalled Ubuntu to have the software center experience an error and shut down when I tried to install chrome. I suppose this is why I'm looking for a distro with Chrome as the main browser.

---

### Post by stalkingwolf on 2015-03-08
I have both Chrome and Chromium installed.  As i recall they were both installed from symantic.

Many Colleges will tell students that they must use this or that.  a specific O/S , Browser etc. if you push and dig a little deeper you will find the reason is that the particular app or O/S is all their onboard tech support knows how to support.   I know this from experience with Colorado Tech.  They told me I had to use windows and power point.  I told them   HMMMM   well what i told them is not printable here.

other then a couple mic tweaks i had no problem using my setup.

When we moved in here I was told that the install tech had to have a windows machine to set up the internet.  I said HMMMM   and booted my wifes dual boot system.  6 mo . later when the same tech came to replace a bad router i didnt give it a thought.  He sat down at her computer did what he had to and started to leave.  As he went out the front door I said Oh By the way, you just did your first linux install. please do not tell customers that they MUST have windows.

---

### Post by buzzingrobot on 2015-03-08
This ([https://code.google.com/p/chromium/issues/detail?id=401655](https://code.google.com/p/chromium/issues/detail?id=401655)) says Chrome/Chromium for Linux is broken for kernel versions below 3.17.

(More here: [http://www.phoronix.com/scan.php?page=news_item&px=Google-Chrome-TSYNC-Kernel&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Phoronix+%28Phoronix%29](http://www.phoronix.com/scan.php?page=news_item&px=Google-Chrome-TSYNC-Kernel&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Phoronix+%28Phoronix%29). This also says work on patching earlier Ubuntu kernels is in progress.)

---

### Post by Tar_Ni on 2015-03-08
> **Barsoom88 said:**
> Tried installing and uninstalling chrome a few times but nothing soooo I reinstalled Ubuntu to have the software center experience an error and shut down when I tried to install chrome. I suppose this is why I'm looking for a distro with Chrome as the main browser.

You can try Cubuntu. It's a French Linux distro that ships Ubuntu with the Cinnamon + MATE desktop environment as well as the Google Chrome browser as default.

[http://www.cubuntu.fr/?q=node/5](http://www.cubuntu.fr/?q=node/5)  (You need to selection this iso: [14-04-2-v183b-stable.iso]("http://sourceforge.net/projects/cubuntu/files/14-04-2-v183b-stable.iso/download")  which is the 14.04.02 LTS 64 bit.)

Though it is considered a 'distro', it is in fact nothing more than Ubuntu 14.04.2 64 bit with the Mate and Cinnamon DE installed. It comes bundled with the most popular apps, Chrome, VLC, Skype ect. It might suit your needs though, that is remaining on Ubuntu while getting Chrome out-of-the-box.

**Beware that you will need to install support for english language through the Synaptic Package Manager once the installation (in french) is completed. If you don't know how to do that, please request assistance in the Beginner Forum.

---

### Post by craig10x on 2015-03-08
Can't figure why there would be any problem installing Google Chrome from their website....you just download the deb file in firefox, and when the little window comes up, you ask it to open in ubuntu software center...then software center open, shows chrome after about 30 seconds and you hit "install"...never, ever had a problem doing that...
Then you just type chrome in dash, click it to open, and lock it to the unity launcher...It even puts the chrome ppa updater into your software updater sources, automatically...

---

### Post by vasa1 on 2015-03-08
> **buzzingrobot said:**
> This ([https://code.google.com/p/chromium/issues/detail?id=401655](https://code.google.com/p/chromium/issues/detail?id=401655)) says Chrome/Chromium for Linux is broken for kernel versions below 3.17.

(More here: [http://www.phoronix.com/scan.php?page=news_item&px=Google-Chrome-TSYNC-Kernel&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Phoronix+%28Phoronix%29](http://www.phoronix.com/scan.php?page=news_item&px=Google-Chrome-TSYNC-Kernel&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Phoronix+%28Phoronix%29). This also says work on patching earlier Ubuntu kernels is in progress.)

```
05:02 AM ~ $ uname -a
Linux vasa1-Inspiron-1545 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```I have **Version 41.0.2272.76 (64-bit)**. I'm not sure anything is broken.

---

### Post by Barsoom88 on 2015-03-09
Tar_Ni,
I've check out the website you suggested my passable French should allow me to use the distro. I"ll download and use as a backup! ;)

---

### Post by Barsoom88 on 2015-03-09
[B]UPDATE
After searching Distrowatch the only two distros were: Simplicity and Android. Simplicity has Chrome as its primary browser BUT the install was too quirky for me to rely on: too bad because the layout was great....a more permanent type would have been perfect. Android was quirky from the beginning as it turned the screen sideways as in the form of a tablet not good for a laptop. Out of desperation I went to Mint and used the information provided by kc1di and it worked perfectly....so far. :p
[/B]

---

### Post by Tar_Ni on 2015-03-09
> **Barsoom88 said:**
> Tar_Ni,
I've check out the website you suggested my passable French should allow me to use the distro. I"ll download and use as a backup! ;)

Good but don't forget that you can switch to english language after the installation is completed. Just get the Synaptic Package Manager and install the english language support package.

EDIT: If Linux Mint works with Chrome than fine. But if you want to use Ubuntu (and easily switch between Unity, Cinnamon or MATE desktop environments) than give Cubuntu a shot.

---

### Post by Mike_Walsh on 2015-03-09
> **stalkingwolf said:**
> I have both Chrome and Chromium installed.  As i recall they were both installed from symantic.

Many Colleges will tell students that they must use this or that.  a specific O/S , Browser etc. if you push and dig a little deeper you will find the reason is that the particular app or O/S is all their onboard tech support knows how to support.   I know this from experience with Colorado Tech.  They told me I had to use windows and power point.  I told them   HMMMM   well what i told them is not printable here.

other then a couple mic tweaks i had no problem using my setup.

When we moved in here I was told that the install tech had to have a windows machine to set up the internet.  I said HMMMM   and booted my wifes dual boot system.  6 mo . later when the same tech came to replace a bad router i didnt give it a thought.  He sat down at her computer did what he had to and started to leave.  As he went out the front door I said Oh By the way, you just did your first linux install. please do not tell customers that they MUST have windows.

HMMMMM..... Nice one!


Regards,

Mike. :D

---

### Post by Mike_Walsh on 2015-03-09
> **vasa1 said:**
> ```
05:02 AM ~ $ uname -a
Linux vasa1-Inspiron-1545 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```I have **Version 41.0.2272.76 (64-bit)**. I'm not sure anything is broken.

Have to agree with you on that point, vasa. Exactly the same set-up here; works flawlessly.

I'm not too sure where SOME 'techs' and/or 'devs' get their information from.....


Regards,

Mike.

---

### Post by kerry_s on 2015-03-09
deepin linux has chrome & is based on ubuntu.
[http://www.linuxdeepin.com/index.en.html](http://www.linuxdeepin.com/index.en.html)

---

