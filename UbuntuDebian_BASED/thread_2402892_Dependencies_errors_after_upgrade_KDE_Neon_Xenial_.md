---
title: "Dependencies errors after upgrade KDE Neon Xenial to Bionic"
date: 2018-10-05
forum: Ubuntu/Debian BASED
---

### Post by lighttemplar on 2018-10-05
I did upgrade from KDE Neon Xenial to Bionic. It went with problems because of postfix configuration bug (konsole window must be wide open), so I should restart it and continue manually. *dpkg --configure -a* went good. 
Now, as I have my laptop restarted and launched *sudo apt update && sudo apt full-upgrade*

I don't understand messages, it lists all the same versions but compares xenial against bionic.

How can I solve this puzzle?

[ATTACH]281253[/ATTACH][ATTACH]281254[/ATTACH][ATTACH]281255[/ATTACH]

---

### Post by lighttemplar on 2018-10-05
apt suggests to remove such packages as kwin, plasma-desktop, discover and kinfocenter - are they really thrown away in Bionic?

---

### Post by coffeecat on 2018-10-05
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by lighttemplar on 2018-10-05
So, I made some steps, now there are less problems. 
First, I removed some packages from hold back, which looked old for me: simple-scan and subtitlecomposer 
then I found, that many of packages have higher versions, than those in the ubuntu bionic repositories. And I realized, they was installed from Padoka PPA. So I downgraded them with help of ppa-purge.

For now I have much less errors.
```
Starting pkgProblemResolver with broken count: 6
Starting 2 pkgProblemResolver with broken count: 6
Investigating (0) colord:amd64 < 1.2.12-1ubuntu1 -> 1.3.3-2build1 @ii umU Ib >
Broken colord:amd64 Depends on libsane1:amd64 < none | 1.0.27-1~experimental3ubuntu2 @un uH > (>= 1.0.24)
  Considering libsane1:amd64 0 as a solution to colord:amd64 29
  Holding Back colord:amd64 rather than change libsane1:amd64
Investigating (0) libcurl3:amd64 < 7.47.0-1ubuntu2.9 -> 7.58.0-2ubuntu2 @ii umU Ib >
Broken libcurl3:amd64 Conflicts on libcurl4:amd64 < none -> 7.58.0-2ubuntu3.3 @un uN Ib >
  Considering libcurl4:amd64 4 as a solution to libcurl3:amd64 16
  Added libcurl4:amd64 to the remove list
  Conflicts//Breaks against version 7.58.0-2ubuntu3 for libcurl4 but that is not InstVer, ignoring
  Fixing libcurl3:amd64 via keep of libcurl4:amd64
Investigating (0) vlc-bin:amd64 < none -> 3.0.3-1-1ubuntu1 @un uN Ib >
Broken vlc-bin:amd64 Breaks on vlc-nox:amd64 < 2.2.2-5ubuntu0.16.04.4 @ii mK > (< 3.0.0-1~)
  Considering vlc-nox:amd64 -3 as a solution to vlc-bin:amd64 7
  Added vlc-nox:amd64 to the remove list
  Fixing vlc-bin:amd64 via remove of vlc-nox:amd64
Investigating (0) cryfs:amd64 < 0.9.7-1-ppa5~xenial -> 0.9.9-1ubuntu1 @ii umU Ib >
Broken cryfs:amd64 Depends on libcurl4:amd64 < none | 7.58.0-2ubuntu3.3 @un uH > (>= 7.16.2)
  Considering libcurl4:amd64 4 as a solution to cryfs:amd64 2
  Holding Back cryfs:amd64 rather than change libcurl4:amd64
Investigating (0) orthanc:amd64 < 1.0.0+dfsg-1build1 -> 1.3.1+dfsg-1build2 @ii umU Ib >
Broken orthanc:amd64 Depends on libcurl4:amd64 < none | 7.58.0-2ubuntu3.3 @un uH > (>= 7.16.2)
  Considering libcurl4:amd64 4 as a solution to orthanc:amd64 1
  Holding Back orthanc:amd64 rather than change libcurl4:amd64
Investigating (0) gimagereader:amd64 < 3.1.2+git368fa8f-2build1 -> 3.2.3-2 @ii umU Ib >
Broken gimagereader:amd64 Depends on libsane1:amd64 < none | 1.0.27-1~experimental3ubuntu2 @un uH > (>= 1.0.24)
  Considering libsane1:amd64 0 as a solution to gimagereader:amd64 0
  Holding Back gimagereader:amd64 rather than change libsane1:amd64
Investigating (0) libvlccore8:amd64 < 2.2.2-5ubuntu0.16.04.4 @ii mK Ib >
Broken libvlccore8:amd64 Depends on vlc-data:amd64 < 2.2.2-5ubuntu0.16.04.4 -> 3.0.3-1-1ubuntu1 @ii umU > (= 2.2.2-5ubuntu0.16.04.4)
  Considering vlc-data:amd64 1 as a solution to libvlccore8:amd64 -1
  Removing libvlccore8:amd64 rather than change vlc-data:amd64
 Try to Re-Instate (1) colord:amd64
 Try to Re-Instate (1) cryfs:amd64
 Try to Re-Instate (1) orthanc:amd64
 Try to Re-Instate (1) gimagereader:amd64
Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libass5 libcdio13 libchromaprint0 libdirectfb-1.2-9 libiso9660-10 liblircclient0 liblivemedia50 libomxil-bellagio-bin libomxil-bellagio0
  libpostproc-ffmpeg53 libvcdinfo0
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libvlccore8 vlc-nox
The following NEW packages will be installed:
  gstreamer1.0-gl gstreamer1.0-plugins-bad libaribb24-0 libde265-0 libgps23 libgraphene-1.0-0 libgstreamer-gl1.0-0 libgstreamer-plugins-bad1.0-0
  liblivemedia62 libmicrodns0 libnfs11 libofa0 libopenmpt-modplug1 libplacebo4 libspandsp2 libsrtp2-1 libva-wayland2 libzbar0 vlc-bin vlc-l10n
  vlc-plugin-base vlc-plugin-qt vlc-plugin-skins2 vlc-plugin-video-output vlc-plugin-video-splitter vlc-plugin-visualization
The following packages have been kept back:
  colord cryfs gimagereader orthanc
The following packages will be upgraded:
  gir1.2-gst-plugins-base-1.0 kinfocenter kwayland-data kwin kwin-common kwin-data kwin-x11 libcurl3 libfarstream-0.2-5 libkf5waylandclient5
  libkf5waylandserver5 libkwin4-effect-builtins1 libkwineffects11 libopenjpeg5 libqt5gui5 libqt5gui5-dbgsym plasma-desktop plasma-desktop-data
  plasma-framework plasma-workspace qt5-gtk-platformtheme qtwayland5 sddm-theme-breeze vlc vlc-data
25 upgraded, 26 newly installed, 2 to remove and 4 not upgraded.
```

---

### Post by lighttemplar on 2018-10-05
and the rest was actually simple. I did let apt do, what it wanted, and then last four [[COLOR=#000000][FONT=monospace]colord, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]cryfs, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]orthanc, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]gimagereader[/FONT][/COLOR]] package for package removed, looked, what depends on them, corrected ppas and removed another one package, which I had from .deb installed. 

Congrats me, I did upgrade! 
Now remains the last simplest task: enabling rest ppas. 
We can mark it as solved.

---

### Post by lighttemplar on 2018-10-05
Just for logs:
I had to remove masterPDF, to enable and change repository for R-Project, reinstall Zulucrypt   and something else a little, can't remember

---

### Post by oldos2er on 2018-10-05
> **lighttemplar said:**
> We can mark it as solved.

You can do that under the Thread Tools menu at the top of the page, and thank you.

---

