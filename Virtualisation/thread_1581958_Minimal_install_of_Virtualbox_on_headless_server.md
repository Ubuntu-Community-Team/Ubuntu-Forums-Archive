---
title: "Minimal install of Virtualbox on headless server"
date: 2010-09-25
forum: Virtualisation
---

### Post by memilanuk on 2010-09-25
Hello all,

I am working at installing Virtualbox on an older PC that I have pressed into service as a headless server for educational purposes.  

A couple questions, if you don't mind:

1)  Since I'm installing this on a headless machine (Ubuntu 10.04.1 server installation), and the majority of the guests are probably going to be headless as well (though I might try playing with RDP just for giggles)... how much do I really need all the qt libraries and umpteen X11 related packages that seem to be dependencies (not just 'suggested' or 'recommended') for a headless installation?

2)  If I'm running primarily headless guests, USB shouldn't be much of an issue.  Would you recommend the OSE or the PUEL version?  I've always used the PUEL version on Windows, as I wanted/needed the added features at times.

3)  Any ideas whats up with the virtualbox.org site?  It's been intermittently unavailable over the last day or so, which seems a bit odd.  Makes the entries in my /etc/apt/sources.list not play nice when they can't check in...

Monte

---

### Post by CharlesA on 2010-09-25
I'd go with PUEL for VRPD and whatnot. Makes it (fairly) easy to install the VM, since you don't exactly have remote access during an install.

Also: You do need the libraries and whatnot, since VBox is dependent on them.

---

### Post by memilanuk on 2010-09-25
Any thoughts on benefits of rdp vs vnc?  

Apparently I've chosen an inconvenient time to start playing with this stuff; virtualbox.org's website apparently suffered some hardware failure and is down for a day or two - which takes with it the download, the manual, and the deb repository :(

I've been playing with a couple different installs today; Debian 5.06 and Ubuntu 10.04.1, installing the OSE version in both (used backports for Debian to get a remotely recent version)... in both not only was my user not added to the vboxusers group (no biggie), there was no vboxusers group to begin with (little bit bigger deal...).  No USB (don't care), apparently no rdp (kinda sucks for doing installs)... but lo and behold... VNC seems to work just fine for connecting to the machines and controlling the installation process inside the VM.  So far, anyways.

Monte

---

### Post by CharlesA on 2010-09-25
How did you use VNC? I was under the impression that you need to have the closed source version to use VRPD to connect, but maybe I am thinking of something else.

Were you running a GUI and had the VMs running on it?

---

### Post by memilanuk on 2010-09-25
No... just plain vanilla server installs, nothing added but screen & ssh... and all the cruft that virtualbox pulls in with it.

Started it with a command like so (via PuTTY/ssh)...

```
monte@vbox-server:~$ vboxheadless --startvm test -n -m 5902 -o foobarbaz
Oracle VM VirtualBox Headless Interface 3.2.4_OSE
(C) 2008-2010 Oracle Corporation
All rights reserved.

25/09/2010 19:33:23 Listening for VNC connections on TCP port 5902
Set framebuffer: buffer=-1235505144 w=800 h=600 bpp=32
Set framebuffer: buffer=-1282314240 w=640 h=480 bpp=32
Set framebuffer: buffer=-1235972088 w=720 h=400 bpp=32
Set framebuffer: buffer=-1234817016 w=640 h=480 bpp=32
```


And then opened up a TightVNC client and connected to the hosts ip address @ port 5902, and supplied the required password (foobarbaz).  Voila! connected to the VM booting from a CentOS net install iso ;)

---

### Post by CharlesA on 2010-09-25
Interesting. I didn't know VirtualBox could do VNC.

I wonder if that's specifically for the open source version, since the only options I have are:

```
VBoxHeadless: error: Unknown option: '-n'
Usage:
   -s, -startvm, --startvm <name|uuid>   Start given VM (required argument)
   -v, -vrdp, --vrdp on|off|config       Enable (default) or disable the VRDP
                                         server or don't change the setting
   -p, -vrdpport, --vrdpport <ports>     Comma-separated list of ports the VRDP
                                         server can bind to. Use a dash between
                                         two port numbers to specify a range
   -a, -vrdpaddress, --vrdpaddress <ip>  Interface IP the VRDP will bind to
   -c, -capture, --capture               Record the VM screen output to a file
   -w, --width                           Frame width when recording
   -h, --height                          Frame height when recording
   -r, --bitrate                         Recording bit rate when recording
   -f, --filename                        File name when recording.  The codec
                                         used will be chosen based on the
                                         file extension

```

---

### Post by memilanuk on 2010-09-25
Neither did I... a quick text search through the PDF manual for 'VNC' returns nothing.  Searching in the forums returns nothing either unless you search for '5900'...

I found it by accident when I was having problems connecting to the RDP port of the VM, and ran 'vboxheadless --help' to check the options:

```

monte@vbox-server:~$ vboxheadless --help
Oracle VM VirtualBox Headless Interface 3.2.4_OSE
(C) 2008-2010 Oracle Corporation
All rights reserved.

Usage:
   -s, -startvm, --startvm <name|uuid>   Start given VM (required argument)
   [COLOR="Blue"]-n, --vnc                             Enable the built in VNC server
   -m, --vncport <port>                  TCP port number to use for the VNC server
   -o, --vncpass <pw>                    Set the VNC server password[/COLOR]
   -c, -capture, --capture               Record the VM screen output to a file
   -w, --width                           Frame width when recording
   -h, --height                          Frame height when recording
   -r, --bitrate                         Recording bit rate when recording
   -f, --filename                        File name when recording.  The codec
                                         used will be chosen based on the
                                         file extension


```

---

### Post by CharlesA on 2010-09-25
Interesting. Learn something new every day. :)

Thanks. I'll stick to the closed source version of VBox, since I've been running [phpvirtualbox]("http://code.google.com/p/phpvirtualbox/") for a while now instead of forwarding the VBox GUI over SSH.

It's still in beta but it works very well for me. :)

---

### Post by memilanuk on 2010-09-25
I hadn't made it quite that far along just yet... I was considering installing vboxtool so I could get more multiple VMs running instead of starting each one inside another screen window.  I also saw vboxremote mentioned in their forums... any idea how the two compare?

Granted... mine is buried inside my household LAN behind a router w/ firewall... but this is a little worrisome:

> This is intended to be run on a local network or intranet where access to the phpVirtualBox script is limited by network connectivity. The script performs no front-end user authentication of any kind. [COLOR="Red"]In other words, anyone who has access to this script on your web server may administer your VirtualBox installation[/COLOR]

---

### Post by CharlesA on 2010-09-26
Indeed. It had me worried at the start, but I just ended up using .htaccess to password protect that area and use HTTPS instead of normal HTTP.

If someone doesn't know the password, they can't get in.

Granted, the other problem is that there is no authentication for VRDP, but I have that limited to just my desktop, and none of the machines are logged in to the console.

It's probably not as secure as say, making everything listen on lo and tunnelling them over SSH, but it works for me.

---

### Post by memilanuk on 2010-09-28
Charles,

Since Virtualbox got their site back up and running to where I could actually go compare [the closed-source and open-source version descriptions]("http://www.virtualbox.org/wiki/Editions")... thought I should mention that apparently the VNC option is only in the OSE version, since it doesn't have RDP support (or USB).

Edited to add: ...and apparently not compiled into the OSE version that ships with Ubuntu as it doesn't work on 10.04.1 LTS with VB 3.1.6 OSE installed from the repos:

```

monte@vbox-server:~$ vboxheadless --startvm "Ubuntu Server - Test" -n
Sun VirtualBox Headless Interface 3.1.6_OSE
(C) 2008-2010 Sun Microsystems, Inc.
All rights reserved.

Unknown option: -n

Usage:
   -s, -startvm, --startvm <name|uuid>   Start given VM (required argument)
   -c, -capture, --capture               Record the VM screen output to a file
   -w, --width                           Frame width when recording
   -h, --height                          Frame height when recording
   -r, --bitrate                         Recording bit rate when recording
   -f, --filename                        File name when recording.  The codec
                                         used will be chosen based on the
                                         file extension

monte@vbox-server:~$

```

Monte

---

### Post by CharlesA on 2010-09-28
Interesting find.

Thanks.

---

### Post by memilanuk on 2010-09-28
It does beg the question... if RDP is not supported by Virtualbox in their OSE version, and the Ubuntu version doesn't appear to have VNC support compiled in... how in the heck is a person supposed to access a VM running in Virtualbox  on a headless Ubuntu server?!?

Not everyone has the hardware to run KVM and the like, and not everyone runs Virtualbox only on the desktop...

---

### Post by CharlesA on 2010-09-28
> **memilanuk said:**
> It does beg the question... if RDP is not supported by Virtualbox in their OSE version, and the Ubuntu version doesn't appear to have VNC support compiled in... how in the heck is a person supposed to access a VM running in Virtualbox  on a headless Ubuntu server?!?

Not everyone has the hardware to run KVM and the like, and not everyone runs Virtualbox only on the desktop...
I know what you mean. I've always just used the non-free version. I just wonder why VNC was removed from the OSE.

*shrug*

---

### Post by memilanuk on 2010-09-28
Is RDP really any safer than VNC (no idea, just asking)?  I know VNC seems to be in increasingly bad favor due to people running it over un-encrypted connections and getting hacked as a result... but seems like completely eliminating it from the OSE version in the Ubuntu repositories instead of leaving it as an option for the sysadmin to use is a bit extreme...

---

### Post by CharlesA on 2010-09-28
I think RDP is encrypted, but if you have null authentication, then anyone can connect.

The same thing can be said for VNC, except it made you set a password (in your case at least).

In any case, if I am working remotely and need to access the VRDP, I just tunnel it over SSH and set the firewall to only allow it from localhost and one other ip address.

---

### Post by memilanuk on 2010-09-28
<sigh>guess I get to uninstall the OSE version and install the PUEL version.  Highly annoying though... I was kind of happy because the OSE version in the repos only pulled in about half the extraneous graphics libraries that the 'full' version does.

---

### Post by CharlesA on 2010-09-28
> **memilanuk said:**
> <sigh>guess I get to uninstall the OSE version and install the PUEL version.  Highly annoying though... I was kind of happy because the OSE version in the repos only pulled in about half the extraneous graphics libraries that the 'full' version does.

Good luck! At least there are options. :)

---

### Post by jdpipe on 2011-03-08
For what it's worth, VirtualBox doesn't support VNC on the plain vanilla install on Ubuntu 10.04.2:

john@xxxxxx:/srv/svn$ vboxheadless --help
Sun VirtualBox Headless Interface 3.1.6_OSE
(C) 2008-2010 Sun Microsystems, Inc.
All rights reserved.

Unknown option: --help

Usage:
   -s, -startvm, --startvm <name|uuid>   Start given VM (required argument)
   -c, -capture, --capture               Record the VM screen output to a file
   -w, --width                           Frame width when recording
   -h, --height                          Frame height when recording
   -r, --bitrate                         Recording bit rate when recording
   -f, --filename                        File name when recording.  The codec
                                         used will be chosen based on the
                                         file extension

---

