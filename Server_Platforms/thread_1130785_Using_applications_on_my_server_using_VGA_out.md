---
title: "Using applications on my server using VGA out"
date: 2009-04-20
forum: Server Platforms
---

### Post by jesus_jones on 2009-04-20
Hi, 

I'm completely new to both servers and ubuntu. 

Anywho, 

I'm currently using my server for ftp/file storage but I was wondering can I install applications to play media on it to my television through the vga/rgb and audio jack output. It's sitting behind my tv so it might as well do something. 


Thanks in advance.

---

### Post by MaindotC on 2009-04-20
It's definitely possible.  My setup (listed in my signature) has a video card with a video-out capability and I watch youtube or other media in my tv.

---

### Post by jesus_jones on 2009-04-20
Great and can you do it remotely through some kind of GUI/web browser based app? and how?

---

### Post by nandemonai on 2009-04-20
First you'll need a GUI on the server. Second a way to control it from another machine (That is unless you want to hook up a keyboard and mouse).

Example xubuntu desktop and remote desktop.

There are other ways of doing this but the above example is how I used to do it.

---

### Post by MaindotC on 2009-04-20
I just use my laptop to VNC into the desktop which is connected to the TV.  Unfortunately my TV only supports 1024x768.  I watch movies all the time from those sites that let you watch them in your browser.  Just click play, then full-screen, then close VNC client.  One other option would be to use a wireless keyboard.

---

### Post by jesus_jones on 2009-04-21
Hi thanks for the responses, I'm running webmin at the moment which gets me to the command line, I'll fiddle around with vnc and see what happens. Thanks for the help thus far. 

What I really want is a set top box that I can control from my laptop that also lets me access my files using ftp...not alot to ask. :P

---

### Post by Kareeser on 2009-04-21
You can try forwarding your X session through SSH.

It'll allow you to use applications on the server while outputting the interface to the connecting computer.

All you have to do is add the "X" switch to your ssh command.

```
ssh server -X
```

Practical application: I use this setup to control Rhythmbox on my desktop computer and play music with my good speakers, while I'm sitting in bed across the room with my Laptop!

---

