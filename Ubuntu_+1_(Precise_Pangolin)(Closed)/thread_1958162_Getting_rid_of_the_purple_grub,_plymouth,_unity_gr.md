---
title: "Getting rid of the purple grub, plymouth, unity greeter"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by audibel on 2012-04-13
Don't get me wrong, I like purple.  It's a regal color, and it has it's place, but it's not on my desktop.  So my mission has been to rid myself of all the purple on the desktop.  That includes the grub screen, plymouth boot splash, and the purple polka dotted mat before my user background is displayed in unity greeter.  

I wanted to compile a list of all of this information in one place so that a. other people could use it as a reference, and b. I wouldn't have to worry about forgetting it.  These are the answers which have worked for me, if you have anything to add please do so.  If something doesn't work for you please let me know.

We'll start with the earliest process: grub.  These instructions were taken from AskUbuntu here: [http://askubuntu.com/questions/47488/how-to-change-the-purple-background-color-in-grub](http://askubuntu.com/questions/47488/how-to-change-the-purple-background-color-in-grub)

```
sudo gedit /lib/plymouth/themes/default.grub
```

In gedit change the color here:

```
if background_color 200,200,200; then
   clear
fi
```

200,200,200 is the rgb value for gray which is what I've chosen, set it to whatever rgb value you'd like.  Then:

```
sudo update-grub
```

Next we move to Plymouth. Instructions following are taken from the Khattam Blog:  [http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html](http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html)

```
sudo cp -R /lib/plymouth/themes/ubuntu-logo /lib/plymouth/themes/ubuntu-logo-nonpink
sudo gedit /lib/plymouth/themes/ubuntu-logo-nonpink/ubuntu-logo.plymouth
```
edit the file so that it looks like this:
```
[Plymouth Theme]
Name=Ubuntu Logo NonPink
Description=A theme that features a blank background with a logo.
ModuleName=script
 
[script]
ImageDir=/lib/plymouth/themes/ubuntu-logo-nonpink
ScriptFile=/lib/plymouth/themes/ubuntu-logo-nonpink/ubuntu-logo.script
```
save and exit.  Next we edit the actual colors:
```
sudo gedit /lib/plymouth/themes/ubuntu-logo-nonpink/ubuntu-logo.script
```
and in gedit edit the colors here::
```
Window.SetBackgroundTopColor (0.85, 0.85, 0.85);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.75, 0.75, 0.75);  # an equally nice colour on the bottom
```
These colors are the RGB values divided by 256.  So .75x3 is an RGB value of 192, 192, 192.  We'll stick with the gray theme.  Khattam recommends for this color inverting the color of the logo file itself.  
```
sudo gimp /lib/plymouth/themes/ubuntu-logo-nonpink/ubuntu_logo.png
```
and then going to the Color -> Invert.  Once you've done editing your new plymouth theme you can add it by:
```

sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-logo-nonpink/ubuntu-logo.plymouth 100
sudo update-alternatives --config default.plymouth

``` and selecting the number corresponding to non-pink.  You finish up by:
```
sudo update-initramfs -u
```
That takes care of Plymouth.  

Unity-greeter is the trickiest one and the one that requires the most work.  This is actually a bug and hopefully one day it will be fixed, but for now in order to rid yourself of the purple polka dots you have to download the source for unity-greeter, patch it and then edit a small conf file in the /etc/lightdm directory.  If you don't feel comfortable doing this then you'll just have to wait until it's fixed somewhere down the road.  

The bug is reported here: [https://bugs.launchpad.net/lightdm/+bug/970024](https://bugs.launchpad.net/lightdm/+bug/970024)  The patch is available from that bug report.  So working from your ~ directory (or other directory of your choosing ~/src would be a good one.
```
apt-get source unity-greeter
cd unity-greeter-0.2.7/
wget -q https://launchpadlibrarian.net/100026654/lightdm%20backgroundcolor2.patch
patch -p0 < "lightdm backgroundcolor2.patch"
./configure
```

If you have a functional development environment you may have all the packages necessary, but probably not.  One of the packages required is gtk+-3.0  This is added using:
```
sudo apt-get install libgtk-3-dev
```
The others I installed in order to keep it from groaning were:
```
libglib2.0-dev (2.32.0-1ubuntu3)
libpcre3-dev (8.12-4)
libpcrecpp0 (8.12-4)
libvala-0.16-0 (0.16.0-1ubuntu1)
valac-0.16 (0.16.0-1ubuntu1)
valac-0.16-vapi (0.16.0-1ubuntu1)
zlib1g-dev (1:1.2.3.4.dfsg-3ubuntu4)
libappindicator3-dev (0.4.92-0ubuntu1)
libdbus-1-dev (1.4.18-1ubuntu1)
libdbus-glib-1-dev (0.98-1ubuntu1)
libdbusmenu-glib-dev (0.6.1-0ubuntu2)
libgtk2.0-dev (2.24.10-0ubuntu6)
libindicator-dev (0.5.0-0ubuntu1)
liblightdm-gobject-1-dev (1.2.0-0ubuntu2)
libxklavier-dev (5.2.1-1ubuntu1)
libxml2-dev (2.7.8.dfsg-5.1ubuntu4)
libindicator3-dev (0.5.0-0ubuntu1)
libcanberra-dev (0.28-3ubuntu3)
libcanberra-gtk-common-dev (0.28-3ubuntu3)
libcanberra-gtk3-dev (0.28-3ubuntu3)
autoconf (2.68-1ubuntu2)
automake (1:1.11.3-1ubuntu2)
autotools-dev (20120210.1ubuntu1)
intltool (0.50.2-2)
libxml-parser-perl (2.41-1build1)
m4 (1.4.16-2ubuntu1)
```

  sudo apt-get install all of those packages or use synaptic which is probably easier.  You should then be able to:
```
./configure
make        
sudo make install

```
See the following two posts for a better, more ubuntu way to do the previous step.

and that will install the patched unity-greeter, but according to the bug report you will have to create the file /etc/lightdm/greeter-bottom-color.conf and put in a valid html color
Mine looks like this:
```
#C0C0C0
```
and that's the entire contents of the file.  If there's any more purple on your desktop please let me know, because I've done my best to irradicate all traces of royal nastiness.  Reboot and enjoy.

---

### Post by NHclimber on 2012-04-13
Well organized and clear. Thanks.

I would recommend building unity-greeter 'the debian/ubuntu way' though, rather than with configure/make/install. If you build it as a package, then it can be removed/downgraded or upgraded when they fix the bug.  Also, you can grab the packages necessary for building a package with apt-get build-dep (it's not foolproof though - sometimes necessary build-deps are missing).

To get a working environment necessary for building most ubu packages:
```
sudo apt-get install build-essential devscripts
```To install libraries, etc necessary for building unity-greeter:
```
sudo apt-get build-dep unity-greeter
```Then, using and adding to your shell commands:
```
apt-get source unity-greeter
cd unity-greeter-0.2.7/
wget -q https://launchpadlibrarian.net/100026654/lightdm%20backgroundcolor2.patch
patch -p0 < "lightdm backgroundcolor2.patch"
debuild -us -uc
cd ..
sudo dpkg -i unity-greeter*.deb

```

---

### Post by mc4man on 2012-04-14
> **NHclimber said:**
> 
```
apt-get source unity-greeter
cd unity-greeter-0.2.7/
wget -q https://launchpadlibrarian.net/100026654/lightdm%20backgroundcolor2.patch
patch -p0 < "lightdm backgroundcolor2.patch"
[COLOR="Blue"]dpkg-source --commit[/COLOR]
debuild -us -uc
cd ..
sudo dpkg -i unity-greeter*.deb

```

If you don't commit the changes from the patch then debuild will error out, 'error: aborting due to unexpected upstream changes', ect.

Running the blue will pop up a choice to name patch, then  nano is good, if desired can edit in description ect., though not necessary.
At a min just ctrl+o, enter, ctrl+x, then proceed with debuild ...

(patch will be added to /debian/patches
If not wanting to do this then use instead of debuild ..

dpkg-buildpackage -rfakeroot -D -us -uc

*Usually find best to first mkdir <whatever> & cd to it, keeps all the files contained in one place
For packages I know I'm keeping usually up the version so the/it doesn't update back but so I'll get informed of a new version, I use +nmu1

Just to note - the deal with debuild/dpkg-source --commit is  sources with 'format' 3.0 (quilt) which the greeter source is

---

### Post by audibel on 2012-04-15
Excellent advice, didn't even think of this while I was doing, wish I would have :)

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by audibel on 2012-04-15
> **MarkieB said:**
> Is there a way to simply change the background image/s?

The answer to *simply* changing the background image/s would be no, no simple way.  I guess it depends on what version of Ubuntu you're using and which images you want to change.  I think that would be a great HOWTO to write as well, but my main goal was to eliminate all the purple.  There are plenty of plymouth splash screen themes out there to use if you want a nice graphic on startup.  Me I just didn't want the purple :)  Setting the background image for unity-greeter is done automatically for 12.04 based on the user wallpaper.  

Which backgrounds are trying to change?

Now what I'd really like is a seamless boot image from grub to unity-greeter, but it's a more difficult topic.

---

### Post by MarkieB on 2012-04-15
no longer participating in ubuntuforums.org

---

### Post by Holstener Liesel on 2012-04-26
It's also possible (and much easier) to use lightdm-gtk-greeter  from the ubuntu repos instead of unity greeter.

---

