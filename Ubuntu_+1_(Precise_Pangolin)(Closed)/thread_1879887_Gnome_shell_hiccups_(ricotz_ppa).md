---
title: "Gnome shell hiccups (ricotz ppa)"
date: 2011-11-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2011-11-12
GS was failing to start earlier after some updates:

```
paul@precise-64:~/Desktop$ gnome-shell --replace &
[1] 2995
paul@precise-64:~/Desktop$ gnome-shell: symbol lookup error: gnome-shell: undefined symbol: meta_prefs_override_preference_location
^C
[1]+  Exit 127                gnome-shell --replace
paul@precise-64:~/Desktop$
```

This is now fixed after gnome-shell itself was updated again:

```
paul@precise-64:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.2.1+git20111112.90119593-0ubuntu1~12.04~ricotz0
  Candidate: 3.2.1+git20111112.90119593-0ubuntu1~12.04~ricotz0
  Version table:
 *** 3.2.1+git20111112.90119593-0ubuntu1~12.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     3.2.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
N: Ignoring file 'ricotz-testing-oneiric.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
paul@precise-64:~$
```

The bad news is that configuration settings are no longer being picked up correctly. GS extensions are no longer visible in gnome-tweak-tool and I can't restore my previous window button placement settings. Running:

```
gconftool --type string --set /desktop/gnome/shell/windows/button_layout "close,minimize,maximize:"
```
 
and restarting GS had no effect. :confused:

---

### Post by Harry33 on 2011-11-12
I do not use any GS extensions, so I have no experience about them.

But other than that, the Ricotz Testing PPA works very well now.

---

### Post by paul_in_london on 2011-11-12
> **Harry33 said:**
> I do not use any GS extensions, so I have no experience about them.

But other than that, the Ricotz Testing PPA works very well now.

Thanks for your reply Harry. Only one of my GS extensions was working anyway before these updates (noa11y to get rid of the accessibility icon) even though apparently compatible with GS 3.2. It's still working, but no longer showing up in gnome-tweak-tool.

So apart from that you didn't lose any settings (e.g. window button placement) after the latest updates from the ricotz ppa?

---

### Post by Jim_in_Omaha on 2011-11-12
I lost the extensions control in Gnome Shell tweak tool, and the theme is lost in the title bar, and it will not change. Just started after the update.

---

### Post by Harry33 on 2011-11-12
It seems that the latest updates (gir1.2-mutter-3.0, gsettings-desktop-schemas, gnome-shell, libmutter0) are connected to each other. All these must be updated at the same time.

Also, gnome-tweak-tool (3.2.1-0ubuntu1) seems to be too old for the new gsettings-desktop-schemas (3.3.0+git20111112). It takes pretty long time (~20 sec) for g-t-t to open and there are a number of warning messages about misssing gconf settigns.

---

### Post by crdlb on 2011-11-12
It appears that mutter has just been ported from gconf to GSettings (i.e. dconf): [http://git.gnome.org/browse/mutter/commit/?id=d0910da036cfe7e9c86e19ccb3e765953b5dc045](http://git.gnome.org/browse/mutter/commit/?id=d0910da036cfe7e9c86e19ccb3e765953b5dc045)

The GSettings key for button layout is in org.gnome.desktop.wm.preferences.

---

### Post by paul_in_london on 2011-11-12
> **crdlb said:**
> It appears that mutter has just been ported from gconf to GSettings (i.e. dconf): [http://git.gnome.org/browse/mutter/commit/?id=d0910da036cfe7e9c86e19ccb3e765953b5dc045](http://git.gnome.org/browse/mutter/commit/?id=d0910da036cfe7e9c86e19ccb3e765953b5dc045)

The GSettings key for button layout is in org.gnome.desktop.wm.preferences.

Tried:

```
gsettings set org.gnome.desktop.wm.preferences button-layout 'close,minimize,maximize:'
```

Check:

```
gsettings get org.gnome.desktop.wm.preferences button-layout
'close,minimize,maximize:'
```

Reloaded GS. Still no-go.

---

### Post by crdlb on 2011-11-12
Do you have the latest version of gsettings-desktop-schemas? If you do, maybe the transition just hasn't been completed.

---

### Post by paul_in_london on 2011-11-12
> **crdlb said:**
> Do you have the latest version of gsettings-desktop-schemas? If you do, maybe the transition just hasn't been completed.

AFAIK, yes. From today's updates:

```
paul@precise-64:~$ ls -lart /var/cache/apt/archives/gsettings-desktop-schemas*
-rw-r--r-- 1 root root   9258 Nov 12 16:14 /var/cache/apt/archives/gsettings-desktop-schemas-dev_3.3.0~git20111112.a6de26d3-0ubuntu1~12.04~ricotz0_amd64.deb
-rw-r--r-- 1 root root 126150 Nov 12 16:14 /var/cache/apt/archives/gsettings-desktop-schemas_3.3.0~git20111112.a6de26d3-0ubuntu1~12.04~ricotz0_amd64.deb
paul@precise-64:~$
```

```
paul@precise-64:~$ apt-cache policy gsettings-desktop-schemas
gsettings-desktop-schemas:
  Installed: 3.3.0~git20111112.a6de26d3-0ubuntu1~12.04~ricotz0
  Candidate: 3.3.0~git20111112.a6de26d3-0ubuntu1~12.04~ricotz0
  Version table:
 *** 3.3.0~git20111112.a6de26d3-0ubuntu1~12.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     3.2.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
N: Ignoring file 'ricotz-testing-oneiric.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
paul@precise-64:~$
```

---

### Post by paul_in_london on 2011-12-02
I was just wondering - has anyone done a fresh PP install and then added the ricotz testing ppa? If you have, are the window buttons on the left?! I thought this might have sorted itself out by now, but mine are still on the right despite what I've done previously via gconf and (more recently) gsettings.

---

### Post by pferraro on 2011-12-02
> **paul_in_london said:**
> GS was failing to start earlier after some updates:

```
paul@precise-64:~/Desktop$ gnome-shell --replace &
[1] 2995
paul@precise-64:~/Desktop$ gnome-shell: symbol lookup error: gnome-shell: undefined symbol: meta_prefs_override_preference_location
^C
[1]+  Exit 127                gnome-shell --replace
paul@precise-64:~/Desktop$
```

This is now fixed after gnome-shell itself was updated again:

```
paul@precise-64:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.2.1+git20111112.90119593-0ubuntu1~12.04~ricotz0
  Candidate: 3.2.1+git20111112.90119593-0ubuntu1~12.04~ricotz0
  Version table:
 *** 3.2.1+git20111112.90119593-0ubuntu1~12.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     3.2.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
N: Ignoring file 'ricotz-testing-oneiric.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-oneiric.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
paul@precise-64:~$
```

The bad news is that configuration settings are no longer being picked up correctly. GS extensions are no longer visible in gnome-tweak-tool and I can't restore my previous window button placement settings. Running:

```
gconftool --type string --set /desktop/gnome/shell/windows/button_layout "close,minimize,maximize:"
```
 
and restarting GS had no effect. :confused:

Update the button-layout key from the org.gnome.shell.overrides schema.  This key overrides the default button-layout from the org.gnome.desktop.wm.preferences schema.  Changing the button layout no longer requires you to restart gnome-shell.

---

### Post by paul_in_london on 2011-12-02
> **pferraro said:**
> Update the button-layout key from the org.gnome.shell.overrides schema.  This key overrides the default button-layout from the org.gnome.desktop.wm.preferences schema.  Changing the button layout no longer requires you to restart gnome-shell.

Top man!

```
gsettings set org.gnome.shell.overrides button-layout 'close,minimize,maximize:'
```

did the trick and without having to restart GS as you said. Cheers!

---

### Post by Jim_in_Omaha on 2011-12-03
> **paul_in_london said:**
> I was just wondering - has anyone done a fresh PP install and then added the ricotz testing ppa? If you have, are the window buttons on the left?! I thought this might have sorted itself out by now, but mine are still on the right despite what I've done previously via gconf and (more recently) gsettings.

I had to rebuild my T500 Thinkpad because of a really strange crash that killed the kernal. I intentionally went with the testing ppa of Gnomeshell to test it out. The extensions did not work and I was unable to add the buttons. And I have not moved them to the left.

The memory hog issue seems to be related to the extensions-commons somehow. Right now I'm running the release 3.2 without that and have had no memory issues on either the desktop or the T500 (after reversing from the testing PPA)

---

### Post by paul_in_london on 2011-12-03
> **Jim_in_Omaha said:**
> I had to rebuild my T500 Thinkpad because of a really strange crash that killed the kernal. I intentionally went with the testing ppa of Gnomeshell to test it out. The extensions did not work and I was unable to add the buttons. And I have not moved them to the left.

The memory hog issue seems to be related to the extensions-commons somehow. Right now I'm running the release 3.2 without that and have had no memory issues on either the desktop or the T500 (after reversing from the testing PPA)

Thanks again for the fix. I'm still using the ricotz-testing ppa and some GS extensions aren't working for me at the moment (e.g. **noa11y**). The warning given is "Extension does not support shell version").

---

