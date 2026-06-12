---
title: "xmms wma"
date: 2004-12-05
forum: The Cafe
---

### Post by mikeymike on 2004-12-05
how do i install it cause im used to fedora New to ubuntu

can u install rpms or is there another route to install it

---

### Post by adbak on 2004-12-05
Open up Synaptic and search for XMMS.  Right click on it and click Install.  Then click Apply.  Once it's done installing, it should be under Applications > Multimedia > XMMS.

---

### Post by mikeymike on 2004-12-05
[QUOTE=adbak]Open up Synaptic and search for XMMS.  Right click on it and click Install.  Then click Apply.  Once it's done installing, it should be under Applications > Multimedia > XMMS.[/QUOTE]


lol i kno that part...  thanks anyways but i shoulda been more specific 

Does anybody know how to install the .wma package "xmms-wma" so i can play .wma files with xmms

---

### Post by adbak on 2004-12-05
I don't think that there's a package called xmms-wma that you can download, but try installing the package "libmikmod2" and that may cover wma files.  I don't have any wma files so I can't test it on my machine, but I know that that package works for mp3s too.

---

### Post by ayam on 2004-12-21
I had WMA support on Beep-Media-Player [BMP], which is very similar visually to XMMS from a basic users perspective, when I was using Slackware and it cna be done on Warty

1) Fire up synaptic (sorry not too familiar with apt commands yet) and get Beep-Media
 player 
2) Then I got a bmp wma plug-in that is already compiled etc. I just found a RPM format. My file was called libwma.so
3) Copy this ****.so file into /home/<username>/.bmp/Plugins/Input/libwma.so 
You probably ned to create some of teh directories
4) Start BMP and goto Preferences>Audo I/O Plugins and see if WMA player is listed. This shold work no probs

NOTE 1: I also installed libgtk1.2, xmms and libmikmod in the fustration fo getting this plugin to work. It was strange but the plugin was not listed even though I had the file copied into the plugin directory and then one day I started the ocmputer and I accidently played a WMA file. 

NOTE 2: Try a range of WMA plugins for BMP as I have two version that I tried for Slackware and Ubuntu. Only one of them works. I can't remember where I found this file :( Hope this helps!

---

### Post by shimon on 2004-12-21
why not just download w32codec from mallrat? a lot easier

---

### Post by JCaudill on 2004-12-23
I had this same question.  I have a ton of wma files, and I want to play them with XMMS.  Here is what I did to get it to work on Ubuntu.

apt-get install xmms          (to get xmms)
apt-get install xmms-dev    (needed for xmms-config app)

Once I had that I grabbed this file:  [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2)

This is the source for the xmms-wma plugin.  I then extracted it and ran make install.
After that I started up xmms and it magically plays WMA files now.  

Hope this helps!  email me if you need help.  I can try to help you directly.

---

### Post by nocturn on 2004-12-23
[QUOTE=JCaudill]I had this same question.  I have a ton of wma files, and I want to play them with XMMS.  Here is what I did to get it to work on Ubuntu.

apt-get install xmms          (to get xmms)
apt-get install xmms-dev    (needed for xmms-config app)

Once I had that I grabbed this file:  [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2)

This is the source for the xmms-wma plugin.  I then extracted it and ran make install.
After that I started up xmms and it magically plays WMA files now.  

Hope this helps!  email me if you need help.  I can try to help you directly.[/QUOTE]


If you are using xmms, are you getting the extremly small fonts too?
Thanks

Guy

---

### Post by JCaudill on 2004-12-23
[QUOTE=nocturn]If you are using xmms, are you getting the extremly small fonts too?
Thanks

Guy[/QUOTE]

I run 1600x1200 on my 20" lcd.  The fonts on xmms are a little small.  I figured that a skin may help, but I haven't looked into that.

---

### Post by homerhomer on 2005-02-12
Here's a wma for Beep. I just aliened an rpm and it works well

enjoy

:D

To install it, just uncompress the file and as root type

dpkg -i filename.deb

---

### Post by jasplund on 2005-03-01
[QUOTE=homerhomer]Here's a wma for Beep. I just aliened an rpm and it works well

enjoy

:D

To install it, just uncompress the file and as root type

dpkg -i filename.deb[/QUOTE]

It doesn't work. The file installs and it appears as installed in synaptic but there's no wma-plugin in beep.

---

### Post by Topper on 2005-04-30
[QUOTE=homerhomer]Here's a wma for Beep. I just aliened an rpm and it works well

enjoy

:D

To install it, just uncompress the file and as root type

dpkg -i filename.deb[/QUOTE]

I tried it and it works great. Thanks!

---

### Post by mikeymike on 2005-04-30
well what i did cause i figured it out a while back 

is download the rpm from here
[http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/) 

then 
```
sudo alien xmms-wma-1.0.4-1.i386.rpm   
```
then
```
sudo dpkg -i *.deb
```

* = the path etc.....

then it works after your restart

---

### Post by jiyuu0 on 2005-04-30
updated:
[http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)

---

### Post by linTrog on 2006-02-13
works perfectly thx!

---

### Post by grit on 2006-02-14
[QUOTE=jiyuu0]updated:
[http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)[/QUOTE]

Works like a charm, thanks :)

---

### Post by TechSonic on 2006-02-15
O.o what the hell.. .I got WMA support in XMMS.  All I had to do was install the w32codecs and all formats started working, even XM and IT.

However, you could just use Sound converter and make an MP3 or OGG (recommended)

---

### Post by flapane on 2006-05-03
does anyone compiled libwma.so from beep media player?
The [http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)  one caus TONS OF PROBLEMS like segmentation fault, so google says that ppl used to compile the bmp one and they say it's GREAT [http://prdownload.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz](http://prdownload.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz)
I can't manage to, I get lot of errors while compiling...

---

### Post by xaxa100 on 2006-10-20
is the same package working if you want to listen to online radio??

---

### Post by Lord Darth Vader on 2007-02-06
It worked! It didn't even need to restart the system.

---

### Post by Iona on 2007-03-08
Thanks - This totaly solved my problem.  XD

Ty,
Damien.

---

### Post by treblesix on 2007-07-17
I still can't play WMA files :(

I have tried installing those packages, but it says I have a later version of XMSS-WMA installed.

According the the XMMS prefs, I have v1.0.5 installed. The WMA files will load into the playlist, but they will not play.

Anyone got any ideas?

---

