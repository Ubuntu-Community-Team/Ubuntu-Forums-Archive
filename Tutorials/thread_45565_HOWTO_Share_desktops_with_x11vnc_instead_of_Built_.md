---
title: "HOWTO: Share desktops with x11vnc instead of Built in Remote Desktop"
date: 2005-06-30
forum: Tutorials
---

### Post by intangible on 2005-06-30
This explains how to share individual logged in users desktops using x11vnc instead of the built-in "Remote Desktop" feature of Ubuntu.  The reason for this is because "vino" which is used by the "Remote Desktop" option is inadequate for a lot of people (no clipboard support), no accessible configuration options, and quite slow.

This is a decent companion to sharing a VNC -> GDM connection (both these howtos work together!) [http://www.ubuntuforums.org/showthread.php?t=42941](http://www.ubuntuforums.org/showthread.php?t=42941)

OK, we have a two step process here, getting x11vnc to run automagically on a user's login and then installing autocutsel; Autocutsel is used to make sure the VNC Clipboard gets updated from both just selecting and right-click copying.  **You do not have to install autocutsel, it just makes things work a little nicer**.

Before you do anything else, you need to enable the universe repositories: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

**Setting up x11vnc**
[list=1]
[*] Install x11vnc: **sudo apt-get install x11vnc**
[*] Set the password: **vncpasswd ~/.vnc/passwd** (vncpasswd is included with vnc-common, which is installed by default)
[*] Make it auto-start when the user logs in and show which port we're running on (useful if you run multiple vnc servers) the port will be put in **~/.vnc/port.txt**: 
[list=1]
[*]**sudo gedit /usr/local/bin/sharex11vnc** Paste in the following:
```
#!/bin/sh

x11vnc -nap -bg -many -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}"|grep -Eo "[0-9]{4}">~/.vnc/port.txt

# comment out the following if you don't want a popup telling you which port you're using.
zenity --info --text="Your VNC port is `cat ~/.vnc/port.txt`"
```
[*]**sudo chmod 755 /usr/local/bin/sharex11vnc**
[*]**System->Preferences->Sessions->Startup Programs** then click **Add** and type in **sharex11vnc**
[/list]
[/list]

**Installing autocutsel**:
[list=1]
[*] Download tar.gz from [http://www.lepton.fr/tools/autocutsel/](http://www.lepton.fr/tools/autocutsel/)
[*] Move file: **sudo mv /home/user/location/autocutsel-0.8.0.tar.gz /usr/src**
[*] Extract file: **cd /usr/src;sudo tar -xzvf autocutsel-0.8.0.tar.gz**
[*] Install packages required to compile and install autocutsel into a deb package:
[list=1]
[*] **sudo apt-get install gcc checkinstall libx11-dev libxaw8-dev** This may take a while if you don't already have gcc or the xlibs installed installed.
[*] **cd autocutsel-0.8.0**
[*] **./configure --prefix=/usr**
[*] **sudo checkinstall -y --nodoc** The resulting deb will be installed and the package will be left in the current directory
[/list]
[*] Make it auto-start when the user logs in:
**System->Preferences->Sessions->Startup Programs** then click **Add** and type in **autocutsel**
[/list]

The best VNC client for windows is UltraVNC [http://ultravnc.sf.net](http://ultravnc.sf.net) - I recommend it for all your VNC needs.

---

### Post by intangible on 2005-06-30
Once you've set this up, to have it startup for additional users: 
1. create a password as them: **vncpasswd ~/.vnc/passwd**
2. add **sharex11vnc** and **autocutsel** to thier **System->Preferences->Sessions->Startup Programs** (or thier startup scripts).

---

### Post by alinux on 2005-09-01
Great GUIDE thanks a lot!

---

### Post by one_ro on 2005-09-08
[QUOTE=intangible]This explains how to share individual logged in users desktops using x11vnc instead of the built-in "Remote Desktop" feature of Ubuntu.  The reason for this is because "vino" which is used by the "Remote Desktop" option is inadequate for a lot of people (no clipboard support), no accessible configuration options, and quite slow.
[...][/QUOTE]
Great! Now I would like to connect remotely to another Kubuntu. I also have a Kubuntu installed. How exactly do I do this?
Thx!

---

### Post by zorzeta on 2005-11-04
The same problems. None of VNC to GDM HowTo's posted in this forum by now work with CLEAN Ubuntu Breezy install. Tried all of them. 

Server seemed to work, but no connections from clients, even from localhost. The same time Remote Desktop (vivo) works just fine.

It would be nice to have guaranted to work on Breezy VNC to GDM HowTo finaly.

---

### Post by chaumurky on 2005-11-13
**libxaw8-dev **seemed to be missing but **libxaw7-dev **worked fine for me. I also needed** build-essential **on my basic 'server + xubuntu' install. Thank you.

---

### Post by talz13 on 2005-12-18
This guide is for connecting to a session that has logged in directly, and the other guide is for starting new sesssions remotely, right?

Well, what I had going on my FC3 install that I just formatted was a vnc user that would be logged in at startup (the local monitor still shows the login screen, but the user is active), all the users session programs would start up (I had azureus run on login), and I could connect to the users desktop via vnc to perform tasks and such.

Neither of these guides seems to do quite what I'm looking for.  I believe I followed this guide under FC3:
[http://www.fedoraforum.org/forum/showthread.php?t=42062](http://www.fedoraforum.org/forum/showthread.php?t=42062)
but config files and stuff are different from FC3

So any way to get a single VNC user active at boot, with his gnome session started automatically, and be able to log on from VNC or locally, like I used to have set up?




edit: didn't notice that this howto was listed under 5.04, as I'm running 5.10, but any help would still be appreciated :)

---

### Post by intangible on 2005-12-21
If you followed this guide, the only additional change you need to make is to make a specific user login at startup through gdm (just sudo gdmsetup).

Let me know if you're having problems.

---

### Post by miatapaul on 2006-01-04
This works great on my local network. I need to change the port to run on port 21. I have the port forwared on my router. I have this working under Windows running UltraVNC server using port 65557, so I connect using mywebaddress.com:65557 and it connects. From work they only have port 21 and 80 open so that is what I have to use to access my home workstation from work.

---

### Post by Schmic on 2006-01-14
Good HowTo *intangable*. i'm a 7 day linux newbie and i got it working, learnt a few things on the way as well.
Thanks to *chaumurky* for the tip on **Build-essential**, needed to install that to get autocutsel to work on my new ubuntu 5.10:) .

Now is there any chance i can get a HowTo on getting this to run inside ssh automatically(or any other security so its not plain text transfers). I started looking myself but my the hack it looks like i will have to do is prodably the hard way and good chance it will not work with alot of HELP?? posts in the future:p.

---

### Post by chaumurky on 2006-01-15
Assuming you have both the above setup done and ssh installed on the remote server, in the client machine open a terminal and go:

```
ssh <remoteusername>@<remoteserver> -L 5900:127.0.0.1:5900
``` 
Then in another terminal go:

```
xvncviewer localhost:0
``` 
That's very basic. You should confirm that works before you go crazy with passwordless (key auth) stuff. Some manual reading wouldn't go astray after that... ;-)

---

### Post by shizow on 2006-01-17
is it possible to have more than one connection to one remote desktop, when i try to connect from  a second client, one can enter a password but then then connection breaks immediatly, as long as there is already another client connected to the server

---

### Post by wjp79 on 2006-02-06
I followed the instructions and it worked... 1 time

If I disconnect and try to reconnect i get an error:

"the connection closed unexpectedly"

I'm using ubuntu (5.10) with gdm
I connect through ssh
If I reboot the machine, I can reconnect again 
Is there an log available somewhere??

What am I doing wrong???
sharex11 script:

#!/bin/sh

x11vnc -nap -bg -desktop "VNC ${USER}@${HOSTNAME}"|grep -Eo "[0-9]{4}">~/.vnc/port.txt

# comment out the following if you don't want a popup telling you which port you're using.
zenity --info --text="Your VNC port is `cat ~/.vnc/port.txt`"

---

### Post by intellidenuser on 2006-02-09
Hey, Will you be able to VNC in when logged out with this guide?

---

### Post by dpm on 2006-02-16
Hi, 

this might be a very basic question, but I cannot figure it out:

Which viewer and with which parameters do I connect to the x11vnc server?

I've tried 
```
vncviewer <hostnameofthevncserver>:1
``` 
but I only seem to connect to the vino-server (i.e the connection is just as slow as usual and the clipboard is not working) instead of to the x11vnc server.

Do I have to kill the vino-server process, or is there a way to specify which vnc server I want to connect to?

BTW, the port x11vnc is listening to is 5901.

Thanks.

---

### Post by bryan986 on 2006-03-26
Well this works all fine and dandy but its slower than the built in remote desktop and more limited. For example it doesn't show the windows when you drag them, it only shows a gray rectangle.

---

### Post by strips on 2006-05-20
Thank you intangible !!!

This is what I've been looking for for a long time. I have never been satisfied with Vino.

It worked perfect for my Dapper install. Only the **libxaw8-dev** package doesn't exist in Dapper. As mentioned earlier **libxaw7-dev** works though.

[QUOTE=desp]Hi, 
Which viewer and with which parameters do I connect to the x11vnc server?
I've tried 
```
vncviewer <hostnameofthevncserver>:1
``` 
but I only seem to connect to the vino-server (i.e the connection is just as slow as usual and the clipboard is not working) instead of to the x11vnc server.

Do I have to kill the vino-server process, or is there a way to specify which vnc server I want to connect to?

BTW, the port x11vnc is listening to is 5901.

Thanks.[/QUOTE]

You need the port after the colon, not 1
```
$ vncviewer <vncServerHost>:5901
```

The Vinoserver can run parallel.

__________
Regards
Stian H. Larssen

---

### Post by strips on 2006-05-20
[QUOTE=bryan986]Well this works all fine and dandy but its slower than the built in remote desktop and more limited. For example it doesn't show the windows when you drag them, it only shows a gray rectangle.[/QUOTE]

If you got 100Mbit LAN Vino might run faster. But if you like to save some bandwidth, x11vnc uses **incredible** less bandwidth.

Vino server with no arguments very quickly maxes my wlan to 20MBit throughout. With -bgr233 -encoding hextile it consumes typically 3-6Mbit

x11vnc server with no arguments consumes never more than 3Mbit and lowers down no almost zero with little usage. Thats sweet :mrgreen: 

So x11vnc kicks Vinos *** when you need to save a bit bandwidth. 

Some thinks just showing a rectangle is a positive thing. Why waste bandwidth.

---

### Post by strips on 2006-05-20
[QUOTE=intellidenuser]Hey, Will you be able to VNC in when logged out with this guide?[/QUOTE]

No

---

### Post by NinjitsuStylee on 2006-07-11
Maybe someone can redirect answers regarding remote logging to here?:
[http://www.ubuntuforums.org/showthread.php?t=213877](http://www.ubuntuforums.org/showthread.php?t=213877)

---

### Post by vanstrien on 2006-12-12
You may want to add '-shared' to the line in the original posting.  This allows you to connect more than one viewer to the server. This is especially important if your connection dies for some reason and you need to reconnect.  Otherwise you'll get kicked out until something in the original VNC connection times out.

```
x11vnc -nap -bg -many **-shared** -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}"
```

Don't confuse this with '-many', which tells VNC to allow more connections, not exit after the first connection exits.

---

### Post by JungMin on 2007-07-02
Great help.  I have it working....Except,

On the client side, the window pops up with the client opens and shows the 'server-machine'.  I can see the screen and move the mouse - see where the mouse is going, but if i try to open an application or minimize something or open a menu, i can't see any changes on the client side.  i am using a laptop and am sitting at the server.  Its working, but its like its not refreshing on the client side??

---

### Post by dannyboy79 on 2007-07-02
what you are saying is that you have logged into your x11vnc server from your laptop and can see everything. then you go to the server and open a new window but the laptop doesn't show that window opened? I believe you have to right click on the window border within the client x11vnc session, and chose refresh screen, and the window which the server opened should now show on the client side. 

I can't say why it wouldn't automagically apear cause I use this setup but haven't been home to watch the server's screen. but I can tell you that when i do get home, whatever I did on the client, say open up a webbrowser or what have you, it's always there on the server when I get home. So I wonder if the client affects the server but the server doesn't affect teh client? not sure. you would think it should since x11vnc is suppose to share the already open session of the server. let me know what you find out if the refresh window doesn't help.

---

### Post by maggs on 2007-07-02
Hi. having a small problem getting autocutsel to install. This is what's happening. Running 7.04

user@MAPSVR:~/autocutsel-0.8.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by dannyboy79 on 2007-07-02
> **maggs said:**
> Hi. having a small problem getting autocutsel to install. This is what's happening. Running 7.04

user@MAPSVR:~/autocutsel-0.8.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

well I hope you already read config.log before you posted, did that point you to anything that you could fix? THen I would ask if you have the build-essential package installed? other than that, not sure. I didn't even install that package to get this to work. as far as copying and pasting, I guess I haven't seen the need for it yet as I am normally only x11vnc'd into my home computer to maybe open some torrents or to change around some port forwarding on my router. check out winscp if you need to copy files securely from your ssh server at home to any computer on the outside! you don't even need to install on it the windows computer, it just runs like putty does. just double click it and it runs. SWEET!!

UPDATE: I ssh'd into my home server and created a tunnel for my x11vnc server and I am now writing this from my home server over vnc thru ssh. Anyway, I just tried to copy and paste from the server to the client and it worked without ever installing the autocutsel. I can't say the same for going from client to server but I can speak for copying from server to client, and it does work by simply highlighting a word or sentence, then right clicking chose copy, then exit full screen of the vnc session and try to paste it into my machine I am sitting at and it works and never installed the autocutsel for everyone's FYI. good luck to all!

---

### Post by maggs on 2007-07-02
I can copy and paste from the server to the client but not the client to server. I got rid of all errors bar the last one;
checking for C compiler default output file name... configure: error: C compiler cannot create executables
Any ideas why this is happening?
My system is a bit of a hybrid as the only way I could get 7.04 desktop to install was to install server first then add the desktop. Maybe this has something to do with the error.

It was the build-essentials that was the main problem. Works ok now.

---

### Post by JungMin on 2007-07-03
> ...then you go to the server and open a new window but the laptop doesn't show that window opened?

Not exactly....I mean try to do anything on the client from my Mac doesnt refresh on the Mac, although it works on the server.  (On the client I click minimize, the screen on the client doesnt change/folder doesnt minimize.  But when i look at the server it DID minimize!!)  The client just doesnt refresh......

**UPDATE:   So here is what I figured out by accident....**

Note:  Server is running on Fiesty, client is 'Chicken of the VNC' on a MacBook.  I accidentally had loaded the VNC server twice...the second being Jungmin:1.  So I connected to this, and there is NO delay on when using the client on my Mac.  

BUT, if i connect to Jungmin:0, the client running on my Mac doesn't update!!!  What is going on???

---

### Post by JungMin on 2007-07-03
Well, I couldnt figure it out.....uninstalled it and tried another server and it works.  Thanks for your help!!

---

### Post by dannyboy79 on 2007-07-10
does anyone else's mouse stop working once in awhile? for example: i'll open up devede or firefox and I can't click anything with the mouse cursor, only keyboard works, like tabbing and hitting enter but sometimes I can't tab or hit enter so I am screwed. Any suggestions? I use x11vnc from Fiesty repo's and I use tightvnc with the scale option to 7/8 so that it doesn't fill my entire screen at my work. thanks for any suggesitons. Oh, I normally start the x11vnc after I putty into my server using this command, x11vnc -usepw

this is also thru a putty tunnel if that matters?

---

### Post by yellabelly on 2007-09-27
I hit the same problem "error: C compiler cannot create executables" on  7.10.
The problem is down to missing GNU C/C++ development environment.
I corrected this by "sudo apt-get install g++".

---

### Post by a2brute on 2007-09-27
I noticed no one ever answered the question about how to set this up in KUbuntu instead of Ubuntu.  I was able to get through the first 4 steps with no problem, but the 5th step does not carry over to KUbuntu. 

If anyone knows the full process for getting x11vnc set up in KUbuntu, please post.

Thanks.

---

### Post by krunge on 2007-09-27
You might find a workable solution here: [http://ubuntuforums.org/showpost.php?p=3358127&postcount=339]("http://ubuntuforums.org/showpost.php?p=3358127&postcount=339")

Get rid of the -inetd stuff if you do not want to run it from xinetd/inetd.

Another useful trick is here: [http://ubuntuforums.org/showpost.php?p=3413629&postcount=24]("http://ubuntuforums.org/showpost.php?p=3413629&postcount=24")

---

### Post by robber225 on 2007-12-09
JungMin, I have exactly the same problem. This is a Ubuntu 7.1 w/ flgrx, client is tightvnc viewer on winxp. The client actually was working for a couple of seconds and then it stops updating, though the mouse movement and key strikes are indeed shown on the server (on server's attached screen). Did you find a solution? Or can anybody else help?

---

### Post by krunge on 2007-12-10
> **robber225 said:**
> JungMin, I have exactly the same problem. This is a Ubuntu 7.1 w/ flgrx, client is tightvnc viewer on winxp. The client actually was working for a couple of seconds and then it stops updating, though the mouse movement and key strikes are indeed shown on the server (on server's attached screen). Did you find a solution? Or can anybody else help?

Try this x11vnc option:
```
-noxdamage
```

You can search this forum for that term for more info.  This is a bug in your graphics system: it doesn't properly support the XDAMAGE extension.

---

### Post by airtonix on 2007-12-11
um if your doing remote desktop from linux machine to linux machine, then vnc is not required....this functionality is built in to X and SSH.

> $ ssh [your-username-on-remote-machine]@[ip-address-of-remote-machine] -Xbling! your at the command line....so then 

> $ nautilusBling! again..your now using the remote desktop. with cpu usages happening on remote computer

---

### Post by robber225 on 2007-12-12
Krunge, thanks for the tip, it works :)

---

### Post by BassKozz on 2007-12-14
First off you rock **intangible** :guitar:, Thanks for the AWESOME "How To:"...

I finally got VNC working after [much disappointment](http://ubuntuforums.org/showthread.php?t=618937). :D

I do have a couple of quick questions for ya... 
[LIST=1]
[*]I didn't install **autocutsel** but I am able to copy in ubuntu (via TightVNC) and paste into WinXP just fine with out it... is there a reason why I might want to install autocutsel?
[*]Is there a way to make this auto-run prior to logging on locally?  You see I am trying to use this as a headless (no monitor) server, but If I reboot or shutdown/power up, I have to manually login before the startup programs/scripts load up so is there a way to get this to start w/out having to login?
[/LIST]
If I try and login via SSH and run **sharex11vnc** I get the following error :```

14/12/2007 00:47:26 passing arg to libvncserver: -rfbauth
14/12/2007 00:47:26 passing arg to libvncserver: /home/user/.vnc/passwd
14/12/2007 00:47:26 passing arg to libvncserver: -desktop
14/12/2007 00:47:26 passing arg to libvncserver: VNC user@
14/12/2007 00:47:26 x11vnc version: 0.9.3 lastmod: 2007-09-30
14/12/2007 00:47:26
14/12/2007 00:47:26 *** XOpenDisplay failed. No -display or DISPLAY.
14/12/2007 00:47:26 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
14/12/2007 00:47:26 *** 1 2 3 4
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

14/12/2007 00:47:30

14/12/2007 00:47:30 ***************************************
14/12/2007 00:47:30 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

(zenity:5212): Gtk-WARNING **: cannot open display:
``` 
Because Display :0 hasn't been opened obviously, but is there a way to open :0 via SSH or another method?

---

### Post by krunge on 2007-12-14
> **B/-\ssKozz said:**
> 

Is there a way to make this auto-run prior to logging on locally? ... I have to manually login before the startup programs/scripts load up so is there a way to get this to start w/out having to login?

14/12/2007 00:47:30 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Because Display :0 hasn't been opened obviously, but is there a way to open :0 via SSH or another method?

These links should help:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager")

[http://www.karlrunge.com/x11vnc/faq.html#faq-service]("http://www.karlrunge.com/x11vnc/faq.html#faq-service")

You will need to add a x11vnc call to a Display manager startup script. What that file is called and which directory it is in depends on the display manager (e.g. GDM, KDM) you are running and your linux distro+version.  Some common ones are given in the first link.

---

### Post by BassKozz on 2007-12-14
> **krunge said:**
> These links should help:

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

[http://www.karlrunge.com/x11vnc/#faq-service]("http://www.karlrunge.com/x11vnc/#faq-service")

You will need to add a x11vnc call to a Display manager startup script. What that file is called and which directory it is in depends on the display manager (e.g. GDM, KDM) you are running and your linux distro+version.  Some common ones are given in the first link.

Thanks krunge,

I am using Xubuntu (which I belive is **xfce** display manager), but the links you provided don't have info for **xfce**.

Any idea on how to get this to work with Xubuntu?
Thanks again for your help

---

### Post by krunge on 2007-12-14
> **B/-\ssKozz said:**
> Thanks krunge,

I am using Xubuntu (which I belive is **xfce** display manager), but the links you provided don't have info for **xfce**.

Any idea on how to get this to work with Xubuntu?
Thanks again for your help

If I had to guess it is using one of XDM, GDM, or KDM for its display manager.

Try running this and see if anything pops up:
```
ps wwwwwwwaux | grep -i dm
```

---

### Post by BassKozz on 2007-12-14
I got it working using: ```
sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0
``` :D

Now how can I have this autorun every time the system reboots?  I read in the [FAQ](http://www.karlrunge.com/x11vnc/#faq-display-manager):
> Continuously:   Have x11vnc reattach each time the X server is restarted (i.e. after each logout):

To make x11vnc always attached to the X server including the login screen you will need to add a command to a display manager startup script.

Please consider the security implications of this! Besides having the VNC display for the X session always accessible (but hopefully password protected), there may other issues.

The name of the display manager startup script file depends on desktop used and seem to be:

        GNOME        /etc/X11/gdm/Init/Default  (or Init/:0)
        KDE          /etc/kde*/kdm/Xsetup
        XDM          /etc/X11/xdm/Xsetup        (or xdm/Xsetup_0)
	CDE          /etc/dt/config/Xsetup

although the exact location can depend on operating system and distribution. See the documentation for your display manager:  gdm(1), kdm(1), xdm(1), dtlogin(1) for additional details. There may also be display number specific scripts: e.g. Xsetup_0 vs. Xsetup, you need to watch out for.

Note:  The above gdm setting of KillInitClients=false in /etc/X11/gdm/gdm.conf (or /etc/gdm/gdm.conf, etc.) for GDM is needed here as well. Other display managers (KDM, etc) may also have a similar problem.

Note:  The above Dtlogin*grabServer:False step for Solaris will be needed for dtlogin here as well.

In any event, the line you will add to the display manager script (Xsetup or whatever) will look something like:

  /usr/local/bin/x11vnc -rfbauth /path/to/the/vnc/passwd -o /var/log/x11vnc.log -forever -bg

where you should customize the exact command to your needs.

Happy, happy, joy, joy:  Note that we do not need to specify -display or -auth because happily they are already set for us in the DISPLAY and XAUTHORITY environment variables for the Xsetup script!!!

You may also want to force the VNC port with something like "-rfbport 5900" (or -N) to avoid autoselecting one if 5900 is already taken. 

In my case the file is "/etc/gdm/**gdm.conf**", but what I don't understand is what (exactly) do I need to add to this file, and where in the file should I place the line?

---

### Post by krunge on 2007-12-14
> **B/-\ssKozz said:**
> I got it working using: ```
 sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0
``` :D

In my case the file is "/etc/gdm/**gdm.conf**", but what I don't understand is what (exactly) do I need to add to this file, and where in the file should I place the line?

The gdm.conf (or gdm.conf-custom) is where you put the ```
KillInitClients=false
``` (otherwise GDM will kill x11vnc after a user logs in; you could always just restart x11vnc and reconnect, but that is a pain)

For the x11vnc command, from your post:
> GNOME /etc/X11/gdm/Init/Default (or Init/:0)
so start looking around for that file.  This sort of file is often gratuitously renamed and/or relocated by distros, etc.  so you may have to hunt for it.  See the faq-display-manager link for suggested options.

Once you find it put in your x11vnc command with '-bg' option for it to go into the background.   You do **NOT** need to supply -display or -auth, since the whole idea of the Xsetup, Default script is that those env. vars are already set for the cmds run by the script.

---

### Post by aikidoka on 2007-12-28
First of all, I'm a fresh (since september this year very happy) Ubuntu user. as the family "computer specialist" I've even got most of my family members start using Ubuntu as well. This is my first post and until now the first problem I haven't been able to solve by searching this magnificent forum, it's really great!! :)

now to the situation:
I'm using two ubuntu-machines on my home network where I've followed this HOWTO to set up remote access from one to the other, let's call them server (where x11vnc is installed) and client (where I want to connect - again - with xvncviewer as mentioned on post #11). As I've just suggested, this worked perfectly the first time when I installed it a few days ago, BUT I'm not able to connect from the client anymore. the sharex11vnc file loads without any problems (I guess since the service is running when I log in) and the I can ssh to the server. 
what happens:
after i ssh to the server I open a new terminal window and try to open the vncviewer ```
xvncviewer localhost:0
``` a vnc authentication window pops up, but the problem is that I can't write anything to it so I'm forced to close it since there is nothing I can do :( (see attached picture) Therefore the authentication process gets cancelled and nothing happens :( the first day when this worked this window didn't pop up.
I could try to uninstall everything and redo the HOWTO and see if that solves the problem, but I believe it's better to try and solve it the "hard way" first because of the learning factor. besides, I haven't really got it how the uninstalling of programs work 8-[
I hope someone can help me on this one, it worked really good the first time and I wanted to go over to the next step and try to connect to a server over the internet.

---

### Post by krunge on 2007-12-30
> **aikidoka said:**
> 
As I've just suggested, this worked perfectly the first time when I installed it a few days ago, BUT I'm not able to connect from the client anymore. the sharex11vnc file loads without any problems (I guess since the service is running when I log in).

What did you use to make sure x11vnc is running?  The ps(1) command or something else?
> 
after i ssh to the server I open a new terminal window and try to open the vncviewer a vnc authentication window pops up, but the problem is that I can't write anything to it so I'm forced to close it since there is nothing I can do :( (see attached picture) Therefore the authentication process gets cancelled and nothing happens :( the first day when this worked this window didn't pop up.

What does the x11vnc output file say? If you are not collecting any x11vnc output try adding something like:
```
x11vnc .... -o /tmp/x11vnc.log
```
so when you try to connect you will see the connection logged etc.

However, from what you say I think you have accidentally installed and enabled some other VNC server (e.g. either vncserver or vnc.so) and it is now grabbing the VNC Port (5900) and you are connecting to it instead. The log should tell you which port x11vnc found open (it tries 5900 first, then 5901...)

The HOWTO says to collect the port into ~/.vnc/port.txt, but one might be better off forcing x11vnc to only use one, e.g.:
```
-rfbport 5900
``` then it will exit if it cannot open that port. Then, using ps(1) say, one could see that the x11vnc process is not running if something else grabbed port 5900.

If you do find you **are** connecting to x11vnc and not some other one and are still having the problem, try adding this x11vnc option:
```
-rfbversion 3.7
``` This works around a bug fixed in the upstream x11vnc. Some viewers and x11vnc didn't work at protocol level 3.8

---

### Post by aikidoka on 2007-12-31
First of all, thx for the quick reply! 

To your first question, yes I checked with ps and the service was also running on the right port.
I then added the line you suggested to get an output file and tried to connect, but everything looked fine there as well.
At last I changed the rfbversion (btw, what is that??), but the problem remained, so I much cleverly (stupid me should have tried this before ](*,) ) tried a different vnc viewer (xtightvncviewer from the repos) and it worked like a charm! :lolflag:
The problem seems to be on the xvncviewers authentication program, with xtightvncviewer the prompt for the password is in the CLI whereas the xvncviewer prompts me in a GUI (blah!! ;) ). 
Is there any good reason why I should choose one viewer over the other regarding performance? I can't seem the find out where they differ the most...
I'm still gonna try and figure out what the problem with the xvncviewer is, if I find somthing out I'll post it here as an edit... Or if someone else has an answer for the problem and want to spare me the hard work of searching, please post :D
now, back to work ):P

---

### Post by krunge on 2008-01-01
> 
At last I changed the rfbversion (btw, what is that??)
It is the version of the VNC protocol between server and client. VNC started as RFB (Remote FrameBuffer). The -rfbversion option tells x11vnc which protocol version to advertise.
>  but the problem remained, so I much cleverly (stupid me should have tried this before) tried a different vnc viewer (xtightvncviewer from the repos) and it worked like a charm! The problem seems to be on the xvncviewers authentication program, with xtightvncviewer the prompt for the password is in the CLI whereas the xvncviewer prompts me in a GUI.

Yes, you mentioned you couldn't even type the PW into the GUI, correct? That is really strange... so maybe the whole problem is local.

BTW, what are the versions of the 2 viewers and x11vnc you are using?

---

### Post by chrisdl on 2008-01-30
Okay, I am new to Linux and Ubuntu.  I'm trying to play around and learn this system on the prodding of a friend.  The first thing I wanted to set up is this VNC connection as the remote desktop didn't work.  After reinstalling the Ubutu I have updated all the suggested updates.

I went through the directions except I'm getting an error when I try to set the password and when I reboot it doesn't tell me that VNC is working on any port.  The message just doesn't have a port number.  So I tried running that code line for x11vnc from the terminal and I noticed that it tells me that I can't write to ~/.vnc/port.txt because I don't have permissions.  That's the same error I was getting for setting the password.  It told me I didn't have permission there either.

Can anyone help this newbie?

---

### Post by BassKozz on 2008-01-31
chrisdl,

You have to use "sudo" in the beginning of the command...
i.e.: ```
sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0
```

---

### Post by GamingMazter on 2008-01-31
Thanks. This was really helpful for me :D

---

### Post by chrisdl on 2008-01-31
B/-|ssKoss, what do you mean by that?  In the sharex11vnc file that I created?  Does it need a 'sudo' in front of the x11vnc?

Since I had just started, I thought I would just start from scratch again - this is very frustrating.  I haven't gotten an error in making the password but when I run the line of code again, it still says that it can't make the port.txt file because of permissions.

Does anyone know what I can check?

---

### Post by chrisdl on 2008-01-31
Also let me say that when I initially tried to set the password it didn't understand the command.  I had to 'sudo apt-get install vnc-common' to get it to work.  But it looked like there was a problem with the vnc-common as it was scrolling through the install.  But even after that it appeared that I could set the password.

When I go up to my XP machine it finds the Ubuntu machine and asks for the password so something must be right.  But it gives me the VNC authentication error.

---

### Post by dgrafix on 2008-02-25
Hi,

got as far as the ./configure bit

getting the error:

```
checking for X... libraries , headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for main in -lXext... no
checking for main in -lXaw... no
configure: error: Unable to find Xaw library

```

---

### Post by krunge on 2008-02-25
> **dgrafix said:**
> 
```

checking for IceConnectionNumber in -lICE... no
checking for main in -lXext... no
checking for main in -lXaw... no
configure: error: Unable to find Xaw library

```

Could you send a URL to a tarball, etc, of the source code you are trying to build?  It looks completely hosed trying to find 'main' in libXaw, etc.

---

### Post by s1mon on 2008-03-03
> checking for IceConnectionNumber in -lICE... no
checking for main in -lXext... no
checking for main in -lXaw... no
configure: error: Unable to find Xaw library

Try installing the libaw7-dev package, that fixed it for me.  The libaw8 package isn't available anymore.

s1mon

---

### Post by Deadmode on 2008-04-19
I'm using gOS and I can't figure out where sessions is to put the startup scripts in there.

---

### Post by irvin on 2008-08-01
Hallo

I'm using x11vnc for remote desktop on Ubuntu 8.04 with SSH which works great. With this config I can login after reboot for 1 User:

What I want now is to login with several users at the same time.

for example:
I have these users:

no1@test (admin)
no2@test
no3@test

What does I have to change for login with multiple users at the same time ? So everyone has his own desktop and can use his own files.

I tried several things found here but nothing worked for me.
May somebody made this and can help me ?
++++++++++++++++++
This is my config for 1 User:

I installed this:
openssh-server
x11vnc

Then I made this changes:

made the passwort file:
- sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass

Configure GDM to run x11vnc when at loading time:
- sudo gedit /etc/gdm/Init/Default

and add this line to the file:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr
(sometimes I have to use -xrandr, sometimes not !)

- sudo gedit /etc/gdm/gdm.conf

now search for this line :

#KillInitClients=true

And change it to this:

KillInitClients=false

That's it !
++++++++++++++++++++++++++++

---

### Post by krunge on 2008-08-01
> **irvin said:**
> Hallo

I'm using x11vnc for remote desktop on Ubuntu 8.04 with SSH which works great. With this config I can login after reboot for 1 User:

What I want now is to login with several users at the same time.

for example:
I have these users:

no1@test (admin)
no2@test
no3@test

What does I have to change for login with multiple users at the same time ? So everyone has his own desktop and can use his own files.

I tried several things found here but nothing worked for me.


What you want to do can be done with x11vnc (and Xvfb) using the -create and -unixpw options.

Note that the virtual framebuffer X server Xvfb must be used because if more than one user has an Xsession on the physical display, only one can be active at a time.

Although it can be done, you probably don't want to use the x11vnc+Xvfb method: you should look into the "vncserver" and "nx" applications.

---

### Post by NTolerance on 2008-08-08
delete

---

### Post by irvin on 2008-08-10
OK, Thanks Karl. I thought it would be possible that way.
Does nobody uses a config like I want it to do ?
With vncserver or ?

---

### Post by f0ku5 on 2009-04-23
Thanks for the guide!  Got it working without a hitch on ubuntu 9.04 Jaunty amd64.

FYI:  There's no more need to download and compile autocutsel.  There is now a package in the Universe repository (at least for Hardy/Intrepid/Jaunty, as of 2009-04-23)

---

### Post by kartal on 2009-11-28
Hi

I have tried thr tutorial in the topic and I am getting half success.. I can seem to run the x11vnc on my real desktop as the main admin user. But when I try to connect via ssh and run the x11 server it says it cannot dfind the displaye:0

As I mentioned I could run the server as local user successfully, but then when I use a vnc client to connect to my desktop, I can see the desktop fine. But I cannot modify it, i mean I can modify it but the changes are not shown on my remote only shown on the real x11 server. So my mouse interacts with the server but I just do not see the result on my remote. 

Any suggestions?


thanks

---

### Post by krunge on 2009-11-29
> **kartal said:**
> But when I try to connect via ssh and run the x11 server it says it cannot dfind the displaye:0

There needs to be an X server already running and you need to have permission to attach to it (usually in ~/.Xauthority)

You can use the command 'ps waux' to see if an X server (usually named Xorg) is running.
> 
As I mentioned I could run the server as local user successfully, but then when I use a vnc client to connect to my desktop, I can see the desktop fine. But I cannot modify it, i mean I can modify it but the changes are not shown on my remote only shown on the real x11 server. So my mouse interacts with the server but I just do not see the result on my remote. 

It sounds like you need to supply the "-noxdamage" option to x11vnc to workaround an Xorg bug.  Please search these forums for 'noxdamage' for more info.

---

### Post by war59312 on 2010-05-01
Seems autocutsel no longer works. :(

Tried with Ubuntu 10.04 and seems to do nothing.

Even though autocutsel -verbose shows it doing its think the right click context menu paste is still grayed out when copying back and forth.

At least ctrl +c, ctrl +x, and ctrl +v work between hosts.

Would just be fine if the context menu worked. Thought that is what this program fixed, guess not.

And just so you know pasting via ctrl +v between hosts was already working fine without it.

So seems useless?

---

### Post by krunge on 2010-05-01
> Seems autocutsel no longer works. :(

Tried with Ubuntu 10.04 and seems to do nothing. 
...
So seems useless?
Which VNC server (and its version number) are you using autocutsel with?

---

### Post by HectorG on 2010-08-15
When I get in through the UltraVNC client on a windows machine it shares my workspace and has a long black section feels like 3 or 4 workspace in size and then finally it displays just my wallpaper at the end. It makes my connection VERRRRY slow! It also does this when I try to log in with my iPhone and well renders it useless. Is there any way to limit it to show only the current workspace? 


I run this at startup

```

#!/bin/sh
PORT="5900"
TEXT="X11VNC is listening on $HOST port $PORT"

x11vnc -rfbport $PORT -display :0 -rfbauth ~/.vnc/passwd -noxdamage -bg -forever -listen 192.168.1.253 -gui tray -desktop "VNC ${USER}@${HOSTNAME}"|grep -Eo "[0-9]{4}"

x11vnc -R nodeny
x11vnc -R nolocalhost
x11vnc -R unlock
x11vnc -R nomodtweak

#Pop up a notification with the port 
/home/scripts/alt-notify-send.sh "VNC Port" "$TEXT" "5450" "/usr/share/icons/gnome/scalable/devices/phone.svg"



```

---

### Post by krunge on 2010-08-15
> **HectorG said:**
> When I get in through the UltraVNC client on a windows machine it shares my workspace and has a long black section feels like 3 or 4 workspace in size and then finally it displays just my wallpaper at the end.
From your description I wonder if you accidentally created a ~/.x11vncrc file by clicking around.  I say this because it seems you are describing the '-ncache' option, but I don't see it on your cmdline.  Delete any ~/.x11vncrc file and try again.

---

### Post by HectorG on 2010-08-17
Hey thanks that did the trick! What is the purpose of that ncache? Why would you want those symptoms?

---

### Post by krunge on 2010-08-17
> **HectorG said:**
> Hey thanks that did the trick!

Good, glad it is working for you now.
> What is the purpose of that ncache? Why would you want those symptoms?
The VNC viewer may hide those 'strange' regions from the user.  SSVNC does this automatically on unix and macosx, and other viewers can function well by simply setting the size of the viewer window to match the real display size.

The reason to use -ncache is to get a speedup due to client-side caching of pixel data:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]

I use -ncache 10 to several remote systems across the country and it gives me a very nice improvement in interactive response (I can even use a full-jpeg photo image as the background with no slowdown.) YMMV.

---

### Post by HectorG on 2010-08-17
That's good to know. Thanks again!

---

### Post by sports supplement on 2010-08-22
I have used most of this an a machine which refused to work with Vino on 10.04 (X 64).  Thank you for the post.  I have added to the start line -ncache 10 (this speeds up responses massively), -ncache_cr (for the same reason) and -noxdamage to remove errors reported when trying this from the terminal.

---

### Post by Docfxit on 2010-12-07
I'm trying to use X11.  When Ubuntu boots up it says VNC port 5901.
I can't connect to 5901 but I can connect to 5900.  I can't copy paste from windows so I'm guessing there is a different VNC server running on Ubuntu that I'm connecting to.  How can I stop the other VNC server so I can connect to X11?

docfxit@UbuntuAsterisk:~$ ps ux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
docfxit   5578  0.0  0.7  27688  7296 ?        Ssl  09:46   0:00 x-session-manag
docfxit   5619  0.0  0.0   4432   540 ?        Ss   09:46   0:00 /usr/bin/ssh-ag
docfxit   5621  0.0  0.3   6740  3960 ?        S    09:46   0:00 /usr/lib/libgco
docfxit   5631  0.0  0.0   5012   652 ?        S    09:46   0:00 /usr/bin/gnome-
docfxit   5633  0.0  0.1   2904  1088 ?        Ss   09:46   0:00 dbus-daemon --f
docfxit   5635  0.0  0.9  38136  9852 ?        Sl   09:46   0:00 /usr/lib/gnome-
docfxit   5654  0.0  1.0  17896 10368 ?        S    09:46   0:00 /usr/bin/metaci
docfxit   5656  0.0  1.6  42436 17036 ?        S    09:46   0:00 gnome-panel --s
docfxit   5658  0.0  1.7  79464 17644 ?        S    09:46   0:00 nautilus --no-d
docfxit   5662  0.0  0.4  19468  4976 ?        Ss   09:46   0:00 gnome-volume-ma
docfxit   5667  0.0  0.3  40880  3136 ?        Ssl  09:46   0:00 /usr/lib/bonobo
docfxit   5686  0.0  0.3   8724  3396 ?        S    09:46   0:00 /usr/lib/gnome-
docfxit   5689  0.0  0.6  19208  6796 ?        S    09:46   0:00 vino-session --
docfxit   5690  0.0  0.2  16460  2664 ?        Ss   09:46   0:00 gnome-screensav
docfxit   5695  0.0  0.5  13292  5432 ?        S    09:46   0:00 bluetooth-apple
docfxit   5697  0.0  1.1  34560 12000 ?        S    09:46   0:00 update-notifier
docfxit   5704  0.0  0.9  68940  9840 ?        Sl   09:46   0:00 /usr/lib/evolut
docfxit   5706  0.0  0.7  27704  7296 ?        SNl  09:46   0:00 trackerd
docfxit   5709  0.0  0.1   3716  1572 ?        S    09:46   0:00 autocutsel
docfxit   5720  0.0  1.1  44124 11552 ?        S    09:46   0:00 nm-applet --sm-
docfxit   5723  0.0  1.1  22816 11704 ?        S    09:46   0:00 python /usr/sha
docfxit   5725  0.0  0.7  22164  7668 ?        Ss   09:46   0:00 gnome-power-man
docfxit   5730  0.0  1.5  21592 16156 ?        Ss   09:46   0:02 x11vnc -nap -bg
docfxit   5737  0.0  0.9  36428  9404 ?        Sl   09:46   0:00 /usr/lib/evolut
docfxit   5744  0.0  0.8  65024  9116 ?        S    09:46   0:00 /usr/lib/gnome-
docfxit   5760  0.0  0.6  65952  6436 ?        Sl   09:46   0:00 /usr/lib/evolut
docfxit   5762  0.0  0.0   2664   896 ?        S    09:46   0:00 /usr/lib/nautil
docfxit   5768  0.0  1.2  43976 12436 ?        Sl   09:46   0:00 /usr/lib/gnome-
docfxit   5783  0.0  2.7  64520 28384 ?        Sl   09:46   0:00 /usr/bin/python
docfxit   5805  0.0  1.1  34456 11500 ?        S    09:46   0:00 /usr/lib/fast-u
docfxit   5814  0.0  0.9  30772 10180 ?        S    09:46   0:00 /usr/lib/notifi
docfxit   6236  0.0  1.8  61732 18948 ?        Rl   10:41   0:00 gnome-terminal
docfxit   6238  0.0  0.0   2668   744 ?        S    10:41   0:00 gnome-pty-helpe
docfxit   6239  0.0  0.3   5992  3348 pts/0    Ss   10:41   0:00 bash
docfxit   6289  0.0  1.0  31560 10916 ?        S    10:48   0:00 gksudo /opt/dou
docfxit   6995  0.0  0.0   2624  1004 pts/0    R+   11:37   0:00 ps ux

netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:5900                  *:*                     LISTEN     
tcp        0      0 *:5038                  *:*                     LISTEN     
tcp        0      0 *:sieve                 *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:omniorb               *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 UbuntuAsterisk.loc:5900 netblock-75-79-6-:16001 ESTABLISHED
tcp6       0      0 *:ssh                   *:*                     LISTEN     
udp        0      0 *:32768                 *:*                                
udp        0      0 UbuntuAsteri:netbios-ns *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 UbuntuAster:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:2727                  *:*                                
udp        0      0 *:4520                  *:*                                
udp        0      0 *:sip                   *:*                                
udp        0      0 *:iax                   *:*                                
udp        0      0 *:mdns                  *:*                                
udp6       0      0 *:xdmcp                 *:*   

Thank you,

Docfxit

---

### Post by war59312 on 2011-05-12
Whoops, just realized this was the wrong topic.

Sorry.

Please see: [http://ubuntuforums.org/showthread.php?p=10820136#post10820136](http://ubuntuforums.org/showthread.php?p=10820136#post10820136)

---

### Post by war59312 on 2011-05-15
Wrong topic, sorry.

See: [http://ubuntuforums.org/showthread.php?p=10820136#post10820136](http://ubuntuforums.org/showthread.php?p=10820136#post10820136)

---

### Post by alfonso78 on 2011-11-01
> **vanstrien said:**
> You may want to add '-shared' to the line in the original posting.  This allows you to connect more than one viewer to the server. This is especially important if your connection dies for some reason and you need to reconnect.  Otherwise you'll get kicked out until something in the original VNC connection times out.

```
x11vnc -nap -bg -many **-shared** -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}"
```

Don't confuse this with '-many', which tells VNC to allow more connections, not exit after the first connection exits.

Hi!

I have the problem you describe (I cannot login again if a sesion hangs until I add -shared).
Is there a way to tell to x11vnc to accept the last connection and kill all previous connections rather than consuming resources keeping track of hanging sessions?

thank you!

ps. to make it easier for people to find this solution, I add the error from the logs:

> 01/11/2011 20:02:09 -dontdisconnect: Not shared & existing client
01/11/2011 20:02:09   refusing new client 192.168.100.163
01/11/2011 20:02:09 client_count: 1
01/11/2011 20:02:09 Client 192.168.100.163 gone
01/11/2011 20:02:09 Statistics             events    Transmit/ RawEquiv ( saved)
01/11/2011 20:02:09  TOTALS              :      0 |         0/        0 (  0.0%)
01/11/2011 20:02:09 Statistics             events    Received/ RawEquiv ( saved)
01/11/2011 20:02:09  TOTALS              :      0 |         0/        0 (  0.0%)

---

### Post by krunge on 2011-11-03
> I have the problem you describe (I cannot login again if a sesion hangs until I add -shared).
Is there a way to tell to x11vnc to accept the last connection and kill all previous connections rather than consuming resources keeping track of hanging sessions?

I think something like this will work:

```
x11vnc -forever -nevershared
```

plus any other unrelated options.

---

