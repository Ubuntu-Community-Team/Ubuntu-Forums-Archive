---
title: "HOW TO: Resumable VNC Session Available at Startup"
date: 2007-06-29
forum: Tutorials
---

### Post by moonblink on 2007-06-29
I have a 6.06 server up and running at home and wanted to be able to administer it while at work and/or where ever.  VNC works great for this locally, but doesn't run at startup on default.  A few simple changes can fix that and make it easy to login remotely from anywhere.   I can later explain how I setup my Linksys router (WRT54GL updated with DD-WRT firmware)  connect up to no-ip.com for dynamic/static IP purposes (I have a standard home cable setup) and use SSH to putty and work on my server from anywhere (if anyone is interested)

This is not my original idea nor did I write any of this code.  I compiled this from a number of sources and made it easy to understand (I hope).

How to:  Resumable VNC sessions locally or via SSH. 
 

1. Install x11vnc & xinetd package (if you have not already)


```
sudo apt-get install x11vnc xinetd
```


2. Set the VNC passwd


```
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```


3. Add x11vnc service to xinetd:


```
sudo gedit /etc/xinetd.d/x11vnc
```


Enter this into the new file:



```
service x11vnc

{

        port            = 5900

        type            = UNLISTED

        socket_type     = stream

        protocol        = tcp

        wait            = no

        user            = root

        server          = /usr/bin/x11vnc

        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg

        disable         = no

}
```


4. Configure GDM to run x11vnc when at loading time:


```
sudo gedit /etc/X11/gdm/Init/Default
```


and this line to the file:


```
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```


(you can change the port and other parameters)


5. If you restart your PC at this stage you&#8217;ll only be able to login, then the GDM will kill your session. To avoid this we must change another file:


```
sudo gedit /etc/X11/gdm/gdm.conf
```


now search for this line :

#KillInitClients=true

And change it to this:

KillInitClients=false


6. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)


```
sudo /etc/init.d/xinetd stop

sudo killall x11vnc

sudo /etc/init.d/xinetd start
```


7. Install OpenSSH-Server for remote connections...using putty or whatever...


```
sudo apt-get install openssh-server
```


Restart your box, you will have resumable VNC sessions available on startup available via a secure shell.

Download [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") at your remote location to login remotely.

Thanks.

Moon.

---

### Post by indelible on 2007-07-10
Great HOWTO, worked pretty well for me on 7.04, just have a couple questions.

> **moonblink said:**
> 
4. Configure GDM to run x11vnc when at loading time:

```
sudo gedit /etc/X11/gdm/Init/Default
```

and this line to the file:

```
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```



This should be added to the very end of the file as I've done, or does it matter?

> **moonblink said:**
> 

5. If you restart your PC at this stage you&#8217;ll only be able to login, then the GDM will kill your session. To avoid this we must change another file:


```
sudo gedit /etc/X11/gdm/gdm.conf
```


now search for this line :

#KillInitClients=true

And change it to this:

KillInitClients=false



The only problem I'm having is that my vnc session is dropped right after login, so I have to reconnect to see the desktop.  I assume this has something to do with the KillInitClients setting, although I've double checked that it's uncommented and set to false, and rebooted.  Is there any reason it would not be reading the setting from my gdm.conf, or seems to be ignoring it?

---

### Post by moonblink on 2007-07-11
Indelible, yeah you can add it to the second to last line, right before the "end" line. 

Also regarding your VNC connection shutting down just after login, I had that same issue with 7.04 server.  I could not get it to clear up so I went back to 6.06 and it worked like a charm...I changed the file several different ways to see if that was it on 7.04 and never got it to comply, its really just an inconvenience since you can just re-login and its all good. 

Thanks

Moon.

---

### Post by Kreychek on 2007-08-02
First off, good writeup, worked well, until...

I upgraded to the new 2.6.22-9-generic kernel today. Now, when connecting, the password prompt is different. Has the VNC logo and is a different size. Minor point. Same password that I had before works when connecting to the box while it's displaying the GDM login. Upon logging in to X, the connection drops. Again, no biggie, used to happen before the kernel upgrade too. However, upon reconnecting via VNC, I get the error, "Failed to connect to server". My VNC client is the same as before, UltraVNC.

Tried using the previous kernel, same problem.

The guide I followed for the kernel upgrade is listed here:
[http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html](http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html)

I am undoubtedly a noob, but it doesn't look like any of the packages that the howto had me install were related to VNC, etc.

Any help would be greatly appreciated, as this is a headless box and I have no means of interacting w/X otherwise. Thanks in advance.

Update:

I tried running
```
 /usr/bin/x11vnc -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg

```

and that started x11vnc and allowed me to connect via VNC after I had logged into Gnome. Perhaps it has something to do w/xinetd that gets changed after upgrading kernels? Even though, as I said, using the previous kernel, same problem occured. I suspect a package was installed/changed that affected how xinetd works. I may be totally wrong though. :confused:

Anyway, I'd like to get this working in the same fashion as it was previously, where no additional commands have to be manually run in order to VNC after logging in to GDM. Thanks

---

### Post by Linuxnz on 2007-08-24
I set up as suggested.  Am running on xubuntu,  Fiesty   7.04   256MB RAM

vnc viewer won't make a connection. I just get a window saying "The connection closed unexpectedly

Do you wish to attempt to reconnect to max:1?"

Clicking "Yes" just gets the same result.

If I run it manually (even after the changes suggested) using sudo x11vnc it runs fine.  No password of course.

Any ideas where to look / start?

Thanks - Chris

---

### Post by BDNiner on 2007-08-24
Great Post, it worked for me on the first try. The only problem but i guess it is not a problem really. When i enable desktop effects the screen doesn't update on the computer that i am using to remote control. So i can move the windows around, and they move on my ubuntu box, but on the other one nothing happens. I can even spin the desktop around and it shows the 1st desktop only, but the ubuntu machine spins. 

Maybe it is just too much information to send, so it crashes, not really a bug because there is no reason to use 3d effects on a machine you are connecting to. i just thought it was interesting.

---

### Post by Linuxnz on 2007-08-28
I have fixed the issue with "The connection closed unexpectedly Do you wish to attempt to reconnect to max:1?" on my Xubuntu server.

The problem was there is more than one **gdm.conf **file to fix with the **KillInitClients=false**.

On my system there was also a file called **gdm-cdd.conf** which to me looked very much like the gdm.conf I had already edited.

Hope this helps someone else.

Thanks Moonblink it works very well.  My Xubuntu NAS server is now easy to manage.  Nice work.

Regards - Chris

---

### Post by rdd on 2007-10-30
Thanks for this great HOWTO. Also works on Gutsy with a little change to the location of the gdm configuration. It is now located directly under /etc/gdm. 4 and 5 should now look like this

4. Configure GDM to run x11vnc when at loading time:

```
sudo gedit /etc/gdm/Init/Default
```

and this line to the file:

```
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```

(you can change the port and other parameters)

5. If you restart your PC at this stage you&#8217;ll only be able to login, then the GDM will kill your session. To avoid this we must change another file:

```
sudo gedit /etc/gdm/gdm.conf
```

now search for this line :

```
#KillInitClients=true
```

And change it to this:

```
KillInitClients=false
```



regards

tom

---

### Post by DDM on 2007-10-30
Good stuff. Is there a way to setup a "virtual" session at startup? What I mean is, I have a headless Mythbuntu server connected to a TV, and it runs the MythTV frontend through xdm. I can get to Gnome on it by using FreeNX, and I've messed around with Xvnc a little, but I can't get either to load by itself on startup.

So basically, I'd like a way to have a FreeNX or VNC session start by itself on the Mythbuntu server, and have a few GUI apps start on it (Azureus, I have to run it since it has autospeed and azsmrc), and be able to login to them and have them persist and all that fun stuff. Any ideas?

---

### Post by zanolla on 2007-11-04
Hi everybody.
Very nice how to & updates.
I've only a problem. I follow the guide, but I would like that the server requires the password at each connection...
I've done the 
```
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```
but the password is not requested by the server..
How can I correct that?
I've also used the
```
x11vnc -rfbauth /etc/x11vnc.pass
```
but nothing...
suggestions?

Thanks!

p.s. sorry for my English, I'm Italian...

---

### Post by zanolla on 2007-11-04
Oh yeah!
I've solved that with a little add:
```
service x11vnc

{

        port            = 5900

        type            = UNLISTED

        socket_type     = stream

        protocol        = tcp

        wait            = no

        user            = root

        server          = /usr/bin/x11vnc

        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg -rfbauth /etc/x11vnc.pass

        disable         = no

}
```

in the file:
```
/etc/xinetd.d/x11vnc
```

Thanks guys!

---

### Post by daflame on 2007-11-18
Great How To!  I have another suggestion though.  FreeNX is an even better alternative since it uses the native XDM protocols and compresses the stream so only what is needed passes to the client.  Plus you get sessions by default and an unlimited number of them to boot!

If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of NoMachine server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by svtcontour on 2008-04-23
Worked great for Me!  Love having desktop access right away :-)

---

### Post by Ocelaris on 2010-08-03
This is the best post, I've been coming back to this for years. Always hard to find. For reference for Ubuntu 10.04 they've moved /etc/X11/Init/Default to /etc/gdm/Init/Default. Everything else works flawlessly in 10.04 Lucid Lynx. 

<rant> Really Vino is horrible, has been for 3 releases now and I don't know why. I keep trying other flavors (Centos) because of stupid things here in Ubuntu/Debian land like network manager and Vino. Really wish they would get a reliable product to replace those two nightmares of a program. I always end up getting it to work, but I've been struggling with stupid mindless things that should be dead simple. </rant>

---

### Post by Cue2 on 2011-10-26
is there a way to adapt this to LightDM (Ubuntu's new display manager) instead of GDM?

---

