---
title: "Why does ps -a show two terminals when there is only one open"
date: 2019-01-05
forum: Virtualisation
---

### Post by robertzito on 2019-01-05
Can someone help me understand why my computer shows two terminal when I am the only one using it 

```
ps -a           
  PID TTY          TIME CMD
 1193 tty1     00:00:01 Xorg
 1210 tty1     00:00:00 gnome-session-b
 1228 tty1     00:00:06 gnome-shell
 1255 tty1     00:00:00 ibus-daemon
 1258 tty1     00:00:00 ibus-dconf
 1260 tty1     00:00:00 ibus-x11
 1304 tty1     00:00:00 gsd-xsettings
 1306 tty1     00:00:00 gsd-a11y-settin
 1307 tty1     00:00:00 gsd-clipboard
 1308 tty1     00:00:00 gsd-color
 1312 tty1     00:00:00 gsd-datetime
 1313 tty1     00:00:00 gsd-housekeepin
 1314 tty1     00:00:00 gsd-keyboard
 1325 tty1     00:00:00 gsd-media-keys
 1328 tty1     00:00:00 gsd-mouse
 1336 tty1     00:00:00 gsd-power
 1340 tty1     00:00:00 gsd-print-notif
 1346 tty1     00:00:00 gsd-rfkill
 1347 tty1     00:00:00 gsd-screensaver
 1357 tty1     00:00:00 gsd-sharing
 1365 tty1     00:00:00 gsd-smartcard
 1371 tty1     00:00:00 gsd-sound
 1378 tty1     00:00:00 gsd-wacom
 1547 tty1     00:00:00 ibus-engine-sim
 1656 tty2     00:01:35 Xorg
 1663 tty2     00:00:00 gnome-session-b
 1767 tty2     00:05:23 gnome-shell
 1810 tty2     00:00:02 ibus-daemon
 1814 tty2     00:00:00 ibus-dconf
 1816 tty2     00:00:00 ibus-x11
 1879 tty2     00:00:00 gsd-power
 1881 tty2     00:00:00 gsd-print-notif
 1882 tty2     00:00:00 gsd-rfkill
 1883 tty2     00:00:00 gsd-screensaver
 1885 tty2     00:00:00 gsd-sharing
 1899 tty2     00:00:00 gsd-xsettings
 1900 tty2     00:00:00 gsd-wacom
 1906 tty2     00:00:00 gsd-sound
 1909 tty2     00:00:00 gsd-smartcard
 1919 tty2     00:00:00 gsd-clipboard
 1922 tty2     00:00:00 gsd-a11y-settin
 1923 tty2     00:00:00 gsd-datetime
 1924 tty2     00:00:00 gsd-color
 1927 tty2     00:00:00 gsd-keyboard
 1928 tty2     00:00:00 gsd-housekeepin
 1929 tty2     00:00:00 gsd-mouse
 1935 tty2     00:00:00 gsd-media-keys
 1954 tty2     00:00:00 python
 1961 tty2     00:00:00 gsd-printer
 1976 tty2     00:00:00 hidpi-notificat
 1992 tty2     00:00:00 hidpi-daemon
 1994 tty2     00:00:00 gsd-disk-utilit
 2000 tty2     00:00:03 nautilus-deskto
 2108 tty2     00:00:00 ibus-engine-sim
 2566 tty2     00:00:00 io.elementary.a
 6741 pts/0    00:00:00 ps
```

---

### Post by wildmanne39 on 2019-01-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Is ubuntu running in a virtual environment?

---

### Post by QIII on 2019-01-05
Would you please run

```
top
```

and look for any odd names besides your own, root and perhaps a service popping in now and then?  For instance, I have some KVM virtual machines running, so occasionally "libvert" shows up.

Press cntl-C to stop the updates, then copy and paste the first 20 or so lines back here.

---

### Post by QIII on 2019-01-05
I have to run for a bit, so let me get in this bit of information by way of explanation of where I am going.

For each session, there is one and only one "controlling terminal" that the session claims.  You would expect that if you are the only one logged into the computer, there would be only one controlling terminal as a general rule.

If two people are logged on, there would be two.  That seems to be your concern.

However -- If you are logged in in one session, switch to another user (or, say, you switch to a different DE and start a session without logging out of the first), then there should be two controlling terminals, one associated with each session.  Remember that Linux is by design a multi-user environment.  But it doesn't have the sense to know if you are you_1 or you_2 -- or if your neighbor is a bad guy who somehow managed to log in to your machine.

---

### Post by robertzito on 2019-01-05
This is from top


```

top - 22:40:44 up  2:14,  1 user,  load average: 0.20, 0.48, 0.44
Tasks: 285 total,   1 running, 212 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.4 us,  0.4 sy,  0.0 ni, 99.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 65919460 total, 61137144 free,  1962792 used,  2819524 buff/cache
KiB Swap:  4193788 total,  4193788 free,        0 used. 63138064 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1199 root     -51   0       0      0      0 S   0.7  0.0   1:23.74 irq/132-nv+ 
 1656 root      20   0  364732  87472  69004 S   0.7  0.1   5:25.42 Xorg        
 1767 rzito     20   0 4043428 394480 100292 S   0.7  0.6  13:05.13 gnome-shell 
13134 rzito     20   0 1851364 224432 152532 S   0.7  0.3   0:11.91 Web Content 
  985 root      20   0  215056  24064  11820 S   0.3  0.0   0:04.49 system76-d+ 
 1577 root      20   0 2008272  67632  52572 S   0.3  0.1   0:16.50 nordvpnd    
11058 root      20   0   12756   5484   4724 S   0.3  0.0   0:06.08 openvpn     
12096 rzito     20   0  832920  55732  28692 S   0.3  0.1   0:02.75 gnome-term+ 
12433 root      20   0       0      0      0 I   0.3  0.0   0:07.86 kworker/6:+ 
13062 rzito     20   0 1981400 331676 160068 S   0.3  0.5   0:16.84 firefox     
13194 rzito     20   0 1686180 167520  93752 S   0.3  0.3   0:05.47 WebExtensi+ 
13455 rzito     20   0   52448   4096   3348 R   0.3  0.0   0:00.17 top         
    1 root      20   0  225496   9200   6624 S   0.0  0.0   0:04.96 systemd     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    3 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_gp      
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_par_gp  
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:+ 

```

---

### Post by QIII on 2019-01-05
OK.

Let's have a look at 

```
ps -eaf | grep -e tty -e UID
```

---

### Post by robertzito on 2019-01-06
Here is ps -eaf | grep -e tty -e UID


```

UID        PID  PPID  C STIME TTY          TIME CMD
gdm       1194  1175  0 02:52 tty1     00:00:00 /usr/lib/gdm3/gdm-x-session gnome-session --autostart /usr/share/gdm/greeter/autostart
root      1196  1194  0 02:52 tty1     00:00:00 /usr/lib/xorg/Xorg vt1 -displayfd 3 -auth /run/user/119/gdm/Xauthority -background none -noreset -keeptty -verbose 3
gdm       1212  1194  0 02:52 tty1     00:00:00 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
gdm       1230  1212  0 02:52 tty1     00:00:05 /usr/bin/gnome-shell
gdm       1258  1230  0 02:52 tty1     00:00:00 ibus-daemon --xim --panel disable
gdm       1261  1258  0 02:52 tty1     00:00:00 /usr/lib/ibus/ibus-dconf
gdm       1263     1  0 02:52 tty1     00:00:00 /usr/lib/ibus/ibus-x11 --kill-daemon
gdm       1308  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-xsettings
gdm       1309  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-a11y-settings
gdm       1311  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-clipboard
gdm       1312  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-color
gdm       1316  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-datetime
gdm       1318  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-housekeeping
gdm       1320  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-keyboard
gdm       1328  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-media-keys
gdm       1331  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-mouse
gdm       1332  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-power
gdm       1338  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-print-notifications
gdm       1341  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-rfkill
gdm       1342  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
gdm       1347  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-sharing
gdm       1350  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-smartcard
gdm       1355  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-sound
gdm       1365  1212  0 02:52 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-wacom
gdm       1547  1258  0 02:52 tty1     00:00:00 /usr/lib/ibus/ibus-engine-simple
rzito     1661  1606  0 02:52 tty2     00:00:00 /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=pop gnome-session --session=pop
root      1663  1661  3 02:52 tty2     00:00:40 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
rzito     1671  1661  0 02:52 tty2     00:00:00 /usr/lib/gnome-session/gnome-session-binary --session=pop
rzito     1775  1671  7 02:52 tty2     00:01:16 /usr/bin/gnome-shell
rzito     1818  1775  0 02:52 tty2     00:00:00 ibus-daemon --xim --panel disable
rzito     1822  1818  0 02:52 tty2     00:00:00 /usr/lib/ibus/ibus-dconf
rzito     1824     1  0 02:52 tty2     00:00:00 /usr/lib/ibus/ibus-x11 --kill-daemon
rzito     1887  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-power
rzito     1889  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-print-notifications
rzito     1890  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-rfkill
rzito     1891  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
rzito     1892  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-sharing
rzito     1903  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-xsettings
rzito     1907  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-wacom
rzito     1908  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-sound
rzito     1913  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-smartcard
rzito     1924  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-clipboard
rzito     1927  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-a11y-settings
rzito     1930  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-datetime
rzito     1931  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-color
rzito     1934  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-keyboard
rzito     1935  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-housekeeping
rzito     1940  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-mouse
rzito     1941  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-media-keys
rzito     1975     1  0 02:52 tty2     00:00:00 /usr/lib/gnome-settings-daemon/gsd-printer
rzito     1977  1775  0 02:52 tty2     00:00:00 python /home/rzito/.local/share/gnome-shell/extensions/desk-changer@eric.gach.gmail.com/desk-changer-daemon.py
rzito     1983  1671  0 02:52 tty2     00:00:00 /usr/bin/python3 /usr/lib/hidpi-daemon/hidpi-notification
rzito     1989  1671  0 02:52 tty2     00:00:00 /usr/bin/python3 /usr/lib/hidpi-daemon/hidpi-daemon
rzito     1992  1671  0 02:52 tty2     00:00:00 /usr/lib/gnome-disk-utility/gsd-disk-utility-notify
rzito     2004  1671  0 02:52 tty2     00:00:02 nautilus-desktop
rzito     2113  1818  0 02:52 tty2     00:00:00 /usr/lib/ibus/ibus-engine-simple
rzito     2588  1671  0 02:53 tty2     00:00:00 io.elementary.appcenter -s
rzito     3291     1  9 02:53 tty2     00:01:33 /usr/lib/firefox/firefox -new-window
rzito     3364  3291  7 02:53 tty2     00:01:10 /usr/lib/firefox/firefox -contentproc -childID 1 -isForBrowser -prefsLen 1 -prefMapSize 177467 -schedulerPrefs 0001,2 -parentBuildID 20181207224003 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 3291 true tab
rzito     3425  3291  1 02:53 tty2     00:00:16 /usr/lib/firefox/firefox -contentproc -childID 2 -isForBrowser -prefsLen 175 -prefMapSize 177467 -schedulerPrefs 0001,2 -parentBuildID 20181207224003 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 3291 true tab
rzito     3508  3291  0 02:53 tty2     00:00:00 gjs /home/rzito/.local/share/gnome-shell/extensions/gsconnect@andyholmes.github.io/service/nativeMessagingHost.js /home/rzito/.mozilla/native-messaging-hosts/org.gnome.shell.extensions.gsconnect.json gsconnect@andyholmes.github.io
rzito     3522  3291  0 02:53 tty2     00:00:00 /usr/bin/python3 /usr/bin/chrome-gnome-shell /usr/lib/mozilla/native-messaging-hosts/org.gnome.chrome_gnome_shell.json chrome-gnome-shell@gnome.org
rzito     3894  3291  1 02:58 tty2     00:00:10 /usr/lib/firefox/firefox -contentproc -childID 4 -isForBrowser -prefsLen 6347 -prefMapSize 177467 -schedulerPrefs 0001,2 -parentBuildID 20181207224003 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 3291 true tab
rzito     4497  3291  0 03:07 tty2     00:00:00 /usr/lib/firefox/firefox -contentproc -childID 8 -isForBrowser -prefsLen 6361 -prefMapSize 177467 -schedulerPrefs 0001,2 -parentBuildID 20181207224003 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 3291 true tab
rzito     4620  3291  0 03:08 tty2     00:00:00 /usr/lib/firefox/firefox -contentproc -childID 9 -isForBrowser -prefsLen 6375 -prefMapSize 177467 -schedulerPrefs 0001,2 -parentBuildID 20181207224003 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 3291 true tab
rzito     4738  4701  0 03:09 pts/0    00:00:00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn -e tty -e UID

```

---

### Post by QIII on 2019-01-06
OK.  I think I may see what is going on.

There are two sessions running:  One on tty1 and one on tty2.  Neither of them is some nefarious agent hacking your machine.

If you scan down the UID column on where tty1 is shown, you see root and gdm.

The first two lines indicate an autostart session on vt1.  Down further, where your username starts showing up, you'll see a gnome shell running with your uid and root on vt2.

I've never seen this behavior before, but I suspect you have set up your system to start without entering your password.  I've never set up that way, so I can't confirm just yet.  I may spin up a virtual machine to see if I can replicate the behavior.

What it looks like is that there is a greeter waiting for your input to log in to a session that is idle.

Do you have things set up to start without entering your password?

---

### Post by robertzito on 2019-01-06
Yes I use a password

---

### Post by QIII on 2019-01-06
OK.  Does this occur on reboots?

---

### Post by robertzito on 2019-01-06
I ran ps -eaf | grep -e tty -e UID  on POP-OS 18.04 and Ubuntu18.04 and it still shows me a TTY2 and GDM as TTY1 in my VM both with passwords.

---

### Post by QIII on 2019-01-06
OK.  Hold on.

You are running this command in an OS running on a VM?  If so, then that was a bit of diagnostic information I didn't have.

What you are seeing is what I might reasonably expect if you were running the command from inside a VM.  I'll have to test that.  But at 1:30am I'm a bit punchy.

---

### Post by robertzito on 2019-01-06
yes

---

### Post by robertzito on 2019-01-06
Here is an image of my DEV folder there are like 60 tty


[IMG]https://i.redd.it/qadsapl7wr821.png[/IMG]

---

### Post by QIII on 2019-01-06
That's entirely normal.

I'll putter around with the issue a bit later today.

---

### Post by robertzito on 2019-01-06
Yes

---

### Post by again? on 2019-01-06
You may find this is related to gdm3.
Not that I understand... just an observation.

With lightdm..
```
**[COLOR="#006400"]glen@Gubu:~$[/COLOR] ps -a**
  PID TTY          TIME CMD
 2200 pts/0    00:00:00 ps
```

With gdm3...
```
**[COLOR="#006400"]glen@Gubu:~$[/COLOR] ps -a**
  PID TTY          TIME CMD
 1346 tty1     00:00:01 Xorg
 1365 tty1     00:00:00 gnome-session-b
 1393 tty1     00:00:04 gnome-shell
 1409 tty1     00:00:00 ibus-daemon
 1412 tty1     00:00:00 ibus-dconf
 1414 tty1     00:00:00 ibus-x11
 1443 tty1     00:00:00 gsd-xsettings
 1446 tty1     00:00:00 gsd-a11y-settin
 1448 tty1     00:00:00 gsd-clipboard
 1450 tty1     00:00:00 gsd-color
 1451 tty1     00:00:00 gsd-datetime
 1454 tty1     00:00:00 gsd-housekeepin
 1456 tty1     00:00:00 gsd-keyboard
 1460 tty1     00:00:00 gsd-media-keys
 1465 tty1     00:00:00 gsd-mouse
 1466 tty1     00:00:00 gsd-power
 1470 tty1     00:00:00 gsd-print-notif
 1474 tty1     00:00:00 gsd-rfkill
 1476 tty1     00:00:00 gsd-screensaver
 1478 tty1     00:00:00 gsd-sharing
 1485 tty1     00:00:00 gsd-smartcard
 1490 tty1     00:00:00 gsd-sound
 1493 tty1     00:00:00 gsd-wacom
 1536 tty1     00:00:00 ibus-engine-sim
 1584 tty2     00:00:02 Xorg
 1595 tty2     00:00:00 gnome-session-b
 1779 tty2     00:00:07 gnome-shell
 1793 tty2     00:00:00 ibus-daemon
 1797 tty2     00:00:00 ibus-dconf
 1799 tty2     00:00:00 ibus-x11
 1877 tty2     00:00:00 gsd-power
 1878 tty2     00:00:00 gsd-print-notif
 1879 tty2     00:00:00 gsd-rfkill
 1880 tty2     00:00:00 gsd-screensaver
 1885 tty2     00:00:00 gsd-sharing
 1888 tty2     00:00:00 gsd-smartcard
 1890 tty2     00:00:00 gsd-sound
 1896 tty2     00:00:00 gsd-xsettings
 1901 tty2     00:00:00 gsd-wacom
 1911 tty2     00:00:00 gsd-a11y-settin
 1912 tty2     00:00:00 gsd-color
 1915 tty2     00:00:00 gsd-clipboard
 1916 tty2     00:00:00 gsd-housekeepin
 1917 tty2     00:00:00 gsd-datetime
 1921 tty2     00:00:00 gsd-media-keys
 1922 tty2     00:00:00 gsd-keyboard
 1925 tty2     00:00:00 gsd-mouse
 1964 tty2     00:00:00 gsd-printer
 1980 tty2     00:00:00 clipit
 1986 tty2     00:00:00 indicator-messa
 2003 tty2     00:00:00 python3
 2012 tty2     00:00:00 easystroke
 2013 tty2     00:00:00 gsd-disk-utilit
 2014 tty2     00:00:00 indicator-appli
 2018 tty2     00:00:00 blueman-applet
 2026 tty2     00:00:00 ibus-engine-sim
 2128 tty2     00:00:00 zeitgeist-datah
 2164 pts/0    00:00:00 ps
```

---

