---
title: "Musepack plugins for xmms and beep-media-player added"
date: 2005-06-25
forum: Ubuntu Backports
---

### Post by Slo Mo Snail on 2005-06-25
Hi,
I added bmp-musepack and xmms-musepack to extras a few minutes ago... can someone test these? the sources of these packages lie in sources...

for more information about musepack visit [http://www.musepack.net](http://www.musepack.net)

---

### Post by tristure on 2005-06-26
Hi, I would like to test xmms-musepack, but I still can't find it.

I've got :
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

in my sources.list

I ran apt-get update, then apt-cache search musepack, or xmms, or mpc, and couldn't find it. What am I doing wrong?
Thanks.

---

### Post by Slo Mo Snail on 2005-06-26
It's currently in extras-staging (and libmpcdec in backports-staging)
add these 2 lines to your sources.list

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

---

### Post by tristure on 2005-06-26
Thank you.

Right now I have problems with libmpcdec. Here's the output (in french) :

Dépaquetage de libmpcdec3 (à partir de .../libmpcdec3_1.2-1~5.04ubp1_i386.deb) ...
dpkg*: erreur de traitement de /var/cache/apt/archives/libmpcdec3_1.2-1~5.04ubp1_i386.deb (--unpack)*:
 tentative de remplacement de «*/usr/lib/libmpcdec.so.3.0.0*», qui appartient aussi au paquet libmpcdec
dpkg-deb: sous-processus paste tué par le signal (Relais brisé (pipe))
Des erreurs ont été rencontrées pendant l'exécution*:
 /var/cache/apt/archives/libmpcdec3_1.2-1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tristan@dhcp-255-84:~$

As far as I understand, the problem is that it tried to install libmpcdec3 whereas I have libmpcdec installed...

---

### Post by tristure on 2005-06-26
Nevermind, I uninstalled libmpcdec and installed libmpcdec3, and installed the wmms plugin succesfully. Seems to be working for no. I'll report later if I encounter further problems.

---

### Post by Slo Mo Snail on 2005-06-26
I don't speak french (?) but it seems you have libmpcdec already installed (compiled from hand probably? or from another source?)

Just remove the old package and reinstall...

---

### Post by WMCoolmon on 2005-06-29
I can't seem to see either; I'm guessing that's because I'm on AMD64. I do know that I was able to get bmp-musepack working on this platform, though. IIRC, I basically installed libmusepack and bmp-musepack from source. Not sure if I had to jump through any more hoops than that.

---

### Post by Slo Mo Snail on 2005-06-29
I don't have any amd64 machines here so there is no amd64 binary package... but I think the sources should build on amd64...
was everything compiled ok for you? and what exactly does not work?

---

### Post by Oktane on 2005-06-30
I've solved problem with playing mpc files in xmms by hands. I've got deb-package libmpcdec3_1.2-1_i386.deb from [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) and then to so:

1. extract the data.tar.gz from libmpcdec3_1.2-1_i386.deb
2. extract the libmpcdec.so.3.0.0 from data.tar.gz to xmms libraries folder (in my case it was ///usr/lib/xmms/Input)
3. restart xmms
4. have fun with listening mpc's :)

I hope it will help somebody ;)

---

### Post by pateretou on 2005-07-02
Hello
packages deleted ? :(
Thx

Pat

---

### Post by Slo Mo Snail on 2005-07-03
Yes they're deleted... I'll reupload them in an hour, but with a different (lesser) version as the way I versioned them before will make problems when updating to breezy

EDIT: uploaded them again for x86... ppc follows later. Everybody who has installed the old packages should "downgrade" them ;)

---

### Post by WMCoolmon on 2005-07-04
[QUOTE=Slo Mo Snail]I don't have any amd64 machines here so there is no amd64 binary package... but I think the sources should build on amd64...
was everything compiled ok for you? and what exactly does not work?[/QUOTE]

Yeah, everything seemed to compile fine once I had the right packages. And it worked fine too, at least in BMP; I don't think I ever got things working in XMMS.

How hard would it be for me to put things together so they could be packaged?

---

### Post by WMCoolmon on 2005-07-08
Alright, using checkinstall I've created .deb packages for libmpcdec and the bmp-plugin packages for AMD64.

If you want to compile the libraries manually, grab them from the musepack site, and make sure you **use the option "--prefix=/usr" for libmpcdec**. Other than that, it's a simple ./configure; make; make install; style procedure. You shouldn't get any compiler errors or need any workarounds to get them to work.

I don't have anyplace to upload the .deb packages tonight, if I feel like trying to get SFTP working tomorrow and remember them, I'll get 'em uploaded.

Edit: Also, you'll need libtag-dev installed to compile them.

Edit 2: It looks like some of my MPC files aren't working and crash bmp as soon as it tries to display their length in the playlist; I'm not sure if this is due to corruption (it just seems to be most of one directory) or some bug with the plugin.

---

### Post by ad1138 on 2005-08-14
The version available now on the repositories suggested in the "Unofficial Starter Guide" (which is version 1.2 RC1) made BMP crash, so I tried to compile it (downloaded from musepack.net). Everything went ok, but BMP still crashes when I try to add (not even to play) a MPC file.

---

### Post by RaymondQE on 2005-08-16
Hey guys, There's a huge memleak with APE tagged MPC files when using taglib 1.3.1.  You can compile a newer version from source using the instructions listed at the bottom of this thread

[http://www.ubuntuforums.org/showthread.php?t=34997&page=1&pp=10&highlight=musepack](http://www.ubuntuforums.org/showthread.php?t=34997&page=1&pp=10&highlight=musepack)

---

### Post by Slo Mo Snail on 2005-08-17
yeah i fixed the memleak for breezy... btw, the two plugins are in breezy now :)

---

### Post by RaymondQE on 2005-08-17
Thanks Slo Mo Snail for adding the patch to libtag.  I'm not using Hoary, so will hoary users be able to apt-get it from backports and if so, will the libtag packages have new names e.g. libtag0c2?

---

