---
title: "Fonts Microsoft and other"
date: 2022-05-14
forum: Ubuntu/Debian BASED
---

### Post by ray42 on 2022-05-14
System: Pop OS 22.04LTS

I have installed:

```

[COLOR=#444444][FONT=&quot]sudo apt install ttf-mscorefonts-installer
[/FONT][/COLOR]
```

Lots of sites give the exact same procedure, this installs without fault but does not show any new fonts.

Also I get lots of fonts listed for Noto (lots and lots). 

Q: Can I remove undesirable fonts, are they needed for system?
Q: What is going on with the perfect installation of MS fonts?

---

### Post by mIk3_08 on 2022-05-14
> **ray42 said:**
> System: Pop OS 22.04LTS

I have installed:

```

[COLOR=#444444][FONT=&amp]sudo apt install ttf-mscorefonts-installer
[/FONT][/COLOR]
```

Lots of sites give the exact same procedure, this installs without fault but does not show any new fonts.

Also I get lots of fonts listed for Noto (lots and lots). 

Q: Can I remove undesirable fonts, are they needed for system?
Q: What is going on with the perfect installation of MS fonts?
For me, I always do a manual install. Go to you Ubuntu System folder and /Font folder then put there you downloaded font. Good Luck and Cheers.

---

### Post by ray42 on 2022-05-22
I don't understand the issue but some users are experiencing a similar issue.

[https://www.reddit.com/r/pop_os/comments/uhwcfd/microsoft_fonts_error_when_installed_on_2204_lts/](https://www.reddit.com/r/pop_os/comments/uhwcfd/microsoft_fonts_error_when_installed_on_2204_lts/)

---

### Post by #&amp;thj^% on 2022-05-22
here's the DL: [https://pkgs.org/download/ttf-mscorefonts-installer](https://pkgs.org/download/ttf-mscorefonts-installer)

---

### Post by ray42 on 2022-05-23
Aha! I get an error see image:

[https://pasteboard.co/D68Z4eAr7dg5.png](https://pasteboard.co/D68Z4eAr7dg5.png)

It does install with Sudo but doesn't work, there are no fonts to view or use. So my previous post still stands. I had the exact same error for Day Planner. So stuff is missing in Pop 22.04LTS to allow it to install.

See previous post:

[https://ubuntuforums.org/showthread.php?t=2474789](https://ubuntuforums.org/showthread.php?t=2474789)

---

### Post by iamjiwjr on 2022-05-23
I install Synaptic. Inside Synaptic I search and install ubuntu-restricted-addons and ubuntu-restricted extras. It installs the MS fonts, additional media codecs, and other goodies. I just did a fresh install today and it  worked great.

---

### Post by #&amp;thj^% on 2022-05-23
> So stuff is missing in Pop 22.04LTS to allow it to install.
I just did this for friend that use's PopOS
I used this to install them:
```
sudo apt install --reinstall ttf-mscorefonts-installer
```
then I cached/genrerated them with:
```
sudo fc-cache -fv
```
Then I noticed there was no place to accept the EULA.
What worked for me was:
```
echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | sudo debconf-set-selections
sudo apt-get install ttf-mscorefonts-installer
```
That seemed to work for him.
If you still can't make work, just use this from Debian.
```
wget http://ftp.us.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.8_all.deb
```
install with:
```
sudo dkpg -i ttf-mscorefonts-installer_3.8_all.deb
```
Run the above in the same Directory the Download was located.
You may be missing some packages on your end as well:
so it won't hurt to:
```
sudo apt install libmspack0 cabextract
```

---

### Post by SeijiSensei on 2022-05-23
This must be a "feature" of PopOS.  I'm running KDE Neon 5.24, which is Ubuntu 20.04 plus the most up-to-date Plasma desktop.  I installed the fonts by my usual method:
```
sudo apt install ttf-mscorefonts-installer
```

The installer pops up a licensing agreement in text mode with an [OK] box at the bottom. You have to use Tab to get the box, then click Enter. You'll get a second text mode window which asks you to confirm your installation. I confirmed. Now if I go to the Fonts app in KDE (System Settings > Appearance > Fonts), all the MS fonts are there. They didn't appear in LibreOffice Writer until I rebooted.

---

### Post by ray42 on 2022-05-23
Thanks folks, it seems there is a deeper issue, I have chatted with a member on [https://chat.pop-os.org/](https://chat.pop-os.org/) and he has the same issue with the same OS release.

---

### Post by ray42 on 2022-05-24
I have other fonts issues. What can be deleted from fonts. I assume some are system fonts? How do I know which is which?

Also this MS font issue I tried the advice after install and used:

```

sudo fc-cache -f -v

```

This is the output:

```

/usr/share/fonts: caching, new cache contents: 0 fonts, 6 dirs/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 89 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cMap: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 5 dirs
/usr/share/fonts/cmap/adobe-cns1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-gb1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-korea1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/opentype: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/opentype/fira: caching, new cache contents: 97 fonts, 0 dirs
/usr/share/fonts/opentype/noto: caching, new cache contents: 80 fonts, 0 dirs
/usr/share/fonts/opentype/urw-base35: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 11 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/truetype/dejavu: caching, new cache contents: 22 fonts, 0 dirs
/usr/share/fonts/truetype/droid: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/liberation2: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/libreoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype/noto: caching, new cache contents: 308 fonts, 0 dirs
/usr/share/fonts/truetype/roboto-slab: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu: caching, new cache contents: 14 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/urw-base35: caching, new cache contents: 35 fonts, 0 dirs
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/root/.local/share/fonts: skipping, no such directory
/root/.fonts: skipping, no such directory
/usr/share/fonts/X11: skipping, looped directory detected
/usr/share/fonts/cMap: skipping, looped directory detected
/usr/share/fonts/cmap: skipping, looped directory detected
/usr/share/fonts/opentype: skipping, looped directory detected
/usr/share/fonts/truetype: skipping, looped directory detected
/usr/share/fonts/type1: skipping, looped directory detected
/usr/share/fonts/X11/Type1: skipping, looped directory detected
/usr/share/fonts/X11/encodings: skipping, looped directory detected
/usr/share/fonts/X11/misc: skipping, looped directory detected
/usr/share/fonts/X11/util: skipping, looped directory detected
/usr/share/fonts/cmap/adobe-cns1: skipping, looped directory detected
/usr/share/fonts/cmap/adobe-gb1: skipping, looped directory detected
/usr/share/fonts/cmap/adobe-japan1: skipping, looped directory detected
/usr/share/fonts/cmap/adobe-japan2: skipping, looped directory detected
/usr/share/fonts/cmap/adobe-korea1: skipping, looped directory detected
/usr/share/fonts/opentype/fira: skipping, looped directory detected
/usr/share/fonts/opentype/noto: skipping, looped directory detected
/usr/share/fonts/opentype/urw-base35: skipping, looped directory detected
/usr/share/fonts/truetype/arphic: skipping, looped directory detected
/usr/share/fonts/truetype/dejavu: skipping, looped directory detected
/usr/share/fonts/truetype/droid: skipping, looped directory detected
/usr/share/fonts/truetype/freefont: skipping, looped directory detected
/usr/share/fonts/truetype/liberation: skipping, looped directory detected
/usr/share/fonts/truetype/liberation2: skipping, looped directory detected
/usr/share/fonts/truetype/libreoffice: skipping, looped directory detected
/usr/share/fonts/truetype/msttcorefonts: skipping, looped directory detected
/usr/share/fonts/truetype/noto: skipping, looped directory detected
/usr/share/fonts/truetype/roboto-slab: skipping, looped directory detected
/usr/share/fonts/truetype/ubuntu: skipping, looped directory detected
/usr/share/fonts/type1/gsfonts: skipping, looped directory detected
/usr/share/fonts/type1/urw-base35: skipping, looped directory detected
/usr/share/fonts/X11/encodings/large: skipping, looped directory detected
/var/cache/fontconfig: cleaning cache directory
/root/.cache/fontconfig: not cleaning non-existent cache directory
/root/.fontconfig: not cleaning non-existent cache directory
fc-cache: succeeded

```

Q: Why a non-existent directory, and why looped?

---

### Post by Holger_Gehrke on 2022-05-24
The non-existent directories are user-specific directories for fonts which may or may not exist for a given user. Since you're executing fc-cache with sudo it's looking for fonts in root's home directory and there aren't any fonts there.
The loops are probably the result of following some symbolic links. If the looping wasn't detected some fonts would be cached twice with different paths to find the exact same font ...

Holger

---

### Post by #&amp;thj^% on 2022-05-24
> **Holger_Gehrke said:**
> The non-existent directories are user-specific directories for fonts which may or may not exist for a given user. Since you're executing fc-cache with sudo it's looking for fonts in root's home directory and there aren't any fonts there.
The loops are probably the result of following some symbolic links. If the looping wasn't detected some fonts would be cached twice with different paths to find the exact same font ...

Holger

+1 well said.
@ray42 Sorry maybe too many cooks here, confusing you now.
I just install 22.04 in a KVM, for testing, all went well with:
```
apt policy libmspack0 cabextract
libmspack0:
  Installed: (none)
  Candidate: 0.10.1-2build2
  Version table:
     0.10.1-2build2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
cabextract:
  Installed: (none)
  Candidate: 1.9-3
  Version table:
     1.9-3 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
As I pointed earlier the needed packages, but no reply back from you.
On with the install.
```
echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | sudo debconf-set-selections

```
EULA is now approved for your system, we go to:
```
sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  cabextract libmspack0
The following NEW packages will be installed:
  cabextract libmspack0 ttf-mscorefonts-installer
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 87.9 kB of archives.
After this operation, 276 kB of additional disk space will be used.
Do you want to continue? [Y/n] 


```
hit enter:
Now you will see what fonts are installed:
```
Get:1 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libmspack0 amd64 0.10.1-2build2 [39.6 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 cabextract amd64 1.9-3 [23.4 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu jammy/multiverse amd64 ttf-mscorefonts-installer all 3.8ubuntu2 [24.9 kB]
Fetched 87.9 kB in 1s (114 kB/s)                    
Preconfiguring packages ...
Selecting previously unselected package libmspack0:amd64.
(Reading database ... 222918 files and directories currently installed.)
Preparing to unpack .../libmspack0_0.10.1-2build2_amd64.deb ...
Unpacking libmspack0:amd64 (0.10.1-2build2) ...
Selecting previously unselected package cabextract.
Preparing to unpack .../cabextract_1.9-3_amd64.deb ...
Unpacking cabextract (1.9-3) ...
Selecting previously unselected package ttf-mscorefonts-installer.
Preparing to unpack .../ttf-mscorefonts-installer_3.8ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.8ubuntu2) ...
Setting up libmspack0:amd64 (0.10.1-2build2) ...
Setting up cabextract (1.9-3) ...
Setting up ttf-mscorefonts-installer (3.8ubuntu2) ...
Processing triggers for update-notifier-common (3.192.54) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [198 kB]
Fetched 198 kB in 1s (195 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arial32.exe [554 kB]
Fetched 554 kB in 2s (326 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arialb32.exe [168 kB]
Fetched 168 kB in 1s (275 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
Get:1 http://downloads.sourceforge.net/corefonts/comic32.exe [246 kB]
Fetched 246 kB in 1s (420 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
Get:1 http://downloads.sourceforge.net/corefonts/courie32.exe [646 kB]
Fetched 646 kB in 1s (942 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
Get:1 http://downloads.sourceforge.net/corefonts/georgi32.exe [392 kB]
Fetched 392 kB in 1s (295 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
Get:1 http://downloads.sourceforge.net/corefonts/impact32.exe [173 kB]
Fetched 173 kB in 1s (221 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
Get:1 http://downloads.sourceforge.net/corefonts/times32.exe [662 kB]
Fetched 662 kB in 1s (1,002 kB/s)                                              
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
Get:1 http://downloads.sourceforge.net/corefonts/trebuc32.exe [357 kB]
Fetched 357 kB in 1s (475 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe
Get:1 http://downloads.sourceforge.net/corefonts/verdan32.exe [352 kB]
Fetched 352 kB in 1s (576 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe
Get:1 http://downloads.sourceforge.net/corefonts/webdin32.exe [185 kB]
Fetched 185 kB in 2s (122 kB/s)                                                

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: /var/lib/update-notifier/package-data-downloads/partial/webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Processing triggers for libc-bin (2.35-0ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for fontconfig (2.13.1-4.2ubuntu5) ...

```
I've had 2 other PopOS users confrim this works for them.
Good Luck
```
 apt policy ttf-mscorefonts-installer
ttf-mscorefonts-installer:
  Installed: 3.8ubuntu2
  Candidate: 3.8ubuntu2
  Version table:
 *** 3.8ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/multiverse i386 Packages
        100 /var/lib/dpkg/status

```

---

