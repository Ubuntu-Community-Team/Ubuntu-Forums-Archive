---
title: "Ubuntu Dock, Dash to Dock and Dash to Panel etc"
date: 2017-09-08
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-08
Installed a fresh copy of Ubuntu yesterday (couldn't stay away from experimenting). Firefox is still 50, and gnome shell extensions cannot be installed without chrome-gnome-shell, so first tried the default Software. It didn't have it, so installed Synaptic from the terminal. This time universe was enabled by default. Installed Dash to Dock, and that made a mess of docks. Rebooted, but the mess was still there. (1st screeny on the left). Installed Dash to Panel, and got 3 docks. Checked if I can uninstall Ubuntu Dock, to find that, if I do that, Ubuntu Desktop would also go away. 

Today, when I booted Ubuntu, Dash to Panel is there, and the mess is gone, (I haven't upgraded the system yet) but Ubuntu Dock is enabled, and not showing. (2nd screeny) It being an extension, and enabled, there is a worry that it might come back and mess up, meaning a permanent bug. If the devs can make it so, once a user installs another panel, Dash to Panel or whatever, the default Ubuntu Dock gets disabled, would be nice.

*All this on default Ubuntu (Wayland).*

---

### Post by amano on 2017-09-08
sudo apt purge ubuntu-dock ?

---

### Post by Perfect Storm on 2017-09-08
Disable ubuntu dock extension: [https://extensions.gnome.org/extension/1290/disable-ubuntu-dock/](https://extensions.gnome.org/extension/1290/disable-ubuntu-dock/)

I haven't tried it, so let us know.

---

### Post by Rifester on 2017-09-08
My system is broken due to the new dock.   The Ubuntu Dock has never functioned for me.  I can't even open Displays in the settings (it just closes Settings). I originally had Dash to Dock installed but now it has issues as well.   Currently running Dash to Panel and will probably have to re-install if I want to test the new dock/settings.  It appears that running Gnome extensions outside of what is pre-installed is going to be a bad idea.

---

### Post by Chanath on 2017-09-08
[COLOR=#000000]sudo apt purge ubuntu-dock would uninstall Ubuntu Desktop.

How about testing on bare metal?
[/COLOR]

---

### Post by Chanath on 2017-09-08
> **Rifester said:**
> It appears that running Gnome extensions outside of what is pre-installed is going to be a bad idea.

Pre-installed unmovable extensions appear to be bad. Extensions should be open to all Gnome-shell users, even those from other distros.

---

### Post by Chanath on 2017-09-08
> **Artificial Intelligence said:**
> Disable ubuntu dock extension: [https://extensions.gnome.org/extension/1290/disable-ubuntu-dock/](https://extensions.gnome.org/extension/1290/disable-ubuntu-dock/)

I haven't tried it, so let us know.

I have tried both Ubuntu Dock related extensions, [https://ubuntuforums.org/showthread.php?t=2370670](https://ubuntuforums.org/showthread.php?t=2370670)

---

### Post by Frogs Hair on 2017-09-08
Spent a long time to trying the completely remove/purge and reinstall extensions including ubu-dock, dash-to-dock and honestly reinstalling was quicker.  I setup ubu-dock size and color with the following extension and haven't touched it since.   

[https://extensions.gnome.org/extension/1282/dock-settings/](https://extensions.gnome.org/extension/1282/dock-settings/)

---

### Post by Chanath on 2017-09-08
Looks like things are getting better. There is Dock separately in the new Settings, and Screen position in it - left, bottom and right. It also has Always show Dock, on/off. Right now, putting On doesn't bring it in, when Dash to Panel is installed and on, and that's good. UbuDock is enabled, though. Still doesn't work well with [https://extensions.gnome.org](https://extensions.gnome.org) - It shows ERROR there. Hope the devs could get everything fixed by the official release day.

---

### Post by Frogs Hair on 2017-09-08
The linked extension is now broken on my installation , but was able to remove it with no ill effects. Stay away , stay very far away. :p  

[https://extensions.gnome.org/extensi...dock-settings/]("https://extensions.gnome.org/extension/1282/dock-settings/")

---

### Post by Rifester on 2017-09-08
I'm giving up on trying to repair, time for a fresh install.

---

### Post by P-I H on 2017-09-08
These are my findings.
There are to many ways to manage extensions.
- In tweak-tool it's only possible to turn Extensions on and off, but there are no change for system extensions
- In the webpage [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/) you may turn on and off extensions and also install and uninstall extensions, except the system extensions
- I found a third alternative "Shell Extensions" here you may turn on and off extensions  and also change settings, but not on system extensions
- In Software you are able to install and I suppose uninstall extensions
- In Packages you are able to install and uninstall extensions, if you are able to find them

---

### Post by Chanath on 2017-09-08
Installed in another partition the default Ubuntu afresh. Here I won't install any Dash type or Panel type extensions, if at all only Hide Top Bar. I want to find out what happens to UbuDock. Right now, there is a mismatch of colouring; the top panel, which is default Gnome-shell, is now dynamic and takes the colour just below it. The Ubuntu default wallpaper has few colours, and they are taken by the top panel, making it quite pretty. (Unity Launcher also took the colours of the wallpaper.) Other than that, it takes the colour of the top panel of the window, when touched. That too is nice, but it hits the Ambiance theme. But, the UbuDock is not doing all that, yet. There'd be lot of catching-up work to do. Gnome and the extensions are done by others, who cannot be controlled.

The top panel colours and UbuDock colour don't match.

---

### Post by Frogs Hair on 2017-09-08
Being that new position settings were added to the ubuntu-dock today I think new features/settings are forth coming. I don't plan to corrupt or break it by using any related extensions. Good luck to those who do !

Edit: I have made some modifications in the dconf editor.

---

### Post by ventrical on 2017-09-09
> **Frogs Hair said:**
> Spent a long time to trying the completely remove/purge and reinstall extensions including ubu-dock, dash-to-dock and honestly reinstalling was quicker.  I setup ubu-dock size and color with the following extension and haven't touched it since.   

[https://extensions.gnome.org/extension/1282/dock-settings/](https://extensions.gnome.org/extension/1282/dock-settings/)

Like I said in another thread , fresh installs best way to go. It will break everytime you update/upgrade otherwise. I don't really consider breakage, especially when the theme is hard coded. 

Regards..

---

### Post by Chanath on 2017-09-09
You can't keep on installing afresh. In this one, I am going to leave as much as vanilla Ubuntu intact until the final release. Just update/upgrade. Next download will be the final one. But, I'll experiment with extensions, just to see what might be useful.

There are few problems, though. Below screeny. Something is covering the right top corner of Terminal. This happens only with the Terminal.

---

### Post by Frogs Hair on 2017-09-09
I have customized the theme and icons which requires the user themes extension as for the dock I'll use the dconf editor.

---

### Post by Chanath on 2017-09-09
[SIZE=2][FONT=arial]I have decided to keep it as much as in the vanilla form, but test most of extensions that might go against Ubuntu Dock system extension. I found one already other than those two with Ubuntu in their name. I'll check this some more, before naming it.[/FONT][/SIZE]:)

---

### Post by Chanath on 2017-09-09
You guys might find this extension interesting, [https://extensions.gnome.org/extension/1037/customcorner/](https://extensions.gnome.org/extension/1037/customcorner/)
I had the corners made hot by another very old script before, but this is more interesting.

---

### Post by BigCityCat on 2017-09-09
here is what I have learned based on upgrading from 17.04. Of course all the extensions were still installed and functioning. I had a message in the tweak tool that there was a problem with dash to dock all though it was working. There was a conflict though with ubuntu dock and it was giving me a weird applications grid bug. Also you could turn extensions off and on but it had no impact either way. here is what I did.
1. navigate to local/share/gnome-shell/extensions and delete all extensions
2. navigate to usr/share/gnome-shell/extensions and delete all extensions
3. open webroswer and go to gnome shell extensions website and install ubuntu dock settings
4. open synaptic and install the gnome-shell-extension that you want to use
5. open tweak tool and find ubuntu dock settings
6. set up the extensions you wish to use

note - you can't use synaptic on wayland so you will probably have to login to the x session

---

### Post by Frogs Hair on 2017-09-09
> [COLOR=#000000] open webroswer and go to gnome shell extensions website and install ubuntu dock settings[/COLOR]

This extension broke right after installed. I have noticed that ubu-dock,dash-to-dock,and ubuntu dock settings use an almost identical schema and all three are named dash-to-dock  this might account for the conflicts and breakage.

---

### Post by BigCityCat on 2017-09-09
> **Frogs Hair said:**
> This extension broke right after installed. I have noticed that ubu-dock,dash-to-dock,and ubuntu dock settings use an almost identical schema and all three are named dash-to-dock  this might account for the conflicts and breakage.

I think you may also be able to install this extension through synaptic. I think it is gnome-shell-extension-ubuntu-dock-settings or something like that. No i just checked, it's not there. Can you download and install it locally? here is the link.

[https://github.com/higgslagrangian/dock-settings/](https://github.com/higgslagrangian/dock-settings/)

---

### Post by BigCityCat on 2017-09-09
Just open gnome tweak after you download and install it from the file.

---

### Post by Frogs Hair on 2017-09-09
I can do all I want from the dconf editor, I'll wait and see what options the devs add to the ubu-dock settings.

---

### Post by Chanath on 2017-09-10
Few interesting things,

1) You can install Synaptic in Wayland and use it. Install from the terminal and start it from the terminal first time. Then it'd work normally.
2) Install chrome-gnome-shell from synaptic or terminal, so you can use Firefox to check Gnome extensions.
3) It maybe quite easy to remove Ubuntu dock, but don't know, if it'd come back after a dist-upgrade (1st screenshot on the left). The standard Dash would come back. 
4) Added Custom hotcorners to make my life easy. 
5) Installed Dash to Panel, and it worked quite nicely, bringing the Dash down, without the bugs that Ubuntu Dock add (2nd screenshot)

If this prevails, I can use the default Ubuntu for day to day work.:)

Sometimes funny things happen (see the 3rd screenshot) -- no icons in Nautilus. 
You can see that Synaptic is there, and no Dash on the left.

---

### Post by fthx on 2017-09-10
Come on it's so easy to remove ubuntu-dock, at least 4 solutions :
1) uninstall gnome-shell-extension-ubuntu-dock package (but it removes ubuntu-desktop metapackage, not a good thing)
2) create a void ubuntu-dock extension in your home folder which overrides the /usr/share one
3) install the Disable Ubuntu Dock extension
4) in /usr/share/gnome-shell/extensions , delete the ubuntu dock folder (but the dock will come back after each dock package update)

---

### Post by Chanath on 2017-09-10
> **fthx said:**
> Come on it's so easy to remove ubuntu-dock, at least 4 solutions :
1) uninstall gnome-shell-extension-ubuntu-dock package (but it removes ubuntu-desktop metapackage, not a good thing)
2) create a void ubuntu-dock extension in your home folder which overrides the /usr/share one
3) install the Disable Ubuntu Dock extension
4) in /usr/share/gnome-shell/extensions , delete the ubuntu dock folder (but the dock will come back after each dock package update)

Sure!:)
3) It maybe quite easy to remove Ubuntu dock, but don't know, if it'd come back after a dist-upgrade.

---

### Post by ventrical on 2017-09-10
> **Chanath said:**
> You can't keep on installing afresh. 

Oh yes I can.!! :)

---

### Post by Chanath on 2017-09-10
There is a pretty bad problem with rendering atm. Just can't use Nautilus without icons, so installed PCManFM to use a file manager with icons. Moving windows happens with slight jumps, Few days ago the movements were smoother. Getting worse?

---

### Post by ventrical on 2017-09-10
> **Chanath said:**
> There is a pretty bad problem with rendering atm. Just can't use Nautilus without icons, so installed PCManFM to use a file manager with icons. Moving windows happens with slight jumps, Few days ago the movements were smoother. Getting worse?

Try installing extremetux racer and see if it  sort of locks up your graphics. It did for me in unity. Removed dash2dock and still no fix.

---

### Post by dino99 on 2017-09-10
> **Frogs Hair said:**
> This extension broke right after installed. I have noticed that ubu-dock,dash-to-dock,and ubuntu dock settings use an almost identical schema and all three are named dash-to-dock  this might account for the conflicts and breakage.

That is a serious confusing design; please report (if not already done) :confused:

---

### Post by Chanath on 2017-09-10
> **ventrical said:**
> Try installing extremetux racer and see if it sort of locks up your graphics. It did for me in unity. Removed dash2dock and still no fix.


There is nothing wrong with Unity on 17.10.  Its working with a full blast of Compiz on it. Its full upgraded and has kernel 4.13.1 in it. I haven't had any problems with any apps. No problem whatsoever!


However I try to give a chance to vanilla Ubuntu, it gives trouble. That's why I said its an experiment. Ubuntu Dock is a fork of dash to Dock, but by trying to block certain original settings, its becoming a bug, rather than a feature. Dash to Dock is still there in gnome extensions, so even though Didier says it can be easily interchanged, it won't. Didier says,

> You may notice that this release is very similar to the original Dash to Dock but with less features, no settings panel, and different defaults. This is on purpose, because we wanted to bring a simpler dock experience into GNOME Shell for Ubuntu users, and we didn't want to expose all of the settings that the original Dash to Dock had.
Some settings will be available through an add-on to the Settings program for Ubuntu, but not all. For those who do want all the available options, the original Dash to Dock extension is fully compatible with this dock. Simply install it from GNOME Extensions like normal.
[https://github.com/micheleg/dash-to-dock/tree/ubuntu-dock](https://github.com/micheleg/dash-to-dock/tree/ubuntu-dock).

Michele Gaio had enough time to fine tune his Dash to Dock, but Ubuntu Dock is an ongoing experiment. Even Tweaks (JBicha maintains it) can't disable Ubuntu Dock. Anyway, we'd await positive changes.

---

### Post by P-I H on 2017-09-10
I have no problems with Ubuntu Dock. Basic settings are available in Settings/Dock. In case you want all possible settings, install the extension Ubuntu Dock Settings.
The extension UbuntuAppIndicators also works very well.
The picture is from an installation of today's ISO.

---

### Post by Chanath on 2017-09-10
> **P-I H said:**
> I have no problems with Ubuntu Dock. Basic settings are available in Settings/Dock. In case you want all possible settings, install the extension Ubuntu Dock Settings.

I know about these extensions, but I don't want to use them. If there is a system extension, I'd like it to be user friendly. And, I'd like the said Tweaks to works as mentioned in Didier's Github page. He is the person, who had created this Ubuntu Dock. There should be coordination between Ubuntu Dock and Tweaks. 17.10 is not yet released officially, so they are at the moment expectations. 

I have reinstalled Ubuntu 17.10 again. The rendering is okay atm.

---

### Post by Chanath on 2017-09-10
Even more interesting...
2nd pic after rebooting...but, where is Ubuntu Dock...?

---

### Post by Chanath on 2017-09-10
So, installed Dash to Panel...maybe, the Dock bugs would be over...

---

### Post by Chanath on 2017-09-11
I had to install 17.10 daily again on another matter, and it gave me a chance to check something else. I wanted to use Dash to Panel, and disable Ubuntu Dock, so it won't leave any residue, when Overview is activated. Earlier tries with different extensions left a residue, or even Dash to Dock. Now, without using any extensions especially to disable Ubuntu dock worked. I haven't installed Tweaks yet in this new installation, as Tweaks cannot disable system extensions yet. (I will install Tweaks later anyway to change icons etc.) Dconf editor is also not installed. 

The 1st screenshot shows that system extensions are intact [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/)
They are not touched in /usr/share/gnome-shell/extensions too. (2nd screenshot) 
3rd screenshot shows that there is no residue of Ubuntu dock. I have to wait few upgrades and the final dist-upgrade to see, if this state would prevail. :) [URL="https://extensions.gnome.org/local/"]


[/URL]

---

### Post by Perfect Storm on 2017-09-12
Dash to Dock seems to be broken atm. The 'Show applications' do nothing now, and it says error on the extension site. I can't even disable it.

---

### Post by ventrical on 2017-09-12
> **Artificial Intelligence said:**
> Dash to Dock seems to be broken atm. The 'Show applications' do nothing now, and it says error on the extension site. I can't even disable it.

Thats exactly what I got about 6 weeks ago!! I filed a bug but forget.. uh jbicha adressed it I think. I forget the workaround atm..

Regards..

---

### Post by P-I H on 2017-09-12
Ubuntu Dock with the extension "Ubuntu Dock Settings" works great on my system. You get about the same settings as in "Dash to Dock"
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.12.0-13-generic x86_64 bits: 64
           Desktop: Gnome 3.25.91
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.70 date: 07/27/2017
CPU:       Octa core AMD Ryzen 7 1700 Eight-Core (-HT-MCP-) cache: 4096 KB
           clock speeds: max: 3724 MHz 1: 3724 MHz 2: 3724 MHz 3: 3724 MHz
           4: 3724 MHz 5: 3724 MHz 6: 3724 MHz 7: 3724 MHz 8: 3724 MHz
           9: 3724 MHz 10: 3724 MHz 11: 3724 MHz 12: 3724 MHz 13: 3724 MHz
           14: 3724 MHz 15: 3724 MHz 16: 3724 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380]
           Display Server: wayland (X.Org 1.19.3 ) driver: amdgpu
           Resolution: 1920x1200@59.88hz
           OpenGL: renderer: AMD Radeon R9 380 Series (AMD TONGA / DRM 3.15.0 / 4.12.0-13-generic, LLVM 5.0.0)
           version: 4.5 Mesa 17.2.0
Audio:     Card-1 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-2 Advanced Micro Devices [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380]
           driver: snd_hda_intel
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.12.0-13-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
            
Drives:    HDD Total Size: 490.1GB (12.3% used)
           ID-1: /dev/nvme0n1 model: N/A size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 57G (26%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 40.0C gpu: 51.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 661 fan-2: 599 fan-3: 879 fan-4: 0 fan-5: 671
Info:      Processes: 372 Uptime: 1:59 Memory: 2203.2/16057.4MB
           Client: Shell (bash) inxi: 2.3.37 
p-i@pi-MS-7A34:~$
```

---

### Post by Chanath on 2017-09-12
> **P-I H said:**
> Ubuntu Dock with the extension "Ubuntu Dock Settings" works great on my system. You get about the same settings as in "Dash to Dock"

The idea is that Ubuntu dock should not bring in any bugs that might be already in Dash to dock, and/or allow some outside extension break it. If a system extension can be meddled that way, its a risk.

---

### Post by Perfect Storm on 2017-09-13
> **ventrical said:**
> Thats exactly what I got about 6 weeks ago!! I filed a bug but forget.. uh jbicha adressed it I think. I forget the workaround atm..

Regards..

If you at a time remembering it, I'll gladly know the fix.

---

### Post by Perfect Storm on 2017-09-14
> **Artificial Intelligence said:**
> If you at a time remembering it, I'll gladly know the fix.

I have now tried to remove Dash to Dock from ~/.local/share/gnome-shell/extension then I can removed it. But reloading a new Dash to Dock from Gnome Extension website and the same thing happens to Dash to Dock again.

---

### Post by dino99 on 2017-09-14
There is a gschema conflict, which need a fix (coming soon). The link below propose a workaround ppa.
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1711617](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1711617)

---

### Post by Chanath on 2017-09-14
If Ubuntu needs to use a fork of dash2dock, Ubuntu should fork it in such a way, that dash2dock wouldn't trouble Ubuntu dock. You can't have the cake and eat it. Maybe, the developer(s) should look at the Zorin's forking gnome extensions and making them system. The idea there is either use mine, or go away. Of course, Ubuntu would take that stand, as it'd alienate users. 

Users know, Gnome has extensions, and the users love freedom. So, Ubuntu is sort of up against the wall with Gnome coming in. Giving an alternative, saying either use Ubuntu default or install gnome-session package, if you want the "vanilla" experience is asking for trouble. You can read about this 2-way method here, [https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/](https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/)

---

### Post by Frogs Hair on 2017-09-14
> **dino99 said:**
> There is a gschema conflict, which need a fix (coming soon). The link below propose a workaround ppa.
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1711617](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1711617)

Thanks for the link. I noticed this after a few days of experimenting dash-to-dock and related extensions.

[https://ubuntuforums.org/showthread.php?t=2370853&page=3](https://ubuntuforums.org/showthread.php?t=2370853&page=3)

---

### Post by P-I H on 2017-09-14
The "Ubuntu Dock" with "Ubuntu Dock Settings" gives the same experience as Dash to Dock.

From the description of the "Ubuntu Dock Settings"
"Ubuntu Dock Settings by higgslagrangian
The purpose of this extension is simply to customize the Ubuntu Dock. It does not provide any extra functionality; when opening the settings, it will simply show the settings offered by Ubuntu Dock itself."

---

### Post by Chanath on 2017-09-14
If there is an app, Ubuntu Dock Settings outside Ubuntu, then what the use of a system extension called Ubuntu Dock? Is it just to mimic Unity Launcher?
There is also a "Disable Ubuntu Dock" too, even before 17.10 is officially released. There is also another older extension, created around 2016, which would also disable Ubuntu Dock. Dash to Dock would also disable Ubuntu Dock with few up and down installs. Ubuntu Dock would show that its enabled, but won't be shown and that without Dash to Dock.

---

### Post by P-I H on 2017-09-14
The Ubuntu Dock Settings extension only enables available settings in Ubuntu Dock, that isn't enabled as standard. You need Ubuntu Dock to be able to use Ubuntu Dock settings.

---

### Post by Chanath on 2017-09-14
> **P-I H said:**
> The Ubuntu Dock Settings extension only enables available settings in Ubuntu Dock, that isn't enabled as standard. You need Ubuntu Dock to be able to use Ubuntu Dock settings.

Ubuntu Dock Settings extension created by someone outside Ubuntu, meaning Ubuntu Dock, which is a system extension, is already compromised. Only 2 such extensions at the moment and one quite old one, that can compromise the system extension. A system default app is a system default app, should not be that easily played around by anyone. All these 6 years, Unity's top panel could not be compromised, even Ubuntu Tweak couldn't, or later Unity Tweak couldn't, or was not allowed to.

This system extension, Ubuntu Dock can be easily kicked out. That's not good for the distro called Ubuntu, but maybe good enough for users. Ubuntu must be Ubuntu, and if it has to mimic Unity, then it must have a launcher, which is completely Ubuntu, a fork or not a fork, and cannot be compromised. Even, before the Ubuntu 17.10 is released, its flagship launcher is broken into.

If you look at #37, you'd see that Ubuntu Dock is not showing, even with all the Ubuntu Dock files are intact. And, I am not a coder. I also have Unity Greeter, which most people said won't work with Gnome.

---

### Post by Perfect Storm on 2017-09-15
> **Artificial Intelligence said:**
> I have now tried to remove Dash to Dock from ~/.local/share/gnome-shell/extension then I can removed it. But reloading a new Dash to Dock from Gnome Extension website and the same thing happens to Dash to Dock again.

Removed it again and downloaded once more. Now it works! Strange...

---

### Post by ventrical on 2017-09-16
> **Chanath said:**
> If there is an app, Ubuntu Dock Settings outside Ubuntu, then what the use of a system extension called Ubuntu Dock? Is it just to mimic Unity Launcher?


In the thread of conventional wisdom - yes. For now at least.  The  ..uh .. aspiration... if I may .. is to  incorporate  some of the solid ideas of unity7  into the gnome project. This will not happen while there is a conflagration between all the docking and gnome menu issues.We will get a  good release for 17.10 but the default may be somewhat restricted. This may spell good news for QA testers as it may extend the life and usefulness of unity7 into the 18.04 cycle. The other good news is that it is not unity7 affecting gnome-default...

 If we embrace the current "mock" dash and test it , it may be happen-chance that developers will work the harder at fixing it and it will have more unity7 DNA incorporated into it.

regards..

---

### Post by Chanath on 2017-09-16
> **ventrical said:**
> In the thread of conventional wisdom - yes. ....

 If we embrace the current "mock" dash and test it , it may be happen-chance that developers will work the harder at fixing it and it will have more unity7 DNA incorporated into it.

regards..

Greetings!

It won't be that easy, when the original work is someone else's, and who had been in the scene, before the idea of making default Ubuntu, Gnome. 
As dash2dock is still out there as an independent extension, and also no one can really stop that developers thinking for the future, Ubuntu dock is going to have a hard time.

---

### Post by mc4man on 2017-09-16
Not sure what the issue is here. This commit is what allowed ubuntu to install the dock on the image (system
[https://github.com/micheleg/dash-to-dock/commit/4dd565dad920ce44303635b550a39bbdbe34fb70](https://github.com/micheleg/dash-to-dock/commit/4dd565dad920ce44303635b550a39bbdbe34fb70)

And ubuntu could care less if users want to use the orig., from /usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com/README.md

> This dock is a fork of the original [Dash to Dock]([https://github.com/micheleg/dash-to-dock/](https://github.com/micheleg/dash-to-dock/)) (master Branch) extension for GNOME. The original extension was very powerful, but we wanted a simpler, more integrated experience for general Ubuntu users. You can install the original extension for more (but not officially supported) features.

---

### Post by ventrical on 2017-09-16
> **Chanath said:**
> Greetings!

It won't be that easy, when the original work is someone else's, and who had been in the scene, before the idea of making default Ubuntu, Gnome. 
As dash2dock is still out there as an independent extension, and also no one can really stop that developers thinking for the future, Ubuntu dock is going to have a hard time.

Well then , of course there is that reality that you mention.  A larger group of devs and hacks want to kill unity7 altogether so we are beyond conventional wisdom here - so - as it stands - we are not getting a unity mock up , but, rather a gnome mock facsimile . So now we know  why unity7 will be included in 18.04 because it will be needed for a rolling QA development cycle. So here again .. it comes down to what resources in the community are willing to commit. So veteran QA testers might stop and think .. do I want to spend 10 hours testing gnome-shell or 10 hours testing unity7 alongside gnome or can I spend 20 hours a week and do both?

regards..

---

### Post by ventrical on 2017-09-16
> **mc4man said:**
> Not sure what the issue is here. This commit is what allowed ubuntu to install the dock on the image (system
[https://github.com/micheleg/dash-to-dock/commit/4dd565dad920ce44303635b550a39bbdbe34fb70](https://github.com/micheleg/dash-to-dock/commit/4dd565dad920ce44303635b550a39bbdbe34fb70)

And ubuntu could care less if users want to use the orig., from /usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com/README.md

> 
but we wanted a simpler, more integrated experience for general Ubuntu users. 


I am just curious as to how they arrived at this declaration as unity7 was the more integrated experience with less clicks.

---

### Post by Chanath on 2017-09-16
> **ventrical said:**
> Well then , of course there is that reality that you mention.  A larger group of devs and hacks want to kill unity7 altogether so we are beyond conventional wisdom here - so - as it stands - we are not getting a unity mock up , but, rather a gnome mock facsimile . So now we know  why unity7 will be included in 18.04 because it will be needed for a rolling QA development cycle. So here again .. it comes down to what resources in the community are willing to commit. So veteran QA testers might stop and think .. do I want to spend 10 hours testing gnome-shell or 10 hours testing unity7 alongside gnome or can I spend 20 hours a week and do both?

regards..

I think killing Unity for any reason is foolish after developing it for last 6+ years. That the Unity look *has to be* in the next Ubuntu 17.10 as default is *not *a devs' decision, but a company decision. 17.10 release is a test, not for us, but for the devs. If the devs can't come up with a viable Unity look, the whole Gnome idea would be taken off. You couldn't break the top bar of Unity, also one tweak, that could play around with the Unity launcher was taken into fold. This can't be done with gnome extensions. No managing director would allow his products to be played around by outsiders. For the moment, the devs are allowed to make use of the dash2dock, but they have to come out with a dock that's typically Ubuntu for 18.04 LTS. You can't give out an LTS with a launcher that can be broken into. That goes for the top panel too.

---

### Post by deadflowr on 2017-09-16
> I am just curious as to how they arrived at this declaration as unity7 was the more integrated experience with less clicks.

I think they refer to a more integrated experience versus normal gnome shell.
I doubt unity figures into it.

---

### Post by mc4man on 2017-09-16
> **deadflowr said:**
> I think they refer to a more integrated experience versus normal gnome shell.
I doubt unity figures into it.
That's certainly what they meant.
I'd expect a fair amount of tweaking/bug fixing to improve user experience & performance on the Desktop, something that has been lacking in Ubuntu for the last couple of years as many devs/employees were occupied elsewhere

---

### Post by ventrical on 2017-09-16
> **deadflowr said:**
> I think they refer to a more integrated experience versus normal gnome shell.
I doubt unity figures into it.

Hi Deadflowr,

  I guess I meant to say;  how do they collect their statistics to make their declarative on "general ubuntu users" because I have not seen any solid data that suggests that "general ubuntu users" would prefer a gnome/unity mock up. I can state definitively  (using ubuntu_forums as a QA data test model) that , on average, "general ubuntu users" would comprise greater than 60%+_ end_user space on unity/unity7.

So, going a little off topic, we would have to assume that since gnome-shell is going to be default for 17.10/18.04 it would bring more testing and general end_user resources to bear on gnome/wayland and much less on unity and the other distros in ubuntu exclusively. However I DO recognize that Fedora is very popular with it's gnome/wayland DE but  it is beyond the pale to use those numbers and factor them into an ubuntu style concept!

 Allow me to say that I like to think that most of my contributions are done in the spirit of community and building on the themes, concepts and directions of the founders but, no matter how much devotion and dedication to a new theme or new default DE , we cannot deny the math, the numbers, that  are pointing in a different direction and so we cannot exclude that large base of volunteer QA techs and the current "general user database" which is too large to let go unattended to, hence why unity7 will be in 18.04. If QA is to have any impact on the new default , whether on the QA tracker or in development version, then developers have to look at the numbers realistically. I am not critisizing  anyones coding or contributions, I am just saying , look at the numbers from an end_user perspective, really! and then stand me corrected :)

Regards..

edit: side reference

> 
Numbers, on the other hand, do not lie. According to the poll, 63% of  the voters agreed that Unity is the best desktop (with an understanding  that the poll was run on a Ubuntu-centric site).
This has  surprised a lot of people, but I would argue that it shouldn't. Why?  Unity has been around for a while now, and it's had plenty of time to  evolve and get things right. The initial release was 2010, and the Unity  we have now is not the Unity we had then. Users have had plenty of time  to acclimate. The HUD, the Dash, Scopes &#8212; they all work in a harmony  that most desktops can't replicate.


[http://www.techrepublic.com/article/the-science-behind-the-ebb-and-flow-of-ubuntu-unitys-popularity/](http://www.techrepublic.com/article/the-science-behind-the-ebb-and-flow-of-ubuntu-unitys-popularity/)

---

### Post by ventrical on 2017-09-16
> **mc4man said:**
> That's certainly what they meant.
I'd expect a fair amount of tweaking/bug fixing to improve user experience & performance on the Desktop, something that has been lacking in Ubuntu for the last couple of years as many devs/employees were occupied elsewhere

There's the rub. Integrating an unity idea does not necessarily mean that they have  to merge an unity concept. it's going to  be fun to watch all this take place ...

---

### Post by mc4man on 2017-09-16
> **ventrical said:**
> 

  I guess I meant to say;  how do they collect their statistics to make their declarative ... 
Just my viewpoint..
The move to Gnome was purely financial, making for a good user experience is ingrained & a little financial

---

### Post by ventrical on 2017-09-16
> **mc4man said:**
> Just my viewpoint..
The move to Gnome was purely financial, making for a good user experience is ingrained & a little financial

Of course I realize that absolutely.. but I wasn't questioning your viewpoint, I was questioning  context from the link you provided as to how the devs/canonical derive their stats - so , for all those who had worked devotedly on unity, and they get tossed and we think it won't affect ubuntu as a whole?  I can see it as perhaps  a percursor to seconding all the ubuntu DE derivatives to the community eventually allowing canonical to retire it's support completely.  Stay tuned .. :)

---

### Post by Chanath on 2017-09-16
My viewpoint is that the devs' *have *to make 17.10 look like Unity, the launcher and the top panel. That's a MD's decision. A company decision. And, both those have to be more Ubuntu, and cannot be played around by outsiders. The Dash2dock fork is for the 17.10, the intermediate release, but not for the LTS release. The LTS release must be there for next 5 years and it should be pure Ubuntu. So, by that time, the devs have to create a dock and a top panel.

You can't just say, "hey if you don't like the default Ubuntu, go and install gnome-session." ([https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/](https://didrocks.fr/2017/09/11/ubuntu-gnome-shell-in-artful-day-11/)) 

Ubuntu is Ubuntu, it can have derivatives, but not an alternative.

---

### Post by P-I H on 2017-09-16
I have been using Unity since it was first available.
To customize Unity I needed two packages, Unity Tweak tool and Compiz config manager. Especially Compiz Config Manager wasn't the most stable package.
[https://askubuntu.com/questions/121996/how-can-i-fix-a-broken-desktop-due-to-compiz](https://askubuntu.com/questions/121996/how-can-i-fix-a-broken-desktop-due-to-compiz)

In my view Ubuntu Artful  Aardvark is more stable. I need the Ubuntu Dock Settings and also gnome-tweak-tool for some minor changes, but these are quite easy to understand and use.

In Unity I also installed indicators to get weather information and information about the health of the computer. The gnome extensions to support this is also easy to understand and use. The Indicators that support Steam and Dropbox are installed automatically. Notifications for Spotify works excellent and also allow to skip forward and backward in the playlist.

---

### Post by mc4man on 2017-09-16
> **ventrical said:**
>  I was questioning  context from the link you provided as to how the devs/canonical derive their stats - :)

Not sure there are any stats to date, as far as Canonical's use of focus groups, who knows, those results in the past never jived with me anyway..

I think some things are just plain obvious.

I'll give you a quote from a report I closed as invalid (the causative issues are still valid, the bug's suggestion wasn't really..
> I understand and agree gnome-shell's animations are poor in places. Sub-
optimal performance of the shell in general makes them sometimes miss
frames and stutter. Plus the chosen easing curves are also questionable
(bug 1713021).

But these are all fixable bugs. I would be disappointed if we disabled
animations to work around the problems rather than fixing the problems.
(Daniel van Vugt <daniel.van.vugt@canonical.com>

So I'd see "general ubuntu users" as any run of the mill user & what they get on the default install thru normal usage. In that case any engaged dev can pick up on the problems or deficiencies of gnome-shell.

---

### Post by Chanath on 2017-09-16
> **mc4man said:**
> 

So I'd see "general ubuntu users" as any run of the mill user & what they get on the default install thru normal usage. 

Too bad that the devs think "general ubuntu users," as the type, who'd use something without (much) thinking, like those who use cameras just to point and shoot. There'd be quite a few "derivatives" of the default Ubuntu, before long. With Gnome-shell and with some other system extensions (Zorin) and with only Gnome-flashback and so on.

(BTW, I am writing from Ubuntu-Gnome 17.10, which can be just made into an installable live iso. And, such an iso would be a pure gnome based on Ubuntu 17.10. This can be done after the 17.10 final release day, even if Ubuntu-Gnome 17.10 final won't be released officially. The creator/uploader of that iso doesn't even have to maintain it, for all packages would be maintained by Ubuntu itself, as Ubuntu default is now Gnome.)

---

