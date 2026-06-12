---
title: "how to compile wine 1.16 with acceptEx patch?"
date: 2009-03-02
forum: Wine
---

### Post by Yeeha on 2009-03-02
As i see infamous acceptEx bug still is problem for playing warcraft3 and other good old games. Apparently theres patch for it [http://bugs.winehq.org/show_bug.cgi?id=9787](http://bugs.winehq.org/show_bug.cgi?id=9787) but how to use it? Any help appreciated.

---

### Post by snakt on 2009-06-20
im not very experienced, but, from what i can tell the alterd source file needs to be placed into the source of 1.16 and then compiled for your use.

I dont know how to compile wine but ill gather some links:

Wine bug tracking link for AcceptEX [http://bugs.winehq.org/show_bug.cgi?id=9787]("http://bugs.winehq.org/show_bug.cgi?id=9787")

From this link there is some information about wine 1.18 not compiling with AcceptEX

Compiling wine from source code [http://www.winehq.org/docs/wineusr-guide/installing-wine-source]("http://www.winehq.org/docs/wineusr-guide/installing-wine-source")

Compiling wine from source code with patches [http://www.wine-reviews.net/benchmarks/compile-wine-with-the-3dmark-patch.html]("http://www.wine-reviews.net/benchmarks/compile-wine-with-the-3dmark-patch.html")

If anyone else can shed some more light on this i would also like to use this patch. The only reason i keep going back to windows is because i cant chat in Warcraft III. Yes i know, this is a very sad reason to do that to myself, but its the only game i play anymore.

Good luck, letme know if you have a win :D

---

### Post by snakt on 2009-06-20
The patch is in this link :D [http://bugs2.winehq.org/attachment.cgi?id=836]("http://bugs2.winehq.org/attachment.cgi?id=836")

I'm going to attempt the compile myself now, ill let you know how it goes. ;)

---

### Post by snakt on 2009-06-20
For compiling wine 1.1.24 on ubuntu jaunty.

Steps I have taken to compile wine with the patch are as follows (although all steps may not be needed):

DEPENDENCIES:

Make sure you remove any existing wine installations or configurations.

I donk know id it matters but if you have had a previous installation of wine the configuration directory is in you home directory. Delete (after backup?) all the contents of ".wine"

```
sudo apt-get install build-essentials
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get build-dep wine
```

Copy information for patch from the following link [http://bugs.winehq.org/attachment.cgi?id=8368]("http://bugs.winehq.org/attachment.cgi?id=8368") into a file named "acceptex.patch".

Download the latest (another if you like but I'm doing latest) from [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449").

Extract the wine source code into its own directory EG. "wine-1.1.24-source"

Copy the patch file created earlier into the folder the wine source was extracted.

```
cd ./wine-1.1.24-source
```

```
patch -p1 < acceptex.patch
```

COMPILING:

```
./configure
```

Output ening in "configure: Finished.  Do 'make depend && make' to compile Wine." means this has completed successfully.

At this point it is time to make a cup of coffie / pot of soup / walk the dog. You may have enough time to do all of these things ZZzZzzzZzzzz....

```
make depend && make
```

INSTALL:

The install command must be run with sudo as the installer needs permissions to modify copy etcc to /usr ++ more
```
sudo make install
```


IT WORKS!!!!!!!!!!!!!!!!!! WOHOOOOO!!!!!!!!!!!!!!!!!!!!!!

Total time: About 50 mins.
Result: PRICELESS!!!:popcorn::KS:p):P:D:mad::p;)

---

### Post by snakt on 2009-06-21
After some testing i am getting some random crashes when in game, reverting to source code from stable release wine v1.0.1.

I let you know how it goes :D

---

### Post by stimpak on 2009-06-27
do you know if you need to uninstall any older version , or you can just install on top of it?

---

### Post by snakt on 2009-06-27
Yes you need to remove it, I have found a much better and stabler mehod on the wine webpage.

See the "How to get Battle.net working?" section of this webpage (see link below).

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126&iTestingId=41436]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126&iTestingId=41436").

---

### Post by grizlo42 on 2009-07-01
i tried following both sets of directions, and I either have the same problem, or i get an error saying it can't find the disk even if its there and installed....

---

### Post by grizlo42 on 2009-07-01
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub

when i use the git version

---

### Post by snakt on 2009-07-02
Sorry mate, I haven't run into this issue as i use a directory I have had for some time now, I just add the custom servers to the registry and I'm off.

Not that I know but it sounds like your having issues with SecurRom.

If you have an existing directory just running it from there should do wonders.

FYI: Now that I have been running the GIT from WineHQ i have had no issues from Warcraft except when loosing focus of the window you get white textures and flashing.

Other then that (without trying to alt-tab or using in wine desktop mode) i have had no issues and can see every everyone's chat just fine.

---

