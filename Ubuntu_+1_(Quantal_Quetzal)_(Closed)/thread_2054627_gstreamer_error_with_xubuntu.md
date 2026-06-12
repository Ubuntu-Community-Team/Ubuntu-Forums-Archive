---
title: "gstreamer error with xubuntu"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-09-07
I guess I should just try to install restricted from software center.

---

### Post by mc4man on 2012-09-07
Maybe try a restart
(the bad plugin does dvd but this sounds like possibly a udisks2 deal

---

### Post by ventrical on 2012-09-07
No go. Even switched back to Ubuntu desktop. Tried VLC .. etc..

VLC really buggy with this LONG horizontal window.


```

ventrical@ventrical:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)
ventrical@ventrical:~$ 

```

ignore second screenshot

---

### Post by mc4man on 2012-09-07
Now that I think 2 sec's about,  that error won't be related to mounting or stale mountpoints, ect.

No issue here but only Ubuntu.
> VLC really buggy with this LONG horizontal window.

What do you mean by long?

---

### Post by ventrical on 2012-09-07
And it sort of rolls too...

---

### Post by mc4man on 2012-09-07
You need to take precautions & not let vlc run without an env of LIBOVERLAY_SCROLLBAR=0 or you may get impossibly sized windows.

To test if this is your vlc issue
**First** remove ~/.config/vlc/vlc-qt-interface.conf (screen for reminder
Then start vlc from terminal with this

LIBOVERLAY_SCROLLBAR=0 vlc

If all better then vlc's .desktop can be adjusted & only use above from terminal or create an alias
Edit have some posts on that or can show you here.

---

### Post by ventrical on 2012-09-08
I cannot find the file, nor the directory.

root@ventrical:~# cd .config
[email]root@ventrical:~/.config[/email]# cd vlc
-bash: cd: vlc: No such file or directory
[email]root@ventrical:~/.config[/email]# dir
ibus
[email]root@ventrical:~/.config[/email]#

---

### Post by mc4man on 2012-09-08
.config is a hidden folder in home, ctrl+h exposes them 
or let nautilus take you there
```
nautilus .config/vlc
```

---

### Post by ventrical on 2012-09-08
Ok .. first .. thanks. I thought the nautilus/terminal  was no longer allowed to work. Ok .. great.

 All that worked well. Then , when I went to play the dvd I got this:

```

[0x798108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: ELEKTRA_169
libdvdnav: DVD Serial Number: 324E5186
libdvdnav: DVD Title (Alternative): ELEKTRA_169
libdvdnav: Unable to find map file '/home/ventrical/.dvdnav/ELEKTRA_169.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[0x7f86e4000b78] main input error: ES_OUT_RESET_PCR called
[0x7f86e4000b78] main input error: ES_OUT_RESET_PCR called
libdvdnav: Suspected RCE Region Protection!!!
[0x7f86e4000b78] main input error: ES_OUT_RESET_PCR called
[0x7f86e4000b78] main input error: ES_OUT_RESET_PCR called


```

I mean , it always seems to work on other versions of Ubuntu.

Thanks for your time.

---

### Post by mc4man on 2012-09-08
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If running the env fixed your vlc issue then you cannot run without the env.
If you do so & get the bad windows again then you must again delete that file 
 You should fix your vlc.desktop so you can open vlc normally from menu

simplified method to edit vlc.desktop
[http://ubuntuforums.org/showpost.php?p=12193744&postcount=15](http://ubuntuforums.org/showpost.php?p=12193744&postcount=15)

creating an alias for opening vlc from terminal as just vlc
[http://ubuntuforums.org/showpost.php?p=12189489&postcount=3](http://ubuntuforums.org/showpost.php?p=12189489&postcount=3)

orig post here on this issue & bug link
[http://ubuntuforums.org/showthread.php?t=1988663](http://ubuntuforums.org/showthread.php?t=1988663)

---

### Post by ventrical on 2012-09-08
@mac4man,

Thanks for the tips. Worked great. 

Regards,

Ventrical

---

### Post by mc4man on 2012-09-09
As a small reminder - 
while you've fixed the .desktop & maybe thru a terminal (bash), if you happen to run the vlc binary directly you'll likely get poor behavior.

One way in ubuntu for that to happen is to start vlc from the sound menu which calls the binary, not the .desktop
If that happens just delete that .conf & refrain from whatever called it.

There is a way to dispense with all this by use of a binary redirect, it's actually easy but requires some care if you update or re-install the app. (so won't post, hopefully this will be fixed this month or so.
(- screen shows the idea if you're curious, I just put a new git vlc in  

The symlink 'vlc' calls the helper script 'vlc.helper' which sets the env & then runs the renamed binary, 'vlc.real'

---

### Post by ventrical on 2012-09-09
> **mc4man said:**
> 

There is a way to dispense with all this by use of a binary redirect, it's actually easy but requires some care if you update or re-install the app. (so won't post, hopefully this will be fixed this month or so.

That's good news for sure. :)




Thanks for sharing the intricacies involved. I think it helps us appreciate the work behinds the scenes a little bit more.

Regrards..

---

