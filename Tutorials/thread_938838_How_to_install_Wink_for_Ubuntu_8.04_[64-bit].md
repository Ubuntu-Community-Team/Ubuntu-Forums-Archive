---
title: "How to install Wink for Ubuntu 8.04 [64-bit]"
date: 2008-10-05
forum: Tutorials
---

### Post by linuxed on 2008-10-05
**[color=red]Updated for Ubuntu 10.04[/color]**

Name: Wink
Version: 1.5.1060

Wink is a great program for creating video tutorials through the use of flash animation.  You can take screen captures with Wink either on-demand or on a time-delay basis and then compile those screenshots into a swf file for use in a web page.  You can also add explanation boxes, buttons and titles to your presentations.  If you're looking for an easy way to create a video tutorial on how to use certain software applications or perhaps even a website then you definitely want to check out Wink.  Unfortunately the wink package available in the Ubuntu repository is only available for the 32-bit architecture so this guide will walk you through installing it on the 64-bit version of Ubuntu.


[list=1]
[*]First off you'll need to install the following package.
```

sudo apt-get install ia32-libs

```
[*]The next step is to download the Wink package. [_Click here for a list of download locations._](http://packages.ubuntu.com/hardy-updates/i386/wink/download)  Select one of the listed mirrors and save the file to your desktop.
[*]Download the libstdc++5 package. [_Click here for a list of download locations._](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)  Select one of the listed mirrors and save the file to your desktop.
[*]Open your terminal and type the following:
```

mkdir -p /tmp/libstdc5
dpkg --extract ~/Desktop/libstdc++5*.deb /tmp/libstdc5
sudo cp /tmp/libstdc5/usr/lib/* /usr/lib32
sudo dpkg --force-architecture -i ~/Desktop/wink*.deb
sudo rm /usr/lib/wink/libexpat.so.0
sudo ln -s /lib32/libexpat.so.1 /lib32/libexpat.so.0
sudo ln -s /lib32/libexpat.so.0 /usr/lib/wink/libexpat.so.0

```
[*]Before running the program for the first time you need to make sure that all required libraries are installed.
```

ldd /usr/lib/wink/wink

```
[*]If none of the libraries say "not found" then you should now be able to open wink from the Applications > Graphics menu.
[/list]


**NOTES:**
If any libraries are listed as not found then you may need to install additional packages or as a last resort manually extract the files from a package into your /usr/lib32 directory.  You can search the Ubuntu repository for the name of the missing library.  [_Click here to use the "Package Contents" search._](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=contents&keywords=libexpat.so.1.5.2)  Enter the name of the library you are missing and search for a package that contains it.  When you've found the correct package download the i386 version and extract the missing library into your /usr/lib32 folder.


**To uninstall type the following:**
```

sudo dpkg -r wink

```

---

### Post by thierrybo on 2008-11-11
Thanks,

works on 8.10 64 bits too ! I uses the default gcc-4.2-base, not gcc-3.3-base.

---

### Post by mrbhave on 2008-11-29
Thanks for the post - I'm getting the following error message...any ideas?

$ dir /usr/lib32/libexpat*
/usr/lib32/libexpat.so.1      /usr/lib32/libexpatw.so.1
/usr/lib32/libexpat.so.1.5.2  /usr/lib32/libexpatw.so.1.5.2

$ dpkg-deb --build wink
dpkg-deb: building package `wink' in `wink.deb'.

$ sudo dpkg -i wink.deb
Selecting previously deselected package wink.
dpkg: regarding wink.deb containing wink:
 libexpat1 conflicts with wink (<= 1.5.1060-4)
  wink (version 1.5.1060-3ubuntu1.2) is to be installed.
dpkg: error processing wink.deb (--install):
 conflicting packages - not installing wink
Errors were encountered while processing:
 wink.deb

---

### Post by binbash on 2008-11-29
THanks, nice how to.

---

### Post by linuxed on 2008-11-30
> **mrbhave said:**
> Thanks for the post - I'm getting the following error message...any ideas?

$ dir /usr/lib32/libexpat*
/usr/lib32/libexpat.so.1      /usr/lib32/libexpatw.so.1
/usr/lib32/libexpat.so.1.5.2  /usr/lib32/libexpatw.so.1.5.2

$ dpkg-deb --build wink
dpkg-deb: building package `wink' in `wink.deb'.

$ sudo dpkg -i wink.deb
Selecting previously deselected package wink.
dpkg: regarding wink.deb containing wink:
 libexpat1 conflicts with wink (<= 1.5.1060-4)
  wink (version 1.5.1060-3ubuntu1.2) is to be installed.
dpkg: error processing wink.deb (--install):
 conflicting packages - not installing wink
Errors were encountered while processing:
 wink.deb
Make sure you're not installing the package over a previous installation.  Type "sudo apt-get purge wink" or if you've already removed it using apt-get then type "sudo dpkg -P wink".

I've updated the guide above for Ubuntu 8.10.  Try starting over with the new instructions above and see if it makes any difference.  Instead of installing with dpkg try double clicking on the deb package that you created and see if that helps.

---

### Post by mrbhave on 2008-12-12
The updated procedure works perfectly - many thanks!

---

### Post by bluntknife on 2009-02-06
This is an excellent guide and worked for me flawlessly.

[Unbuntu 8.10 Desktop AMD64, kernel: 2.6.27-9-generic]

Many thanks.

---

### Post by zajc on 2009-04-24
It also works on 9.04 (64-bit). The bug when capturing frames with Pause or Shift+Pause still remains. The **workaround** is to **turn off Num Lock**.

Add: I was using *wink_1.5.1060-7_i386.deb* package.

---

### Post by OmegaBLK on 2009-05-11
Thank you for this nice, short tutorial on how to get the Wink 32-bit binary to work in 64-bit Ubuntu.  I am using the 64-bit version of Jaunty (9.04).  Kudos to you my friend.

---

### Post by froller on 2009-06-24
Good howto.  Installed flawless on Jaunty 2.6.28-13-generic x86_64. ACER Aspire 7520.  Thanx.

---

### Post by klaas.holwerda on 2009-07-08
> **zajc said:**
> It also works on 9.04 (64-bit). The bug when capturing frames with Pause or Shift+Pause still remains. The **workaround** is to **turn off Num Lock**.

Add: I was using *wink_1.5.1060-7_i386.deb* package.

I got 

[http://ftp.kfki.hu/linux/debian/pool/non-free/w/wink/wink_1.5.1060-8_i386.deb](http://ftp.kfki.hu/linux/debian/pool/non-free/w/wink/wink_1.5.1060-8_i386.deb) 

That did work, after also installing:

 apt-get install libstdc++5

The ubuntu one gives the expat1 problem mentioned above:

 wink_1.5.1060-3ubuntu1.2_i386.deb

---

### Post by nadian on 2009-11-06
Has anyone got an update for these instructions that works in ubuntu 9.10, heres my issue - wink seems to install, correct icon appears in grphics menu but..when i click on it there's a brief flash and nothing happens. I ran the ldd /usr/lib/wink/wink and all seem to be there.
a couple of minutes later synaptics package manager repoted an error and removed wink and dependent libraries???
Can anyone help?
incidently I've tried WINE with windows build wink 2, it kind of works at first - although no sound - but when rendered urgh....doesn't really work, missing huge parts, text boxes and annotations disappear e.t.c

---

### Post by linuxed on 2009-11-06
**Installing on Karmic**

Download the following files to your desktop.

[wink_1.5.1060-6_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/w/wink/wink_1.5.1060-6_i386.deb)
[libstdc++5_3.3.6-17ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb)
[libstdc++5_3.3.6-17ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb)
[libexpat1_2.0.1-4ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/e/expat/libexpat1_2.0.1-4ubuntu1_i386.deb)

Click on the libstdc++5_3.3.6-17ubuntu1_amd64.deb file to install it manually using the gui.  Then type the following:
```

cd ~/Desktop

sudo apt-get install ia32-libs libatk1.0-0 libc6 libfreetype6 libgcc1 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libx11-6 libxext6 libxi6 libexpat1

dpkg-deb -x libexpat*.deb libexpat
sudo mv libexpat/lib/* /usr/lib32

dpkg-deb -x libstdc++5*i386.deb libstdc++5
sudo mv libstdc++5/usr/lib/* /usr/lib32

sudo ln -s /usr/lib32/libexpat.so.1 /usr/lib32/libexpat.so.0

sudo dpkg --force-architecture -i wink*.deb

```

---

### Post by nadian on 2009-11-06
thanks for your help, unfortunately still got problems. 
1. Although i've downloaded to desktop, when i go to desktop the files are not there?, if i click on download (in firefox download manager) and open containingg folder it opens to desktop...and files not there.(however they have downloaded and still appear in download manager...??. I did doubleclick  on [libstdc++5_3.3.6-17ubuntu1_amd64.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb") anyway and got this message
Error: Wrong architecture 'amd64 
my laptop is Intel(R) Core(TM)2 Extreme CPU X9000  @ 2.80GHz could that be one issue?

---

### Post by nadian on 2009-11-06
[FuriousX]("http://ubuntuforums.org/member.php?u=948654") - do i really want to download a jpg called 'dark evil' from an online file repository?. no.

---

### Post by linuxed on 2009-11-07
> **nadian said:**
> thanks for your help, unfortunately still got problems. 
1. Although i've downloaded to desktop, when i go to desktop the files are not there?, if i click on download (in firefox download manager) and open containingg folder it opens to desktop...and files not there.(however they have downloaded and still appear in download manager...??. I did doubleclick  on [libstdc++5_3.3.6-17ubuntu1_amd64.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb") anyway and got this message
Error: Wrong architecture 'amd64 
my laptop is Intel(R) Core(TM)2 Extreme CPU X9000  @ 2.80GHz could that be one issue?
This guide was written specifically for 64-bit Ubuntu users.  Wink is currently available only as 32-bit package so if you want to install it on a 64-bit OS it requires a few extra steps.  If you're currently running a 32-bit version of Ubuntu then you shouldn't have to do anything other than install the actual wink package.  Since you received an error stating "wrong architecture" I'm assuming you've installed the i386 version of Ubuntu and not the amd64 version.  You should be able to install wink with the following steps.
```

sudo apt-get remove wink
sudo dpkg -i libstdc++5*i386.deb
sudo dpkg -i wink*.deb

```

---

### Post by nadian on 2009-11-07
thanks linuxed, have 32bit as you said, have downloaded and sudo dkpg as instructed seemed to go ok. But I'm a newbie and don't now what to do next. I tried to run with wink and sudo wink at the terminal but i get..
/usr/lib/wink/wink: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
also there's no wink in applications after dpkg so i guess there's another step I need?

---

### Post by linuxed on 2009-11-07
```

sudo apt-get install libexpat1
sudo ln -s /usr/lib/libexpat.so.1 /usr/lib/libexpat.so.0

```
Once installed wink should be listed under Applications > Graphics.

---

### Post by nadian on 2009-11-07
Ok I got the symbolic link to work:
g@g-laptop:~$ sudo ln -s /usr/lib/libexpat.so.1 /usr/lib/libexpat.so.0
ln: creating symbolic link `/usr/lib/libexpat.so.0': File exists
 but I think wink itsels is no installing in the right place? at the moment i have 
wink deb on desktop - i cd to home/g/Desktop and run dpkg from there:

Desktop$ sudo dpkg -i wink*.deb
(Reading database ... 210797 files and directories currently installed.)
Preparing to replace wink 1.5.1060-6 (using wink_1.5.1060-6_i386.deb) ...
Unpacking replacement wink ...
Setting up wink (1.5.1060-6) ...

Processing triggers for desktop-file-utils ...
Processing triggers for man-db ..
but when i try to run wink:
/usr/lib/wink/wink: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
maybe wink is not installing where it should because i am unpacking from desktop?
sorry I'm new to all this

---

### Post by linuxed on 2009-11-07
Run the following commands and then post the output.  Select, right click and copy the output from your terminal window.  Unfortunately I can't offer any additional suggestions without this info.  I'd recommend editing out your username from all of the content before posting.  Just a minor security precaution.
```

ldd /usr/lib/wink/wink

ls -l /lib/libexpat*

file /lib/libexpat*

ls -l /usr/lib/libexpat*

file /usr/lib/libexpat*

ls -l /usr/lib/wink/libexpat*

file /usr/lib/wink/libexpat*

ls -l /usr/lib/libstdc++*

file /usr/lib/libstdc++*

ls -l /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve*

file /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve*

```

---

### Post by nadian on 2009-11-07
Linuxed thanks for persevering with me, heres the whole output from those commands:
g@g-laptop:~$ ldd /usr/lib/wink/wink
    linux-gate.so.1 =>  (0x0068a000)
    libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x001b1000)
    libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00d31000)
    libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00ebe000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x005aa000)
    libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0x0092c000)
    libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0x00110000)
    libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00b37000)
    libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00123000)
    libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00e41000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x0074c000)
    libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x005c4000)
    libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x0011d000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00a92000)
    libXi.so.6 => /usr/lib/libXi.so.6 (0x00b00000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0x00161000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0x00771000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00572000)
    libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0x00bb4000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00171000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00935000)
    libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x0068b000)
    libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x0070a000)
    libexpat.so.0 => not found
    libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00598000)
    libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x0018f000)
    libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x005a5000)
    libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x0067a000)
    libcairo.so.2 => /usr/lib/libcairo.so.2 (0x008a0000)
    libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00c6e000)
    libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00aab000)
    libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00680000)
    libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00733000)
    libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00736000)
    libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00ef9000)
    libXft.so.2 => /usr/lib/libXft.so.2 (0x00750000)
    libz.so.1 => /lib/libz.so.1 (0x00a79000)
    libpcre.so.3 => /lib/libpcre.so.3 (0x00b7f000)
    /lib/ld-linux.so.2 (0x00194000)
    librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x0073f000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0x00b19000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00ad8000)
    libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00dc6000)
    libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x00f04000)
    libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00764000)
    libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00b1d000)
    libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00d04000)
    libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00927000)
    libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00af6000)
    libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0x00e0d000)
    libselinux.so.1 => /lib/libselinux.so.1 (0x00e21000)
    libexpat.so.1 => /lib/libexpat.so.1 (0x00e46000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00b0b000)
g@g-laptop:~$ ls -l /usr/lib/libexpat*
lrwxrwxrwx 1 root root 22 2009-11-07 11:44 /usr/lib/libexpat.so.0 -> /usr/lib/libexpat.so.1
g@g-laptop:~$ file /usr/lib/libexpat*
/usr/lib/libexpat.so.0: broken symbolic link to `/usr/lib/libexpat.so.1'
g@g-laptop:~$ ls -l /usr/lib/wink/libexpat*
lrwxrwxrwx 1 root root 16 2009-11-07 11:49 /usr/lib/wink/libexpat.so.0 -> ../libexpat.so.1
g@g-laptop:~$ file /usr/lib/wink/libexpat*
/usr/lib/wink/libexpat.so.0: broken symbolic link to `../libexpat.so.1'
g@g-laptop:~$ ls -l /usr/lib/libstdc++*
lrwxrwxrwx 1 root root     18 2009-11-07 08:22 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root 737192 2008-05-10 07:18 /usr/lib/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root     19 2009-11-02 22:51 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r-- 1 root root 962800 2009-10-15 00:51 /usr/lib/libstdc++.so.6.0.13
g@g-laptop:~$ file /usr/lib/libstdc++*
/usr/lib/libstdc++.so.5:      symbolic link to `libstdc++.so.5.0.7'
/usr/lib/libstdc++.so.5.0.7:  ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
/usr/lib/libstdc++.so.6:      symbolic link to `libstdc++.so.6.0.13'
/usr/lib/libstdc++.so.6.0.13: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
g@g-laptop:~$ ls -l /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve*
ls: cannot access /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve*: No such file or directory
g@g-laptop:~$ file /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve*
/usr/lib/gtk-2.0/2.10.0/engines/libqtcurve*: ERROR: cannot open `/usr/lib/gtk-2.0/2.10.0/engines/libqtcurve*' (No such file or directory)
g@g-laptop:~$ 

it looks like the last command had an issue?
hope you can help

---

### Post by linuxed on 2009-11-07
The following commands should fix it.
```

sudo rm /usr/lib/libexpat.so.0
sudo rm /usr/lib/wink/libexpat.so.0
sudo apt-get install --reinstall libexpat1
sudo apt-get install gtk2-engines-qtcurve
sudo ln -s /lib/libexpat.so.1 /usr/lib/libexpat.so.0
sudo ln -s /lib/libexpat.so.1 /usr/lib/wink/libexpat.so.0

```
Test wink again with "ldd /usr/lib/wink/wink" and make sure the libexpat library doesn't say "not found."  For some reason the libexpat1 package in the Ubuntu repository has been changed in Karmic to install the libexpat libraries to the /lib folder.  In all previous versions of Ubuntu those libraries were installed to /usr/lib which is why the wink package includes a symlink to /usr/lib/libexpat.so.1.  Unfortunately the changes to the libexpat1 package in Karmic now breaks the wink package.  The gtk2-engines-qtcurve package is also missing from the list of dependencies in the wink package and since the libqtcurve.so is a required library of wink it causes an error to be thrown each time it's run.

---

### Post by nadian on 2009-11-07
Thank you very much linuxed it's finally up and running.What a palava!. I don't know if you still want to help,( I understand completely if you don't) but the next  issue is it records fine, i can add text boxes e.t.c but when i render the project the resulting swf runs superfast - over in a split second (although setting the frame rate to 2 helps a bit), and all annotations added text box, speech bubble help, are absent.
thanks again anyway.

---

### Post by linuxed on 2009-11-07
I've always used the default timed capture settings which seem to work fine for me.  Click on New, 4 frames a second, click OK, click minimize to tray, right click on the wink icon in your tray, click start timed capture.  When you're done right click on the wink icon and click stop timed capture.  You can then add additional time to any of the frames by entering the number of milliseconds in the text box where it says "Stay in this frame for time".  You'll notice that a 0 will appear in the textbox by default.  Ignore that setting.  The 0 is merely a representation of the default value (which is not 0 milliseconds).  Only change the 0 to a different setting if you want to pause on a certain frame for an extended period of time.  1000 milliseconds = 1 second.

I'm not sure why the callouts would be missing.  The only suggestions I can offer would be to use the default callouts included in the program and make sure to include a next button on each frame that contains a callout.

To add a callout:
[list=]
[*]Select the frame
[*]Check the box labeled textbox
[*]Click the choose callout button
[*]Select the desired callout and click ok
[*]Make sure the next button is checked and uncheck the previous button if it's not needed
[*]Move the callout and next button objects to the desired location on the screen by clicking and dragging them
[/list]

Before you render the swf file click Project > Settings.  Select a location to save the project, select Macromedia Flash as the output file type, enter a frame rate of 20 and click ok.  Click Project > Render.

---

### Post by nadian on 2009-11-09
OK I have narrowed down the issue a little more, firstly I made a stupid mistake, after rendering from wink, i clicked the resulting swf file , instead of the html attached to it, and that seems to make it run superfast in totem movie player, running from html makes it run at correct speed in firefox. Secondly adding textboxes does work so long as I run in HTML. Thanks for all your help and patience linuxed. It seems the problem with wink is now solved thanks to you.

---

### Post by nomnex on 2009-11-26
@nadian

Wink 1.5 is not in the karmic repository at my knowledge because 9.10 dropped libstdc++5.

[https://code.launchpad.net/~ubuntu-branches/ubuntu/karmic/wink/karmic]("https://code.launchpad.net/%7Eubuntu-branches/ubuntu/karmic/wink/karmic")

I have seen your post in Wink Google group. I am afraid Wink is a dead (closed) project on Linux

Version 2 is available since 2007 and has never been updated for Linux. There is a serious bug which defeat the purpose of the software (taking print-screens vs. making a full movie needing edition with a video editor) i.e. Windows manager locks the keyboard keys and prevents to take open menus in the window - you will only have the main window.

The known bugs page on debugmode.com is also dated 2007. That's a great deception. If the author would agree to make his code open, others could take the project over.

For software presentation, RMD (GUI) or ffmpeg (CLI) does not come close to Wink in my view. There is no Wink replacement for Linux open source at my knowledge.

Edit: Version 2 for windows is version 1.5 for Linux (same build)

---

### Post by dotdot on 2009-12-03
bump - anyone got a list of what needs ... and yes will be ... done to get wink working on 10.09. ?

I hear what the last guy said however that doesn't take us forward here.

We've gone from one release to another and now some software which did work in the past doesn't.

That , for me and i'm sure many others , is not exactly what could be described as a step forward.

hey , don't get me wrong, it's not like this software is like the new instant messaging package which when you realise it's poor you can just get rid off and install pidgin because it's better. Here there is no software which comes close to wink.

Trust me I've used it for years.

Years... doesn't mean I'm staying on 10.09.... 

now this has been mentioned both here and the software forum for wink.

what needs to be done.. ? we've got a developer who no longer works on his own product and an os which doesn't hold onto the objects which it did in the past... 

Can someone help here.. ?  positive's please ?

(oh and please don't suggest myremotedesktop - as a replacement-  it is the worst piece of software I have ever downloaded... EVER!).

---

### Post by nomnex on 2009-12-03
You can try this

source:
[html]http://www.******************/ubuntu-user/287053-how-install-wink-karmic-koala-32-bit-version.html[/html]> > On 11/27/2009 09:38 AM, user1 wrote:
>> My wink installs and works fine in 9.04. However I cannot get it
>> installed in 9.10, it complains of some dependency problems, it wants
>> libstdc++5 >= 1:3.3.4-1, but I cannot get this installed (it's not
>> there).

I followed the directions (which is for 64-bit) on :

[http://ubuntuforums.org/archive/index.php/t-938838.html](http://ubuntuforums.org/archive/index.php/t-938838.html)

Then I took /lib/libexpat.so.1.5.2 and renamed it to libexpat.so.0

Then I placed this libexpat.so.0 in ~/wink/usr/lib32 and /usr/lib

And now wink works just fine for me. - ThanksAdditionally file a bug on Launchpad and contact the author at [satish at debugmode dot com] and ask nicely. I will. With a bit of luck we will get back this fine freeware in our newer distributions.

---

### Post by dotdot on 2009-12-15
worked for me.

generally i don't care what is done to get this working - within the bounds of reality of course.

thanks to the person who came up with a solution m essy but hey wtf ;)

gj as those folks say in the us.

+1 + slap on the back.

can't say any fairer that that.

---

### Post by Harvard_LLC on 2010-07-31
Just an Update that this will install on Ubuntu 10.04 64 bit as well.
You need to correct the following lines from the original post.


sudo ln -s /usr/lib32/libexpat.so.1 ./wink/usr/lib32/libexpat.so.0

become

sudo ln -s /lib32/libexpat.so.1 ./wink/usr/lib32/libexpat.so.0
(remove the usr/)

the libstc++5 needs to be inastalled as well.

Download it from from 
[http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb)
wget [http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb)

dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs

sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib32/

cd /usr/lib32

sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

Hope this helps someone.

---

### Post by anantshri on 2010-09-06
download link is not working on first page

at this point the direct working download link is [http://old-releases.ubuntu.com/ubuntu/pool/multiverse/w/wink/wink_1.5.1060-6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/w/wink/wink_1.5.1060-6_i386.deb)

hope this can help someone

---

### Post by lenn-art on 2010-09-27
> **anantshri said:**
> download link is not working on first page

at this point the direct working download link is [http://old-releases.ubuntu.com/ubuntu/pool/multiverse/w/wink/wink_1.5.1060-6_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/w/wink/wink_1.5.1060-6_i386.deb)

hope this can help someone

Yes, you helped me! Thanks a lot. I needed also the libstdc++5 package, which i found here [http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

---

### Post by cadcam on 2010-09-28
so, i also can't run wink.  I took care of the c++5, but i can't find a ia32-lib for an i386 arch.  i can find amd versions......

help?


thanks,
A

---

### Post by linuxed on 2010-09-29
This guide is only meant to be used for 64-bit systems.  If you're using a 32-bit system then you can just install the wink and libstdc++5 packages without any modifications or extra steps.  The ia32-libs package contains 32-bit libraries for use on a 64-bit system so don't worry about installing that package for an i386 system.

If you are using a 64-bit system then just type:
```

sudo apt-get install ia32-libs

```

---

### Post by cadcam on 2010-09-29
right, i'm running lucid 64 (intel, not amd).  i can't get the 32 libraries.  

mantra@mantra:~$ sudo apt-get install ia32-libs
[sudo] password for mantra: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
mantra@mantra:~$ 

all repositories are activated.  

thanks,
A

---

### Post by linuxed on 2010-09-29
Try running "sudo apt-get update" and then "sudo apt-get install ia32-libs".  If nothing else works you can [download the package and install it manually here.](http://packages.ubuntu.com/lucid-updates/amd64/ia32-libs/download)

---

### Post by cadcam on 2010-09-30
i tried sudo apt-get update more than a few times.  the link you sent me is also one I found, but again, only for amd and not intel architecture.  

i just can't seem to find an intel one....

A.

---

### Post by linuxed on 2010-10-01
What does the following command output on your system?
```

uname -m

```
The ia32-libs package can be installed on either amd64 or ia64 systems.  There aren't separate packages for 64-bit Intel cpus.  Have you tried to install the amd64 package on your system using dpkg?
```

wget -P ~/Desktop "http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu26_amd64.deb"
sudo dpkg --force-architecture -i ~/Desktop/ia32-libs*.deb

```
If nothing else works you might try using the getlibs package.
```

wget -P ~/Desktop "http://frozenfox.freehostia.com/cappy/getlibs-all.deb"
sudo dpkg -i ~/Desktop/getlibs*.deb

```
With getlibs installed you can then try to download any missing libraries for wink.
```

wget -P ~/Desktop "http://mirrors.kernel.org/ubuntu/pool/multiverse/w/wink/wink_1.5.1060-6_i386.deb"
sudo dpkg --force-architecture -i ~/Desktop/wink*.deb
getlibs /usr/lib/wink/wink

```

---

### Post by cadcam on 2010-10-01
yeah the forcing architecture install ended badly.  didn't like it.

mantra@mantra:~$ uname -m
i686
mantra@mantra:~$

i tried the other stuff, and it was error filled as well, but now when I open wink, i get 

/usr/lib/wink/wink: error while loading shared libraries: libexpat.so.0:  cannot open shared object file: No such file or directory
mantra@mantra:~$ 
mantra@mantra:~$ aptitude search libexpat.so.0
mantra@mantra:~$ aptitude search libexpat
v   libexpat-dev                    -                                           
p   libexpat-ocaml                  - OCaml expat bindings                      
v   libexpat-ocaml-14p41            -                                           
p   libexpat-ocaml-dev              - OCaml expat bindings                      
v   libexpat-ocaml-dev-14p41        -           dp                                
i   libexpat1                       - XML parsing C library - runtime library   
i A libexpat1-dev                   - XML parsing C library - development kit   
mantra@mantra:~$ sudo apt-get install libexpat1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libexpat1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mantra@mantra:~$ sudo apt-get install libexpat-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libexpat1-dev instead of libexpat-dev
libexpat1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mantra@mantra:~$ wink
/usr/lib/wink/wink: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
mantra@mantra:~$ 

unsure whats happening here, i have this wink installed (though not functioning)
ii  wink           1.5.1060-6     Tutorial and Presentation Creating Software


i searched the ubuntu packages site, but i can't find anything useful 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

more thoughts?

---

### Post by linuxed on 2010-10-02
Well, I don't think you have a 64-bit OS installed.  The version of Ubuntu you're running appears to be the 32-bit version.  Regardless of whether your cpu supports 64-bit you still have to install the 64-bit version of the OS.  Since you appear to be running a 32-bit OS you shouldn't have to install the ia32-libs package which would also explain why it wasn't found in the software repository when you ran "apt-get install ia32-libs."

I would recommend running the following to purge the ia32-libs package from your system.
```

sudo dpkg --purge ia32-libs

```
Then make sure you have libexpat1 installed.
```

sudo apt-get install libexpat1

```
And finally create a symlink to the libexpat library.  If the first command throws an error just ignore it.  I can't remember if there is a symlink installed in the wink folder by default so it may state something like "file not found."
```

sudo rm /usr/lib/wink/libexpat.so.0
sudo ln -s /lib/libexpat.so.1 /lib/libexpat.so.0
sudo ln -s /lib/libexpat.so.0 /usr/lib/wink/libexpat.so.0

```

---

### Post by cadcam on 2010-10-03
huh.  it is possible the 64 bit version was overwitten when i formatted last week, as I didn't check the image to see which one I installed......suck.  ok, i'm gong to reinstall, with the 64 image, and then get back to you..  (luckily, installs of ubuntu take about, a second)


i686 means clearly does pertain to x86......damn.  my bad.  will write back once i reload.

thanks,
A

---

### Post by stevestark on 2010-10-03
what files do i need for karmic 9.10?

---

### Post by linuxed on 2010-10-04
> **stevestark said:**
> what files do i need for karmic 9.10?
Ignore the Ubuntu version listed in the thread's title.  The instructions should work for any recent version of Ubuntu including 9.10 or 10.04.

---

### Post by Jamina1 on 2011-07-29
I can't get this to work on 11.04. I am stuck at 
```
ematheson@elanor-ubuntu:~/Desktop$ sudo dpkg --force-architecture -i ~/Desktop/wink*.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding .../wink_1.5.1060-3ubuntu1_i386.deb containing wink:i386:
 libexpat1 conflicts with wink (<= 1.5.1060-4)
  wink:i386 (version 1.5.1060-3ubuntu1) is to be installed.
dpkg: error processing /home/ematheson/Desktop/wink_1.5.1060-3ubuntu1_i386.deb (--install):
 conflicting packages - not installing wink:i386
Errors were encountered while processing:
 /home/ematheson/Desktop/wink_1.5.1060-3ubuntu1_i386.deb

```

I tried the suggestion of sudo apt-get remove wink and received 
```
ematheson@elanor-ubuntu:~/Desktop$ sudo apt-get remove wink
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'wink' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```

I need this to work. I've installed everything else that's needed but libexpat1 is preventing me from installing wink. What do I do?

---

### Post by linuxed on 2011-07-29
```

sudo dpkg --purge wink
sudo apt-get install ia32-libs
sudo dpkg --force-architecture --force-conflicts -i wink*.deb
sudo rm /usr/lib/wink/libexpat.so.0
sudo ln -s /lib32/libexpat.so.1 /lib32/libexpat.so.0
sudo ln -s /lib32/libexpat.so.0 /usr/lib/wink/libexpat.so.0

```

---

### Post by thierrybo on 2012-11-21
My successful wink installation with Ubuntu 12.04 64bits 

```
sudo apt-get install ia32-libs
sudo apt-get install libstdc++5
sudo dpkg --force-architecture -i ~/wink*.deb
sudo rm /usr/lib/wink/libexpat.so.0
sudo ln -s /lib/i386-linux-gnu/libexpat.so.1.5.2 /lib/i386-linux-gnu/libexpat.so.0
sudo ln -s /lib/i386-linux-gnu/libexpat.so.0 /usr/lib/wink/libexpat.so.0
```

---

