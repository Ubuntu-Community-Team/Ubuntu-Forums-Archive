---
title: "HOWTO: SimCity 3000 on 9.04/9.10 (including 64-bit)"
date: 2009-10-25
forum: Tutorials
---

### Post by overridex on 2009-10-25
I recently had a craving to play some of my older Loki games, but I quickly found that games made for Linux distributions from 2001 or so don't work so easily on modern distributions.  Here's a quick run down on how to get the SimCity 3000 native Linux port working again.

Be sure to check out my howto for Sid Meier's Alpha Centauri and Kohan: Immortal Sovereigns as well:

[http://ubuntuforums.org/showthread.php?t=1206578]("http://ubuntuforums.org/showthread.php?t=1206578")

You'll need to following files before we get started:

[http://www.overridex.net/files/loki_compat_libs-1.3.tar.bz2]("http://www.overridex.net/files/loki_compat_libs-1.3.tar.bz2")
[http://www.overridex.net/files/loki_patch]("http://www.overridex.net/files/loki_patch")
[http://www.overridex.net/files/sc3u-2.0a-x86.run]("http://www.overridex.net/files/sc3u-2.0a-x86.run")

**Step 1: Install the game**

Insert your game cd and run the following commands, assuming the game is in your first cdrom:

```

cd /media/cdrom
linux32 /bin/bash setup.sh

```

Cancel or press Ctrl-C for the Loki Update and Loki Uninstall setups, then install SimCity 3000 - I installed everything, and I installed to ~/games/SC3U with the symlinks in ~/bin.  If you want to install somewhere system wide, you will need to run the install as root with sudo.

If you see messages like these during the install:

```

Unable to find file 'bin/x86/sc3u'
Unable to find file 'bin/x86/lib'

```

Then you should run the following commands after install to copy over some files that weren't copied.  Assuming you installed to ~/games/SC3U:

```

cp -r /media/cdrom/bin/x86/glibc-2.1 ~/games/SC3U/.
cd ~/games/SC3U
ln -s glibc-2.1/* .

```

**Step 2: Update the game**

Run the following commands in the directory where you downloaded the game patch and loki_patch to:

```

chmod +x ./sc3u-2.0a-x86.run
_POSIX2_VERSION=199209 ./sc3u-2.0a-x86.run --keep
cd sc3u-2.0a-x86/bin/Linux/x86
cp ../../../../loki_patch .
cd ../../..
PATH=./bin/Linux/x86/:$PATH ./update.sh

```

**Step 3: Install the Loki Compatibility libraries**

Extract the loki_compat_libs-1.3.tar.bz2 file somewhere - I put it in ~/games/ since I planned to use them for more than one game, and my games are installed in sub directories there.

```

tar xvjf /path/to/downloaded/loki_compat_lib-1.3.tar.bz2

```

**Step 4: Running the game**

You can now run the game by changing to the game's directory, and running the following command:

```

LD_LIBRARY_PATH=../Loki_Compat/ SDL_AUDIODRIVER="dsp" SDL_PATH_DSP="/dev/dsp" ../Loki_Compat/ld-linux.so.2 ./sc3u.dynamic

```

**Step 5: Running the game via a script**

You can automate starting the game by creating the following script in your game directory.  I named mine runsc3u.sh:

```

#!/bin/sh
# A simple shell script to launch SimCity 3000 on a modern Linux distribution

SCRIPTLOC=$0
DIRNAME=""

# Step through symlinks to find where the script really is
while [ -L $SCRIPTLOC ]; do
        SCRIPTLOC=`readlink $SCRIPTLOC`
done

# Get the directory the script is in, then change to it
DIRNAME=`dirname $SCRIPTLOC`
cd $DIRNAME

# Run the game
LD_LIBRARY_PATH=../Loki_Compat/ SDL_AUDIODRIVER="dsp" SDL_PATH_DSP="/dev/dsp" ../Loki_Compat/ld-linux.so.2 ./sc3u.dynamic $*

```

Remember, if you have Loki_Compat installed somewhere else, you'll need to update the last command of the script.

You should also symlink runsc3u.sh into your PATH somewhere - ~/bin is in my PATH, so I created a symlink there.

**Ready to play!**

You should now be all set to play by running 'runsc3u.sh'.  You may want to create a new entry in your menu to launch this, which you can do under System->Preferences->Menu Editor. You can find an icon to use attached to this post.

Have fun, let me know if you run into any problems following this tutorial.

---

### Post by Thoddy on 2010-02-17
For me it doesn't work! :(

I've tried so many things to get SC3U running on my ubuntu 9.10, none of them worked. I was actually even thinking about installing an old ubuntu (with a 2.2.5 kernel) on a virtual machine using VirtualBox!! :D


Usually my tries ended up in segfaults or other things, but now (with this tutorial) the game actually seems to start...

...but then I get a black screen with a blue bar that has a little green and a little red line in it. Seems like a dialog with two buttons, but no test and only the lines instead of buttons (very low resolution, too). There's nothing I can do, can't press these lines, or go on pressing ESC or some like that. I can't even stop the game by finding the PID and doing a 'kill -9 PID', actually need to 'kill -9 -1', which obvioulsy is annoying!! :(

Any ideas, anyone?

---

I am running ubuntu 9.10 karmic on a 32-bit quad core intel chip with 4gig of ram. And I have the original "Sim City 3000 Unlimited Linux" CD.

---

### Post by sg_free on 2010-09-22
Thank you so much for posting these instructions!  I had mourned the loss of my SC3K on an old RedHat worktation, and, having just loaded Ubuntu 10.04 on my PC, used your guidance to install this and it works great!
happy joy!

---

### Post by desperado618 on 2011-05-11
During the first step of running setup.sh I receive a message that I do not have write access to /usr/bin. I also tried it using sudo and get an error saying it cant find the file (sudo sh setup.sh). 
Can I install everything into my home directory to avoid the error? If so, do I need to modify any path statements? 
is this error occurring because I am installing from a locally mounted ISO?

Any assistance would be greatly appreciated.

FYI I am running maverick 64bit

---

### Post by linuxsafari on 2011-12-03
Updated links to files, as of dec 2011:

at [http://icculus.org/loki_setup/](http://icculus.org/loki_setup/) :
[http://svn.icculus.org/loki_setup]("http://svn.icculus.org/loki_setup")
[http://svn.icculus.org/loki_patch]("http://svn.icculus.org/loki_patch")
[http://svn.icculus.org/loki_update]("http://svn.icculus.org/loki_update")
[http://svn.icculus.org/loki_setupdb]("http://svn.icculus.org/loki_setupdb")

at [http://updates.lokigames.com/sc3u/](http://updates.lokigames.com/sc3u/) :
[http://updates.lokigames.com/sc3u/sc3u-2.0a-x86.run]("http://updates.lokigames.com/sc3u/sc3u-2.0a-x86.run")

at [http://www.swanson.ukfsn.org/loki/](http://www.swanson.ukfsn.org/loki/) :
[http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.4.tar.bz2]("http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.4.tar.bz2")

---

### Post by linuxsafari on 2011-12-03
> **linuxsafari said:**
> Updated links to files, as of dec 2011:

at [http://icculus.org/loki_setup/](http://icculus.org/loki_setup/) :
[http://svn.icculus.org/loki_setup]("http://svn.icculus.org/loki_setup")
[http://svn.icculus.org/loki_patch]("http://svn.icculus.org/loki_patch")
[http://svn.icculus.org/loki_update]("http://svn.icculus.org/loki_update")
[http://svn.icculus.org/loki_setupdb]("http://svn.icculus.org/loki_setupdb")

at [http://updates.lokigames.com/sc3u/](http://updates.lokigames.com/sc3u/) :
[http://updates.lokigames.com/sc3u/sc3u-2.0a-x86.run]("http://updates.lokigames.com/sc3u/sc3u-2.0a-x86.run")

at [http://www.swanson.ukfsn.org/loki/](http://www.swanson.ukfsn.org/loki/) :
[http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.4.tar.bz2]("http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.4.tar.bz2")

loki_patch pre-compiled file can be found at [http://icculus.org/~msphil/loki/x86/loki_patch](http://icculus.org/~msphil/loki/x86/loki_patch)

---

