---
title: "Issues setting up VNC Over SSH"
date: 2007-03-29
forum: Server Platforms
---

### Post by silurius on 2007-03-29
[SIZE="1"]***Resolved 3/31/2006, but other issues arose and were logged _[in this thread]("http://ubuntuforums.org/showthread.php?t=399842").***[/SIZE]_

I'm attempting to implement VNC over SSH on a web server using default configurations and ports, and am hitting a wall.  I have read the [VNCOverSSH guide]("https://help.ubuntu.com/community/VNCOverSSH"), and SSH is working great.  My issue involves the [fifth step]("https://help.ubuntu.com/community/VNCOverSSH#head-f09843431b09ba40966092f04f15548732d97fed-2"):

[INDENT]__________________________________________
[FONT="Arial"]To enable a listening VNC server on the server computer, enter this command into a terminal prompt:[/FONT]

[FONT="Lucida Console"][COLOR="Navy"]vncserver :1[/COLOR][/FONT]

[FONT="Arial"]The first time you do this, you'll be prompted for a password to use for incoming connections:[/FONT]

[FONT="Lucida Console"][COLOR="Navy"]You will require a password to access your desktops.

Enter, and verify the password you wish to use to access the server's desktop from the client computer.[/COLOR][/FONT]

[FONT="Arial"]You should then see startup messages from the VNC server similar to the following:[/FONT]

[FONT="Lucida Console"][COLOR="Navy"]New 'X' desktop is hendrix:1

Creating default startup script /home/jimi/.vnc/xstartup
Starting applications specified in /home/jimi/.vnc/xstartup
Log file is /home/jimi/.vnc/hendrix:1.log[/COLOR][/FONT]
__________________________________________[/INDENT]


This is where things differ.  For me, when I entered [FONT="Lucida Console"][COLOR="Navy"]vncserver :1[/COLOR][/FONT], I was indeed prompted to create a password.  But the rest of the result is simply:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]A VNC server is already running as :1[/COLOR][/FONT][/INDENT]

When I entered [FONT="Lucida Console"][COLOR="Navy"]vncserver :1[/COLOR][/FONT] a second time, I was not prompted for the password again so I assume it was stored somewhere and that some part of this is functioning.

I don't have a clue where I should be troubleshooting.  What should I do next?

**Edit:** Hmm, this is interesting.  When I simply type [FONT="Lucida Console"][COLOR="Navy"]vncserver[/COLOR][/FONT], I get (where *useraccount* is my user's account name, etc.):

[INDENT][FONT="Lucida Console"][COLOR="Navy"]Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

New 'X' desktop is hostname.domain.com:2

Creating default startup script /useraccount/.vnc/xstartup
Starting applications specified in /useraccount/.vnc/xstartup
Log file is /useraccount/.vnc/hostname.domain.com:2.log[/COLOR][/FONT][/INDENT]

---

### Post by silurius on 2007-03-29
Another clue.  The guide directs me to paste this into the very bottom of the **/etc/vnc.conf** file which I did:

```
$fontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/misc,";
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/cyrillic,";
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/100dpi/:unscaled,";
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/75dpi/:unscaled,";
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/Type1,";
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/CID,";
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/100dpi,";
$fontPath .= "[COLOR="Red"]/usr/share/X11[/COLOR]/fonts/75dpi,";
# paths to defoma fonts
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,";
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID";
```

Although X11 is installed (shows as such in the Synaptic Package Manager), the **X11** folder does not exist in the **/usr/share/** path.

What might this mean?

---

### Post by silurius on 2007-03-29
Just to clarify what I'm seeing: On a Windows machine, I launch VNC (tried both UltraVNC and TightVNC) and point it to either the hostname or the IP, both of which I can ping.  Error: "[COLOR="Red"]Failed to connect to the server![/COLOR]".

I do have Firestarter installed, but I opened up my VNC port, enabled all connections from my client machine, and even turned off the firewall to no avail.  No events show up in the log either, so I think the VNC server is just not running.

---

### Post by scxtt on 2007-03-29
it's probably best to start over from scratch w/ running vncservers, so do:

vncserver -kill :1

and make sure no more are running by doing **ps -ef | grep vnc** and see if you see a :2 or :3 ...

then just type **vncserver** - it'll start one on the next :X available ...

as far as fonts go, that should be defined just fine by /etc/X11/xorg.conf - i don't have a **/usr/share/X11/fonts** directory either - but i do have the X11 folder ...

---

### Post by Mr. C. on 2007-03-29
You can't move onto the client to connect, until you have the server running correctly.

Your error messages is telling you 1) you alread had a vncserver listening, and 2) that it started another one on the second port :2.  Use :

netstat -n | grep 590[0-9]

to verify to yourself that a vncserver is listening already, and on which ports.

MrC

---

### Post by silurius on 2007-03-29
> **scxtt said:**
> it's probably best to start over from scratch w/ running vncservers, so do:

vncserver -kill :1

and make sure no more are running by doing **ps -ef | grep vnc** and see if you see a :2 or :3 ...

then just type **vncserver** - it'll start one on the next :X available ...

as far as fonts go, that should be defined just fine by /etc/X11/xorg.conf - i don't have a **/usr/share/X11/fonts** directory either - but i do have the X11 folder ...
Ran [FONT="Lucida Console"][COLOR="Navy"]vncserver -kill :1[/COLOR][/FONT] and got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]Can't find file /[USERACCOUNT]/.vnc/[HOSTNAME].[DOMAIN].com:1.pid
You'll have to kill the Xtightvnc process manually[/COLOR][/FONT][/INDENT]

Ran [FONT="Lucida Console"][COLOR="Navy"]ps -ef | grep vnc[/COLOR][/FONT] and got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]root      5370  5352  0 14:54 pts/0    00:00:00 grep vnc[/COLOR][/FONT][/INDENT]

(no :2 or :3)

Tried running [FONT="Lucida Console"][COLOR="Navy"]vncserver[/COLOR][/FONT] anyway, and got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

New 'X' desktop is [HOSTNAME].[DOMAIN].com:2

Starting applications specified in /root/.vnc/xstartup
Log file is /[USERACCOUNT]/.vnc/[HOSTNAME].[DOMAIN].com:2.log[/COLOR][/FONT][/INDENT]

---

### Post by silurius on 2007-03-29
> **Mr. C. said:**
> You can't move onto the client to connect, until you have the server running correctly.

Your error messages is telling you 1) you alread had a vncserver listening, and 2) that it started another one on the second port :2.  Use :

netstat -n | grep 590[0-9]

to verify to yourself that a vncserver is listening already, and on which ports.

MrCNo result, unfortunately.

Thanks for the replies, by the way.

---

### Post by silurius on 2007-03-29
Just tried: [FONT="Lucida Console"][COLOR="Navy"]kill Xtightvnc[/COLOR][/FONT] and got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]-bash: kill: Xtightvnc: arguments must be process or job IDs[/COLOR][/FONT][/INDENT]

Not sure how to get the process ID so I can kill it.  But that may not be necessary, as I don't even see it listed in xfce4-taskmanager.

---

### Post by Mr. C. on 2007-03-29
ps -ef | grep -i vnc

The PID is the number in the second column.

MrC

---

### Post by silurius on 2007-03-29
> **Mr. C. said:**
> ps --ef | grep -i vnc

The PID is the number in the second column.

MrCRan [FONT="Lucida Console"][COLOR="Navy"]ps --ef | grep -i vnc[/COLOR][/FONT] and got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]ERROR: Unknown gnu long option.[/COLOR][/FONT][/INDENT]

Ran [FONT="Lucida Console"][COLOR="Navy"]ps -e -f | grep -i vnc[/COLOR][/FONT] and got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]root      5382     1  0 14:55 pts/0    00:00:00 Xtightvnc :2 -desktop X -lf 1024
 -auth /root/.Xauthority -geometry 1024x768 -depth 24 -rfbwait 120000 -rfbauth /
root/.vnc/passwd -rfbport 5902 -co /etc/X11/rgb
root      6124  5352  0 16:00 pts/0    00:00:00 grep -i vnc[/COLOR][/FONT][/INDENT]

Killed process 5382 (no feedback given).  Ran [FONT="Lucida Console"][COLOR="Navy"]ps -e -f | grep -i vnc[/COLOR][/FONT] again and got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]root      6132  5352  0 16:06 pts/0    00:00:00 grep -i vnc[/COLOR][/FONT][/INDENT]

Killing process 5382 seems to have no effect.  Launching vncserver generates an error similar to the above:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

New 'X' desktop is [HOSTNAME].[DOMAIN].com:2

Starting applications specified in /root/.vnc/xstartup
Log file is /[USERACCOUNT]/.vnc/[HOSTNAME].[DOMAIN].com:2.log[/COLOR][/FONT][/INDENT]

---

### Post by Mr. C. on 2007-03-29
Sorry, stupid typo on my part.  Single dashes.   I'll correct above.

Looks like you found your second process.

vncserver -kill does the same thing, but you have to give it the instance number.

MrC

---

### Post by scxtt on 2007-03-29
what's the contents of **~/.vnc** (do **ls -l ~/.vnc**)?  i think if there is a *.pid file associated w/ :1, you'll always get new sessions starting @ :2 ...

i've gotten *Please set correct fontPath in the vncserver script.* - but i'm still able to connect to the VNC server at the respective :X connection ...

---

### Post by silurius on 2007-03-29
> **scxtt said:**
> what's the contents of **~/.vnc** (do **ls -l ~/.vnc**)?  i think if there is a *.pid file associated w/ :1, you'll always get new sessions starting @ :2 ...

i've gotten *Please set correct fontPath in the vncserver script.* - but i'm still able to connect to the VNC server at the respective :X connection ...If I browse to that folder in a terminal, I see:

[INDENT][FONT="Lucida Console"][COLOR="Navy"][USERACCOUNT].[HOSTNAME].[DOMAIN].com:2.log
[USERACCOUNT].[HOSTNAME].[DOMAIN].com:2.pid
passwd
xstartup[/COLOR][/FONT][/INDENT]

If I run [FONT="Lucida Console"][COLOR="Navy"]ls -l ~/.vnc[/COLOR][/FONT] I get:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]passwd
xstartup[/COLOR][/FONT][/INDENT]

---

### Post by silurius on 2007-03-29
Just ran [FONT="Lucida Console"][COLOR="Navy"]vncserver -kill :1[/COLOR][/FONT] and it successfully killed Xtightvnc process ID 9995.  Running a [FONT="Lucida Console"][COLOR="Navy"]ps -ef | grep vnc[/COLOR][/FONT] again, I got:

[INDENT][FONT="Lucida Console"][COLOR="Navy"]Please set correct fontPath in the vncserver script.

New 'X' desktop is [HOSTNAME].[DOMAIN].com:2

Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/[HOSTNAME].[DOMAIN].com:2.log[/COLOR][/FONT][/INDENT]

which looks OK.  But still no worky.  Same error on the client side.

---

### Post by scxtt on 2007-03-29
how exactly are you trying to connect?  you've got a vncserver running on :2 ... so when you fire up a vncviewer, you should enter something like:

<IP of vncserver host>:2
(ex. 192.168.1.100:2)

---

### Post by silurius on 2007-03-29
> **scxtt said:**
> how exactly are you trying to connect?  you've got a vncserver running on :2 ... so when you fire up a vncviewer, you should enter something like:

<IP of vncserver host>:2
(ex. 192.168.1.100:2)Aha, that actually worked.  Didn't realize I had use the ":2" on the client side.  Thanks!

However, it looks like this is not the exact flavor of VNC I was hoping to enable.  I would like to view the actual xfce session that happens to be running.  Until I feel more comfortable with Ubuntu (and until my server is generally stable and ready for application development), I need the flexibility of having a fully-functional remote GUI.  I recall seeing a VNC server package for that before, but now I'm not seeing it in my searches.

Just in case I'm really stuck with this variant of VNC, is there documentation on what is and isn't possible?  A terminal window was up in the VNC session, for example, but when I closed it I was unsure how to relaunch it again.

---

### Post by scxtt on 2007-03-29
if you want to use your current session - install a package called **x11vnc** ... then run it as follows:

x11vnc -rfbauth ~/.vnc/passwd -display :0 &

that'll use your already existing VNC password to protect this session too ... and as soon as you close the client, the session is terminated (unless you tell it otherwise) ...

then connect via **vncviewer <IP address>:0**

---

### Post by silurius on 2007-04-02
> **scxtt said:**
> if you want to use your current session - install a package called **x11vnc** ... then run it as follows:

x11vnc -rfbauth ~/.vnc/passwd -display :0 &

that'll use your already existing VNC password to protect this session too ... and as soon as you close the client, the session is terminated (unless you tell it otherwise) ...

then connect via **vncviewer <IP address>:0**Excellent!  I'm in good shape now and shall rack the server.  You've been a great help to me.

So just to clarify, assuming I don't reconfigure X, Xfce or VNC and I leave my Xfce login session open (but locked), I should not have issues accessing my system over Session 2 going forward?  Is that correct, or are there exceptions I should be aware of?

It's clear that VNC stops running altogether when I log out of Xfce and face a login prompt.  Are there tricks to enable me to VNC into that screen, or even to a command prompt or something? I'm trying to train myself on remoting in under different conditions, and logging in just after a reboot is the one scenario I can imagine happening a lot.

---

### Post by silurius on 2007-04-02
Well I might have answered part of my questions, by creating an x11vnc_startup.sh script, placing that in my user folder, and calling it automatically from Startup Applications in Xfce.

[INDENT][FONT="Lucida Console"][COLOR="Navy"]# Launches VNC server.  Remote client connects to current session.
x11vnc -rfbauth ~/.vnc/passwd -display :0 &[/FONT][/COLOR][/INDENT]

Strangely, when I ran the script manually to test, although my terminal session gave output that looked encouraging, I'm getting the "VNC authentication failed!" on the client end now.

Looking at the server during that failure, I see:

[INDENT][FONT="Lucida Console"][COLOR="Navy"][MYUSER]@[MYSERVER]:~$ 02/04/2007 10:19:02 Got connection from client [MYIP]
02/04/2007 10:19:02   other clients:
02/04/2007 10:19:02 Disabled X server key autorepeat.
02/04/2007 10:19:02   to force back on run: 'xset r on' (3 times)
02/04/2007 10:19:02 created xdamage object: 0x1e0002f
02/04/2007 10:19:03 Client Protocol Version 3.4
02/04/2007 10:19:03 Protocol version sent 3.4, using 3.4
02/04/2007 10:19:16 Couldn't read password file: /home/[MYUSER]/.vnc/passwd
02/04/2007 10:19:16 rfbAuthProcessClientMessage: password check failed
02/04/2007 10:19:16 client_count: 0
02/04/2007 10:19:16 Restored X server key autorepeat to: 1
02/04/2007 10:19:16 connect_once: invalid password or early disconnect.
02/04/2007 10:19:16 connect_once: waiting for next connection.
02/04/2007 10:19:16 Client [MYIP] gone
02/04/2007 10:19:16 Statistics             events    Transmit/ RawEquiv ( saved)
02/04/2007 10:19:16  TOTALS              :      0 |         0/        0 (  0.0%)
02/04/2007 10:19:16 Statistics             events    Received/ RawEquiv ( saved)
02/04/2007 10:19:16  TOTALS              :      0 |         0/        0 (  0.0%)
02/04/2007 10:19:17 destroyed xdamage object: 0x1e0002f
[MYUSER]@[MYSERVER]:~$ [/FONT][/COLOR][/INDENT]

Why would it be failing at this point?

Any other best practice tips or gotcha warnings?

---

### Post by silurius on 2007-04-02
OK I caught part of the problem -- needed to su prior to running command first.

Now the question is, how to have it autostart without authenticating as super user, or how to protect su password in some way?

Again, best practice guidelines catered for a N00b (read: verbose/explicit) would be most appreciated.

**Edit:** Just spotted **fluxbox **and **fluxboxconf**.  Starting to look into what those might offer me....

---

### Post by silurius on 2007-04-02
OK I don't believe fluxbox is what I need.  I got into a fluxbox session, but it's a little too lightweight for my needs (unless I'm a dope -- couldn't do anything after logging in).  I'm going to stick with Xfce and start a new thread for my remaining issues.

---

### Post by Cato2 on 2008-06-06
Here's what I just did to get VNC working over SSH on Ubuntu Gutsy 7.10 (should work on any release really).  Specifically I used Xubuntu, but this should work on other Ubuntu flavous just as well.

**Summary:** this lets you open up only the SSH port on your remote PC, which is important as VNC is not a secure protocol - it doesn't use encrypted passwords or data, so you should NOT simply set it up without SSH for Internet remote access.  

This mini HOWTO assumes:

1. An Ubuntu PC ('server') with a permanent X display that you need to connect to from a remote system - the server should be a desktop PC where someone is usually logged in and you want to see exactly what issues they are having and help fix any problems.

2. NAT router serving the 'server' desktop PC 

3. This NAT router has a static Internet address (or can use dynamic DNS)

4. NAT router can port-forward as required to the desktop PC

On the Ubuntu system that you want to access remotely (i.e. the server):

1. Install SSH server and client on your Ubuntu server (desktop PC): "sudo aptitude install openssh-server openssh-client" and configure a static IP address for your desktop PC (see Network Manager for details, or edit "/etc/network/interfaces" to look something like this, for whatever your LAN address range is:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.99
        netmask 255.255.255.0
        gateway 192.168.0.1

```
Gateway is your NAT firewall/router.

2. If this is going to be Internet accessible, I'd recommend not using port 22 (the default) - instead, pick a random port (or one that your NAT firewall/router can forward, many of them are restricted) and use that.  This random port number simply reduces 'door knocking' probes on port 22, it does NOT make your server secure on its own.  You will need to edit "/etc/ssh/sshd_config" to specify the port (see man sshd_config) and run "/etc/init.d/ssh restart" - then run "netstat -apn | grep ssh" and check sshd is listening on the port you want.

3. **Change your password to be a very strong one** - e.g. at least 10 characters, mixture of upper case, lower case, numbers and punctuation.  Ideally generate a random password that's pronounceable (Google for tools, or use 'pwgen' which is not very pronouncable in its generated passwords).  Your ONLY defence against password guessing is a strong password, as it's quite easy to test all the ports on your PC and find which one your SSH is listening on.

4. Test this locally on your server (i.e. connect to the server from itself) by doing "ssh -p NNN user@server" where NNN is the port number, user is a valid user on the 'server' and server is the hostname or IP address. 

5. Install "x11vnc" on the server, using "sudo aptitude install x11vnc" (you must have the 'universe' repository enabled via Synaptic or editing /etc/apt/sources.list).  **NOTE**: This enables you to access the actual X display being used, so it's most useful when remotely accessing a desktop PC that will usually have someone logged in - if your server is not a desktop PC, check the standard VNC server and use that.

6. Enable unattended upgrades on the remote server using "sudo aptitude install unattended-upgrades" - this ensures that any security updates that can be safely done automatically are installed without you even having to log in and run "aptitude update && aptitude safe-upgrade".  This is VERY IMPORTANT unless you monitor the Ubuntu security announcements religiously and apply updates asap.  It ensures that even if there is an SSH remote exploit announced in Ubuntu, you will get this fixed as soon as possible, reducing your vulnerability time to the minimum.

On your NAT firewall/router, configure port forwarding which means such that any TCP traffic to port NNN is forwarded. NOTE: If you are not using static IP address for your NAT firewall/router, you'll need to research a dynamic DNS tool for Ubuntu so you can use a DNS name instead.  I didn't need to do this so it's not included here.

On your local PC (client):

1.  Install SSH client, and test connecting using SSH to your server PC, i.e. ssh to localhost or whatever the server name is.  Be sure to specify port NNN, the default will not work.  NOTE:  If you're using Windows, Cygwin SSH is quite nice as its command line is identical (in fact it is the same software, ported to Cygwin).  However, for most Windows users, PuTTY will be better and it has a better terminal emulator to run vi, nano, etc.  On an Ubuntu client, just "sudo aptitude install openssh-client".

2. Now log in remotely from your client PC using your SSH client software (e.g. PuTTY), using the previously allocated port NNN.  At the shell prompt, use nano or vi to create a new file "~/start-vnc" that should contain the following: ```

# Run X11VNC against real display, assumes 'fred' logged into X
sudo x11vnc -forever -localhost -display :0 -auth /home/fred/.Xauthority
```  You need to replace 'fred' with the username of the person logged into the main X display - this will only work if this is predictable i.e. a single-user desktop PC.)
Type "chmod +x start-vnc" to make this executable.

3. Now start ANOTHER SSH session, whose only purpose is to carry VNC traffic, as follows - this is using Cygwin SSH, Putty will be similar: ```
ssh -p NNN -t -L 5900:localhost:5900 user@server ./start-vnc
```  This uses 'SSH port forwarding', aka tunnelling, nothing to do with the NAT router's port forwarding but similar in concept.  The idea is that your VNC client (viewer) contacts an SSH process on your client PC (localhost) using port 5900 - this is then tunnelled securely over the network through to the SSH server (desktop PC) where it pops out, also on port 5900.  (If you are using dynamic DNS, use your DNS name for the server.)  NOTE: You will be asked for the password for 'user' TWICE, once by SSH and once by sudo.  This is not very convenient but there is a way round this.

4. Download a suitable VNC viewer  ("sudo aptitude install xtightvncviewer" works well on Ubuntu, or UltraVNC on Windows) that supports a good compression technique (mainly tightvnc), and install this. 

Now you have everything set up for normal operation.  To connect to the remote PC:

1. Start the SSH port forwarding session as in step 3 just above.  This creates your secure SSH tunnel to the server.  You can also open a normal SSH session for terminal use, which can be handy in debugging.

2. Run your VNC viewer, say UltraVNC on Windows, and connect to localhost - you can't connect to the server directly, as VNC is not actually listening on the Ethernet interface at all (due to the "-localhost" option to x11vnc), and in any case your NAT router/firewall is only port-forwarding on port NNN.  On Ubuntu, you can use something like "xtightvncviewer -bgr233 -encoding tight localhost" to use only 8-bit colour for speed - the 'tight' is important to force use of TightVNC encoding which is efficient.

3. When you are done, close your VNC viewer and hit Ctrl/C in the SSH session started for port forwarding (or just close that client).  The x11vnc server will be killed, which helps avoid consuming resources when you're not using it.

That's it - hope this works for you.  I had a slightly different start-vnc script using 'su' but otherwise the above is what I did, and it's relatively easy to get it going all things considered.  Certainly easier than doing this on Windows in my experience, where VNC would often stop working...

The x11vnc author's page has some other tools that can automate this further, but the above may be easier to debug.

You can also start x11vnc from a KDE, GNOME or XFCE auto-start, but it's not necessary as you can just as easily start it with the SSH port-forwarding command.

Check the other HOWTOs on SSH if you have problems, and in particular for x11vnc see the parts about using x11vnc over SSH at [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/) (by author of x11vnc). Also, [http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions](http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions) is pretty good (Gento has a great wiki generally but there are some differences from Ubuntu).

---

