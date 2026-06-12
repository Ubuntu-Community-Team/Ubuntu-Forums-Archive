---
title: "Two processes attempt to mount blank optical discs"
date: 2015-06-01
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-06-01
[This bug]("https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964") has been around quite a long time and since it's getting no dev love I decided to try and determine which process in addition to 'nautilus', 'caja', and possibly other file managers is mounting blank CD's, DVD's, etc. It's easy to reproduce - I did a fresh install of Ubuntu Wily and before making any changes just popped in a blank DVD:

[ATTACH=CONFIG]262352[/ATTACH]

You can change the automount settings to avoid that but then it interferes with automounting of flash drives, cameras, etc:

[ATTACH=CONFIG]262353[/ATTACH]

Any thoughts on how to determine what process other than the file manager is automounting blank optical media?

I know it's just a cosmetic thing but it's downright ugly and just has "not ready for prime time" written all over it :cry:

---

### Post by mc4man on 2015-06-01
Well one (or the system) can't mount a blank disk, there is nothing to mount. (only a file system can be mounted.
One pop up  is from the fie manager, the other one maybe from gvfs?  The location of blank media would be - 
burn:///

Overall Gnome screwed up this automount option, it shouldn't include blank media or audio cd's (cdda), Ubuntu has declined to address..

---

### Post by kansasnoob on 2015-06-01
> **mc4man said:**
> Well one (or the system) can't mount a blank disk, there is nothing to mount. (only a file system can be mounted.
One pop up  is from the fie manager, the other one maybe from gvfs?  The location of blank media would be - 
burn:///

Overall Gnome screwed up this automount option, it shouldn't include blank media or audio cd's (cdda), Ubuntu has declined to address..

In Vivid it also effected Ubuntu Mate which surprised me. I'll try Ubuntu Mate Wily ASAP to see if it's still effected. I know the latest Debian stable and Sid are not effected.

---

### Post by mc4man on 2015-06-01
By not affected do you mean not error' popup or that blank media & audio cds aren't affected by the automount option.
(- from an audio cd perspective if automount is disabled then autorun or the 'select what to do' popup don't work.

---

### Post by kansasnoob on 2015-06-02
> **mc4man said:**
> By not affected do you mean not error' popup or that blank media & audio cds aren't affected by the automount option.
(- from an audio cd perspective if automount is disabled then autorun or the 'select what to do' popup don't work.

It turns out I was at least partly wrong. In Vivid I know this effected Ubuntu w/Unity, Ubuntu Mate, and flashback (whether added to Ubuntu or Ubuntu GNOME). It also effected GNOME Shell in Ubuntu GNOME albeit in a different way where the pop-up at the bottom of the screen asking what to do would simply reappear again after selecting what to do.

In both Debian Jessie and Debian testing I don't see that in either the default GNOME Shell DE or flashback, but I just installed Debian Jessie w/Mate and there she be:

[ATTACH=CONFIG]262359[/ATTACH]

I'll try to get Ubuntu Mate Wily installed within the next 24 hours or so to be sure it's also still effected.

But since this effects Debian with the Mate DE we can at least rule out Nautilus itself as the culprit. Martin Wimpress has been excellent at chasing down bugs so hopefully I can draw his attention to this. I'd be willing to provide the leg work if only I knew what I was doing.

---

### Post by kansasnoob on 2015-06-02
This does still effect Ubuntu Mate Wily so i updated the info in my OP to reflect that.

---

### Post by QDR06VV9 on 2015-06-02
I don't see it on fedora! Not that it matters.
```
inxi -FxzD
System:    Host: localhost.localdomain Kernel: 4.0.4-301.fc22.x86_64 x86_64 (64 bit gcc: 5.1.1)
           Desktop: MATE 1.10.0  Distro: Fedora release 22 (Twenty Two)
Machine:   System: Acer product: Aspire 5750 v: V1.14
           Mobo: Acer model: JE50_HR Bios: Acer v: V1.14 date: 09/07/2011
CPU:       Dual core Intel Core i3-2330M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8780
           clock speeds: max: 2200 MHz 1: 903 MHz 2: 954 MHz 3: 1049 MHz
           4: 899 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: Fedora X.org 117.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 10.5.4 Direct Rendering: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.0.4-301.fc22.x86_64
Network:   Card-1: Broadcom NetLink BCM57785 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: enp2s0f0 state: down mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak]
           driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 176.3GB (16.8% used)
           ID-1: /dev/sda model: Hitachi_HTS54161 size: 160.0GB
           ID-2: USB /dev/sdb model: SanDisk_Cruzer size: 16.3GB
Partition: ID-1: / size: 74G used: 5.4G (8%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 195 Uptime: 7:27 Memory: 784.6/3805.9MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.391) inxi: 2.2.21 
[me@localhost ~]$ 

```

---

### Post by kansasnoob on 2015-06-02
Which desktop environment are you running on Fedora?

I welcome any and all feedback - it's important to know how far upstream the bug resides :)

> **runrickus said:**
> I don't see it on fedora! Not that it matters.
```
inxi -FxzD
System:    Host: localhost.localdomain Kernel: 4.0.4-301.fc22.x86_64 x86_64 (64 bit gcc: 5.1.1)
           Desktop: MATE 1.10.0  Distro: Fedora release 22 (Twenty Two)
Machine:   System: Acer product: Aspire 5750 v: V1.14
           Mobo: Acer model: JE50_HR Bios: Acer v: V1.14 date: 09/07/2011
CPU:       Dual core Intel Core i3-2330M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8780
           clock speeds: max: 2200 MHz 1: 903 MHz 2: 954 MHz 3: 1049 MHz
           4: 899 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: Fedora X.org 117.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 10.5.4 Direct Rendering: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.0.4-301.fc22.x86_64
Network:   Card-1: Broadcom NetLink BCM57785 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: enp2s0f0 state: down mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak]
           driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 176.3GB (16.8% used)
           ID-1: /dev/sda model: Hitachi_HTS54161 size: 160.0GB
           ID-2: USB /dev/sdb model: SanDisk_Cruzer size: 16.3GB
Partition: ID-1: / size: 74G used: 5.4G (8%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 195 Uptime: 7:27 Memory: 784.6/3805.9MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.391) inxi: 2.2.21 
[me@localhost ~]$ 

```

---

### Post by QDR06VV9 on 2015-06-02
> **kansasnoob said:**
> Which desktop environment are you running on Fedora?

I welcome any and all feedback - it's important to know how far upstream the bug resides :)
[COLOR=#ff0000]Desktop: MATE 1.10.0  Distro: Fedora release 22 
[/COLOR]What burner is used? Could it be CD/DVD Creator? On Fedora they shipped with xfburn.

---

### Post by kansasnoob on 2015-06-02
> **runrickus said:**
> [COLOR=#ff0000]Desktop: MATE 1.10.0  Distro: Fedora release 22 
[/COLOR]What burner is used? Could it be CD/DVD Creator? On Fedora they shipped with xfburn.

AFAIK both Caja and Nautilus provide their own "built-in" CD/DVD Creator (which I never use) so I can't say for sure, but Debian Mate shipped without Brasero or Xfburn. I'm tied up ATM but I think I'll see if the command "top" will show anything when the blank disc is inserted :confused:

Where there's a will there's a way ;)

---

### Post by mc4man on 2015-06-02
Here the error popup appears to come from gvfs, one element would be gvfsd-burn though something calls it I suppose, see screen 
This would be the alt. message when  /usr/lib/gvfs/gvfsd-burn is made unavailable
(sudo mv /usr/lib/gvfs/gvfsd-burn  /usr/lib/gvfs/gvfsd-burn.bak

---

### Post by kansasnoob on 2015-06-03
> **mc4man said:**
> Here the error popup appears to come from gvfs, one element would be gvfsd-burn though something calls it I suppose, see screen 
This would be the alt. message when  /usr/lib/gvfs/gvfsd-burn is made unavailable
(sudo mv /usr/lib/gvfs/gvfsd-burn  /usr/lib/gvfs/gvfsd-burn.bak

So I've been assuming that Nautilus (or Caja) is trying to mount the blank media after gvfs, but from the appearance of that maybe the file manager is mounting the media before gvfs?????

---

### Post by kansasnoob on 2015-06-03
Any idea where gvfs logs would be?

---

### Post by VMC on 2015-06-03
> **kansasnoob said:**
> Any idea where gvfs logs would be?

No idea, but "burn.mount" is *AutoMount=true*, found  under "/usr/share/gvfs/mounts/". What would happen if made false?

---

### Post by VMC on 2015-06-03
I don't have my dvd handy ( i use usb), but when the message appears, is it show up here "/run/user/$uid/gvfs/" ?

---

### Post by mc4man on 2015-06-03
> **VMC said:**
> No idea, but "burn.mount" is *AutoMount=true*, found  under "/usr/share/gvfs/mounts/". What would happen if made false?
That would get rid of the 'error' popup (needs a new session to take affect.
blank media isn't negativity affected by the automount option for gnome, an autorun option is always possible (ask, do nothing, do something) so can't see any reason (yet) while that file shouldn't be set to false

(- in the case of optical media with something on it I think Gnome screwed this up a while back, likely part of their ongoing 'simplification'

---

### Post by kansasnoob on 2015-06-03
> **VMC said:**
> No idea, but "burn.mount" is *AutoMount=true*, found  under "/usr/share/gvfs/mounts/". What would happen if made false?

I see what you mean:

> lance@lance-desktop:~$ cat /usr/share/gvfs/mounts/burn.mount
[Mount]
Type=burn
Exec=/usr/lib/gvfs/gvfsd-burn
AutoMount=true


I'll give it a whirl and see what happens.

---

### Post by kansasnoob on 2015-06-03
Reboot required after changing that but it seems to work:

> lance@lance-desktop:~$ cat /usr/share/gvfs/mounts/burn.mount
[Mount]
Type=burn
Exec=/usr/lib/gvfs/gvfsd-burn
AutoMount=false


That said I want to test this for a few days to be sure there are no other ill effects associated with that change.

---

### Post by QDR06VV9 on 2015-06-03
> **VMC said:**
> No idea, but "burn.mount" is *AutoMount=true*, found  under "/usr/share/gvfs/mounts/". What would happen if made false?

> **kansasnoob said:**
> Reboot required after changing that but it seems to work:



That said I want to test this for a few days to be sure there are no other ill effects associated with that change.

Nice! Great Detective work guys.

---

### Post by kansasnoob on 2015-06-03
I decided to check Precise which was not effected and the same file is set to "true" so the actual "bug" is probably somewhere in some executable file, but if this workaround causes no problems it's certainly simple enough :D

I'm going to apply this workaround to my in-house "stable" Trusty installs which get used a lot for a variety of things and make sure there are no ill effects before I recommend it as a workaround to others though.

---

### Post by QDR06VV9 on 2015-06-03
> **kansasnoob said:**
> I decided to check Precise which was not effected and the same file is set to "true" so the actual "bug" is probably somewhere in some executable file, but if this workaround causes no problems it's certainly simple enough :D

I'm going to apply this workaround to my in-house "stable" Trusty installs which get used a lot for a variety of things and make sure there are no ill effects before I recommend it as a workaround to others though.
Yep was the same on Fedora also, but the work around is working nicely under Trusty And Wily.;)

---

### Post by kansasnoob on 2015-06-03
Sadly I'm finding now that "workaround" only fixes things for one mount. After editing file reboot, then insert blank disc and you get no already mounted warning. But then eject the disc, close the tray again, and the darn warning is back. But we're definitely looking nearly in the right place.

---

### Post by kansasnoob on 2015-06-03
Maybe also need to change "recent.mount"???

---

### Post by kansasnoob on 2015-06-03
Here's what I'm thinking of switching to false:

> lance@lance-desktop:~$ cat /usr/share/gvfs/mounts/recent.mount
[Mount]
Type=recent
Exec=/usr/lib/gvfs/gvfsd-recent
AutoMount=true


Something I notice also is that an auto backup is apparently created for edited files:

```
lance@lance-desktop:~$ ls /usr/share/gvfs/mounts
afc.mount         cdda.mount      gphoto2.mount    recent.mount
afp-browse.mount  computer.mount  http.mount       sftp.mount
afp.mount         dav.mount       localtest.mount  smb-browse.mount
archive.mount     dav+sd.mount    mtp.mount        smb.mount
burn.mount        dns-sd.mount    network.mount    trash.mount
**[COLOR="#FF0000"]burn.mount~[/COLOR]**       ftp.mount       obexftp.mount

```

Not sure if that would interfere with anything :confused:

---

### Post by kansasnoob on 2015-06-03
Nope, editing recent.mount didn't help with repetitive mounts :(

---

### Post by QDR06VV9 on 2015-06-03
I even tired Dougs Suggestion "sudo mv /usr/lib/gvfs/gvfsd-burn  /usr/lib/gvfs/gvfsd-burn.bak"
with the first edit's still in place. And after the second mount right back where we started.:rolleyes:

---

### Post by mc4man on 2015-06-03
> **runrickus said:**
> I even tired Dougs Suggestion "sudo mv /usr/lib/gvfs/gvfsd-burn  /usr/lib/gvfs/gvfsd-burn.bak"
with the first edit's still in place. And after the second mount right back where we started.:rolleyes:

That wasn't a suggestion of a fix, was just a way to affect the popup leading to a conclusion that the *orig.*  pop up was gvfs related..

---

### Post by mc4man on 2015-06-03
> **kansasnoob said:**
> Sadly I'm finding now that "workaround" only fixes things for one mount. After editing file reboot, then insert blank disc and you get no already mounted warning. But then eject the disc, close the tray again, and the darn warning is back. But we're definitely looking nearly in the right place.
Does seem to be the case.
The best solution would be that no optical media is affected in any manner  by /org/gnome/desktop/media-handling/automount & all optical media is controlled only by whatever it is that uses ' Ask .. (default), Do nothing, or Do something ' (as set in  System Settings > Details > Removable Media > ect.

---

### Post by mc4man on 2015-06-03
My bigger issue is I don't want internal partitions automounted but do want optical media with something on it to respond to a set action, be it a vid dvd, audio cd, data disk, ect.
So because upstream could care less I do this - 
2 autostart .desktops, first one is immediate & disables automount, 2nd one is delayed a bit & re-enables it.
ex.
```
[Desktop Entry]
Type=Application
Name=Disable automount
Exec=gsettings set org.gnome.desktop.media-handling automount false
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true

```

```
[Desktop Entry]
Type=Application
Name=Enable automount
Exec=gsettings set org.gnome.desktop.media-handling automount true
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=4
```

---

### Post by QDR06VV9 on 2015-06-03
> **mc4man said:**
> That wasn't a suggestion of a fix, was just a way to affect the popup leading to a conclusion that the *orig.*  pop up was gvfs related..

Oh yes I knew that, but just was trying it out.
You know the old saying "nothing ventured nothing gained"
But it really did not cause the issues I thought it might,"gvfsd-burn.bak" I'm sure down the road a little it for sure it would have.
Thanks Kind Regards

---

### Post by kansasnoob on 2015-06-03
I'm not quite following - I assume you're edits apply to "org/gnome/desktop" but I really don't know where to do that.

I know for instance though with the existing dconf bits & pieces in "org/gnome/desktop" that if I set both "automount" and "automount-open" to false then the "media already mounted" warning goes away. The downside is that doing so interferes with mounting usb drives, cameras, etc.

On another note - a lot of simple things that should work just don't - like changing the default video player from Totem to VLC. Why even provide a GUI if it doesn't work?

> **mc4man said:**
> My bigger issue is I don't want internal partitions automounted but do want optical media with something on it to respond to a set action, be it a vid dvd, audio cd, data disk, ect.
So because upstream could care less I do this - 
2 autostart .desktops, first one is immediate & disables automount, 2nd one is delayed a bit & re-enables it.
ex.
```
[Desktop Entry]
Type=Application
Name=Disable automount
Exec=gsettings set org.gnome.desktop.media-handling automount false
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true

```

```
[Desktop Entry]
Type=Application
Name=Enable automount
Exec=gsettings set org.gnome.desktop.media-handling automount true
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=4
```

---

### Post by mc4man on 2015-06-03
> **kansasnoob said:**
> I'm not quite following - I assume you're edits apply to "org/gnome/desktop" but I really don't know where to do that.

I know for instance though with the existing dconf bits & pieces in "org/gnome/desktop" that if I set both "automount" and "automount-open" to false then the "media already mounted" warning goes away. The downside is that doing so interferes with mounting usb drives, cameras, etc.

On another note - a lot of simple things that should work just don't - like changing the default video player from Totem to VLC. Why even provide a GUI if it doesn't work?
That post was an Ot (off-topic) as the issue you are into here isn't solved  by having the automount option enabled. 
(- it is somewhat by disabling automount but that isn't a solution
So in other words ignore.. at least as far as the double pop up..

Though I do think if all optical media was seperated from the Gnome automount function then it would be good for all.

The issue you are seeing with changing default video player thru the Details panel *may* another bug that has been filed quite some time ago, figured out to some extent & .... zilch
Rather than go into some verbose descript., it revolves around the fact that some mimes have multiple types, this causes that option severe issues. The most common is mp4 which has 3.

Easiest solution is to delete ~/.local/share/applications/mimeapps.list, then either don't use the option, do manually per mime type via context menu > properties Or just do once & don't touch or use the context menu > properties on a mime with multiple listings like mp4
Here's one report about
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1280794](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1280794)

(- I myself will no longer file any Gnome bugs upstream for various reasons, least of which is they don't care about bugs from Ubuntu users on a Gnome 1 or more versions behind what they use. Has become most times a waste of time..

---

### Post by VMC on 2015-06-04
Using Xubuntu 14.04. I just tried inserting a blank dvd into my usb optical drive. I didn't get any pop-up, but it is mounted:```
$ gvfs-mount -o
Monitoring events. Press Ctrl+C to quit.
Drive connected:    'Optiarc DVD RW AD-7231S5'
Drive changed:      'Optiarc DVD RW AD-7231S5'
Drive changed:      'Optiarc DVD RW AD-7231S5'
Volume added:       'Blank DVD-R Disc'
Mount added: 'Blank DVD-R Disc'
Mount changed: 'Blank DVD-R Disc'
Mount added: 'Blank DVD-R Disc'
Mount changed: 'Blank DVD-R Disc'
```

Then when I opened the "door" to remove the media, I got this:
```
Drive changed:      'Optiarc DVD RW AD-7231S5'
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Mount changed: 'CD Drive'
Drive changed:      'Optiarc DVD RW AD-7231S5'
Volume removed:     'CD Drive'
Mount removed: 'CD Drive'
Mount removed: 'CD Drive'
Mount changed: 'CD Drive'
```

---

### Post by kansasnoob on 2015-06-04
> **VMC said:**
> Using Xubuntu 14.04. I just tried inserting a blank dvd into my usb optical drive. I didn't get any pop-up, but it is mounted:```
$ gvfs-mount -o
Monitoring events. Press Ctrl+C to quit.
Drive connected:    'Optiarc DVD RW AD-7231S5'
Drive changed:      'Optiarc DVD RW AD-7231S5'
Drive changed:      'Optiarc DVD RW AD-7231S5'
Volume added:       'Blank DVD-R Disc'
Mount added: 'Blank DVD-R Disc'
Mount changed: 'Blank DVD-R Disc'
Mount added: 'Blank DVD-R Disc'
Mount changed: 'Blank DVD-R Disc'
```

Then when I opened the "door" to remove the media, I got this:
```
Drive changed:      'Optiarc DVD RW AD-7231S5'
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Mount changed: 'CD Drive'
Drive changed:      'Optiarc DVD RW AD-7231S5'
Volume removed:     'CD Drive'
Mount removed: 'CD Drive'
Mount removed: 'CD Drive'
Mount changed: 'CD Drive'
```

Good to know .............. I have a dumb question though, does Xubuntu use gvfs? If you don't mind post the output of:

```
apt-cache policy gvfs
```

I plan on checking Lubuntu soon.

---

### Post by VMC on 2015-06-04
Yes, it does. I believe *gvfs* is used across the board. I wouldn't know its counterpart.
```
$ apt-cache policy gvfs
gvfs:
  Installed: 1.20.3-0ubuntu1
  Candidate: 1.20.3-0ubuntu1
  Version table:
 *** 1.20.3-0ubuntu1 0
        100 /var/lib/dpkg/status
```

---

### Post by QDR06VV9 on 2015-06-04
Great Minds Think Alike.LOL
I had borrowed a **USB CD/DVD writer** and got no errors mounting or ejecting and remounting multiple times.
I have a USB install of Lubuntu that i am going to boot to now and see if it shows the same with onboard CD/DVD Drive.
And Drum Roll Please No Errors on Lubuntu 
Probably of no concern but when I open the file manager I get "burn:///"
```
apt-cache policy gvfs
gvfs:
  Installed: 1.24.1-1ubuntu1
  Candidate: 1.24.1-1ubuntu1
  Version table:
 *** 1.24.1-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status
```

```
$ gvfs-mount -o
Monitoring events. Press Ctrl+C to quit.
Drive changed:      'PIONEER DVD-RW DVRTD11RS'
Drive changed:      'PIONEER DVD-RW DVRTD11RS'
Volume added:       'Blank DVD+RW Disc'
Mount added: 'Blank DVD+RW Disc'
Mount changed: 'Blank DVD+RW Disc'
Mount added: 'Blank DVD+RW Disc'
Mount changed: 'Blank DVD+RW Disc'

```
And after ejecting
```
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Mount changed: 'CD Drive'
Drive changed:      'PIONEER DVD-RW DVRTD11RS'
Volume removed:     'CD Drive'
Mount removed: 'CD Drive'
Mount removed: 'CD Drive'
Mount changed: 'CD Drive'

```
So when mounting a USB CD/DVD writer what changes?(Clue?)

---

### Post by kansasnoob on 2015-06-04
I have a USB optical drive also and it's not affected, sorry I forgot to mention that earlier. But every PC I've tested on that has an internal SATA or IDE optical drive complains when a blank disc is mounted.

---

### Post by kansasnoob on 2015-06-06
I've been reading some of the gvfs info:

[https://wiki.gnome.org/Projects/gvfs/doc](https://wiki.gnome.org/Projects/gvfs/doc)

This jumped out at me:

> Mount spec

Mount spec is a tiny class that helps to identify and match mounts. It carries key-value pairs, e.g. information about URI scheme used, backend type, hostname, port, username, domain etc.

**[COLOR="#FF0000"]Specifically during mount operation two instances of mount spec are used.[/COLOR]** The source one carries requested information and is handed over to the backend's GVfsJobMount operation. It is a backend responsibility to process this mount spec, create a new one based on the source one and send it back to the mount tracker for registration. Backend can filter out some information that are not strictly required and only sets those values required for unique mount identification.

**[COLOR="#FF0000"]Mount spec matching is done by comparing all its values, it must be completely equal. In practice, this also means that e.g. scheme://hostname/ and scheme://username@hostname/ may result in two mounts even if user enters the same username in a credential prompt. There's another limitation in real applications at the moment, requesting mount on scheme://hostname/ wouldn't match with scheme://username@hostname/ at the beginning, when mount tracker is trying to find existing mount since we don't know what username to use at this point. Consequently, when going through the mount process and username is known, we don't have a tool for canceling current mount operation and redirecting ourselves to an active mount.[/COLOR]** 

Now, if only I had a brain :biggrin:

---

### Post by ventrical on 2015-06-07
> **runrickus said:**
> Great Minds Think Alike.LOL
I had borrowed a **USB CD/DVD writer** and got no errors mounting or ejecting and remounting multiple times.
I have a USB install of Lubuntu that i am going to boot to now and see if it shows the same with onboard CD/DVD Drive.
And Drum Roll Please No Errors on Lubuntu 
Probably of no concern but when I open the file manager I get "burn:///"
```
apt-cache policy gvfs
gvfs:
  Installed: 1.24.1-1ubuntu1
  Candidate: 1.24.1-1ubuntu1
  Version table:
 *** 1.24.1-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status
```

```
$ gvfs-mount -o
Monitoring events. Press Ctrl+C to quit.
Drive changed:      'PIONEER DVD-RW DVRTD11RS'
Drive changed:      'PIONEER DVD-RW DVRTD11RS'
Volume added:       'Blank DVD+RW Disc'
Mount added: 'Blank DVD+RW Disc'
Mount changed: 'Blank DVD+RW Disc'
Mount added: 'Blank DVD+RW Disc'
Mount changed: 'Blank DVD+RW Disc'

```
And after ejecting
```
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Volume changed:     'CD Drive'
Mount changed: 'CD Drive'
Mount changed: 'CD Drive'
Drive changed:      'PIONEER DVD-RW DVRTD11RS'
Volume removed:     'CD Drive'
Mount removed: 'CD Drive'
Mount removed: 'CD Drive'
Mount changed: 'CD Drive'

```
So when mounting a USB CD/DVD writer what changes?(Clue?)

That's an awesome lubuntu theme you got there ;) sorry for off topic ..

Regards..

---

### Post by George79 on 2015-11-23
Ubuntu 15.10 64-bits and this bug is still present. My hardware is a [Lenovo GP60NB50 External USB]("http://www.amazon.com/Lenovo-GP60NB50-External-Portable-Burner/dp/B00VUDMPLS").

---

### Post by kansasnoob on 2015-11-23
> **George79 said:**
> Ubuntu 15.10 64-bits and this bug is still present. My hardware is a [Lenovo GP60NB50 External USB]("http://www.amazon.com/Lenovo-GP60NB50-External-Portable-Burner/dp/B00VUDMPLS").

Still present in Xenial too, but FYI this section of the forums is for discussion of the dev version(s) of Ubuntu only ;)

---

