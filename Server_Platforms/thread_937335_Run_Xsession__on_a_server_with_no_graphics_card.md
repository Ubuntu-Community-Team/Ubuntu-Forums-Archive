---
title: "Run Xsession  on a server with no graphics card"
date: 2008-10-03
forum: Server Platforms
---

### Post by purple melon on 2008-10-03
Anyone know how to run an Xsession on a server with no graphics card?

I have debian running on the server, which was installed with a laptop running Ubuntu connected via a serial cable. Putty used to access the server serial console port. With debian running and ssh installed on the server I can ssh into the server with the laptop over the lan i.e. from laptop terminal # ssh web-server@192.168.1.9. 

Then logging in as root run "gdm  gdm is already running". running startx throws up errors about no pci device detected and waiting for x to accept connections failures.

is there a failsafe startx command? or a startx to a null device type command?

not sure how much info to add but any web links or help appreciated. ta

---

### Post by nitecon on 2008-10-03
If it is a server why do you need to have it run a window manager?  You will be much better of just using ssh to get into the server and learning how to configure the server through the prompt than using a window manager.  If you absolutely have to you could use XDMCP i guess but that is insecure.

---

### Post by purple melon on 2008-10-04
Thanks nitecon.

Yes I could use ssh and the command line to configure the server, don't have to much experience in the command line so might be a step learning curve. Would be nice to get xsession working or should I just forget about X as it will never work?

---

### Post by purple melon on 2008-10-13
nobody any interest in this then?

---

### Post by lykwydchykyn on 2008-10-13
It sounds like X is running on the workstation.  You can't run "startx" or gdm in an ssh session, because they can't run inside a terminal like that.

If you want a remote GUI, you need to set up XDMCP or VNC.  Have you tried installing tightvncserver and using that?

---

### Post by promodus on 2008-10-13
I apologize, but I find the question challenging to understand.

What machine has no graphics card? The machine you're connecting to?

If I get this right:

[COLOR="Sienna"]your machine[/COLOR] with a graphics card is using ssh to connect to your [COLOR="DarkGreen"]server[/COLOR] without one. You want programs to run on your [COLOR="DarkGreen"]server[/COLOR] but display on [COLOR="Sienna"]your machine[/COLOR].

So in that case

desktop # ssh -X server

once logged into your server, insure that xauth is installed.
From there you can start applications, like gedit for example.
Just SSH -X server, and start the app. 

If you want gdm to be running on the server, then that's different.

---

### Post by purple melon on 2008-10-14
[B]Yes promodus you do have it right.
[/B]
I want to view or display the gdm or xserver (gnome-session) from the server (remote) on to the laptop (local). sorry if these are not the correct terms and don't think I have a total understanding of gdm, xsession or gnome-session! 

**Server (remote) [COLOR="Red"]d390:~#[/COLOR] **
an HP D Class d390 running Debian Lenny Beta2 HPPA, no graphics card in server so access is via a serial cable for initial boot or install then ssh over network once debian hppa has booted.

**Client (local)[COLOR="Blue"]melon@vaio[/COLOR]**
a sony laptop running Gnome desktop on Ubuntu hardy heron, putty used to access server via serial cable then terminal to ssh into server.

When I type on [COLOR="Blue"]melon@vaio[/COLOR] "ssh -X root@d390 xclock" and enter root password the xclock is displayed.

when I type on [COLOR="Blue"]melon@vaio[/COLOR] "ssh -X root@d390 nautilus" nautilus file manager pops up.
```
root@d390's password: 
seahorse nautilus module initialized
Initializing gnome-mount extension
```

when I type "gdm" on [COLOR="Red"]d390:~#[/COLOR]

```
d390:~# gdm
gdm[2174]: WARNING: GDM already running. Aborting!
GDM already running. Aborting!
d390:~# 
```

when I type startx on server or ssh -X root@d390 startx on laptop I get the following message.

```
d390:~# startx

X: warning; process set to priority -1 instead of requested priority 0
X.Org X Server 1.4.2
Release Date: 11 June 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux Debian (xorg-server 2:1.4.2-6)
Current Operating System: Linux d390 2.6.26-1-parisc-smp #2 SMP Wed Sep 10 20:58:00 UTC 2008 parisc
Build Date: 15 September 2008  01:29:21PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct  5 02:14:11 2008
(==) Using config file: "/etc/X11/xorg.conf"
xf86PciVideoInfo is not set
Could not get primary PCI info

waiting for X server to begin accepting connections 
giving up.
xinit:  Connection reset by peer (errno 232):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
d390:~# 
```

When I type on [COLOR="Blue"]melon@vaio[/COLOR] "ssh -X root@d390 gnome-session"

```
SESSION_MANAGER=local/d390:/tmp/.ICE-unix/2577
** ERROR **: You can only run one xsettings manager at a time; exiting
aborting...
** ERROR **: You can only run one xsettings manager at a time; exiting
aborting...
1223170768.404000 Session manager: disconnected...
Window manager warning: Failed to read saved session file /root/.metacity/sessions/default0.ms: Failed to open file '/root/.metacity/sessions/default0.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
** (gnome-settings-daemon:2603): WARNING **: Failed to acquire org.gnome.SettingsDaemon
** (gnome-settings-daemon:2603): WARNING **: Could not acquire name
seahorse nautilus module initialized
** ERROR **: You can only run one xsettings manager at a time; exiting
aborting...
1223170785.412000 Session manager: disconnected...
** (update-notifier:2609): WARNING **: already running?
Initializing gnome-mount extension
** (gnome-settings-daemon:2636): WARNING **: Failed to acquire org.gnome.SettingsDaemon
** (gnome-settings-daemon:2636): WARNING **: Could not acquire name
Window manager warning: Failed to read saved session file /root/.metacity/sessions/default0.ms: Failed to open file '/root/.metacity/sessions/default0.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
** ERROR **: You can only run one xsettings manager at a time; exiting
aborting...
1223170799.412000 Session manager: disconnected...
** (gnome-settings-daemon:2660): WARNING **: Failed to acquire org.gnome.SettingsDaemon
** (gnome-settings-daemon:2660): WARNING **: Could not acquire name
** ERROR **: You can only run one xsettings manager at a time; exiting
aborting...
1223170807.628000 Session manager: disconnected...
** (gnome-settings-daemon:2663): WARNING **: Failed to acquire org.gnome.SettingsDaemon
** (gnome-settings-daemon:2663): WARNING **: Could not acquire name
** ERROR **: You can only run one xsettings manager at a time; exiting
aborting...
** ERROR **: You can only run one xsettings manager at a time; exiting
aborting...
** (gnome-panel:2592): WARNING **: Failed to authenticate with GDM
melon@vaio:~$ 
```

Is my problem that I can't start an other x-session on the laptop as I'm in a gnome session already or because I can't start a x-session on the server to export to the laptop? 

server and laptop names are examples only!

---

### Post by cariboo on 2008-10-14
You can manipulte files on your server from your laptop by using sftp. in the location bar in Nautilus type:

```
sftp://user@server
```

You could also install webmin on your server it is available here:

[http://www.webmin.com/](http://www.webmin.com/)

It is a complete sever administration suite, it even has it's own java based file manager. There is a demo server set up so you try it before you decide whether you can use it or not. 

Running a gui on a server is just a waste of ram and cpu cycles, and there aren't any gui server specific tools. Most of a servers configuration files are text based, so getting comfortable with nano, vi or any other text editor is a good idea.

On my server I use mc aka Midnight Commander, you can run it as root to transfer files  to directories you don't have permission to, it has a built in test editor, you can use to edit config files. It has a builtin ftp client and many more features. mc is available in the repositories so it is easy to install at the prompt type:

```
sudo apt-get install mc
```

and to run it simply type:

```
mc
```

If you need to run as root:

```
sudo mc
```


Jim

---

### Post by lykwydchykyn on 2008-10-15
You can't forward a display manager or gnome session over ssh.  Well, you can try, but as you saw it makes a mess of things or just errors out.  If you want a whole desktop session, this is what VNC is for.  Or XDMCP.

Here's a doc on XDMCP:

[http://tldp.org/HOWTO/XDMCP-HOWTO/](http://tldp.org/HOWTO/XDMCP-HOWTO/)

Another quite novel method I saw someone using on these forums a while back was to run Xephyr, a nested X server, and then run gnome-session in that.

Install xserver-xephyr then do something like this:
```

Xephyr -ac -screen 800x600 -br -reset -terminate :1 &
export DISPLAY=:1
ssh myserver gnome-session

```

---

### Post by tgalati4 on 2008-10-15
I'm not aware of a method to run the X-server without some form of graphics hardware.  Many server platforms have at least an embedded VGA.  Perhaps others know of a way to force xorg without a hardware check.

When an X-server is running, it's helpful to run from a remote machine:

ssh -2 -Y user@servername

Then try:

gnome-panel

---

### Post by purple melon on 2009-01-29
Thanks to all posters

I had to give up on this one, sorry.
 
Gone back to HP-UX on the D390 and acquired a nice Dell Poweredge 2600 which just works with Ubuntu server installed and running a very quick web server.

thanks again

---

### Post by aaron.d on 2009-01-30
good god, i dont get it... You had this working, you said you could run x apps forwarded through ssh to your local (laptop) Xserver.

> When I type on melon@vaio "ssh -X root@d390 xclock" and enter root password the xclock is displayed.

when I type on melon@vaio "ssh -X root@d390 nautilus" nautilus file manager pops up.

I think you don't really understand what X is and its functionality ("client/server").

> Is my problem that I can't start an other x-session on the laptop as I'm in a gnome session already 



You should really read up on what X window system IS:
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

and read about display manager(s):
[http://en.wikipedia.org/wiki/X_display_manager](http://en.wikipedia.org/wiki/X_display_manager)

and DEFINITELY the above cited HOWTO:

[http://tldp.org/HOWTO/XDMCP-HOWTO/](http://tldp.org/HOWTO/XDMCP-HOWTO/)


Don't walk away from this, it is an important concept. I think you just need to grasp the difference between local resources vs. your servers resources and learn to also separate yourself from the Windows world where all the "Windows"/apps and the gui itself are inseparable entities which are rigidly designed to run on and address "local"(physical) resources.

---

### Post by ByteJuggler on 2009-02-11
Just to add:  If you install "vncserver" package, then you can have an X session completely rendering to a virtual VNC display, to which you can then connect (predictably) using VNC.  

Another option is for you to simply install NX, which is a highly optimised updated X protocol based client/server, with which you can likewise either have an entire desktop session, or export single application on a remote machine to your local machine.  

See this [thread]("http://ubuntuforums.org/showthread.php?t=1002240").

---

