---
title: "Need an experienced linux user :)"
date: 2009-11-26
forum: Wine
---

### Post by Xog on 2009-11-26
OS: 9.10 Karmic Koala
wine ver: 1.1.33 (1.2)

Topic: Getting the game "Continuum" (wine.getcontinuum.com) running on the latest wine version.

Issue: Last wine version was working fine with the instructions from the aforementioned website.

The instructions:
> 
0. If you do not already have wine installed on your system, install wine in the standard way on your system.

1. Download standard Continuum installer - 4.7 MB

2. Run the installer downloaded above (default options are fine) on wine.
```

sudo mv /usr/lib/wine/kernel32.dll.so{,.bak}

sudo wget http://subspace2.net/kernel32.dll.so -O /usr/lib/wine/kernel32.dll.so

```
4. Run Continuum.

5. PLAY!

Task: Patch the new wine kernel for this game to run.

Problem: After backing up the wine kernel and getting the patched version, it creates a segmentation fault. Wine basically is broken after patching. Nothing works, not even winecfg. Error returned in terminal after "winecfg" is "Segmentation Fault." A reinstall of wine is needed after patching.

Nobody from ssforum.net or the minegoboom forums (advanced development teams for the game) are around or active very much anymore. I am however in contact with the site editor for wine.getcontinuum.com and when your working  patch is announced, it will be brought to their attention and all credit for the patch will go to you on the website. Gen2ly is here on the ubuntuforums and as you can see his latest patch was credited to him on the website.

Thanks, good luck!  Everything is appreciated!

---

### Post by beastrace91 on 2009-11-27
I see on their website they offer a .deb installer for Wine already compiled with the patch - have you tried installing with this?

Also have you tried compiling Wine from source yourself with the patch applied instead of just over writing the kernel file like their site suggests?

Cheers,
~Jeff

---

### Post by Xog on 2009-11-27
> **beastrace91 said:**
> I see on their website they offer a .deb installer for Wine already compiled with the patch - have you tried installing with this?

Also have you tried compiling Wine from source yourself with the patch applied instead of just over writing the kernel file like their site suggests?

Cheers,
~Jeff

I'm pretty sure that installs wine 1.0.0-rc1 and not 1.1.33

and i don't know how to compile wine, I'm not all that advanced  :P

---

### Post by beastrace91 on 2009-11-27
If their pre-patched version is for the stable Wine release (1.0.0) then I might also be wondering if that kernel file you are copying over is also intended for an older version as well (and thus causing your issues). Most times patches like this need to be kept updated for each successive Wine release.

If you can get a copy of the patch they use can I walk you through compiling Wine from source/applying the patch to the source.

Regards,
~Jeff

---

### Post by Xog on 2009-11-28
> **beastrace91 said:**
> If their pre-patched version is for the stable Wine release (1.0.0) then I might also be wondering if that kernel file you are copying over is also intended for an older version as well (and thus causing your issues). Most times patches like this need to be kept updated for each successive Wine release.

If you can get a copy of the patch they use can I walk you through compiling Wine from source/applying the patch to the source.

Regards,
~Jeff

I uninstalled my other wine version and installed this patched wine version, I'm playing the game now but as of this moment, everything else I enjoy cannot be accessed because of this wine version. I need 1.1.33. If there's anything you can do to help me, let me know.

---

### Post by beastrace91 on 2009-11-28
Sounds like you need to setup multiple version of Wine on your system. I know [Play on Linux](http://playonlinux.com/) is suppose to be able to aide is setting something like this up. Or if you want to do it using just Wine I found a couple pages that might be useful to you:

[Advanced Wine Installations:Multiple Installs](http://wiki.jswindle.com/index.php/Advanced_Wine_User_Installation#Managing_Multiple_Installs)
[Old Nabble Thread on the Topic](http://old.nabble.com/~FAQ:-parallel-install-of-multiple-wine-versions-td22273005.html)

Cheers,
~Jeff

---

### Post by Xog on 2009-12-04
```

mkdir ~/contwine-build
cd ~/contwine-build
sudo apt-get build-dep wine
sudo apt-get source wine
cd wine1.2-1.1.31
sed -i '2568 i\\if (access \& PROCESS_VM_WRITE) return NULL;' dlls/kernel32/process.c
./configure
make
sudo checkinstall

```
At this point the modified wine is installed, so I ran the normal cont installation:
```

wget http://getcontinuum.com/downloads/continuum/Continuum040Setup.exe
wine Continuum040Setup.exe

```
and it all runs fine.

(note: if "checkinstall" isn't already installed, you may have to first issue "sudo apt-get install checkinstall" to get it)[/quote]

---

