---
title: "Dropbox Core Dumping on Kubuntu"
date: 2014-12-23
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2014-12-23
The new 3.0.4 version of Dropbox is crashing and core dumping on a fresh install of today's Kubuntu 15.04 daily. I.e., the installer downloads the binary without a problem, but any attempt to launch the daemon fails.

---

### Post by pnunn on 2014-12-26
I'm getting the same issue today using a version that was working with older installs of Kubuntu happily (not sure of the version of dropbox).

---

### Post by marco-parillo on 2014-12-31
I just followed the 32-bit command line instructions from Dropbox: [https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx) to a new Kubuntu 15.04 Alpha 1 installation. It seemed to work, only it did not place the icon in my System Tray the way it does on Plasma 4, but, when complete, it did pop up a notification that over 100 files were downloaded, which I can see in the Dropbox folder. It looks like your version as wget downloaded for me translated  from: "https://www.dropbox.com/download?plat=lnx.x86" to: [https://dl-web.dropbox.com/u/17/dropbox-lnx.x86-3.0.4.tar.gz](https://dl-web.dropbox.com/u/17/dropbox-lnx.x86-3.0.4.tar.gz)

Definately the same version number:

```
[FONT=fixedsys]ps -ef | grep box
mparillo  2343  2342  3 13:40 ?        00:00:47 /home/mparillo/.dropbox-dist/dropbox-lnx.x86-3.0.4/dropbox
mparillo 22042 22029  0 14:06 pts/5    00:00:00 grep --color=auto box
[/FONT]
```

---

### Post by marco-parillo on 2014-12-31
How are you launching it? I just have a shell script in my $HOME directory (again following their CLI instructions):
```

~/.dropbox-dist/dropboxd

```
That I call when I want to sync.

---

### Post by vasa1 on 2014-12-31
> **marco-parillo said:**
> .. It seemed to work, only it did not place the icon in my System Tray the way it does on Plasma 4, 
...
 /home/mparillo/.dropbox-dist/dropbox-lnx.x86-3.0.4/dropbox
...
Was that Dropbox 3.0.4 on Plasma 4 or was it an older Dropbox? 

The systray icon of Dropbox 3.0.3 has been misbehaving for several users of several Linux distros.

---

### Post by marco-parillo on 2015-01-01
Good call vasa1: My Plasma 4 installation is running 2.10.52 
```

$ ps -ef | grep dropbox
mparillo 21680 21679  6 10:04 ?        00:00:02 /home/mparillo/.dropbox-dist/dropbox-lnx.x86-2.10.52/dropbox
mparillo 21763 21742  0 10:04 pts/0    00:00:00 grep --color=auto dropbox

```

---

### Post by vasa1 on 2015-01-01
I use the Openbox session available in Lubuntu 14.04. I find that killing the panel process (tint2) using "killall -SIGUSR1 tint2" allows the icon to appear. I keep a sleep of 60 seconds between launching dropbox and killing the tint2 process. Maybe you could try something similar with your KDE panel?

My autostart file:
```
(hsetroot -tile /home/vasa1/Dropbox/Backgrounds/gray.png) &
**(sleep 2s && tint2) &**
(sleep 3s && lxclipboard) &
(sleep 5s && udisksctl mount -b /dev/sdb1) &
(sleep 3s && compton --config /home/vasa1/.config/compton.conf -b) &
(sleep 1s && pkill blueman-applet) &
(sleep 1s && pkill applet.py) &
(sleep 1s && pkill update-notifier) &
(sleep 1s && pkill light-locker) &
[B](sleep 1s && /home/vasa1/.dropbox-dist/dropboxd) &
(sleep 60s && killall -SIGUSR1 tint2) &[/B]
(sleep 30s && conky) &

```

---

### Post by buzzingrobot on 2015-01-05
No change after a fresh install of today's (5 Jan) daily. Installing via the command line, or the dropbox_1.6.1_amd64.deb or dropbox_2.10.0_amd64.deb packages from linux.dropbox.com all fail with "Aborted (core dumped)" when ~/.dropbox-dist/dropboxd' is run.

'dropbox start' and 'dropbox start -i' report success, but no Dropbox process launches and no Dropbox folder is created.

[EDIT:  A startup entry of "dropbox start -i" was created. When I logged out, to see what happened, a kdeinit5 error displayed and the machine locked with a black screen and oversized white cursor.  After powering down and on again, the (new) Dropbox signon widget appeared, I logged on to my account and Dropbox is currently synching.  Still no icon in the panel, tho.]

---

### Post by marco-parillo on 2015-01-21
Now it is happening to me also with Alpha 2.
I invoke my shell script, it runs for a second and disappears.
```
 [FONT=monospace][COLOR=#000000]mparillo@mparillo-1504-Alpha2RC1:~$ ps -ef | grep box [/COLOR]
mparillo  2217  2216 29 20:07 ?        00:00:01 /home/mparillo/.drop[COLOR=#ff5454]**box**[/COLOR][COLOR=#000000]-dist/drop[/COLOR][COLOR=#ff5454]**box**[/COLOR][COLOR=#000000]-lnx[/COLOR]
.x86-3.0.5/drop[COLOR=#ff5454]**box**[/COLOR]
mparillo  2250  2170  0 20:07 pts/12   00:00:00 grep --color=auto [COLOR=#ff5454]**box**[/COLOR]
mparillo@mparillo-1504-Alpha2RC1:~$ ps -ef | grep box 
mparillo  2252  2170  0 20:08 pts/12   00:00:00 grep --color=auto [COLOR=#ff5454]**box**[/COLOR][/FONT]


```
I try to invoke it directly and it dumps
```

[FONT=monospace]mparillo@mparillo-1504-Alpha2RC1:~$ ~/.dropbox-dist/dropboxd 
Aborted (core dumped) [/FONT]

```

EDIT: After applying today's updates, it no longer core dumps. But, it still does not give me the indicator in my System Tray.
```

[FONT=monospace]mparillo@mparillo-1504-Alpha2RC1:~/Downloads$ python dropbox.py status 
Up to date[/FONT]

```

---

### Post by marco-parillo on 2015-01-22
> **buzzingrobot said:**
> A startup entry of "dropbox start -i" was created. When I logged out, to see what happened, a kdeinit5 error displayed and the machine locked with a black screen and oversized white cursor.  After powering down and on again, the (new) Dropbox signon widget appeared, I logged on to my account and Dropbox is currently synching.  Still no icon in the panel, tho.]

I think I must have the startup entry also, but I cannot find it in System Settings. Where did you find yours?

---

### Post by buzzingrobot on 2015-01-22
> **marco-parillo said:**
> I think I must have the startup entry also, but I cannot find it in System Settings. Where did you find yours?

System Settings->Startup and Shutdown?

---

### Post by marco-parillo on 2015-01-23
I could find nothing poking around there.
[ATTACH=CONFIG]259444[/ATTACH]
But it is  running:
```
[COLOR=#000000][/COLOR]
[FONT=monospace]mparillo@mparillo-1504-Alpha2RC1:~/Downloads$ ps -ef | grep box 
mparillo  1978  1867  0 Jan22 ?        00:01:22 /home/mparillo/.drop[COLOR=#ff5454]**box**[/COLOR][COLOR=#000000]-dist/drop[/COLOR][COLOR=#ff5454]**box**[/COLOR][COLOR=#000000]-lnx[/COLOR]
.x86-3.0.5/drop[COLOR=#ff5454]**box**[/COLOR][COLOR=#000000] -session 101f91e51d51af000142195192900000018260029_1421953485_699881 [/COLOR]
-name  
mparillo 10229  2310  0 20:09 pts/17   00:00:00 grep --color=auto [COLOR=#ff5454]**box**[/COLOR][COLOR=#000000] [/COLOR]
mparillo@mparillo-1504-Alpha2RC1:~/Downloads$ python dropbox.py status  
Up to date
[/FONT]

```

---

### Post by buzzingrobot on 2015-01-24
> **marco-parillo said:**
> I could find nothing poking around there.


Don't have the 15.04 install at the moment, but on 14.10, when I install Dropbox using the command line rather than a package, when I enable Dropbox there as a startup script, it puts a link to .dropboxd in ~/.kde/autostart.

---

