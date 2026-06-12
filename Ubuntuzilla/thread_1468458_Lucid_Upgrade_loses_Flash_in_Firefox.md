---
title: "Lucid Upgrade loses Flash in Firefox"
date: 2010-05-01
forum: Ubuntuzilla
---

### Post by noob555 on 2010-05-01
Weird problem happened when I upgraded to lucid yesterday.  Firefox says that I have the Flash plugin.  But it's like Flash isn't even there.  I've downloaded Ubuntu-restricted-extras, Medibuntu.  I just can't figure out what's wrong.  Flash just doesn't work at all, it's like it isn't even there.

I'm running Firefox 3.6.3 on a Lucid 32-bit ubuntu system.

Any advice?

I'd really appreciate any help that people can offer.

---

### Post by Joentokyo on 2010-05-01
> **noob555 said:**
> Weird problem happened when I upgraded to lucid yesterday.  Firefox says that I have the Flash plugin.  But it's like Flash isn't even there.  I've downloaded Ubuntu-restricted-extras, Medibuntu.  I just can't figure out what's wrong.  Flash just doesn't work at all, it's like it isn't even there.

 I'm running Firefox 3.6.3 on a Lucid 32-bit ubuntu system.

Any advice?

I'd really appreciate any help that people can offer.

I am having the exact same problem. Firefox says Flash is installed, but if I check the Ubuntu Software Center, it says I need to install it. I have to install Flash every time I reboot. Where does it go?

---

### Post by noob555 on 2010-05-01
I actually tracked my problem down to a glitch in one of my add-ons (Ghostery specifically).  My best advice is try opening firefox in safe mode.

```
firefox -safe-mode
```

A lot of firefox problems are due to little customization tweaks that people make.  Entering into safe mode will temporarily disable all your extensions and return you to the default theme.  

If flash is working in safe mode, then it's just a question of figuring out which of your extensions is causing the glitch.  At that point, you do process of elimination on each of your addons by disabling them individually and restarting.

Honestly, I should have tried it before I posted.  Don't know why I forgot.

---

### Post by Joentokyo on 2010-05-01
> **noob555 said:**
> I actually tracked my problem down to a glitch in one of my add-ons (Ghostery specifically).  My best advice is try opening firefox in safe mode.

```
firefox -safe-mode
```

A lot of firefox problems are due to little customization tweaks that people make.  Entering into safe mode will temporarily disable all your extensions and return you to the default theme.  

If flash is working in safe mode, then it's just a question of figuring out which of your extensions is causing the glitch.  At that point, you do process of elimination on each of your addons by disabling them individually and restarting.

Honestly, I should have tried it before I posted.  Don't know why I forgot.
My problem was different. I had more than one version of the plugin installed. I remove all, and reinstalled.

---

### Post by xDarkicex on 2010-05-02
I got Flash to work for me, example ```
http://img689.imageshack.us/img689/1905/screenshotvbg.png
```

All I did was go too System Help and support search FLASH them it will bring up a list, choose internet and Networks then from that  page click the Flash plugin installer worked for me so best of luck.

---

### Post by zappa on 2010-05-05
Hey guys, 

For me it was not an extension. 
I clicked on the link that replaces a Youtube movie. 
- The .deb is too old
- The karmic (via apt in FF, which you need to configure in about:config, it does not work either as you get the message lucid partner not known)

So what did work (as re-installing and purging and even deleting the package in /var/cache/apt did not)

Well, choose the simple tar package. 
Untar
replace the (in my case still old indeed) 

/~/.mozilla/plugins/libflashplayer.so

Fixed. 

As this tread comes up first in a Google search with flash lucid in the last week, I hope it helps someone ;-)

---

### Post by viralmeme on 2010-05-05
[QUOTE=noob555;9211247]Weird problem happened when I upgraded to lucid yesterday.  Firefox says that I have the Flash plugin/QUOTE]

$mkdir ./mozilla/plugins
$ ln -s /usr/lib/flashplugin-installer/libflashplayer.so ./mozilla/plugins/libflashplayer.so

---

### Post by yuki000 on 2010-05-12
> **zappa said:**
> Hey guys, 

For me it was not an extension. 
I clicked on the link that replaces a Youtube movie. 
- The .deb is too old
- The karmic (via apt in FF, which you need to configure in about:config, it does not work either as you get the message lucid partner not known)

So what did work (as re-installing and purging and even deleting the package in /var/cache/apt did not)

Well, choose the simple tar package. 
Untar
replace the (in my case still old indeed) 

/~/.mozilla/plugins/libflashplayer.so

Fixed. 

As this tread comes up first in a Google search with flash lucid in the last week, I hope it helps someone ;-)

:guitar:
thank you this works for me

---

### Post by EllyBilateralCI on 2010-05-13
> **xDarkicex said:**
> I got Flash to work for me, example ```
http://img689.imageshack.us/img689/1905/screenshotvbg.png
```All I did was go too System Help and support search FLASH them it will bring up a list, choose internet and Networks then from that  page click the Flash plugin installer worked for me so best of luck.

By the way .... How did you get Help And support to work because when I put in FLASH - it didn't give me a list - only brought up Desktop User guide, Character Palette, etc

---

### Post by carltonh on 2010-05-22
Note that this is a major bug that still exists in the 8.04 to 10.04 upgrade.  Here is the work around I did after the upgrade:
```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
sudo aptitude install flashplugin-installer
```

Here is the bug in Launchpad:
[https://bugs.launchpad.net/ubuntu/lucid/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/lucid/+source/flashplugin-nonfree/+bug/429841)

I confirm the workaround just worked for me today.

---

### Post by tragen on 2010-05-23
Just as FYI, for myself. I lost flash in firefox, in upgrade to lucid (though had a problem during the install where the screen was blank and not sure if completed fine or not, but gf had restarted computer, I just forced a "dpkg --configure -a" to get it back).

Anywho...

For me, after trying the uninstall/install of the flash plugin (both nonfree and adobe) via various methods mentioned in the threads I could find other than this one. Hulu etc still complained flash needed upgrading. I had even tried uninstalling/reinstalling firefox (all this via synaptic manager or the ubuntu software center).

One thread commented about the plugins not working/being there even though they showed up fine in firefox. My firefox was showing very outdated shockwave/flash version so firefox wasn't picking up the update.

I did apt get purge on firefox and the mozilla files were still on my system. I had to manually remove all mozilla folder/files to get it to do a clean install and BAM...working now.

So my problem (on 32bit system btw) was that firefox's old config/plugin files were causing the issue and ubuntu was NOT truly uninstalling/purging it from system.

But then this could be a legacy thing from having Ubuntu upgraded constantly over the past 4 years or so. ;)

Just posting in forum in case someone else has the trouble. I don't think it is worth a bug post unless others have the issue too.

Cheers

---

### Post by fiklein on 2010-05-23
Solution #10 worked for me. I had already uninstalled in Synaptic and reinstalled without benefit. I uninstalled again using Synaptic then switched to the commands in #10 in Terminal.  Thank you!!

---

### Post by jawrat on 2010-05-25
```
sudo apt-get remove --purge flashplugin-installer
sudo apt-get install flashplugin-installer
```

did the trick for me.  just a heads up for those searching... :)

---

### Post by rwigle on 2010-05-26
> **jawrat said:**
> ```
sudo apt-get remove --purge flashplugin-installer
sudo apt-get install flashplugin-installer
```

did the trick for me.  just a heads up for those searching... :)

Ditto for me after trying several other approaches.

---

### Post by bopomofo on 2010-06-16
> **zappa said:**
> Hey guys, 

For me it was not an extension. 
I clicked on the link that replaces a Youtube movie. 
- The .deb is too old
- The karmic (via apt in FF, which you need to configure in about:config, it does not work either as you get the message lucid partner not known)

So what did work (as re-installing and purging and even deleting the package in /var/cache/apt did not)

Well, choose the simple tar package. 
Untar
replace the (in my case still old indeed) 

/~/.mozilla/plugins/libflashplayer.so

Fixed. 

As this tread comes up first in a Google search with flash lucid in the last week, I hope it helps someone ;-)

I had to do an additional step:

Enable the flash plugin via Tools > Add-ons > Plugins > Right Click Shockwave Flash and click Enable

---

### Post by llangwm on 2010-06-20
#13 worked for me ... thanks!

---

### Post by FourBrane on 2010-07-11
$mkdir ./mozilla/plugins
$ ln -s /usr/lib/flashplugin-installer/libflashplayer.so ./mozilla/plugins/libflashplayer.so[/QUOTE]

Thanks, ymitchel. This was the solution for me. Checking .mozilla/plugins, I found an old version of libflashplayer.so, so I deleted it and linked to the new as you indicated. Bingo.
If anyone has lost flash on upgrading, they probably already have a plugins subdirectory. In my case, the upgrade process didn't remove the older flash build.

---

