---
title: "Ubuntu server, multi-user remote desktop access"
date: 2009-10-27
forum: Server Platforms
---

### Post by Seamus Farrell on 2009-10-27
[B]I am having difficulty setting up vnc on a ubuntu server so that multiple authorised users can log to establish remote desktop sessions, without anyone needing to be logged in at the console.  While we can easily get remote command line access (putty / ssh), we need the graphical interface e.g. for eclipse.
An attempt to log in from Windows using RealVNC's VncViewer, connecting to port 5901, 5902, or 5903, fails with an immediate message "The connection closed unexpectedly".  Attempts to connect to other unconfigured ports fail as expected with a "connection refused" error.
I did succeed in getting remote desktop access using xming, but it was far too slow to be practical.  In my previous job there was the kind of setup I'm trying to get working here and it was very successful.  That was under Centos 5.

I've described below what I did.  I'm sorry for the verbose description, but since I'm not sure where it's going wrong, I don't know which detail to leave out.  I've tried searching the internet and found lots of threads dealing with similar difficulties with some solutions, but none seem to deal with exactly my situation, and the solutions refer to files not present on my system.

I'm a newbe to ubuntu, and a comparative newbe to linux.  I would appreciate any help, or directions to elsewhere I might try.
----------------------------------------------------------

My system is Ubunto 9.04 64-bit server
From uname -a I get
Linux dh15k 2.6.28-16-server #55-Ubuntu SMP Tue Oct 20 20:37:10 UTC 2009 x86_64 GNU/Linux
For now at least, I'm trying all of this within a local network.

Here's what I did:
1.  Using the Synaptic Package Manager, I installed the vnc4server (installed
version 4.1.1+x.org 1.0.2-0ubuntu7)

2.    To /etc/services, I added the following lines:
#----------------------------------------------------
vnc-1   5901/tcp
vnc-2   5902/tcp
vnc-3   5903/tcp
#----------------------------------------------------

3.  I added a file /etc/xinetd.d/xnvserver with the following content:
#-------------------------------------------
service vnc-1  
{  
    disable         = no
    socket_type  = stream
    protocol       = tcp
     wait            = no
    user            = nobody
    server         = /usr/bin/Xvnc
server_args = -inetd -query localhost -once -geometry 640x480 -depth 8 securitytypes=none log_on_failure += USERID IdleTimeout=604800
}

service vnc-2
{
 disable = no
 socket_type = stream
 protocol = tcp
 wait = no
 user = nobody
 server = /usr/bin/Xvnc
 server_args = -inetd -query localhost -once -geometry 800x600 -depth 16 securitytypes=none log_on_failure += USERID IdleTimeout=604800
}


service vnc-3
{
 disable = no
 socket_type = stream
 protocol = tcp
 wait = no
 user = nobody
 server = /usr/bin/Xvnc
 server_args = -inetd -query localhost -once -geometry 1000x760 -depth 16 securitytypes=none log_on_failure += USERID IdleTimeout=604800
}
#-------------------------------------------------------------------------------
4.  I started System/Administration/Login Window and on the Remote tab, set style to be "Same as Local". I clicked on the "Configure XDMCP" button and ticked the box "Honor indirect requests".
Using ctrl-backspace I restarted GDM.

5.  I restarted xinetd:
sudo /etc/init.d/xinetd restart
* Stopping internet superserver xinetd
* Starting internet superserver xinetd

Using the log viewer, from Syslog I can see that xinet.d has restarted.  The log entries include the following:
Oct 27 15:31:01 dh15k xinetd[17031]: Reading included configuration file: /etc/xinetd.d/vncservers [file=/etc/xinetd.d/vncservers] [line=28]
and
Oct 27 15:31:01 dh15k xinetd[17031]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Oct 27 15:31:01 dh15k xinetd[17031]: Started working: 3 available services

6.   To verify that my network or my vncviewer are not the source of the problem, I enabled a remote desktop:
/System/Preferences/Remote Desktop
I ticked the "Allow other users to view your desktop" and the "Allow other users to control your desktop".
Having done so, using vncviewer on the Windows system I was able to connect to my ubuntu system (xxx.xxx.xxx:0)and got the full desktop as expected.

This is probably the wrong place to be asking this, and no doubt it's a problem already well solvedin ubuntu, but I can't find what to do.

What next ??

Thanks in advance.

[/B]

---

### Post by scorp123 on 2009-10-27
Why not X-over-SSH ??
```
ssh -X remote-user@server /usr/bin/eclipse
```

You could even launch a full desktop session that way if you like ...
```
ssh -X remote-user@server /usr/bin/gnome-session
```


In our own environment @work we use this professional solution from Sun:
[http://wikis.sun.com/display/VDI3dot1/Home](http://wikis.sun.com/display/VDI3dot1/Home)

That way everyone gets their own private Ubuntu VM and they can do in there whatever they like.

But maybe such a solution would be overkill for you ... ?

---

### Post by scorp123 on 2009-10-27
BTW ... you said you're a "newbie to Ubuntu" and "newbie to Linux" ... Is there any particular reason why you use Ubuntu?

Because this VNC remote access stuff that you want to achieve here is way easier to achieve in e.g. OpenSUSE. There all it takes is a mouse click:
[LIST]
[*]enable VNC remote access [X]
[/LIST]

And that's it. The rest is done for you automatically.

Maybe you'd like to try that? You can still use Ubuntu for other jobs ...

---

### Post by HermanAB on 2009-10-27
Hmm, VNC is mainly a Windows XP Home Edition thing.  On Linux, VNC is almost always the WRONG solution.

As suggested above, you should rather use SSH.  Install the SSH server package and then use the following magical incantation from the other desktop systems:
$ ssh -X -C -c blowfish user@server gnome-panel

This also works with Xming and PuTTY from Windows.  Do run Xming first of course, then PuTTY.

Cheers,

Herman

---

### Post by Lars Noodén on 2009-10-28
I'd second what HermanAB says about VNC and the suggestion for X forwarding.  Additionally, VNC normally needs to be tunneled over SSL or SSH anway, but with insecure clients, that is moot.  I'm not sure which is slower over high-latency (slow) nets, X over SSH or RFB (or something) over SSH.  

If you're just running a single program on the remote machine, then Scorp123's suggestion works.  

Regarding suggestions about other distros, no need.  Especially for ones without a good history of working with or for the open source community.  If you do want to try an RPM-based distro, Fedora is the most in line with Free Software goals and its parent company (Red Hat) has contributed to the community, even defending it on occasion.

Ubuntu works well.

What you are describing sounds like a matter of configuring **xinetd** since you are trying to have it govern the connections.  

To get more useful feedback from VNC while you play with it, stop it, then run it in debug mode to watch the messages.

```

sudo /etc/init.d/xinetd stop
sudo /usr/sbin/xinetd -d -dontfork

```

Also make sure that tcpd doesn't have anything blocking you in /etc/hosts.deny and /etc/hosts.allow.

---

### Post by Seamus Farrell on 2009-10-28
Thanks for your feedback.
I did succeed in running eclipse on the Ubuntu server system from Ms Windows using putty and xming (thanks for the suggestions from Scorp123 and HermanAB), but like my earlier experience with xming running the whole gnome desktop, screen response, while better, is still just too slow to be a practical solution.  Also, despite my best efforts, the fonts all looked a bit crude.  I could live with the fonts, but the speed ...
Anyway, I tried your (Lars Nooden) suggestion about starting xinetd in debug mode.  The two files hosts.allow and hosts.deny only have comments.
Below I have included what look to me like the important sections of the debug output of xinetd.  Everything looks OK to my untrained eye, so I suspect that the problem may lie with the vnc4server setup.  Is there any way that I can turn on debug or log output for vnc as well as for xinetd?
By the way, thanks again to the three of you who have answered my query.  This kind of altruistic behaviour is one of the more wonderful aspects of the Internet, and gives the lie to those who say that old-fashioned values like kindness and courtesy have no room in the modern world.
;=======================================
Service defaults
    Bind = All addresses.
    Only from: All sites
    No access: No blocked sites
    No logging

Service configuration: vnc-1
    id = vnc-1
    flags = IPv4
    socket_type = stream
    Protocol (name,number) = (tcp,6)
    port = 5901
    wait = no
    user = 65534
    Groups = no
    PER_SOURCE = -1
    Bind = All addresses.
    Server = /usr/bin/Xvnc
    Server argv = Xvnc -inetd -query localhost -once -geometry 640x480 -depth 8 securitytypes=none log_on_failure += USERID IdleTimeout=604800
    Only from: All sites
    No access: No blocked sites
    No logging

Service configuration: vnc-2 .....

09/10/28@18:39:51: DEBUG: 20919 {cnf_start_services} Started service: vnc-1
09/10/28@18:39:51: DEBUG: 20919 {cnf_start_services} Started service: vnc-2
09/10/28@18:39:51: DEBUG: 20919 {cnf_start_services} Started service: vnc-3
09/10/28@18:39:51: DEBUG: 20919 {cnf_start_services} mask_max = 8, services_started = 3
09/10/28@18:39:51: NOTICE: 20919 {main} xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
09/10/28@18:39:51: NOTICE: 20919 {main} Started working: 3 available services
09/10/28@18:39:51: DEBUG: 20919 {main_loop} active_services = 3


09/10/28@18:40:14: DEBUG: 20919 {main_loop} select returned 1
09/10/28@18:40:14: DEBUG: 20919 {server_start} Starting service vnc-1
09/10/28@18:40:14: DEBUG: 20919 {main_loop} active_services = 3
09/10/28@18:40:14: DEBUG: 21083 {exec_server} duping 9
09/10/28@18:40:14: DEBUG: 20919 {main_loop} active_services = 3
09/10/28@18:40:14: DEBUG: 20919 {main_loop} select returned 1
09/10/28@18:40:14: DEBUG: 20919 {check_pipe} Got signal 17 (Child exited)
09/10/28@18:40:14: DEBUG: 20919 {child_exit} waitpid returned = 21083
09/10/28@18:40:14: DEBUG: 20919 {server_end} vnc-1 server 21083 exited
09/10/28@18:40:14: INFO: 20919 {conn_free} freeing connection
09/10/28@18:40:14: DEBUG: 20919 {child_exit} waitpid returned = -1
09/10/28@18:40:14: DEBUG: 20919 {main_loop} active_services = 3

---

### Post by Lars Noodén on 2009-10-28
> **Seamus Farrell said:**
> 09/10/28@18:40:14: DEBUG: 20919 {server_start} Starting service vnc-1
09/10/28@18:40:14: DEBUG: 20919 {main_loop} active_services = 3
09/10/28@18:40:14: DEBUG: 21083 {exec_server} duping 9
09/10/28@18:40:14: DEBUG: 20919 {main_loop} active_services = 3
09/10/28@18:40:14: DEBUG: 20919 {main_loop} select returned 1
09/10/28@18:40:14: DEBUG: 20919 {check_pipe} Got signal 17 (Child exited)
09/10/28@18:40:14: DEBUG: 20919 {child_exit} waitpid returned = 21083

It seems to choke on trying to run vnc server, in this case Xvnc according to the configuration you posted.   
It looks like there is a start up script wrapper for [Xvnc](http://linux.die.net/man/1/xvnc) called [vncserver](http://linux.die.net/man/1/vncserver).  Those wrappers tend to exist when it is difficult to launch manually.  

Try getting that (Xvnc direct or via the vncserver wrapper) set up standalone first, then when it is working try transferring the settings to xinetd.

---

### Post by scorp123 on 2009-10-28
> **HermanAB said:**
> Hmm, VNC is mainly a Windows XP Home Edition thing.  On Linux, VNC is almost always the WRONG solution. You keep repeating that misinformation. It doesn't get true because of that, you know?

VNC was developed on Unix-like OS. Look it up. And it's not "always the wrong" solution. It can do things X-over-SSH can't, e.g. survive disconnects without having the applications die.

If you know what you want and what you do then VNC is an OK solution too. And it has nothing to do with "Windows XP Home" ... it seems you still keep mixing up VNC and RDP ???

---

### Post by scorp123 on 2009-10-28
> **Lars Noodén said:**
>  Especially for ones without a good history of working with or for the open source community.  Ever heard of "technical merits" and all that? You know ... some people don't care about politics and pick their distro based on "what works". And like it or not but in many areas Novell's products do a better job than the Debian/Ubuntu crowd. Sad but true.

(and nope, I don't like Novell's stupid deal with Microsoft either but that doesn't stop me from using their products if they fit my needs ...)

---

### Post by y@w on 2009-10-28
Ok, not really helping solve the problem at hand, but I thought I'd throw out another solution that hasn't been mentioned..

I'd check out [FreeNX]("http://freenx.berlios.de/"). I've used it in the past and it's almost as responsive as RDP in my experience.

---

### Post by scorp123 on 2009-10-28
> **y@w said:**
>  I'd check out [FreeNX]("http://freenx.berlios.de/"). 

+1

If responsiveness is an issue, then FreeNX should be given a try. FreeNX does an amazing job at compressing the traffic and the applications do feel highly responsive (better than VNC or SSH or any other mechanism)

---

### Post by mahirarif on 2009-11-01
i use a script which runs on ubuntu. i got the ubuntu pc version installed on my server. i want to grant people remote access to it. right now my friends connect to it thru VNC. i was thinking of putting the script up on my webpage. the script i have uses the terminal. is there any way so that i can only grant access to my friends just to the terminal?
 
coz VNC slows things down coz of the full desktop being shown :/

---

### Post by mahirarif on 2009-11-01
i got a ubuntu desktop version installed on my server. i want to grant ONLY terminal access to my friend back in the UK. is there a way by which i can only grant him remote TERMINAL access only?;)

---

### Post by Lars Noodén on 2009-11-02
> **mahirarif said:**
> i got a ubuntu desktop version installed on my server. i want to grant ONLY terminal access to my friend back in the UK. is there a way by which i can only grant him remote TERMINAL access only?;)

You can do that with SSH.  How much / little access do you want to allow?

---

### Post by OneMixDJ on 2009-11-02
*Hmmm....*:-k

FreeNX sounds like what I might want to consider.

I have family (absolute non-techies) who at times need for me to check their machines remotely. With that, I'm thinking that having a server set up as a "middleman" for them to connect to (maybe via browser) and grant me access to their desktops would be much easier for both parties involved.

See below, not sure if I'm trying to achieve the same objective here. 

I have a Ubuntu Server available that could be used for this purpose. 
I'm just not sure if I'm on the right track.

[IMG]http://i989.photobucket.com/albums/af14/OneMixDJ/remote-desktop-solution.jpg[/IMG]

---

### Post by jolig on 2009-11-05
Hello,

It seems that with the latest Ubuntu 9.10, the GDM configuration has changed which is limitating the number of available sessions which seems to produce that kind of behavior.

I am also looking for a solution.

---

### Post by bmullan on 2009-12-03
> **Seamus Farrell said:**
> [B]I am having difficulty setting up vnc on a ubuntu server so that multiple authorised users can log to establish remote desktop sessions, without anyone needing to be logged in at the console.  While we can easily get remote command line access (putty / ssh), we need the graphical interface e.g. for eclipse.
An attempt to log in from Windows using RealVNC's VncViewer, connecting to port 5901, 5902, or 5903, fails with an immediate message "The connection closed unexpectedly".  Attempts to connect to other unconfigured ports fail as expected with a "connection refused" error.
I did succeed in getting remote desktop access using xming, but it was far too slow to be practical.  In my previous job there was the kind of setup I'm trying to get working here and it was very successful.  That was under Centos 5.

I've described below what I did.  I'm sorry for the verbose description, but since I'm not sure where it's going wrong, I don't know which detail to leave out.  I've tried searching the internet and found lots of threads dealing with similar difficulties with some solutions, but none seem to deal with exactly my situation, and the solutions refer to files not present on my system.

I'm a newbe to ubuntu, and a comparative newbe to linux.  I would appreciate any help, or directions to elsewhere I might try.
----------------------------------------------------------

My system is Ubunto 9.04 64-bit server
From uname -a I get
Linux dh15k 2.6.28-16-server #55-Ubuntu SMP Tue Oct 20 20:37:10 UTC 2009 x86_64 GNU/Linux
For now at least, I'm trying all of this within a local network.

Here's what I did:
1.  Using the Synaptic Package Manager, I installed the vnc4server (installed
version 4.1.1+x.org 1.0.2-0ubuntu7)

2.    To /etc/services, I added the following lines:
#----------------------------------------------------
vnc-1   5901/tcp
vnc-2   5902/tcp
vnc-3   5903/tcp
#----------------------------------------------------

3.  I added a file /etc/xinetd.d/xnvserver with the following content:
#-------------------------------------------
service vnc-1  
{  
    disable         = no
    socket_type  = stream
    protocol       = tcp
     wait            = no
    user            = nobody
    server         = /usr/bin/Xvnc
server_args = -inetd -query localhost -once -geometry 640x480 -depth 8 securitytypes=none log_on_failure += USERID IdleTimeout=604800
}

service vnc-2
{
 disable = no
 socket_type = stream
 protocol = tcp
 wait = no
 user = nobody
 server = /usr/bin/Xvnc
 server_args = -inetd -query localhost -once -geometry 800x600 -depth 16 securitytypes=none log_on_failure += USERID IdleTimeout=604800
}


service vnc-3
{
 disable = no
 socket_type = stream
 protocol = tcp
 wait = no
 user = nobody
 server = /usr/bin/Xvnc
 server_args = -inetd -query localhost -once -geometry 1000x760 -depth 16 securitytypes=none log_on_failure += USERID IdleTimeout=604800
}
#-------------------------------------------------------------------------------
4.  I started System/Administration/Login Window and on the Remote tab, set style to be "Same as Local". I clicked on the "Configure XDMCP" button and ticked the box "Honor indirect requests".
Using ctrl-backspace I restarted GDM.

5.  I restarted xinetd:
sudo /etc/init.d/xinetd restart
* Stopping internet superserver xinetd
* Starting internet superserver xinetd

Using the log viewer, from Syslog I can see that xinet.d has restarted.  The log entries include the following:
Oct 27 15:31:01 dh15k xinetd[17031]: Reading included configuration file: /etc/xinetd.d/vncservers [file=/etc/xinetd.d/vncservers] [line=28]
and
Oct 27 15:31:01 dh15k xinetd[17031]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Oct 27 15:31:01 dh15k xinetd[17031]: Started working: 3 available services

6.   To verify that my network or my vncviewer are not the source of the problem, I enabled a remote desktop:
/System/Preferences/Remote Desktop
I ticked the "Allow other users to view your desktop" and the "Allow other users to control your desktop".
Having done so, using vncviewer on the Windows system I was able to connect to my ubuntu system (xxx.xxx.xxx:0)and got the full desktop as expected.

This is probably the wrong place to be asking this, and no doubt it's a problem already well solvedin ubuntu, but I can't find what to do.

What next ??

Thanks in advance.

[/B]

Did you not want to use FreeNX ??   It works great.
I install FreeNX on the "server" side and then use NoMachine's NX Client to access.

Pretty simple to setup and gets your users a desktop that is very responsive.   FreeNX also supports Samba, Cups/printing, load balancing etc.

The NXClient also supports RDP, VNC.

---

### Post by husskii on 2009-12-04
Hi mate I think I kjnow what your after I just did it my self.. If you follow these steps u will have no problem connecting via vnc.... if u have any trouble let me know and Ill help were I can...

Im guessing you already have ubuntu installed and ssh so your next step is to open terminal or putty and type the following, and agree at the prompts.

(1) #sudo apt-get install vnc4server

After it is installed you should be logged as normal user and not root.

(2) #vncserver :1 -geometry 1024x768 -depth 16
or
#vncserver :1 -geometry 1024x768 -depth 24

Once you type the above command u will prompt for password. This is the password, this is the password u will set for vnc to connect to the server. Once it is complete we can change the setting for the server. Before we do that we have to kill the server.

type the following command into terminal

(3) #vncserver -kill :1

Then

(4) nano /home/userXX/.vnc/xstartup  - (userXX = your user name)
and paste all this code (below) into it.


```
Code:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
# xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &
```

Now everything is done. All you have to do is to restart the system which is good for the setting to work properly. Once you have restarted, start the vnc server by typing the following into putty & your done.

(5) #vncserver

******for the next user follow on from step (2)
i.e (2) #vncserver :2 -geometry 1024x768 -depth 16

to (5) then restart again and start vnc server..

***IMPORTANT****
Make sure to start vnc server in the same order as the ports originally assigned for each user, otherwise which ever user u start first will be on port :1 etc

Hope this helps :)

---

