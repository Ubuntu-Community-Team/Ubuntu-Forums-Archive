---
title: "Ubuntu Gnome bugs?"
date: 2014-01-12
forum: Ubuntu Development Version
---

### Post by ubunt72 on 2014-01-12
I read that Ubuntu Trusty has a lot of bugs and with Gnome, probably as well?

I think I found one.   I cannot easily rename files (on my other - 'external' drive).   When I try to rename a file, the name goes 'blank' (white) and I cannot see anything that I type.  Wtheck?

Is this a well known bug?   The other thing that seems to happen is that another file adjacent to it gets renamed instead.   This is really annoying.   I had to boot up another OS to rename the files.

Edit:  P.S.  It only happens with my external drive.   I don't have this problem with other distros I've used meaning this is a new problem.  But, no matter what I did, the same issue occurs.   If I try renaming a file in my home directory or some place on the OS drive, it works as it should.   I have no idea what to even google if this is a bug in trusty.   Or maybe it's a new bug?   It's definitely a bug - it reoccurs each time.

---

### Post by sammiev on 2014-01-12
I just tried the above with renaming a few files on my external drive with no issues. I as well use Ubuntu Gnome.

---

### Post by kansasnoob on 2014-01-12
Are you fully updated?

If not I'd suspect this bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961)

---

### Post by ubunt72 on 2014-01-12
I believe I am.   I am using Nautilus 3.8.2.   The file manager is called Nautilus?   Does Unity do this as well?   There is no indication of what the program is called.   Strange.  I'm not as familiar with Gnome.  It's called 'Files' but there's a blurb about Nautilus in the License description.

---

### Post by ubunt72 on 2014-01-12
Gnome-shell is at the latest showing in the repo, at 3.8.4-0buntu7.  Problem still occurs.   Trying to rename any file (either in FS or a window) on the other drive results in the text disappearing and just 'white space' there and if you type, nothing is shown.   It looks related to the error in the link posted, above.

---

### Post by kansasnoob on 2014-01-12
> **ubunt72 said:**
> Gnome-shell is at the latest showing in the repo, at 3.8.4-0buntu7.  Problem still occurs.   Trying to rename any file (either in FS or a window) on the other drive results in the text disappearing and just 'white space' there and if you type, nothing is shown.   It looks related to the error in the link posted, above.

I'll check this out myself soon. It may be a different bug.

Before I try could you tell me what file system is in use on the external drive?

I generally still use FAT32 on my flash drives.

---

### Post by grahammechanical on 2014-01-13
I would not say that Trusty is buggy. No. Not at all. Do not forget that Trusty is the development branch that will become Ubuntu 14.04 and it is important that "bugs" be identified and fixed before it becomes Ubuntu 14.04. So, see bug reports not as an indication that something is buggy but as an indication that people are working to create a stable release.

Another thing to keep in mind is that the term "Trusty" will apply also to the development branches of the flavours, Xubuntu, Kubuntu, Lubuntu, Ubuntu Studio, Mythbuntu and Ubuntu Gnome as well as Ubuntu Touch and the core applications that come with it.

Ubuntu Gnome is in the same situation as Xubuntu, Kubuntu and Lubuntu and that is having to deal with bugs in the desktop environment/user interface which may be Gnome shell, Xfce, Kde and Lxde as appropriate. Ubuntu avoids those bugs. How many bugs are upstream bugs but Ubuntu gets the blame.

Regards.

Regards.

---

### Post by ubunt72 on 2014-01-13
> **kansasnoob said:**
> I'll check this out myself soon. It may be a different bug.

Before I try could you tell me what file system is in use on the external drive?

I generally still use FAT32 on my flash drives.
Sorry, I took so long to follow up.   The drive is using ext3.    It's not a flash drive but a legacy HDD in an enclosure and attached via eSATA.  

I use ext4, obviously, with the OS and would if I start from scratch with a new 'data' HDD.   Not sure why a different file system would cause any trouble like what is happening, though.

---

### Post by kansasnoob on 2014-01-14
> **ubunt72 said:**
> Sorry, I took so long to follow up.   The drive is using ext3.    It's not a flash drive but a legacy HDD in an enclosure and attached via eSATA.  

I use ext4, obviously, with the OS and would if I start from scratch with a new 'data' HDD.   Not sure why a different file system would cause any trouble like what is happening, though.

That's OK, I still have several external drives that are formatted NTFS, ext2, and ext3. In fact some of my internal data partitions are still ext3 :)

Sheesh, I still have some old external enclosures that are USB 1.1 :(

Anyway I've tried a lot of renaming scenarios with Nautilus 3.8.2 and 3.10.1 and the only problems I see are theme related. Like here's just one example:

[ATTACH=CONFIG]249494[/ATTACH]

You'll notice that it's almost impossible to see the .png and some themes are even worse :(

I've really not found a theme that works well in Ubuntu GNOME Trusty yet. Does any of this make sense?

I assume that the theme devs simply need time to catch up with the latest gtk changes.

---

### Post by ubunt72 on 2014-01-14
What do you use for screenshots in Gnome?  I could display what I see and post it?   I cannot really see yours, sorry. ;)

---

### Post by ubunt72 on 2014-01-14
> **ubunt72 said:**
> I read that Ubuntu Trusty has a lot of bugs and with Gnome, probably as well?

I think I found one.   I cannot easily rename files (on my other - 'external' drive).   When I try to rename a file, the name goes 'blank' (white) and I cannot see anything that I type.  Wtheck?

Is this a well known bug?   The other thing that seems to happen is that another file adjacent to it gets renamed instead.   This is really annoying.   I had to boot up another OS to rename the files.

Edit:  P.S.  It only happens with my external drive.   I don't have this problem with other distros I've used meaning this is a new problem.  But, no matter what I did, the same issue occurs.   If I try renaming a file in my home directory or some place on the OS drive, it works as it should.   I have no idea what to even google if this is a bug in trusty.   Or maybe it's a new bug?   It's definitely a bug - it reoccurs each time.
Btw, what are your operations exactly?   My exact motions are:
1) right click on file folder and click 'rename...' - immediately, the file name disappears.  
2) I can type but no output of text shows up (until I type the 'Enter'  key or click the left button of the mouse) - i.e. it's just a blank space there.  Whatever I typed is the new file name.   Really annoying and not  really usable.  Seems like an obvious bug.

If I don't type anything and click somewhere else in the 'white space' of the window, then the current file name displays.  

This only happens with my 'external drive' so far.   I have tried renaming folders in my Home directory and it works as it should. 

I have no idea what to google or what to search in launchpad bugs.  :-/

---

### Post by kansasnoob on 2014-01-14
> **ubunt72 said:**
> What do you use for screenshots in Gnome?  I could display what I see and post it?   I cannot really see yours, sorry. ;)

It's gnome-screenshot and should show up if you open the dash and start typing screenshot. Of course it should also work if you press PrtScn on the keyboard but I know some (or most) of the keyboard shortcuts are known to be in a semi-borked state ATM :(

---

### Post by kansasnoob on 2014-01-14
> **ubunt72 said:**
> Btw, what are your operations exactly?   My exact motions are:
1) right click on file folder and click 'rename...' - immediately, the file name disappears.  
2) I can type but no output of text shows up (until I type the 'Enter'  key or click the left button of the mouse) - i.e. it's just a blank space there.  Whatever I typed is the new file name.   Really annoying and not  really usable.  Seems like an obvious bug.

If I don't type anything and click somewhere else in the 'white space' of the window, then the current file name displays.  

This only happens with my 'external drive' so far.   I have tried renaming folders in my Home directory and it works as it should. 

I have no idea what to google or what to search in launchpad bugs.  :-/

OK I had seen that! I thought it had been fixed along with this:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961)

Please give me several hours to follow-up ................ it may be tomorrow because I'm literally cleaning up a bunch of crap (cattle pens  + melting snow = a mess) , but I know what you're talking about.

I'll probably need to start with a fresh install of Ubuntu GNOME because I've dinked around so much with my current installs they may no longer be truly representative of the "current state" :D

---

### Post by ubunt72 on 2014-01-14
> **kansasnoob said:**
> It's gnome-screenshot and should show up if you open the dash and start typing screenshot. Of course it should also work if you press PrtScn on the keyboard but I know some (or most) of the keyboard shortcuts are known to be in a semi-borked state ATM :(

[[img]http://s8.postimg.org/hxk3g8rmp/renaming2.jpg[/img]](http://postimg.org/image/hxk3g8rmp/)

---

### Post by kansasnoob on 2014-01-14
> **ubunt72 said:**
> [[img]http://s8.postimg.org/hxk3g8rmp/renaming2.jpg[/img]](http://postimg.org/image/hxk3g8rmp/)

Yes, I had seen that. Let me follow up with a fresh install :D

We'll nail it down. BTW next week will be Alpha 2 testing week for Ubuntu GNOME.

---

### Post by kansasnoob on 2014-01-15
I've been trying very hard to reproduce that file renaming issue w/o luck :(

```
lance@lance-desktop:~$ sudo apt-cache show nautilus
[sudo] password for lance: 
Package: nautilus
Priority: optional
Section: gnome[COLOR="#FF0000"][/COLOR]
Installed-Size: 4048
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Josselin Mouette <joss@debian.org>
Architecture: amd64
**[COLOR="#FF0000"]Version: 1:3.8.2-0ubuntu8[/COLOR]**
Replaces: nautilus-data (<< 1:3.2.1-2ubuntu1), nautilus-sendto
Depends: libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbusmenu-glib4 (>= 0.4.2), libexempi3 (>= 2.2.0), libexif12, libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.25.2), libglib2.0-0 (>= 2.37.3), libgnome-desktop-3-7 (>= 3.2.0), libgtk-3-0 (>= 3.7.10), libnautilus-extension1a (>= 1:2.91), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libunity9 (>= 3.8.4), libx11-6, libxml2 (>= 2.7.4), libzeitgeist-1.0-1 (>= 0.3.14), session-migration, nautilus-data (>= 1:3.8), nautilus-data (<< 1:3.9), shared-mime-info (>= 0.50), desktop-file-utils (>= 0.7), gvfs (>= 1.3.2), libglib2.0-data, gsettings-desktop-schemas
Recommends: eject, brasero (>= 2.26), librsvg2-common, gvfs-backends
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs, gnome-sushi
Breaks: gnome-bluetooth (<< 3.0), gnome-session (<< 2.28), gnome-volume-manager (<< 2.24), nautilus-sendto-empathy (<< 3.0), rhythmbox (<< 0.12)
Filename: pool/main/n/nautilus/nautilus_3.8.2-0ubuntu8_amd64.deb
Size: 484266
MD5sum: 3090546e30789b0f3860a2cc69463b5f
SHA1: b16654c40be1b444ca78e3c43700d6da06bac81e
SHA256: 6de92bf3e5adc8673fa988e3fbda44b069ec84442132dafa65bd2dee7bb8f27f
Description-en: file manager and graphical shell for GNOME
 Nautilus is the official file manager for the GNOME desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the GNOME
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
Description-md5: 007268d365c98355ef914766c16ee43f
Homepage: http://www.gnome.org/projects/nautilus/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop

```

So please post the output of:

```
sudo apt-cache show nautilus
```

And if you don't mind include the name of the file/folder you're trying to rename. If it contains personal info I can understand why you might not want to include the full file name, but at least include the file type. Or if it's a folder please include the file types inside the folder.

---

### Post by xc3RnbFO8P on 2014-01-15
No problem here:

```
sudo apt-cache show nautilus
[sudo] password for rig: 
Package: nautilus
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1622
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: amd64
Version: 1:3.10.1-0ubuntu1~trusty1
Replaces: nautilus-data (<< 1:3.2.1-2ubuntu1), nautilus-sendto
Depends: libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbusmenu-glib4 (>= 0.4.2), libexempi3 (>= 2.2.0), libexif12, libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgnome-desktop-3-7 (>= 3.2.0), libgtk-3-0 (>= 3.9.12), libnautilus-extension1a (>= 1:2.91), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libunity9 (>= 3.8.4), libx11-6, libxml2 (>= 2.7.4), libzeitgeist-1.0-1 (>= 0.3.14), session-migration, nautilus-data (>= 1:3.10), nautilus-data (<< 1:3.11), shared-mime-info (>= 0.50), desktop-file-utils (>= 0.7), gvfs (>= 1.3.2), libglib2.0-data, gsettings-desktop-schemas
Recommends: eject, brasero (>= 2.26), librsvg2-common, gvfs-backends
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs, gnome-sushi
Breaks: gnome-bluetooth (<< 3.0), gnome-session (<< 2.28), gnome-volume-manager (<< 2.24), nautilus-sendto-empathy (<< 3.0), rhythmbox (<< 0.12)
Conffiles:
 /etc/xdg/autostart/nautilus-autostart.desktop 132571316e477d7e4a822a6eb985102a
Description-en: file manager and graphical shell for GNOME
 Nautilus is the official file manager for the GNOME desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the GNOME
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
Description-md5: 007268d365c98355ef914766c16ee43f
Homepage: http://www.gnome.org/projects/nautilus/
Original-Maintainer: Josselin Mouette <joss@debian.org>

Package: nautilus
Priority: optional
Section: gnome
Installed-Size: 4048
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Josselin Mouette <joss@debian.org>
Architecture: amd64
Version: 1:3.8.2-0ubuntu8
Replaces: nautilus-data (<< 1:3.2.1-2ubuntu1), nautilus-sendto
Depends: libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbusmenu-glib4 (>= 0.4.2), libexempi3 (>= 2.2.0), libexif12, libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.25.2), libglib2.0-0 (>= 2.37.3), libgnome-desktop-3-7 (>= 3.2.0), libgtk-3-0 (>= 3.7.10), libnautilus-extension1a (>= 1:2.91), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libunity9 (>= 3.8.4), libx11-6, libxml2 (>= 2.7.4), libzeitgeist-1.0-1 (>= 0.3.14), session-migration, nautilus-data (>= 1:3.8), nautilus-data (<< 1:3.9), shared-mime-info (>= 0.50), desktop-file-utils (>= 0.7), gvfs (>= 1.3.2), libglib2.0-data, gsettings-desktop-schemas
Recommends: eject, brasero (>= 2.26), librsvg2-common, gvfs-backends
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs, gnome-sushi
Breaks: gnome-bluetooth (<< 3.0), gnome-session (<< 2.28), gnome-volume-manager (<< 2.24), nautilus-sendto-empathy (<< 3.0), rhythmbox (<< 0.12)
Filename: pool/main/n/nautilus/nautilus_3.8.2-0ubuntu8_amd64.deb
Size: 484266
MD5sum: 3090546e30789b0f3860a2cc69463b5f
SHA1: b16654c40be1b444ca78e3c43700d6da06bac81e
SHA256: 6de92bf3e5adc8673fa988e3fbda44b069ec84442132dafa65bd2dee7bb8f27f
Description-en: file manager and graphical shell for GNOME
 Nautilus is the official file manager for the GNOME desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the GNOME
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
Description-md5: 007268d365c98355ef914766c16ee43f
Homepage: http://www.gnome.org/projects/nautilus/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop

```



[[img]http://farm4.staticflickr.com/3820/11969892244_415a5cf888_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/11969892244/)
[nautilus](http://www.flickr.com/photos/96052779@N07/11969892244/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by ubunt72 on 2014-01-15
```
Package: nautilus
Priority: optional
Section: gnome
Installed-Size: 4048
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Josselin Mouette <joss@debian.org>
Architecture: amd64
Version: 1:3.8.2-0ubuntu8
Replaces: nautilus-data (<< 1:3.2.1-2ubuntu1), nautilus-sendto
Depends: libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbusmenu-glib4 (>= 0.4.2), libexempi3 (>= 2.2.0), libexif12, libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.25.2), libglib2.0-0 (>= 2.37.3), libgnome-desktop-3-7 (>= 3.2.0), libgtk-3-0 (>= 3.7.10), libnautilus-extension1a (>= 1:2.91), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libunity9 (>= 3.8.4), libx11-6, libxml2 (>= 2.7.4), libzeitgeist-1.0-1 (>= 0.3.14), session-migration, nautilus-data (>= 1:3.8), nautilus-data (<< 1:3.9), shared-mime-info (>= 0.50), desktop-file-utils (>= 0.7), gvfs (>= 1.3.2), libglib2.0-data, gsettings-desktop-schemas
Recommends: eject, brasero (>= 2.26), librsvg2-common, gvfs-backends
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs, gnome-sushi
Breaks: gnome-bluetooth (<< 3.0), gnome-session (<< 2.28), gnome-volume-manager (<< 2.24), nautilus-sendto-empathy (<< 3.0), rhythmbox (<< 0.12)
Filename: pool/main/n/nautilus/nautilus_3.8.2-0ubuntu8_amd64.deb
Size: 484266
MD5sum: 3090546e30789b0f3860a2cc69463b5f
SHA1: b16654c40be1b444ca78e3c43700d6da06bac81e
SHA256: 6de92bf3e5adc8673fa988e3fbda44b069ec84442132dafa65bd2dee7bb8f27f
Description-en: file manager and graphical shell for GNOME
 Nautilus is the official file manager for the GNOME desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the GNOME
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
Description-md5: 007268d365c98355ef914766c16ee43f
Homepage: http://www.gnome.org/projects/nautilus/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop

Package: nautilus
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 4052
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: amd64
Version: 1:3.8.2-0ubuntu4
Replaces: nautilus-data (<< 1:3.2.1-2ubuntu1), nautilus-sendto
Depends: libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbusmenu-glib4 (>= 0.4.2), libexempi3 (>= 2.2.0), libexif12, libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.25.2), libglib2.0-0 (>= 2.37.3), libgnome-desktop-3-7 (>= 3.2.0), libgtk-3-0 (>= 3.7.10), libnautilus-extension1a (>= 1:2.91), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libunity9 (>= 3.8.4), libx11-6, libxml2 (>= 2.7.4), libzeitgeist-1.0-1 (>= 0.3.14), session-migration, nautilus-data (>= 1:3.8), nautilus-data (<< 1:3.9), shared-mime-info (>= 0.50), desktop-file-utils (>= 0.7), gvfs (>= 1.3.2), libglib2.0-data, gsettings-desktop-schemas
Recommends: eject, brasero (>= 2.26), librsvg2-common, gvfs-backends
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs, gnome-sushi
Breaks: gnome-bluetooth (<< 3.0), gnome-session (<< 2.28), gnome-volume-manager (<< 2.24), nautilus-sendto-empathy (<< 3.0), rhythmbox (<< 0.12)
Conffiles:
 /etc/xdg/autostart/nautilus-autostart.desktop 132571316e477d7e4a822a6eb985102a
Description-en: file manager and graphical shell for GNOME
 Nautilus is the official file manager for the GNOME desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the GNOME
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
Description-md5: 007268d365c98355ef914766c16ee43f
Homepage: http://www.gnome.org/projects/nautilus/
Original-Maintainer: Josselin Mouette <joss@debian.org>

```
It's not at the latest, then?   Anyway, it doesn't matter what folder it is.  I can create a folder or change any current folder, it has the same operation in which the text disappears (there's just blank space below).  Are you duplicating the same situation exactly - using an external drive connected via eSATA?   Maybe it doesn't matter how it's connected but to just make sure everything is as similar as possible?

Let me say it another way.   I go to the external drive (window) with nautilus.   I right click and move the mouse pointer down until I get to 'New Folder.'   I click it.   It has blank space underneath a file folder icon.   This also occurs when clicking to 'Rename' any current folder in the window (filename on the drive).

---

### Post by ubunt72 on 2014-01-15
Hey, I upgraded it to Version: 1:3.8.2-0ubuntu8 and now it's working properly!   Sorry, guys!   I should have upgraded to the latest that is in the repo (and if that didn't work, then the latest via changing the ppa or source?).   I thought I already had the latest... strange.

---

### Post by kansasnoob on 2014-01-16
> **ubunt72 said:**
> Hey, I upgraded it to Version: 1:3.8.2-0ubuntu8 and now it's working properly!   Sorry, guys!   I should have upgraded to the latest that is in the repo (and if that didn't work, then the latest via changing the ppa or source?).   I thought I already had the latest... strange.

So is this solved?

---

### Post by mc4man on 2014-01-16
It was fixed in 1:3.8.2-0ubuntu5 so when using 1:3.8.2-0ubuntu4 it was broken 
Better to use apt-cache policy instead of apt-cache show (neither needs sudo

---

### Post by ubunt72 on 2014-01-16
> **mc4man said:**
> It was fixed in 1:3.8.2-0ubuntu5 so when using 1:3.8.2-0ubuntu4 it was broken 
Better to use apt-cache policy instead of apt-cache show (neither needs sudo
That's interesting.   Thanks for the info.   I wouldn't have thought it'd be broken with seemingly only subtle changes to the version number?   But, that shows to consider switching to a different version even if it doesn't look like it changed much.

Should I mark the thread as solved?   I should be okay with this version then? :)

---

### Post by mc4man on 2014-01-16
> **ubunt72 said:**
> That's interesting.   Thanks for the info.   I wouldn't have thought it'd be broken with seemingly only subtle changes to the version number?   But, that shows to consider switching to a different version even if it doesn't look like it changed much.

Should I mark the thread as solved?   I should be okay with this version then? :)
You can mark as solved, shouldn't be an issue going forward.
This issue was caused by the new gtk (3.10) affecting the current nautilus (3.8) being used. In this case the bug report linked in post 3 shows "fix released' When you see that scroll down the report page, there will usually be a comment stating what package it was fixed in, ect. - ex.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961/comments/7](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1266961/comments/7)

---

### Post by Baldrick_NZ on 2014-01-17
> **ubunt72 said:**
> I read that Ubuntu Trusty has a lot of bugs and with Gnome, probably as well?

I think I found one.   I cannot easily rename files (on my other - 'external' drive).   When I try to rename a file, the name goes 'blank' (white) and I cannot see anything that I type.  Wtheck?

Is this a well known bug?   The other thing that seems to happen is that another file adjacent to it gets renamed instead.   This is really annoying.   I had to boot up another OS to rename the files.

Edit:  P.S.  It only happens with my external drive.   I don't have this problem with other distros I've used meaning this is a new problem.  But, no matter what I did, the same issue occurs.   If I try renaming a file in my home directory or some place on the OS drive, it works as it should.   I have no idea what to even google if this is a bug in trusty.   Or maybe it's a new bug?   It's definitely a bug - it reoccurs each time.


Odd, I have the very same prob with Ubuntu Gnome 13.10. For me, as a work around, I drag the file to the desktop and rename then drag it back. Very strange bug indeed.

---

### Post by Toni Ridwan Affandi on 2014-05-07
I suspect there are  still not serious but effective and annoying bug in (Gnome?) Ubuntu 14.04

I thing it is about Windows (content, appearance)  management. I have two notebooks, one Asus A43E with i3 Intel, new one  Lenovo G405S with AMD A8 and GPU. The former one with Ubuntu 13.10  crashed unbootable after frozen after trying for a few hours for  multiple monitor. Hence both have fresh install of Ubuntu 14.04 since  release date. Always updated whenever available.

On both computer I encounter these bugs:

1.  LibreOffice Calc unfocused window's content not refresh properly when  scrolled with mouse. Complete detail and screenshot here:

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1311980](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1311980)

2. Windows just vanished with ununderstandable reason. It is annoying (since hampering productivity), embarassing (if you experience it in front of non Ubuntu public).

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1311983](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1311983)

It  is affecting LIBREOFFICE, THUNDERBIRD AND FIREFOX (Core apps I would say). Happening A FEW TIMES ON DAILY BASIS. I can not determine (yet), what action leads to this  problem, so I can only make screen shot to show my points. In LibreOffice is happens more likely if you have two open windows. Opening (new) third window can lead to some window grabbing problem. I am sure this is not a memory (room) problem, because not having this kind of problem in 13.10 and since 9.04.


If anybody gives a (hard) try and can confirm these errors please (upvote?) my bug reports, that it is affected you as user too. I do hope this bug on important apps of Ubuntu 14.04 will soon get ironed out. Thank you everybody.

---

### Post by cariboo on 2014-05-08
@Toni Ridwan Affandi, I guess you didn't see the blue announcement at the top of the page, thread closed.

---

