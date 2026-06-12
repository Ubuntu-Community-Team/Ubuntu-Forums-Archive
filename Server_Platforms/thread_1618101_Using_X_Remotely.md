---
title: "Using X Remotely"
date: 2010-11-10
forum: Server Platforms
---

### Post by tg3793 on 2010-11-10
[COLOR=Gray]I've been working on this since last night (a few hours) but can't seem to find what I am looking for. I'll spare you the details of what I've tried already.[/COLOR]

Could someone guide me through connecting to my Ubuntu server using a remote X session? The "kicker" is that I want to do this from a Knoppix LIVE CD. So whatever method I am given will have to be something that is common to most Linux distros.

I imagine I will need help with two important steps:

**1)** verifying that I have an xserver of some kind running on my server.
**2)** command line statement for starting the Xserver from the remote machine.

---

### Post by tg3793 on 2010-11-10
This seems promising. I found this line. 

**[COLOR=DarkRed]ssh -X scribe@192.168.0.3[/COLOR]**

However when I run it I get this:

[COLOR=DarkRed]Your CPU appears to be lacking expected security protections.
Please  check your BIOS settings, or for more information, run:
   /usr/bin/check-bios-nx --verbose

Last login: Tue Nov  9 22:40:37  2010 from 192.168.0.2
scribe@scribe-desktop:~$ startx

X: user not authorized to run the  X server, aborting.
Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:   Resource temporarily unavailable (errno 11):  unable to connect to X  server
xinit:  No such process (errno 3):  Server error.
[/COLOR]

---

### Post by koenn on 2010-11-10
ignoring the warning about your CPU,
the problem is about authentication between your pc and the server. 
also, you don't really want to startx in your server, you want to run a 
program and show it on your PC, so call a GUI program that is installed on your server (say, firefox : )
 
you could try   -Y i.s.o. -X; i'ts less concerned about security
```

ssh -Y scribe@123.123.123.123 

## or
ssh -Y scribe@123.123.123.123 firefox &

```

alternatively, you can handle X security with xauth or xhosts
first, install xauth  (on the server, IIRC, so that would be your Ubuntu machine) and see if that helps (afaik you only need it installed, you don't have to do anythin,g with it). Then try ssh -X ... again

if that didn't work, 
try this : ```

xhost +
ssh -X scribe@123.123.123.123 
```

once you have something that works, read the relevant man pages (xauth, xhost, ssh, ...) so you know the risks and for ways to deal with them

---

### Post by rickyrockrat on 2010-11-16
I just posted this, which should take you step-by-step.

[http://ubuntuforums.org/showthread.php?t=1623135](http://ubuntuforums.org/showthread.php?t=1623135)

---

### Post by JP121 on 2010-11-16
> **rickyrockrat said:**
> I just posted this, which should take you step-by-step.

[http://ubuntuforums.org/showthread.php?t=1623135](http://ubuntuforums.org/showthread.php?t=1623135)

That sounds a lot more difficult then what I do.  When I connect I use username@ip -X.  One logged in, all I have to do to launch an application is type in its command, say nautilus, I just type in nautilus.

---

### Post by pricetech on 2010-11-16
I seem to have mine working to a point.  I made sure that X forwarding was set to yes in my sshd_config and that my client also supported it.

I can connect just fine now but when I run

```
sudo startx -- :1
```

I get:

```
--
no protocol specified
```

So I seem to be getting farther than you are.  Maybe the steps I've followed will help you.  Where exactly are you getting stalled ??

---

### Post by koenn on 2010-11-16
> **pricetech said:**
> I seem to have mine working to a point.  I made sure that X forwarding was set to yes in my sshd_config and that my client also supported it.

I can connect just fine now but when I run

```
sudo startx -- :1
```

...

"startx" is a bad test, because you shouldn't have X on the remote machine at all. X is on your local machine (your "desktop")

tip; install x11-apps on the remote machine (it's a small collection of X apps). Then in an ssh -X session, run 'xeyes'. 
you'll *see* it your local machine (where you ssh from, where X is), but it'll be *running* on the remote machine (where you installed xeyes, but where you don't have/need X)

---

### Post by pricetech on 2010-11-16
> **koenn said:**
> but where you don't have/need X)

Except I do need X running, and forwarding to my client.

---

### Post by koenn on 2010-11-16
...

---

### Post by koenn on 2010-11-16
nope,
you have X running on the client, and the remote application forwarding its (GUI) output to it.

see screenshot attached : Ubuntu client (with X, obviously) running xeyes on a debian server (where no X present & 'startx not found')

---

### Post by pricetech on 2010-11-16
> **koenn said:**
> nope,
you have X running on the client, and the remote application forwarding its (GUI) output to it.)

Maybe we're talking apples and oranges.  I don't need a handful of graphical apps forwarded to the client, I need to whole desktop forwarded to the client.  If I read the OP correctly, that's what he / she is after too.

I normally use NX for that but for some reason I can't get it to work under Xubuntu.

Doesn't much matter though.  I've only played with Xubuntu for a few hours and already don't like it.  I'm wiping and putting Ubuntu on since it works.  I was just trying something "lighter" since the machine is an older one.

---

### Post by koenn on 2010-11-17
> **pricetech said:**
> Maybe we're talking apples and oranges.  I don't need a handful of graphical apps forwarded to the client, I need to whole desktop forwarded to the client.  If I read the OP correctly, that's what he / she is after too..
I don't know that it's really that different. For one, where do you draw the lin,e between 'a desktop' and ' a handfull of programs'. Also, you *can* actually export an entire desktop as if it was just a program - identical to the technique i described for 1 program. If done this  with fluxbox : just run 'startfluxbox' in your ssh -X shell; then run any other program from a fluxbox menu. 

You can do the same for a gnome desktop by running 'gnome-panel' in the ssh -X session. gnome-panel gives you access to the menus for apps,and when you run them, they show up on your PC seamlessly. 


But I gather you're thinking  something more 'remote desktop' style, like vnc or windows rdp. The 'native' solution for that would be [xdmcp]("https://wiki.ubuntu.com/xdmcp"), which, iirc, does indeed require X on both ends

---

### Post by rickyrockrat on 2010-12-12
If you want the whole desktop, aren't you looking for vncviewer??

That's essentially a whole desktop.  You start vncserver, which sets up an initial password, then do a vncviewer.

---

