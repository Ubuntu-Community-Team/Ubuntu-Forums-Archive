---
title: "HOW TO: Install fbcondecor"
date: 2011-05-07
forum: Tutorials
---

### Post by echo6 on 2011-05-07
[ATTACH]191467[/ATTACH][ATTACH]191478[/ATTACH]

If you have ever seen screen shots of Gentoo Linux then you may have wondered how the virtual terminals have graphical images in the background.

This is possible using a Kernel patch and splash utils writen by Michal Januszewski [http://dev.gentoo.org/~spock/projects/fbcondecor/](http://dev.gentoo.org/~spock/projects/fbcondecor/)

As this is a Kernel patch, you will need to recompile the Linux kernel to use the splash utils.

There are some old Debian packages available for splash utils e.g.
[http://forums.linuxmint.com/viewtopic.php?f=42&t=20973](http://forums.linuxmint.com/viewtopic.php?f=42&t=20973)
However these are getting a little long in the tooth.  Also there are some issues when trying to compile them manually, e.g.
[http://ubuntuforums.org/showthread.php?t=1503255](http://ubuntuforums.org/showthread.php?t=1503255)

Grab the latest version of the fbcondecor patch from [http://dev.gentoo.org/~spock/projects/fbcondecor/](http://dev.gentoo.org/~spock/projects/fbcondecor/) or
older versions are available here [http://dev.gentoo.org/~spock/projects/fbcondecor/archive/](http://dev.gentoo.org/~spock/projects/fbcondecor/archive/)

There are many guides available on how to compile a Linux kernel, and there are many guides available on compiling it the Ubuntu way.  If you are interested check out these guides
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)
[http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/)

I will describe what works for me!

Start a terminal session then do the following
```
mkdir fbcondecor
cd fbcondecor
wget http://dev.gentoo.org/~spock/projects/fbcondecor/archive/fbcondecor-0.9.6-2.6.38.patch
sudo apt-get install linux-source
sudo adduser $USER src
su $USER
cd /usr/src
mkdir linux-source
tar xvjf linux-source-2.6.38.tar.bz2 -C linux-source
cd linux-source/linux-source-2.6.38
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev libncurses5 libncurses5-dev
cp -v /boot/config-$(uname -r) .config
make menuconfig
```

Now navigate to Drivers->Graphics Support->Console Display Driver Support

[ATTACH]191469[/ATTACH]

Currently the options we require isn't available, we need to patch the kernel and disable some graphics drivers.
Exit out of the menuconfig

The first line is a dry run, you can use this to check that the patch will apply without errors. The second line applies the patch to the Kernel source code.

```
patch -p1 <~/fbcondecor/fbcondecor-0.9.6-2.6.38.patch --dry-run
patch -p1 <~/fbcondecor/fbcondecor-0.9.6-2.6.38.patch
```

Now we need to disable some Framebuffer drivers which are not compatible with the fbcondecor patch and will prevent us from selecting the Kernel option, do the following.

```
sed -i 's/CONFIG_FB_S3=m/CONFIG_FB_S3\ is\ not\ set/' .config
sed -i 's/CONFIG_FB_VT8623=m/CONFIG_FB_VT8623\ is\ not\ set/' .config
sed -i 's/CONFIG_FB_ARK=m/CONFIG_FB_ARK\ is\ not\ set/' .config
sed -i 's/CONFIG_FB_TILEBLITTING/CONFIG_FB_TILEBLITTING\ is\ not\ set/' .config
```

Now run make menuconfig and navigate to Drivers->Graphics Support->Console Display Driver Support
Now you have the Support for the Framebuffer Console Decorations option, [*] enable it!
Exit and save the config
[ATTACH]191690[/ATTACH]

```
sudo INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-fb kernel_image kernel_headers modules_image
```
It will take a while!

Once completed there will be two debian packages in the parent directory waiting to be installed.
```
cd ../
sudo dpkg -i linux-image-2.6.38.2-fb_2.6.38.2-fb-10.00.Custom_i386.deb linux-headers-2.6.38.2-fb_2.6.38.2-fb-10.00.Custom_i386.deb
```
Reboot into your new kernel

Now lets setup the splashutils.  We will also need miscsplashutils for one binary which we will compile and install manually, called fbres.

```
cd ~/fbcondecor
wget http://dev.gentoo.org/~spock/projects/fbsplash/current /splashutils-1.5.4.3.tar.bz2
wget http://dev.gentoo.org/~spock/projects/fbsplash/current/miscsplashutils-0.1.8.tar.bz2
tar zxvf splahutils-1.5.4.3.tar.bz2
cd splashutils-1.5.4.3
sudo apt-get install libgpm-dev libklibc-dev fbset
```

You only need to do this step if you have the initial release of Natty Narwal.
There is a bug in the release version of klibc, see [https://launchpad.net/ubuntu/+source/klibc/1.5.20-1ubuntu6](https://launchpad.net/ubuntu/+source/klibc/1.5.20-1ubuntu6) without fixing this splashutils will fail to compile. This is not really the prober way, it is just quick and dirty, remember after you have succesfully compiled you may want to remove the symlink
```
cd /usr/lib/klibc/include
sudo ln -sf ../../../include/i386-linux-gnu/asm asm
```

Now you are ready to compile the splashutils.

```
cd ~/fbcondecor/splashutils-1.5.4.3/
./configure
make
sudo make install
```

We need to patch the script splash_manager so it correctly locates our files, copy and paste the following into a file called splash_manager.patch

```
*** /usr/bin/splash_manager     2010-08-15 15:37:07.000000000 +0100
--- splash_manager      2010-08-15 15:43:17.772646002 +0100
***************
*** 25,34 ****
  spl_util=splash_util.static
  spl_daemon=fbsplashd.static
  spl_decor=fbcondecor_ctl
! spl_dir="//lib/splash"
  spl_fifo=${spl_dir}/cache/.splash
  spl_pidfile=${spl_dir}/cache/daemon.pid
! themedir="//etc/splash"

  spl_daemon_exename="$(basename ${spl_daemon})"
  spl_daemon_short="${spl_daemon:0:9}"
--- 25,34 ----
  spl_util=splash_util.static
  spl_daemon=fbsplashd.static
  spl_decor=fbcondecor_ctl
! spl_dir=""
  spl_fifo=${spl_dir}/cache/.splash
  spl_pidfile=${spl_dir}/cache/daemon.pid
! themedir="/etc/splash"

  spl_daemon_exename="$(basename ${spl_daemon})"
  spl_daemon_short="${spl_daemon:0:9}"
```

```
sudo patch -p1 /usr/bin/splash_manager < splash_manager.patch
```

Now for fbres. You will get compile errors don't worry about these, we are only interested in the fbres binary

```
cd ../
tar xvjf miscsplashutils-0.1.8
cd miscsplashutils-0.1.8
make
sudo cp -v fbres /bin/fbres
```

OK now get a sample theme file.

```
wget http://dev.gentoo.org/~spock/projects/fbsplash/current/fbsplash-theme-gentoo-r2.tar.bz2
tar xvjf fbsplash-theme-gentoo-r2.tar.bz2
sudo mikdir /etc/splash
cp -Rv gentoo /etc/splash/
```

Study the config files in gentoo/*.cfg use these as your template, replace the directory path in the .cfg files for any themes you create and for any images etc  fbsplash is used on Gentoo for the boot splash screen, so you won't need to worry about the silentpic line which is used for during boot.

You can have different backgrounds for each of your virtual terminals.  To set your theme edit the file /etc/rc.local as root and before the exit statement e.g.

```
for i in 1 2 3 4 5 6 7 ; do splash_manager -c set -t gentoo --tty=${i}; done
```

To test, switch to a virtual terminal and manually type
```
sudo splash_manager -c set -t gentoo --tty=1
```
Assuming you are on virtual terminal 1, you will see the Gentoo sample backdrop. You can remove the errors by editing the config file and removing the lines which specify the fonts it can't find.

[ATTACH]191468[/ATTACH]

TROUBLESHOOTING
1. Check that /dev/fbcondecor exists
2. Check that your image file conforms to supported types, is the correct size
3. Check that your config files have the correct paths for your images

REVERSING THE CHANGES
1. sudo dpkg -r linux-image-2.6.38.2-fb linux-headers-2.6.38.2-fb
2. If you haven't removed your splashutils directory cd ~/fbcondecor/splashutils-1.5.4.3 ; sudo make uninstall
3. Don't forget you will have to manually remove the /bin/fbres binary

---

### Post by Amnay on 2012-01-03
That worked for me perfectly (Ubuntu 10.10, Linux 3.1.0).
Thank you so much for posting this tutorial.
Compiling splashutils didn't succeed at first for it couldn't find libfreetype, but it worked eventually after installing pkg-config.

---

### Post by echo6 on 2012-01-15
Thanks for the reply, I really want to do a ppa for this to save having to go through the pain each time I do an install on a new machine.

---

### Post by nekro4083 on 2012-02-01
Thanks. Great post. Work fine for me.

---------------

Updating Ubuntu 11.10

1) The last version of splashutils (1.5.4.4) not compile in my ubuntu/kubuntu 11.10 (32bit). I using version 1.5.4.3 and compile fine.

Need the following packages

```

sudo apt-get install libjpeg62-dev libpng12-dev zlib1g-dev pkg-config libfreetype6-dev

```2) The miscsplashutils-0.8.1 as a path problem in libfreetype.a and libz.a 
For solving:

First method

```

sudo ln -s /usr/lib/i386-linux-gnu/libfreetype.a /usr/lib/libfreetype.a
sudo ln -s /usr/lib/i386-linux-gnu/libz.a /usr/lib/libz.a

```Second method

```

sudo cd /youSourceCode/fbtruetype
sudo nano -w Makefile

```and change this line from 

```

LIBSS    = $(LIBDIR)/libfreetype.a $(LIBDIR)/libz.a -lm

```to

```

LIBSS    = $(LIBDIR)/i386-linux-gnu/libfreetype.a $(LIBDIR)/i386-linux-gnu/libz.a -lm

```

Adjust path for fbres and usleep

```

sudo ln -s /lib/splash/bin/fbres /bin/fbres
sudo ln -s /lib/splash/bin/usleep /bin/usleep

```

Sorry for my bad english

---

