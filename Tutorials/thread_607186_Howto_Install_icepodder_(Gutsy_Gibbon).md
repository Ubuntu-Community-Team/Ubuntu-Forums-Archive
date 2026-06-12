---
title: "Howto: Install icepodder (Gutsy Gibbon)"
date: 2007-11-08
forum: Tutorials
---

### Post by handband2 on 2007-11-08
Installing **[COLOR="Red"]icepodder[/COLOR]** (Gutsy Gibbon)

Install Dependencies:
```
$ sudo apt-get install build-essential python python-xmms bittorrent python-wxgtk2.6 python-pyrss2gen python-feedparser
```

**Go here to download the source files:**  [http://icepodder.fryingoverajungle.net/?page_id=4](http://icepodder.fryingoverajungle.net/?page_id=4)
or
**Click Here to download source files:**  [http://www.icepodder.com/wp-content/uploads/2007/02/IcePodder-5.4.tar.bz2](http://www.icepodder.com/wp-content/uploads/2007/02/IcePodder-5.4.tar.bz2)
or
```
$ wget http://www.icepodder.com/wp-content/uploads/2007/02/IcePodder-5.4.tar.bz2
```

Extract Files:
```
$ tar -jxvf IcePodder-5.4.tar.bz2
```

Move to icepodder folder:
```
$ cd ./icepodder
```

Install icepodder:
```
$ sudo ./install.sh
```

Add as application:
```
$ sudo gedit /usr/share/applications/icepodder.desktop
```

Insert into gedit file:
```

[Desktop Entry]
Encoding=UTF-8
Name=IcePodder
Exec=icepodder %u
Icon=/usr/share/icepodder/icons_status/application.ico
Type=Application
Categories=Application;AudioVideo;
MimeType=text/rss;text/xml;text/php;application/rss+xml
Comment=A Gnome Pocast handler
```

Some might have to run the following to get the program icons to show up in the **Applications** > **Sound & Video** list:
```
$ killall gnome-panel
```

**Note:**
[COLOR="Red"]An error can occur when trying to run icepodder when python-wxgtk2.8 is installed.[/COLOR]

---

### Post by jkc96405 on 2007-12-03
Thanks for the howto.:):)  I followed your directions and cut and paste the commands into terminal.  When I attempted to start icepodder from the command line, it returned the following:

CastPodderGui.py:48: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from   wxPython.wx import *
[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Beep-Media-Player couldn't be imported
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in <module>
    main()
  File "CastPodderGui.py", line 3617, in main
    myApp = iPodderGui(ipodder)
  File "CastPodderGui.py", line 685, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "CastPodderGui.py", line 1519, in OnInit
    self.InitHooks()
  File "CastPodderGui.py", line 1876, in InitHooks
    for att, method in inspect.getmembers(self, inspect.ismethod): 
  File "/usr/lib/python2.5/inspect.py", line 206, in getmembers
    value = getattr(object, key)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 9331, in GetAcceleratorTable
    return _core_.Window_GetAcceleratorTable(*args, **kwargs)
TypeError: in method 'Window_GetAcceleratorTable', expected argument 1 of type 'wxWindow *'

What do I do next?

Thanks

jkc

---

### Post by handband2 on 2007-12-06
The error comes from python-wxgtk2.8 being installed.

If you don't mind uninstalling python-wxgtk2.8, icepodder will run fine.  My system doesn't need python-wxgtk2.8 but you might have something that requires it.  Double check if it is required for another package.

Here is the command to remove python-wxgtk2.8:
```

sudo apt-get purge python-wxgtk2.8

```

---

### Post by glabonte on 2007-12-14
Great instructions!

I found a deb package available for download on the icepodder webpage.  When I clicked on it to download, I got the option to have the "GDebi Package Installer" automatically install it.  I used this option and everything appears to be fine (I did have to use your instructions to get it added to the menu).

I just started using the program, so I haven't run into any problems yet.  Is it ok to use GDebi, or is it better to install it manually using the tarball?

Thanks!

---

### Post by theRevMom on 2008-02-01
Thank you!  I'm grateful to you for posting this how-to for those of us who loved I-podder and aren't techie enough to have figured out icepodder on our own.  Kuddos to you!

:KS

---

### Post by scottfinneran on 2009-03-03
> **handband2 said:**
> The error comes from python-wxgtk2.8 being installed.

If you don't mind uninstalling python-wxgtk2.8, icepodder will run fine.  My system doesn't need python-wxgtk2.8 but you might have something that requires it.  Double check if it is required for another package.



If you do want to keep 2.8 and 2.6 simultaneously installed, a quick hack to CastPodderGui.py (in to the top directory of the source tree) will do the trick:

Change the line that reads:
```

wxversion.ensureMinimal('2.6')

```
to read:
```

wxversion.select('2.6')

```
This will cause the 2.6 version rather than the default 2.8 to be used.

---

### Post by handband2 on 2009-03-03
> **scottfinneran said:**
> If you do want to keep 2.8 and 2.6 simultaneously installed, a quick hack to CastPodderGui.py (in to the top directory of the source tree) will do the trick:

Change the line that reads:
```

wxversion.ensureMinimal('2.6')

```
to read:
```

wxversion.select('2.6')

```
This will cause the 2.6 version rather than the default 2.8 to be used.

Thanks for the info!

To get around this error it might be better to install the subversion of icepodder:
```
sudo apt-get install subversion
```
```
svn co https://icepodder.svn.sourceforge.net/svnroot/icepodder icepodder
```

Enjoy!

---

### Post by flamaest on 2011-05-10
If you google it, there seems to be a version 5.5 which indicates many issues have been resolved in the changlog:


[http://rpm.pbone.net/index.php3/stat/4/idpl/14901037/dir/mandrake_other/com/icepodder-5.5-0.68.3mdv2011.0.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/14901037/dir/mandrake_other/com/icepodder-5.5-0.68.3mdv2011.0.noarch.rpm.html)



Changelog for icepodder-5.5-0.68.3mdv2011.0.noarch.rpm :
Fri Dec 10 13:00:00 2010 Oden Eriksson 5.5-0.68.3mdv2011.0
+ Revision: 619584
- the mass rebuild of 2010.0 packages

Fri Sep 11 14:00:00 2009 Thierry Vignaud 5.5-0.68.2mdv2010.0
+ Revision: 437931
- rebuild

Sat Dec 27 13:00:00 2008 Adam Williamson 5.5-0.68.1mdv2009.1
+ Revision: 319977
- clean spec
- no longer has any use for pyxmms
- no longer needs wxpython 2.6, works with 2.8 – change deps, drop wx26.patch
- bump to svn to get fix for wx 2.6 dep

---

### Post by sellingandbuyingmusk on 2012-03-17
how to Install icepodder in ubuntu 11.10 64bit? I had problems installing it the information on this page.

ubuntu@ubuntu:~/Desktop/icepodder$ run ./install.sh
No command 'run' found, did you mean:
 Command 'crun' from package 'ceph' (universe)
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (universe)
 Command 'qrun' from package 'torque-client-x11' (universe)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found

Is there something i doing wrong?  Do have to use 32bit Ubuntu 11.10?

---

### Post by handband2 on 2012-03-17
> **sellingandbuyingmusk said:**
> how to Install icepodder in ubuntu 11.10 64bit? I had problems installing it the information on this page.

ubuntu@ubuntu:~/Desktop/icepodder$ run ./install.sh
No command 'run' found, did you mean:

Is there something i doing wrong?  Do have to use 32bit Ubuntu 11.10?

Try:
```

sudo ./install.sh

```
Not:
```

run ./install.sh

```

---

