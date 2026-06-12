---
title: "I Don't Know What I Need, Need Help"
date: 2009-12-08
forum: Server Platforms
---

### Post by pepsifx357 on 2009-12-08
I want to be able to control a computer from over 100 feet away with a keyboard, mouse, and monitor.  I can't do it with USB, and I don't have a 100'DVI cable for the monitor.  I was looking into VNC and Tight VNC tried both but the latency is tremendous compared to Windows Remote Desktop.  So, would a thin client be able to do this or am I mixed up.  I need a professional solution for this, as it is for my business.  LOW Latency for controlling the computer is key.

Specifics:

This is a recording srudio.  The computer I need to run is in a machine room 100 feet away.  The computer runs Ubuntu and the Audio software and the analog audio comes from this computer to my Mixer.  I can control the playback with MIDI machine control but as for editing of the computer I need to be able to see the desktop.

I need help.

Thanks,

Ben

---

### Post by squaregoldfish on 2009-12-08
You might want to try out SSH with X11 tunneling. You can SSH into the remote machine with the -Y flag, which will set the local screen as the X display. Any applications you start on the remote machine in the SSH session will be displayed on the thin client machine.

As long as you're on a local wifi network (or better yet, ethernet), the latency should be pretty low.

Steve.

---

### Post by cybergalvez on 2009-12-08
use NX either NXFree or the one from nomachine.  should give you what you want
Jose

---

### Post by pepsifx357 on 2009-12-08
> **squaregoldfish said:**
> You might want to try out SSH with X11 tunneling. You can SSH into the remote machine with the -Y flag, which will set the local screen as the X display. Any applications you start on the remote machine in the SSH session will be displayed on the thin client machine.

As long as you're on a local wifi network (or better yet, ethernet), the latency should be pretty low.

Steve.

WHATTT? lol

So you're saying that if I have a Desktop machine and on another machine I type:

> sudo ssh -Y ben@10.10.10.201

I will be able to see that computers desktop like I was one it?

What about if the desktop that I'm trying to connect to is on a virtual machine?

---

### Post by squaregoldfish on 2009-12-08
You won't see the remote machine's desktop, but any program you run will be in a window on your local desktop.

So, if you do:

ssh -Y ben@10.10.10.201

and then, after logging in, type

firefox

You'll get a new Firefox window on your screen, but the application will be running on the remote machine - it just sends all the display stuff to your computer.

As for accessing a VM in this way, I'm sure it's possible but I've never done it, so I can't help.

Steve.

---

### Post by srt4play on 2009-12-08
> **cybergalvez said:**
> use NX either NXFree or the one from nomachine.  should give you what you want
Jose

This is what I would use too.

---

### Post by pepsifx357 on 2009-12-08
I like the ssh command.

About this NX.  It seems I need a server client and node, how does this work?

---

