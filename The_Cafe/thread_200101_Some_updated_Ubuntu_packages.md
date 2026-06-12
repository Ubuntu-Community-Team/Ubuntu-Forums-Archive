---
title: "Some updated Ubuntu packages"
date: 2006-06-19
forum: The Cafe
---

### Post by xXx 0wn3d xXx on 2006-06-19
Hi, I recently compilied a few programs for my Ubuntu machine and I packaged them and uploaded them. I have the latest versions of some commonly used applications like:

Gnomebaker 
Inkscape
Bonfire
Wget
Vlc
Mplayer
Xchat
and a few more...

You can acess the hosting site with the files at [http://ubuntu.filefront.com ]("http://ubuntu.filefront.com")and then just click the "Files" tab to view all of them.

---

### Post by Harold P on 2006-06-19
I'm assuming these are all debian packages? :p

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=Harold P]I'm assuming these are all debian packages? :p[/QUOTE]
Of course :) If anyone wants me to build a package/thinks it should be there, tell me and I will build it.

---

### Post by rai4shu2 on 2006-06-19
Cool. I've been meaning to compare Bonfire and Gnomebaker.

---

### Post by Nonno Bassotto on 2006-06-19
Could you please try to package ktabedit?
[http://kguitartmp.sourceforge.net/](http://kguitartmp.sourceforge.net/)
I've tried to do this myself, but ran into some problems, because of some font packages conflict. It was the first time I tried to build a package myself, I had to install dozens of dev files (these are common files, but I didn't have any dev file installed) and finally desisted because of the conflict.
Thank you

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=Nonno Bassotto]Could you please try to package ktabedit?
[http://kguitartmp.sourceforge.net/](http://kguitartmp.sourceforge.net/)
I've tried to do this myself, but ran into some problems, because of some font packages conflict. It was the first time I tried to build a package myself, I had to install dozens of dev files (these are common files, but I didn't have any dev file installed) and finally desisted because of the conflict.
Thank you[/QUOTE]
Sure I just need to install kde but I should be able to compile it.

---

### Post by xXx 0wn3d xXx on 2006-06-19
Wow that package is hard to build...I got to the last configure step and then I need tse but it's really hard to install. If I can get that to work then the package will be built :) Can anyone who has installed tse help me on this one ?

---

### Post by Iandefor on 2006-06-19
EDIT: Nevermind.

---

### Post by disturbed1 on 2006-06-20
Shouldn't use checkinstall to package programs for other users, it doesn't build a correct control file. Checkinstall won't install any of the required depends, and unless a correctly defined configure script is used it installs the binaries to /usr/local/bin, this can have issues if/when the debian/ubuntu updates come around, which will install to /usr/bin.

You can use the --prefix= option and the build static = yes, shared = no, but then you end up with a huge deb.

With Bonfire, if you don't have libnotify installed, you won't get the nice system tray icon, no gdl, and you won't be able to move the windows around, same if you enabled the beagle search feature.

Checkinstall is nice for your own system, so you can use apt to remove the install. I've ran into problems building on one Ubuntu machine, then attempting to install that package on another machine with the exact same hardware, it didn't work. I've also used checkinstall to create .debs for backup, then when I reinstall the complete OS, sure the .deb file installs without errors (because there is no control file) but the application won't run correctly.

[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html")
[http://www.debian-administration.org/articles/336]("http://www.debian-administration.org/articles/336")

here's your control file for gnomebaker
> 
Package: gnomebaker-0.5.1
Priority: extra
Section: checkinstall
Installed-Size: 2744
Maintainer: root@localhost
Architecture: i386
Version: 0.5.1-1
Description: Gnomebaker 0.5.1 packaged by xXx 0wn3d xXx from ubuntuforums.org
 
here's the control file from an official gnomebaker deb
> 
Package: gnomebaker
Version: 0.5.1-0ubuntu1
Section: gnome
Priority: optional
Architecture: i386
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.13.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libfontconfig1 (>= 2.3.0), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.10.0), libgnome-keyring0 (>= 0.4.3), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.13.0), libgnomevfs2-0 (>= 2.13.92-0ubuntu4), libgstreamer0.8-0 (>= 0.8.11), libgtk2.0-0 (>= 2.8.0), libice6, liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.12.2), libpopt0 (>= 1.7), libsm6, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1), cdrecord, mkisofs, cdda2wav, cdrdao
Recommends: dvd+rw-tools, gstreamer0.8-mad, gstreamer0.8-flac, gstreamer0.8-vorbis
Installed-Size: 2640
Maintainer: Goedson Teixeira Paixao <goedson@debian.org>
Description: application for CD/DVD creation in the GNOME desktop
 Gnomebaker is an easy to use CD/DVD burner. Its current features include:
   * Data and audio CD burning
   * Multisession CDs
   * DVD formating
   * DVD data disk burning
   * On-the-fly data CD burning
   * Cue bin data CD writing 


Not knocking your effort, but trying to save other people from having issues.

---

### Post by Iandefor on 2006-06-20
[quote=disturbed1]Shouldn't use checkinstall to package programs for other users, it doesn't build a correct control file. Checkinstall won't install any of the required depends, and unless a correctly defined configure script is used it installs the binaries to /usr/local/bin, this can have issues if/when the debian/ubuntu updates come around, which will install to /usr/bin.

You can use the --prefix= option and the build static = yes, shared = no, but then you end up with a huge deb.

With Bonfire, if you don't have libnotify installed, you won't get the nice system tray icon, no gdl, and you won't be able to move the windows around, same if you enabled the beagle search feature.

Checkinstall is nice for your own system, so you can use apt to remove the install. I've ran into problems building on one Ubuntu machine, then attempting to install that package on another machine with the exact same hardware, it didn't work. I've also used checkinstall to create .debs for backup, then when I reinstall the complete OS, sure the .deb file installs without errors (because there is no control file) but the application won't run correctly.

[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html")
[http://www.debian-administration.org/articles/336]("http://www.debian-administration.org/articles/336")

here's your control file for gnomebaker
 
here's the control file from an official gnomebaker deb
 


Not knocking your effort, but trying to save other people from having issues.[/quote] I'd been wondering if that was what he'd done.

---

