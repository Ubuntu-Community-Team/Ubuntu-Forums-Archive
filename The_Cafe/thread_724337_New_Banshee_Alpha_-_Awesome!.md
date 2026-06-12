---
title: "New Banshee Alpha - Awesome!"
date: 2008-03-14
forum: The Cafe
---

### Post by Mazza558 on 2008-03-14
[http://abock.org/2008/03/13/banshee-10-alpha-1/]("http://abock.org/2008/03/13/banshee-10-alpha-1/")

This looks amazing.

**To install from source:**

Follow this guide:

[http://banshee-project.org/OnePointEx/TrunkOnUbuntu]("http://banshee-project.org/OnePointEx/TrunkOnUbuntu")

followed by this:

[http://banshee-project.org/OnePointEx/BuildingAndRunning]("http://banshee-project.org/OnePointEx/BuildingAndRunning")

(See the "Building" section)

---

### Post by hyperair on 2008-03-14
What do you mean they require gstreamer package which aren't in the repos? If you do ```
sudo apt-get build-dep banshee
``` you should get all the required packages immediately.

EDIT: Either way I'm building a .deb, I'll post it when I'm done. However, it may or may not work in Gutsy, because I'm using Ubuntu Hardy.

Also, read this: [http://banshee-project.org/OnePointEx/TrunkOnUbuntu](http://banshee-project.org/OnePointEx/TrunkOnUbuntu)

About the .deb, it seems make segfaulted while running.. =\ I'll see what I can do, but no guarantees.

---

### Post by Mazza558 on 2008-03-14
> **hyperair said:**
> What do you mean they require gstreamer package which aren't in the repos? If you do ```
sudo apt-get build-dep banshee
``` you should get all the required packages immediately.

EDIT: Either way I'm building a .deb, I'll post it when I'm done. However, it may or may not work in Gutsy, because I'm using Ubuntu Hardy.

Also, read this: [http://banshee-project.org/OnePointEx/TrunkOnUbuntu](http://banshee-project.org/OnePointEx/TrunkOnUbuntu)

About the .deb, it seems make segfaulted while running.. =\ I'll see what I can do, but no guarantees.

Thanks, compiling now.

---

### Post by natedawg on 2008-03-14
YES!!! I have been waiting for this release for months now. It will be so nice to finally have a play queue in banshee.  I'm compiling now :)

---

### Post by Mazza558 on 2008-03-14
Wow, it's really nice, even for a preview/alpha. I love the Last.fm integration. This'll replace Exaile for me, for sure. Only problem is, it's now crashed X twice for me.

---

### Post by hyperair on 2008-03-14
Deb ready! Get it here: [http://www.mediafire.com/?q2obdmyyykj](http://www.mediafire.com/?q2obdmyyykj)

---

### Post by n3tfury on 2008-03-14
> **Mazza558 said:**
> [http://abock.org/2008/03/13/banshee-10-alpha-1/]("http://abock.org/2008/03/13/banshee-10-alpha-1/")

This looks amazing. Only problem is, I can't install from source due to requiring the gstreamer packages (they're not in the repos). Anyone got a deb files?

hm.  when i clicked on this thread you made it seem like you've been using it.  nice job to draw attention.

---

### Post by bobbocanfly on 2008-03-15
New alpha looks brilliant. Only started using banshee about 20 minutes ago but loving it. This seems to add to the greatness.

---

### Post by Polygon on 2008-03-15
> **hyperair said:**
> Deb ready! Get it here: [http://www.mediafire.com/?q2obdmyyykj](http://www.mediafire.com/?q2obdmyyykj)

your deb doesnt work, it tells me that dependency is not satisfiable (libc6) but when i try to install it:

mark@Aurora:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@Aurora:~$

also compiling the source requires me to either install or compile some other stuff, so far ive had to install 'monodoc' from apt-get, and then compile mono.addins (google) and ndesk.dbus in order for banshee to not complain, It finally just got done through configure, so i shall see how it works after its done compiling

edit2: i give up, even after install mono-addins and ndesk-dbus it still says those files are missing. whatever.

---

### Post by tretle on 2008-03-15
I have  the same libc6 issue :(

---

### Post by hyperair on 2008-03-15
Could you do:
```

apt-cache policy libc6

```

---

### Post by bobbocanfly on 2008-03-15
No need to use a deb really, compiling is dead easy. 

```
cd wherever-you-downloaded-it
tar -xvf banshee-1-0.98.1.tar.bz2
cd banshee-1-0.98.1
sudo apt-get build-dep banshee
./configure
make
sudo make install 
```

When you want to remove it im pretty sure the makefile has an uninstall clause so cd back into the source directory and run

```
sudo make uninstall
```

---

### Post by Mazza558 on 2008-03-15
> **n3tfury said:**
> hm.  when i clicked on this thread you made it seem like you've been using it.

Wow, that seems pretty far fetched to me. Although I said "awesome", there was an equal chance that I had either used it or was commenting on the screenshot. 

>  nice job to draw attention

Nice job to start a flamewar.

---

### Post by FuturePilot on 2008-03-15
I'm guessing it was compiled against Hardy's libc6.
I got the same error as well.

---

### Post by pjalegria on 2008-03-15
me too:(

---

### Post by hyperair on 2008-03-15
> **Mazza558 said:**
> Wow, that seems pretty far fetched to me. Although I said "awesome", there was an equal chance that I had either used it or was commenting on the screenshot. 



Nice job to start a flamewar.

That is enough. He may feel like instigating, but you are only dropping to his level if you respond.

> **FuturePilot said:**
> I'm guessing it was compiled against Hardy's libc6.
I got the same error as well.

Bingo. I'm very sorry I don't have a Gutsy installation I could compile from. Perhaps if I'm free I'll use a LiveCD on a VM and compile it there.

---

### Post by Mazza558 on 2008-03-15
> **hyperair said:**
> That is enough. He may feel like instigating, but you are only dropping to his level if you respond.


Don't worry, I only respond to the first aggravating comment, in case the poster wishes to come back and apologise. After that, it's a waste of my time and the poster will learn that they're not getting anywhere.

---

### Post by hyperair on 2008-03-15
> **Mazza558 said:**
> Don't worry, I only respond to the first aggravating comment, in case the poster wishes to come back and apologise. After that, it's a waste of my time and the poster will learn that they're not getting anywhere.
Well that's good to know.

---

### Post by NullHead on 2008-03-15
hyperair: 

I don't suppose there is a chance you could compile a deb for amd64???

If not it's fine I'll test your deb out in my 32bit hardy install :D

---

### Post by Perpetual on 2008-03-15
Thanks for the mention of the new Banshee Alpha.  Looking forward to trying it out later today.

I do hope though that it works better with my ipod.  Specifically, when I delete files from my ipod in Banshee it does not actually free the space on the ipod.  The tracks are no longer accessible but the free space on the ipod does not change.  I have read others have this issue but have never really dug deep into a fix.

Regardless, I really like banshee so am excited about a new version!

---

### Post by hyperair on 2008-03-15
No it's not possible for me to do that-I just don't know how. However, I will post instructions on how to compile a deb below:

1. Install build-essential, dpkg-dev and fakeroot
```
sudo apt-get install build-essential dpkg-dev fakeroot
```
2. Install Banshee's build-dependencies
```
sudo apt-get build-dep banshee
```
3. Navigate into a directory where we can dump all our rubbish in:
```
mkdir -p ~/src/banshee && cd ~/src/banshee
```
4. Get the deb sources for the current version of Banshee in Ubuntu's repositories:
```
apt-get source banshee
```
5. Get the archive of the new Banshee:
```
wget http://banshee-project.org/files/banshee/banshee-1-0.98.1.tar.bz2
```
6. Extract the source of the new Banshee:
```
tar xvjf banshee-1-0.98.1.tar.bz2
```
7. Copy the debian folder from the old Banshee folder to the new Banshee folder:
```
cp -r banshee-0*/debian banshee-1-0.98.1
```
8. Enter the Banshee folder:
```
cd banshee-1-0.98.1
```
9. Edit the debian/changelog file
```
gedit debian/changelog
```
Add this to the top:
```

banshee (0.98.1~hyperbuntu0) unstable; urgency=low

  * New upstream release (1.0 Alpha 1)
  
 -- Hyperair <hyperair@gmail.com>  Sat, 15 Mar 2008 03:12:30 +0800

```
You can replace the name and email address with your own, and change the timestamp also, but it really doesn't matter.

10. Replace the contents of debian/banshee.install with this:
```

debian/tmp/usr/bin
debian/tmp/usr/share
debian/tmp/usr/lib/pkgconfig
debian/tmp/usr/lib/banshee-1
debian/banshee.xpm /usr/share/pixmaps

```

11. Remove all patches, they won't patch on the new source:
```

rm -f debian/patches/*

```

12. Compile!
```
dpkg-buildpackage -rfakeroot
```

13. Install your deb:
```
sudo dpkg -i ../banshee*.deb
```

If it goes well, don't forget to upload your deb and post a link back here =)

---

### Post by FuturePilot on 2008-03-15
Great How To ;)
I don't have time now but I will try to compile this with those instructions when I get some time. :)

---

### Post by hyperair on 2008-03-15
Oh I'd also like to express my thanks to the opener of this thread, he alerted me to the existence of this new version of Banshee. =D I can finally ditch the resource hogging Amarok (it does in GNOME at least) and shift over to a Gtk solution!

[quote=FuturePilot]Great How To
I don't have time now but I will try to compile this with those instructions when I get some time.[/quote]

Thanks.

---

### Post by Superkoop on 2008-03-15
I'm not sure, (I haven't tried installing this .deb) but I think the libc6 problem is similar to a problem I had when I installed the latest version of The Mana World. So I had to temporarily enable the hardy repos to get it.
Open:
```

sudo gedit /etc/apt/sources.list
```

Then add the following line to the bottom:

```
deb http://archive.ubuntu.com/ubuntu/ hardy main
```
Save it.
Now:
```

sudo apt-get upgrade
```

Go ahead and upgrade your libc6 now, either from the terminal or synaptic.
While you have that repository open, ONLY update the libc6. You could get yourself in some trouble if you try updating some other things.

When you are done getting it, just comment it out, or else delete that line from the sources.list.
And update again:

```
 sudo apt-get upgrade 
```

That *should* satisfy your dependency. 
But do note: DO THAT AT YOUR OWN RISK! And if you have no idea what I was talking about, just compile the source. ;)

---

### Post by Perpetual on 2008-03-15
Thanks for the howto hyperair.  Just a note

```
sudo apt-get install build-essentials dpkg-dev fakeroot
```

Should be build-essential without the 's'.

---

### Post by SomeGuyDude on 2008-03-15
Well I've spent the last half hour installing about five ******* billion dependencies. Still can't get it compiled. I'll try the full how-to next after I get a shower.

---

### Post by hyperair on 2008-03-15
They're not for the every day user to do. If you're not sure, best you don't try. An easier way to get a deb:
```

./configure
make
sudo checkinstall

```

But before that you must make sure you have checkinstall installed on your system. ```
sudo apt-get install checkinstall
```

This method is easier and faster to do, but doesn't automatically set up dependencies for the resulting deb. As such this is probably better for only personal use.

---

### Post by vexorian on 2008-03-15
So, they now want us to be required to use MONO to play multimedia, insanity on the raise lately.

---

### Post by FuturePilot on 2008-03-15
gah! Almost
```
Trying patch debian/patches/01_gst-inspect.patch at level 1 ... 0 ... success.
Trying patch debian/patches/02_pkgconfig.patch at level 1 ... 0 ... 2 ... failure.
make: *** [debian/stamp-patched] Error 1

```
Any ideas?

---

### Post by Mazza558 on 2008-03-15
Wow, I'm amazed people are having so much trouble with this...

I just followed this guide:

[http://banshee-project.org/OnePointEx/TrunkOnUbuntu]("http://banshee-project.org/OnePointEx/TrunkOnUbuntu")

followed by this:

[http://banshee-project.org/OnePointEx/BuildingAndRunning]("http://banshee-project.org/OnePointEx/BuildingAndRunning")

(See the "Building" section)

---

### Post by bobbocanfly on 2008-03-15
> **Perpetual said:**
> Thanks for the mention of the new Banshee Alpha.  Looking forward to trying it out later today.

I do hope though that it works better with my ipod.  Specifically, when I delete files from my ipod in Banshee it does not actually free the space on the ipod.  The tracks are no longer accessible but the free space on the ipod does not change.  I have read others have this issue but have never really dug deep into a fix.

Regardless, I really like banshee so am excited about a new version!

AS this is a preview release a lot of stuff isnt working, including most hardware oriented stuff. CDs wont play so i doubt it will work with your iPod.

---

### Post by igknighted on 2008-03-15
> **vexorian said:**
> So, they now want us to be required to use MONO to play multimedia, insanity on the raise lately.

Banshee is and always has been a media player built on Mono/C#, and is hardly anything new to the linux multimedia world.  If you don't like that, don't use it.  It's not default or anything.  I use it because I think it is the best music player available for Gnome and could care less what language it is programmed in, but no one is forcing you to use it.

---

### Post by bongo on 2008-03-15
I'm getting this error when typing dpkg-buildpackage -rfakeroot...
Any takers?
Thanks!!!
```
make[1]: Entering directory `/home/max/src/banshee/banshee-1-0.98.1'
make[1]: Leaving directory `/home/max/src/banshee/banshee-1-0.98.1'
rm -f debian/stamp-makefile-build
rm -f debian/stamp-autotools-files
test -d . && cd . && \
          rm -f intltool-extract intltool-merge intltool-update po/.intltool-merge-cache; \
          if test -d doc; then find doc -name '*.omf.out' -exec rm -f \{\} \; ; fi; \
          if test -d help; then find help -name '*.omf.out' -exec rm -f \{\} \; ; fi
rm -f debian/cdbs-install-list debian/cdbs-package-list
rm -rf /home/max/src/banshee/banshee-1-0.98.1/.wapi
rm -f build/mcs-test-79698.exe
dpkg-source: building banshee in banshee_0.98.1~hyperbuntu0.tar.gz
dpkg-source: building banshee in banshee_0.98.1~hyperbuntu0.dsc
test -x debian/rules
mkdir -p "."
/usr/bin/make -f debian/rules reverse-config
make[1]: Entering directory `/home/max/src/banshee/banshee-1-0.98.1'
for i in ./config.guess ./config.sub  ; do \
                if test -e $i.cdbs-orig ; then \
                        mv $i.cdbs-orig $i ; \
                fi ; \
        done
make[1]: Leaving directory `/home/max/src/banshee/banshee-1-0.98.1'
if [ "debian/stamp-patched" = "reverse-patches" ]; then rm -f debian/stamp-patched; fi
patches: debian/patches/01_gst-inspect.patch debian/patches/02_pkgconfig.patch debian/patches/03_fix_2.18_multimedia_keys.patch debian/patch$
Trying patch debian/patches/01_gst-inspect.patch at level 1 ... 0 ... success.
Trying patch debian/patches/02_pkgconfig.patch at level 1 ... 0 ... 2 ... failure.

```

---

### Post by Perpetual on 2008-03-15
> **bobbocanfly said:**
> AS this is a preview release a lot of stuff isnt working, including most hardware oriented stuff. CDs wont play so i doubt it will work with your iPod.

Thanks for the heads-up.  Haven't had time yet to test things.

---

### Post by FuturePilot on 2008-03-15
> **bongo said:**
> I'm getting this error when typing dpkg-buildpackage -rfakeroot...
Any takers?
Thanks!!!
```
make[1]: Entering directory `/home/max/src/banshee/banshee-1-0.98.1'
make[1]: Leaving directory `/home/max/src/banshee/banshee-1-0.98.1'
rm -f debian/stamp-makefile-build
rm -f debian/stamp-autotools-files
test -d . && cd . && \
          rm -f intltool-extract intltool-merge intltool-update po/.intltool-merge-cache; \
          if test -d doc; then find doc -name '*.omf.out' -exec rm -f \{\} \; ; fi; \
          if test -d help; then find help -name '*.omf.out' -exec rm -f \{\} \; ; fi
rm -f debian/cdbs-install-list debian/cdbs-package-list
rm -rf /home/max/src/banshee/banshee-1-0.98.1/.wapi
rm -f build/mcs-test-79698.exe
dpkg-source: building banshee in banshee_0.98.1~hyperbuntu0.tar.gz
dpkg-source: building banshee in banshee_0.98.1~hyperbuntu0.dsc
test -x debian/rules
mkdir -p "."
/usr/bin/make -f debian/rules reverse-config
make[1]: Entering directory `/home/max/src/banshee/banshee-1-0.98.1'
for i in ./config.guess ./config.sub  ; do \
                if test -e $i.cdbs-orig ; then \
                        mv $i.cdbs-orig $i ; \
                fi ; \
        done
make[1]: Leaving directory `/home/max/src/banshee/banshee-1-0.98.1'
if [ "debian/stamp-patched" = "reverse-patches" ]; then rm -f debian/stamp-patched; fi
patches: debian/patches/01_gst-inspect.patch debian/patches/02_pkgconfig.patch debian/patches/03_fix_2.18_multimedia_keys.patch debian/patch$
Trying patch debian/patches/01_gst-inspect.patch at level 1 ... 0 ... success.
Trying patch debian/patches/02_pkgconfig.patch at level 1 ... 0 ... 2 ... failure.

```
Oh good, I thought maybe it was just me. A few posts back I posted that same error. Hopefully someone knows something.

---

### Post by hyperair on 2008-03-15
> **FuturePilot said:**
> gah! Almost
```
Trying patch debian/patches/01_gst-inspect.patch at level 1 ... 0 ... success.
Trying patch debian/patches/02_pkgconfig.patch at level 1 ... 0 ... 2 ... failure.
make: *** [debian/stamp-patched] Error 1

```
Any ideas?

Oh I'm so sorry! I forgot to mention that you must empty out the directory debian/patches. Delete everything in that folder. 

EDIT: I've edited the howto a little: look at step 11 onwards.

---

### Post by FuturePilot on 2008-03-16
Thanks hyperair :)
I'm so close 
```
checking for NDESK_DBUS... configure: error: Package requirements (ndesk-dbus-1.0 >= 0.5                ndesk-dbus-glib-1.0 >= 0.3) were not met:

Requested 'ndesk-dbus-1.0 >= 0.5' but version of NDesk.DBus is 0.4.2
You may find new versions of NDesk.DBus at http://www.ndesk.org/DBusSharp

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NDESK_DBUS_CFLAGS
and NDESK_DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** [config.status] Error 1

```
Is there a way to make it use 0.4.2 instead?

---

### Post by kindofabuzz on 2008-03-16
when i do: 
./configure --prefix=/usr --disable-docs

starts the configure then i get:

checking for GNOMEVFS... configure: error: Package requirements (gnome-vfs-2.0) were not met:

No package 'gnome-vfs-2.0' found

---

### Post by adityakavoor on 2008-03-16
> **Mazza558 said:**
> Wow, I'm amazed people are having so much trouble with this...

I just followed this guide:

[http://banshee-project.org/OnePointEx/TrunkOnUbuntu]("http://banshee-project.org/OnePointEx/TrunkOnUbuntu")

followed by this:

[http://banshee-project.org/OnePointEx/BuildingAndRunning]("http://banshee-project.org/OnePointEx/BuildingAndRunning")

(See the "Building" section)

Would this work in ubuntu 7.04 ?

---

### Post by hyperair on 2008-03-16
It should work. Speaking of which, those having problems building a Banshee deb, follow instructions from here first:
[http://banshee-project.org/OnePointEx/TrunkOnUbuntu](http://banshee-project.org/OnePointEx/TrunkOnUbuntu)

---

### Post by adityakavoor on 2008-03-16
Do you recommended to add this line in my feisty sources list ??

```

deb http://ppa.launchpad.net/ruben/ubuntu gutsy main

```

---

### Post by hyperair on 2008-03-16
I have no idea really, but it's worth a try. Why don't you just upgrade to Gutsy?

---

### Post by adityakavoor on 2008-03-16
> **hyperair said:**
> I have no idea really, but it's worth a try. 

If it breaks my repository :confused: :confused:

Should I take the risk ?

---

### Post by adityakavoor on 2008-03-16
> Why don't you just upgrade to Gutsy?

My graphics card is blacklisted by compiz in the gutsy version

---

### Post by FuturePilot on 2008-03-16
I'm getting closer ;)
```
dh_install: banshee-daap missing files (debian/tmp/usr/lib/banshee/Banshee.Plugins/Banshee.Plugins.Daap.dll*), aborting
make: *** [binary-install/banshee-daap] Error 1

```
Adding that repo helped with the previous error.

---

### Post by SomeGuyDude on 2008-03-16
GNOME's amaroK killer? I'd say so. This is a gorgeous player.

I'm back on MPD/Sonata just for the battery life and I'm too much of a lazy *** to juggle two players, but I'm definitely loving this thing.

---

### Post by hyperair on 2008-03-16
> **FuturePilot said:**
> I'm getting closer ;)
```
dh_install: banshee-daap missing files (debian/tmp/usr/lib/banshee/Banshee.Plugins/Banshee.Plugins.Daap.dll*), aborting
make: *** [binary-install/banshee-daap] Error 1

```
Adding that repo helped with the previous error.

Could you post the debian/control file as well as each debian/*.install file?

> **SomeGuyDude said:**
> GNOME's amaroK killer? I'd say so. This is a gorgeous player.

I'm back on MPD/Sonata just for the battery life and I'm too much of a lazy *** to juggle two players, but I'm definitely loving this thing.
Yeah I'm finally not using Amarok. =D

---

### Post by Lord Illidan on 2008-03-16
I've tried it on Arch Linux...

Finally, they implemented the one thing I had been waiting for ever since I started using Banshee (and the one thing that drove me back to Amarok all the time)

I am of course, referring to the Artist/Album browser.

However, it seems rather buggy. No doubt this is due to the alpha release, and I should probably update my svn sources.

It rocks, enough said. I think this might throw me off Amarok.

---

### Post by bongo on 2008-03-16
I got it to work by downloading the source file and not doing your method with debian patches:
Downloaded the sourcefile from [http://banshee-project.org/files/banshee/banshee-1-0.98.1.tar.gz](http://banshee-project.org/files/banshee/banshee-1-0.98.1.tar.gz) and unpacked it in ~/install then...
```
./configure
make
``` (got error about not finding NDesk.Dbus)
so I typed:
```
cd /usr/local/lib/mono/

sudo ln -s /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/ ndesk-dbus-1.0

```

then I made the following:
```
make && sudo make install
sudo checkinstall
sudo make uninstall
sudo dpkg -i banshee-1_0.98.1-1_i386.deb
```

I got errors when not typing sudo install with checkinstall, do you always have to do that?
Eitherway, works fine now with that method, somewhat unorthodox though :)

Works fine except search for genres doesn't work...

---

### Post by DDuong on 2008-03-16
Awesome!  I will try this out instead of Amarok.

---

### Post by corney91 on 2008-03-16
I tracked down and compiled both [ndesk-dbus]("http://www.ndesk.org/DBusSharp") and [mono addins]("http://www.mono-project.com/Mono.Addins") and have got up to the 'make'. But this outputs:```
Compiling Banshee.Core.dll...
error CS0006: cannot find metadata file `/usr/local/lib/mono/mono-addins/Mono.Addins.dll'
error CS0006: cannot find metadata file `/usr/local/lib/mono/ndesk-dbus-1.0/NDesk.DBus.dll'
Compilation failed: 2 error(s), 0 warnings
make[4]: *** [../../../bin/Banshee.Core.dll] Error 1
make[4]: Leaving directory `/home/dan/Desktop/banshee-1-0.98.1/src/Core/Banshee.Core'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dan/Desktop/banshee-1-0.98.1/src/Core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dan/Desktop/banshee-1-0.98.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dan/Desktop/banshee-1-0.98.1'
make: *** [all] Error 2

```
1. Why is it using .dlls? Isn't that a windows extension?
2. Anyone know how to solve this?
Thanks in advance.

---

### Post by bongo on 2008-03-16
> **corney91 said:**
> I 
[/CODE]
1. Why is it using .dlls? Isn't that a windows extension?
2. Anyone know how to solve this?
Thanks in advance.
1. It is using mono, ie C# in other words its keeping that "syntax" (making exe files and dll files) but it is still "native", check this for more info: [http://en.wikipedia.org/wiki/Mono_%28software%29](http://en.wikipedia.org/wiki/Mono_%28software%29)

2. See my post above, make a symlink and it should work.

Good luck!

---

### Post by corney91 on 2008-03-16
Thanks for the reply,
I'd already done that and it still doesn't work:(
There's another NDesk.DBus.dll in /usr/lib/cli/ndesk-dbus-1.0/. Would that work instead?
Also for the other error (error CS0006: cannot find metadata file `/usr/local/lib/mono/mono-addins/Mono.Addins.dll) there's a Mono.Addins.dll in /usr/lib/f-spot/. Do I need to symlink that as well?
Thanks.

---

### Post by Mohammed Abbas on 2008-03-16
Hey guys !
I get this whenever I try to compile the package

```

Compiling Banshee.Services.dll...
./Banshee.Sources/DatabaseSource.cs(72,38): error CS0183: The given expression is always of the provided (`Hyena.Data.IFilterable') type
Compilation failed: 1 error(s), 0 warnings
make[4]: *** [../../../bin/Banshee.Services.dll] Error 1
make[4]: Leaving directory `/home/mohammed/banshee-1-0.98.1/src/Core/Banshee.Services'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/mohammed/banshee-1-0.98.1/src/Core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mohammed/banshee-1-0.98.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mohammed/banshee-1-0.98.1'
make: *** [all] Error 2


```


Is there anything I can do to get this to work after installing dozens of dependencies ?

---

### Post by hyperair on 2008-03-16
I'm sorry but at this point I'm rather baffled, as I think your libndesk-dbus packages aren't the same as the one found in Ubuntu Hardy. =\

---

### Post by FuturePilot on 2008-03-16
> **Mohammed Abbas said:**
> Hey guys !
I get this whenever I try to compile the package

```

Compiling Banshee.Services.dll...
./Banshee.Sources/DatabaseSource.cs(72,38): error CS0183: The given expression is always of the provided (`Hyena.Data.IFilterable') type
Compilation failed: 1 error(s), 0 warnings
make[4]: *** [../../../bin/Banshee.Services.dll] Error 1
make[4]: Leaving directory `/home/mohammed/banshee-1-0.98.1/src/Core/Banshee.Services'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/mohammed/banshee-1-0.98.1/src/Core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mohammed/banshee-1-0.98.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mohammed/banshee-1-0.98.1'
make: *** [all] Error 2


```


Is there anything I can do to get this to work after installing dozens of dependencies ?
Make sure you add that repo and update all the available mono packages. I got that error and upgrading the mono package fixed it. But now I'm stuck at another error. :p

---

### Post by hyperair on 2008-03-16
@FuturePilot: If you're referring to the banshee-daap error, please list all your debian/*.install files. I only had banshee.install and monodoc-banshee-manuall.install files. Also please post your debian/control file.

---

### Post by beefcurry on 2008-03-16
Awesome, it just keeps improving..

---

### Post by FuturePilot on 2008-03-16
> **hyperair said:**
> @FuturePilot: If you're referring to the banshee-daap error, please list all your debian/*.install files. I only had banshee.install and monodoc-banshee-manuall.install files. Also please post your debian/control file.
```
$ ls debian/*.install
debian/banshee-daap.install  debian/banshee.install

```
```
$ cat debian/control 
Source: banshee
Section: sound
Priority: optional
Maintainer: Sebastian Dröge <slomo@debian.org>
Build-Depends: debhelper (>= 5), cdbs, cli-common-dev (>= 0.4.4), mono-gmcs (>= 1.1.10) | c-sharp-2.0-compiler, libmono-dev (>= 1.1.10), libgtk2.0-cil (>= 2.8.0), libglib2.0-cil (>= 2.8.0), libgnome2.0-cil (>= 2.8.0), libgconf2.0-cil (>= 2.8.0), libglade2.0-cil (>= 2.8.0), libipod-cil (>= 0.6.3), libipodui-cil (>= 0.6.3), libnjb-cil (>= 0.3.0), libsqlite3-dev (>= 3.2), libmono-sqlite2.0-cil, gstreamer0.10-tools, gstreamer0.10-plugins-base-apps, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-gnomevfs, libgstreamer0.10-dev (>= 0.10.3), libgstreamer-plugins-base0.10-dev (>= 0.10.3), libglib2.0-dev, libgnome2-dev, libgnomeui-dev, libgconf2-dev, gconf2, libgtk2.0-dev (>= 2.8), libgnomevfs2-dev, libgnome-desktop-dev, libdbus-1-dev (>= 0.90), libdbus-glib-1-dev (>= 0.70), libnautilus-burn-dev (>= 2.12.0), libmusicbrainz4-dev (>= 2.1.1), libavahi1.0-cil (>= 0.6), pkg-config, intltool (>= 0.35.0), libmono-cairo2.0-cil, libmono2.0-cil, libmono-system-web2.0-cil, libmono-system-data2.0-cil, boo (>= 0.7.6), libtotem-plparser-dev, libndesk-dbus1.0-cil (>= 0.4), libndesk-dbus-glib1.0-cil (>= 0.3), sharutils, libtaglib2.0-cil (>= 2.0.0)
Standards-Version: 3.7.2

Package: banshee
Architecture: any
Depends: ${shlibs:Depends}, ${cli:Depends}, ${misc:Depends}, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good (>= 0.10.6), gstreamer0.10-gnomevfs, gnome-volume-manager, hal
Recommends: gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad
Suggests: banshee-daap
Conflicts: banshee-offical-plugins
Replaces: banshee-offical-plugins
Provides: banshee-offical-plugins
Description: Audio Management and Playback application
 Banshee is an audio management and playback application for the GNOME
 Desktop, allowing users to import audio from CDs, search their library,
 create playlists of selections of their library, sync music to/from iPods,
 and burn selections to a CD.
 .
 http://banshee-project.org

Package: banshee-daap
Architecture: all
Depends: ${shlibs:Depends}, ${cli:Depends}, ${misc:Depends}, banshee (>= ${source:Version}), banshee (<< ${source:Version}.1~), avahi-daemon
Replaces: banshee (<< 0.10.5)
Description: Audio Management and Playback application (DAAP sharing plugin)
 Banshee is an audio management and playback application for the GNOME
 Desktop, allowing users to import audio from CDs, search their library,
 create playlists of selections of their library, sync music to/from iPods,
 and burn selections to a CD.
 .
 http://banshee-project.org
 .
 This package contains the DAAP (iTunes) sharing plugin for accessing and
 creating DAAP shares from your library.

```
Thanks for your help hyperair ;)

---

### Post by Mohammed Abbas on 2008-03-16
thank you guys ! I installed the .deb package and it's now working perfectly ! :D

---

### Post by gfg on 2008-03-16
Would anyone be able to make a 64bit hardy .deb? It would be greatly appreciated!

---

### Post by Polygon on 2008-03-16
I have the same issue as futurepilot, and same output from ls and cat as him as well

---

### Post by adamc83 on 2008-03-16
I've got a hardy version up in my ppa:
[https://launchpad.net/~adam-caldwell/+archive](https://launchpad.net/~adam-caldwell/+archive)

Has both 32 and 64-bit versions. Works fine for me on 64-bit.

---

### Post by hyperair on 2008-03-16
Remove debian/banshee-daap.install, and remove its corresponding entry from debian/control, i.e. remove this portion:
```
Package: banshee-daap
Architecture: all
Depends: ${shlibs:Depends}, ${cli:Depends}, ${misc:Depends}, banshee (>= ${source:Version}), banshee (<< ${source:Version}.1~), avahi-daemon
Replaces: banshee (<< 0.10.5)
Description: Audio Management and Playback application (DAAP sharing plugin)
 Banshee is an audio management and playback application for the GNOME
 Desktop, allowing users to import audio from CDs, search their library,
 create playlists of selections of their library, sync music to/from iPods,
 and burn selections to a CD.
 .
 http://banshee-project.org
 .
 This package contains the DAAP (iTunes) sharing plugin for accessing and
 creating DAAP shares from your library.
```\

@adamc83: :mad: now you say! After we've all gone through the trouble of compiling debs!

---

### Post by adamc83 on 2008-03-16
I just finished it this morning, didnt realize there was already a forum thread with people trying to get it to compile... I'm new to packaging, but as far as I can tell it should work fine for anyone using hardy.

---

### Post by FuturePilot on 2008-03-16
Doh ](*,)
```
dh_install -pbanshee  
cp: cannot stat `./debian/tmp/usr/bin': No such file or directory
dh_install: command returned error code 256
make: *** [binary-install/banshee] Error 1

```
That directory is listed in debian/banshee.install though :-k

---

### Post by justinclark on 2008-03-16
Sorry for sounding a little out of the loop (Im not very advanced) but have we found a way to install and use this on 7.10?  I would like to use this so any help would be great. Thanks

---

### Post by FuturePilot on 2008-03-16
Haha! I've got it! :D
I had to remove everything from debian/banshee.install :confused:

Anyways here it is for 7.10
[banshee_0.98.1~hyperbuntu0_i386.deb]("http://www.mediafire.com/?8otw94zloz2")

You'll need to add this repo for some of the newer mono packages
```
deb http://ppa.launchpad.net/ruben/ubuntu gutsy main
```

Special thanks to hyperair for helping me out ;)

---

### Post by gfg on 2008-03-16
> **adamc83 said:**
> I've got a hardy version up in my ppa:
[https://launchpad.net/~adam-caldwell/+archive](https://launchpad.net/~adam-caldwell/+archive)

Has both 32 and 64-bit versions. Works fine for me on 64-bit.

Worked great. Thanks alot!

---

### Post by justinclark on 2008-03-16
Im sorry, can someone give me the idiots guide to installing this?  I dont know how to add repos and when I download that .deb I get that error.  Help?!:confused:

---

### Post by FuturePilot on 2008-03-16
In a terminal
```
gksudo gedit /etc/apt/sources.list
```
add this to the bottom of the file
```
deb http://ppa.launchpad.net/ruben/ubuntu gutsy main
```
Save it, and close Gedit. Then run this to update the apt database.
```
sudo apt-get update
```
Then double click the .deb.

---

### Post by justinclark on 2008-03-16
You Ubuntu so therefore you are! Lol Thank you mucho!

---

### Post by FuturePilot on 2008-03-16
No problem ;)

---

### Post by Polygon on 2008-03-16
thanks futurepilot, that worked for me as well

only problem is that the traybar icon is missing and the program seems to crash randomly, but whatever :D

---

### Post by gubemton on 2008-03-16
I got horrible dependancy problems after updating mono using the ppa on gutsy.The deb works fine on hardy with me though.

---

### Post by tretle on 2008-03-17
> **adamc83 said:**
> I've got a hardy version up in my ppa:
[https://launchpad.net/~adam-caldwell/+archive](https://launchpad.net/~adam-caldwell/+archive)

Has both 32 and 64-bit versions. Works fine for me on 64-bit.

It looks alright but I cant seem to get banshee to add music to the music library though. Using your hardy 64bit version.

---

### Post by tbob on 2008-03-17
[solved]

---

### Post by nicky.7 on 2008-03-19
i just installed banshee-1 from your repo and the songs doesn't start to play.. do u have an idea??

---

### Post by hyperair on 2008-03-20
Does anyone here get sound distortion when playing songs? It can't be GStreamer's fault, which Banshee uses, because Totem doesn't produce the same sound distortion.

---

### Post by BradwJensen on 2008-03-20
> **adamc83 said:**
> I've got a hardy version up in my ppa:
[https://launchpad.net/~adam-caldwell/+archive]("https://launchpad.net/%7Eadam-caldwell/+archive")

Has both 32 and 64-bit versions. Works fine for me on 64-bit.

Woo-hoo!
Thank you for this! :)

---

### Post by igknighted on 2008-03-20
> **nicky.7 said:**
> i just installed banshee-1 from your repo and the songs doesn't start to play.. do u have an idea??

If you try to play a song that you don't have the proper codecs installed for (at least with the older banshee), it will do exactly what you describe.  Install the proper codecs, or else every time you get to a song   that it can't play you will have to close and re-open the program.

---

### Post by hyperair on 2008-03-20
I believe argument about Microsoft and Mono does stray from the original topic. More on topic: does anyone get any sound distortion when playing songs in Banshee? Specifically users of Ubuntu Hardy.

---

### Post by drascus on 2008-03-20
Wow that does look really nice I am waiting for the first user release of Songbird to come out personally. I think browsing the web for media is a cool concept.

---

### Post by Lord Illidan on 2008-03-20
I felt the discussion was getting way too off topic. I opened another thread for people who want to discuss [Novell, Microsoft and their patent issues]("http://ubuntuforums.org/showthread.php?t=730344"). Let's keep this thread about Banshee, please.

---

### Post by BradwJensen on 2008-03-21
> **hyperair said:**
> I believe argument about Microsoft and Mono does stray from the original topic. More on topic: does anyone get any sound distortion when playing songs in Banshee? Specifically users of Ubuntu Hardy.

When playing in the new Alpha of banshee I do..  Also, in the alpha I can't get the Meta data editor to open without banshee crashing.

---

### Post by hyperair on 2008-03-21
Glad to hear I'm not the only one.

---

### Post by BradwJensen on 2008-03-21
> **hyperair said:**
> Glad to hear I'm not the only one.

ha, but I am sure we're both not glad to hear the crappy sound quality :P

---

### Post by hyperair on 2008-03-22
I've found a way to fix this. Open your equalizer. Reduce the Pre-amp until you no longer here any distortion. =D

---

### Post by rye_ on 2008-03-22
rhythmbox ftw!

---

### Post by BradwJensen on 2008-03-22
> **hyperair said:**
> I've found a way to fix this. Open your equalizer. Reduce the Pre-amp until you no longer here any distortion. =D

Hm..  I might try that, but i already tried to just turn off the whole equalizer with the checkbox and it did not really make a difference..  I have some nice tower speakers hooked up here though, so maybe it's more noticable for me?

Mine also makes horrible static-ish sounds in parts (like when you change a radio station in the car and it makes that cut out sound.. yuck), when it plays fine in 0.13.2

---

### Post by BradwJensen on 2008-03-22
> **rye_ said:**
> rhythmbox ftw!

I'm not against it, but I really wish it had built in CD ripping to FLAC like Banshee does (not having to use code lines or an outside program like sound juicer).  Plus it still does not show my cover.jpg files as album art

:P

I do however like it's scan for missing files at startup
Oh, and it actually sorts my double disc CDs by the correct disc, then track number. :) (banshee doesn't)

---

### Post by Lord Illidan on 2008-03-24
I've got a wierd bug. Selecting Add to Playlist freezes banshee for me..

---

### Post by banjobacon on 2008-03-24
> **BradwJensen said:**
> I'm not against it, but I really wish it had built in CD ripping to FLAC like Banshee does (not having to use code lines or an outside program like sound juicer).

Edit > Preferences > Music. There's a setting for your preferred format. You can set it to flac with hardly any effort at all. I guess this setting isn't clearly labeled (the word "rip" appears nowhere on the screen).

---

### Post by amazingtaters on 2008-03-24
The queing is the best thing for me. I really love it because I can thow a few tracks in order and study for a while. Once the final for Banshee 1.0 comes out I will be infinitely happy.

---

### Post by Major_Kong on 2008-03-26
Is a 7.10 64-bit package avaliable ?

---

### Post by psychicdragon on 2008-03-27
Here's a quick and dirty i386 package of alpha2.

[http://www.mediafire.com/?jdviy3wo0mt]("http://www.mediafire.com/?jdviy3wo0mt")

EDIT: Works for me in hardy, no idea if gutsy meets the depends.

---

### Post by Bastanteroma on 2008-03-27
That package installed on an up-to-date Hardy, but it seems to be missing things like 'Banshee.Core,1.0' and 'taglib-sharp', and it won't scan any files.

It's better than I've managed - I can't get past the ./configure step.

---

### Post by psychicdragon on 2008-03-27
Yeah, the dependecies are crap. My bad. Make sure you have all the packages listed on the release page and it will work, otherwise it won't.

[http://banshee-project.org/Releases/0.98.1]("http://banshee-project.org/Releases/0.98.1")

---

### Post by Mazza558 on 2008-03-27
Wow, video playback?!

---

### Post by Bastanteroma on 2008-03-27
Installling taglib sharp fixed things. Should have tried that...

---

### Post by hyperair on 2008-03-27
Huh, there's an Alpha 2?!

Either way I'm in the process of building a deb with the correct dependencies. =)

Here it is: [http://www.mediafire.com/download.php?9bhdg3uxbzg](http://www.mediafire.com/download.php?9bhdg3uxbzg)

For those who have already downloaded, installed, and got everything working using the deb from psychicdragon, don't bother getting this one. The only difference is the dependencies.

---

### Post by zeltak on 2008-03-27
Hi

I am using gutsy 64bit but i cant get past the gstreamer >10.3 error in the .configure part. can any one help?


Zeltak

---

### Post by hyperair on 2008-03-27
Use this command:
```
sudo apt-get build-dep banshee
```

---

### Post by zeltak on 2008-03-27
hi

Thx for the answer

i get this error when i run the build command

sudo apt-get build-dep banshee

E: Build-Depends dependency for banshee cannot be satisfied because no available versions of package libipod-cil can satisfy version requirements

installed libipod-cil but still get the same message. it seems like the config file wants a very new version of gstreamer:

checking for GNOMEVFS... yes
checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.3
                gstreamer-base-0.10 >= 0.10.3
                gstreamer-plugins-base-0.10 >= 0.10.3
                gstreamer-controller-0.10 >= 0.10.3
                gstreamer-dataprotocol-0.10 >= 0.10.3) were not met:

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found


any more ideas? (perhaps someone has a 64 bit gutsy deb... ;-))

thx in advance

Zeltak

---

### Post by hyperair on 2008-03-27
Could you post your sources.list file?

---

### Post by zeltak on 2008-03-27
here it is:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main

deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main

deb [http://www.estamos.de/download/apt](http://www.estamos.de/download/apt) stable main

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main

deb [http://sshmenu.sourceforge.net/debian](http://sshmenu.sourceforge.net/debian) stable contrib

deb [http://ppa.launchpad.net/conduit/ubuntu](http://ppa.launchpad.net/conduit/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/conduit/ubuntu](http://ppa.launchpad.net/conduit/ubuntu) gutsy main

deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy exaile

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

deb [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

#Added by prevu
deb file:/var/cache/prevu/gutsy-debs ./

deb [http://ppa.launchpad.net/hanno-stock/ubuntu](http://ppa.launchpad.net/hanno-stock/ubuntu) gutsy main

deb [http://ppa.launchpad.net/timlinux/ubuntu](http://ppa.launchpad.net/timlinux/ubuntu) gutsy main

deb [http://ppa.launchpad.net/ruben/ubuntu](http://ppa.launchpad.net/ruben/ubuntu) gutsy main

---

### Post by MaX on 2008-03-27
> **hyperair said:**
> Huh, there's an Alpha 2?!

Either way I'm in the process of building a deb with the correct dependencies. =)

Here it is: [http://www.mediafire.com/download.php?9bhdg3uxbzg](http://www.mediafire.com/download.php?9bhdg3uxbzg)

For those who have already downloaded, installed, and got everything working using the deb from psychicdragon, don't bother getting this one. The only difference is the dependencies.

Hey!
Saw your post on the Banshee blog and got here... But the mediafire link doesn't work. Please up another. or mail it to me. PM Me for address.

---

### Post by hyperair on 2008-03-27
Try this: [http://www.mediafire.com/?9bhdg3uxbzg](http://www.mediafire.com/?9bhdg3uxbzg)

---

### Post by MaX on 2008-03-27
It's the same link... it still doesn't work
I'm probably on Telia Broad Band and they have been locked out by a stupid American company and mediafire is probably using that.
Could you upload to Rapidshare? Or attach it here (?)

---

### Post by Tomosaur on 2008-03-27
Anybody got a .deb for Gutsy? I'd love to give this a go but I don't have the time to chase up all the dependencies to build from source.

---

### Post by denisesballs on 2008-03-27
> **hyperair said:**
> Huh, there's an Alpha 2?!

Either way I'm in the process of building a deb with the correct dependencies. =)

Here it is: [http://www.mediafire.com/download.php?9bhdg3uxbzg](http://www.mediafire.com/download.php?9bhdg3uxbzg)

For those who have already downloaded, installed, and got everything working using the deb from psychicdragon, don't bother getting this one. The only difference is the dependencies.

When trying your package I get:

```
jesse@e6300:~/systems$ sudo dpkg -i banshee-1_0.98.2~hyperbuntu0_i386.deb 
Selecting previously deselected package banshee-1.
(Reading database ... 149164 files and directories currently installed.)
Unpacking banshee-1 (from banshee-1_0.98.2~hyperbuntu0_i386.deb) ...
dpkg: dependency problems prevent configuration of banshee-1:
 banshee-1 depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.6.1-1ubuntu10.
 banshee-1 depends on libcairo2 (>= 1.5.14); however:
  Version of libcairo2 on system is 1.4.10-1ubuntu4.4.
 banshee-1 depends on libgconf2.0-cil (>= 2.20.0); however:
  Version of libgconf2.0-cil on system is 2.16.0-7ubuntu1.
 banshee-1 depends on libglade2.0-cil (>= 2.12.0); however:
  Version of libglade2.0-cil on system is 2.10.2-1ubuntu2.
 banshee-1 depends on libglib2.0-0 (>= 2.16.0); however:
  Version of libglib2.0-0 on system is 2.14.1-1ubuntu1.
 banshee-1 depends on libglib2.0-cil (>= 2.12.0); however:
  Version of libglib2.0-cil on system is 2.10.2-1ubuntu2.
 banshee-1 depends on libgnome2.0-cil (>= 2.20.0); however:
  Version of libgnome2.0-cil on system is 2.16.0-7ubuntu1.
 banshee-1 depends on libgtk2.0-cil (>= 2.12.0); however:
  Version of libgtk2.0-cil on system is 2.10.2-1ubuntu2.
 banshee-1 depends on libpango1.0-0 (>= 1.20.0); however:
  Version of libpango1.0-0 on system is 1.18.3-0ubuntu1.
dpkg: error processing banshee-1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 banshee-1
```

I did apt-get build-dep banshee. I can build it from source okay, but video playback doesn't work.

---

### Post by amic on 2008-03-28
I'm running 7.10 and believe I have all the repositories needed. Here's my problem: everything is fine until "make." I get the following error(s):

```
Compiling Banshee.Widgets.dll...
./Banshee.Widgets/VolumeButton.cs(55,17): error CS0612: `Gtk.Tooltips' is obsolete
Compilation failed: 1 error(s), 0 warnings
make[4]: *** [../../../bin/Banshee.Widgets.dll] Error 1
make[4]: Leaving directory `/home/david/Documents/banshee-1-0.98.1/src/Core/Banshee.Widgets'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/Documents/banshee-1-0.98.1/src/Core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/david/Documents/banshee-1-0.98.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/Documents/banshee-1-0.98.1'
make: *** [all] Error 2
```

Any ideas would be greatly appreciated.

P.S. I'm running 64bit

---

### Post by mondoUNC on 2008-03-28
I installed the Alpha using one of the debs that I thought was for Gutsy but now mono is gone and I can't reinstall one of my favorite dvd ripper, HandbrakeGTK (it needs mono).

I posted a [thread]("http://ubuntuforums.org/showthread.php?t=737031") elsewhere but no reply. Can anyone help?

---

### Post by drsaamah on 2008-03-29
Alright question.  I got so lost in trying to get the alpha version of banshee on my computer that I gave up on compiling and used one of the deb's above.  Problem is I got a little too excited and installed the 0.98.1 deb.  So now i want to install the 0.98.2 deb and it wont let me until i get rid of the prior one.  How do I do this?  'sudo apt-get remove banshee-1' says it cant find package banshee-1 (probably since it wasn't installed through repos?).
Help?  Thanks in advance!

---

### Post by hyperair on 2008-03-29
All the packages I have produced and adam caldwell have produced are for **Ubuntu Hardy**.

---

### Post by drsaamah on 2008-03-29
right thats not the issue.  they work just fine on gutsy as well.  my issue is how do i get rid of it??  i installed the deb for 0.98.1 and it worked great, thank you very much.  but i meant to install 0.98.2, and now I cannot until i uninstall 0.98.1.  How would you go about doing this?

---

### Post by drsaamah on 2008-03-29
Never mind, i just did it through synaptic.

---

### Post by drsaamah on 2008-03-29
Okay the 0.98.2 deb didn't work so I went back to compiling from source, but this time used the whole like svn co thing (i guess its called a 'trunk' or something... ?_?) and it worked fine.  The only weird thing is I checked the "About" and it says the version is 0.98.3 even though banshee's website even says there have only been 2 alpha versions so far.  If the "About" screen is right you guys might want to upgrade.

---

### Post by mkantor1 on 2008-03-29
The  trunk is where all of the bleeding edge development happens.  It is constantly evolving, and there might be unstable or untested code in there.  The Alpha 2 release has probably been cleaned up a little and had any half-implemented features removed or disabled.  They probably bump the trunk version when any changes are made after the Alpha release, so what you're using is more like a transient banshee somewhere between alpha 2 and the upcoming "official" alpha 3.

---

### Post by hyperair on 2008-03-29
I'm proud to announce the birth of the Banshee team, started by Jorge O. Castro, Sebastian Dröge, Adam Caldwell and I. We'll be bringing Banshee 1.0 Alpha packages to you (only Ubuntu Hardy so far), as well as other future upstream versions. 

Here's the link: [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive)

EDIT: Ubuntu Gutsy support is now ONLINE!

EDIT: I've backported the required packages from Hardy to Gutsy, and would like feedback as to whether it works. Anyone?

---

### Post by zombiepig on 2008-03-30
I've just installed alpha-2 from the launchpad ppa, on hardy x64. However, I can't add any items to the library - everytime I try banshee sits with  "Importing Media - scanning for media" bar bouncing back and forth, and no hdd activity or anything.
Any ideas?

---

### Post by hyperair on 2008-03-30
Could you try adding one file at a time? Instead of import local folder, import local file. See if that works. Scanning for library items doesn't use much HDD I'm not mistaken, because it just gets a file listing. It generally happens when your library is really huge and it needs to build a huge list of files before it can begin importing.

---

### Post by dalonso on 2008-03-30
This is happening to me too. No warnings at all, neither by running it in the cli.

I'm not getting banshee to import my music.

---

### Post by hyperair on 2008-03-30
Like I said in my previous post: it could be taking time to scan a huge collection of music. Could you try using a smaller folder to import or import a single file just to see if it works? If it doesn't at least we know there's a problem and can fix it.

---

### Post by mkantor1 on 2008-03-30
> **hyperair said:**
> 
I've backported the required packages from Hardy to Gutsy, and would like feedback as to whether it works. Anyone?

Works like a charm for me, thanks!

---

### Post by dalonso on 2008-03-30
> **hyperair said:**
> Like I said in my previous post: it could be taking time to scan a huge collection of music. Could you try using a smaller folder to import or import a single file just to see if it works? If it doesn't at least we know there's a problem and can fix it.

No, it's not a problem of time. The importing action actually ends without adding anything to the library.

---

### Post by banjobacon on 2008-03-30
So, will version 1.0 be out in time for Hardy? If not, which version will be available in the Hardy repository?

---

### Post by hyperair on 2008-03-30
Those with problems can you state your distro and architecture? At least I know which is the faulty build.

@banjobacon: I don't think it'll be out in time, but never mind, the PPA will be updated regularly with the latest build.

---

### Post by BradwJensen on 2008-03-30
> **hyperair said:**
> Those with problems can you state your distro and architecture? At least I know which is the faulty build.

@banjobacon: I don't think it'll be out in time, but never mind, the PPA will be updated regularly with the latest build.

I am running the latest Hardy Heron, 32 bit.

I also can't add music to my database using any method (with alpha 1 or alpha 2).

Also, I am not sure if this is a bug or not implemented yet, but I can't open the meta data editor in either of the alphas without Banshee crashing.

Thank you for the Repo thing! :)

---

### Post by hyperair on 2008-03-30
Could you post the command line output when you try? Start banshee from the terminal and then attempt to add your music collection.

---

### Post by MaX on 2008-03-30
Adding Movies doesn't work at all for me using the PPA version of Banshee...

---

### Post by BradwJensen on 2008-03-30
> **hyperair said:**
> Could you post the command line output when you try? Start banshee from the terminal and then attempt to add your music collection.

Saddly, when I started Banshee in terminal then tried adding my Music Collection (even just one file at a time), It shows nothing more in the Terminal..  Nothing more than that it started Banshee.

I let it do the "Scanning for media" for almost a whole hour, and nothing changed.  It still had the bar under "scanning for media" going back and fourth.  That is what it has always done with both the alphas (for me).

Also, if i click the stop button, then the pop up asks me if i want to stop "importing" and i click stop - It still shows the "Scanning for media" with the bar going back and fourth.

---

### Post by zombiepig on 2008-03-30
> **BradwJensen said:**
> Saddly, when I started Banshee in terminal then tried adding my Music Collection (even just one file at a time), It shows nothing more in the Terminal..  Nothing more than that it started Banshee.

I let it do the "Scanning for media" for almost a whole hour, and nothing changed.  It still had the bar under "scanning for media" going back and fourth.  That is what it has always done with both the alphas (for me).

Also, if i click the stop button, then the pop up asks me if i want to stop "importing" and i click stop - It still shows the "Scanning for media" with the bar going back and fourth.

Exactly the same behaviour here. I'll add that I've got barely any music on my laptop (about 20 albums or so), so it's not a problem related to large collections.

---

### Post by fluffman86 on 2008-03-30
has anyone gotten the iPod integration to work yet?  I've been wanting something like this for the whole last year that I've been using linux...so much so that I simply haven't used my 1.25 year old iPod for the last year, hehe.  :P

I've installed banshee 0.98 alpha 2 from the banshee ppa repositories, and I've compiled from svn the subprojects (libipoddevice, ipod-sharp, and njb-sharp) with no luck.  When I plug in my iPod, it's recognized by Ubuntu, pops up on the desktop, Rhthmbox pops up and I can listen to the music on it, and yet nothing happens in Banshee.  I've tried restarting banshee and plugging/unplugging my iPod in every possible configuration.

Thanks in advance for any help!

edit: it would help if I RTFA.  From [http://banshee-project.org/Releases/0.98.2]("http://banshee-project.org/Releases/0.98.2"):
>  Currently Missing Features

    * This release does not contain any hardware support
          o No audio CD support
          o No CD burning
         ***_ o No iPod support_***
          o No USB Mass Storage support
          o No MTP device support 


yeah...

---

### Post by zombiepig on 2008-03-31
Scanning works for me with the latest version! Thanks!

---

### Post by BradwJensen on 2008-03-31
> **zombiepig said:**
> Scanning works for me with the latest version! Thanks!

Lucky you..

I just got the Alpha 3 update and it still doesn't work for me.. I try to open even just one file and it does nothing but 'scans for media'.. forever.

---

### Post by hyperair on 2008-04-01
There's actually been some discussion about this issue in #banshee on irc.gnome.org. It'd be nice if you could join and help us test.

---

### Post by zombiepig on 2008-04-10
Looks like alpha 3 is out now, with support for audio cds, usb mass storage players and lots of bug fixes. I'm hoping it hits the ppa soon! :)

---

### Post by SomeGuyDude on 2008-04-10
If it worked with Conky, I'd be using it now.

---

### Post by hyperair on 2008-04-11
I've just uploaded to the PPA. If all goes well, please remove your "banshee" package and install "banshee-1" from the PPA. Apparently both Banshee 1.0 Alpha and the stable should be able to co-exist peacefully, so I'll be removing "banshee" shortly.

---

### Post by zombiepig on 2008-04-11
ok, removing and installing banshee-1 did the trick. Thanks!!

---

### Post by luck555 on 2008-04-14
hi i'm traing to install banshe alpha 3 but when i use make i get somthing like this and don't know how to fix this:

Compiling MusicBrainz.dll...
./MusicBrainz/MusicBrainzObject.cs(368,25): error CS0117: `System.Net.HttpWebRequest' does not contain a definition for `CachePolicy'
./MusicBrainz/MusicBrainzObject.cs(394,61): error CS0117: `System.Net.HttpWebResponse' does not contain a definition for `IsFromCache'
Compilation failed: 2 error(s), 0 warnings
make[4]: *** [../../../bin/MusicBrainz.dll] B&#322;&#261;d 1
make[4]: Opuszczenie katalogu `/home/lucas/Desktop/banshee-1-0.98.3/src/Libraries/MusicBrainz'
make[3]: *** [all-recursive] B&#322;&#261;d 1
make[3]: Opuszczenie katalogu `/home/lucas/Desktop/banshee-1-0.98.3/src/Libraries'
make[2]: *** [all-recursive] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/lucas/Desktop/banshee-1-0.98.3/src'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/lucas/Desktop/banshee-1-0.98.3'
make: *** [all] B&#322;&#261;d 2

---

### Post by hyperair on 2008-04-14
You are advised to use the PPA here: [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive)

If you still wish to compile from source, you should still add the PPA, then run "sudo apt-get build-dep banshee-1" before compiling. This error happens presumably because you're an Ubuntu Gutsy user, and hence don't have the required dependencies. The dependencies are provided by the PPA.

---

### Post by SomeGuyDude on 2008-04-14
I get a GStreamer problem when running it in Hardy. Starting to piss me off because neither that nor Exaile will play.

---

### Post by Vaelrith on 2008-04-15
Any idea when it will be officially released?  I really like it, especially the video playback.  However, it would be nice if you could make the video play fulls creen.

---

### Post by banjobacon on 2008-04-17
Pardon me if this has already addressed in this thread, but is there no plugins package in the PPA? I'm specifically wondering what happened to DAAP support.

---

### Post by hyperair on 2008-04-17
@SomeGuyDude: GStreamer problems usually arise when you haven't installed the required plugins. What file is it you are trying to play? If you are trying to play mp3s, then install ubuntu-restricted-extras.

@Vaelrith: I have no idea when it will be officially released. I'll bring up the issue about fullscreen video in #banshee.

@banjobacon: They have been merged into the actual banshee-1 package itself. However, DAAP support is still unstable and is disabled in banshee-1. However, when 1.0 is finally released, all features which were previously in Banshee 0.13.x and more will be included. There is no plan to separate the plugins from the actual package as of now.

---

### Post by charding on 2008-04-19
In your instructions on this page, you should say that you need to run:

sudo apt-get update

after you add the PAA to /etc/apt/sources.list

---

### Post by hyperair on 2008-04-19
@charding: It's PPA not PAA. But thanks for telling me anyway. I've edited the PPA description.

---

### Post by Mazza558 on 2008-04-21
Speaking of the actual app itself, I lOVE IT! I've been using the latest alpha and it's shaping up to be the best gnome music player. Will there be any additional features that aren't in the Alpha?

---

### Post by amazingtaters on 2008-04-21
> **Mazza558 said:**
> Speaking of the actual app itself, I lOVE IT! I've been using the latest alpha and it's shaping up to be the best gnome music player. Will there be any additional features that aren't in the Alpha?

Well for one iPod support will be added back in. The plugins that users of the old Banshee have come to love (or hate) will be making a return as well, but aren't in Trunk as of now.

---

### Post by zachtib on 2008-04-21
Just installed from the Banshee-Team PPA...

Wow...

I love the Artist/Album browser, and also that it has video support

---

### Post by geoken on 2008-04-21
Can someone answer a couple question about the new USB support? I'd love to try it but won't get a chance for a few days.

Basically, what I wanted to know was whether it allows you to a) transfer a bunch of songs by transfering a playlist which references those songs b) specify which folder the songs will be going in to (ie. my mp3 player needs files dropped into it's /Music directory).

---

### Post by vietcaterpillar on 2008-04-22
Ah folks, I'm getting a strange dependency error i can't seem to find with i do the preliminary ./configure

"gdk-x11-2.0"

> 
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for GDK_X11... configure: error: Package requirements (gdk-x11-2.0 >= 2.8) were not met:

No package 'gdk-x11-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDK_X11_CFLAGS
and GDK_X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


anybody got any suggestions?

---

### Post by hyperair on 2008-04-22
@vietcaterpillar: Try using the [Banshee-Team PPA](http://edge.launchpad.net/~banshee-team/+archive).

If you still want to compile from source at that point, you can add the PPA entries to your sources.list, then run ```
sudo apt-get build-dep banshee-1
```This will install the required build-dependencies for Banshee 1.0, after which you will be able to compile the program just fine.

---

### Post by banjobacon on 2008-04-22
I want to like Banshee, as it has a pretty good interface. However, it always has some really annoying flaws. 

The latest version doesn't automatically detect my MP3 player. Ubuntu detects it just fine, so I'm guessing it's not a HAL issue, but a Banshee one.

Once I get Banshee to recognize my MP3 player (by manually inserting a file onto the player), I can't drag items from the artist or album list. That's kind of lame. 

Banshee still doesn't know how to deal with various artist albums. 

Banshee still doesn't automatically detect new songs in my ~/Music/ folder. 

I consider submitting bugs, but I don't bother because Rhythmbox does all these things pretty well already.

---

### Post by KhaosMind on 2008-04-22
great app now it index the files cool, but even if it is better than rythmbox still do the same, waste a lot of space. common they got a whole bar just for 5 buttons, just like ryhmbox who has an entire bar only for the song time. i dont own an ipod and i never did but i used itunes on windows because is the best app to navigate through music(great use of space, but could be better) and sadly it still holds that position. gmusicbrowser is almost what i want but lacks good features

---

### Post by adityakavoor on 2008-04-29
please link me to installation of new banshee on hardy

---

### Post by hyperair on 2008-04-29
[http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive)

---

### Post by graabein on 2008-04-29
> **zachtib said:**
> Just installed from the Banshee-Team PPA...

Wow...

I love the Artist/Album browser, and also that it has video support

Can you post a screenshot of the artist/album browser? 

I use **Quod Libet** mostly because of its [album view]("http://www.williambrownstreet.net/wordpress/wp-content/wbs_quodlibet6.png").

---

### Post by chri2020 on 2008-04-30
hi,
i just installed this from the deb at [http://www.mediafire.com/?q2obdmyyykj](http://www.mediafire.com/?q2obdmyyykj)
and it worked perfectly,
i was just wondering if it still possible to run the old version, without unistalling this version, and how to do it.
thanks

---

### Post by kk0sse54 on 2008-04-30
I love the look and some of the features but sadly i find it very laggy and constantly crashes on me. Maybe it's because i have such a big library or it's still a buggy program but i use Exaile now and it works like a charm.

---

### Post by Vaelrith on 2008-04-30
> **C!oud said:**
> I love the look and some of the features but sadly i find it very laggy and constantly crashes on me. Maybe it's because i have such a big library or it's still a buggy program but i use Exaile now and it works like a charm.

It is alpha after all.

---

### Post by hyperair on 2008-04-30
> **chri2020 said:**
> hi,
i just installed this from the deb at [http://www.mediafire.com/?q2obdmyyykj](http://www.mediafire.com/?q2obdmyyykj)
and it worked perfectly,
i was just wondering if it still possible to run the old version, without unistalling this version, and how to do it.
thanks

That deb is outdated. Please head over to [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive). Use that repository to install "banshee-1". That package will be able to co-exist with Banshee 0.13.x. However, you must make sure that you downgrade "banshee" back to 0.13.x first, or they will conflict.

---

### Post by adityakavoor on 2008-04-30
I installed banshee-1 alpha and now bith the old banshee and the new one also aren't working.

```
aditya@ubuntu:~$ banshee-1

(Nereid:7442): Gtk-WARNING **: Theme directory 96x96/action of theme HumanAzul2 has no size field

[Info  09:05:44.547] All services are started 2.090787s
** (Nereid:7442): DEBUG: bp_stop: setting state to GST_STATE_NULL
[Error 09:05:48.840] GStreamer resource error: NotFound

(Nereid:7442): GStreamer-CRITICAL **: gst_element_query_duration: assertion `GST_IS_ELEMENT (element)' failed
** (Nereid:7442): DEBUG: bp_stop: setting state to GST_STATE_NULL
[Error 09:05:55.621] GStreamer resource error: NotFound

(Nereid:7442): GStreamer-CRITICAL **: gst_element_query_duration: assertion `GST_IS_ELEMENT (element)' failed
** (Nereid:7442): DEBUG: bp_stop: setting state to GST_STATE_NULL
[Error 09:05:57.187] GStreamer resource error: NotFound

(Nereid:7442): GStreamer-CRITICAL **: gst_element_query_duration: assertion `GST_IS_ELEMENT (element)' failed
** (Nereid:7442): DEBUG: bp_stop: setting state to GST_STATE_NULL
[Error 09:06:00.926] GStreamer resource error: NotFound

(Nereid:7442): GStreamer-CRITICAL **: gst_element_query_duration: assertion `GST_IS_ELEMENT (element)' failed
** (Nereid:7442): DEBUG: bp_stop: setting state to GST_STATE_NULL
[Error 09:06:03.501] GStreamer resource error: NotFound

(Nereid:7442): GStreamer-CRITICAL **: gst_element_query_duration: assertion `GST_IS_ELEMENT (element)' failed
** (Nereid:7442): DEBUG: bp_stop: setting state to GST_STATE_NULL
[Error 09:06:05.757] GStreamer resource error: NotFound

```

Please help. I am using hardy. Ubuntu restricted extras installed

---

### Post by hyperair on 2008-04-30
If the old one isn't working any more then you must have installed the package from the wrong source. Please use [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive).

About your library errors, delete all your files from your library in Banshee 1.0 and then reimport it.

---

### Post by adityakavoor on 2008-04-30
Thanks for  the superfast reply. will try it now

---

### Post by adityakavoor on 2008-04-30
> About your library errors, delete all your files from your library in Banshee 1.0 and then reimport it.

Where will these files be ?

---

### Post by adityakavoor on 2008-04-30
> Where will these files be ?

Sorry for this dumb question.

I reimported library and everything is fine. Thanks

Banshee rocks

---

### Post by chri2020 on 2008-05-02
> **hyperair said:**
> That deb is outdated. Please head over to [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive). Use that repository to install "banshee-1". That package will be able to co-exist with Banshee 0.13.x. However, you must make sure that you downgrade "banshee" back to 0.13.x first, or they will conflict.

thanks, that worked great :)
i love the video library feature,
does anyone know if they will be adding the equivalent to cover art for videos?

---

### Post by hyperair on 2008-05-02
I wasn't aware that videos had cover art in the first place. Perhaps thumbnails. But no, not cover art.

---

### Post by monolux on 2008-05-02
Does it have any advantage in relation to Amarok?
:confused:

---

### Post by hyperair on 2008-05-03
Well a few people have switched from Amarok to Banshee 1.0 so you should really try it yourself and see. For me, what I really like is that my entire collection can be used directly as a playlist so I don't have to refresh the playlist every time I add a new song to the collection. Also, Banshee 1.0 manages its own database using a SQLite backend, while not hogging the CPU like Amarok does with a huge library. On my system, I had to set up Amarok with MySQL in order to have reasonable performance with Amarok and my massive collection (4976 songs). Also Banshee 1.0 supports playing and managing videos in its library.

---

### Post by isaacj87 on 2008-05-06
Apparently the Banshee 1.0 Beta has been release including MTP/iPod support!

Any chances we can see an update to the PPA repo? 

Thanks!

---

### Post by Vaelrith on 2008-05-06
Videos on my iPod... finally...

---

### Post by illu45 on 2008-05-07
The new alpha looks very nice, and the added functionality (play queue!) is awesome. Unfortunately, my entire computer freezes whenever I open the Edit menu. I suppose its possible that I'm missing a dependency...

---

### Post by hyperair on 2008-05-07
Hey hey I have to sleep and attend college you know! They released it at about 5AM my time! Either way it has been uploaded, just wait for it to build.

---

### Post by graabein on 2008-05-07
Dang it, please post some screenshots of the new version for us that don't build from source or wait for it to hit the repo's...

---

### Post by hyperair on 2008-05-07
Screenshots. Not much changed.

EDIT: .. actually there are screenshots here: [http://www.banshee-project.org/Releases/0.99.1](http://www.banshee-project.org/Releases/0.99.1)

---

### Post by pt123 on 2008-05-07
> **isaacj87 said:**
> 
Any chances we can see an update to the PPA repo? 

Thanks!

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

This one currently has Alpha3, so beta should hopefully arrive soon.

---

### Post by hyperair on 2008-05-07
> **pt123 said:**
> [https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

This one currently has Alpha3, so beta should hopefully arrive soon.

Beta 1 has been uploaded two hours back. However, launchpad.net's build system has awesomely put the i386 packages in a queue that will last for another hour before Banshee's turn arrives. So we have packages for amd64 and lpia, but not i386. Pffft.

---

### Post by bobbocanfly on 2008-05-07
Wahey, i386 Hardy build started 5 minutes ago! Wont be long now.

---

### Post by hyperair on 2008-05-07
The Hardy i386 deb is done.

---

### Post by wyth on 2008-05-07
This will be interesting when it's finished.  Right now, it locks up my entire desktop when navigating around the options (I know, it's alpha).

Just curious: In the stable version, the radio section has a tree view.  Personally, I prefer tree view over what Banshee and Rhythmbox offer, and it's one of the reasons I still use Amarok as my main audio player/podcatcher.  I just find the tree view more intuitive and cleaner.  (I'd use Exaile, but it's always been fairly crashtastic for me.)

Since it's clear tree view is included in at least one view of Banshee, is there a way to enable it as the default, through a config file or something?  That would pretty much seal the deal for me, since it's podcast feature now offers almost the same level of fine-grain control as Amarok.  

I'd just prefer a GTK app for all this stuff, but I'm picky about what features I need.

---

### Post by fluffman86 on 2008-05-07
So the new beta (0.99.1) is supposed to work with iPods, but it's not showing up.  I have the plugin enabled in edit > prefs > mange extensions, but still no dice.

Anyone know the official status of iPod support in Banshee?

---

### Post by hyperair on 2008-05-07
Oh crap. My bad. I think I left out a few dependencies... ipod-sharp and podsleuth if I'm not mistaken. Give me some time, I'll try and sort it out before I go to sleep.

---

### Post by monolux on 2008-05-07
> **hyperair said:**
> Well a few people have switched from Amarok to Banshee 1.0 so you should really try it yourself and see. For me, what I really like is that my entire collection can be used directly as a playlist so I don't have to refresh the playlist every time I add a new song to the collection. Also, Banshee 1.0 manages its own database using a SQLite backend, while not hogging the CPU like Amarok does with a huge library. On my system, I had to set up Amarok with MySQL in order to have reasonable performance with Amarok and my massive collection (4976 songs). Also Banshee 1.0 supports playing and managing videos in its library.
Txs for the info all go have a look in the banshee music player! : )

---

### Post by Lem on 2008-05-07
Looking good. Fullscreen crashes out on me as soon as I move the mouse though.

Nice to see the ipod/mtp plugins in there. All we need now is a good radio plugin.

---

### Post by spanella47 on 2008-05-07
installing the new beta is giving me this error: any ideas?

An unhandled exception was thrown: duplicate column name: TitleLowered

  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in /build/buildd/banshee-1-0.99.1/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate () [0x000ae] in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176 
  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1-0.99.1/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.24.17

Assembly Version Information:

System.Transactions (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
gdk-sharp (2.12.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (0.99.1.35408)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
Banshee.Core (0.99.1.35411)
Hyena (0.99.1.35406)
System (2.0.0.0)
Banshee.Services (0.99.1.35412)
Banshee.ThickClient (0.99.1.35415)
Nereid (0.99.1.35416)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-17-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

[/etc/debian_version]
lenny/sid

---

### Post by pt123 on 2008-05-08
The beta is crashing when viewing fullscreen after a few seconds  and move the mouse to a corner. 
```

[Info  18:20:51.587] Running Banshee 0.99.1
[Info  18:20:54.277] All services are started 2.275058s
[Info  18:20:55.305] nereid Client Started

(Nereid:7092): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: libgdk-2.0-0.dll
  at (wrapper managed-to-native) Hyena.Gui.CompositeUtils:gdk_screen_is_composited (intptr)
  at Hyena.Gui.CompositeUtils.IsComposited (Gdk.Screen screen) [0x00000] in /build/buildd/banshee-1-0.99.1/src/Libraries/Hyena.Gui/Hyena.Gui/CompositeUtils.cs:130 
  at Banshee.NowPlaying.OverlayWindow.OnRealized () [0x00000] in /build/buildd/banshee-1-0.99.1/src/Extensions/Banshee.NowPlaying/Banshee.NowPlaying/OverlayWindow.cs:80 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Widget.realized_cb(IntPtr )
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.NowPlaying.FullscreenWindow.ShowControls() in /build/buildd/banshee-1-0.99.1/src/Extensions/Banshee.NowPlaying/Banshee.NowPlaying/FullscreenWindow.cs:line 180
   at Banshee.NowPlaying.FullscreenWindow.OnMotionNotifyEvent(Gdk.EventMotion evnt) in /build/buildd/banshee-1-0.99.1/src/Extensions/Banshee.NowPlaying/Banshee.NowPlaying/FullscreenWindow.cs:line 240
   at Gtk.Widget.motionnotifyevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Widget.motionnotifyevent_cb(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run() in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 114
   at Banshee.Gui.GtkBaseClient.Startup() in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 55
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup) in /build/buildd/banshee-1-0.99.1/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:line 54
   at Banshee.Gui.GtkBaseClient.Entry() in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 50
   at Nereid.Client.Main() in /build/buildd/banshee-1-0.99.1/src/Clients/Nereid/Nereid/Client.cs:line 47

```

---

### Post by hyperair on 2008-05-08
@spannela47: It seems to me that your banshee database is corrutped somehow. Move ~/.config/banshee-1/banshee.db elsewhere, and then try again.

@pt123: Noted. I'm discussing it on #banshee as I post this. It seems that a file "Hyena.Gui.dll.config" is missing. This could cause other bugs as well. Sebastian Dröge is fixing this in svn at the moment.

EDIT: A fix is on the way, please be patient ;)
EDIT 2: I've gotten the fix into the package, now just wait for it to build :)

---

### Post by kpkeerthi on 2008-05-08
:)
I'm happy to know that iPod support has now been added. I'm going to build this from source today (in Archlinux though). When banshee 1.0 final I'll kiss good bye to rhythmbox.

---

### Post by hyperair on 2008-05-08
kpkeerthi: I'd actually encourage you to follow trunk in ArchLinux. Just run "yaourt -S banshee-1-svn" periodically to update =D

---

### Post by kpkeerthi on 2008-05-08
> **hyperair said:**
> kpkeerthi: I'd actually encourage you to follow trunk in ArchLinux. Just run "yaourt -S banshee-1-svn" periodically to update =D
Absolutely. I'm going to download the PKGBUILD so I can compile-install it with the post_install() and pre_remove() fixes you have suggested in [AUR]("http://aur.archlinux.org/packages.php?ID=15961") ;)

---

### Post by fluffman86 on 2008-05-08
> **hyperair said:**
> Oh crap. My bad. I think I left out a few dependencies... ipod-sharp and podsleuth if I'm not mistaken. Give me some time, I'll try and sort it out before I go to sleep.

Thanks!  It was great waking up to find this update ready!

Banshee now recognizes my iPod, and I can manually drag songs onto it.  Next I'm going to try adding video files and subscribing to some video podcasts.  

Now I just have one question remaining: should the iPod do an iTunes-like sync?  According to the [Banshee DAP Guide]("http://banshee-project.org/Guide/DAPs"), the Zen can synchronize.  But I don't have (AFAICT) any sync buttons.  Should I?

---

### Post by hyperair on 2008-05-08
@fluffman86: I have no Ipod so I really don't know. Why don't you drop by #banshee at irc://irc.gnome.org?

---

### Post by s_spiff on 2008-05-08
he means join the irc channel at irce://irc.gnome.org. Its a place where many banshee users will be, and you can interact with them.

---

### Post by spanella47 on 2008-05-08
@Hyperair - if I erase the banshee-1 config folder i get a different error:

```
An unhandled exception was thrown: table CoreTracks has no column
named PrimarySourceID

 at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr
pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000]
 at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader
(CommandBehavior behavior, Boolean want_results, System.Int32&
rows_affected) [0x00000]
 at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000]
 at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute
(Hyena.Data.Sqlite.HyenaSqliteConnection hconnection,
Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in
/build/buildd/banshee-1-0.99.1/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116
Exception has been thrown by the target of an invocation.

 at System.Reflection.MonoMethod.Invoke (System.Object obj,
BindingFlags invokeAttr, System.Reflection.Binder binder,
System.Object[] parameters, System.Globalization.CultureInfo culture)
[0x00000]
 at System.Reflection.MethodBase.Invoke (System.Object obj,
System.Object[] parameters) [0x00000]
 at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate ()
[0x000ae] in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176
 at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in
/build/buildd/banshee-1-0.99.1/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136
Exception has been thrown by the target of an invocation.

 at System.Reflection.MonoCMethod.Invoke (System.Object obj,
BindingFlags invokeAttr, System.Reflection.Binder binder,
System.Object[] parameters, System.Globalization.CultureInfo culture)
[0x00000]
 at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr,
System.Reflection.Binder binder, System.Object[] parameters,
System.Globalization.CultureInfo culture) [0x00000]
 at System.Reflection.ConstructorInfo.Invoke (System.Object[]
parameters) [0x00000]
 at System.Activator.CreateInstance (System.Type type, Boolean
nonPublic) [0x00000]
 at System.Activator.CreateInstance (System.Type type) [0x00000]
 at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in
/build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55
 at Hyena.Gui.CleanRoomStartup.Startup
(Hyena.Gui.StartupInvocationHandler startup) [0x00048] in
/build/buildd/banshee-1-0.99.1/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.24.17

Assembly Version Information:

System.Transactions (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
gdk-sharp (2.12.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (0.99.1.35408)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
Banshee.Core (0.99.1.35411)
Hyena (0.99.1.35406)
System (2.0.0.0)
Banshee.Services (0.99.1.35412)
Banshee.ThickClient (0.99.1.35415)
Nereid (0.99.1.35416)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-17-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

[/etc/debian_version]
lenny/sid
```

---

### Post by fluffman86 on 2008-05-08
> **hyperair said:**
> @fluffman86: I have no Ipod so I really don't know. Why don't you drop by #banshee at irc://irc.gnome.org?

shoot...IRC is blocked at work :(  I'll be on tonight then.

As for subscribing to video podcasts, banshee crashes when I type in the feed ([http://www.podshow.com/feeds/hd.xml](http://www.podshow.com/feeds/hd.xml)) for GeekBrief.tv.

Running from terminal, I get the following error:
```
[Info  10:30:45.094] Running Banshee 0.99.1
[Info  10:30:48.382] All services are started 2.838866s
[Info  10:30:50.471] nereid Client Started
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.InvalidCastException: Cannot cast from source type to destination type.
  at Hyena.Data.Sqlite.SqliteModelProvider`1[Migo.Syndication.Feed].Save (Migo.Syndication.Feed ) [0x00000] in /build/buildd/banshee-1-0.99.1/src/Libraries/Hyena/Hyena.Data.Sqlite/SqliteModelProvider.cs:265 
  at Migo.Syndication.Feed.Save () [0x00000] in /build/buildd/banshee-1-0.99.1/src/Libraries/Migo/Migo/Migo.Syndication/Feed.cs:1090 
  at Migo.Syndication.FeedsManager.CreateFeed (System.String url) [0x0003f] in /build/buildd/banshee-1-0.99.1/src/Libraries/Migo/Migo/Migo.Syndication/FeedsManager.cs:230 
  at Banshee.Podcasting.PodcastCore.SubscribeToPodcast (System.Uri uri, FeedAutoDownload syncPreference) [0x0000d] in /build/buildd/banshee-1-0.99.1/src/Extensions/Banshee.Podcasting/Banshee.Podcasting/PodcastCore.cs:349 
  at Banshee.Podcasting.PodcastCore.RunSubscribeDialog () [0x00084] in /build/buildd/banshee-1-0.99.1/src/Extensions/Banshee.Podcasting/Banshee.Podcasting/PodcastCore_Interface.cs:207 
  at Banshee.Podcasting.PodcastCore.OnPodcastAdd (System.Object sender, System.EventArgs e) [0x00023] in /build/buildd/banshee-1-0.99.1/src/Extensions/Banshee.Podcasting/Banshee.Podcasting/PodcastCore_Interface.cs:316 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run() in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 114
   at Banshee.Gui.GtkBaseClient.Startup() in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 55
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup) in /build/buildd/banshee-1-0.99.1/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:line 54
   at Banshee.Gui.GtkBaseClient.Entry() in /build/buildd/banshee-1-0.99.1/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 50
   at Nereid.Client.Main() in /build/buildd/banshee-1-0.99.1/src/Clients/Nereid/Nereid/Client.cs:line 47
Real-time signal 1
```

Edit: same thing happens with audio podcasts, as well.

---

### Post by hyperair on 2008-05-08
@spanella47: Did you remove ~/.config/banshee as well?

---

### Post by spanella47 on 2008-05-08
@hyperair: No, didnt want to get rid of my old banshee.db if i could do it another way

wrote the banshee mailing list and turned out running src/nuke-core-tables worked. I'd been compiling from source before the PPA existed so the upgrade wasn't upgrading my db smoothly for whatever reason.

Everythings fine now though, thanks

---

### Post by pt123 on 2008-05-09
> **hyperair said:**
> 
@pt123: Noted. I'm discussing it on #banshee as I post this. It seems that a file "Hyena.Gui.dll.config" is missing. This could cause other bugs as well. Sebastian Dröge is fixing this in svn at the moment.

Thanks the latest build in the repos is not crashing. 

There is problem with playing a video in full screen and then exiting the full screen, Banshee disappears from the windows list thus it is not picked up in Compiz's expo and scale plugins.  Ends up becoming a phantom window.

---

### Post by hyperair on 2008-05-09
@pt123: What version are you running?

---

### Post by pt123 on 2008-05-09
0.99.1-3ubuntu1~hardy3
similar thing was happening on the build before.

---

### Post by hyperair on 2008-05-10
Could you post the command line output when that happens? Just run "banshee-1" in a terminal. Then play a video, fullscreen, and de-fullscreen it.

---

### Post by pt123 on 2008-05-10
> **hyperair said:**
> Could you post the command line output when that happens? Just run "banshee-1" in a terminal. Then play a video, fullscreen, and de-fullscreen it.
```

[Info  19:11:16.141] Running Banshee 0.99.1
[Info  19:11:28.964] All services are started 8.95355s
[Info  19:11:30.225] nereid Client Started

(Nereid:6503): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by hyperair on 2008-05-10
Weird. O_o. Report a bug in bugzilla.gnome.org?

---

### Post by linuxgeoff on 2008-05-10
I have been using banshee for 6 months on xubuntu gibbon running on an old laptop (300MHz, 128MB).  The laptop accesses network server (all wired and fixed IP) with about 20000 tracks on it.
It worked OK but sometimes took an age to respond, and I was eagerly awaiting banshee 1 which looked like it would perform much better.  

banshee 1 installed from [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive)

Horror of horrors, it is MUCH worse.  Between every track played,  there is now a 60 sec pause while the CPU and disk are thrashed. When playing a track, the playback often pauses while the CPU is off doing something other than playing music.  It is basically unuseable, which is a real shame as it looks like it's way better in terms of features.

I was surprised as I was expecting Banshee 1 to be a more efficient program, not less.  Is this a temporary shortcoming, or will banshee 1's performance shortfalls persist?  

Anyone got any ideas why my performance is so bad (i'm guessing that it's paging in parts of the DB and this what takes all the time betewwn tracks - maybe?).  More importantly, any ideas how I might get acceptable performance?  Otherwise, I'll stick to the old version

thanks,  Geoff

---

### Post by zachtib on 2008-05-10
For me, Banshee 1.0 works great.  The UI is much improved as well.  I never used Banshee because of the lack of a browser, but 1.0 fixes this.  Also, I like the Video support, I can add and tag all my tv shows and movies

---

### Post by Bo Rosén on 2008-05-11
With Banshee 0.99.1 from the repo, I noticed it won't import videos correctly unless they are in a subfolder to where I keep the music.

/home/brosen/Media/Musicvideo/ 
gets oddly truncated to
/home/brosen/Media/Music\ideo  Yes, the 'v' gets dropped

If I move the folder to /home/brosen/Media/Music it's all fine.

The Media folder is on a separate drive if that matters.

---

### Post by hyperair on 2008-05-11
> **Bo Rosén said:**
> With Banshee 0.99.1 from the repo, I noticed it won't import videos correctly unless they are in a subfolder to where I keep the music.

/home/brosen/Media/Musicvideo/ 
gets oddly truncated to
/home/brosen/Media/Music\ideo  Yes, the 'v' gets dropped

If I move the folder to /home/brosen/Media/Music it's all fine.

The Media folder is on a separate drive if that matters.

Sounds like a bug. Please file a bug report [here](http://bugzilla.gnome.org). Thank you.

---

### Post by Bo Rosén on 2008-05-11
Done.
[http://bugzilla.gnome.org/show_bug.cgi?id=532596](http://bugzilla.gnome.org/show_bug.cgi?id=532596)

---

### Post by Bo Rosén on 2008-05-11
And, while I'm playing with Banshee :)
Is there supposed to be Internet Radio and support for Podcasts in 0.99.1? 
Just asking 'cause I'm not seeing it.

---

### Post by hyperair on 2008-05-11
> **Bo Rosén said:**
> And, while I'm playing with Banshee :)
Is there supposed to be Internet Radio and support for Podcasts in 0.99.1? 
Just asking 'cause I'm not seeing it.

No to both.

---

### Post by Bo Rosén on 2008-05-11
Good! Nothing wrong here then. :)

---

### Post by PRGUY85 on 2008-05-13
I just installed the deb package for Banshee Beta.  It is a nice media player yet I don't see much difference in functionality between this and Rhythmbox.  Also, Banshee is using up to 90mb RAM even when minimized...hehe my Ubuntu sessions are rapidly catching up to XP in RAM usage with Firefox and Banshee using 180-200 mb RAM...

---

### Post by hyperair on 2008-05-13
One thing I really like in Banshee that no other player (except maybe Amarok) can compare is the searching capability. Banshee supports searching by tags, and boolean operators are also supported in searching. I don't see such things available in Rhythmbox.

---

### Post by PRGUY85 on 2008-05-13
How much RAM is Banshee using on your setup?

---

### Post by hyperair on 2008-05-13
6.19% of my total, and my total is 1280MiB so it'd be 79.232MiB I guess. Either way you shouldn't get uncomfortable about your RAM usage unless you notice your Swap usage going up. When that begins rising, your system slows down. Otherwise it's fine.

---

### Post by PRGUY85 on 2008-05-13
Its just some Winblows players use 20-30 so I found this surprising on Ubuntu.

---

### Post by hyperair on 2008-05-13
It's a given that if you add more features to a program, it's going to take more memory. Most "Winblows playesr" don't have as many features as Banshee does. One which comes close, but doesn't quite reach it, is Windows Media Player, but that drinks CPU and RAM like nobody's business.

---

### Post by PRGUY85 on 2008-05-13
> **hyperair said:**
> It's a given that if you add more features to a program, it's going to take more memory. Most "Winblows playesr" don't have as many features as Banshee does. One which comes close, but doesn't quite reach it, is Windows Media Player, but that drinks CPU and RAM like nobody's business.


Not to start a flame war here or anything for I believe Ubuntu is a better OS that Windows XP, Media Jukebox and Windows Media Player never reach 50-60 MB RAM.  Media Jukebox has the same functionality Banshee/Rhythmbox has using 30-40 mb RAM at the most (minimized 20 MB RAM).  Sure I could go to Windows and use those but I prefer my Ubuntu setup and just find it strange that Linux cannot create a media player that rivals some of XP's players with equal functionality and similar levels of RAM usage.  Right now, Banshee is reaching iTunes RAM Usage at times, which is a travesty.

---

### Post by zekopeko on 2008-05-13
does Banshee Beta 1 have iPod support? i read somewhere that there was a packaging problem in the PPA. is that fixed?

---

### Post by PRGUY85 on 2008-05-13
> **zekopeko said:**
> does Banshee Beta 1 have iPod support? i read somewhere that there was a packaging problem in the PPA. is that fixed?

Yes, it does.

---

### Post by zekopeko on 2008-05-13
just plugged my ipod 5.5gen and i don't see it in banshee. rythmbox see's and auto opens.

any tips?

---

### Post by hyperair on 2008-05-13
> **PRGUY85 said:**
> Not to start a flame war here or anything for I believe Ubuntu is a better OS that Windows XP, Media Jukebox and Windows Media Player never reach 50-60 MB RAM.  Media Jukebox has the same functionality Banshee/Rhythmbox has using 30-40 mb RAM at the most (minimized 20 MB RAM).  Sure I could go to Windows and use those but I prefer my Ubuntu setup and just find it strange that Linux cannot create a media player that rivals some of XP's players with equal functionality and similar levels of RAM usage.  Right now, Banshee is reaching iTunes RAM Usage at times, which is a travesty.

I think you haven't looked deep enough at the features Banshee is providing. I don't see Podcast support in WMP or Media Jukebox. I can't say anything about Rhythmbox because I used it 2 years ago, and ditched it. I also don't see an extensive search feature implemented in WMP or Media Jukebox, nor do I see last.fm support in WMP. What about bookmarks, plugin support and Boo scripting support? I don't see that in other players either.

---

### Post by hyperair on 2008-05-13
> **zekopeko said:**
> just plugged my ipod 5.5gen and i don't see it in banshee. rythmbox see's and auto opens.

any tips?

Install podsleuth. Then restart Banshee, and try again.

---

### Post by PRGUY85 on 2008-05-13
Point taken, Hyperair :)

Yet, I do wish it went down a bit hehe.

---

### Post by hyperair on 2008-05-13
> **PRGUY85 said:**
> Point taken, Hyperair :)

Yet, I do wish it went down a bit hehe.

That is true. I think there are plans ahead to reduce the CPU and memory footprint of Banshee when it approaches 1.0. Right now we're still in Beta 1.

---

### Post by zekopeko on 2008-05-13
banshee freezes without any useful error from the terminal when i plug my ipod.
on a side note: how do you stop rhythmbox from autostarting on ipod connect?

Scratch that. It works now. Probably conflicting ipod library that's been removed now.

Scratch scratch that. It doesn't work. it's sees the ipod but it isn't seeing the song and videos and playlists.

---

### Post by hyperair on 2008-05-13
Check System->Preferences->Removable Drives and Media.

---

### Post by zekopeko on 2008-05-13
it looks like there is a problem with podsleuth.

[http://bugzilla.gnome.org/show_bug.cgi?id=531927](http://bugzilla.gnome.org/show_bug.cgi?id=531927)

any chance for an updated podsleuth for hardy?

---

### Post by hyperair on 2008-05-13
Hardy has 0.6.1, and that is the latest version of Podsleuth available here: [http://www.banshee-project.org/files/podsleuth](http://www.banshee-project.org/files/podsleuth)

Also the latest version found in Debian is 0.6.1: [http://packages.debian.org/sid/sound/podsleuth](http://packages.debian.org/sid/sound/podsleuth)

If a new tarball is released, tell me, I'll package it in the banshee-team PPA.

---

### Post by PRGUY85 on 2008-05-15
Its weird but whenever I open Banshee Beta followed by Firefox 3.0 beta 5, I lose all my bookmarks and saved cookies... If I turn it off, its all back to normal.

---

### Post by hyperair on 2008-05-15
That certainly is the weirdest thing I've heard.

---

### Post by linuxgeoff on 2008-05-18
> **hyperair said:**
>  I think there are plans ahead to reduce the CPU and memory footprint of Banshee when it approaches 1.0. Right now we're still in Beta 1.

Can anyone expand upon this?  Right now I've given up using Banshee 0.99 and am using 0.13, as the memory / CPU usage of 0.99 kills me (using an old laptop as a "sound-bridge").

Is it possible to build a version with just the music playing options (i.e. no video, no burn, no ipod, etc.)?  and will this likely get me around the memory problem?  or should I just wait till 1.0?

Any views?  Ta.  very much.  geoff

---

### Post by hyperair on 2008-05-18
> **linuxgeoff said:**
> Can anyone expand upon this?  Right now I've given up using Banshee 0.99 and am using 0.13, as the memory / CPU usage of 0.99 kills me (using an old laptop as a "sound-bridge").

Is it possible to build a version with just the music playing options (i.e. no video, no burn, no ipod, etc.)?  and will this likely get me around the memory problem?  or should I just wait till 1.0?

Any views?  Ta.  very much.  geoff

It's possible, but it will be of no use. The modules that aren't needed can be disabled to conserve memory. From what I have heard, it's the library database backend that needs tweaking to make it use less CPU/RAM. However, it's not been done yet, but will be done when 1.0 is finally released.

---

### Post by PRGUY85 on 2008-05-20
Is there a way for Banshee to stay connected to my Library folder and autoupdate? I see no option to select a Library folder, just Import option which I don't think stays updated with changes on the folder.

---

### Post by hyperair on 2008-05-20
> **PRGUY85 said:**
> Is there a way for Banshee to stay connected to my Library folder and autoupdate? I see no option to select a Library folder, just Import option which I don't think stays updated with changes on the folder.

No, not yet. But I think we can expect to see this feature in 1.0 when it's finally released.

---

### Post by isaacj87 on 2008-05-20
@hyperair:

I'm sorry if you already answered this question, but is the user supposed to be able to synchronize with their iPods? (I can't) Or is iPod capability limited at the moment?

---

### Post by hyperair on 2008-05-20
> **isaacj87 said:**
> @hyperair:

I'm sorry if you already answered this question, but is the user supposed to be able to synchronize with their iPods? (I can't) Or is iPod capability limited at the moment?

Please read the below quoted posts.

> **zekopeko said:**
> it looks like there is a problem with podsleuth.

[http://bugzilla.gnome.org/show_bug.cgi?id=531927](http://bugzilla.gnome.org/show_bug.cgi?id=531927)

any chance for an updated podsleuth for hardy?

> **hyperair said:**
> Hardy has 0.6.1, and that is the latest version of Podsleuth available here: [http://www.banshee-project.org/files/podsleuth](http://www.banshee-project.org/files/podsleuth)

Also the latest version found in Debian is 0.6.1: [http://packages.debian.org/sid/sound/podsleuth](http://packages.debian.org/sid/sound/podsleuth)

If a new tarball is released, tell me, I'll package it in the banshee-team PPA.

---

### Post by isaacj87 on 2008-05-20
Yeah, I saw those. Strange thing is, I don't have any trouble seeing my iPod in Banshee-1?! I can even add playlists to iPod, but I can't save my changes to the iPod...

I read through the bug report...seemed like users were having trouble getting Banshee-1 to display their pods. But I'm just going to assume my trouble is also podsleuth related (even though I have a bit more success), I'll be looking forward to a fix I guess! :)

---

### Post by hyperair on 2008-05-20
> **isaacj87 said:**
> Yeah, I saw those. Strange thing is, I don't have any trouble seeing my iPod in Banshee-1?! I can even add playlists to iPod, but I can't save my changes to the iPod...

I read through the bug report...seemed like users were having trouble getting Banshee-1 to display their pods. But I'm just going to assume my trouble is also podsleuth related (even though I have a bit more success), I'll be looking forward to a fix I guess! :)

Sorry, I don't think your issue is to do with the podsleuth. However, your issue is also a known issue and will probably be fixed by 1.0's release. But as of now, I don't know the cause or any workarounds for this.

---

### Post by pt123 on 2008-05-23
The Beta-2 got released when I updated the PPA source a new package was there. 

But run it gives a Fatal error
```

An unhandled exception was thrown: duplicate column name: ExternalID

  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in /build/buildd/banshee-1-0.99.2/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate () [0x000ae] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176 
  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1-0.99.2/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.24.16

Assembly Version Information:

System.Transactions (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
gdk-sharp (2.12.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (0.99.2.13426)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
Banshee.Core (0.99.2.13429)
Hyena (0.99.2.13425)
System (2.0.0.0)
Banshee.Services (0.99.2.13431)
Banshee.ThickClient (0.99.2.13433)
Nereid (0.99.2.13434)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-16-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

[/etc/debian_version]
lenny/sid




```

---

### Post by isaacj87 on 2008-05-23
> **pt123 said:**
> The Beta-2 got released when I updated the PPA source a new package was there. 

But run it gives a Fatal error
```

An unhandled exception was thrown: duplicate column name: ExternalID

  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in /build/buildd/banshee-1-0.99.2/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate () [0x000ae] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176 
  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1-0.99.2/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1-0.99.2/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.24.16

Assembly Version Information:

System.Transactions (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
gdk-sharp (2.12.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (0.99.2.13426)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
Banshee.Core (0.99.2.13429)
Hyena (0.99.2.13425)
System (2.0.0.0)
Banshee.Services (0.99.2.13431)
Banshee.ThickClient (0.99.2.13433)
Nereid (0.99.2.13434)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-16-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

[/etc/debian_version]
lenny/sid




```

I'm having the same issue.

---

### Post by bobbocanfly on 2008-05-23
Beta 2 working perfectly for me. Good job ~banshee-team!

Edit: Heh, maybe not, locks up when i try to go into the main preferences window

---

### Post by isaacj87 on 2008-05-23
Hmmm...Found a *solution* (worked for me). Just move the dir ~/.config/banshee-1 (or delete it) and then try opening Banshee Beta 2 again.

---

### Post by eatfruit on 2008-05-23
Yeah, I was having same trouble but that worked a treat.  Thanks

---

### Post by hyperair on 2008-05-23
That's a database migration error. Nothing new really. If that happens again you can try running the script at the bottom of this page: [http://svn.gnome.org/viewvc/banshee/trunk/banshee/src/nuke-core-tables?view=markup](http://svn.gnome.org/viewvc/banshee/trunk/banshee/src/nuke-core-tables?view=markup)

Warning: your music library will probably be wiped out.

---

### Post by pt123 on 2008-05-23
I am having trouble with the intereface for the video browser. When you click on a video it plays in the main frame. To get back to the list of videos I can only go by using the sidebar. The video still continues playing (which isn't a bad feature) but there is no way to return back to the video.

---

### Post by hyperair on 2008-05-24
> **pt123 said:**
> I am having trouble with the intereface for the video browser. When you click on a video it plays in the main frame. To get back to the list of videos I can only go by using the sidebar. The video still continues playing (which isn't a bad feature) but there is no way to return back to the video.

Double click on "Now Playing" on the sidebar.

---

### Post by pt123 on 2008-05-24
> **hyperair said:**
> Double click on "Now Playing" on the sidebar.

Thanks is there also anyway to monitor certain folders. So they don't have to be imported every time?

---

### Post by hyperair on 2008-05-24
Not yet. It'll probably be put in before 1.0 is out though.

---

### Post by hotweiss on 2008-05-24
Can someone tell me how to install GnomeVFS, I'm missing this dependency.

---

### Post by hyperair on 2008-05-24
Last I checked, it wasn't a dependency of Banshee.

---

### Post by hotweiss on 2008-05-24
Well I used Synaptic Package Manager to find Gnome VFS, and now I got to this problem:

> checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.3
		gstreamer-base-0.10 >= 0.10.3
		gstreamer-plugins-base-0.10 >= 0.10.3
		gstreamer-controller-0.10 >= 0.10.3
		gstreamer-dataprotocol-0.10 >= 0.10.3) were not met:

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found

---

### Post by hotweiss on 2008-05-24
Nevermind, I got it installed using this site:

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

This is a really nice media player. Would be great if it had Shoutcast built-in.

---

### Post by hyperair on 2008-05-24
If you want to compile from source in the future, use this command with the deb-src line for PPA enabled.
```
sudo apt-get build-dep banshee-1
```

That will satisfy your dependencies.

---

### Post by hotweiss on 2008-05-24
> **hyperair said:**
> If you want to compile from source in the future, use this command with the deb-src line for PPA enabled.
```
sudo apt-get build-dep banshee-1
```

That will satisfy your dependencies.

I just listen to internet radio, so I'll be sticking with BMPx.

---

### Post by DarkOx on 2008-05-24
Weird. I just upgraded to the latest banshee. Podcast support is great, but I don't seem to be able to adjust the artist/album browser up or down any more. Is this a bug? What I really want to see is a list of my albums, which is all scrunched up at the bottom right now. Anyone else have this problem?

---

### Post by tolremeno on 2008-05-24
Does Banshee no longer have daap support? I can't seem to find it.

---

### Post by hyperair on 2008-05-25
> **tolremeno said:**
> Does Banshee no longer have daap support? I can't seem to find it.

DAAP support is disabled for the time being because it is considered unstable. You can compile and enable it using --enable-daap if you wish.

---

### Post by tolremeno on 2008-05-25
Will do. Thanks.

edit: is it still being developed?

---

### Post by hyperair on 2008-05-25
Yes it is. It's 1.0 Beta 2. The "Beta" indicates a state of incompleteness. It will continue to be developed, not to worry. There are plans to continue after 1.0's release too. Banshee is definitely a piece of software that's here to stay.

---

### Post by tolremeno on 2008-05-25
Oh, you misunderstand. I was referring to DAAP support and asking whether it was still being developed as part of the Banshee project.

:-)

---

### Post by hyperair on 2008-05-25
Oh, sorry. The DAAP support is in active development, not to worry.

---

### Post by tolremeno on 2008-05-25
Sweet, thanks.

---

### Post by aerials on 2008-05-25
I just did a fresh Hardy install and tested Banshee 1.0 Beta 2 for a few hours. While I liked the speed and easiness with which it handled my ~8500 songs, I disliked the incapability to handle compilation albums like soundtracks etc. For me, there's no benefit in having an album browser when it lists every soundtrack with multiple artists as single albums by these artists.
The other thing is the handling of album art. The previous versions (0.1x) took the folder.jpg file I placed in every single album folder as cover art, while the new version tries to fetch it from the net (I guess). This might work for roughly 80% of my albums, but all the non mainstream and really rare stuff will never get a cover that way. 
But otherwise, the new interface is really nice, I hope the compilation handling will get implemented soon :) I will investigate further in the artwork thing, but I haven't found a setting to point Banshee to use my folder.jpg files yet...
For now I'm back on Hardy's stock 0.13 Banshee, still getting used to Firefox 3 ;)

---

### Post by jaithehulk on 2008-05-26
hey will this Player sync with my Creative ZEN Vision:M??
I wld luv it if it can do that!!

---

### Post by hyperair on 2008-05-26
I have no idea. Why don't you try and tell us the results? If the Creative ZEN uses the MTP protocol or you can just copy audio files into it manually, then Banshee should be able to sync with it.

---

### Post by Mazza558 on 2008-05-26
Just had an awesome idea... 

What if Miro was merged with Banshee, and Banshee added music stores like Jamendo...

:o

---

### Post by fwre01 on 2008-05-26
The new release of banshee is shaping up to be something special. The new features are looking FANTASTIC! i installed beta 2 yesterday.

i plugged my ipod and didnt see a sync button...has this feature been removed? (i hope not) i cudnt see any mention of it anywhere in the blurb

---

### Post by spanella47 on 2008-05-26
got a problem with videos:
video playback is black until window is moved and is always black in fullscreen

used to have this problem with totem and compiz before, but this has been fixed for quite sometime (possibly a year). Is banshee using the non-default gstreamer video output or something strange like that?

---

### Post by hyperair on 2008-05-27
Nope, Banshee uses the defualt gstreamer video input, specified in gstreamer-properties.

---

### Post by jaithehulk on 2008-05-27
> **jaithehulk said:**
> hey will this Player sync with my Creative ZEN Vision:M??
I wld luv it if it can do that!!
the problem is i dont see any mount or sync button in Banshee..
hence how do i make banshee aware of my player?
are there any plugins available??
I Use GNOMAD2 for my ZEN...which automatically detects MTP devices...

---

### Post by hyperair on 2008-05-27
MTP device huh? Make sure you've got the MTP extension enabled in Banshee, then plug it in. If it doesn't work, then file a bug at bugzilla.gnome.org

---

### Post by graabein on 2008-05-27
I will try it out when it hits [GetDeb]("http://www.getdeb.net") (which appears to be down atm). 

Does anyone know if it is as fast as **Quod Libet**? 

I really like Quod Libet's speed, tag editing (Ex Falso), album view and plugins for downloading cover art etc. **Banshee 1.0** really has to impress for me to drop Quod Libet as my preferred player...

---

### Post by Mazza558 on 2008-05-27
> **graabein said:**
> I will try it out when it hits [GetDeb]("http://www.getdeb.net") (which appears to be down atm)

Works here...

---

### Post by Ub1476 on 2008-05-27
I would like to see Banshee be able to load as a deamon, like MPD, so when I exit whatever I do, it'll still run until I shut the computer off. Love MPD for that. I'm gonna have a hard time switching if such a feature doesn't get implented, cause my main concern (and most others) is to listen to music, everywhere and anytime. Can Banshee do _that_?

---

### Post by hyperair on 2008-05-27
I highly recommend that you do **not** use GetDeb.net's debs in this case. Not that I have anything against it, but if anything breaks, nobody can see the build logs and tell whether it's a packaging error or a Banshee bug, so it's pretty much unsupported. Instead you're recommended to use the APT repository here: [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive) It'll provide for automatic updating within 24 hours of every release.

There is no client/daemon interface for Banshee, but I can't say for sure whether they will or will not have it in the future. You're invited to come to #banshee on irc.gnome.org and ask the developers yourself. 

As for speed, Banshee's pretty fast too, but if you're looking for a lightweight player without any advanced features, such as Quot Libet, then Banshee probably isn't for you. But don't take my word for it, go give it a try!

---

### Post by spanella47 on 2008-05-27
> **hyperair said:**
> Nope, Banshee uses the defualt gstreamer video input, specified in gstreamer-properties.

any ideas why this may be happening then?

---

### Post by cmost on 2008-05-27
> **aerials said:**
> For now I'm back on Hardy's stock 0.13 Banshee, still getting used to Firefox 3 ;)

Why do you simply accept, without question, what's put on your plate?  If you don't like Firefox 3, you're free to remove it and replace it with the more stable Firefox 2.x.  Furthermore, many people have been bellyaching about Pulseaudio...it too, can be similarly removed and replaced by the more tried and tested ALSA.  Geesh!  Sometimes I think "Ubuntu" is an African word that means "too lazy to learn how to configure Debian."

Back on topic, the new Banshee is fabulous.  I am considering switching too it when it goes gold.  I have been using Exaile but I don't like how the latest version fails to remember my Shoutcast streams in the playlist from session to session.

---

### Post by junior aspirin on 2008-06-02
a quick question about ipod support. A relative of mine has a new ipod nano, its working fine with rhythmbox at the moment, but they want to copy videos to it.  Will banshee automatically transcode videos to a smaller filesize/correct format when it copies them over? or is that yet to be implemented. i dont personally have an ipod so am unable to test.

---

### Post by hyperair on 2008-06-02
I don't think video transcoding has been implemented yet. However it should be in 1.0 if I'm not mistaken.

---

### Post by fluffman86 on 2008-06-05
> **hyperair said:**
> I don't think video transcoding has been implemented yet. However it should be in 1.0 if I'm not mistaken.

Wow!  Even iTunes can't do on the fly video encoding.  That'd be pretty amazing.

Junior Aspirin: If you need to convert videos to iPod format now, you can use [MediaCoder](http://mediacoder.sf.net) or [Handbrake](handbrake.m0k.org).  Both have linux clients.

It's been about a year since I've used either (don't really watch many vids on my ipod anymore because it takes so long to rip/convert movies), but last time I found mediacoder to be easier.  It even has a special "one-click" feature to convert to ipod format.  Handbrake worked well, too, and it may have been a little faster, but I'm pretty sure I had to do things from the command line.  Things may have changed though.  YMMV.

Oh, and also, you may want to look up DVD Fab Decrypter.  I use the free version under Wine to rip movies and then DVD Shrink under Wine to shrink them to 4.7 GB and burn them (so I don't scratch my real ones).  Anyhoo, the paid version of DVD Fab will let you rip from DVD straight to iPod format, no intermediary required.

---

### Post by Mr. Picklesworth on 2008-06-05
Yah, Banshee 1 is amazing! Only one flaw I have noticed is that audio management has a silly precedence over video management, which we can see in the global Preferences dialog which has management preferences for audio files. On the other hand, the only way to change video management stuff is in the context menu for the video library!

Not the end of the world, though. If Banshee had the Miro media guide built in there with all the right file handlers, it would replace that program in seconds. Actually, I think I may switch soon anyway, just as soon as BitTorrent feeds work in Banshee. It is rather a shame how bloated Miro the program is, so this is definitely a breath of fresh air after using that thing.

Can Banshee treat a mass storage device, or a networked storage device, with the same joy it gives to media players? Right now I am using my Nokia N810 as a portable media player, but popping it in just mounts the disk and Canola does nothing for it. Connecting via Bluetooth, etc. doesn't do anything either. Makes me sad :(

Can I tell it "this disk = a PMP" and have the appropriate options become available, or am I doomed for now?

By the way, the LastFM stuff is really impressive. If anyone has skipped it just thinking "it's yet another LastFM client", look again! It gives out a list of multiple tracks to choose from for a radio station so you can really quickly browse what's available.

---

### Post by zombiepig on 2008-06-05
> **Mr. Picklesworth said:**
> 

Can Banshee treat a mass storage device, or a networked storage device, with the same joy it gives to media players? Right now I am using my Nokia N810 as a portable media player, but popping it in just mounts the disk and Canola does nothing for it. Connecting via Bluetooth, etc. doesn't do anything either. Makes me sad :(

Can I tell it "this disk = a PMP" and have the appropriate options become available, or am I doomed for now?


You need to create a .is_audio_player file on the disk - see [http://banshee-project.org/Guide/DAPs/MassStorageDevices](http://banshee-project.org/Guide/DAPs/MassStorageDevices) for details

---

### Post by Mr. Picklesworth on 2008-06-05
Great. Thanks, zombiepig!
That automatic audio conversion is pretty cool. Too bad this device supports every format under the sun... no reason to do it - or to download my audio podcasts in Banshee, for that matter ;)
Need synchronized podcast interfaces, now, so I don't end up downloading stuff I've already listened to on another device.

Hopefully Banshee will also let me change video bitrate and size for the device; that would be beautiful.

Here's a tip, just in case:
If you own a device that supports every file format under the sun, add the following line to .is_audio_player:
output_formats=*

---

### Post by FuturePilot on 2008-06-06
I just tried Banshee again for the third time :shock: and this time I think it's a winner. For one I noticed it doesn't try to guess information for blank ID3 tag entries anymore. Some of my files are missing the Album information from the ID3 tag and before Banshee would try to guess what the album was by using the name of the folder that it was in. The problem was, I don't organize my music by Artist/Album hierarchy so it was inserting totally nonsense stuff for Album. Now it seems to insert something more sensible like Unknown Album which is much better. 

Another big plus is that it has video support. I haven't found a good media player that does audio **and** video. Usually it's just one or the other. 

Another cool thing is that I can rip and burn CDs which is something else I haven't found in other players.

Banshee is the ultimate media player I've been looking for for a long time now. :guitar: The only thing I think it's missing is streaming support. Though I was able to force it to open a stream by doing an Open Location and pointing it to my .pls file. I think I'm going to switch to Banshee from Exaile. I've been a bit disappointed in Exaile recently.

Anyways, great job to the Banshee devs! :guitar:

---

### Post by Mr. Picklesworth on 2008-06-06
I would really prefer media players to just ignore hierarchy altogether. They confuse themselves with their own podcast downloads, even!
Problems with this concept are particularly visible with Banshee now, since video and audio files all end up in the same library, both organized completely differently. Seems the trick is never to look at the files themselves...

---

### Post by pt123 on 2008-06-06
Yeah I don't use folder names for artists, it's annoying when you many songs by different artists. I use folder names for a poor implementation of tags.Since so far no Gnome media player supports tags (i.e. like Google with their Email).

Rhythmbox might get it soon
[http://bugzilla.gnome.org/show_bug.cgi?id=324540](http://bugzilla.gnome.org/show_bug.cgi?id=324540)

---

### Post by Islington on 2008-06-06
does banshee have gapless playback?

---

### Post by banjobacon on 2008-06-06
Does anyone else experience a problem with transferring album art to iPods? I'm transferring albums for which Banshee has the right album art. Once on the iPod, however, many covers are wrong (the came cover is used for multiple albums). Covers also appear distorted in the smaller thumbnails used for the album list. I'm using a 6th gen iPod Classic.

---

### Post by zachtib on 2008-06-06
Oops: [http://banshee-project.org/Releases/1.0.0](http://banshee-project.org/Releases/1.0.0)

banshee-project.org linked to that... looks like it was put up early

It's not in the PPA yet, but I guess it will be soon, and I'm guessing this means they're about to release

Screenshot in case they change it:

---

### Post by FuturePilot on 2008-06-07
Would it be possible to include the patched version of pidgin-musictracker in the repo? The current one doesn't work with Banshee 1.0 but there's a patch out there for it.

Oh and Banshee 1.0 packages are building as I post this. :guitar:

---

### Post by Metaleks on 2008-06-07
> **FuturePilot said:**
> Would it be possible to include the patched version of pidgin-musictracker in the repo? The current one doesn't work with Banshee 1.0 but there's a patch out there for it.

Oh and Banshee 1.0 packages are building as I post this. :guitar:
Finally!  Many thanks.  I've been refreshing the PPA for a while now waiting for them, lol.

---

### Post by FuturePilot on 2008-06-07
> **Metaleks said:**
> Finally!  Many thanks.  I've been refreshing the PPA for a while now waiting for them, lol.

Don't thank me, thank the Ubuntu Banshee team and the Banshee devs. ;)

---

### Post by Metaleks on 2008-06-07
Installed 1.0 finally...everything looks great.  It's just that I can't play a single one of my songs for some strange reason.  It just sits on the "idle" message.

> **FuturePilot said:**
> Don't thank me, thank the Ubuntu Banshee team and the Banshee devs. ;)
I was thanking you for telling me that they were being built :)

Edit: Nevermind.  After rescanning my entire library (even though everything was already loaded properly into Banshee) it now works.  However, choosing a song while in shuffle mode won't let me play it >_<  I later figured out that this only happened with .m4a files.  Is this a bug?  Or are these files not supported?

---

### Post by Mr. Picklesworth on 2008-06-07
I think that's a bug, Metaleks...

Banshee will not play formats even that are supported by GStreamer, such as .m4v or .mov, because it seems to have a list of supported formats *hard-coded* instead of determined dynamically.

Alas, I am still trying to figure out whether it is reported or not. Either I have been spoiled by Launchpad, or GNOME's Bugzilla is an epic failure of usability.

---

### Post by Metaleks on 2008-06-07
> **Mr. Picklesworth said:**
> It's an ugly bug, Metaleks...

Banshee will not play formats even that are supported by GStreamer, such as .m4v or .mov, because it seems to have a list of supported formats *hard-coded* instead of determined dynamically.

Alas, I am still trying to figure out whether it is reported or not. Either I have been spoiled by Launchpad, or GNOME's Bugzilla is an epic failure of usability.
My problem actually turned out to be silly.  I was missing the gstreamer aac codec.  Once that was installed, everything worked like a charm.  Banshee is fully functional now.

[However, some people still can't play mp4s even with all the proper codecs installed.](http://ubuntuforums.org/showthread.php?t=456353)  The solution appears to be to install libfaad2-0.  I can't vouch for it's effectiveness, though.

---

### Post by Swarms on 2008-06-07
Got a strange issue, when I configure a new last.fm radiostation; stays permanently after reopening of the program, but some don't.

Is there a way to solve this?

---

### Post by Metaleks on 2008-06-07
Ahhhh!

Where did the synchronizing option go for MTP devices?  It was here in 0.13, but not in 1.0? :confused:

---

### Post by hyperair on 2008-06-08
> **FuturePilot said:**
> Would it be possible to include the patched version of pidgin-musictracker in the repo? The current one doesn't work with Banshee 1.0 but there's a patch out there for it.

Heheh. I wrote that patch. I'll ask the rest of the team and see if I can package the patch. :)

> **Metaleks said:**
> Ahhhh!

Where did the synchronizing option go for MTP devices?  It was here in 0.13, but not in 1.0? :confused:
Unfortunately, synchronizing hasn't been implemented in 1.0, but copying to the devices has.

---

### Post by FuturePilot on 2008-06-08
> **hyperair said:**
> Heheh. I wrote that patch. I'll ask the rest of the team and see if I can package the patch. :)


Awesome. Thanks! :)

---

### Post by hyperair on 2008-06-08
Here are pidgin-musictracker debs with the Banshee 1.0 patch inside. Have fun :) 

I'll upload it to the PPA if Sebastian Dröge consents, but until then be happy with this deb. :)

---

### Post by fwre01 on 2008-06-08
> **Metaleks said:**
> Ahhhh!

Where did the synchronizing option go for MTP devices?  It was here in 0.13, but not in 1.0? :confused:

Im rly shocked this has been taken out, this is what made banshee brilliant in the first place! Does anyone know if this is going to be implemented in the future?

EDIT: Hmmmm, i just watched the Banshee demo they did on LugRadio and they mentioned they were going to have two different synchronization models. One that copies in real time and one that automatically sync's your device when it is plugged in.

I havent installed 1.0 yet, but i hope there is an auto-sync function

Has anyone used auto-sync with an iPod yet?

---

### Post by hyperair on 2008-06-08
Sync has not come to 1.0 yet for all digital audio players. It should be in 1.1 though. So just wait a little longer. However you can still copy your music in manually.

---

### Post by Swarms on 2008-06-08
Autosync would be awesome! Removing any need of having iTunes, if there was just an easy way to seup your iPhone that would be kickass.

---

### Post by FuturePilot on 2008-06-08
> **hyperair said:**
> Here are pidgin-musictracker debs with the Banshee 1.0 patch inside. Have fun :) 

I'll upload it to the PPA if Sebastian Dröge consents, but until then be happy with this deb. :)

Many thanks! :)

---

### Post by FuturePilot on 2008-06-08
Question, what happened to the little popup notification bubble when the song changes? It doesn't seem to work with 1.0. It was working with 0.99.3.

---

### Post by speedemonV12 on 2008-06-08
i just threw this one in my apps for a test drive and WOW this is amazing

just set this to my default player over rythmbox !

---

### Post by fluffman86 on 2008-06-09
> **FuturePilot said:**
> Question, what happened to the little popup notification bubble when the song changes? It doesn't seem to work with 1.0. It was working with 0.99.3.

Ditto for me.  Has a bug been filed?  Also, a few of my albums will "freeze" after some songs.  E.g., play track 1...banshee goes on to 2, then 3, then says "idle" without going on to track 4.  I double click on track 4 to play it, and it plays fine, then plays 5, then again goes idle.

Also, I'm having trouble dragging and dropping songs onto my iPod.  This worked fine in 0.99.3 but now nothing happens in 1.0.0 DRAFT.

edit: drag and drop works.  I was trying to drag "Music Library" or certain smart playlists (like "Recently Added").  Didn't this work before?  I don't really remember.  Anyhoo, I tried dragging and dropping single songs or a group of songs (all of them in my recently added list by hitting ctrl+a) onto my ipod, and it appears to work...

---

### Post by kpkeerthi on 2008-06-09
Sorry to see you go... rhythmbox! You've been loyal to me for many years.

---

### Post by Major_Kong on 2008-06-09
It's still a bit too gnomish (lack of "advanced" options if you want them) but still better than rythmbox.

---

### Post by barbedsaber on 2008-06-09
ah, thats all well and good, but there is still one question...


will it blend? :)

---

### Post by mrgnash on 2008-06-09
> **Major_Kong said:**
> It's still a bit too gnomish (lack of "advanced" options if you want them) but still better than rythmbox.

That's a virtue, not a flaw.

---

### Post by Mr. Picklesworth on 2008-06-09
> **mrgnash said:**
> That's a virtue, not a flaw.

Yay, someone who understands! Indeed, Banshee has been designed cleanly such that those things do not need to exist. It does not have a confused code base or a two-headed design :)

Really, a good example of "too many options" versus "magical defaults" is Beagle vs. Tracker. Tracker exposes a horrifying number of advanced options down to its indexer's nice value as if they are normal. Beagle, on the other hand, while theoretically slower (it's written in Mono), actually performs way better for me because it figures that stuff out automatically. It has been written to determine, on its own, how not to interfere with what I wish to do.

---

### Post by speedemonV12 on 2008-06-09
this program is amazing.. my new favorite

---

### Post by MemoryDump on 2008-06-09
I'm trying to compile from source and I'm getting this:

```
./Banshee.Widgets/VolumeButton.cs(55,17): error CS0612: `Gtk.Tooltips' is obsolete
Compilation failed: 1 error(s), 0 warnings
make[4]: *** [../../../bin/Banshee.Widgets.dll] Error 1
```
how to I update Gtk.Tooltips?

edit: trying svn now.. wish me luck ;)
edit2: SVN installed/compiled OK! w00t - what's the command to update it now in the future?

---

### Post by Robux the great on 2008-06-09
I have just had a look at the banshee website.

It looks awesome

I will be down loading this to have a look

Will it be going in to Ubuntu repository?

Regards

Rob

---

### Post by aamukahvi on 2008-06-09
Wonder what happened to their web site?
[http://banshee-project.org/](http://banshee-project.org/)

---

### Post by Frak on 2008-06-09
> **FuturePilot said:**
> I just tried Banshee again for the third time :shock: and this time I think it's a winner. For one I noticed it doesn't try to guess information for blank ID3 tag entries anymore. Some of my files are missing the Album information from the ID3 tag and before Banshee would try to guess what the album was by using the name of the folder that it was in. The problem was, I don't organize my music by Artist/Album hierarchy so it was inserting totally nonsense stuff for Album. Now it seems to insert something more sensible like Unknown Album which is much better. 

Another big plus is that it has video support. I haven't found a good media player that does audio **and** video. Usually it's just one or the other. 

Another cool thing is that I can rip and burn CDs which is something else I haven't found in other players.

Banshee is the ultimate media player I've been looking for for a long time now. :guitar: The only thing I think it's missing is streaming support. Though I was able to force it to open a stream by doing an Open Location and pointing it to my .pls file. I think I'm going to switch to Banshee from Exaile. I've been a bit disappointed in Exaile recently.

Anyways, great job to the Banshee devs! :guitar:
aye, +1

Though, I just share my Zune folder, for which the Zune software automatically sorts the music by artist, then by album.

---

### Post by Metaleks on 2008-06-10
There was a Banshee update an hour ago.  Anyone know what that was about?  The website is down.  And I can't find the release notes anywhere.

---

### Post by vivekrocks on 2008-06-10
:)

---

### Post by Major_Kong on 2008-06-10
> **mrgnash said:**
> That's a virtue, not a flaw.

Not really. What if i want to do something more "advanced" like tweaking with the import format settings? The options that Banshee gives are very limited. Or for that matter the transcode settings when sending flac files to my portable mp3 player ? 
These are basic options that are avaliable to many audio players... There's a lack of a "advanced" button in banshee.

EDIT: Or how do i tweak the album groupping settings ? 

@New Package
Why is brasero a dependency of the banshee package ?

---

### Post by Frak on 2008-06-10
Burning CDs/DVDs

---

### Post by Major_Kong on 2008-06-10
> **Frak said:**
> Burning CDs/DVDs

Should be a "recommended" package anyway...

---

### Post by Robux the great on 2008-06-10
Hi 

I will be checking this out

Thanks for the heads up

Regards

Rob

---

### Post by OZFive on 2008-06-10
Banshee is indeed awesome, I am loving the new stuff in it and cannot wait till it is fully finished and at 1.0.  

The iPod disk useage meter does not fit astheticly with the rest of the program in my opinion.  Is it a direct rip of the iTunes one?

---

### Post by zekopeko on 2008-06-10
> **Metaleks said:**
> There was a Banshee update an hour ago.  Anyone know what that was about?  The website is down.  And I can't find the release notes anywhere.

i don't know the specifics but it also updated the podsleuth package for me for my ipod and it's finally working(ipod managment i mean)!

anyway, bye bye exaile. welcome banshee :D

---

### Post by hyperair on 2008-06-10
I've shifted stuff from Recommends to Depends because the proper behaviour for those packages is for them to be installed by default.

---

### Post by castrojo on 2008-06-10
[http://digg.com/linux_unix/Banshee_1_0_Final_Released](http://digg.com/linux_unix/Banshee_1_0_Final_Released)

Please digg!

---

### Post by Npl on 2008-06-10
From the screenshots it pretty much looks like Rhythmbox?

---

### Post by banjobacon on 2008-06-10
Unlike some, I'm moving back to Rhythmbox. Managing my iPod with Banshee just doesn't work correctly. Most of the album art is incorrect. Worse than that, I often find my iPod says there's no music on it after using Banshee to transfer music onto it. The solution to the "No Music" problem is to use Rhythmbox. I don't have to actually do anything but have Rhythmbox access my iPod. After ejecting, it works as it should. 

Rhythmbox may not transfer artwork onto my iPod, but I'd rather lose this feature than have it never work.

---

### Post by Hairy_Palms on 2008-06-10
definately an improvement over the previous release, however ill still be sticking to rhythmbox too, it still uses over double the ram of rhythmbox to do the same things, not to mention its mono dependancy, no thanks.

---

### Post by FuturePilot on 2008-06-10
So, anyone know what happened to the notification bubbles? I kind of miss that. :(

---

### Post by Frak on 2008-06-10
> **FuturePilot said:**
> So, anyone know what happened to the notification bubbles? I kind of miss that. :(
They said they hated you... so they left.



;)

---

### Post by FuturePilot on 2008-06-10
> **Frak said:**
> They said they hated you... so they left.



;)

How dare they! :evil: :lol:

---

### Post by OZFive on 2008-06-11
I was wondering, it the "now Playing" in the side list supposed to do anythin when playing music?  I iknow it shows video during vid play.  How about music?

---

### Post by Christmas on 2008-06-11
I like very much the new layout of the website. As for the player itself, it's pretty buggy in my opinion (tested it from 0.99.1 up to 1.0.0).

---

### Post by adityakavoor on 2008-06-11
any one got pidgin music tracker working with banshee-1 ?

music tracker works well with exaile

---

### Post by elashish on 2008-06-11
Out of curiosity, any way to configure banshee so it actually closes when you close the window (instead of just minimizing to the tray)?

---

### Post by janfsd on 2008-06-11
Banshee still doesn't have proper crossfade :(

[http://bugzilla.gnome.org/show_bug.cgi?id=440952](http://bugzilla.gnome.org/show_bug.cgi?id=440952)

---

### Post by elashish on 2008-06-11
> **elashish said:**
> Out of curiosity, any way to configure banshee so it actually closes when you close the window (instead of just minimizing to the tray)?

Nevermind, I figured it out - I disabled the Notification Area extension under preferences. It'd still be nice to have the icon though, it's just that I want it to stop playing when I close it.

---

### Post by MaX on 2008-06-11
Ok, I'm probably out on a limb here but....
I'm running Banshee from the PPA and I'm also running Intrepid.

When I try to start, Banshee tells me this:
```
An unhandled exception was thrown: duplicate column name: ExternalID

  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in /build/buildd/banshee-1-1.0.0/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate () [0x000ae] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176 
  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1-1.0.0/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.24.17

Assembly Version Information:

System.Transactions (2.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.0.0.12614)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gtk-sharp (2.12.0.0)
Hyena (1.0.0.12613)
System (2.0.0.0)
gdk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
Banshee.Core (1.0.0.12618)
Banshee.Services (1.0.0.12619)
Banshee.ThickClient (1.0.0.12622)
Nereid (1.0.0.12623)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-17-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu intrepid (development branch)"

[/etc/debian_version]
lenny/sid

```

---

### Post by FuturePilot on 2008-06-11
> **adityakavoor said:**
> any one got pidgin music tracker working with banshee-1 ?

music tracker works well with exaile

You need a patched version that works with Banshee 1.0. You can get it [here]("http://ubuntuforums.org/showpost.php?p=5140193&postcount=304")

---

### Post by speedemonV12 on 2008-06-11
is the banshee-1 package found in synaptic the currrent version 1.0 found on the banshee site?

---

### Post by geoken on 2008-06-11
I'm on hardy and have the exact same error (line for line) as MaX. 

Any ideas?

---

### Post by geoken on 2008-06-11
Deleting the 'banshee -1' folder in /home/<username>/.config/ just solved this issue for me.

---

### Post by fluffman86 on 2008-06-12
I'm almost ready to quit banshee because of what it just did to me.

I just edited the tags on several albums in banshee.  I realized that I didn't change the filename along with them, so I opened up ex falso to change the filename based on the track title that I had just changed.  

ex falso finds no new titles...they only show up in banshee, which means that while banshee may "support" tag editing, they don't mean the standard ID3 tags.  grr...

---

### Post by FuturePilot on 2008-06-12
> **fluffman86 said:**
> I'm almost ready to quit banshee because of what it just did to me.

I just edited the tags on several albums in banshee.  I realized that I didn't change the filename along with them, so I opened up ex falso to change the filename based on the track title that I had just changed.  

ex falso finds no new titles...they only show up in banshee, which means that while banshee may "support" tag editing, they don't mean the standard ID3 tags.  grr...

Make sure you enable the option to "Write metadata to files" under Edit&#8594;Preferences. It seems to off by default.

---

### Post by fluffman86 on 2008-06-12
> **FuturePilot said:**
> Make sure you enable the option to "Write metadata to files" under Edit&#8594;Preferences. It seems to off by default.

Haha. Yeah, thanks.  I just realized and came back to edit my post before anyone saw my stupidity.  

I turned it on the "write metadata" option in a previous release but it looks like it got turned off somehow.  Oh well, all is good now.  

Banshee still RAWKZ, just ignore my previous post :guitar:

---

### Post by Tomatz on 2008-06-12
Songbird is much better and has some awesome plugins. It also allows you to download tracks from within (only download free tracks it would be illegal not to).

Get it from [www.getdeb.net](www.getdeb.net)

---

### Post by adityakavoor on 2008-06-12
When I import media from the same directory 'n' times, the song gets an entry in the 

library that many number of times. Banshee should only append the new files added to 

the library. To see a song many times in a library is irritating. see attachment -- the songs are repeated twice

---

### Post by Swarms on 2008-06-12
> **Tomatz said:**
> Songbird is much better and has some awesome plugins. It also allows you to download tracks from within (only download free tracks it would be illegal not to).

Get it from [www.getdeb.net](www.getdeb.net)

Ignore this Ballmer impostor!

---

### Post by Tomatz on 2008-06-12
> **Swarms said:**
> Ignore this Ballmer impostor!

I got 5 words for you...

I love the ubuntu forums!!

Whhoooo whoooo yeah whooo 

Developers Developers Developers Developers Developers Developers!!!!!!

Urrgh *tomatz dies of heart attack*

:lolflag:

---

### Post by Tomatz on 2008-06-12
> **Swarms said:**
> Ignore this Ballmer impostor!


They float swarms... and when your down Redmond with me....


You'll float too!!!

Muhhhhaaaa

---

### Post by Frak on 2008-06-12
> **Tomatz said:**
> Songbird is much better and has some awesome plugins. It also allows you to download tracks from within (only download free tracks it would be illegal not to).

Get it from [www.getdeb.net](www.getdeb.net)
Banshee hasn't forgotten its identity, that is all.

---

### Post by geoken on 2008-06-12
I'm probably sticking with rhythmbox. I haven't been too impressed by banshee. Despite all the claims of awesomeness, I'm just not seeing it.

IMO, the only thing it has on RhythmBox is video support, but the video support isn't good enough to make me give up Miro. I thought the video support would let me watch some of the video podcasts I subscribe to (rather than just listening to them like RhythmBox) but it didn't work. It's at the point where I consider it a non-feature. Right now all it will do is present me a flat list of my video files, even the Nautilus beats this by presenting me a tree view and video thumbnails. Sure, I can add metadata, but that would mean I need to maintain two video libraries (one in banshee and one in my prefered app). 

Apart from that, I can't find anything that banshee does better than rhythmbox. The much applauded LastFM plugin has similar abilities to rhtymbox's. Create stations, love/ban tracks, skip tracks. banshee has a favorite artists view, but I can't click artists and play them so it isn't really any benefit. Also, the tracklist view makes the current song go into buffer loop of I try to click on any individual track. In terms of core usage (making a station based on tag, neighborhood, or similar artist; save that station then play it) both apps function identically.

Podcasts work the exact same.

RhytmBox has better radio support. Actually, banshee has no radio support.

Rhtymbox can work with my Mp3 player (Creative Zen). Banshee can only read it, but can't transfer music to it. 

Rhytmbox has a better UI (subjective). For the mast part the UI's are identical, but I've noticed some small annoyances in bashee's. For example, the scrub bar is way too small, I don't need it often but when I do (long 1hr+ dj sets)it's hard to use. Also, seeing as they put so little importance on the scrub bar, it's strange that the default action when scrolling over the tray icon is to seek through the track rather than adjusting volume (a much more common task). I think even skipping/rewinding tracks would have been more desirable than the tray icon's current actions.

It doesn't watch library folders

It also uses massive amounts of memory (100mb + while sitting idle)

---

### Post by Tomatz on 2008-06-12
> **Frak said:**
> Banshee hasn't forgotten its identity, that is all.

Fair enough. I've just never been a fan, its functional and lightweight though.

---

### Post by Major_Kong on 2008-06-12
> Rhtymbox can work with my Mp3 player (Creative Zen). Banshee can only read it, but can't transfer music to it. 

I have a Creative Zen V Plus, and it can transfer to it. Actually it's the only thing i use Banshee for, rythmbox has some problems transcoding audio files when needed. Granted it HAS some problems, it does the job* i want it to do.


*actually, i would be happier if i could have better control over the transcoding settings but still...

---

### Post by geoken on 2008-06-12
> **Major_Kong said:**
> I have a Creative Zen V Plus, and it can transfer to it. 

That's actually a different player. It's confusing because creative uses a really convoluted naming scheme. The creative Zen, Zen Vision, and Zen V are all completely different players. 


If you're going to use an app only for file transfers try Amarok. Amarok handles my player even better than RhyhmBox. With amarok I can grab a playlist, drag it to my player and Amarok will automatically transfer all the associated songs and generate the playlist on my player. No other app was able to do this.

---

### Post by Major_Kong on 2008-06-12
> **geoken said:**
> That's actually a different player. It's confusing because creative uses a really convoluted naming scheme. The creative Zen, Zen Vision, and Zen V are _all completely different players_. 


If you're going to use an app only for file transfers try Amarok. Amarok handles my player even better than RhyhmBox. With amarok I can grab a playlist, drag it to my player and Amarok will automatically transfer all the associated songs and generate the playlist on my player. No other app was able to do this.

Oops, my bad. 

Very nice feature indeed. But i don't use playlists very often or at all for that matter... But tell me what transcoding options do you have ?

---

### Post by Mateo on 2008-06-12
> **geoken said:**
> That's actually a different player. It's confusing because creative uses a really convoluted naming scheme. The creative Zen, Zen Vision, and Zen V are all completely different players. 

I have a ZEN and i have the opposite experience of you.  I can transfer but can't play from it.

---

### Post by geoken on 2008-06-12
> **Major_Kong said:**
> 

Very nice feature indeed. But i don't use playlists very often or at all for that matter... But tell me what transcoding options do you have ?

You first go to Tools>Script Manager and click the 'Get More Scripts' button. This will open a little window with a bunch of scripts/plugins, download the one called transKode. The transKode config has a drop down menu that lets you choose the profile, there are options like AAC, FLAC, OGG, MP3, WAV, WMA, APE. Once you choose a profile you can tweak some of the advanced settings (bitrate, replay gain, VBR settings and even equalization). Then you save your settings and go to the 'Device Settings' and choose to enable or disable transcoding (you also choose 'transcode whenever possible' and 'transcode whenever necessary')

---

### Post by jeffreyvergara.NET on 2008-06-13
cool! i really love the new banshee!

---

### Post by Changturkey on 2008-06-13
My Ipod Shuffle is detected, but I can't do anything with it. I restored it on a Windows machine, could that be a problem or?

---

### Post by Psyphre on 2008-06-14
Hey, just wondering if anyone has managed to use custom album art in this new banshee? The old one would be able to use images placed in the track's folder, but banshee 1.0 doesnt seem to do this anymore.

---

### Post by mrgnash on 2008-06-14
I am a big fan of Rhythmbox, but Banshee 1.0 has converted me. Podcast support seems to be better (especially given that it also supports vodcasts), and the fact that it can index my music AND video collections is really neat. Now all it needs is some type of collection monitoring, and support for online radio stations.

---

### Post by cgrenier on 2008-06-15
Psyphre: I just read that they are going to implement that soon.  In the meantime, you can save an image as "artist-albumname.jpg" without spaces or special characters into your /home/USER/.cache/album-art/ folder and Banshee will pick it up as album art.  It's a lot of work for album art but still good to know.

---

### Post by Psyphre on 2008-06-15
> **cgrenier said:**
> Psyphre: I just read that they are going to implement that soon.  In the meantime, you can save an image as "artist-albumname.jpg" without spaces or special characters into your /home/USER/.cache/album-art/ folder and Banshee will pick it up as album art.  It's a lot of work for album art but still good to know.

Thanks alot, thats really useful to know.

---

### Post by hoboken on 2008-06-15
Banshee 1.0 is the media player to end all media players IMO. Best thing gnome has ever seen! 

Video is a nice addition but I can't use it - compiz is the problem. You remember that old compiz problem that caused videos to seem black, and only appear when moving or resizing the window? Well, it's that. No idea how to fix besides switching to metacity - not an option! 

I'm sure they'll iron out these bugs - I can't wait!

---

### Post by Tomatz on 2008-06-15
> **hoboken said:**
> Banshee 1.0 is the media player to end all media players IMO. Best thing gnome has ever seen! 

Video is a nice addition but I can't use it - compiz is the problem. You remember that old compiz problem that caused videos to seem black, and only appear when moving or resizing the window? Well, it's that. No idea how to fix besides switching to metacity - not an option! 

I'm sure they'll iron out these bugs - I can't wait!

You should check out songbird ;)

---

### Post by FuturePilot on 2008-06-15
Is there any way to rescan your library to pick up any new songs that were added?

---

### Post by Mateo on 2008-06-15
Yeah, I'm loving it.  The only downside is that it's a little too heavy on the resources.

I'm thinking about a server set up though.  And mpd is really the only answer when you want to have your song collection sit and play off a server.

---

### Post by hoboken on 2008-06-15
Songbird eh? I'm installing now, see how it goes. Cheers!

---

### Post by Frak on 2008-06-15
> **FuturePilot said:**
> Is there any way to rescan your library to pick up any new songs that were added?
Mine does that automatically...

---

### Post by FuturePilot on 2008-06-15
> **Frak said:**
> Mine does that automatically...

Automagically? Hmmmm. It didn't seem to do that. I added some new songs to my collection and started up Banshee but they never showed up. :confused:

---

### Post by fwre01 on 2008-06-15
> **Frak said:**
> Mine does that automatically...


Can banshee monitor folders?? i didnt think it could

---

### Post by Frak on 2008-06-15
> **FuturePilot said:**
> Automagically? Hmmmm. It didn't seem to do that. I added some new songs to my collection and started up Banshee but they never showed up. :confused:
Automagically with the ability to File->Import Folder :P

---

### Post by fwre01 on 2008-06-15
oh...so, it doesnt monitor folders automatically? (shame)

---

### Post by palimmo on 2008-06-15
> **isaacj87 said:**
> Hmmm...Found a *solution* (worked for me). Just move the dir ~/.config/banshee-1 (or delete it) and then try opening Banshee Beta 2 again.

Thanks!

Same problem with banshee 1.0

---

### Post by Major_Kong on 2008-06-16
> **geoken said:**
> You first go to Tools>Script Manager and click the 'Get More Scripts' button. This will open a little window with a bunch of scripts/plugins, download the one called transKode. The transKode config has a drop down menu that lets you choose the profile, there are options like AAC, FLAC, OGG, MP3, WAV, WMA, APE. Once you choose a profile you can tweak some of the advanced settings (bitrate, replay gain, VBR settings and even equalization). Then you save your settings and go to the 'Device Settings' and choose to enable or disable transcoding (you also choose 'transcode whenever possible' and 'transcode whenever necessary')

Sold.

Now if only Amarok would make gtk version... Well, you can't have everything and it's good enough for now...

---

### Post by Tomatz on 2008-06-16
> **Major_Kong said:**
> Sold.

Now if only Amarok would make gtk version... Well, you can't have everything and it's good enough for now...

Exaile?

Very like amarok but written in gtk ;)

---

### Post by Major_Kong on 2008-06-16
> **Tomatz said:**
> Exaile?

Very like amarok but written in gtk ;)

Does it have the same transcoding features that amarok has ?

---

### Post by geoken on 2008-06-16
> **mrgnash said:**
> I am a big fan of Rhythmbox, but Banshee 1.0 has converted me. Podcast support seems to be better (especially given that it also supports vodcasts), and the fact that it can index my music AND video collections is really neat. Now all it needs is some type of collection monitoring, and support for online radio stations.

My experience with video podcasts is identical in banshee and rhythmbox. Both will download them and play the audio and neither will play the video.

---

### Post by jviscosi on 2008-06-16
> **mrgnash said:**
> I am a big fan of Rhythmbox, but Banshee 1.0 has converted me. Podcast support seems to be better (especially given that it also supports vodcasts), and the fact that it can index my music AND video collections is really neat. Now all it needs is some type of collection monitoring, and support for online radio stations.

I tried Banshee 1.0 the other day and it stuffed all my podcasts in with the regular music (I have an old 4G iPod).  I didn't see any see any options for changing that.  Did I just miss something?

---

### Post by barbedsaber on 2008-06-16
I have been converted

---

### Post by Tomatz on 2008-06-17
> **Major_Kong said:**
> Does it have the same transcoding features that amarok has ?


I dunno i haven't used it much. Its in the repos so you can just uninstall it if you dont like it.

---

### Post by forestpixie on 2008-06-17
I've never found either exaile or banshee to deal with playlists very well although exaile seems a bit better. Banshee seems to make the whole playlist thing very hard - perhaps I've not worked out an easy way.

Exaile sometimes has problems restarting from last played.

---

### Post by Tomatz on 2008-06-17
> **forestpixie said:**
> I've never found either exaile or banshee to deal with playlists very well although exaile seems a bit better. Banshee seems to make the whole playlist thing very hard - perhaps I've not worked out an easy way.

Exaile sometimes has problems restarting from last played.

I keep saying this on this thread, you really should check out **songbird**. It is by far the best media player for linux. It is based on the geko engine and already has some great plugins.

[www.getdeb.net](www.getdeb.net)

---

### Post by forestpixie on 2008-06-17
> I keep saying this on this thread, you really should check out songbird.I have looked at it a few times - even in the dark times at least I think I did - but I'll just stick to amarok for the time being thanks :D

I only use them for music and having a playlist editor that works and an app that starts off where I left it is good.

---

### Post by Major_Kong on 2008-06-18
> **Tomatz said:**
> I dunno i haven't used it much. Its in the repos so you can just uninstall it if you dont like it.

It doesn't...

---

### Post by tbroderick on 2008-06-18
New Banshee release in early July

[http://gburt.blogspot.com/2008/06/banshee-momentum.html](http://gburt.blogspot.com/2008/06/banshee-momentum.html)

SVN already has internet radio and multi-artist support.

---

### Post by barbedsaber on 2008-06-19
were can I find a banshee irc channel or help forum?

---

### Post by Tomatz on 2008-06-19
> **Major_Kong said:**
> It doesn't...

Oh well...

Why you would need that in a media player i dont know :confused:


Too much bloat for me.

---

### Post by tbroderick on 2008-06-19
> **barbedsaber said:**
> were can I find a banshee irc channel or help forum?

#banshee @ irc.gnome.org

---

### Post by Vaelrith on 2008-06-19
Is anyone else having problems showing cover art from banshee 1.0 in the now playing screenlet?

The song info (title, artist, album) shows up, just not the cover art...

---

### Post by FuturePilot on 2008-06-20
> **tbroderick said:**
> New Banshee release in early July

[http://gburt.blogspot.com/2008/06/banshee-momentum.html](http://gburt.blogspot.com/2008/06/banshee-momentum.html)

SVN already has internet radio and multi-artist support.

Awesome! Internet radio was the one thing I thought it was missing. This is great!:guitar:

---

### Post by Major_Kong on 2008-06-20
> **Tomatz said:**
> Oh well...

Why you would need that in a media player i dont know :confused:


Too much bloat for me.

I need something to transfer my music (and if necessary transcode it) to my Zen V Plus.
I can't find a standalone app that does this.

It's that simple.


PS: If that's too bloat for you, why are you interested in "jukebox" audio players ? Something along the lines of Audacious would be better suited for you.

---

### Post by geoken on 2008-06-20
> **Tomatz said:**
> 

Why you would need that in a media player i dont know :confused:


Too much bloat for me.

A typical situation where I would need that is when I'm listening to music and say "Wow, I haven't heard this song in a while. I'm going to put it on my Mp3 player". Doesn't really seem like a strange situation to me:confused:

It also isn't really bloat. It's just sending the file to ffmpeg/LAME. Calling it bloat would be like calling a nautilus script bloat.

---

### Post by mrgnash on 2008-06-20
> **FuturePilot said:**
> Awesome! Internet radio was the one thing I thought it was missing. This is great!:guitar:

Me too :)

---

### Post by Nom de plume on 2008-06-26
> **bobbocanfly said:**
> No need to use a deb really, compiling is dead easy. 

```
cd wherever-you-downloaded-it
tar -xvf banshee-1-0.98.1.tar.bz2
cd banshee-1-0.98.1
sudo apt-get build-dep banshee
./configure
make
sudo make install 
```

When you want to remove it im pretty sure the makefile has an uninstall clause so cd back into the source directory and run

```
sudo make uninstall
```

You've just solved my problem without me even having to ask you! Thank you! I've been wrestling with the new Banshee for days! That worked in a flash!:KS

---

### Post by Fingers &amp; Thumbs on 2008-06-26
I'm really liking banshee, it's only giving me one headache, It wont find my usb mobile broadband modem. Is there a way I can instruct it to use dev/ttyUSB0?

---

### Post by Nom de plume on 2008-06-26
> **Major_Kong said:**
> I need something to transfer my music (and if necessary transcode it) to my Zen V Plus.
I can't find a standalone app that does this.

It's that simple.


PS: If that's too bloat for you, why are you interested in "jukebox" audio players ? Something along the lines of Audacious would be better suited for you.

I also have the Creative Zen Plus and I've got it working fine with Gnomad2, only problem is it doesn't copy album art. 

Banshee-1 doesn't see my Zen at all, but then it doesn't give me the option of podcasts either, so I think it might be broken. Anyone got any suggestions for a semi-green Linux girl with a broken Banshee-1?

---

### Post by Nom de plume on 2008-06-26
> **Nom de plume said:**
> I also have the Creative Zen Plus and I've got it working fine with Gnomad2, only problem is it doesn't copy album art. 

Banshee-1 doesn't see my Zen at all, but then it doesn't give me the option of podcasts either, so I think it might be broken. Anyone got any suggestions for a semi-green Linux girl with a broken Banshee-1?

Sorry, I should add a P.S.

I am running Banshee 1.0 Alpha 2 and I have no option to play, get, subscribe to or see podcasts in anyway shape or form, I wouldn't know that they were an option in Banshee unless I'd heard other people talking about them. 

Am I missing something really obvious? Am I glow in the dark green?

---

### Post by FuturePilot on 2008-06-26
> **Nom de plume said:**
> Sorry, I should add a P.S.

I am running Banshee 1.0 Alpha 2 and I have no option to play, get, subscribe to or see podcasts in anyway shape or form, I wouldn't know that they were an option in Banshee unless I'd heard other people talking about them. 

Am I missing something really obvious? Am I glow in the dark green?

Any reason you are running Alpha 2? That is very old dev version. You can find the final release [here]("https://edge.launchpad.net/~banshee-team/+archive")

---

### Post by Major_Kong on 2008-06-27
> **Nom de plume said:**
> I also have the Creative Zen Plus and I've got it working fine with Gnomad2, only problem is it doesn't copy album art. 


The problem with gnomad2 is that it doesn't transcode audio files if necessary.

---

### Post by hyperair on 2008-06-27
> **Nom de plume said:**
> You've just solved my problem without me even having to ask you! Thank you! I've been wrestling with the new Banshee for days! That worked in a flash!:KS

0.98.1 is a rather old version you know. And there are up to date debs for Banshee 1.0 here: [http://edge.launchpad.net/~banshee-team/+archive](http://edge.launchpad.net/~banshee-team/+archive)

---

### Post by MatthewPlanchard on 2008-08-07
> **Vaelrith said:**
> Is anyone else having problems showing cover art from banshee 1.0 in the now playing screenlet?

The song info (title, artist, album) shows up, just not the cover art...

I am having the same problem in Banshee 1.2 . :)

FYI, the NowPlaying modified screenlet from gnome-look.org breaks banshee functionality entirely.

---

### Post by njee on 2008-08-09
yeah the majority of my artwork shows up okay but maybe 5% of the albums won't use the coverart from the folder...which was a pain.

Also no corner display for coverart at the moment and contrary to what it says on the webpage Banshee 1.2 still doesn't group my compilations and soundtracks together....

Still if they can sort out these bugs for me I should be able to dump rhythmbox/gtkpod/sounjuicer/tagtool which would be great!

---

### Post by poetofcode on 2008-08-10
I can't seem to get the NowPlaying screenlet to recognise the Banshee-1 metadata. It just sits there as if it was in Stopped state.

@njee: You have to edit the Album Artist tag for each file in your respective albums which are multi-artist. I just typed in 'now' in the filter to find all my 'Now That's What I Call Music' compilations, selected them all and edited them together, setting the Album Artist (not simply 'Artist') to 'Various'.

That way every song by with an Album Artist of 'Various' will be seen as from the same album. Smart! Shame it's not magic though. It would be nice if it make a guess that you could confirm.

---

### Post by njee on 2008-08-10
hey thanks for the tip - I just tried that and it works...still the web page was billing it as automagical!

Now if I could just get it to detect all my cover art!

---

### Post by Maupertus on 2008-08-12
Mmm, really miffed because apparantly the New Banshee versions aren't available for Ubuntu64....grmpf.

(at least, I can't get it working except when using the standard Repo's, which gives me a really old version)

---

### Post by FuturePilot on 2008-08-12
The 64bit packages should be in here as well. Did you try this repository?
[https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive")

---

### Post by Maupertus on 2008-08-12
> **FuturePilot said:**
> The 64bit packages should be in here as well. Did you try this repository?
[https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive")

Yeah I did, I can find it in the rep, install it, but it doesn't react when I try to start it. The version in the standard repo does, only it's the 0.13 version (if I'm correct)

It may be a completely different problem, but term gives absolutely nothing.

---

### Post by hyperair on 2008-08-13
Hmm? "banshee-1 --debug" gives absolutely nothing? That's new. Do other Mono apps work? Like GNOME Do?

---

### Post by Maupertus on 2008-08-13
> **hyperair said:**
> Hmm? "banshee-1 --debug" gives absolutely nothing? That's new. Do other Mono apps work? Like GNOME Do?

This is the output I get when running banshee-1 --debug. Banshee starts when I run it, but it takes a while (+/- 20 sec)

[QUOTE=terminal output "banshee-1 --debug"]
** Running Mono with --debug   **
[Warn  08:36:17.285] DBus support could not be started. Disabling for this session.
[Info  08:36:17.297] Running Banshee 1.2.0
[Debug 08:36:19.379] Core service started (DBusServiceManager, 0.001683s)
[Debug 08:36:19.382] Core service started (DBusCommandService, 0.001738s)
[Debug 08:36:19.564] Opened SQLite connection to /root/.config/banshee-1/banshee.db
[Debug 08:36:19.565] Core service started (DbConnection, 0.182449s)
[Debug 08:36:19.570] Migrating from database version 0 to 17
[Debug 08:36:19.646] Core service started (PreferenceService, 0.017995s)
[Debug 08:36:19.650] Core service started (SourceManager, 0.002754s)
[Debug 08:36:19.930] Core service started (MediaProfileManager, 0.280026s)
[Debug 08:36:19.946] Core service started (PlayerEngine, 0.014858s)
[Debug 08:36:19.977] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 08:36:20.481] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 08:36:20.501] Core service started (TranscoderService, 0.02579s)
[Debug 08:36:20.505] Core service started (PlaybackController, 0.003078s)
[Debug 08:36:20.538] Core service started (ImportSourceManager, 0.00057s)
[Debug 08:36:20.547] Core service started (LibraryImportManager, 0.008233s)
[Debug 08:36:20.549] Core service started (UserJobManager, 0.000869s)
[Debug 08:36:20.622] Core service started (HardwareManager, 0.071786s)
[Debug 08:36:20.685] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 08:36:20.686] Core service started (GtkElementsService, 0.064119s)
[Debug 08:36:20.797] Core service started (InterfaceActionService, 0.110694s)
[Debug 08:36:20.799] Album artwork path set to /root/.cache/album-art
[Debug 08:36:20.799] Migrated 0 album art images.
[Debug 08:36:20.799] Core service started (ArtworkManager, 0.00149s)
[Debug 08:36:21.533] Core service started (NereidPlayerInterface, 0.733788s)
[Debug 08:36:21.537] Extension service started (DaapService, 0.002196s)
[Debug 08:36:21.540] Extension service started (DapService, 0.001843s)
[Warn  08:36:21.554] Caught an exception - No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x000bc] in /build/buildd/banshee-1-1.2.0/src/Extensions/Banshee.MultimediaKeys/Banshee.MultimediaKeys/MultimediaKeysService.cs:117 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-1-1.2.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:167 
[Warn  08:36:21.555] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Debug 08:36:21.610] Extension service started (BookmarksService, 0.054977s)
[Debug 08:36:21.618] Extension service started (CoverArtService, 0.003864s)
[Debug 08:36:22.061] Extension service started (NotificationAreaService, 0.44226s)
[Debug 08:36:22.204] Extension service started (AudioCdService, 0.138057s)
[Debug 08:36:22.282] Extension service started (LastfmRecommendationService, 0.073049s)
[Debug 08:36:22.329] Audioscrobbler state: connected
[Debug 08:36:22.341] Extension service started (AudioscrobblerService, 0.058279s)
[Debug 08:36:22.359] Extension service started (GnomeService, 0.005024s)
[Error 08:36:22.754] Unknown sort key passed in! Published not recognized
[Debug 08:36:22.950] Extension service started (PodcastService, 0.590646s)
[Debug 08:36:23.912] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 08:36:24.067] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 08:36:24.067] Extension service started (GStreamerCoreService, 1.117152s)
[Debug 08:36:24.080] (libbanshee:player) Using built-in equalizer element
[Debug 08:36:24.130] Player state change: NotReady -> Ready
[Debug 08:36:24.149] Player state change: Ready -> Idle
[Warn  08:36:24.154] Caught an exception - No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x000bc] in /build/buildd/banshee-1-1.2.0/src/Extensions/Banshee.MultimediaKeys/Banshee.MultimediaKeys/MultimediaKeysService.cs:117 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00034] in /build/buildd/banshee-1-1.2.0/src/Core/Banshee.Services/Banshee.ServiceStack/ServiceManager.cs:167 
[Warn  08:36:24.172] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  08:36:24.172] All services are started 4.800558s
[Warn  08:36:24.715] IScreensaverManager extension failed to load - Argument cannot be null.
Parameter name: address (in `NDesk.DBus')
  at NDesk.DBus.Bus.Open (System.String address) [0x00042] in /build/buildd/ndesk-dbus-0.6.0/src/Bus.cs:87 
  at NDesk.DBus.Bus.get_Session () [0x0002e] in /build/buildd/ndesk-dbus-0.6.0/src/Bus.cs:41 
Unable to open the session message bus. (in `NDesk.DBus')
  at NDesk.DBus.Bus.get_Session () [0x00043] in /build/buildd/ndesk-dbus-0.6.0/src/Bus.cs:43 
  at Banshee.GnomeBackend.GnomeScreensaverManager..ctor () [0x00006] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Gnome/Banshee.GnomeBackend/GnomeScreensaverManager.cs:52 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
Exception has been thrown by the target of an invocation. (in `mscorlib')
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.CreateInstance (System.Type expectedType) [0x00000] 
  at Banshee.NowPlaying.ScreensaverManager..ctor () [0x00027] in /build/buildd/banshee-1-1.2.0/src/Extensions/Banshee.NowPlaying/Banshee.NowPlaying/ScreensaverManager.cs:44 
[Warn  08:36:24.793] Migrating Internet Radio Stations - Directory '/root/.config/banshee/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String pattern, FileAttributes mask, FileAttributes attrs) [0x00000] 
  at System.IO.Directory.GetFiles (System.String path, System.String pattern) [0x00000] 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00048] in /build/buildd/banshee-1-1.2.0/src/Extensions/Banshee.InternetRadio/Banshee.InternetRadio/XspfMigrator.cs:63 
[Info  08:36:25.254] nereid Client Started
[Debug 08:36:25.326] Dap support extension loaded: Banshee.Dap.Mtp
[Warn  08:36:25.444] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Hal/Device.cs:227 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:102 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x0006c] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:185 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00044] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:56 
[Debug 08:36:25.651] Dap support extension loaded: Banshee.Dap.MassStorage
[Warn  08:36:25.756] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Hal/Device.cs:227 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:102 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x0006c] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:185 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00044] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:56 
[Debug 08:36:25.924] Dap support extension loaded: Banshee.Dap.Ipod
[Warn  08:36:26.020] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Hal/Device.cs:227 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:102 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x0006c] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:185 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00044] in /build/buildd/banshee-1-1.2.0/src/Backends/Banshee.Hal/Banshee.HalBackend/Volume.cs:56 [/QUOTE]

---

### Post by hyperair on 2008-08-13
Looks to me like some kind of DBus error. How are you attempting to run Banshee? In a GNOME environment? Through SSH X forwarding?

---

### Post by cowanh00 on 2008-08-13
> **hyperair said:**
> Here are pidgin-musictracker debs with the Banshee 1.0 patch inside. Have fun :) 

I'll upload it to the PPA if Sebastian Dröge consents, but until then be happy with this deb. :)

Do you have anything for 64 bit? Pleeeeease!!

---

### Post by Maupertus on 2008-08-13
> **hyperair said:**
> Looks to me like some kind of DBus error. How are you attempting to run Banshee? In a GNOME environment? Through SSH X forwarding?

Yes, I'm running it in Ubuntu64, GNOME edition. Sorry I don't know if I use SSH X forwarding. :D

---

### Post by roundhay on 2008-08-13
I'm having the same problem, i can install Banshee-1 using the repo for hardy and I get the banshee icon in the Gnome menu but when i click on the icon banshee does not run?

can anyone help?

---

### Post by Swarms on 2008-08-13
> **roundhay said:**
> I'm having the same problem, i can install Banshee-1 using the repo for hardy and I get the banshee icon in the Gnome menu but when i click on the icon banshee does not run?

can anyone help?

Try writing banshee-1 in a terminal and see what happens, if it launches, then its probably just something wrong with your launcher. Otherwise, reinstall through Synaptic.

---

### Post by roundhay on 2008-08-13
That sorted the problem, now opens from the icon in Gnome menu!

---

### Post by hyperair on 2008-08-14
How very strange.

EDIT: Ah I understand the issue now. It seems that the menu item launches Banshee like this:
```

banshee-1 --redirect-log <other options which I forgot and are not relevant for this issue anyway>

```

Looking at /usr/bin/banshee-1 (which is a shell script) the redirect log feature seems to be handled inside the shell script itself. When ~/.config/banshee-1 doesn't exist, Then the redirect won't work and Banshee won't even start.

The current workaround is to run banshee-1 from terminal or from Run (Alt+F2) at least once. Then ~/.config/banshee-1 will exist and the redirect will work. Another workaround is to just create the folder ~/.config/banshee-1 manually before running Banshee (only needs to be done for the first run). 

I'll go file a bug report now, thanks for telling.

---

### Post by Maupertus on 2008-08-14
> **hyperair said:**
> How very strange.

EDIT: Ah I understand the issue now. It seems that the menu item launches Banshee like this:
```

banshee-1 --redirect-log <other options which I forgot and are not relevant for this issue anyway>

```

Looking at /usr/bin/banshee-1 (which is a shell script) the redirect log feature seems to be handled inside the shell script itself. When ~/.config/banshee-1 doesn't exist, Then the redirect won't work and Banshee won't even start.

The current workaround is to run banshee-1 from terminal or from Run (Alt+F2) at least once. Then ~/.config/banshee-1 will exist and the redirect will work. Another workaround is to just create the folder ~/.config/banshee-1 manually before running Banshee (only needs to be done for the first run). 

I'll go file a bug report now, thanks for telling.

Somebody beat me to the notification, but yup..this is my 'bug' as well. Launched from terminal and no problems, the only strange thing is that I still get a DBus error when I start launch from terminal. I don't think it affects anything straight away, but do you want me to post the output?

---

### Post by jwkungfu on 2008-08-26
Hi there,
I have a 2GB iPod shuffle that's not working with Ubuntu
Can you please run me thru step by step (newbie/computer klutz here) on how to get the shuffle to work?
Many thanks!

---

### Post by Swarms on 2008-08-26
> **jwkungfu said:**
> Hi there,
I have a 2GB iPod shuffle that's not working with Ubuntu
Can you please run me thru step by step (newbie/computer klutz here) on how to get the shuffle to work?
Many thanks!

First make sure that the plugin named "iPod Support" is enabled.

---

### Post by jwkungfu on 2008-08-27
Thanks but where do I check to see if I have this "iPod Support" plugin...?
Mozilla Firefox has plugins? But I doubt music players are run thru it?
Sorry for being such a newbie klutz.... step by step please....

---

### Post by hyperair on 2008-08-27
You're in a Banshee thread not a Firefox thread. Given the context, I think it was pretty obvious that he meant the "iPod support" plugin in Banshee, not in Firefox.

---

### Post by Swarms on 2008-08-27
Edit -> Preferences -> Extensions.

---

### Post by tuxxy on 2008-08-27
Think Ill wait for a .deb but ye it looks improved an as a Banshee user thin it looks impressive

---

### Post by Swarms on 2008-08-27
> **tuxxy said:**
> Think Ill wait for a .deb but ye it looks improved an as a Banshee user thin it looks impressive

Here you go:
[https://launchpad.net/~banshee-team/+archive](https://launchpad.net/~banshee-team/+archive)

---

### Post by Tiede on 2008-08-27
Hello All!!!
 
I see every one excited about the banshee-1 last.fm love/hate buttons, but it seems as if I don't have them...
Is there a special trick to enabling them?

I know my account info is accurate and I even get music recommendation and last loved songs (thru something else).
Any ideas?
Thanks in advance.


--> Check attachment for clarity if needed.

---

### Post by Swarms on 2008-08-27
It is not where I highlighted?

---

### Post by Tiede on 2008-08-27
Woowaoo! Quick response!:KS

No, although the + icons comes up if I highlight Last.fm
really strange stuff...

---

### Post by tbroderick on 2008-08-27
> **Tiede said:**
> Woowaoo! Quick response!:KS

No, although the + icons comes up if I highlight Last.fm
really strange stuff...

Are you listening to a last.fm radio stream? Looks like you are listening to a library track.

---

### Post by fwre01 on 2008-08-27
does anyone know when they are going to bring back the "sync" button when using an ipod. which basically sync's your entire local library to your ipod automatically? there was talk of it coming out in 1.2. but i still havent seen it. or is there a plugin for this?

---

### Post by Tiede on 2008-08-27
> **tbroderick said:**
> Are you listening to a last.fm radio stream? Looks like you are listening to a library track.
Does this work only with an audio stream? Because yes, I am listening to a library track.
In Rhythmbox, it works with library tracks, so I guess I was expecting same from Banshee-1...
Was I wrong to think so?

---

### Post by hyperair on 2008-08-27
No, Banshee only supports Love/Ban with last.fm radio streams.

---

### Post by OZFive on 2008-08-27
I am curious if anyone else is having this issue....

Firefox + Banshee = No love

If I am running Firefox 3.0 and try to open then play a song in Banshee it will not work.  The song will not play and I have to close Firefox toget it to start.

If I close Firefox I can play songs in Banshee 1.0 and then reopen Firefox and be good.  Unless I come across a Flash movie or something and then the Flash sound will not work.

I have also noticed this issue with Totem (xine).

---

### Post by hyperair on 2008-08-27
Oh I've heard of that issue alright. It's neither Totem/Xine nor Banshee/Gstreamer's fault. It's Flash's fault. Flash uses ALSA, Gstreamer and Xine use PulseAudio. Flash locks your sound device, and PulseAudio doesn't work, or vice versa. To get this to work, either install libflashsupport or install Flash 10. libflashsupport is in the Ubuntu repository, and Flash 10 is available through Markus Thielmann's PPA: [https://launchpad.net/~thielmann/+archive](https://launchpad.net/~thielmann/+archive)

---

### Post by BOBSONATOR on 2008-08-28
does anyone know how to manually add the album art?. i wish i coud just rightclick the song and add it right there,....

---

### Post by hyperair on 2008-08-28
I think it's possible to do so by dragging the image into the cover art logo at the top of Banshee, next to where the title, artist and album are displayed. If not, copy it to ~/.cache/album-art/<artist>-<album>.jpg. <artist> is the artist minus spaces/non-alphanumeric characters. <album> is album minus spaces/non-alphanumeric characters.

---

### Post by thomasboleyn on 2008-10-01
I can't believe there's no 'sync' button in this, it's completely put me off using it..

---

### Post by hyperair on 2008-10-01
1.3.1 has sync. However, it's packaged in a different repository because it's a "development version", and not an actual release. You can get it here: [http://launchpad.net/~banshee-unstable-team/+archive](http://launchpad.net/~banshee-unstable-team/+archive)

---

### Post by thomasboleyn on 2008-10-01
What are the stability issues with 1.3.1?

---

### Post by hyperair on 2008-10-01
I don't know. I personally use Banshee from trunk. The devs say that this is less stable than the stuff that they tell me to push into the Banshee Team repository, but I don't notice much difference.

---

### Post by thomasboleyn on 2008-10-01
I'm using it now, it does seem a lot friendlier to my ipods, particularly their playlists. The drag and drop really isn't too bad I suppose. I always wanted to use it that way on itunes back on xp actually, but it was a huge pain to sort out. Has the cover art in the bottom left corner been scrapped now for good?

---

### Post by TeoK on 2008-10-04
> **OZFive said:**
> I am curious if anyone else is having this issue....

Firefox + Banshee = No love

If I am running Firefox 3.0 and try to open then play a song in Banshee it will not work.  The song will not play and I have to close Firefox toget it to start.

If I close Firefox I can play songs in Banshee 1.0 and then reopen Firefox and be good.  Unless I come across a Flash movie or something and then the Flash sound will not work.

I have also noticed this issue with Totem (xine).


Oz, this is due to some quirk in Flash plugin for firefox.
Go to System->Preferences->Sound
change all tabs to ALSA

~

Anyway, since this is a banshee thread, i'll trash the version with smile:

Does it bother anyone that 1.2.1: 

- does NOT remember playlist order on quit( older version sorts alphabetically) (in 1.2.1 the developers chose the 'cute and stupid' name "Sort Children"  - which needs to be set EVERY SINGLE TIME on start up)
- does NOT remember song order on quit (unlike the older version) 
- sorting produces erroneous results (unlike the older version)
- it's VERY difficult to move the song in playlist ( scrolling 'hangs up') 
- does NOT create playlist name automatically  on dragging ( unlike the older version) 
- columns are not expandable ( unlike the older version) 
 
 ~ 
 The more I look at this "new and improved" version - the more I'm convinced this is the case how the developers pushed for new FEATURES (equalizer, video support) and COMPLETELY destroyed FUNCTIONALITY in the process.
 
 Needless to say I went back to 0.13.2.

---

### Post by hyperair on 2008-10-05
> **TeoK said:**
> Oz, this is due to some quirk in Flash plugin for firefox.
Go to System->Preferences->Sound
change all tabs to ALSA

~

Anyway, since this is a banshee thread, i'll trash the version with smile:

Does it bother anyone that 1.2.1: 

- does NOT remember playlist order on quit( older version sorts alphabetically) (in 1.2.1 the developers chose the 'cute and stupid' name "Sort Children"  - which needs to be set EVERY SINGLE TIME on start up) 
- does NOT remember song order on quit (unlike the older version) 
- sorting produces erroneous results (unlike the older version)
- it's VERY difficult to move the song in playlist ( scrolling 'hangs up') 
- does NOT create playlist name automatically  on dragging ( unlike the older version) 
- columns are not expandable ( unlike the older version) 
 
 ~ 
 The more I look at this "new and improved" version - the more I'm convinced this is the case how the developers pushed for new FEATURES (equalizer, video support) and COMPLETELY destroyed FUNCTIONALITY in the process.
 
 Needless to say I went back to 0.13.2.
[list]
[*]Banshee now sorts by artist name, and I don't see any "Sort Children" option anywhere
[*]I **just** noticed it doesn't remember the song order on quit after reading your post, so obviously it doesn't bother me, but I'll file a bug [b]EDIT: Fixed in trunk (and soon, 1.3.2)
[*]"Sorting produces erroneous results" - I don't understand, please elaborate
[*]It's pretty easy to move a song in a playlist, just drag&drop.
[*]does not create playlist name automatically on dragging - I suppose you mean when you drag a bunch of songs into the list of playlists, a drag target called "New Playlist" appears but doesn't prompt you for a name after that? It didn't bother me, but perhaps it would be a nice thing to add. I'll file a bug
[*]Columns are expandable. Just click the border between column headers to resize
[/list]
Banshee 1.0 was a complete rewrite of Banshee and was released without achieving complete feature parity with 0.3.2. If you're that concerned about the missing features, I recommend waiting for 1.4, but that will mean locking your Banshee version and sticking with Hardy until it comes out, because Intrepid doesn't have Banshee 0.13.2. If I'm not mistaken, that one will have complete feature parity. You could also use some of the development versions found on the [Banshee Unstable PPA](http://launchpad.net/~banshee-unstable-team/+archive).

---

### Post by TeoK on 2008-10-05
* Banshee now sorts by artist name, and I don't see any "Sort Children" option anywhere
    - right-click on the "Music Library", you'll see "Sort Children" instead of "Sort Playlists" as it used to be in old version. The developer felt the need to be "cheeky" -  too bad that the developer removed the functionality of remembering the order on quit.
    
    * I just noticed it doesn't remember the song order on quit after reading your post, so obviously it doesn't bother me, but I'll file a bug [b]EDIT: Fixed in trunk (and soon, 1.3.2)
    - ditto
    
    * "Sorting produces erroneous results" - I don't understand, please elaborate
    - Each header of the column has three positions "up" "down" and "off".  When clicking Title or Artist or Album - you'd think the sorting be done in alphabetical order (like in 0.13.2) - but that's NOT the case this one! - it bizarrely groups them in seemingly random chunks no matter how many times you click the header!
    
    * It's pretty easy to move a song in a playlist, just drag&drop.
    - it doesn't work for me. while moving the scrolling locks and I end up overshooting the position. VERY frustrating.
    
    * does not create playlist name automatically on dragging - I suppose you mean when you drag a bunch of songs into the list of playlists, a drag target called "New Playlist" appears but doesn't prompt you for a name after that? It didn't bother me, but perhaps it would be a nice thing to add. I'll file a bug
    - Well , that VERY function WAS in older version !( 0.13.2). It boggles the mind why would anybody want to remove that useful, time-saving trick.
    
    * Columns are expandable. Just click the border between column headers to resize
    - NOT exactly. They are only expandable WITHIN constrains of the window, therefore limiting the number of columns you  might want to see (in practice). The older version was more practical - it expanded beyond the window by utilizing scroll-bar on the bottom.
    
1.2.1 is utterly unusable to me.
These bugs are very serious deal-breakers for me. And I really do not understand why the developers chose to remove so many smart features from 0.13.2

I'll stick with 0.13.2 until new version comes out. 

Banshee is still by far the most intuitive, and...the closest thing to perfect , 'simply beautiful' payer/music organizer (if you pretend iTunes don't exist, LOL)

---

### Post by hyperair on 2008-10-05
> **TeoK said:**
> * Banshee now sorts by artist name, and I don't see any "Sort Children" option anywhere
    - right-click on the "Music Library", you'll see "Sort Children" instead of "Sort Playlists" as it used to be in old version. The developer felt the need to be "cheeky" -  too bad that the developer removed the functionality of remembering the order on quit.
No, actually, it's not being "cheeky". It's more of a technical term. Children of a parent node for example. I'll go bug the devs. About the playlists not staying sorted, file a bug. Software developers are not gods, and hence are imperfect. Mistakes happen, and that's what the bug tracker is for.

> **TeoK said:**
> 
    * "Sorting produces erroneous results" - I don't understand, please elaborate
    - Each header of the column has three positions "up" "down" and "off".  When clicking Title or Artist or Album - you'd think the sorting be done in alphabetical order (like in 0.13.2) - but that's NOT the case this one! - it bizarrely groups them in seemingly random chunks no matter how many times you click the header!
Works fine for me. Perhaps you should whack out Banshee's configuration directory and reimport and see if it works.
    
> **TeoK said:**
> 
    * It's pretty easy to move a song in a playlist, just drag&drop.
    - it doesn't work for me. while moving the scrolling locks and I end up overshooting the position. VERY frustrating.
Doesn't happen for me. For me, it speeds up or slows down scrolling depending on how far I move the song to the border.
    
> **TeoK said:**
> 
    * does not create playlist name automatically on dragging - I suppose you mean when you drag a bunch of songs into the list of playlists, a drag target called "New Playlist" appears but doesn't prompt you for a name after that? It didn't bother me, but perhaps it would be a nice thing to add. I'll file a bug
    - Well , that VERY function WAS in older version !( 0.13.2). It boggles the mind why would anybody want to remove that useful, time-saving trick.

File a bug. It's probably something they forgot to include when they rewrote Banshee.
    
> **TeoK said:**
> 
    * Columns are expandable. Just click the border between column headers to resize
    - NOT exactly. They are only expandable WITHIN constrains of the window, therefore limiting the number of columns you  might want to see (in practice). The older version was more practical - it expanded beyond the window by utilizing scroll-bar on the bottom.
Well I'm sorry it's important for you, but for me, I got pretty irritated if it had a horizontal scrollbar.
    
> **TeoK said:**
> 1.2.1 is utterly unusable to me.
These bugs are very serious deal-breakers for me. And I really do not understand why the developers chose to remove so many smart features from 0.13.2

I'll stick with 0.13.2 until new version comes out. 

Banshee is still by far the most intuitive, and...the closest thing to perfect , 'simply beautiful' payer/music organizer (if you pretend iTunes don't exist, LOL)
I personally don't like iTunes and think Banshee owns it completely and utterly.

---

### Post by xX-Felipao-Xx on 2008-12-27
Is there an automatic way to remove repeated(duplicated) songs from library???

That's really important and useful

---

### Post by hyperair on 2008-12-27
No there isn't. However, there is a playlist generator called Mirage, which generates playlists containing similar songs to a provided song. You could possibly misuse that extension for that purpose.

---

