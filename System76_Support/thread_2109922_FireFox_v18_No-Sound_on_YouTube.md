---
title: "FireFox v18 No-Sound on YouTube"
date: 2013-01-28
forum: System76 Support
---

### Post by Cliff Bentley on 2013-01-28
[COLOR=#000000][FONT=Arial]The  problem is that there is no sound with YouTube videos. Google draws so  many hits on this problem, that I’m confused about which option to take.  I’m a Linux Newbie. This is a new computer from System76.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The YouTube video works fine and video’s with sound work elsewhere {e.g.[/FONT][/COLOR][[COLOR=#000000][FONT=Arial] [/FONT][/COLOR][COLOR=#1155cc][FONT=Arial]_www.snagfilms.com/_[/FONT][/COLOR]]("http://www.snagfilms.com/")[COLOR=#000000][FONT=Arial]  ...}. Sound definitely exists from a number of sources. After a couple  days of use, the Updater prompted me to run updates. So I did and  Firefox was updated to v18.0. I do not recall if I had used YouTube on  this new PC prior to the update, so I don’t know if this problem was  initiated by the update.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Here’s some config info on my new computer and for Firefox:[/FONT][/COLOR]
> [COLOR=#000000][FONT=Arial]Ratel Performance ( ratp1 ) [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Ubuntu 12.10 64 bit, v12.10  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]3rd Generation Intel Core i5 3470 (3.20GHz - 6MB cache - 4 Cores - HD Graphics 2500)     [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]4 GB – 2 x 2 GB - Crucial Sport Dual Channel DDR3 - 1600 MHz     [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Intel High Definition Graphics     [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]250 GB SATA III 6 Gb/s 16 MB Cache     [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]CD-RW / DVD-RW Dual Layer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Logitech Wireless Desktop MK320[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[COLOR=#000000][FONT=Arial]Firefox v18.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]about:plugins (partial, relevant output) >>>[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Shockwave Flash[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]File: libflashplayer.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Shockwave Flash 11.2 r202[/FONT][/COLOR]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Flash  is NOT currently an installed plugin for Firefox. It is my  understanding that I should not need both "Flash" and "Shockwave Flash"  to play YouTube. The Ubuntu Software Center lists “Adobe Flash” under  “Installed” (i.e. green field checkmark), though it is listed as  “Installer”:[/FONT][/COLOR]
> [COLOR=#000000][FONT=Arial]Installer for the Adobe Flash plugin for Mozilla[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]version: flashplugin-installer 11.2.202.261ubuntu0.12.10.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Is there ever a time that both "Flash" and "Shockwave Flash" should be enabled plugins? [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can someone point me to a solution for this?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks,
Cliff
[/FONT][/COLOR]

---

### Post by isantop on 2013-01-30
> **Cliff Bentley said:**
> [COLOR=#000000][FONT=Arial]The  problem is that there is no sound with YouTube videos. Google draws so  many hits on this problem, that I’m confused about which option to take.  I’m a Linux Newbie. This is a new computer from System76.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The YouTube video works fine and video’s with sound work elsewhere {e.g.[/FONT][/COLOR][[COLOR=#000000][FONT=Arial] [/FONT][/COLOR][COLOR=#1155cc][FONT=Arial]_www.snagfilms.com/_[/FONT][/COLOR]]("http://www.snagfilms.com/")[COLOR=#000000][FONT=Arial]  ...}. Sound definitely exists from a number of sources. After a couple  days of use, the Updater prompted me to run updates. So I did and  Firefox was updated to v18.0. I do not recall if I had used YouTube on  this new PC prior to the update, so I don’t know if this problem was  initiated by the update.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Here’s some config info on my new computer and for Firefox:[/FONT][/COLOR]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Flash  is NOT currently an installed plugin for Firefox. It is my  understanding that I should not need both "Flash" and "Shockwave Flash"  to play YouTube. The Ubuntu Software Center lists “Adobe Flash” under  “Installed” (i.e. green field checkmark), though it is listed as  “Installer”:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Is there ever a time that both "Flash" and "Shockwave Flash" should be enabled plugins? [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can someone point me to a solution for this?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks,
Cliff
[/FONT][/COLOR]

There is an update available for Flash. Unfortunately, the servers seem to be having trouble dishing it out to users. Once that issue is cleared up, you should be able to remove and reinstall flash to fix your problem.

---

### Post by Cliff Bentley on 2013-01-31
The Ubuntu Software Center has me confused. It seems to say this installed package "Downloads and installs the Adobe Flash Player plugin ...". It seems to say the name of the relevant file is "[COLOR=#000000][FONT=Arial]flashplugin-installer 11.2.202.261ubuntu0.12.10.1[/FONT][/COLOR]".

What am I missing here? The Ubuntu Software Center does not provide a way to execute this "installer". So I tried from the CLI. This is where my newbieness shows my ignorance. I tried typing the file name to execute it. Error. I tried:
```
sudo locate [COLOR=#000000][FONT=Arial]flashplugin-installer 11.2.202.261ubuntu0.12.10.1[/FONT][/COLOR]
```
Got back lots of output, but could not figure out **which file to execute? What am I supposed to do? **

When I do download it, will it also set it up inside of FireFox? If not, how will I enable it from within FireFox>>Tools>>Add ? Will I need to know which file to enable, or will it be obvious?

---

### Post by isantop on 2013-02-01
> **Cliff Bentley said:**
> The Ubuntu Software Center has me confused. It seems to say this installed package "Downloads and installs the Adobe Flash Player plugin ...". It seems to say the name of the relevant file is "[COLOR=#000000][FONT=Arial]flashplugin-installer 11.2.202.261ubuntu0.12.10.1[/FONT][/COLOR]".

What am I missing here? The Ubuntu Software Center does not provide a way to execute this "installer". So I tried from the CLI. This is where my newbieness shows my ignorance. I tried typing the file name to execute it. Error. I tried:
```
sudo locate [COLOR=#000000][FONT=Arial]flashplugin-installer 11.2.202.261ubuntu0.12.10.1[/FONT][/COLOR]
```
Got back lots of output, but could not figure out **which file to execute? What am I supposed to do? **

When I do download it, will it also set it up inside of FireFox? If not, how will I enable it from within FireFox>>Tools>>Add ? Will I need to know which file to enable, or will it be obvious?

The installer is automatically run during package installation. If you installed flashplugin-installer, then you have flash installed (provided a normal server state, unlike what's going on now)

Ubuntu should automatically notify you that it failed to download additiona files, and allow you to re-attempt the download. If you're not seeing this, then you can run these commands from the comamnd prompt:

```
sudo apt-get remove flash*
sudo apt-get install flashplugin-installer
```

The only reason why this package is goofy is due to licensing limitations.

---

### Post by Cliff Bentley on 2013-02-02
I ran the apt-get remove and then the apt-get install as you suggested. This is the result from my terminal on the latter command:
```

$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf ttf-mscorefonts-installer ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 35 not upgraded.
Need to get 0 B/7,542 B of archives.
After this operation, 139 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 212942 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.261ubuntu0.12.10.1_amd64.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.261.orig.tar.gz
Installing from local file /tmp/tmpjFrdBl.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.261ubuntu0.12.10.1) ...
```
At this point, it looked good. Then I rebooted my box. However, the plugin doesn't seem to load in FireFox. Adobe Flash does not get listed (installed) in FF's Add-ons Manager>>Plugins. So I select its "Get Add-ons" item, but it does not seem to know of an Adobe Flash that can be loaded. The search does not find it. I think I accidentally added some "Extensions" that relate to youtube, but Adobe Flash eludes me. **Any suggestions?**

Thanks.

---

### Post by isantop on 2013-02-05
Nope, the download still isn't working, as is evidenced by this line:

```
Installing from local file /tmp/tmpjFrdBl.gz
```

This is saying that the download timed out, and it's installing a local copy of the file, which is more than likely out of date (since it was downloaded in the past). So any errors you were getting from before would have simply carried over to the new one anyway.

Are flash elements loading in webpages at all?

---

### Post by Cliff Bentley on 2013-02-05
> Are flash elements loading in webpages at all?
Does this answer what you are asking:  YouTube videos load and play. The video plays, pauses, skips, etc. The only thing that does not work is the audio. I presume this is because "Shockwave Flash" gives me video but not audio ??? As I mentioned in the first post, "Shockwave Flash" is a loaded plugin in FF. My on-line research seems to indicate that "Adobe Flash" is required. "Shockwave Flash" is never mentioned as a viable alternative for Linux.

Do you have any idea when they might fix the source? Is there an alternative source I can set up? An alternative player to  "Adobe Flash"?

Thanks for bearing with me on this.

---

### Post by isantop on 2013-02-06
> **Cliff Bentley said:**
> Does this answer what you are asking:  YouTube videos load and play. The video plays, pauses, skips, etc. The only thing that does not work is the audio. I presume this is because "Shockwave Flash" gives me video but not audio ??? As I mentioned in the first post, "Shockwave Flash" is a loaded plugin in FF. My on-line research seems to indicate that "Adobe Flash" is required. "Shockwave Flash" is never mentioned as a viable alternative for Linux.

Do you have any idea when they might fix the source? Is there an alternative source I can set up? An alternative player to  "Adobe Flash"?

Thanks for bearing with me on this.

No, Shockwave Flash is the correct plugin as listed in Firefox. Check that the volume controls in the youtube video player are turned up. Are you getting sound if you go to a non-youtube flash website, like Vimeo?

---

### Post by Cliff Bentley on 2013-02-06
Done - Fixed! Your suggestion to re-check the local sound controls on the YouTube player did it. I definitely tried to get those controls to work before my first post, but they were completely disabled. Apparently, that [COLOR=DarkRed]apt-get[/COLOR] I did 3 days ago did load the flash. It looked to me like the [COLOR=DarkRed]apt-get[/COLOR] had failed because the browser did not list Adobe Flash as a plugin (as I had expected), it listed only Shockwave Flash. So with the browser apparently not knowing of Adobe Flash, I did not think to go back and check those controls on the YouTube player.

I was aware from the beginning that the sound worked on non-YouTube sites. I mentioned that in my first post. Obviously, I had to rule out that simple "fix" before I went through this.

Thanks for all the good help.

---

### Post by thomassisson on 2013-04-27
If you have Kubuntu or are running KDE, follow these instructions. This is assuming you are not having any other sound problems, have Alsa and PulseAudio properly installed, have KMix installed, and the KDE Flash Player Module and Adobe Flash Player are installed. This should apply to any version of Firefox using Adobe Flash.

First, check to see that something is not muted.
Right-click on the volume control on the panel and click on "Select Master Channel ... ." If the volume control is not on your panel, open KMix from the application menu, or just Alt-F2, type kmix in the dialog, and enter. Maximize the window so that all tabs are visible and select "Playback Streams." If there is a red X by the speaker at the bottom of the volume meter, click it. (This may be a good time to check other tabs and look for red Xs.) If you only see System Sounds, you need to close any system settings windows that are open, and select a different tab and return to the tab.

For some absurd, stupid reason, sound is muted in KDE. Try opening a YouTube video to see if you have sound. Make sure the volume is not muted there too. Doh!

If you still don't have sound, try this next step. This should help with disabled sound controls on the YouTube videos.
Open KDE System Settings, click on Adobe Flash Player, check to see that you have four tabs that say Storage, Camera and Mic, Playback, and Advanced.
If you see an error message, open a terminal and type this (or just copy and CRTL-ALT-V) in the terminal, **if you are running a 64 bit version of Linux**:

```
sudo ln -s /usr/lib64/kde4/kcm_adobe_flash_player.so /usr/lib/kde4/
```

**If you are not running a 64 bit Linux**, you will have to find kcm_adobe_flash_player.so. If it is already in /usr/lib/kde4, you are done. Otherwise see if it is in /usr/lib32/kde4, then use this instead:

```
sudo ln -s /usr/lib64/kde4/kcm_adobe_flash_player.so /usr/lib/kde4/
```

***_The final slash is very important._*** If you leave it off, you will be linking the library to kde4. Hopefully, you will get a nasty error message when you try to do that. *You should.*

If you have sound, but still don't have sound in YouTube, something else is wrong. Try purging instead of uninstalling Adobe Flash Player. Also, make sure you purge the open source version of flash.

```
sudo apt-get purge flashplugin*
```

The asterisk (or some call it a star) makes flashplugin a regular expression, so that APT will search for packages containing the word or string "flashplugin."
If you used flash* instead, it would have removed every installed package containing "flash," and there are other packages that use the word.
To be certain what APT will do when using a regular expression, add -s to the command like this:

```
sudo apt-get purge flashplugin*
```

You should be able to use that with any apt-get command.

If you are just bored or frustrated, try this one for fun. "This APT has Super Cow Powers." :P

apt-get moo

---

### Post by MoebusNet on 2013-05-01
Since Firefox is at version 20 now, this thread may be moot.

---

