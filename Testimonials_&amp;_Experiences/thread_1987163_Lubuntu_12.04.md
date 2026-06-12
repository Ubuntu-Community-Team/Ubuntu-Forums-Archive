---
title: "Lubuntu 12.04"
date: 2012-05-26
forum: Testimonials &amp; Experiences
---

### Post by mikewhatever on 2012-05-26
This is going to be. hopefully, [s]a few weeks[/s] one week long ;) experience of running Lubuntu 12.04 on an old computer. The machine in question is a Pentium 4 with 640MB of PC133 RAM and Radeon 9200se graphics. I don't know how old the beast is, but the lack of an integrated ethernet port and USB1 only, as well as the rest of the hardware, suggest it could be a decade old, or thereabout.

**Day One**

_Installation_

I first tried installing Lubuntu 12.04 on an even older Pentium 3 with 384MB of RAM, which didn't work. The installer window would close when copying files, even with a pre-made swap partition.
The installation on the Pentium 4 was fast and uneventful. I've chosen the simplest partition layout: about 79300MB for root and 700 for swap.

_First Impression_

Lubuntu runs very well. It's not memory hungry, so that there is enough RAM left to run applications. 112MB of RAM is what's used to boot.
The default combination of grey and blue is depressing. That might be due to the old CRT monitor, but I like more color and contrast, and changed the theme, the icons and the wallpaper right away.


_Stability_

First and foremost, stability seems to be an issue. I get frequent crashes of the notification daemon, lxpanel, lxkeymap, gnome-mplayer, ...and dutifully send crash reports. Is it because Lubuntu 12.04 is not an LTS, or is that why it's not an LTS?

_Chromium_

The default web browser is an outdated Chromium 18, even after installing all available updates. Google Chrome 19 has been released a few weeks back, and has been updated once already. There seems to be no sign of an update for Chromium.
This is more serious then I thought. The problem was first noticed in February, and is still unresolved. Here is the explanation by Micah Gersten, the maintainer of Chromium: [http://askubuntu.com/a/105487](http://askubuntu.com/a/105487)

_Mplayer2_

Mplayer (Gnome-Mplayer) doesn't work at all, no matter what I try playing. There seems to be a compilation problem. 
Bug report: [https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/976465](https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/976465)

Mplayer2 is, apparently a fork of mplayer with improvements. Purging mplayer2 and gnome-mplayer, and then installing mplayer and gnome-mplayer made everything work. The browser plugin, gecko-mediaplayer gets removed in the process, and needs to be reinstalled as well.

**Day Two**

_Multimedia Codex_

One way to get codex is to install the lubuntu-restricted-extras package. That would give you a lot of stuff apart from codecs, for example, Adobe Flash, unrar, MS fonts, etc. I didn't want any of that, so instead, I've only installed the Bad, the Ugly and FFMPEG gstreamer plugins:
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
gstreamer0.10-ffmpeg

_Keyboard Layouts_

That's done by appending a line to the .bashrc. Mine looks like this: setxkbmap -option grp:alt_shift_toggle "us,il,ru". Reload with "source .bashrc", and it starts working immediately. The layout switcher applet can be added to the panel by right clicking, "Add/Remove panel items", "Keyboard Layout Switcher".

_Samba_

That was just the matter of installing samba, uncommenting a few lines in the config file, and then reloading smbd. I've used this for reference: [http://mostlylinux.wordpress.com/network/samba/](http://mostlylinux.wordpress.com/network/samba/).

_Keyboard Shortcuts_

There are quite a few of them pre-defined in .config/openbox/lubuntu-rc.xml.
alt+f1 opens the menu
ctrl+alt+d opens the file browser
Super+d minimizes all windows
ctrl+alt+del brings up the task manager
ctrl+alt+l locks the screen
alt+PrintSCRN takes a screenshot

There was not shortcut to launch the web browser (possibly because Chromium got removed), so I've added the following to .config/openbox/lubuntu-rc.xml:
```
<!-- Launch a Web Browser on Super + W-->
    <keybind key="W-W">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Web Browser</name>
        </startupnotify>
        <command>x-www-browser</command>
      </action>
    </keybind>

```

openbox --reconfigure to reload

**Day Three**

_OpenBox_

OpenBox is the window manager in Lubuntu. It's one of the lightest I've used, eating up the ridiculous 8MB of RAM and hardly any CPU cycles. It's very fast, very cool, and stable too. It doesn't have rounded corners, 3d transition effects, or transparency, but it gets the job done, which is perfect for an old computer.

_Suspending and Hibernating_

Suspending works like a Swiss clock, but hibernating leaves the pci wireless card unusable.

**Day four**

_Graphics_

[Radeon 9200se is an entry level graphics card from 2003]("https://en.wikipedia.org/wiki/Radeon_R200"). It is no longer supported buy AMD, but the default open source driver does a decent job. Glxgears shows 75FPS, and there haven't been any xserver crashes or lockups. Both LXDE and OpenBox are [gaming friendly]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_precise_desktop&num=1"), and I've been playing WarZone for a considerable part of the day.

**Conclusion**

Well, I rather liked Lubuntu. It's an old school distro with config files for editing the menu or keyboard shortcuts, but it's lean and fast. It would have been a perfect fit for this old machine for the next five years, if only it had been more stable and had a longer support cycle. As is, it feels a beta that needs a liitle more time to mature.
(Note: Lubuntu 12.04 is not an LTS. It's a regular release with 18 months of support.)

---

### Post by Bouvet on 2012-05-26
I just installed Lubuntu on a VirtualBox today.
Granted the PC I uploaded it with is a Pent-Dual-Core, 6 GB, 64-bit Dell,
but I'm looking forward to test driving Lubuntu. 
Keep us all updated on your results.

---

### Post by MG&amp;TL on 2012-05-26
> **mikewhatever said:**
> This is going to be. hopefully, a few weeks long experience of running Lubuntu 12.04 on an old computer. The machine in question is a Pentium 4 with 640MB of PC133 RAM and Radeon 9200se graphics. I don't know how old the beast is, but the lack of an integrated ethernet port and USB1 only, as well as the rest of the hardware, suggest it could be a decade old, or thereabout.


General observations

Lubuntu runs very well. It's not memory hungry, so that there is enough RAM left to run applications. 112MB of RAM is what's used to boot.

The default combination of gray and blue is depressing. I've changed both the theme and the icons right away.

Problems

First and foremost, stability seems to be an issue. I get frequent crashes of the notification daemon, lxpanel, lxkeymap etc, and dutifully send crash reports. Is it because Lubuntu 12.04 is not an LTS, or is that why it's not an LTS?

The default web browser is an outdated Chromium 18, even after installing all available updates. Google Chrome 19 has been released a few weeks back, and has been updated once already. There seems to be no sign of an update for Cromium.

Playing HTML5 videos in Chromium is flacky. Any attempt to resize the player window crashes the player. The same video does not crash in Firefox, even fullscreen. Needless to say, the computer is not powefull enough to play fullscreen videos in a browser (it becomes a slideshow), so I've downloaded the 360p webm file with the intention of playing it in mplayer. That didn't work at all, not sure why.

 The good points are good, so I won't comment on those. ;)

-icons-fair enough-personal choice. I quite like the default theme though.

-crashes. The programs we have most problems with are the notification daemon, and lxpanel. We're not always entirely sure what's going on, but we do our best. On a side note, it's nothing to do with LTS. We're quite a small team (4 or 5 active devs last time I checked), so we just don't have the manpower to put all of the packages back on previous releases for five years.

-Chromium. We rely on ubuntu for chromium, I think you'll find the same one in the repos of Ubuntu.

Good review, hope it serves your machine well.

---

### Post by 2F4U on 2012-05-26
> First and foremost, stability seems to be an issue. I get frequent  crashes of the notification daemon, lxpanel, lxkeymap etc, and dutifully  send crash reports.

I am running Lubuntu 12.04 since it was released on a really old  ThinkPad X31 (8 years old) and my experience is the exact opposite.  Lubuntu runs very stable and I had no crashes at all.

> The default web browser is an outdated Chromium 18, even after  installing all available updates. Google Chrome 19 has been released a  few weeks back, and has been updated once already. There seems to be no  sign of an update for Cromium.

One of the first things I did was to replace Chromium with Firefox. With  respect to resource usage there seems to be not much of a difference,  but Firefox receives regular updates and I don't like Chromium.

---

### Post by summerbuntu on 2012-05-26
Have you compared it to an installation of Xubuntu?  Overall, I have had better success with Xubuntu.

---

