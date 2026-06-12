---
title: "HOWTO:  Control the gnome VNC vino-server from the command line"
date: 2006-09-28
forum: Tutorials
---

### Post by srf21c on 2006-09-28
NOTE:  At long last here's the updated method.  This was tested between two Ubuntu 10.10 Maverick hosts.  Thanks to all the contributors to this thread, especially the posts by [frafu]("http://ubuntuforums.org/showpost.php?p=2333655&postcount=16") and [InkyDinky]("http://ubuntuforums.org/showpost.php?p=8308582&postcount=37")

user@localbox:~$ ssh -Y user@remotebox
user@remotebox:~$ vino-preferences
[[IMG]http://img69.imageshack.us/img69/6493/vinopreferences.png[/IMG]](http://img69.imageshack.us/i/vinopreferences.png/)
# check settings and hit close button
user@remotebox:~$ sudo -s
root@remotebox:~# export DISPLAY=:0.0
root@remotebox:~# xhost +
root@remotebox:~# /usr/lib/vino/vino-server &
# to start the vino server
root@remotebox:~# netstat -nl | grep 5900  
# check to make sure vino server is listening on port 5900
exit or CTRL-D twice to close SSH session to remotebox

user@localbox:~$ ssh -L 5900:localhost:5900 user@remotebox
# establish a new SSH connection to remotebox w/forwarded VNC port
# launch Remote Desktop Viewer (vinagre) under Applications => Internet and connect to localhost
[[IMG]http://img341.imageshack.us/img341/9817/remotedesktopviewer.png[/IMG]](http://img341.imageshack.us/i/remotedesktopviewer.png/)

---

### Post by motin on 2006-10-01
Very interesting. Although I am in the same situation I cannot really use your guide, since I am using Putty from Windows... Can you maybe add some comments on how to achieve the same stuff in my situation? In case you know of course...

---

### Post by srf21c on 2006-10-02
You are perfectable capable of setting each value in the /home/<userhomedir>/.gconf/desktop/gnome/remote_access/%gconf.xml file manually using the gconftool-2 command.

I was unable to dig up any documentation on proper syntax of the  %gconf.xml file so I did not feel qualified on delving into this method in more detail on my original post.  

If you examine an existing %gconf.xml file, and compare that to the gconftool-2 command syntax that I have already posted, you should be able to figure out how to set the other parameters.

---

### Post by motin on 2006-10-08
I have come so far that the vino server asks me for a password. A password that I cannot remember at all. 

The problem is that I cannot change it via CLI. It is not written in plain text in ~/.gconf/desktop/gnome/remote_access/%gconf.xml, so changing it to "qwerty" in the file doesn't help. 

Also, the command:
```
gconftool-2 -s -t string /desktop/gnome/remote_access/vnc_password qwerty
```

Just does the same thing as changing the file manually - ie doesn't help. 

Do you or someone else now in what hash-type the vino passwords are written in?

---

### Post by motin on 2006-10-08
I started a new thread on the matter (generating the password): [http://ubuntuforums.org/showthread.php?p=1592817](http://ubuntuforums.org/showthread.php?p=1592817)

---

### Post by srf21c on 2006-10-09
Don't know what the vino server hash-type is, but here's the string I get after setting the vino password to "qwerty"

 <entry name="vnc_password" mtime="1160442984" type="string">
                <stringvalue>cXdlcnR5</stringvalue>
  </entry>

---

### Post by jdong on 2006-10-09
Have you tried an htpasswd hash in there?

---

### Post by morton2002 on 2006-10-13
Many more details are available in [the spun-off password thread]("http://ubuntuforums.org/showpost.php?p=1613152&postcount=2").  Thanks for your head-start on this, I found the posts very useful and I hope I've helped you too.

---

### Post by srf21c on 2006-10-13
I found a workaround that allows for logging in a user to the desktop remotely, simply edit the gnome desktop preferences to enable autologin, then reboot the box.

Edit the /etc/gdm/gdm.conf-custom file using your favorite text editor, and under the daemon section add the following lines

[daemon]
AutomaticLogin=<username>
AutomaticLoginEnable=true

Then reboot the box and the user will automatically be logged into the desktop on the next boot, thus starting the gnome vino vnc server (if enabled)

---

### Post by frafu on 2006-10-14
@srf21c

I suppose the settings in /etc/gdm/gdm.conf-custom override those in /etc/gdm/gdm.conf

However, there is another question that I am wondering about: how can I enable the vino vnc server for the next boot on a system that is not running. (the disk with the system that does not run being mounted on another system) 

Thanks in advance for your help. 

frafu


Background: 

I have a headless celeronbox with 2 ubuntu dapper systems on it; both systems have remote logins enabled (vino, nx, openssh). I would like to upgrade the second ubuntu to edgy, but I don't know whether the upgrade will disable the remote logins.

Consequently, I thought to edit menu.lst in grub to make it reboot after the upgrade with the system that has not been upgraded and reenable the remote logins from the new edgy before booting into edgy.

---

### Post by frafu on 2006-10-15
I did the upgrade this afternoon and the update manager asked me several times whether I wanted to keep a specific old configuration file from dapper instead of installing the new one. As I kept the old configuration file for the remote desktop (and few others), I was able to connect with my vnc client at once after booting to edgy. 

frafu

---

### Post by srf21c on 2006-10-16
Excellent!  In answer to your question, I think the bottom line is this;  If you want the vino server to start hands-free after a reboot, you need to have automatic login to the desktop enabled.

---

### Post by bobpaul on 2007-03-19
I know it's digging up an old thread, but one could install a windows xserver (cygwin has one, or Xming is good) and enable X forwarding in putty. It's even easier if your local machine is also linux:
```
$ ssh -XC user@host
```

Then you could open vino-preferences remotely. vino-preferences is a simple enough GUI that even across a pretty slow connection it still responds decently.

**EDIT:** I meant uppercase C for compression. Good for slower speed connections. Lowercase c will cause an error. Sorry. Thanks to srfc21 for pointing that out.

---

### Post by srf21c on 2007-03-19
Bob, 

_great_ suggestion....much more elegant than my approach.  Thanks for adding that to the thread.

Btw, have you tested it succesfully?

---

### Post by bobpaul on 2007-03-21
Yeah, I use Xming and putty's X-Forwarding optional from my WinXP machine at work to access my home machine all the time! Errm, I mean... I only do work related things at work. :-\"

Bigger apps, like firefox, are pretty unresponsive, but small config windows like this work just fine. For reference, I have 128kbps upstream on my home connection. I think your command line solution would be the best method over something like dialup as it might take a few minutes for the dialog to "stabilize" on a really slow connection like that.

---

### Post by frafu on 2007-03-21
To open the "Login Window" preferences, you have to type into the terminal after opening your ssh -Y connection: 

```

sudo gdmsetup

```

To open the "Remote Desktop" preferences, you have to type into the terminal:

```

sudo vino-preferences

```

But, the changes made in the forwarded preferences seem not to be effective in the session created by the auto-login at startup.

---

### Post by srf21c on 2007-03-27
```
$ ssh -Xc user@host
```

Bob, I think the original command example you gave above might have a typo.   

The lowercase -c option specifies the cipher to use, whereas the uppercase -C option enables compression.  Did you mean to use the uppercase -C to enable compression?  like this:

```
ssh -XC user@host
```

---

### Post by FXFman1209 on 2007-06-06
Hmm. I know this is an old thread, but... does this work? I don't think you should use sudo with vino-preferences, because your vino preferences are per-user. If you use sudo vino-preferences, it would set the preferences for root, and not the user.

Therefore I propose that you login as the user you want to desktop control, and then just simply do **vino-preferences**.

However, I could be totally wrong, however it works fine for me. Thanks for the -X suggestion, i never even thought of doing that. :-P

---

### Post by theQmaster on 2007-06-17
I have Dapper without keyboard and monitor and I need to connect the desktop to upgrade to Edgy. Remote access seems to be the only options thus far... I have access to a sh session thru putty.

I managed to start x, vino and gdm - when I connect to the box with VNC client it looks like it's connecting but the client doesn't display any window -  it looks that in background... If I kill the vino server I get the windows that the connection has been disconnected....

What's wrong ? It looks that the server awaits for acceptance from the server but I don't get any window since I'm in sh, I only get a broadcast that a connection has been established


Any help?

---

### Post by theQmaster on 2007-06-17
Just realised that my vino server is not starting anymore

mc@gsi:/tmp$ sudo /usr/lib/vino/vino-server

(vino-server:31773): Gtk-WARNING **: cannot open display:


Any good tips ?

---

### Post by frafu on 2007-06-17
Do you have an X server running on your local machine? If so, try to connect through sh with the following command: 

```
 
ssh -Y loginname@remotecomputerip

``` 

Because of the -Y option, the gui of the application started on your remote computer should be displayed on your local machine if there is a X server running on your local machine. 

Particularly, you should be able to start the synaptic Package Manager and reinstall vino. Afterwards, you should start "vino-preferences" from the shell which should display the gui of the preferences on your local machine. There you should be able to enable vino (=vnc server of the remote machine) 

Have a nice day.

---

### Post by theQmaster on 2007-06-17
I my windows' putty I typed the command by I get
**ssh: connect to host localhost port 22: Connection refused**



> **frafu said:**
> Do you have an X server running on your local machine? If so, try to connect through sh with the following command: 

```
 
ssh -Y loginname@remotecomputerip

``` 

Because of the -Y option, the gui of the application started on your remote computer should be displayed on your local machine if there is a X server running on your local machine. 

Particularly, you should be able to start the synaptic Package Manager and reinstall vino. Afterwards, you should start "vino-preferences" from the shell which should display the gui of the preferences on your local machine. There you should be able to enable vino (=vnc server of the remote machine) 

Have a nice day.

---

### Post by frafu on 2007-06-17
Is there an ssh-server running on your remote computer? (If I remember correctly, the ssh-client gets installed by the default ubuntu installation, but the ssh-server is not.) I thought that the ssh server was running on your remote computer... 

Do you have some way to access the remote computer with some shell? If so, you could use the command 
sudo apt-get install openssh-server
to install the ssh-server. 

Unfortunately, I don't have much knowledge about this things.

---

### Post by foxmajik on 2008-07-10
```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```This doesn't actually stop or start the server, it just enables or disables the item in the configuration file.

```
$ gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
jpruitt@winkypop:~$ nmap localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-07-10 15:09 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1712 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.069 seconds
```The vino binary lives here:

```
/usr/lib/vino/vino-server
```

I discovered this while researching after my vino server crashed when I tried to set rotation to normal in the resolution preferences dialog.

Unfortunately starting the server from the command line doesn't seem to make it read the configuration stored in your home directory, and since there's no documentation available I don't know which switches to use to make it read the config, nor do I know what the switches are to specify them on the command line.

```
$ 10/07/2008 03:18:19 PM Autoprobing TCP port
10/07/2008 03:18:19 PM Autoprobing selected port 5900
10/07/2008 03:18:19 PM Advertising security type: 'TLS' (18)
10/07/2008 03:18:19 PM Advertising authentication type: 'VNC Authentication' (2)
10/07/2008 03:18:19 PM Advertising security type: 'VNC Authentication' (2)

jpruitt@winkypop:~$ nmap localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-07-10 15:20 EDT
10/07/2008 03:20:48 PM Got connection from client localhost
10/07/2008 03:20:48 PM   other clients:
Interesting ports on localhost (127.0.0.1):
Not shown: 1711 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 0.070 seconds
```

Unfortunately there is no man page for vino-server.

---

### Post by srf21c on 2008-09-24
Documentation for the vino-server seems hard to come by, indeed.

One option would be to configure a user to automatically log into the desktop on startup, then restart the machine.   That should get the vino server running again, without having to get some hands on the physical console.

---

### Post by foxmajik on 2008-09-24
> **srf21c said:**
> Documentation for the vino-server seems hard to come by, indeed.

One option would be to configure a user to automatically log into the desktop on startup, then restart the machine.   That should get the vino server running again, without having to get some hands on the physical console.

Yes and then anyone who walked by the computer could drop in and delete your / directory, view all of your private documents, impersonate you on the Internet and all sorts of other fun things.  I wish more people would do this.

---

### Post by raindog469 on 2009-03-25
Sorry to bump an old thread, but we have three desktops with wired connections, one running Hardy and the other two Intrepid, and vino-server works fine on them.  But we also have a laptop running Intrepid, and even with automatic login enabled and remote desktop enabled, the server just never runs unless we run /usr/lib/vino/vino-server manually. 

We think this is because the wireless card doesn't get initialized until after the user has automatically been logged in, creating a race condition where vino-server is trying to get an IP address that may or may not exist.  But the gconftool commands also don't seem to cause vino-server to run.  

Anyone have any ideas about this?  I'm just about to install x11vnc and make a script to run it remotely like I used to have to do under Mandriva, but just using Vino would be more convenient.

> **foxmajik said:**
> Yes and then anyone who walked by the computer could drop in and delete your / directory, view all of your private documents, impersonate you on the Internet and all sorts of other fun things.  I wish more people would do this.

I'm sure glad I don't live in a group home.

---

### Post by MidSpeck on 2009-04-16
It's nice that all the information needed is practically linked to from this thread.  However, I'm the sort of guy that likes it all in one spot.

Turn on Ubuntu's built-in VNC server when all you have is SSH: (may have to have the user logged on to the desktop already, I haven't looked into that part of things at all)

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
gconftool-2 -s -t bool /desktop/gnome/remote_access/vnc_password cXdlcnR5
gconftool-2 -s -t list --list-type string
/desktop/gnome/remote_access/authentication_methods '[vnc]'
gconftool-2 --type bool --set /desktop/gnome/remote_access/prompt_enabled 0

```

Make an SSH tunnel to port 5900 and use a VNC viewer to connect.

Note that when you set the vnc_password, it expects it to be base64 encoded.  So you'll be able to tell that my VNC password above is simply "qwerty".  There are plenty of online base64 encoders and decoders to help you generate your own password.

---

### Post by srf21c on 2009-05-04
Thanks for consolidating the info into a single post. Good idea.

---

### Post by mlalkaka on 2009-06-04
> **MidSpeck said:**
> Turn on Ubuntu's built-in VNC server when all you have is SSH: (may have to have the user logged on to the desktop already, I haven't looked into that part of things at all)

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
...

```Make an SSH tunnel to port 5900 and use a VNC viewer to connect.


I know that this command used to work in one of the older versions of Ubuntu (prior to Intrepid Ibex, I believe). However, in the last few releases, this command only works locally. That is, if I run it over an SSH connection, it does nothing. If I run it locally, it actually enables vino server.

Has anyone else noticed this problem? I have noticed it in both Intrepid Ibex (8.10) and Jaunty Jackalope (9.04). How can I get the old functionality back?

---

### Post by mlalkaka on 2009-06-04
It looks like I solved my own problem. :D

While trying to troubleshoot this issue, I decided to try running the vino-server executable directly (from an SSH connection):
```

$ /usr/lib/vino/vino-server --display=:0.0
Failed to open connection to bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

```The error message suggested that the problem may in fact have more to do with D-Bus than GConf or vino. So, after reading the man pages of dbus-launch and dbus-daemon, I decided to try running gconftool through dbus-launch:
```

dbus-launch gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

```This worked perfectly. 

Alternatively, you can also set the environment variables from the file ~/.dbus/session-bus/*-0 (where * is some unique identifier for your computer) manually, or import it into a shell script.

I've attached a Bash script called toggle_vino_server.sh that you can use to enable and disable remote desktop remotely using SSH. There is no need to forward X over SSH to do this either. 

**Before I go any further, though, I must state that the script comes with no warranty whatsoever, and I'm not responsible for anything that happens to you, your computer, or your pet rat, for that matter, by using this script.**

Simply save the script to ~/bin, give the file executable permissions, and run it from the command-line. It takes no parameters -- it will enable the server if it is disabled, and disable the server if it is enabled.

---

### Post by sixerjman on 2009-07-12
Again, setting the gconf preference for enabling or disabling remote desktop
does not address the problem of vino-server not running.

At some point if the vino-server crashes, you need to start it up to have a process listening on port 5900 or whatever port the server is configured to listen to.  dbus-launch fails to start vino-server if the X11 authentication
is not done.

---

### Post by bobpaul on 2009-07-12
> **sixerjman said:**
> Again,  Again? Have you addressed this somewhere else? Please link for context.

> **sixerjman said:**
> setting the gconf preference for enabling or disabling remote desktop does not address the problem of vino-server not running. The gconf preference is polled. If you set it and vino is not running, vino will be launched. If you clear it and vino is running, vino will be killed. If you are not experiencing this behavior, you may have found a bug. Please test from a LiveCD or a fresh install and if the problem persists in that environment, file a bug report.

> **sixerjman said:**
> At some point if the vino-server crashes, Crashes are caused by bugs. If you can reproduce the crash consistently, please file a report. 

> **sixerjman said:**
> dbus-launch fails to start vino-server if the X11 authentication is not done. This is by design. Vino only works on locally logged in X11 sessions. If you need a system for remote sessions only, try tightvncserver, vncserver, or one of the other vnc servers. Alternatively, I highly recommend freenx, as it provides persistent sessions and is much faster.

---

### Post by johnkzin on 2009-07-12
Is there a way to get vino (at the command line OR the GUI) to only accept connections via localhost?  or to specify a port number (5901, 5902, etc.)?


I ask, because this documentation:

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

says vino has an "advanced" tab for restricting access to localhost ... but the GUI control for vino under 9.04 doesn't show an advanced tab.  I started to look at the command line options, to see if it was just missing from the GUI control (but that the underlying functionality might still be there).  But I haven't found those options anywhere.

Is there another widget for controlling vino?  Is the stuff in the "Advanced tab" still there, but only accessible via the command line?

But, really, what I want is:

1) make vino accessible only via localhost (ie. must use SSH)
2) make vino use a port of my choosing (or fail; don't choose a different port)

---

### Post by bobpaul on 2009-07-12
> **johnkzin said:**
> Is there a way to get vino (at the command line OR the GUI) to only accept connections via localhost?  or to specify a port number (5901, 5902, etc.)?


1. Install gconf-editor. It will show up as Applications->System Tools-> Configuration Editor.

2. Browse to /desktop/gnome/remote_access

3. Set "network_interface" to "lo" for local access only.

4. Modify "alternative_port" to change the port used. Additionally, check the box next to "use_alternative_port".

Settings apply immediately. Simply close "Configuration Editor" when you're done.

> **johnkzin said:**
> I ask, because this documentation:

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

That documentation is out of date. The advanced tab was removed a number of releases ago. I'm not sure why.

---

### Post by johnkzin on 2009-07-12
Thanks very much!  exactly what I needed.

---

### Post by InkyDinky on 2009-11-13
For those that stumble upon this thread trying to start vino from the cli via a remote ssh connection look here: [http://ubuntuforums.org/showthread.php?t=1017746]("http://ubuntuforums.org/showthread.php?t=1017746")
at post #7 
```
1. ssh to that machine and authenticate as x
2. sudo -s to become root
3. export DISPLAY=:0.0
4. xhost +
5. exit from root shell using exit
6. export DISPLAY=:0.0
7. start vino-server using /usr/lib/vino/vino-server

```
There may be another way but this saved my bacon after the Karmic upgrade when I needed to get my desktop and vino wasn't started.

---

### Post by Apfelfrisch on 2009-11-26
[LEFT]Thanks a lot. The first tip that works!
[/LEFT]

---

### Post by olangelsa on 2009-12-04
```

dbus-launch gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

```

Thanks mlalkaka.

You solved my problem as well. I have previously been using gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true and false to enable and disable remote desktop capabilities. However, I could not make this work in Ubuntu 9.10. But once I prefixed the command with dbus-launch, as suggested by your code above, it works perfectly.

Thank you very much.

---

### Post by marwooj on 2009-12-29
Does anybody know how to start full gnome session from Putty X11 forwarding?

---

### Post by doobiest on 2010-03-03
> **InkyDinky said:**
> For those that stumble upon this thread trying to start vino from the cli via a remote ssh connection look here: [http://ubuntuforums.org/showthread.php?t=1017746]("http://ubuntuforums.org/showthread.php?t=1017746")
at post #7 
```
1. ssh to that machine and authenticate as x
2. sudo -s to become root
3. export DISPLAY=:0.0
4. xhost +
5. exit from root shell using exit
6. export DISPLAY=:0.0
7. start vino-server using /usr/lib/vino/vino-server

```
There may be another way but this saved my bacon after the Karmic upgrade when I needed to get my desktop and vino wasn't started.

This worked perfectly for me, and really only 6 & 7 are needed.

6. export DISPLAY=:0.0
7. start vino-server using /usr/lib/vino/vino-server

I would a & actually, so /usr/lib/vino-server &

If this happens often you could create a script like I did

sudo vi /usr/local/bin/restart_vnc

insert these two lines

export DISPLAY=:0.0
/usr/lib/vino/vino-server &

save (:wq)

sudo chmod +x /usr/local/bin/restart_vnc


Also the gconf tips here dont work. I'm sure that toggles the config options but doesnt restart a crashed server.

Also I've experienced that SSH -X or -Y and issuing vino-preferences doesnt work. What is actually does it spawn a vino server on the client machine (if linux i guess) so when you vnc through your ssh tunnel it just loops back to your clients desktop.

---

### Post by bobpaul on 2010-03-03
> **doobiest said:**
> 
Also I've experienced that SSH -X or -Y and issuing vino-preferences doesnt work. What is actually does it spawn a vino server on the client machine (if linux i guess) so when you vnc through your ssh tunnel it just loops back to your clients desktop.

If you ssh in and execute vino-preferences, it's running on the remote machine; only the UI is forwarded to the local X11 server. vino-preferences running in this way does not have access to the files/services on the local machine anymore than it would if you were sitting at the remote machines keyboard and running vino-preferences there. If vino-server was running on your local machine, it's either because it was already running or you ran vino-preferences on the local machine instead of the remote host.

You stated "so when you vnc through your ssh tunnel"... How did you have your port tunnel (-L) setup? My guess is you connected to the local vnc server on localhost directly instead of connecting to the ssh client's port tunnel. It didn't loop back... it never even left your machine.

---

### Post by doobiest on 2010-03-03
#ssh -X destination
#vino-preferences
*close vino-preferences
#ps aux|grep vino (shows the server running now)
#vncviewer -via destination localhost (executed locally, not in the ssh session)

This redirected me to my local vncsession, not the remote one. And No I have verified that the vino-server is not running locally on my client

It's completely reproducable I jsut did it right now again.  It does run vino-server on the remote computer but it's attached to my local X display, not the remote one.  If I close the ssh connection, then of course it stops vncing to my local session and doesnt vnc to the remote session either.  The processing for the service might be occuring remotely but the routing is still going local.

---

### Post by doobiest on 2010-03-03
There's no level of technical accuracy here but this should describe what is happening.

[vncviewer]-->[ssh tunnel]-->[remote vnc server]
[local X  ]<--[ssh tunnel]<--[remote vnc server]
[local X  ]-->[ssh tunnel]-->[remote vnc server]
[vncviewer]<--[ssh tunnel]<--[remote vnc server]

(Following the arrows, read some lines left to right and some lines right to left)

ps aux|grep vino-server on Local box = NO
ps aux|grep vino-server on Remote box = YES

Are we certain that X11 Forwarding ISNT bi-directional?  It sure seems that way to me.

---

### Post by tormod on 2010-04-08
Yes, doobiest is right, just running vino-preferences over an X11-forwarding ssh session might start a vino-server controlling the local (to you) display. This was also mentioned here [http://ubuntuforums.org/showpost.php?p=6412467&postcount=4](http://ubuntuforums.org/showpost.php?p=6412467&postcount=4)

You can verify which X server (display) the vino-server is controlling with:
```
cat /proc/`pgrep vino-server`/environ | tr '\0' '\n'|grep DISPLAY
```
If it shows DISPLAY=:0.0 it is the local display on the remote machine, thus the remote screen (which you most likely want to access). If it shows for instance DISPLAY=localhost:10.0 it is tunneling back through your X11-forwarding ssh connection and thus to your local screen and you get a loop.

The use of dbus-launch lets vino-server be started by the dbus server running in the remote session, so that it connects to the display of that session.

---

### Post by tormod on 2010-04-08
So here is how to make this work (tested on Ubuntu 9.10):
Connect with ssh -X to your remote machine. Find the dbus address of the processes in the desktop session running "locally" on the remote machine, for instance the nautilus process:
```
cat /proc/`pgrep nautilus`/environ | tr '\0' '\n' | grep DBUS
```
Now start vino-preferences on the remote machine but set the DBUS address which you found above:
```
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-blahblah... vino-preferences
```
You can now run vinagre on your local machine.

On the other hand, the use of dbus-launch with gconftool-2 makes vinagre start on the right display, however the changes made in the vino-preferences GUI are not applied to the started server. At least that was what happened here, where I ended up with a bunch of dbus and gconf servers running. Even if I turned off the "You must confirm each access to this machine" in the GUI, this option stayed on for the started vino-server, so I could not connect to the unattended machine.

---

### Post by doobiest on 2010-04-08
Thanks thats actually very helpful.  I need to take a deeper look at that.

I'll post this again, because I think what you posted may be too complicated for some users who don't have the background knowledge in this area.

Making a script like is worked great for me. I usually find vino crashes (inconsistently) when I'm using the clipboard.  I can run vnc_restart from ssh easily to gain access again.

doobiest@LinuxBox:/usr/local/bin$ cat vnc_restart 
export DISPLAY=:0.0
/usr/lib/vino/vino-server &

---

### Post by dekelev on 2010-11-12
Quick & Easy setup for connecting to a gnome session on ubuntu 10.04


configure the user on the remote computer:
1. remove /home/user/.gnome2/keyring/default.keyring or login.keyring
2. run command: sudo apt-get install libpam-keyring
3. append to /etc/pam.d/gdm:  @include common-pamkeyring
4. log out and back
5. set 'System->Prefrences->Remote Desktop' ---> when you asked to enter a keyring give an empty password

every time you want to connect from a client computer:
vncviewer -via remote_host localhost:0
OR
vnc into port 5900 at ip_address from any vnc client

Enjoy!

---

### Post by mattnworb on 2011-01-24
> **dekelev said:**
> Quick & Easy setup for connecting to a gnome session on ubuntu 10.04


configure the user on the remote computer:
1. remove /home/user/.gnome2/keyring/default.keyring or login.keyring
2. run command: sudo apt-get install libpam-keyring
3. append to /etc/pam.d/gdm:  @include common-pamkeyring
4. log out and back
5. set 'System->Prefrences->Remote Desktop' ---> when you asked to enter a keyring give an empty password

every time you want to connect from a client computer:
vncviewer -via remote_host localhost:0
OR
vnc into port 5900 at ip_address from any vnc client

Enjoy!

This has the nasty side-effect of storing any passwords that you save in applications (such as Pidgin or Thunderbird) in plaintext, under ~/.gnome2/keyrings. 

Since your user is logged into the machine automatically, then effectively anyone who has physical access to the machine can force a restart and then, if they know where to look, find your passwords.

---

### Post by laciba on 2011-02-17
Another simple workaround that did the trick for me,
in case you unfortunately logged out or rebooted the remote 
machine and no automatic login was set previously. 
(and if  you even want to use vino-server as vnc server after this annoying fact)

The method requires only common sense :)

1.ssh <remote IP> (without -X)
2.sudo -s
3.apt-get install x11vnc (if not yet installed)
4.x11vnc -rfbport 5901 (or use any port not configured for vino-server)
 (you may also have to configure a new tunnel for 5901 port if you played the secure way)  
5. now you can reach logon screen with any  vncviewer connecting to the 5901 port
6. logon to the remote machine and after that close vncviewer (this also halts the x11vnc server)
7. reconnect to the original vino-server on the original 5900 port.

---

### Post by kruykaze on 2011-05-13
> **laciba said:**
> Another simple workaround that did the trick for me,
in case you unfortunately logged out or rebooted the remote 
machine and no automatic login was set previously. 
(and if  you even want to use vino-server as vnc server after this annoying fact)

The method requires only common sense :)

1.ssh <remote IP> (without -X)
2.sudo -s
3.apt-get install x11vnc (if not yet installed)
4.x11vnc -rfbport 5901 (or use any port not configured for vino-server)
 (you may also have to configure a new tunnel for 5901 port if you played the secure way)  
5. now you can reach logon screen with any  vncviewer connecting to the 5901 port
6. logon to the remote machine and after that close vncviewer (this also halts the x11vnc server)
7. reconnect to the original vino-server on the original 5900 port.

sudo x11vnc -rfbport 5901 works very well thank you

---

### Post by Byb on 2013-03-07
> **srf21c said:**
> NOTE:  At long last here's the updated method...
root@remotebox:~# xhost +

Glad to find someone dug this problem and shares 
Although, now I've set my ssh stuff along with the recommended burden of keys authentication, when I issue the xhost + command 
I get this and can't go further
```
root@pc:~# xhost +
No protocol specified
No protocol specified
xhost:  unable to open display ":0.0"
```
Please what is going wrong? I am using LTS12.04.2 with gnome-panel on both computers.
Thank you

---

### Post by tormod on 2013-03-07
> **Byb said:**
> Glad to find someone dug this problem and shares 
Although, now I've set my ssh stuff along with the recommended burden of keys authentication, when I issue the xhost + command 
I get this and can't go further
```
root@pc:~# xhost +
No protocol specified
No protocol specified
xhost:  unable to open display ":0.0"
```
Please what is going wrong? I am using LTS12.04.2 with gnome-panel on both computers.
Thank you

FAIL: logged in as root
FAIL: running xhost +
Possible fail: did not read through the thread

I think I posted correct instructions earlier in this thread.

Tormod

---

### Post by radiobuzzer on 2013-05-23
Your solution does not work in 12.04 
 
cat /proc/`pgrep nautilus`/environ

does not return any DBUS

---

### Post by tormod on 2013-05-24
> **radiobuzzer said:**
> Your solution does not work in 12.04 
 
cat /proc/`pgrep nautilus`/environ

does not return any DBUS

There is no nautilus process in a 12.04 unity session. Use some other process, say, unity.

---

### Post by radiobuzzer on 2013-05-30
So, I couldn't found unity, as I haven't logged in there yet. So I tried with unity-greeter:

```

$ sudo cat /proc/`pgrep unity-greeter`/environ | tr '\0' '\n' | grep DBUS
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-wyRkJe0STA,guid=823c604472e72cb51caf5b090000004b
$ DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-wyRkJe0STA,guid=823c604472e72cb51caf5b090000004b vino-preferences 
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 key
(vino-preferences:10156): Gtk-WARNING **: cannot open display: :0.0
$ #also as sudo
$ sudo DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-wyRkJe0STA,guid=823c604472e72cb51caf5b090000004b vino-preferences 
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 key
(vino-preferences:10158): Gtk-WARNING **: cannot open display: :0.0

```

As you see I am getting an error cannot open display

---

### Post by tormod on 2013-05-31
> **radiobuzzer said:**
> So, I couldn't found unity, as I haven't logged in there yet. So I tried with unity-greeter:

As you see I am getting an error cannot open display
My instructions were for connecting to an already running session. If you don't have a session running, you may as well just use ssh -X and launch any applications remotely as you can see earlier in this thread. Or use autologin which also has been discussed earlier in this thread. Or try laciba's solution.

---

### Post by radiobuzzer on 2013-06-15
> **tormod said:**
> My instructions were for connecting to an already running session. If you don't have a session running, you may as well just use ssh -X and launch any applications remotely as you can see earlier in this thread. Or use autologin which also has been discussed earlier in this thread. Or try laciba's solution.

I would appreciate a solution to start a session only when I want to. This used to happen with the other solution, which is not working any more (I could also see the unity greeter). If there is a session already running, vino/vnc server is also there, so I don't see the reason to use your solution

---

### Post by jasem-elayeb on 2014-02-05
> **motin said:**
> Very interesting. Although I am in the same situation I cannot really use your guide, since I am using Putty from Windows... Can you maybe add some comments on how to achieve the same stuff in my situation? In case you know of course...


use xming with putty

---

