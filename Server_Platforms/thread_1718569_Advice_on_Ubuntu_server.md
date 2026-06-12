---
title: "Advice on Ubuntu server"
date: 2011-03-31
forum: Server Platforms
---

### Post by donniezazen on 2011-03-31
I recently lost lcd screen of my Dell Inspiron 6400/E1505. I am planning to turn it into a home server and keep it in some corner in my home. I have a couple of questions.

1. To be able to use torrent.
2. Access audio/video on other systems.

Leave it on command line to reduce system load. It would be great to begin with regular desktop to be able to use it once a while with external monitor and then quickly switch to command line and leave as server.

I used ajaxplorer and dyndns and loved it.

Sorry if it's a repost. I am a noob.

Thank You.

---

### Post by simolokid4 on 2011-03-31
Not sure what your questions are, but to try and answer atleast a part of your question;

> 1. To be able to use torrent.
2. Access audio/video on other systems.

Torrent -> Try transmission daemon :) I believe it has a webinterface so it's easy to manage.
Audio/video on other systems. Try vlc server for the video, subsonic for audio.

If you're behind a router and want to acces it all from outside of your homenetwork, you will need to forward the appropiate ports.

P.S.: I'm sorry about your screen.. =[ Good thing it's getting ubuntu on it ;D

Hope I helped in some way.

Kind regards.

---

### Post by donniezazen on 2011-03-31
I should start with Ubuntu-desktop install and use VNC for remote desktop, Ajaxplorer for accessing files+video, transmission for download, and subsonic for audio. That's hell of a lot. Can Ajaxplorer do all except remote desktop(not priority)? Or any other protocol to perform all task except remote desktop? I only need remote desktop to download over http.

Thanks for your help.

And it always had Ubuntu and will always be with it.

---

### Post by msandoy on 2011-03-31
You mention that you will have the computer in CLI most of the time. I use rtorrent in CLI, and switch between runnings programs with screen. Screen is like multitasking in text mode. :-)
Rtorrent is fully configurable via ssh. I'd recommend it.

---

### Post by CharlesA on 2011-03-31
> **msandoy said:**
> You mention that you will have the computer in CLI most of the time. I use rtorrent in CLI, and switch between runnings programs with screen. Screen is like multitasking in text mode. :-)
Rtorrent is fully configurable via ssh. I'd recommend it.
+1 to screen. I love it. <3

---

### Post by donniezazen on 2011-03-31
Thanks, I will checkout rtorrent and Screen. 

Any suggestions on how to switch to CLI when not using GUI just to save resources and not waste power etc. ideally without restarting and all other network things running like torrent, Ajaxplorer, subsonic, etc.

---

### Post by CharlesA on 2011-03-31
You can kill Xorg, but I am not sure if that'll have any lasting side effects.

---

### Post by donniezazen on 2011-04-04
I have setup Ajaxplorer. I tried rtorrent but it is very complicated for now. I am trying transmission-daemon which is relatively easy. I am having hard time setting up apache to resolve to transmission-daemon. I am using dyndns. Can somebody help me with virtual host configuration?

---

