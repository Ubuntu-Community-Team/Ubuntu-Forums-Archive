---
title: "Using virtualbox from server install, light gui for vuze config?"
date: 2009-06-14
forum: Server Platforms
---

### Post by talz13 on 2009-06-14
Ok, I know that I don't need a GUI on my new server install for pretty much anything (webmin FTW!), but there are two instances where I'm a bit troubled.

The first is that currently I run a virtualbox "application" on a cron job every morning on my desktop.  This is one main thing I want to get transferred over to the server.  I am already running the VM in "headless" mode, so that should be okay when running on the server.  I was just wondering if simply installing virtualbox by adding the vbox repository and doing "sudo apt-get install virtualbox-2.2" would suffice, since it looks like it pulls in an awful lot of packages to set itself up.

Secondly, I use azureus (vuze) for my torrent app.  I'm quite happy with it, don't want to change, love the specific plugins I use, basically my torrent client choice is not up for discussion.  I have not run it in headless mode before, though, and need to know about setup.  Right now I am planning on just copying all relevant azureus folders from my desktop to the server to be run there (which should keep my configs and everything intact), but I don't know what to do about configuring the plugins.  The main plugins that would need periodic configuration are the Speed Scheduler and RSSFeed Scanner plugins.  I do not believe that these have any simple command line configuration options, and RSSFeed Scanner uses some kind of binary configuration, so manually editing the file would be out of the question for that.  My question on this point is, is it possible to install a very lightweight gui that would only be run when I need to config these plugins and then quit after it is done?  Or could I do X forwarding somehow to just launch the app in GUI mode over the network on my desktop?


Thanks!

---

### Post by lmlypfan on 2009-06-14
Its funny you posted this, i'm in the middle of installing VMware's server platform on my headless 9.04 server. 

Not sure if i 100% understand your question, but I'm fairly confident you cannot just install VirtualBox on a headless server by simply using apt-get. 

Wouldn't it try and install a complete desktop?

Like i said, I'm trying out VMware's server version.

---

### Post by talz13 on 2009-06-15
I might just try out vmware server if I can import my virtualbox image or set up my application easily again.

As far as azureus (vuze) goes, I have gotten it running on the console by copying my existing folders from my ubuntu 64 desktop to the ubuntu 64 server.  I read at:

[http://blog.kagesenshi.org/2006/12/howto-building-x-less-azureus-dedicated.html](http://blog.kagesenshi.org/2006/12/howto-building-x-less-azureus-dedicated.html)

that I should be able to run Xnest and forward the azureus to my local xnest server (or local X server if using ssh X forwarding), but have some issues with running azureus that way.  It appears that it is looking for "swt-pi-gtk-3448" or "swt-pi-gtk" libraries but can't find them.  It is also looking for "GRE/XULRunner" where firefox would have installed things, but there is no firefox by default in ubuntu server:
```
jeff@server2:~/vuze$ echo $DISPLAY
localhost:10.0
jeff@server2:~/vuze$ export DISPLAY=192.168.1.5:1.0
jeff@server2:~/vuze$ echo $DISPLAY
192.168.1.5:1.0
jeff@server2:~/vuze$ ./azureus 
Starting Azureus...
Suitable java version found [java = 1.6.0_13]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: no swt-pi-gtk-3448 or swt-pi-gtk in swt.library.path, java.library.path or the jar file
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib64/firefox-addons for GRE
	Can not use GRE from /usr/lib64/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/xulrunner-addons for GRE
	Can not use GRE from /usr/lib64/xulrunner-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-addons for GRE
	Can not use GRE from /usr/lib/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-addons for GRE
	Can not use GRE from /usr/lib/xulrunner-addons because it's missing components/libwidget_gtk2.so.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuzehas better luck.
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx512m -cp "./Azureus2.jar:./commons-cli.jar:./log4j.jar:./swt.jar" -Djava.library.path="/home/jeff/vuze" -Dazureus.install.path="/home/jeff/vuze" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/jeff/vuze/Azureus2.jar ; file:/home/jeff/vuze/commons-cli.jar ; file:/home/jeff/vuze/log4j.jar ; file:/home/jeff/vuze/swt.jar ; file:/home/jeff/vuze/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Mon Jun 15 11:30:11 EDT 2009::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::69:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to '/tmp'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::110,Main::<init>::84,Main::main::217,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::39,DelegatingMethodAccessorImpl::invoke::25,Method::invoke::597,MainExecutor$1::run::37,Thread::run::619
java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3448 or swt-pi-gtk in swt.library.path, java.library.path or the jar file
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:233)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:130)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:92)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:69)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:217)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:619)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
jeff@server2:~/vuze$ 
```

I have investigated the part of the error message where it suggests:```
DEBUG::Mon Jun 15 12:17:04 EDT 2009::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::69:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to '/tmp'. SWT will extract libraries contained in the swt.jar to this dir.
``` and have downloaded the latest swt-3.4-gtk-linux-x86_64.zip from eclipse, and verified that /tmp is r/w for my user, and that the libswt-gtk-3452.so is extracted to /tmp:```
jeff@server2:/$ ls -l | grep tmp
drwxrwxrwt   7 root root  4096 2009-06-15 12:17 tmp
jeff@server2:/$ cd tmp
jeff@server2:/tmp$ ls -l
total 556
drwxr-xr-x 2 jeff jeff   4096 2009-06-15 12:17 hsperfdata_jeff
-rwxr-xr-x 1 jeff jeff 278200 2009-06-15 09:58 libswt-gtk-3448.so
-rwxr-xr-x 1 jeff jeff 278200 2009-06-15 12:17 libswt-gtk-3452.so
jeff@server2:/tmp$ 
```
so I'm pretty sure that those couple common reasons are not what is happening here.

---

### Post by grantemsley on 2009-06-15
Azureus can theoretically be run without a GUI, but as you've realized it's a PITA to configure that way.

My solution was to install X4vnc and run azureus under that.  You can then connect via VNC from any computer.  It DOES require installing alot of the GUI stuff, but won't start up a full X server on the console.

I also have a script that starts it on boot in /etc/init.d/azureus which I can post if you want.

---

### Post by lmlypfan on 2009-06-15
Here is the guide I used for VMware server.


[http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/]("http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/")

I got it working on the first try, which is a first for me.

---

### Post by talz13 on 2009-06-17
> **grantemsley said:**
> Azureus can theoretically be run without a GUI, but as you've realized it's a PITA to configure that way.

My solution was to install X4vnc and run azureus under that.  You can then connect via VNC from any computer.  It DOES require installing alot of the GUI stuff, but won't start up a full X server on the console.

I also have a script that starts it on boot in /etc/init.d/azureus which I can post if you want.

How did you go about getting X4vnc?  It's not in the repository, is it?

---

### Post by talz13 on 2009-06-19
Ok, here's what I ended up doing:

1.  I just installed virtualbox from the virtualbox repo.  I already had the VM configured, so all I did after that was copy my .VirtualBox folder to the server and continue to run the headless VM as I have in the past.  It pulled a bunch of packages, but it didn't seem to start lots of unnecessary processes, so it's all good.

2.  For Azureus configuration, I just wrote a tiny script to copy the vuze directory from my server to my local machine, run azureus from that directory, change any settings I need to, then copies the local copy back to the server.  It's a bit of a roundabout way of doing things, but if it means simple configuration and no X server processes running, I'm all for it.  Here's the script below:```
#! /bin/bash

SERVER='server2'
REMOTEUSER='jeff'
LOCALUSER='jeff'

rsync -av $SERVER:/home/$REMOTEUSER/vuze/ /home/$LOCALUSER/vuzeSettings/
echo "Got server azureus settings!"
/home/$LOCALUSER/vuzeSettings/azureus &
azureuspid=$!
wait $azureuspid
echo "Done running azureus!"
rsync -av /home/$LOCALUSER/vuzeSettings/ $SERVER:/home/$USER/vuze/
echo "Done pushing azureus settings!"
echo "Please restart azureus on the affected server..."
```

Then I basically used the guide at [http://www.azureuswiki.com/index.php/HeadlessSwingUIAtBoot](http://www.azureuswiki.com/index.php/HeadlessSwingUIAtBoot) to get azureus running from boot, and possibly exiting on shutdown.  I went into webmin and set up a new bootup and shutdown action like so:```
#!/bin/sh
# run azureus on boot

case "$1" in
'start')
	/home/jeff/azureus_script start
	;;
'stop')
	/home/jeff/azureus_script stop
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0
```

---

### Post by grantemsley on 2009-06-22
> **talz13 said:**
> How did you go about getting X4vnc?  It's not in the repository, is it?

Package is xvnc4server.

I love the way I have mine setup, since I can VNC in to change bandwidth settings or check how the torrents are doing.  I really hate azureus's web interface.

The only complicated part of the init script is this part for starting it up:

```

        su $USER -c '( Xvnc4  -screen 0 1280x768 -br -fp /usr/share/fonts/X11/misc/ \
        -PasswordFile /home/$USER/.vnc/passwd -extension XFIXES \
        -httpd /usr/share/vnc-java/ -httpport 5802 :2 >/dev/null 2>&1 &) \
        && sleep 2 && export DISPLAY=:2 && \
        (exec gnome-session >/dev/null 2>&1 &) && sleep 2 && \
        (/home/$USER/azureus/azureus >/dev/null 2>&1 & )'

```

That:

- Starts the VNC server with resolution 1280x768 as user $USER, with a password file previously created.
- Starts gnome-session (you can use fluxbox or another lightweight system, nor none at all, but sometimes things don't appear properly with no window manager
- Starts azureus

Stopping it was a little tricky too...I ended up with this hack:
```

        # Stop azureus gracefully I hope
        if [[ ` ps -ef | grep "/home/$USER/azureus/azureus"|grep -v grep` ]]
        then
                echo -n "Stopping $DESC"
                su $USER -c "kill `ps -ef | grep "/home/$USER/azureus/azureus" | grep "java" | grep -v grep | awk '{print $2}'`"
                echo " ... done."
        else
                echo "Coulnd't find a running $DESC"
        fi

        sleep 10
        # Stop vnc by looking for the command using its passwd file...
        if [[ ` ps -ef | grep "/home/$USER/.vnc/passwd"|grep -v grep` ]]
        then
                echo -n "Stopping VNC server"
                su $USER -c "kill `ps -ef | grep "/home/$USER/.vnc/passwd" | grep -v grep | awk '{print $2}'`"
                echo " ... done."
        else
                echo "Coulnd't find a running VNC server"
        fi

```

It's been running well for me for over a year now.

---

### Post by talz13 on 2009-06-23
> **grantemsley said:**
> Package is xvnc4server.

I still can't find a package for it.  I have universe and multiverse enabled in my sources.list, but all I come up with is:```
[sudo] password for jeff:
linuxvnc - VNC server to allow remote access to a tty
tkvnc - Displays a list of (defined) machines to start VNC to
xtightvncviewer - virtual network computing client software for X
xvnc4viewer - Virtual network computing client software for X
xwnc - Mix of Xvnc and XDarwin with improved protocol
```
Any ideas?

---

### Post by grantemsley on 2009-06-23
My apologies, the package is "vnc4server" and is in universe.

```

Package: vnc4server
Priority: optional
Section: universe/x11
Installed-Size: 2484
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Ola Lundqvist <opal@debian.org>
Architecture: i386
Source: vnc4
Version: 4.1.1+xorg1.0.2-0ubuntu7
Provides: vnc-server, x0vnc-server
Depends: libc6 (>= 2.4), libfontenc1, libgcc1 (>= 1:4.1.1-21), libice6 (>= 1:1.0.0), libsm6, libstdc++6 (>= 4.1.1-21), libx11-6, libxau6, libxdmcp6, libxext6, libxfont1 (>= 1:1.2.9), libxtst6, vnc4-common | vnc-common, x11-common, xbase-clients, xfonts-base, zlib1g (>= 1:1.2.3.3.dfsg-1)
Suggests: vnc-java
Filename: pool/universe/v/vnc4/vnc4server_4.1.1+xorg1.0.2-0ubuntu7_i386.deb
Size: 1089358
MD5sum: 98d31f7f75fbd39ff9ac38c3ad168d4f
SHA1: 17a30e3bd15daac84749fbef45ea88825b1f56b9
SHA256: acae54d2bde2062c109fb5beb033cc8e335303e4f0c5632ac87135e221a5338b
Description: Virtual network computing server software
 VNC stands for Virtual Network Computing. It is, in essence, a remote
 display system which allows you to view a computing `desktop' environment
 not only on the machine where it is running, but from anywhere on the
 Internet and from a wide variety of machine architectures.
 .
 This package provides a vncserver to which X clients can connect and the
 server generates a display that can be viewed with a vncviewer.
 .
 It contains an X server connector so clients can connect to your local X
 desktop directly.
 .
 Note: This server does not need a display. You need a vncviewer to see
 something. This viewer may also be on a computer running other operating
 systems.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by talz13 on 2009-06-27
Ok, I finally gave up on getting RSSFeed Scanner to work with the console mode azureus, so I gave your vnc4server script a try (modified for my dirs):```
su $USER -c '( Xvnc4  -screen 0 1280x768 -br -fp /usr/share/fonts/X11/misc/ \
        -PasswordFile /home/$USER/.vnc/passwd -extension XFIXES \
        -httpd /usr/share/vnc-java/ -httpport 5800 :2 >/dev/null 2>&1 &) \
        && sleep 2 && export DISPLAY=:2 && \
        (exec fluxbox >/dev/null 2>&1 &) && sleep 2 && \
        (/home/$USER/vuze/azureus >/dev/null 2>&1 & )'
```

Which starts up the Xvnc4 server up alright, but I'm still having problems with azureus.  I VNC'd in to the box, opened a command prompt, and launched azureus:```
jeff@server2:~/vuze$ ./azureus
Starting Azureus...
Suitable java version found [java = 1.6.0_13]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: no swt-pi-gtk-3452 or swt-pi-gtk in swt.library.path, java.library.path or the jar file
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib64/firefox-addons for GRE
        Can not use GRE from /usr/lib64/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/xulrunner-addons for GRE
        Can not use GRE from /usr/lib64/xulrunner-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-addons for GRE
        Can not use GRE from /usr/lib/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-addons for GRE
        Can not use GRE from /usr/lib/xulrunner-addons because it's missing components/libwidget_gtk2.so.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuzehas better luck.
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx512m -cp "./Azureus2.jar:./commons-cli.jar:./log4j.jar:./swt.jar" -Djava.library.path="/home/jeff/vuze" -Dazureus.install.path="/home/jeff/vuze" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/jeff/vuze/Azureus2.jar ; file:/home/jeff/vuze/commons-cli.jar ; file:/home/jeff/vuze/log4j.jar ; file:/home/jeff/vuze/swt.jar ; file:/home/jeff/vuze/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Sat Jun 27 13:17:03 EDT 2009::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::69:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to '/tmp'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::110,Main::<init>::84,Main::main::217,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::39,DelegatingMethodAccessorImpl::invoke::25,Method::invoke::597,MainExecutor$1::run::37,Thread::run::619
java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3452 or swt-pi-gtk in swt.library.path, java.library.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:92)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:69)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:217)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
        at java.lang.Thread.run(Thread.java:619)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
jeff@server2:~/vuze$ 
```

which are the same errors I was getting when just exporting display to my local xnest and running it.  I really think there is some underlying issue in why azureus won't startup in gui mode.

Oh, and I have DEFINITELY made sure that I am using the 64bit SWT library, so I really have no idea what it is talking about in the error message.

---

### Post by grantemsley on 2009-06-29
Can't help you with those errors, but if you want a better way to use RSS with azureus, check out flexget ([http://flexget.com/](http://flexget.com/))

It's a python script with a variety of good filters to parse the torrents you want out of an rss feed, and dump the torrents into a directory (you can set azureus to watch a directory for torrents, so they get auto imported).

I've been using it for a few months now, since the azureus plugin filters were a pain to configure. It's run through cron, and has a simple text based config file.

You'll have to read up on it's language for the config file a bit, it's somewhat difficult to understand at first, and is VERY picky about spacing.  But it's worked flawlessly for quite some time now, and doesn't download duplicates or items I don't want.

---

### Post by dmizer on 2009-06-29
I also ended up ditching Azureus for usability concerns. I'm happily using the default Deluge instead.

---

### Post by grantemsley on 2009-06-29
I've tried out Deluge, and it works quite well.  IIRC, the reason I didn't use it was because of the way it moves completed torrents or something like that...and because it's not on the acceptable client list for a couple private trackers I use.

---

