---
title: "held packages"
date: 2015-06-15
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2015-06-15
So just doing my normal updates have been seeing a few held packages that wont come in with dist-upgrade mostly kernels,
But today i Get the following.
```
ud2 (witch is an alias sudo apt-get dist-upgrade)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.0.0-1 linux-headers-4.0.0-1-generic
  linux-image-4.0.0-1-generic linux-image-extra-4.0.0-1-generic
[COLOR=#0000cd]The following packages have been kept back:
  metacity-common[/COLOR]
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.


The following packages will be REMOVED:
  linux-headers-3.19.0-20 linux-headers-3.19.0-20-generic
  linux-image-3.19.0-20-generic linux-image-extra-3.19.0-20-generic
0 upgraded, 0 newly installed, 4 to remove and 1 not upgraded.
After this operation, 289 MB disk space will be freed.
(Reading database ... 259313 files and directories currently installed.)
Removing linux-headers-3.19.0-20-generic (3.19.0-20.20) ...
Removing linux-headers-3.19.0-20 (3.19.0-20.20) ...
Removing linux-image-extra-3.19.0-20-generic (3.19.0-20.20) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.0.0-1-generic
Found initrd image: /boot/initrd.img-4.0.0-1-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
Found Fedora release 22 (Twenty Two) on /dev/sda1
done
Removing linux-image-3.19.0-20-generic (3.19.0-20.20) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.0.0-1-generic
Found initrd image: /boot/initrd.img-4.0.0-1-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
Found Fedora release 22 (Twenty Two) on /dev/sda1
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
me@me-Aspire-5750:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.0.0-1-generic
Found initrd image: /boot/initrd.img-4.0.0-1-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
Found Fedora release 22 (Twenty Two) on /dev/sda1
grdone
me@me-Aspire-5750:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.0.0-1-generic
Found initrd image: /boot/initrd.img-4.0.0-1-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
rmdir: failed to remove ‘/var/lib/os-prober/mount’: Device or resource busy
Found Fedora release 22 (Twenty Two) on /dev/sda1
done
me@me-Aspire-5750:~$ 
```
Proceeded with the updates and upgrades and all is good so I guess I'm just reporting, the os prober report is always around when ever i have a Fedora
 partition in grub but the metacity-common was new.
Cheers

---

### Post by dino99 on 2015-06-15
> **runrickus said:**
> The following packages have been kept back:  metacity-common 
Proceeded with the updates and upgrades and all is good so I guess I'm just reporting, the os prober report is always around when ever i have a Fedora
 partition in grub but the metacity-common was new.
Cheers

Compiz still needs to be rebuilt due to the new metacity. So waiting for compiz to be able to upgrade metacity.
lp:[lpbug]1463645[/lpbug]

---

### Post by QDR06VV9 on 2015-06-15
Good Info Thanks!

---

### Post by v3.xx on 2015-06-15
> **runrickus said:**
> Good Info Thanks!
Yes, good info.

Just updated too.  Still on the 3.19 kernel, 4.0 not offered.

---

### Post by ajgreeny on 2015-06-15
> **v3.xx said:**
> Yes, good info.

Just updated too.  Still on the 3.19 kernel, 4.0 not offered.
Same here, and at the moment wily is kind of boring; nothing seems to be breaking, and I always expect breakages with a development version.

---

### Post by QDR06VV9 on 2015-06-15
> **v3.xx said:**
> Yes, good info.

Just updated too.  Still on the 3.19 kernel, 4.0 not offered.
I switched to Main Sever and I have Proposed Enabled.
But I it is funny to see others receiving updates or New Packages faster than others.
Kind Regards

---

### Post by cecilpierce on 2015-06-24
I did dist-upgrade by mistake and lost desktop except for background screen.
Any way to fix it ?

---

### Post by dino99 on 2015-06-24
> **cecilpierce said:**
> I did dist-upgrade by mistake and lost desktop except for background screen.
Any way to fix it ?

try reinstalling your faulty DE (sudo dpkg-reconfigure unity/gnome/shell/...)

---

### Post by cecilpierce on 2015-06-24
Says "unity is broken or not fully installed"

---

### Post by cecilpierce on 2015-06-24
I guess when all fails, re-install.

Thanks dino99

---

### Post by dino99 on 2015-06-24
> **cecilpierce said:**
> I guess when all fails, re-install.

Thanks dino99

yes if you wish and have time; but you also can:

can uninstall the unity packages from 'synaptic' for example (some are not uninstallable due to cross dependencies)
then downgrade some packages if they have been picked from ppa(s)
then reinstall unity
or use gnome-shell (or else :p)

---

### Post by v3.xx on 2015-06-24
> **dino99 said:**
> Compiz still needs to be rebuilt due to the new metacity. So waiting for compiz to be able to upgrade metacity.
lp:1463645

So has anyone tried compiz yet?  I have not.

---

### Post by dino99 on 2015-06-24
> **v3.xx said:**
> So has anyone tried compiz yet?  I have not.

the opened bug is waiting for lead Marco to approve the changes; but he has not been back yet. So waiting; maybe an other leader will bypass that step, who knows ?

---

### Post by QDR06VV9 on 2015-06-24
> **v3.xx said:**
> So has anyone tried compiz yet?  I have not.
Works good here, on intel drivers and nvidia.

---

### Post by cecilpierce on 2015-06-24
> **dino99 said:**
> yes if you wish and have time; but you also can:

can uninstall the unity packages from 'synaptic' for example (some are not uninstallable due to cross dependencies)
then downgrade some packages if they have been picked from ppa(s)
then reinstall unity
or use gnome-shell (or else :p)

Going to try GS and see if I can get that working for the heck of it !

p.s.
Ilike GS better then unity :p

---

### Post by v3.xx on 2015-06-24
> **dino99 said:**
> the opened bug is waiting for lead Marco to approve the changes; but he has not been back yet. So waiting; maybe an other leader will bypass that step, who knows ?
The only compiz/marco bug I am finding, seems unrelated.  What link are you looking at?

@runrickus
Yes, maybe time to throw it in the pot.

---

### Post by cecilpierce on 2015-06-24
Well GS is working until compiz gets fixed, thanks dino99.

---

### Post by QDR06VV9 on 2015-06-24
> **v3.xx said:**
> The only compiz/marco bug I am finding, seems unrelated.  What link are you looking at?

@runrickus
Yes, maybe time to throw it in the pot.

Maybe you misunderstood him Marco is the lead developer for that team.
Kind regards

---

### Post by dino99 on 2015-06-24
> **cecilpierce said:**
> Well GS is working until compiz gets fixed, thanks dino99.

Hello Miami, you makes me dream  ):P

---

### Post by v3.xx on 2015-06-24
> **runrickus said:**
> Maybe you misunderstood him Marco is the lead developer for that team.
Kind regards

Yes I did misunderstand, thanks

---

### Post by ventrical on 2015-06-26
> **v3.xx said:**
> So has anyone tried compiz yet?  I have not.

I have had compiz working ok since vivid. Yesterday I decided to try the 3D windows option and now the desktop is gone.

Regards..

---

### Post by v3.xx on 2015-06-26
> **ventrical said:**
> I have had compiz working ok since vivid. Yesterday I decided to try the 3D windows option and now the desktop is gone.
Similar results here.  I was in the process of adding my compiz plugins when the desktop crashed.  3D windows was not included in mine.

---

### Post by QDR06VV9 on 2015-06-26
I have the same results with Desktop Cube and 3D Desktop
But the rest of the plugins function with good results, I should have mentioned that earlier.:rolleyes:
Regards

---

### Post by dino99 on 2015-06-27
Approvals are done now; pre-built into the cooking lab :p  we should get compiz soon into the wily archive

> Changelog
compiz (1:0.9.12.1+15.10.20150627.1-0ubuntu1) wily; urgency=medium

  [ Alberts Muktup&#257;vels ]
  * Add support for metacity 3.16. (LP: #1463645)

  [ CI Train Bot ]
  * New rebuild forced.

  [ Eleni Maria Stea ]
  * removed unnecessary glClear which causes bug #1462612 (LP: #1462612)

  [ Martin Wimpress ]
  * Tweak the shadows so subtle drop shadows appears on menus, just as
    they do in Macro.  Change from Shift Switcher to Static Switcher
    because Shift Switcher is causing Compiz to crash, particularly when
    switching while Steam is running.

  [ Stephen M. Webb ]
  * remove a bashism from the xsession set-profile script (LP: #1460324)


---

### Post by dino99 on 2015-06-29
Compiz have finally landed into the repo; and metacity upgrade is now done

---

### Post by QDR06VV9 on 2015-06-29
```
The following packages will be REMOVED:
  libmetacity-private2
The following NEW packages will be installed:
  libmetacity-private3
The following packages will be upgraded:
  compiz compiz-core compiz-dev compiz-gnome compiz-plugins
  compiz-plugins-default libcompizconfig0 libdecoration0 libdecoration0-dev
  metacity-common
10 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
```
Desktop Cube on intel Drivers now works.
3D Desktop still crashes. The 3D Desktop works somewhat on Nvidia Drivers.(Distorted)
Regards

---

### Post by v3.xx on 2015-06-29
Also have compiz running (no 3d desktop).  Seems to use a lot of cpu at times with default plugins, but running ok.

---

### Post by v3.xx on 2015-06-29
I can change any part of my compiz theme except the window border.  It will select, but not change.

---

### Post by muktupavels on 2015-06-29
> **v3.xx said:**
> I can change any part of my compiz theme except the window border.  It will select, but not change.

If you are using session that use gtk-window-decorator with metacity theme then you need update/change theme setting under org.gnome.metacity. If that is not your problem, then just ignore. :)

---

### Post by v3.xx on 2015-06-29
> **albertsmuktupavels said:**
> If you are using session that use gtk-window-decorator with metacity theme then you need update/change theme setting under org.gnome.metacity.
No not the case.  Running marco and the org.gnome.metacity theme setting does not apply.  Maybe a screenshot would better explain.
[ATTACH=CONFIG]262929[/ATTACH]
The other tabs work, just the "Window Border" cannot be changed.

When I start compiz from terminal I get this:
```
compiz (core) - Info: Loading plugin: staticswitcher
compiz (core) - Info: Starting plugin: staticswitcher
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
```

---

### Post by QDR06VV9 on 2015-06-29
> **v3.xx said:**
> No not the case.  Running marco and the org.gnome.metacity theme setting does not apply.  Maybe a screenshot would better explain.
[ATTACH=CONFIG]262929[/ATTACH]
The other tabs work, just the "Window Border" cannot be changed.

When I start compiz from terminal I get this:
```
compiz (core) - Info: Loading plugin: staticswitcher
compiz (core) - Info: Starting plugin: staticswitcher
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
```
This may not be the desired result you want, but may I suggest Emerald theme manager?
How to
 ```
sudo apt-add-repository ppa:noobslab/themes
 sudo apt-get update
 sudo apt-get install emerald
```
There is still a good selection of themes on gnomelook.org or deviant art.
If you decide for that option to call emerald
```
emerald --replace
```
Which of course can be added in startup applications
Or added to ccsm under Window decorations>commands>"emerald --replace &"
I added a screeny
Kind Regards

---

### Post by QDR06VV9 on 2015-06-29
Sorry Double post waited for about 7 mins waiting for the post to take which has been going for a week or more
Not complaining just mention.:p 
I know this is not the desired result you are looking for, But may I suggest Emerald Theme Manager.
To install Emerald
```
sudo apt-add-repository ppa:noobslab/themes

sudo apt-get update

sudo apt-get install emerald
```  
To call emerald
```
emerald --replace
```
If you decide that is something you want you can add to startup applications or ad to ccsm
Window decorations>command>emerald --replace & I added some screenshots to aide if needed
Kind Regards

---

### Post by muktupavels on 2015-06-29
> **v3.xx said:**
> No not the case.  Running marco and the org.gnome.metacity theme setting does not apply.  Maybe a screenshot would better explain.
[ATTACH=CONFIG]262929[/ATTACH]
The other tabs work, just the "Window Border" cannot be changed.

When I start compiz from terminal I get this:
```
compiz (core) - Info: Loading plugin: staticswitcher
compiz (core) - Info: Starting plugin: staticswitcher
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
```

Just try to change org.gnome.metacity theme to name you want to set...

GNOME has org.gnome.desktop.wm.preferences theme setting that was used for "Window Border". In 3.16 mutter switcher to use GTK+ theme so org.gnome.desktop.wm.preferences theme setting is unused by GNOME. That means it will be removed in future. I decided to "move" theme setting to org.gnome.metacity in 3.16 not wait until it will be removed. So metacity 3.16 and newer will ignore org.gnome.desktop.wm.preferences theme setting and use only org.gnome.metacity theme.

I am guessing that you are running gtk-window-decorator (compiz), right? It used to use org.gnome.desktop.wm.preferences theme, but since it will be removed I decided to update gwd too - so it now use org.gnome.metacity theme to get theme for windows borders (and it makes sense since you can not get metacity theme support without metacity).

In your screenshot you just change theme for windows borders... It is 99.99% that it changes org.gnome.desktop.wm.preferences theme setting, but it is now ignored by gtk-window-decorator. At this moment your only option is to used dconf-editor or gsettings from terminal to update theme settings with desired theme under org.gnome.metacity.

---

### Post by mc4man on 2015-06-29
> **v3.xx said:**
> No not the case.  Running marco and the org.gnome.metacity theme setting does not apply.  Maybe a screenshot would better explain.
....
The other tabs work, just the "Window Border" cannot be changed.


Seems to work fine here in Appearance Preferences > Customize > any  of the window borders can be selected & it changes. This is with either marco or compiz
Don't see point of switching to/starting compiz from terminal, works better from mate tweak menu, ie. retains the chosen window deco
(- though can't see using marco over compiz anyway, at least here marco =  h tearing

---

### Post by v3.xx on 2015-06-30
@albertsmuktupavels
> Just try to change org.gnome.metacity theme to name you want to set...
Yes, you are right.  Changing the metacity theme will affect the compiz theme.  So for now, thats my work-a-round.

@mc4man
> Seems to work fine here in Appearance Preferences > Customize > any of the window borders can be selected & it changes.
Thats the way my 14o4 install works, but not wily.  I think for now compiz is up and running, but still needing work.

---

### Post by QDR06VV9 on 2015-07-01
today's updates brings in new held package
```
The following packages have been kept back:
  usb-modeswitch-data

```
Have not seen this one since trusty.
Just reporting.
regards

---

