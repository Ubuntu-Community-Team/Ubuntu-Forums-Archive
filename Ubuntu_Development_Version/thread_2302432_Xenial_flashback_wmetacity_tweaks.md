---
title: "Xenial flashback w/metacity tweaks"
date: 2015-11-10
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-11-10
I really hadn't followed the flashback session much since Trusty other than playing just a teeny-tiny bit to make sure it still existed, but towards the end of the Wily cycle I noticed some fairly significant changes coming to Xenial in September and October on [the mailing list]("https://mail.gnome.org/archives/gnome-flashback-list/") ............... fast forward - still a nice light install on top of an Ubuntu Xenial install:

```
lance@lance-AMD-desktop:~$ **sudo apt-get install gnome-panel**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-panelapplet-5.0 gnome-applets gnome-applets-data
  gnome-flashback gnome-flashback-common gnome-media gnome-panel-data
  gnome-session-flashback gstreamer0.10-gconf gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x
  indicator-applet-complete libcpufreq0 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libpanel-applet0 metacity
Suggested packages:
  tomboy evolution-common desktop-base libvisual-0.4-plugins
  gstreamer0.10-tools gnome-control-center
The following NEW packages will be installed:
  alacarte gir1.2-panelapplet-5.0 gnome-applets gnome-applets-data
  gnome-flashback gnome-flashback-common gnome-media gnome-panel
  gnome-panel-data gnome-session-flashback gstreamer0.10-gconf
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x indicator-applet-complete
  libcpufreq0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libpanel-applet0 metacity
0 upgraded, 21 newly installed, 0 to remove and 22 not upgraded.
Need to get 10.3 MB/12.0 MB of archives.
**After this operation, 51.6 MB of additional disk space will be used.**
```

So far so good, and I see that the Inhibit Applet is back so we can say goodbye to Caffeine :D

So, I'm going to parse [my Trusty notes]("http://ubuntuforums.org/showthread.php?t=2220264") and see what's changed. So far I see that the "panel-run-dialog" is already set to open with Alt+F2 so step #3 can be skipped.

As noted a while back 'dconf-editor' now replaces 'dconf-tools', although installing 'donf-tools' still gets you where you want to go:

```
lance@lance-AMD-desktop:~$ sudo apt-get install dconf-tools -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dconf-editor
The following NEW packages will be installed:
  dconf-editor dconf-tools
0 upgraded, 2 newly installed, 0 to remove and 24 not upgraded.
Inst dconf-editor (3.18.1-1 Ubuntu:16.04/xenial [amd64])
Inst dconf-tools (0.24.0-2 Ubuntu:16.04/xenial [all])
Conf dconf-editor (3.18.1-1 Ubuntu:16.04/xenial [amd64])
Conf dconf-tools (0.24.0-2 Ubuntu:16.04/xenial [all])

```

The same command works for moving window management buttons:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

As noted in [post #2]("http://ubuntuforums.org/showthread.php?t=2302432&p=13388703#post13388703")  theme management has changed so 'shiki-colors-metacity-theme' is now useless. That doesn't leave many additional packages to install:

```
lance@lance-AMD-desktop:~$ sudo apt-get install indicator-applet sensors-applet gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-settings-daemon
  gnome-shell-common hddtemp iio-sensor-proxy libsensors-applet-plugin0
  mutter-common
Suggested packages:
  ksensors
The following NEW packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-settings-daemon
  gnome-shell-common gnome-tweak-tool hddtemp iio-sensor-proxy
  indicator-applet libsensors-applet-plugin0 mutter-common sensors-applet

```

There are no longer any missing menu buttons to restore:

[ATTACH=CONFIG]265469[/ATTACH]

Compositing is now on by default but can be turned off:

```
gsettings set org.gnome.metacity compositing-manager false
```

This still works to disable  webapps management:

```
gsettings set com.canonical.unity.webapps integration-allowed false
```

Ubuntu now uses the GNOME scrollbars which are "baked into" the themes so there are no overlay-scrollbars to be disabled. The numix theme doesn't use GNOME's new scrollbars.

---

### Post by kansasnoob on 2015-11-10
Apparently the settings in org.gnome.desktop.wm.preferences theme are deprecated. I knew from testing GNOME in Wily that tweak-tool had dropped a setting:

[ATTACH=CONFIG]265474[/ATTACH]

So now only the interface settings are controlled:

[ATTACH=CONFIG]265475[/ATTACH]

The wm theme setting is still in dconf:

[ATTACH=CONFIG]265476[/ATTACH]

But changing it does nothing:

[ATTACH=CONFIG]265477[/ATTACH]

So R.I.P Shiki-Colors-Metacity :cry:

---

### Post by kansasnoob on 2015-11-10
The only thing I see specific to flashback that might be considered a bug is the menu contains the user name which displays a blank limb on the tree:

[ATTACH=CONFIG]265478[/ATTACH]

And it can't just be edited out of the menu.

Otherwise I'm quite impressed :guitar:

I had to look at Trusty to remind myself what was displayed on that branch of the tree:

[ATTACH=CONFIG]265486[/ATTACH]

I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1516316](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1516316)

---

### Post by kansasnoob on 2015-11-14
With compositing switched off several apps (nautilus, gedit, totem, gnome-tweak-tool, system-monitor & empathy) have a huge black border:

[ATTACH=CONFIG]265571[/ATTACH]

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/1516323](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/1516323)

It turns out that was not a metacity bug but rather a theme problem that also effects Wily:

[http://www.webupd8.org/2015/11/fix-large-black-borders-around-header.html](http://www.webupd8.org/2015/11/fix-large-black-borders-around-header.html)

---

### Post by tista on 2015-11-28
@kansasnoob,

Thanks for your info...
And today I've checked gnome-flashback-metacity session as well.
In my case, I've rebuilt some flashback packages with git codebase and now it works almost fine with Gtk+ 3.19.3, Gdm 3.19.2 and much more the bleeding-edge codebases... :)

By the way, now I think we might be able to say good-bye to 'unity-related' packages. Actually my flashback could  run with gnome-settings-daemon and without any indicator packages... But ibus seems to tweak a bit more to run automatically when login into flashback though.

Oh forgot to mention, Have you ever experienced that 'libinput' xorg driver caused the issue on "tap-on-click" of toucpad/clickpad? Once libinput was enabled, multi-touch and tap-on-click were disabled on flashback session. Yeah just happened on my Dell XPS11 laptop, on the other hand, 'synaptics' driver seemed OK. I haven't any ideas why this happened...

Anyway I would keep my eyes open on git changes... :)
[ATTACH=CONFIG]265805[/ATTACH]

Best Regards.
Tista

---

### Post by houstonbofh on 2016-03-02
First, thank you for this.  Your threads are the only reason I am still on Ubuntu.  (Well, your threads and Edubuntu adopting Gnome-Panel) :)

Now, is this going to be the master thread like [http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264) is for Trusty?  And do you have any updates before I start to dive in on a test machine?

---

### Post by kansasnoob on 2016-03-03
> **houstonbofh said:**
> First, thank you for this.  Your threads are the only reason I am still on Ubuntu.  (Well, your threads and Edubuntu adopting Gnome-Panel) :)

Now, is this going to be the master thread like [http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264) is for Trusty?  And do you have any updates before I start to dive in on a test machine?

After Xenial is released we'll no longer be able to discuss it here so I do intend to post a thread somewhere, and I'll add a link to that Trusty thread pointing to its location.

---

### Post by kansasnoob on 2016-03-03
Regarding this:

> Edubuntu adopting Gnome-Panel

I want to be perfectly clear. Edubuntu uses this primarily for its LTSP clients, but it's also available for installation on a standard desktop. It's just an option, Unity is the default DE :D

---

### Post by houstonbofh on 2016-03-04
> **kansasnoob said:**
> Regarding this:



I want to be perfectly clear. Edubuntu uses this primarily for its LTSP clients, but it's also available for installation on a standard desktop. It's just an option, Unity is the default DE :D

I guess I should also be clear.  I mean the edubuntu dev also adopting the gnome-pannel application at the gnome project to keep it from being silently dropped. :)

---

### Post by pfeiffep on 2016-03-06
FWIW - I was getting Nautilus and Web Browser errors with Flashback / Metacity and decided to install Ubuntu Mate.
I've found that most everything to which I was accustomed in Metacity was easily duplicated in Ubuntu Mate. There's a different name for some of the utilities

---

### Post by kansasnoob on 2016-03-07
> **pfeiffep said:**
> FWIW - I was getting Nautilus and Web Browser errors with Flashback / Metacity and decided to install Ubuntu Mate.
I've found that most everything to which I was accustomed in Metacity was easily duplicated in Ubuntu Mate. There's a different name for some of the utilities

I added a couple of comments to your other thread. I hadn't noticed that Nautilus was in poor shape in a flashback session so I'll follow up ASAP.

---

### Post by oldfred on 2016-03-08
So far everything but Nautilus works well.

If I click on anything in the icon on upper right Location options, it often sends cpu to 100% and screen turns grey. After about 10 or 20 seconds and by the time I get to htop to see use it recovers and continues. 
It hangs when I want to add boot mark, but after it recovers bookmark is there.

---

### Post by kansasnoob on 2016-03-08
> **oldfred said:**
> So far everything but Nautilus works well.

If I click on anything in the icon on upper right Location options, it often sends cpu to 100% and screen turns grey. After about 10 or 20 seconds and by the time I get to htop to see use it recovers and continues. 
It hangs when I want to add boot mark, but after it recovers bookmark is there.

It does that [in Ubuntu GNOME]("https://bugs.launchpad.net/ubuntu/+source/gnome-flashback/+bug/1554171/comments/3") too, but also I think [flashback should be using ubuntu's settings instead of gnome-shell's]("https://mail.gnome.org/archives/gnome-flashback-list/2016-March/msg00003.html").

I haven't checked a fresh install of Ubuntu yet to see what happens in Unity.

---

### Post by kansasnoob on 2016-03-08
I just checked and using the Nautilus menus in Ubuntu's default session seem to work OK.

---

### Post by houstonbofh on 2016-03-08
> **pfeiffep said:**
> FWIW - I was getting Nautilus and Web Browser errors with Flashback / Metacity and decided to install Ubuntu Mate.
I've found that most everything to which I was accustomed in Metacity was easily duplicated in Ubuntu Mate. There's a different name for some of the utilities

Also some of the utilities behave very differently.  In some cases, so differently that they are a deal breaker.

---

### Post by kansasnoob on 2016-03-08
> **houstonbofh said:**
> Also some of the utilities behave very differently.  In some cases, so differently that they are a deal breaker.

Without something specific we wouldn't know what to fix now would we?

There really is no need to just say I like x DE better than y or z DE. If one DE suits your needs better than another then that's what you should use.

---

### Post by kansasnoob on 2016-04-04
I filed a new bug report about the missing nautilus preferences menu since nothing had yet been done to address that:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1565780](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1565780)

---

### Post by u2nTu on 2016-04-11
No comments on Nemo? The 14.04 version lacks only the dual location header feature in order to fully restore the Nautilus of old, as it was before being stripped (the best graphical file browser in all of Linux, IMO, and pretty sure I tried them all). Everything else, incl dual pane and script automation works just fine (for me, anyways).

Following this thread, and its successor after the 26th, to keep up on the classic DE. (Mods, please add a "Stalk" button under KN's avatar, maybe OF's and a few others too.)

---

### Post by kansasnoob on 2016-04-11
Nemo never has been a dependency of GNOME Flashback. Is it even part of an entire DE, or just an individual project?

---

### Post by kansasnoob on 2016-04-11
> **kansasnoob said:**
> Nemo never has been a dependency of GNOME Flashback. Is it even part of an entire DE, or just an individual project?

Answered my own question, Nemo is part of the Cinnamon DE. I don't think Cinnamon ever has been well maintained in the Ubuntu repos.

---

### Post by houstonbofh on 2016-04-13
Since it is bumped...

I went ahead and dove into a trial on a laptop 9 days ago, and I am very impressed!  It is a LOT less work to get it going now, and THE WEATHER APPLET IS BACK!  WooHoo! So far the only odd issue I have found is ctl-drag and shift-drag seem to not be working.  But I install the CD from 4/4/16 and updated from there so it could be dev cruft.  Anyone else see this?

Also, occasionally gksu will have the password field grayed out and you have to switch users and back to get it normal...  But not always?  Odd...

So far, I am VERY happy!  This is the first release I have looked forward to in a LONG time!

---

### Post by houstonbofh on 2016-04-29
Found another bug.  [https://bugs.launchpad.net/ubuntu-gnome-flashback/+bug/1502476](https://bugs.launchpad.net/ubuntu-gnome-flashback/+bug/1502476)  Not the first, however...  Now to see if I can find a way to add a darker theme so it is less noticeable.

On the plus side, the gksu bug above appears fixed now.

---

### Post by cariboo on 2016-04-29
Thread closed, as we are testing yakkety.

---

