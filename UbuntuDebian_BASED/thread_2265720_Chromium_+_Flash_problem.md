---
title: "Chromium + Flash problem"
date: 2015-02-17
forum: Ubuntu/Debian BASED
---

### Post by p.callan on 2015-02-17
This is just a quick FYI post. I learned long ago not to spend endless hours trying to fix some insanely trivial problem that should have been working out of the box. My heart can't take it. And to be honest it's too expensive. Installed Firefox instead which just works.

1. Using Chromium [COLOR=#303942][FONT=Droid Sans]Version 37.0.2062.120 Built on Ubuntu 12.04, running on elementary OS 0.2.1 (281580).
2. Wanted to update my website at weebly.com but "Oops! You need flash player to use this editor".
3. Followed directions [here]("https://helpx.adobe.com/se/flash-player/kb/enable-flash-player-google-chrome.html") ;
4. Gave up. (Maybe this thread can help someone else)

> [/FONT][/COLOR][COLOR=#333333][FONT=adobe-clean][FONT=inherit][h=2]Install Flash Player 11.2[/h][/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=adobe-clean][FONT=inherit]
[LIST=1][FONT=inherit]
[*][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]Download the latest Flash Player from the [Adobe site]("http://www.adobe.com/support/flashplayer/downloads.html").  [COLOR=#00ff00][OK][/COLOR][/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]

[*][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]Unpack the installation file.  [COLOR=#00ff00][OK][/COLOR]

[FONT=Courier New]tar -zxvf flashplayer_11_plugin_debug.i386.tar.gz[/FONT]

The package contains the following:[/FONT]

[LIST]
[*][FONT=Courier New]libflashplayer.so[/FONT]
[*]usr
[/LIST]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]

[*][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]Create a directory, [FONT=Courier New]plugins[/FONT], in the Google Chrome's installation directory.[/FONT]
[FONT=inherit][FONT=Courier New]sudo mkdir /opt/google/chrome/plugins  [COLOR=#00ff00][This is not the correct dir. Rather it's in /usr/lib/chromium-browser/plugins/][/COLOR][/FONT][/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]

[*][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]Copy [FONT=Courier New]libflashplayer.so[/FONT] to the [FONT=Courier New]plugins[/FONT] directory.[/FONT]
[FONT=inherit][FONT=Courier New]cp libflashplayer.so /opt/google/chrome/plugins  [COLOR=#00ff00][OK after changing path][/COLOR][/FONT][/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]

[*][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]Copy the Flash Player Local Settings configurations files to the [FONT=Courier New]/usr[/FONT] directory.[/FONT]
[FONT=inherit][FONT=Courier New]sudo cp –r usr/* /usr   


[COLOR=#ff0000][Doesn't work at all. Gives:  

[/COLOR][/FONT][COLOR=#ff0000][FONT=inherit]mecomp:~/Downloads$ sudo cp –r usr/* /usr
[/FONT][/COLOR][COLOR=#FF0000][FONT=inherit]cp: cannot stat `–r': No such file or directory
[/FONT][/COLOR][COLOR=#FF0000][FONT=inherit]cp: omitting directory `usr/bin'
[/FONT][/COLOR][COLOR=#FF0000][FONT=inherit]cp: omitting directory `usr/lib'
[/FONT][/COLOR][COLOR=#FF0000][FONT=inherit]cp: omitting directory `usr/share'[/FONT][/COLOR][/FONT]
[COLOR=#ff0000]
Then I try to copy the files manually and check that I have all the priviliges, which I have. Error message: "Permission denied".  ][/COLOR]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]

[*][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]Restart Google Chrome and [enable system Flash Player]("https://helpx.adobe.com/flash-player/kb/enable-flash-player-google-chrome.html#main-pars_header").  [COLOR=#ff0000][I don't get this far][/COLOR][/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/LIST]
[/FONT]
[/FONT][/COLOR]
[COLOR=#303942][FONT=Droid Sans]



END_[/FONT][/COLOR]

---

### Post by ajgreeny on 2015-02-17
You went wrong at the first step by going to adobe and downloading the flashplayer from there.

Chromium needs the libpepflashplayer that google-chrome uses and will not work with the flashplayer still used by Firefox.

For chromium in the most recent ubuntu OSs, you just need to run ```
sudo apt-get install pepperflashplugin-nonfree
```and it's all done for you.

 I'm.not sure about Elementary-OS based on 12.04, but I think it needs a PPA repository enabled.

---

### Post by coffeecat on 2015-02-17
I'm not sure about Elementary OS either, but with Ubuntu the fix is indeed "insanely trivial" and is as ajgreeny has already posted. The package pepperflashplugin-nonfree is in the Ubuntu Multiverse repository, so if your Elementary sources.list includes that, the fix for Elementary will be the same.

You posted in Installation and Upgrades, a sub-forum of the Ubuntu Official Flavours Support section. Elementary is not an Ubuntu official flavour, so...

*Thread moved to **Ubuntu/Debian BASED**.*

I have amended your thread title, which was uncalled for.

My advice to anyone reading this thread and needing to enable flash in Chromium is to follow ajgreeny's post, not the method detailed by the OP.

---

### Post by p.callan on 2015-02-17
No, actually that was the first thing I tried. It didn't make any difference at all and that's why I moved on to the guide. Flash isn't available through the software center for chrome. I checked that too.

---

### Post by coffeecat on 2015-02-17
> **p.callan said:**
> No, actually that was the first thing I tried. It didn't make any difference at all and that's why I moved on to the guide.

It's always worked for me in Ubuntu.

> **p.callan said:**
>  Flash isn't available through the software center for chrome. I checked that too.

That&#8217;s because Google Chrome comes complete with flash pre-installed.

---

### Post by ajgreeny on 2015-02-17
See post #23 of thread at [http://ubuntuforums.org/showthread.php?t=1976503&page=2](http://ubuntuforums.org/showthread.php?t=1976503&page=2)

That should work in Elementary-OS based on 12.04

---

### Post by coffeecat on 2015-02-17
@ajgreeny, thanks for noticing that the OP is using a distro based on 12.04. I missed that. Yes, something based on 12.04 will need a PPA repository for the pepperflash plugin.

This following basically says the same as links that can be found from your link, but the OP may find this useful:

[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash)

---

### Post by p.callan on 2015-02-17
"That’s because Google Chrome comes complete with flash pre-installed."
It may, but a "chrome: plugins" (or was it "about: plugins") doesn't list it either before nor after the attempted installation. And flash content doesn't work so..

---

### Post by ajgreeny on 2015-02-17
Have you actually done what we have told you about enabling the PPA repository?

It worked for me when I was using 12.04 and chromium, so it should work for you as well.  I am, however, getting confused about what application you are speaking about; google-chrome or chromium.  If it's chromium you must add the PPA for pepperflash in 12.04; if it's google-chrome it comes with pepperflash installed by default, so no need to do anything extra.

---

