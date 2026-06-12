---
title: "gnome-shell 3.3.90"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jbicha on 2012-03-14
I've begun uploading the new clutter and gnome-shell to the normal Precise repositories. As usual in these big transitions, you probably want to wait to update until it finishes later today.

---

### Post by dino99 on 2012-03-14
wow :) does Precise  been un-freezed ? (but happy news, dont stop the move)

---

### Post by dmiranda on 2012-03-14
A really big "Thank You" to Jeremy, Rico and everyone else that helps this transition. Today you made a lot of users happy :p

---

### Post by Gregory Lee on 2012-03-14
Yes, thanks in advance.  I'm not seeing it yet -- is it really here?

---

### Post by grahammechanical on 2012-03-14
I am just being curious. Is testing these alternate User Interfaces part of Ubuntu Q&A.

Regards.

---

### Post by schtufbox on 2012-03-14
Might explain why Gnome-shell wouldn't start after my updates earlier :)  Will try again tomorrow!

---

### Post by kaldor on 2012-03-14
I tend to use Shell a lot. Thanks for your work :)

---

### Post by keithpeter on 2012-03-14
Hello All

Thanks for this.

Is the intention to get to gnome-shell 3.4.x before Precise ships?

---

### Post by grahammechanical on 2012-03-14
> Is the intention to get to gnome-shell 3.4.x before Precise ships?

I think that was the intention.

[http://www.webupd8.org/2012/03/gnome-shell-34-might-make-it-in-ubuntu.html#more]("http://www.webupd8.org/2012/03/gnome-shell-34-might-make-it-in-ubuntu.html#more")

Note the comment at the bottom.

This post on this forum mentions 3.3.90 and not 3.4. So, I guess for you it is wait and see time.

Regards.

---

### Post by jjcv on 2012-03-14
This is great news.  Thanks to all those involved.  I never use anything but gnome-shell :-)

---

### Post by PaulW2U on 2012-03-14
> **Gregory Lee said:**
> Yes, thanks in advance.  I'm not seeing it yet -- is it really here?

Yes but held back from upgrading awaiting a new version of gnome-tweak-tool.

---

### Post by Space_Balls on 2012-03-14
> **grahammechanical said:**
> I think that was the intention.

[http://www.webupd8.org/2012/03/gnome-shell-34-might-make-it-in-ubuntu.html#more]("http://www.webupd8.org/2012/03/gnome-shell-34-might-make-it-in-ubuntu.html#more")

Note the comment at the bottom.

This post on this forum mentions 3.3.90 and not 3.4. So, I guess for you it is wait and see time.

Regards.

3.3.90 is just the dev Version of gnome-shell 3.4. If 3.3.90 is in the official repos, it's just a matter of waiting for the final release to have 3.4.

GNOME versioning:
3.{even #} = stable releases
3.{odd #} = development branch

---

### Post by ryley on 2012-03-14
To those who have upgraded gnome-shell, have you had any issues with extension compatibiltes? I was using the ricotz-testing and staging ppa's a few weeks ago and none of the extensions from extensions.gnome.org or the Webupd8 ppa were able to be activated.

---

### Post by shuttleworthwannabe on 2012-03-14
I am looking forward to trying the dev version of Gnome Shell--just a sneak peak at Fedora alpha in live mode--so far I like the smoothness and slickness. Just fabulous!

---

### Post by jbicha on 2012-03-14
Except for ARM & PowerPC & a few rarely used universe apps, the new builds are done. It may take a few hours to show up on your mirror.

It should be safe to upgrade when apt-cache policy cheese returns
```
Candidate: 3.3.90-0ubuntu2
```

---

### Post by kurt18947 on 2012-03-15
...... and every one of my 10 gnome extensions is broken:lolflag:

---

### Post by PaulW2U on 2012-03-15
> **kurt18947 said:**
> ...... and every one of my 10 gnome extensions is broken:lolflag:

And the extensions website shows a lot less extensions available. ;)

I guess we'll have to learn to use Gnome Shell in its native form until the extensions are updated and made compatible with this new version.

---

### Post by topyli on 2012-03-15
Something seems to have broken during the 3.90 uploads. With 3.3.90-0ubuntu1~precise3, the shell integration of the new GNOME apps (Web, Documents, Contacts) worked as advertised, and the menubar was replaced with a nice menu in the shell panel. Now with 3.3.90-0ubuntu1, the menu is duplicated in both the window and the panel.

Anyone else noticing this, or have I broken something locally?

---

### Post by novafluxx on 2012-03-15
Great to know that the latest Gnome-Shell will be available in 12.04! I like having options and while Unity is interesting and fun to learn (reminds me a LOT of Mac OS X), Gnome-Shell is the most likely the future of Fedora and RHEL which I need to stay abreast of.

---

### Post by jbicha on 2012-03-15
topyli, in the GNOME3 PPA, I disabled a patch in **gnome-settings-daemon** which fixed the duplicated new gmenu in GNOME Shell 3.4 but unfortunately it causes all the menus in Unity to be duplicated. Seb Bacher is working on a proper fix.

---

### Post by Gregory Lee on 2012-03-15
My screen freezes immediately after login.  My mouse is still active, though it does nothing, and I can still get a console with ctl-alt-F1.  Back to Unity, for now.

---

### Post by cmccauley on 2012-03-15
> **Gregory Lee said:**
> My screen freezes immediately after login.  My mouse is still active, though it does nothing, and I can still get a console with ctl-alt-F1.  Back to Unity, for now.

I have a similar problem using oneric with the ricotz gnome-shell PPA and the gnome3-ppa. I'm using the NVIDIA driver (post-release-updates). In my case, I can't get a console and have to power off. I've kicked-off the upgrade to precise so hopefully that fixes it.

Chris

---

### Post by bmbaker on 2012-03-15
funny! i have been using ricotz/testing for ages no problems!
try the packages from the ppa and see if you have them all installed in synaptic from the precise repos!

---

### Post by topyli on 2012-03-16
> **jbicha said:**
> topyli, in the GNOME3 PPA, I disabled a patch in **gnome-settings-daemon** which fixed the duplicated new gmenu in GNOME Shell 3.4 but unfortunately it causes all the menus in Unity to be duplicated. Seb Bacher is working on a proper fix.

Thanks! Launchpad tells me the fix is already done :)

---

### Post by kaldor on 2012-03-16
Shell is still held back for me. What's going on here? I'm assuming it's on my end, since apparently others upgraded yesterday.

```


The following packages have been kept back:
  empathy empathy-common gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-mutter-3.0 gnome-online-accounts gnome-shell
  gnome-shell-common gnome-tweak-tool libclutter-1.0-0 libcogl-pango0
  libgoa-1.0-0 libidl0 libmutter0 libpackagekit-glib2-14 libpurple0
  libtotem-plparser17 mutter-common nautilus-sendto-empathy udisks wine1.4
  wine1.4-amd64 wine1.4-common wine1.4-i386:i386
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.


```

---

### Post by dino99 on 2012-03-16
> **kaldor said:**
> Shell is still held back for me. What's going on here? I'm assuming it's on my end, since apparently others upgraded yesterday.

```


The following packages have been kept back:
  empathy empathy-common gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-mutter-3.0 gnome-online-accounts gnome-shell
  gnome-shell-common gnome-tweak-tool libclutter-1.0-0 libcogl-pango0
  libgoa-1.0-0 libidl0 libmutter0 libpackagekit-glib2-14 libpurple0
  libtotem-plparser17 mutter-common nautilus-sendto-empathy udisks wine1.4
  wine1.4-amd64 wine1.4-common wine1.4-i386:i386
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.


```

the faulty package might be gnome-tweak-tool, uninstall it for the moment, but at first glance gnome-shell is still missing some updates (at least on my system)

---

### Post by bmbaker on 2012-03-16
looks like your missing mutter!

---

### Post by pressureman on 2012-03-16
It appears that modal dialogs are now attached to the parent window, whether you like it or not.

I previously disabled this functionality with:

```

gconftool-2 --set /desktop/gnome/shell/windows/attach_modal_dialogs false --type bool

```

GNOME Shell appears to pay no attention to this setting anymore.

It's very annoying when the "File > Open" dialog cannot be moved to reveal the content underneath it.

---

### Post by kaldor on 2012-03-16
> **bmbaker said:**
> looks like your missing mutter!

I already had a large chunk of updates yesterday and the day before. These are the only ones remaining.

---

### Post by bmbaker on 2012-03-16
you can also check that all these packages are installed

[http://packages.ubuntu.com/precise/gnome/gnome-shell](http://packages.ubuntu.com/precise/gnome/gnome-shell)

---

### Post by kaldor on 2012-03-16
Just removed the tweak tool. Still same:

```


The following packages have been kept back:
  empathy empathy-common gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-mutter-3.0 gnome-online-accounts gnome-shell
  gnome-shell-common gvfs gvfs:i386 gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gvfs-libs:i386 libclutter-1.0-0
  libcogl-pango0 libgoa-1.0-0 libidl0 libmutter0 libpackagekit-glib2-14
  libpurple0 libtotem-plparser17 mutter-common nautilus-sendto-empathy udisks
  wine1.4 wine1.4-amd64 wine1.4-common wine1.4-i386:i386
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.


```

I also did autoremove just in case. No luck. Tried switching servers also.

---

### Post by jbicha on 2012-03-16
> **pressureman said:**
> It appears that modal dialogs are now attached to the parent window, whether you like it or not.

I previously disabled this functionality with:

```

gconftool-2 --set /desktop/gnome/shell/windows/attach_modal_dialogs false --type bool

```GNOME Shell appears to pay no attention to this setting anymore.

gnome-shell 3.4 doesn't use gconf any more in favor of gsettings. Try looking in org.gnome.shell.overrides.

---

### Post by pressureman on 2012-03-16
> **jbicha said:**
> gnome-shell 3.4 doesn't use gconf any more in favor of gsettings. Try looking in org.gnome.shell.overrides.

Thanks, found it.

```

gsettings set org.gnome.shell.overrides attach-modal-dialogs false

```

---

### Post by jbicha on 2012-03-16
kaldor, I believe you're going to have to do a dist-upgrade for gnome-shell 3.3.90. If that command wants to remove something important, you can post the output here.

---

### Post by Gregory Lee on 2012-03-16
> **Gregory Lee said:**
> My screen freezes immediately after login.
I'm up for a few hours now in GS 3.3.90 with no freezes or crashes.

---

### Post by pressureman on 2012-03-16
My shell seems to crash whenever I mouse into the hot corner just after an apt-get upgrade. I thought it might have just been a one-off, if some libs were updated, but it seems to happen each time. After the crash, gnome restarts automatically (usually), and it's OK then to mouse into the hot corner.... until I do the next apt-get upgrade.

---

### Post by kaldor on 2012-03-16
Just upgraded it, and only have one issue: where's the Adwaita titlebar? It seems stuck on Ambiance, whereas the rest of the theme is correct.

Edit: seems the rest of the theme is turning out somewhat buggy too. Something missing?

Edit 2: Nevermind, gnome-tweak-tool fixed it. 

Shell feels overall a bit more responsive. However, I really hate the new maximize behaviour on the Web (epiphany) application. It looks much less sleek than before :(

---

### Post by jbicha on 2012-03-16
The theme chooser in System Settings currently only sets the gconf value for the window theme, not the gsettings one that GNOME Shell 3.4 is looking for. I think it would be a relatively easy fix to have it set both. On the other hand, GNOME Tweak Tool 3.4 does the opposite, and I'm not sure how difficult that would be to fix.

---

