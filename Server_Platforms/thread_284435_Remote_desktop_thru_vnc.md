---
title: "Remote desktop thru vnc"
date: 2006-10-25
forum: Server Platforms
---

### Post by allthegoodnamesaretakin on 2006-10-25
Ok , here's my problem , i am trying to set up a remote desktop to my ubuntu machine, i did a search on it in these forums and came up with some answers on this thread ([http://ubuntuforums.org/showthread.php?t=191564&highlight=setup+ssh+server](http://ubuntuforums.org/showthread.php?t=191564&highlight=setup+ssh+server). I still cannot get on to my ubuntu box.
    I have a Fedora 5 box setup with vnc and it works fine, i also  opened up ports 5900/5901 for FC5 on my router. I figured if FC5 is using those ports then obviously ubuntu cannot, so i opend up ports 5902/5903 for Ubuntu, i also adjusted these ports in Xvnc in the xinet.d directory.

     Yesterday i set up vnc using the old method on Breezy and tested it on my LAN , i brought up a vnc client and typed in the internal IP address and it connected me only after i got back on the ubuntu box and allowed it to control the desktop. that may be another problem i might have.I have been trying different variations in my vcn client like(hostname:LAN IP address , or hostname:0 ). For all i know i may not be putting in the right info.I am using Dapper right now BTW. Any help would be appreciated. 

Thanks in advance!!

](*,)

---

### Post by Paerez on 2006-10-25
I have another non-ubuntu server that runs linux, and I run tightvnc server on it. I don't forward the ports, I just use -via ([http://www.tightvnc.com/vncviewer.1.html)](http://www.tightvnc.com/vncviewer.1.html)). So my command looks like this:

```
$ vncviewer -via myserver.com localhost:1
```

when you do -via, it makes an ssh connection, then "localhost" is my server, since it is currently connected to my server with -via.

And voila, no open ports!

---

### Post by DouglasAWh on 2008-03-11
> **Paerez said:**
> I have another non-ubuntu server that runs linux, and I run tightvnc server on it. I don't forward the ports, I just use -via ([http://www.tightvnc.com/vncviewer.1.html)](http://www.tightvnc.com/vncviewer.1.html)). So my command looks like this:

```
$ vncviewer -via myserver.com localhost:1
```

when you do -via, it makes an ssh connection, then "localhost" is my server, since it is currently connected to my server with -via.

And voila, no open ports!

I know this is like way old, but I am very, very frustrated with VNC.  I can't get it working with an Apple server and I can't get it working between two Ubuntu boxes.  There's no frickin firewall.

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

I can ssh from both machines to the other.  However, VNC does not work.

```

vncviewer: unable to open display ""

```

I get a different error going the other way, but seeing as how I can't VNC in, I can't exactly copy and paste now can I.

Thanks for the help.

---

### Post by HermanAB on 2008-03-11
Hmm, I don't understand why everybody tries to use VNC.  It is slow and insecure, a bad combination.  VNC copies the whole friggen desktop ala Windows RDP, while you already have one on the local machine so you don't need another slow one on top.

The best way to remote into a Linux machine is with SSH.  So you should install openssh and openssh-server packages.  SSH is secure and can do everything VNC does and more, way easier.

Once you have your keys distributed, you can put an application link on the desktop or in a menu, that will connect to a remote machine and launch a specific application at the click of a mouse.  You can even run a remote taskbar with its menus.  (If your local system uses Gnome, run KDE Kicker and vice versa, to keep your sanity).

eg:
$ ssh -C -c blowfish -X user@server gedit
$ ssh -C -c blowfish -X user@server gnome-panel
$ ssh -C -c blowfish -X user@server kicker

Cheers,

Herman

---

### Post by Oldsoldier2003 on 2008-03-11
> **HermanAB said:**
> Hmm, I don't understand why everybody tries to use VNC.  It is slow and insecure, a bad combination.  VNC copies the whole friggen desktop ala Windows RDP, while you already have one on the local machine so you don't need another slow one on top.

The best way to remote into a Linux machine is with SSH.  So you should install openssh and openssh-server packages.  SSH is secure and can do everything VNC does and more, way easier.

Once you have your keys distributed, you can put an application link on the desktop or in a menu, that will connect to a remote machine and launch a specific application at the click of a mouse.  You can even run a remote taskbar with its menus.  (If your local system uses Gnome, run KDE Kicker and vice versa, to keep your sanity).

eg:
$ ssh -C -c blowfish -X user@server gedit
$ ssh -C -c blowfish -X user@server gnome-panel
$ ssh -C -c blowfish -X user@server kicker

Cheers,

Herman

i really don't see the point of even installing x on a server.... but thats just me i guess

---

### Post by HermanAB on 2008-03-11
Well, that is the whole point with SSH and X forwarding.  You don't need to run X on the server.  With X forwarding, only an X client runs on the server (part of SSH actually) and the X server is the one already running on your desktop.

So, through SSH, you can run any graphical program on a server, without actually running the graphics on the server.

Cheers,

Herman

---

### Post by DouglasAWh on 2008-03-11
these aren't two servers, they are my desktop and laptop.  I WANT to see where exactly everything was when I left it.  I suppose if I want to see files though I could just navigate to them, but I use such deep file paths it's easier to do it GUI style than through terminal.  Here's an example of why I would want to use the GUI and if someone has a way to do it otherwise, I'd be happy to hear it:

Thunderbird (like most e-mail clients) has some issues with auto filters when you have two versions open.  If I auto filter Y to Y folder, it goes there, but I never get notification on the box I am on now if the other box did the forwarding.  Very irritating.  Thus, it's nice to be able to go in and close thunderbird.  WAIT.  Yes, you can close the app through terminal, but I want to actually see the folders bolded and if I close thunderbird they aren't going to magically get bolded on my current machine...so I need to go in.  I could in and see the non-expunged content, yes, but this isn't about a work around, this is about doing it the way I want to do it.

The point is well taken though and I'll do that in the future if I can't get VNC going.  Also, if you tunnel VNC through ssh you get all the security of ssh, so don't give me the insecure garbage.

---

### Post by HermanAB on 2008-03-11
Hmm, my point being that SSH can do everything that VNC does and more, so tunneling VNC through SSH is kinda redundant.

To run Tbird through SSH:
$ ssh -X user@server thunderbird

La voila...

If you want a clickable menu, run gnome-panel or KDE kicker, then launch whatever you want from the menu:
$ ssh -X user@server kicker

and that will give you a local copy of the remote KDE taskbar - this even works on Windows with Cygwin.

You can also run the whole flippen desktop if you really want to - the commands are something like startkde and startgnome, dunno exactly, left as an exercise for the reader...

I'll give you one tip - do 'init 3' before you try to launch a desktop remotely to make sure that it isn't already running.

Cheers,

H.

---

### Post by DouglasAWh on 2008-03-12
I think the -X is what I needed.  I've got an X-window forwarded, but now I've got to figure out how to close Thunderbird remotely to get to do what I really want to happen.  I also need to figure out how to get out of a man page (though opening up another terminal session is an easy enough work around).  I did, in my tinkering, figure out that alt+esc is the same thing as alt+tab without the bar in front, which is kinda cool.  Time for bed.  I'll look in to this more tomorrow.

EDIT: I thought I had tried CTRL + Z, but I guess not.  Maybe I was doing ALT+Z.  I clear indication it is bed time...

---

