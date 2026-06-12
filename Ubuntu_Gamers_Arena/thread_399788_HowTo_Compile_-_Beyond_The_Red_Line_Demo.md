---
title: "HowTo: Compile - Beyond The Red Line Demo"
date: 2007-04-02
forum: Ubuntu Gamers Arena
---

### Post by hikaricore on 2007-04-02
[size=4]*** This HOWTO is now outdated.  The [official linux demo installer]("http://homepage.ntlworld.com/karajorma/Misc-Downloads/BtRLDemo-Linux.torrent") has been released ***
*[thanks aidanr for the status update on the release]*  :)[/size]

[SIZE="3"]_HowTo: Compile Beyond The Red Line Demo (from source)_[/SIZE]

[I]At the time I'm writing this, the linux installer has not yet been released.
I imagine this will become obsolete in a matter of weeks.[/I]

Ok first let me start by saying this howto is written for Ubuntu Edgy.
It should work about the same way under Dapper and Feisty, but I can't guarantee all libraries will be availible via the repos, especially in Dapper.  >.<

For this howto you will need the following:

1. btrl demo source
2. btrl demo windows installer
3. wine or a windows pc to steal the installed files from
4. libsdl-dev (and friends), libtheora-dev, libogg-dev, libvorbis-dev
5. you'll obviously need build-essential installed but this assumes you already have
...(if you don't have build-essential run: *sudo apt-get install build-essential*)

You will need the download and install the windows version:
(either with WINE or install on a windows machine then copy the data files)
[http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Windows.torrent](http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Windows.torrent)
[http://files.filefront.com/7090920](http://files.filefront.com/7090920)
[http://www.thecylonbase.com/index.php?option=com_frontpage&Itemid=1](http://www.thecylonbase.com/index.php?option=com_frontpage&Itemid=1)
[http://games.internode.on.net/filelist.php?filedetails=6722](http://games.internode.on.net/filelist.php?filedetails=6722)
[http://files.moddb.com/6720/download-bsg-beyond-the-red-line-demo/](http://files.moddb.com/6720/download-bsg-beyond-the-red-line-demo/)

Save this file to your home directory.

Open a new terminal (you should be at your home directory but it isn't required).

```

wget http://www.freespacefaq.com/Downloads/BtRL/btrl_fs2_open-3.6.9.tar.bz2
sudo apt-get install libsdl1.2-dev libogg-dev libtheora-dev libvorbis-dev libalut0 libopenal0a libopenal-dev

```

This should install the following (23 libraries in all i believe):

> libalut-dev libalut0 libopenal0a libsdl1.2-dev libogg-dev libtheora-dev libaa1-dev
libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev libdirectfb-dev libdirectfb-extra
libesd0-dev libgl1-mesa-dev libglu1-mesa-dev libjpeg62-dev libncurses5-dev libsdl1.2-dev
libslang2-dev libxt-dev mesa-common-dev libopenal-dev

Now that all the the libraries are installed, decompress the btrl demo archive and begin compiling.

```

tar -jxvf btrl_fs2_open-3.6.9.tar.bz2
cd btrl_fs2_open-3.6.9
./configure
make

```

The make process will take awhile depending on your system, so bounce around the fourms or go
for a walk or something while you wait. :)

Assuming all went well and the game binary compiled it should now be in the code directory inside the
directory you compiled from.

But before we go any further you'll need to install the windows version of the demo so that you
have the data, graphic, and sound files needed to actually run the demo.  Assuming you already have
wine installed and working:

```

wine ../BtRLDemoInstaller.exe

```

Wait for the installer window to come up and follow through installation.

This may take awhile as the decompressed data files are about 750mb.  The installer may even seem to freeze,
just give it 10-20 minutes to complete and try not to get too anxious.  :P  Remember where you install the
game so we'll be able to copy the game binary that has already been compiled.

You should still be in the *~/btrl_fs2_open-3.6.9* directory once the installer completes.
Copy the binary to the location you installed Btrl windows demo into.

Example:

```

cp code/fs2_open_r ~/.wine/drive_c/Program\ Files/BtrlDemo

```

Then we'll change to the game directory and launch the demo.

```

cd ~/.wine/drive_c/Program\ Files/BtrlDemo
./fs2_open_r

```

The game will probably give you an error message saying the resolution is not supported.
Simply exit the game by hitting escape twice, and we're back to our terminal one last time.  :)


```
pico ~/.btrl_demo/fs2_open.ini
```

Find this line:

> VideocardFs2open=OGL -(800x600)x16 bit

I believe it was 800x600 but no matter, it's that line.  Replace it with this:

> VideocardFs2open=OGL -(**1024x768**)x16 bit

ctrl+o to save, then ctrl+x to exit

Then you should be able to launch the game using:

```
./fs2_open_r
```

Hopefully I've covered everything possible here.

Please let me know if I"ve missed anything.

I'll also be posting this up on UGA in a few minutes, but I promised the forums I'd do it, so I wanted to post here first.  ^_^

---

### Post by aidanr on 2007-04-03
nice, wine needed pdh.dll and odbcbcp.dll for the installer to work, they can be found through google, and put in ~/.wine/drive_c/windows/system32

runs really well and it's a great game :)

---

### Post by loctar on 2007-04-04
Hm, I get the game running, but once I go to the BriefingRoom it crashes...

[I]ERROR: "Could not load ABexp04 anim file" at fireball/fireballs.cpp:697
Vertex3f: 1[/I]

Anyone got a fix?

---

### Post by aidanr on 2007-04-04
the linux installer is up now, try that instead

[http://homepage.ntlworld.com/karajorma/Misc-Downloads/BtRLDemo-Linux.torrent](http://homepage.ntlworld.com/karajorma/Misc-Downloads/BtRLDemo-Linux.torrent)

---

### Post by Perfect Storm on 2007-04-04
Thanks for the link/tips, aidanr.

---

### Post by hikaricore on 2007-04-04
Figures they'd post it up while I'm busy.  :P

I've been watching their site for a day and a half, rofl.

---

### Post by Perfect Storm on 2007-04-04
They sneaked it out while you were looking the other way :popcorn:

---

### Post by hikaricore on 2007-04-04
Just a note if you install anywhere but the default directory you may have to edit the "/usr/local/bin/btrl_demo" file.

```
sudo pico /usr/local/bin/btrl_demo
```

I personally added:

FSO_DATA_PATH="/media/devistate/linux.bin/beyondtheredline"

Before the "export" section as shown below:

> 
**FSO_DATA_PATH="/media/devistate/linux.bin/beyondtheredline"**

export LD_LIBRARY_PATH
export FSO_DATA_PATH

PL2PATH="${HOME}/.btrl_demo/data/players/single"


This may have been an issue I caused myself but incase anyone else comes across it.  :)

---

