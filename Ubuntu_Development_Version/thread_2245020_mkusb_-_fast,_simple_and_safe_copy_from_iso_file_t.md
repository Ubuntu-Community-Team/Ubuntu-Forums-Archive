---
title: "mkusb - fast, simple and safe copy from iso file to pendrive for iso testing"
date: 2014-09-20
forum: Ubuntu Development Version
---

### Post by sudodus on 2014-09-20
I have made ***mkusb*** more user friendly, and I think that it is quite convenient now to make USB pendrives. It is described at this link

[https://help.ubuntu.com/community/mkusb/isotesting](https://help.ubuntu.com/community/mkusb/isotesting)

This method works well for me, so I want to share it.

-o-

I was also reading about the interesting method(s) discussed in the following link
[URL="http://ubuntuforums.org/showthread.php?t=2244584"]
Installing Utopic[/URL]

which is showing a good alternative, at least if there will be a tutorial how to make it work:

 > **matt_symes said:**
> 
i can and do install ISOs onto my machines by PXE booting into the live ISO environment and installing over NFS.


---

### Post by sudodus on 2014-09-22
If you prefer a simple text interface, try ***mkusb-nox*** 'No X', described at [this link in our forums]("http://ubuntuforums.org/showthread.php?t=1958073&page=4&p=13126863#post13126863") and this [link to an Ubuntu community wiki page]("https://help.ubuntu.com/community/mkusb/v7").

---

### Post by ventrical on 2014-09-23
> **sudodus said:**
> I have made ***mkusb*** more user friendly, and I think that it is quite convenient now to make USB pendrives. It is described at this link

[https://help.ubuntu.com/community/mkusb/isotesting](https://help.ubuntu.com/community/mkusb/isotesting)

This method works well for me, so I want to share it.

-o-

I was also reading about the interesting method(s) discussed in the following link
[URL="http://ubuntuforums.org/showthread.php?t=2244584"]
Installing Utopic[/URL]

which is showing a good alternative, at least if there will be a tutorial how to make it work:


 I checked the pages out and I still can't find what pkg to download to give this program a test run.

Regards..

---

### Post by zika on 2014-09-23
> **ventrical said:**
> I checked the pages out and I still can't find what pkg to download to give this program a test run.
Regards..[https://help.ubuntu.com/community/mkusb/isotesting](https://help.ubuntu.com/community/mkusb/isotesting)
[https://help.ubuntu.com/community/mkusb/v9#Installation](https://help.ubuntu.com/community/mkusb/v9#Installation)
[URL="http://phillw.net/isos/linux-tools/mkusb/"]http://phillw.net/isos/linux-tools/mkusb/'
[/URL]Nice reading and cool project. What's more important: **works**. Thank You @sudodus.
As always, I **do** prefer **CLI** version ;).

---

### Post by ventrical on 2014-09-23
Ahhh.. I didn't see that...

While 

```

sudo add-apt-repository ppa:mkusb/ppa


```
will install the stable version mkusb 8.5.4

---

### Post by sudodus on 2014-09-23
> **zika said:**
> [https://help.ubuntu.com/community/mkusb/isotesting](https://help.ubuntu.com/community/mkusb/isotesting)
[https://help.ubuntu.com/community/mkusb/v9#Installation](https://help.ubuntu.com/community/mkusb/v9#Installation)
[URL="http://phillw.net/isos/linux-tools/mkusb/"]http://phillw.net/isos/linux-tools/mkusb/'
[/URL]Nice reading and cool project. What's more important: **works**. Thank You @sudodus.
As always, I **do** prefer **CLI** version ;).

I'm glad you like it :-) and that there are other people who prefer a CLI version ;-)

---

### Post by sudodus on 2014-09-23
> **ventrical said:**
> Ahhh.. I didn't see that...

While 

```

sudo add-apt-repository ppa:mkusb/ppa

```
will install the stable version mkusb 8.5.4

Yes, until ***you*** have found the last bug :-P mkusb version 9 will be at

```
sudo add-apt-repository ppa:mkusb/unstable
```

---

### Post by sudodus on 2014-10-14
Version 9 has advanced to **ppa:mkusb/ppa** now :-)

---

### Post by Elfy on 2014-10-14
I saw no obvious way to choose usb with this. Could have been lack of tea.

---

### Post by sudodus on 2014-10-14
> **Elfy said:**
> I saw no obvious way to choose usb with this. Could have been lack of tea.

Hi Elfy,

Obviously something is wrong or not intuitive. Please explain what you did and how mkusb failed, and I'll try to improve it. (Reply here or via a message, whatever you think is better.)

---

### Post by sudodus on 2014-10-16
> Went through - get to the screen with drives - no apparent way to choose  where to install, proof that it is in fact going to copy to the usb?

[http://www.zimagez.com/zimage/screenshot-161014-092314.php](http://www.zimagez.com/zimage/screenshot-161014-092314.php)

hope that helps 

Yes, I think I understand now, and my guesses about the problem were so wrong :razz:

I'd like to continue the dialogue with corresponding screen-shots from the bleeding edge version 9.1

-o-

Is the following a correct interpretation of your message?

When you reach the window of the first screenshot - Warning and overview, you think that something will be selected automatically, so you dare not continue with the OK button. Or you dare, but ***you are playing the role of a newbie***, who would not dare to continue.

***So I must make it clear, that it is only a warning and overview, you should select drive at the next window.***

I could write it on the button: "Select drive in the next window" (instead of "OK")

***Edit***: Done, compare attachment #1 with attachment #5

Available now from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/) 
Will soon be available (and tested) via ***ppa:mkusb/unstable***

---

### Post by Elfy on 2014-10-16
yep - you got it - that makes sense now

---

### Post by zika on 2014-10-17
Since I can not boot from 14.10 made with UNetBootIn for some time (some COM32 error that I did nothave any spare time to investigate) I'll test Your app as soon as newest .iso finish downloading. Grabbing opportunity to thank you for effort before I do the actual test.
As soon as I got myself some thumb twirling time waiting for DL I kind of found plausible solution:  Boot - TAB - &#8222;unetbootindefault&#8220; - Enter. Will see... Well, that worked. Now to try mkusb... **MKUSB work(ed) great**. Cool! 
As anegote, making a mistake in choosing which .iso to download (U+1 habbit of choosing anything that have as much &#8222;next&#8220; in its name as it is humanly possible) I ended up in UbuntuNextDesktop. No comment. :) Luckily I've read about password-bug but... I'm obviously [too old]("http://cdn.acidcow.com/pics/20141016/dose_truth_18.jpg") for new way of using computer(s).
Back to DL to prepare proper 14.10 I need today for my new workplace machine, which I even did not see yet... Fingers crossed.

---

### Post by sudodus on 2014-10-18
I'm glad mkusb works well for you, *zika* :-)

I'm using it too when isotesting Utopic. An issue appeared after an update of Trusty a couple of weeks ago (I suspect a but with Zenity or bash or the cooperation of them). I was able to change mkusb, so that it is no longer affected by it. Otherwise most of the work lately is polishing, to make the text more informative as less ambiguous.

---

### Post by zika on 2014-10-18
> **sudodus said:**
> I'm glad mkusb works well for you, *zika* :-)
I'm using it too when isotesting Utopic. An issue appeared after an update of Trusty a couple of weeks ago (I suspect a but with Zenity or bash or the cooperation of them). I was able to change mkusb, so that it is no longer affected by it. Otherwise most of the work lately is polishing, to make the text more informative as less ambiguous.I'm and old geezer and everything was really clear and straightforward even to this old/weary head of mine, at first try. Cool.

---

### Post by Hazzabin on 2014-10-18
I would like to add a BIG thank you for this app.

Ran it twice yesterday 2 diff iso's worked beautifully 

And yup I'm a very old fella too, so should be ever so simple for the younger people to follow :lolflag:

---

### Post by sudodus on 2014-11-10
There are mkusb PPAs ('ppa' and 'unstable') for ***Vivid*** now. I tested it in a Lubuntu Vivid i386 live session, and it works as it should.

---

### Post by zika on 2014-11-10
Thank You for both the head(s)up and all the work in maintaining this app.

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> There are mkusb PPAs ('ppa' and 'unstable') for ***Vivid*** now. I tested it in a Lubuntu Vivid i386 live session, and it works as it should.
@sudodus
I installed the ppa . amd64bit fully updated/upgraded ubuntu-desktop vivid. Shutdown . Startup . Nothing. Do I have to yet install more programs ?

---

### Post by ventrical on 2014-11-17
Followed script, get redundant .1, .2 ...

```

ventrical@ventrical-MS-7798:~$ 
ventrical@ventrical-MS-7798:~$ wget http://phillw.net/isos/linux-tools/mkusb/mkusb-installer
--2014-11-17 14:11:59--  http://phillw.net/isos/linux-tools/mkusb/mkusb-installer
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4528 (4.4K) [text/plain]
Saving to: ‘mkusb-installer.1’

mkusb-installer.1   100%[=====================>]   4.42K  --.-KB/s   in 0.009s 

2014-11-17 14:11:59 (473 KB/s) - ‘mkusb-installer.1’ saved [4528/4528]

ventrical@ventrical-MS-7798:~$ 
ventrical@ventrical-MS-7798:~$ wget http://phillw.net/isos/linux-tools/mkusb/mkusb-installer
--2014-11-17 14:12:48--  http://phillw.net/isos/linux-tools/mkusb/mkusb-installer
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4528 (4.4K) [text/plain]
Saving to: ‘mkusb-installer.2’

mkusb-installer.2   100%[=====================>]   4.42K  --.-KB/s   in 0.009s 

2014-11-17 14:12:49 (466 KB/s) - ‘mkusb-installer.2’ saved [4528/4528]

ventrical@ventrical-MS-7798:~$ 
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2014-11-17
Ok...

```


bash mkusb-installer

```

but it is hard to follow the instructions at the links...

```

ventrical@ventrical-MS-7798:~$ bash mkusb-installer
Current directory:  /home/ventrical
HOME directory:     /home/ventrical
Desktop directory:  /home/ventrical/Desktop
pv needs the 'universe' repository
/usr/bin/wget
file=mk_install-and-test-mkusb.bash
--2014-11-17 14:17:38--  http://phillw.net/isos/linux-tools/mkusb/mk_install-and-test-mkusb.bash
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9828 (9.6K) [text/plain]
Saving to: &#8216;mk_install-and-test-mkusb.bash&#8217;

mk_install-and-test 100%[=====================>]   9.60K  --.-KB/s   in 0.03s  

2014-11-17 14:17:38 (350 KB/s) - &#8216;mk_install-and-test-mkusb.bash&#8217; saved [9828/9828]

/usr/bin/sudo
/usr/bin/gksudo
[sudo] password for ventrical: 
/dev/sda6       54737928 12425696  39508596  24% /
Running with elevated (root alias superuser) permissions
Current directory:  /home/ventrical
User: root
+--------------------------------------------------------------------+
|  Testing only, 'unstable': Install and Test MKUSB in this computer |
+--------------------------------------------------------------------+
You may need to add the repo manually to

/etc/apt/sources.list

Add the line(s), for example if you run trusty,
mkusb is the same for all versions,
but not universe, where you find pv

deb http://ppa.launchpad.net/mkusb/unstable/ubuntu trusty main
deb http://archive.ubuntu.com/ubuntu trusty universe
----------------------------------------------------------------------
Current directory:  /home/ventrical
ubuntu
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w
--2014-11-17 14:17:54--  http://phillw.net/isos/linux-tools/mkusb/md5sum.txt.asc
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2156 (2.1K) [text/plain]
Saving to: &#8216;md5sum.txt.asc&#8217;

md5sum.txt.asc      100%[=====================>]   2.11K  --.-KB/s   in 0.002s 

2014-11-17 14:17:54 (1.25 MB/s) - &#8216;md5sum.txt.asc&#8217; saved [2156/2156]

md5sum.txt.asc does not check its own md5sum. But you can
check that it is has a good signature.
-------------------------------------------------------------------------------
gpg: directory `/home/ventrical/.gnupg' created
gpg: new configuration file `/home/ventrical/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/ventrical/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/ventrical/.gnupg/secring.gpg' created
gpg: keyring `/home/ventrical/.gnupg/pubring.gpg' created
gpg: /home/ventrical/.gnupg/trustdb.gpg: trustdb created
gpg: error reading key: public key not found
gpg: requesting key EB0FC2C8 from hkp server pgp.mit.edu
gpg: key EB0FC2C8: public key "Nio Sudden Wiklund (sudodus) <nio.wiklund@gmail.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
-------------------------------------------------------------------------------
gpg: Signature made Wed 22 Oct 2014 10:30:07 AM EDT using RSA key ID EB0FC2C8
gpg: Good signature from "Nio Sudden Wiklund (sudodus) <nio.wiklund@gmail.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 0303 EA77 E34C 52F2 2958  47C6 BD43 C742 EB0F C2C8
-------------------------------------------------------------------------------
mkusb-installer: md5sum OK
mk_install-and-test-mkusb.bash: md5sum OK
--2014-11-17 14:17:59--  http://phillw.net/isos/linux-tools/mkusb/test-images/mini.iso
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32505856 (31M) [application/octet-stream]
Saving to: &#8216;mini.iso&#8217;

mini.iso            100%[=====================>]  31.00M   296KB/s   in 1m 45s 

2014-11-17 14:19:45 (301 KB/s) - &#8216;mini.iso&#8217; saved [32505856/32505856]

mini.iso: md5sum OK
--2014-11-17 14:19:45--  http://phillw.net/isos/linux-tools/mkusb/test-images/TinyCore-5.4.iso
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14680064 (14M) [application/octet-stream]
Saving to: &#8216;TinyCore-5.4.iso&#8217;

TinyCore-5.4.iso    100%[=====================>]  14.00M   312KB/s   in 48s    

2014-11-17 14:20:33 (299 KB/s) - &#8216;TinyCore-5.4.iso&#8217; saved [14680064/14680064]

TinyCore-5.4.iso: md5sum OK
--2014-11-17 14:20:33--  http://phillw.net/isos/linux-tools/mkusb/mkusb
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 68514 (67K) [text/plain]
Saving to: &#8216;mkusb&#8217;

mkusb               100%[=====================>]  66.91K   206KB/s   in 0.3s   

2014-11-17 14:20:34 (206 KB/s) - &#8216;mkusb&#8217; saved [68514/68514]

mkusb: md5sum OK
--2014-11-17 14:20:34--  http://phillw.net/isos/linux-tools/mkusb/mkusb-nox
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22869 (22K) [text/plain]
Saving to: &#8216;mkusb-nox&#8217;

mkusb-nox           100%[=====================>]  22.33K  --.-KB/s   in 0.1s   

2014-11-17 14:20:35 (152 KB/s) - &#8216;mkusb-nox&#8217; saved [22869/22869]

mkusb-nox: md5sum OK
Install if necessary the help packages 'pv' 'xterm' 'zenity'
pv needs the 'universe' repository
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xterm is already the newest version.
zenity is already the newest version.
The following packages were automatically installed and are no longer required:
  g++-4.8 gsettings-ubuntu-touch-schemas libass4 libatk-bridge2.0-dev
  libatk1.0-dev libatspi2.0-dev libaudclient2 libaudcore1 libavcodec54
  libavcodec55 libavformat54 libavformat55 libavutil52 libavutil53
  libcairo-script-interpreter2 libcairo2-dev libconnectivity-cpp0 libcurl3-nss
  libdbus-1-dev libdbus-cpp3 libdbus-glib-1-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgdk-pixbuf2.0-dev libglib2.0-dev
  libgnome-media-profiles-3.0-0 libgtk-3-dev libharfbuzz-dev
  libharfbuzz-gobject0 libhud-client2 libice-dev libinput0 liblightdm-qt5-3-0
  libmagickcore5 libmagickcore5-extra libmagickwand5 libmediascanner-2.0-0
  libmediascanner-2.0-1 libmediascanner-2.0-2 libmirclient-dev
  libmirclientplatform-mesa libmircommon-dev libmircommon1 libmirplatform
  libmirplatform1 libmirplatform2 libmirplatformgraphics-mesa libmirprotobuf0
  libmirserver25 libmowgli-2-0 libmowgli2 liboil0.3 libpango1.0-dev libpay1
  libpcre3-dev libpcrecpp0 libpixman-1-dev libpng12-dev libpoppler46
  libprocess-cpp1 libprotobuf-dev libprotobuf-lite8 libpthread-stubs0-dev
  libsm-dev libstdc++-4.8-dev libswscale2 libts-0.0-0 libu1db1
  libubuntu-application-api-test1 libubuntu-application-api1
  libubuntu-location-service0 libubuntu-location-service1
  libubuntu-platform-hardware-api1 libupstart-app-launch2 liburcu1
  libwayland-dev libx11-dev libx11-doc libxau-dev libxcb-render0-dev
  libxcb-shm0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxkbcommon-dev libxrandr-dev libxrender-dev libxtst-dev
  linux-headers-3.15.0-1 linux-headers-3.15.0-1-generic linux-headers-3.15.0-2
  linux-headers-3.15.0-2-generic linux-headers-3.15.0-3
  linux-headers-3.15.0-3-generic linux-headers-3.15.0-4
  linux-headers-3.15.0-4-generic linux-headers-3.15.0-5
  linux-headers-3.15.0-5-generic linux-headers-3.15.0-6
  linux-headers-3.15.0-6-generic linux-headers-3.16.0-10
  linux-headers-3.16.0-10-generic linux-headers-3.16.0-11
  linux-headers-3.16.0-11-generic linux-headers-3.16.0-16
  linux-headers-3.16.0-16-generic linux-headers-3.16.0-17
  linux-headers-3.16.0-17-generic linux-headers-3.16.0-18
  linux-headers-3.16.0-18-generic linux-headers-3.16.0-21
  linux-headers-3.16.0-21-generic linux-headers-3.16.0-22
  linux-headers-3.16.0-22-generic linux-headers-3.16.0-3
  linux-headers-3.16.0-3-generic linux-headers-3.16.0-9
  linux-headers-3.16.0-9-generic linux-image-3.15.0-1-generic
  linux-image-3.15.0-2-generic linux-image-3.15.0-3-generic
  linux-image-3.15.0-4-generic linux-image-3.15.0-5-generic
  linux-image-3.15.0-6-generic linux-image-3.16.0-10-generic
  linux-image-3.16.0-11-generic linux-image-3.16.0-16-generic
  linux-image-3.16.0-17-generic linux-image-3.16.0-18-generic
  linux-image-3.16.0-21-generic linux-image-3.16.0-22-generic
  linux-image-3.16.0-3-generic linux-image-3.16.0-9-generic
  linux-image-extra-3.15.0-1-generic linux-image-extra-3.15.0-2-generic
  linux-image-extra-3.15.0-3-generic linux-image-extra-3.15.0-4-generic
  linux-image-extra-3.15.0-5-generic linux-image-extra-3.15.0-6-generic
  linux-image-extra-3.16.0-10-generic linux-image-extra-3.16.0-11-generic
  linux-image-extra-3.16.0-16-generic linux-image-extra-3.16.0-17-generic
  linux-image-extra-3.16.0-18-generic linux-image-extra-3.16.0-21-generic
  linux-image-extra-3.16.0-22-generic linux-image-extra-3.16.0-3-generic
  linux-image-extra-3.16.0-9-generic tsconf ubuntu-purchase-service
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev zlib1g-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  pv
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 44.9 kB of archives.
After this operation, 166 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ vivid/universe pv amd64 1.5.7-2 [44.9 kB]
Fetched 44.9 kB in 0s (109 kB/s)
Selecting previously unselected package pv.
(Reading database ... 714746 files and directories currently installed.)
Preparing to unpack .../archives/pv_1.5.7-2_amd64.deb ...
Unpacking pv (1.5.7-2) ...
Processing triggers for man-db (2.7.0.2-3) ...
--2014-11-17 14:20:57--  http://phillw.net/isos/linux-tools/mkusb/mkusb.desktop
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 499 [text/plain]
Saving to: &#8216;mkusb.desktop&#8217;

mkusb.desktop       100%[=====================>]     499  --.-KB/s   in 0s     

2014-11-17 14:20:58 (68.9 MB/s) - &#8216;mkusb.desktop&#8217; saved [499/499]

mkusb.desktop: md5sum OK
--2014-11-17 14:20:58--  http://phillw.net/isos/linux-tools/mkusb/mkusb.svg
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7841 (7.7K) [image/svg+xml]
Saving to: &#8216;mkusb.svg&#8217;

mkusb.svg           100%[=====================>]   7.66K  --.-KB/s   in 0.02s  

2014-11-17 14:20:58 (368 KB/s) - &#8216;mkusb.svg&#8217; saved [7841/7841]

mkusb.svg: md5sum OK
--2014-11-17 14:20:58--  http://phillw.net/isos/linux-tools/mkusb/mkusb.png
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10792 (11K) [image/png]
Saving to: &#8216;mkusb.png&#8217;

mkusb.png           100%[=====================>]  10.54K  --.-KB/s   in 0.03s  

2014-11-17 14:20:58 (362 KB/s) - &#8216;mkusb.png&#8217; saved [10792/10792]

mkusb.png: md5sum OK
--2014-11-17 14:20:58--  http://phillw.net/isos/linux-tools/mkusb/mkusb.8.gz
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2002 (2.0K) [application/x-gzip]
Saving to: &#8216;mkusb.8.gz&#8217;

mkusb.8.gz          100%[=====================>]   1.96K  --.-KB/s   in 0.002s 

2014-11-17 14:20:59 (1.26 MB/s) - &#8216;mkusb.8.gz&#8217; saved [2002/2002]

mkusb.8.gz: md5sum OK

Done, test with the following small ISO files in
the directory /home/ventrical
'mini.iso' and 'TinyCore-5.4.iso'

ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2014-11-17
and then... but it failed to overwrite. I rebooted and got the the "cow" error.  Do I have to erase the USB first?

---

### Post by sudodus on 2014-11-17
This 'green screen' indicates a successful installation. There is no need to erase anything, because, it will be overwritten anyway.

In my experience, if you reach this far with mkusb, there is a bootable USB (if the iso file is OK). For example, it worked Nov 9 with the following file (a Lubuntu desktop daily iso file)

```

-rw------- 1 olle olle 750780416 nov  9 16:36 vivid-desktop-i386.iso
```

---

### Post by sudodus on 2014-11-17
I'm rather sure it has written (but probably 'saw' it write via the pv output to the mkusb console).

If I remember correctly, the Verbatim pendrive is good. Could it be that the daily built iso file is bad?

***Tell me which flavour, version etc that you are testing right now, and I'll zsync the iso file and try it on this side of the Atlantic*** :-)

---

### Post by sudodus on 2014-11-17
> **ventrical said:**
> Ok...

```


bash mkusb-installer

```

but it is hard to follow the instructions at the links...


Please point to what is hard to follow, and I'll try to improve the instructions :-)

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> I'm rather sure it has written (but probably 'saw' it write via the pv output to the mkusb console).

If I remember correctly, the Verbatim pendrive is good. Could it be that the daily built iso file is bad?

***Tell me which flavour, version etc that you are testing right now, and I'll zsync the iso file and try it on this side of the Atlantic*** :-)

 No .. it did not overwrite the Verbatim. Yes .. Verbatim is good.. so is Kingston. SDC is just flawed when it come to creating persistive 'live' USB drives.

  It all happened so fast - so I think there was an error. It says it wrote  to Verbatim but did not unless it can transfer 1.1 GBs in 1/2 a second.

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> I'm rather sure it has written (but probably 'saw' it write via the pv output to the mkusb console).

If I remember correctly, the Verbatim pendrive is good. Could it be that the daily built iso file is bad?

***Tell me which flavour, version etc that you are testing right now, and I'll zsync the iso file and try it on this side of the Atlantic*** :-)

> 
Could it be that the daily built iso file is bad?


absolutely not .. because it worked just fine (even with Kingston) using the 'restore image' method I have referenced to in the other thread.

ubuntu-gnome-desktop-amd64.iso Nov. 10 or 
[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

---

### Post by sudodus on 2014-11-17
> **ventrical said:**
> No .. it did not overwrite the Verbatim. Yes .. Verbatim is good.. so is Kingston. SDC is just flawed when it come to creating persistive 'live' USB drives.

  It all happened so fast - so I think there was an error. It says it wrote  to Verbatim but did not unless it can transfer 1.1 GBs in 1/2 a second.

Yes, that is definitely too fast. Maybe you are missing some crucial program, that is supposed to be available for the mkusb bash script, so that it is simply skipped.

Please try to repeat it, and post the text in the mkusb console! I think I can use that text to debug the problem.

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> Please point to what is hard to follow, and I'll try to improve the instructions :-)

> 
but is also available


assumption propounds the idea that there is only one step involved for persons who are running ubuntu and that just installing the ppa will also install the 'mkusb' program but then there is another argument which supersedes the original argument and so when the first direction is followed it is assumed the program will be installed and that the second argument will not be needed.. but .. as in my test case I needed to run the second part of the argument which is not made immediately clear because the first argument claims the end result of the both, which , in fact , it does not.  Others may find it clear , but I did not.

Thanks .

Hope it is of some help.

> 
**from the unstable PPA**

 This version is still developed and debugged. It can be downloaded from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/) but is also available from our unstable PPA. 
While 
sudo add-apt-repository ppa:mkusb/ppawill install the stable version mkusb 9.0.6 
the unstable PPA 
sudo add-apt-repository ppa:mkusb/unstablewill install mkusb 9.x.x (testing new features and bug-fixes) 


---

### Post by sudodus on 2014-11-17
I'll try to improve that description/instruction :-)

Thank you for making me aware of it :-)

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> Yes, that is definitely too fast. Maybe you are missing some crucial program, that is supposed to be available for the mkusb bash script, so that it is simply skipped.

Please try to repeat it, and post the text in the mkusb console! I think I can use that text to debug the problem.


  I did , I did , I did !! :) lol .. but here goes again..

```


ventrical@ventrical-MS-7798:~$ bash makeusb-installer
bash: makeusb-installer: No such file or directory
ventrical@ventrical-MS-7798:~$ bash mkusb-installer
Current directory:  /home/ventrical
HOME directory:     /home/ventrical
Desktop directory:  /home/ventrical/Desktop
pv needs the 'universe' repository
/usr/bin/wget
file=mk_install-and-test-mkusb.bash

Do you want to download an updated version of the second script?
mk_install-and-test-mkusb.bash? (y/N) y
--2014-11-17 15:45:02--  http://phillw.net/isos/linux-tools/mkusb/mk_install-and-test-mkusb.bash
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9828 (9.6K) [text/plain]
Server file no newer than local file ‘mk_install-and-test-mkusb.bash’ -- not retrieving.

/usr/bin/sudo
/usr/bin/gksudo
[sudo] password for ventrical: 
/dev/sda6       54737928 12472680  39461612  25% /
Running with elevated (root alias superuser) permissions
Current directory:  /home/ventrical
User: root
+--------------------------------------------------------------------+
|  Testing only, 'unstable': Install and Test MKUSB in this computer |
+--------------------------------------------------------------------+
You may need to add the repo manually to

/etc/apt/sources.list

Add the line(s), for example if you run trusty,
mkusb is the same for all versions,
but not universe, where you find pv

deb http://ppa.launchpad.net/mkusb/unstable/ubuntu trusty main
deb http://archive.ubuntu.com/ubuntu trusty universe
----------------------------------------------------------------------
Current directory:  /home/ventrical
ubuntu
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w
--2014-11-17 15:45:50--  http://phillw.net/isos/linux-tools/mkusb/md5sum.txt.asc
Resolving phillw.net (phillw.net)... 176.31.100.215
Connecting to phillw.net (phillw.net)|176.31.100.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2156 (2.1K) [text/plain]
Server file no newer than local file ‘md5sum.txt.asc’ -- not retrieving.

md5sum.txt.asc does not check its own md5sum. But you can
check that it is has a good signature.
-------------------------------------------------------------------------------
uid                  Nio Sudden Wiklund (sudodus) <nio.wiklund@gmail.com>
-------------------------------------------------------------------------------
gpg: Signature made Wed 22 Oct 2014 10:30:07 AM EDT using RSA key ID EB0FC2C8
gpg: Good signature from "Nio Sudden Wiklund (sudodus) <nio.wiklund@gmail.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 0303 EA77 E34C 52F2 2958  47C6 BD43 C742 EB0F C2C8
-------------------------------------------------------------------------------
mkusb-installer: md5sum OK
mk_install-and-test-mkusb.bash: md5sum OK
mini.iso: md5sum OK
TinyCore-5.4.iso: md5sum OK
mkusb: md5sum OK
mkusb-nox: md5sum OK
Install if necessary the help packages 'pv' 'xterm' 'zenity'
pv needs the 'universe' repository
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xterm is already the newest version.
zenity is already the newest version.
pv is already the newest version.

0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mkusb.desktop: md5sum OK
mkusb.svg: md5sum OK
mkusb.png: md5sum OK
mkusb.8.gz: md5sum OK

Done, test with the following small ISO files in
the directory /home/ventrical
'mini.iso' and 'TinyCore-5.4.iso'

ventrical@ventrical-MS-7798:~$ 


```

---

### Post by sudodus on 2014-11-17
It ***seems*** that the installation is OK. Thank you :-)

But I was thinking of the 'mkusb console' window while mkusb is running and creating (or trying to create) the USB boot drive. Something like the following text

```
ubuntu
select_source: imagefile=/media/multimed-2/test/lubuntu/vivid-desktop-i386.iso
imagefile=/media/multimed-2/test/lubuntu/vivid-desktop-i386.iso
The iso file SHOULD BE loop mounted on a temporary file READ-ONLY:
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
mount: blockenhet /media/multimed-2/test/lubuntu/vivid-desktop-i386.iso är skrivskyddad, monterar som endast läsbar
disk_name_type=desktop
Lubuntu 15.04 "Vivid Vervet" - Alpha i386 _found_ in iso-file
Lubuntu 15.04 "Vivid Vervet" - Alpha i386 _not_ in any possible target drive
livedrive=/sdb
ans=1
 
Installing /media/multimed-2/test/lubuntu/vivid-desktop-i386.iso to /dev/sdd ...
 
< "/media/multimed-2/test/lubuntu/vivid-desktop-i386.iso" pv -s 750780416 | dd bs=4096  of=/dev/sdd
 716MB 0:02:15 [5.29MB/s] [===========================================================>] 100%            
183296+0 records in
183296+0 records out
750780416 bytes (751 MB) copied, 147.083 s, 5.1 MB/s
Syncing the device ...
Done :-)
```

---

### Post by sudodus on 2014-11-17
Should I try the Ubuntu-Gnome amd64 daily iso file?

...

*Edit*: It works for me to create Ubuntu-Gnome amd64 daily iso file with mkusb, and to install mkusb into it and to create another working pendrive from it.

```
$ ls -l vivid-desktop-amd64.iso
totalt 1049604
-rw------- 1 olle olle 1073741824 nov 17 15:46 vivid-desktop-amd64.iso
$ md5sum vivid-desktop-amd64.iso 
55f9ea90ed957ec41876d8a1e081bab5  vivid-desktop-amd64.iso
```

I don't know how you managed to fail using mkusb and can only guess rather far-fetched scenarios like 'Did you overwrite the drive where you were storing the iso file?', 'Did you clone a symbolic link or a truncated file instead of the whole iso file?'

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> Should I try the Ubuntu-Gnome amd64 daily iso file?

...

*Edit*: It works for me to create Ubuntu-Gnome amd64 daily iso file with mkusb, and to install mkusb into it and to create another working pendrive from it.

```
$ ls -l vivid-desktop-amd64.iso
totalt 1049604
-rw------- 1 olle olle 1073741824 nov 17 15:46 vivid-desktop-amd64.iso
$ md5sum vivid-desktop-amd64.iso 
55f9ea90ed957ec41876d8a1e081bab5  vivid-desktop-amd64.iso
```

I don't know how you managed to fail using mkusb and can only guess rather far-fetched scenarios like 'Did you overwrite the drive where you were storing the iso file?', 'Did you clone a symbolic link or a truncated file instead of the whole iso file?'



  I removed the old persistent partition and created new ext4 .. then:

got this  (I think this one worked).

---

### Post by sudodus on 2014-11-17
> **ventrical said:**
> I removed the old persistent partition and created new ext4 .. then:

got this  (I think this one worked).

So the problem was this updated/upgraded persistent live drive?

It is easy to test, so soon you know if mkusb made a good booting USB pendrive :-P

---

### Post by ventrical on 2014-11-17
Success! I have basically the same thing as this:  [http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

produces.

Nice work :)

---

### Post by ventrical on 2014-11-17
I  am wondering where the EFI partiton came from . :)  Gee .. hope I haven't had this machine in UEFI mode all this time :)

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> So the problem was this updated/upgraded persistent live drive?

It is easy to test, so soon you know if mkusb made a good booting USB pendrive :-P

Yep .. mkusb .. boss program :)

Regards..

---

### Post by sudodus on 2014-11-17
Basically the same as 'Disks', yes.

But safer, because mkusb does not offer installation to non-USB devices (SATA, IDE ...) unless you 'toggle USB', and the final warning has a red background.

There is also a wiping option 'wipe the first megabyte', and the quick option for iso-testing, which can match the iso file and pendrive and see that it is recloning with a new daily built version. And there is an option to install from compressed image files, file.img.gz and file.img.xz.

-o-

Try the quick option for iso-testing - very few steps - I think you will like it :-)

[Installing again alias iso testing]("https://help.ubuntu.com/community/mkusb/pictures#Installing_again_alias_iso_testing")

---

### Post by sudodus on 2014-11-17
> **ventrical said:**
> I  am wondering where the EFI partiton came from . :)  Gee .. hope I haven't had this machine in UEFI mode all this time :)

No the amd64 iso file comes like this, so that it can be used also in UEFI mode, when it boots from grub in that FAT32 partition.

---

### Post by ventrical on 2014-11-18
> **sudodus said:**
> No the amd64 iso file comes like this, so that it can be used also in UEFI mode, when it boots from grub in that FAT32 partition.

Yes .. I remember now.

Thanks again.

---

### Post by sudodus on 2014-11-18
> **ventrical said:**
> [QUOTE=sudodus;13169109]Please point to what is hard to follow, and I'll try to improve the instructions :smile:

> 
but is also available


assumption propounds the idea that there is only one step involved for  persons who are running ubuntu and that just installing the ppa will  also install the 'mkusb' program but then there is another argument  which supersedes the original argument and so when the first direction  is followed it is assumed the program will be installed and that the  second argument will not be needed.. but .. as in my test case I needed  to run the second part of the argument which is not made immediately  clear because the first argument claims the end result of the both,  which , in fact , it does not.  Others may find it clear , but I did  not.

Thanks .

Hope it is of some help.

> 
**from the unstable PPA**

 This version is still developed and debugged. It can be downloaded from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/) but is also available from our unstable PPA. 
While 
sudo add-apt-repository ppa:mkusb/ppawill install the stable version mkusb 9.0.6 
the unstable PPA 
sudo add-apt-repository ppa:mkusb/unstablewill install mkusb 9.x.x (testing new features and bug-fixes) 

[/QUOTE]

I edited the [mkusb/v9 wiki page]("https://help.ubuntu.com/community/mkusb/v9"). Check if I fixed the issue, or if I should change something else. See the attached screenshot.

---

### Post by ventrical on 2014-11-18
> **sudodus said:**
> I edited the [mkusb/v9 wiki page]("https://help.ubuntu.com/community/mkusb/v9"). Check if I fixed the issue, or if I should change something else. See the attached screenshot.

```


sudo apt-get install mkusb

```

 That's what was missing but  then there is:

> 
**from phillw.net**

 The unstable version is also available from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/) 
Download the shell-script file **mkusb-installer** with the browser or do it directly from a terminal window with 
wget [http://phillw.net/isos/linux-tools/mkusb/mkusb-installerand](http://phillw.net/isos/linux-tools/mkusb/mkusb-installerand) run it from a terminal window with 
bash mkusb-installer
...
[sudo] password:
...
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w
...


 but this appears like it is a second  proceedure that needs to be done... so you could try this:

> 

**Installation**

  
**from the unstable PPA**

 This version is still developed and debugged. It is available from our unstable PPA. 
While 
sudo add-apt-repository ppa:mkusb/ppa sudo apt-get update sudo apt-get install mkusbwill install the stable version mkusb 9.1 
the unstable PPA 
sudo add-apt-repository ppa:mkusb/unstable sudo apt-get update sudo apt-get install mkusbwill install mkusb 9.x.x (testing new features and bug-fixes) 
 
and run it from a terminal window with 
bash mkusb-installer
...
[sudo] password:
...
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w
...
[LIST]
[*]Enter your password (installed systems typically require password, but not live systems) 
[*]Enter **w** (for wget) and the shell-script will download, check and install mkusb plus some small iso files for testing. 
[*]Repeat the command **bash mkusb-installer** if some file was not downloaded correctly. 
[/LIST]


---

### Post by ventrical on 2014-11-18
Or, what I am trying to say is to change:

> 
The unstable version is also available from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/)



to

> 

Another method is  to download from [http://phillw.net/isod/linux-tools/mkusb/](http://phillw.net/isod/linux-tools/mkusb/)



Does this make sense in how you designed the flowchart ?

Regards..

---

### Post by sudodus on 2014-11-18
What about writing like this?

[SIZE=4]from phillw.net[/SIZE]

 Another method is to download **mkusb** from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/) It will bring the same bleeding edge version as you get via the unstable PPA.

---

### Post by ventrical on 2014-11-18
> **sudodus said:**
> What about writing like this?

[SIZE=4]from phillw.net[/SIZE]

 Another method is to download **mkusb** from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/) It will bring the same bleeding edge version as you get via the unstable PPA.

Yes . Exactly... but one more thing , if I may .... the code/set of instructions could (should) also be ammended to the first block-set of instructions because it appears that we are only to execute these instructions only after we do the alternate method of downloading from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/)

```

bash mkusb-installer

```

I used to work for a security company from Austria and they had some difficulties with the english language and North American mild slang venaculars. I helped edit their help files.  Some persons  from Ukraine would use Rosetta translators and it became a disaster.  If you would compliment a person the Rosetta would interperet it as an insult.. so it was very difficult.

  Your english is excellent ... but it  just looked like  *to me* that there was a missing step in the order of operations.

Regards..

---

### Post by sudodus on 2014-11-18
> **ventrical said:**
> Yes . Exactly... but one more thing , if I may .... the code/set of instructions could (should) also be ammended to the first block-set of instructions because it appears that we are only to execute these instructions only after we do the alternate method of downloading from [http://phillw.net/isos/linux-tools/mkusb/](http://phillw.net/isos/linux-tools/mkusb/)

```

bash mkusb-installer

```

I used to work for a security company from Austria and they had some difficulties with the english language and North American mild slang venaculars. I helped edit their help files.  Some persons  from Ukraine would use Rosetta translators and it became a disaster.  If you would compliment a person the Rosetta would interperet it as an insult.. so it was very difficult.

  Your english is excellent ... but it  just looked like  *to me* that there was a missing step in the order of operations.

Regards..

It is very important that the instructions are clear, and I appreciate your help. But I don't quite understand. Do you mean that

1. these commands should be in the same code box

```
wget http://phillw.net/isos/linux-tools/mkusb/mkusb-installer
bash mkusb-installer
...
[sudo] password:
...
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w
...
```

2. or do you mean that the wget and mkusb-installer commands should be used also when using the PPAs?

For testing it is good to use them also with the PPA, but the PPA method works without them (like using any PPA for example for Ubuntu Tweak).

default. Something else :-P

---

### Post by ventrical on 2014-11-18
> **sudodus said:**
> It is very important that the instructions are clear, and I appreciate your help. But I don't quite understand. Do you mean that

1. these commands should be in the same code box

```
wget http://phillw.net/isos/linux-tools/mkusb/mkusb-installer
bash mkusb-installer
...
[sudo] password:
...
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w
...
```

2. or do you mean that the wget and mkusb-installer commands should be used also when using the PPAs?

For testing it is good to use them also with the PPA, but the PPA method works without them (like using any PPA for example for Ubuntu Tweak).

default. Something else :-P

See the wiki. I just put in a demarcation line. Thats all that is needed. You have made it correct when you added:

```


sudo apt-get install mkusb

```

 As I did not see it there before.


> 
2. or do you mean that the wget and mkusb-installer commands should be used also when using the PPAs?


This is where I was confused .. but others did not seem to be confused. Also..

> ]
Install via ppa or wget, uninstall or quit? (p/w/u/Q) w 


This line is confusing (to me) as  it is assumed that If I have the ppa installed then why to I need to use wget. It is a redundancy but perhaps it is a good safety measure and is really harmless but a noob or other may get confused. So the alternate method suggests *two* ways to download the script _then_ if _ I am not using ubuntu or debian = wget else ppa:   I am not critisizing but if I am programmer/dev who is veiwing your app I will see this and question why the code  presents an argument against itself that is not necessary.

So  for clarity , if  I were to change I would put:

```

wget, uninstall or quit? (w/u/Q) w

```

So as I had said .. it may be  a good safety practice but logic tells me that it is redundant. I hope you do not think I ciritisize too much :) apologies if it sounds so..

edit:

Looking at wiki it is very clear to me now.

Thanks..

---

### Post by sudodus on 2014-11-18
> **ventrical said:**
> See the wiki. I just put in a demarcation line. Thats all that is needed. You have made it correct when you added:

```


sudo apt-get install mkusb

```

 As I did not see it there before.

I added 'apt-get update' and 'apt-get install mkusb' today after your heads-up comment. You made me see that it was missing.
> 

So as I had said .. it may be  a good safety practice but logic tells me that it is redundant. I hope you do not think I ciritisize too much :) apologies if it sounds so..

On the contrary, I'm glad to cooperate to make the instructions better. Thank you :-)

---

### Post by sudodus on 2014-11-18
> **ventrical said:**
>  Also..

This line is confusing (to me) as  it is assumed that If I have the ppa installed then why to I need to use wget. It is a redundancy but perhaps it is a good safety measure and is really harmless but a noob or other may get confused. So the alternate method suggests *two* ways to download the script _then_ if _ I am not using ubuntu or debian = wget else ppa:   I am not critisizing but if I am programmer/dev who is veiwing your app I will see this and question why the code  presents an argument against itself that is not necessary.

So  for clarity , if  I were to change I would put:

```

wget, uninstall or quit? (w/u/Q) w

```

So as I had said .. it may be  a good safety practice but logic tells me that it is redundant. I hope you do not think I ciritisize too much :) apologies if it sounds so..

edit:

Looking at wiki it is very clear to me now.

Thanks..

I see your point. I can explain why the ppa option is there:

- It is an advantage to install via the ppa, because then you will get updates automatically. This is good for everybody, so I want to encourage it.

- wget and bash-installer bring two small iso files, that are convenient for testing. They also copy the desktop file(s) into the desktop directory. I must confess that I made this method in order to make it convenient *for me* to test mkusb (to make it very convenient and efficient to test mkusb in different distros, versions and flavours.

(This is not a final statement - only an explanation why it is like it is - should it be written in the wiki page as a foot-note?)

---

### Post by ventrical on 2014-11-18
> **sudodus said:**
> I see your point. I can explain why the ppa option is there:

- It is an advantage to install via the ppa, because then you will get updates automatically. This is good for everybody, so I want to encourage it.

- wget and bash-installer bring two small iso files, that are convenient for testing. They also copy the desktop file(s) into the desktop directory. I must confess that I made this method in order to make it convenient *for me* to test mkusb (to make it very convenient and efficient to test mkusb in different distros, versions and flavours.

(This is not a final statement - only an explanation why it is like it is - should it be written in the wiki page as a foot-note?)


  I am just curious , first, that, does the ppa option automatically create the ppa and/or offer ppa options or, does the ppa have to be created manually first (as in the first option as presented in the wiki) ? <I have not used this option from the second method described at the wiki>

Regards..

---

### Post by sudodus on 2014-11-18
The script runs the commands to install and use the ppa. You told you are a programmer by profession, so you can see it easily by looking at the script file 

***mk_install-and-test-mkusb.bash*** (which is called by ***mkusb-installer***)

```
if [ "$ans" == "p" ]
then
 add-apt-repository ppa:mkusb/unstable
 apt-get update
 apt-get install mkusb
elif [ "$ans" == "w" ]
...
```

---

### Post by ventrical on 2014-11-18
> **sudodus said:**
> The script runs the commands to install and use the ppa. You told you are a programmer by profession, so you can see it easily by looking at the script file 

***mk_install-and-test-mkusb.bash*** (which is called by ***mkusb-installer***)

```
if [ "$ans" == "p" ]
then
 add-apt-repository ppa:mkusb/unstable
 apt-get update
 apt-get install mkusb
elif [ "$ans" == "w" ]
...
```

Ahhh.. very bright:)
I had to be shown:)

Regards..

---

### Post by ventrical on 2014-11-18
I am just bringing up this screen to mention that it takes about 30 to 45 seconds after the ==> 100% mark is reached.  I was almost tempted to close the window before it was completely installed (which it did install).

Is is possible to put a:

========================>100%
please wait.

Thanks

---

### Post by sudodus on 2014-11-19
I see what you mean. I don't think it can be put exactly where you want it, but it would be possible to put it before that.

```
Please wait for sync (flushing file system buffers to the drive) until 'Done' is written ...
=======================================>100%
```

---

### Post by ventrical on 2014-11-19
> **sudodus said:**
> I see what you mean. I don't think it can be put exactly where you want it, but it would be possible to put it before that.

```
Please wait for sync (flushing file system buffers to the drive) until 'Done' is written ...
=======================================>100%
```

That is just a well.

Thanks.:)

Regards..

---

### Post by sudodus on 2014-11-19
The 'Please wait' is there now, available from phillw.net, but Launchpad is slow, so it is not yet in the [unstable] PPA:

```
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...

```

Not that it is necessary to wait long when installing Tiny Core as in the following 'text screenshot', but  definitely *valuable when installing Ubuntu flavours into slow USB 2  pendrives*. Thanks for the tip *ventrical* :-)


```
ubuntu
The iso file SHOULD BE loop mounted on a temporary file READ-ONLY:
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
mount: blockenhet /media/multimed-2/CD/tinycore/TinyCore-5.4.iso är skrivskyddad, monterar som endast läsbar
disk_name_type=title
MENU TITLE TinyCore _found_ in iso-file
MENU TITLE TinyCore _not_ in any possible target drive
livedrive=/sdb
ans=1
 
Installing TinyCore-5.4.iso to /dev/sdd ...
 
< "TinyCore-5.4.iso" pv -s 14680064 | dd bs=4096  of=/dev/sdd
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
  14MB 0:00:00 [ 387MB/s] [==================================>] 100%            
3584+0 records in
3584+0 records out
14680064 bytes (15 MB) copied, 0.0362259 s, 405 MB/s
Syncing the device ...
Done :-)
[COLOR=#696969]Cleanup after mkusb finished :-)[/COLOR]

```

---

### Post by ventrical on 2014-11-19
> **sudodus said:**
> The 'Please wait' is there now, available from phillw.net, but Launchpad is slow, so it is not yet in the [unstable] PPA:


Oh yes it is :)

```

The following packages will be upgraded:
  gir1.2-pango-1.0 libpango-1.0-0 libpango1.0-0 libpango1.0-dev
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 mkusb
8 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 579 kB of archives.
After this operation, 0 B of additional disk space will be used.

```

whoops :) spoke to soon . That must have been a previous change to ppa :)

---

### Post by sudodus on 2014-11-19
The new version 9.1.2 has reached MKUSB unstable now :-)

(I think the updates including copies for all current versions reached the PPA less than an hour after my previous post, so fairly fast today.)

---

### Post by ventrical on 2014-11-19
> **sudodus said:**
> The 'Please wait' is there now, available from phillw.net, but Launchpad is slow, so it is not yet in the [unstable] PPA:

```
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...

```



I have the new update but the message does not show. I also rebooted.

Regards..

---

### Post by ventrical on 2014-11-19
Is this opensource app? If so I would like to see source code for mkusb. Has it already been downloaded to directory or do I have to download from net?

Thanks

---

### Post by sudodus on 2014-11-19
Of course it is open source. It is a bash shellscript (with some minor help scripts). So the program code is the source code, just read it with your favourite editor :-)

---

### Post by sudodus on 2014-11-19
> **ventrical said:**
> I have the new update but the message does not show. I also rebooted.

Regards..

The new text strings are in mkusb version 9.1.2, but are printed only when you copy/clone/flash a new system. I skip printing them during iso-testing re-cloning, because iso-testers know the program, and would only be irritated by the text (I think). If you think otherwise, it can be changed.

*Edit*: in the unstable ppa

---

### Post by ventrical on 2014-11-19
> **sudodus said:**
> The new text strings are in mkusb version 9.1.2, but are printed only when you copy/clone/flash a new system. 


Ok.. I see . Makes sense. Thanks

---

### Post by sammiev on 2014-11-23
Decided to try a few daily installs and have not tried mkusb yet, so todays the day.

No issues here and must add, it works great. Thanks!

---

### Post by sudodus on 2014-11-24
> **sammiev said:**
> Decided to try a few daily installs and have not tried mkusb yet, so todays the day.

No issues here and must add, it works great. Thanks!

I'm glad mkusb works well for you. Then it was worthwhile to make it. Please let me know if you get some problem with mkusb in the future, or if you want it changed somehow :-)

---

### Post by balloons on 2014-11-24
Cool! So this is what came out of the vUDS session for a few moons ago. Love it! Thanks for helping make it easier for folks to create and use usb keys to install ubuntu. Especially when they are using it for testing :-)

---

### Post by sudodus on 2014-11-24
Well, I think mkusb is a project alongside that vUDS session. I had some inspiration from that project though :-)

And I think the Ubuntu mainstream effort went into debugging the Startup Disk Creator alias usb-creator-gtk, which is much better now, but still suffers from some bugs.

---

