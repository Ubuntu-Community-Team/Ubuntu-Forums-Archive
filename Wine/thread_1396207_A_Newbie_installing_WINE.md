---
title: "A Newbie installing WINE"
date: 2010-02-01
forum: Wine
---

### Post by Starblaster1234 on 2010-02-01
While trying to install WINE, I received this error:

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

What did I do wrong?

I'd be glad to attempt anything and I have a very nice Internet connection. If you'd like me to run any tests I'll do that too.

Thanks,
Starblaster1234

---

### Post by beastrace91 on 2010-02-01
Crack open terminal and give this a try: 

sudo apt-get install wine1.2

Regards
~Jeff

---

### Post by Starblaster1234 on 2010-02-02
```
:~$ sudo apt-get install wine1.2
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cabextract libmpg123-0 libopenal1 ttf-liberation ttf-mscorefonts-installer
  ttf-symbol-replacement ttf-tahoma-replacement winbind wine1.2-gecko
The following NEW packages will be installed:
  cabextract libmpg123-0 libopenal1 ttf-liberation ttf-mscorefonts-installer
  ttf-symbol-replacement ttf-tahoma-replacement winbind wine1.2 wine1.2-gecko
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.3MB of archives.
After this operation, 103MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net karmic/main ttf-symbol-replacement 1.1.37-0ubuntu2 [53.4kB]
Get:2 http://us.archive.ubuntu.com karmic/universe libmpg123-0 1.7.3-0ubuntu1 [379kB]
Get:3 http://ppa.launchpad.net karmic/main ttf-tahoma-replacement 1.1.37-0ubuntu2 [90.6kB]
Get:4 http://ppa.launchpad.net karmic/main wine1.2 1.1.37-0ubuntu2 [9,077kB]
Get:5 http://us.archive.ubuntu.com karmic/universe libopenal1 1:1.8.466-2 [94.1kB]
Get:6 http://us.archive.ubuntu.com karmic/multiverse wine1.2-gecko 1.0.0-0ubuntu3 [8,123kB]
Get:7 http://us.archive.ubuntu.com karmic/universe cabextract 1.2-3 [55.4kB]
Get:8 http://us.archive.ubuntu.com karmic/main ttf-liberation 1.05.1.20090721-0ubuntu1 [1,038kB]
Get:9 http://us.archive.ubuntu.com karmic/multiverse ttf-mscorefonts-installer 3.0 [35.9kB]
Get:10 http://us.archive.ubuntu.com karmic-updates/main winbind 2:3.4.0-3ubuntu5.4 [4,379kB]
Fetched 23.3MB in 17s (1,313kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package ttf-symbol-replacement.
(Reading database ... 147106 files and directories currently installed.)
Unpacking ttf-symbol-replacement (from .../ttf-symbol-replacement_1.1.37-0ubuntu2_all.deb) ...
Selecting previously deselected package ttf-tahoma-replacement.
Unpacking ttf-tahoma-replacement (from .../ttf-tahoma-replacement_1.1.37-0ubuntu2_all.deb) ...
Selecting previously deselected package libmpg123-0.
Unpacking libmpg123-0 (from .../libmpg123-0_1.7.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libopenal1.
Unpacking libopenal1 (from .../libopenal1_1%3a1.8.466-2_i386.deb) ...
Selecting previously deselected package wine1.2.
Unpacking wine1.2 (from .../wine1.2_1.1.37-0ubuntu2_i386.deb) ...
Selecting previously deselected package wine1.2-gecko.
Unpacking wine1.2-gecko (from .../wine1.2-gecko_1.0.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package cabextract.
Unpacking cabextract (from .../cabextract_1.2-3_i386.deb) ...
Selecting previously deselected package ttf-liberation.
Unpacking ttf-liberation (from .../ttf-liberation_1.05.1.20090721-0ubuntu1_all.deb) ...
Selecting previously deselected package ttf-mscorefonts-installer.
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.0_all.deb) ...
Selecting previously deselected package winbind.
Unpacking winbind (from .../winbind_2%3a3.4.0-3ubuntu5.4_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up ttf-symbol-replacement (1.1.37-0ubuntu2) ...
Setting up ttf-tahoma-replacement (1.1.37-0ubuntu2) ...
Setting up libmpg123-0 (1.7.3-0ubuntu1) ...

Setting up libopenal1 (1:1.8.466-2) ...

Setting up wine1.2 (1.1.37-0ubuntu2) ...
procps stop/waiting

Setting up wine1.2-gecko (1.0.0-0ubuntu3) ...
Setting up cabextract (1.2-3) ...
Setting up ttf-liberation (1.05.1.20090721-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.

Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-02-02 06:53:26--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-02-02 06:53:27--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384      473K/s   in 0.4s    

2010-02-02 06:53:27 (473 KB/s) - `./andale32.exe' saved [198384/198384]

--2010-02-02 06:53:27--  http://downloads.sourceforge.net/corefonts/arialb32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2010-02-02 06:53:28--  http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolving superb-dca2.dl.sourceforge.net... 209.61.193.20
Connecting to superb-dca2.dl.sourceforge.net|209.61.193.20|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/arialb32.exe?download&failedmirror=superb-dca2.dl.sourceforge.net [following]
--2010-02-02 06:53:28--  http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/arialb32.exe?download&failedmirror=superb-dca2.dl.sourceforge.net
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2010-02-02 06:53:28--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/x-msdos-program]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176      881K/s   in 0.2s    

2010-02-02 06:53:28 (881 KB/s) - `./arialb32.exe' saved [168176/168176]

--2010-02-02 06:53:28--  http://downloads.sourceforge.net/corefonts/arial32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2010-02-02 06:53:28--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 65.49.46.188
Connecting to cdnetworks-us-2.dl.sourceforge.net|65.49.46.188|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

100%[======================================>] 554,208      433K/s   in 1.3s    

2010-02-02 06:53:30 (433 KB/s) - `./arial32.exe' saved [554208/554208]

--2010-02-02 06:53:30--  http://downloads.sourceforge.net/corefonts/comic32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2010-02-02 06:53:30--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/octet-stream]
Saving to: `./comic32.exe'

100%[======================================>] 246,008     1.29M/s   in 0.2s    

2010-02-02 06:53:30 (1.29 MB/s) - `./comic32.exe' saved [246008/246008]

--2010-02-02 06:53:30--  http://downloads.sourceforge.net/corefonts/courie32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2010-02-02 06:53:31--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/x-msdos-program]
Saving to: `./courie32.exe'

100%[======================================>] 646,368     1.45M/s   in 0.4s    

2010-02-02 06:53:31 (1.45 MB/s) - `./courie32.exe' saved [646368/646368]

--2010-02-02 06:53:31--  http://downloads.sourceforge.net/corefonts/georgi32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2010-02-02 06:53:31--  http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Resolving superb-dca2.dl.sourceforge.net... 209.61.193.20
Connecting to superb-dca2.dl.sourceforge.net|209.61.193.20|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/georgi32.exe?download&failedmirror=superb-dca2.dl.sourceforge.net [following]
--2010-02-02 06:53:31--  http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/georgi32.exe?download&failedmirror=superb-dca2.dl.sourceforge.net
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2010-02-02 06:53:32--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `./georgi32.exe'

100%[======================================>] 392,440     1.40M/s   in 0.3s    

2010-02-02 06:53:32 (1.40 MB/s) - `./georgi32.exe' saved [392440/392440]

--2010-02-02 06:53:32--  http://downloads.sourceforge.net/corefonts/impact32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following]
--2010-02-02 06:53:32--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `./impact32.exe'

100%[======================================>] 173,288     1.06M/s   in 0.2s    

2010-02-02 06:53:32 (1.06 MB/s) - `./impact32.exe' saved [173288/173288]

--2010-02-02 06:53:33--  http://downloads.sourceforge.net/corefonts/times32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following]
--2010-02-02 06:53:33--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

100%[======================================>] 661,728      861K/s   in 0.8s    

2010-02-02 06:53:34 (861 KB/s) - `./times32.exe' saved [661728/661728]

--2010-02-02 06:53:34--  http://downloads.sourceforge.net/corefonts/trebuc32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following]
--2010-02-02 06:53:34--  http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe
Resolving superb-sea2.dl.sourceforge.net... 209.160.57.180
Connecting to superb-sea2.dl.sourceforge.net|209.160.57.180|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/trebuc32.exe?download&failedmirror=superb-sea2.dl.sourceforge.net [following]
--2010-02-02 06:53:34--  http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/trebuc32.exe?download&failedmirror=superb-sea2.dl.sourceforge.net
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following]
--2010-02-02 06:53:34--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `./trebuc32.exe'

100%[======================================>] 357,200      635K/s   in 0.5s    

2010-02-02 06:53:35 (635 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2010-02-02 06:53:35--  http://downloads.sourceforge.net/corefonts/verdan32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following]
--2010-02-02 06:53:35--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/x-msdos-program]
Saving to: `./verdan32.exe'

100%[======================================>] 351,992     1.24M/s   in 0.3s    

2010-02-02 06:53:36 (1.24 MB/s) - `./verdan32.exe' saved [351992/351992]

--2010-02-02 06:53:36--  http://downloads.sourceforge.net/corefonts/webdin32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following]
--2010-02-02 06:53:36--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 65.49.46.188
Connecting to cdnetworks-us-2.dl.sourceforge.net|65.49.46.188|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

100%[======================================>] 185,072      265K/s   in 0.7s    

2010-02-02 06:53:37 (265 KB/s) - `./webdin32.exe' saved [185072/185072]

andale32.exe: OK
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: OK
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: OK
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: OK
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: OK
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
georgi32.exe: OK
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: OK
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
times32.exe: OK
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
trebuc32.exe: OK
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
verdan32.exe: OK
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
webdin32.exe: OK
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.

Setting up winbind (2:3.4.0-3ubuntu5.4) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Looks to me that it went through okay....am I correct?

---

### Post by avajesh on 2010-02-02
install msttcorefonts also after installing wine.

---

### Post by beastrace91 on 2010-02-02
> **Starblaster1234 said:**
> 
Looks to me that it went through okay....am I correct?

Correct, you should be good to go :)

~Jeff

---

