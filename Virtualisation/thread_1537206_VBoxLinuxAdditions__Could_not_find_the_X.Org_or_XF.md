---
title: "VBoxLinuxAdditions : Could not find the X.Org or XFree86"
date: 2010-07-23
forum: Virtualisation
---

### Post by steph33560 on 2010-07-23
Hi,

I've got a windows host, running an ubuntu (ubuntu server amd64) O/S with Virtualbox.

To share folders from win32 host, I must install VBoxLinuxAdditions to be able to share my folders using vboxfs.
So, when Virtuabox Addons CDROM virtually mounted :
> $ sudo sh VBoxLinuxAdditions-amd64.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 3.2.6 Guest Additions for Linux.........
VirtualBox Guest Additions installer
Removing installed version 3.2.6 of VirtualBox Guest Additions...
tar: Taille de l'enregistrement = 8 blocs
Building the VirtualBox Guest Additions kernel modules
Building the main Guest Additions module ...done.
Building the shared folder support module ...done.
Building the OpenGL support module ...done.
Doing non-kernel setup of the Guest Additions ...done.
Starting the VirtualBox Guest Additions ...done.
Installing the Window System drivers ...fail!
(Could not find the X.Org or XFree86 Window System.)Here is the problem : my linux guest does not have any X environment :(

So, I'd look at [Xming X Server]("http://www.straightrunning.com/XmingNotes/changes.php"), tying in putty to use "enable X11 forwarding" to 127.0.0.1:0.0 on windows host... does not work yet ](*,)

Any idea to make it simpler ?

Thanks :)




[URL="http://www.straightrunning.com/XmingNotes/changes.php"]
[/URL]

---

### Post by TheFu on 2010-07-23
Why not just load the ubuntu-desktop metapackage into your server installation? You don't have to use the full-gnome package, you could just install a minimal window manager and the dependencies should pull X11 in for you.  Perhaps LXDE or XFCE metapackages would be better? I dunno.

$ sudo apt-get install lxde-core lxde

Should do it.  That would remove the need to use Xming, which was very buggy the last time I used it.

If you really want to remotely connect via X/Windows, you'll want to load the x11-client packages (not the server(s) or the fonts which will run on the desktop you use to remotely connect). If you are outside your VM LAN, using `ssh -X` would be a secure method to have all the X/Windows traffic tunneled inside an ssh connection.

---

