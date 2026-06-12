---
title: "rdesktop/xrdp: error - problem connecting (to 127.0.0.1 5910)"
date: 2006-08-24
forum: Server Platforms
---

### Post by mikko.ostlund on 2006-08-24
Hi!

Abstract: I have installed xrdp in Fedora Core 5, but fail to connect to
it with "rdesktop localhost". I'm hoping someone can help me to get it
working.

Details about my system:
   * "uname -a":    Linux desktop 2.6.17-1.2174_FC5 #1 Tue Aug 8 15:30:55 \
                    EDT 2006 i686 i686 i386 GNU/Linux
   * Gnome version: 2.4.13
       Distributor: Red Hat, Inc
        Build date: 08/02/2006
   * rdesktop version: 1.4.1
   * xrdp version: 0.3.1
   * Firewall: "Disabled" (in dialog "System"->"Administration"->
                  ->"Security Level and Firewall")
   * SELinux: "Disabled" (in the same dialog as the firewall above)

Details about how I installed xrdp:
1. I browsed to
    http://sourceforge.net/project/showfiles.php?group_id=112022&package_id=195021&release_id=435591"
   and downloaded "xrdp-0.3.1.tar.gz".
2. I unpzipped it with "gunzip xrdp-0.3.1.tar.gz".
3. I untared it with "tar xvf xrdp-0.3.1.tar".
4. I entered the xrdp-0.3.1 directory with "cd xrdp-0.3.1".
5. I built the whole project by running "make" in the xrdp-0.3.1 directory.
6. I switched to the root user with "su".
7. I installed everything with "make install".

Details about how I ran it and how the problem occurred:
1. I started xrdp by running, still logged in as root, "/usr/local/xrdp/xrdpstart.sh".
2. In another terminal window, logged in as a normal user, I ran "rdesktop localhost".
3. A window, titled "rdesktop - localhost", appeared.
4. Inside the "rdesktop - localhost" window a subwindow appeared. The title of the subwindow was "Connection Log".
5. In the subwindow, the following text appeared:
   "started connecting
    connecting to sesman
    sending login info to sesman
    receiving sesman header
    receiving sesman data
    sesman started a session
    connecting to 127.0.0.1 5910
    error - problem connecting"
6. End of story; nothing further happened.

Contents of file "/usr/local/xrdp/sesman.log":
    [20060824-16:27:30] [DEBUG] starting sesman with pid 3727
    [20060824-16:27:30] [DEBUG] listening...
    [20060824-16:27:39] [DEBUG] granted TS access to user mikko
    [20060824-16:27:39] [DEBUG] starting Xvnc session...
    [20060824-16:27:41] [DEBUG] session 3730 - user mikko - terminated

The following files contained nothing (size 0 bytes):
    "/usr/local/xrdp/sesman.boot.log"
    "/usr/local/xrdp/xrdp.boot.log"

The user "hela" of this forum, seems to have got around the problem by
installing "kubuntu-desktop" (refer to the posting
[http://www.ubuntuforums.org/showthread.php?t=239616)](http://www.ubuntuforums.org/showthread.php?t=239616)), but I would like to
see the problem actually solved for the Gnome desktop.

Appreciating any attempts to shed some light on this,

   Mikko
   Stockholm, Sweden

---

### Post by mrnumnuts on 2006-10-05
I don't know if you found the answer to this or not, but I needed this last night. 

Edit /usr/local/xrdp/startwm.sh

the following is commented out in the file:
# gnome
#if [ "'which gnome-session'" != "" ]; then
#  gnome-session
#  exit 0
#fi

I left this alone and added this to the begining of the file:

if [ "'which gnome-session'" != "" ]; then
  dbus-launch gnome-session
  exit 0
fi

Thanks,
Robert

---

### Post by mikko.ostlund on 2006-10-06
mrnumnuts,

Thanks! But no; I get the same result when trying with
your "dbus-launch" suggestion as when I tried it as
described in my previous posting. I just get
"error - problem connecting" in the rdesktop window.
Thanks for trying anyway,

Regards,

   Mikko

---

### Post by Sunon on 2006-11-16
I was having some of the same issues with xrdp as you seem to have, but I finally figured out the issue.  My issue had to do firstly with installing vnc4server and secondly with Xvnc not being able to see my fonts.

So first, if you don't have vnc installed, do that.  Xrdp doesn't have its own vnc server, it relies on Xvnc.

Second, if you installed vnc4server check that it can locate your fonts by running "Xvnc :1".  It will tell you right away if it cannot locate your fonts.  The easiest fix for this is to symlink ("ln -s") your fonts folder to where it is looking for your fonts.  Xvnc will bomb out if it cannot find the fonts and as far as sesman knows the session was terminated.

---

### Post by Robert Citek on 2006-11-29
> **Sunon said:**
> Second, if you installed vnc4server check that it can locate your fonts by running "Xvnc :1".  It will tell you right away if it cannot locate your fonts.  The easiest fix for this is to symlink ("ln -s") your fonts folder to where it is looking for your fonts.

If I start Xvnc, I get this:

```

$ Xvnc :100
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
29/11/06 12:02:29 Xvnc version 3.3.7 - built Feb 20 2006 12:05:53
29/11/06 12:02:29 Copyright (C) 2002-2003 RealVNC Ltd.
29/11/06 12:02:29 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
29/11/06 12:02:29 All Rights Reserved.
29/11/06 12:02:29 See http://www.realvnc.com for information on VNC
29/11/06 12:02:29 Desktop name 'x11' (rwcitek:100)
29/11/06 12:02:29 Protocol version supported 3.3
29/11/06 12:02:29 Listening for VNC connections on TCP port 6000
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'

```

So which folder should I be softlinking to?  Or do I need to install some font package?  If so, which one?

Regards,
- Robert

---

### Post by Sunon on 2006-11-30
Robert,
the vnc server is looking for your fonts in this base directory: "'/usr/X11R6/lib/X11/fonts".  What you want to do is locate where this directory is on your system (do a "locate fonts" command)  when you see the one that contains 100dpi, 75dpi, misc, etc. then you have found where your fonts are.  I don't remember for sure the path but I can post it later when I can look for it.

so the command you want is "ln -s /path/found/in/locate /usr/X11R6/lib/X11/fonts"

but you may have to create some of the new path IE "mkdir /usr/X11R6/lib/X11"

But you won't have to create the "fonts" directory, that is what the link command is for.

---

### Post by Sunon on 2006-12-06
here are the commands that I ran to link my fonts folder (this was an edgy install):

su
cd /usr/share/X11/
ln -s /usr/share/fonts/X11 fonts

so MY fonts are at /usr/share/fonts/X11

and Xvnc wanted to see them at /usr/share/X11/fonts

hope this clears up any confusion

---

### Post by jhenager on 2007-11-24
You will want to use sudo with the above command.
Even with this, I cannot even connect to localhost.
jeff@jeff-desktop:~$ vncviewer 

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Sat Nov 24 11:02:48 2007
 main:        unable to connect to host: Connection refused (111)

---

### Post by alisonnic on 2008-01-25
Has anyone solved this problem??

I'm running Gutsy.  I've built and installed xrdp, and got it running.  I commented out the kde section in startwm.sh and added these lines before the existing gnome lines:

```
if [ "'which gnome-session'" != "" ]; then
dbus-launch gnome-session
exit 0
fi
```

I've also installed the vnc4server package, even though the current release of xrdp includes a lightweight vnc server.  (It doesn't say how to install or start it, though.)

Anyway, after installing vnc4serve, if I run it I get this:

> alison@Auburn:/usr/local/xrdp$ Xvnc :1 &

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Fri Jan 25 20:48:36 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!


Searching for these font libraries is largely unsuccessful:

> alison@Auburn:/usr/local/xrdp$ locate fonts | grep TTF
alison@Auburn:/usr/local/xrdp$ locate fonts | grep QTF
alison@Auburn:/usr/local/xrdp$ locate fonts | grep CID
/var/lib/defoma/gs.d/dirs/fonts/CIDFnmap

But, hoping these missing fonts aren't crucial, I tried to log in anyway.  I get the same dreaded sequence as everyone else seems to be getting:

> connecting to sesman ip 127.0.0.1 port 3350
sesman connect ok
sending login info to sesman
login successful for display 10
started connecting
connecting to 127.0.0.1 5910
error - problem connecting

Note that the above log occurs when connecting using Remote Desktop Connection from a Windows XP box, but I get exactly  the same messages when I attempt to connect from a Remotedesktop Client session on the local (Ubuntu) box.

Here's the contents of the sesman.log section for the RDC login from Windows XP:

> [20080125-20:54:05] [INFO ] scp thread on sck 5 started successfully
[20080125-20:54:05] [INFO ] granted TS access to user alison
[20080125-20:54:05] [INFO ] starting Xvnc session...
[20080125-20:54:05] [INFO ] starting sessvc - xpid=12155 - wmpid=12154
[20080125-20:54:06] [INFO ] session 12153 - user alison - terminated

And for the login from Remotedesktop Client on the local machine:

> [20080125-20:57:21] [INFO ] scp thread on sck 5 started successfully
[20080125-20:57:21] [INFO ] granted TS access to user alison
[20080125-20:57:21] [INFO ] starting Xvnc session...
[20080125-20:57:21] [INFO ] starting sessvc - xpid=12170 - wmpid=12169
[20080125-20:57:22] [INFO ] session 12168 - user alison - terminated

Any ideas? 

Has *anyone* out there gotten Xrdp to work on Gutsy?

---

