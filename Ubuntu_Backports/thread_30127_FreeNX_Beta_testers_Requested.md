---
title: "FreeNX: Beta testers Requested"
date: 2005-04-27
forum: Ubuntu Backports
---

### Post by jdong on 2005-04-27
New copies of freenx were uploaded into staging yesterday.


Can people help me to test it?

I don't think it's working, but it may just be my client.

---

### Post by epb613 on 2005-04-27
I have no idea what the program is or does, but I just tried to install it and everything went perfectly fine. Any other way I can help test it?

---

### Post by MarioFuentes on 2005-04-27
[QUOTE=jdong]New copies of freenx were uploaded into staging yesterday.


Can people help me to test it?

I don't think it's working, but it may just be my client.[/QUOTE]
 and the URL?

---

### Post by epb613 on 2005-04-27
Mario:

First, add the following to the end of your /etc/apt/sources.list (type: sudo pico /etc/apt/sources.list in a terminal to edit it) file:
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports-staging main universe multiverse restricted 
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras-staging main universe multiverse restricted

Next, in a terminal, type: sudo apt-get update

Then type: sudo apt-get install freenx

---

### Post by jimcooncat on 2005-04-27
\\:D/ 
Thank you folks! Really need this to switch our work computers to Linux.

---

### Post by A-star on 2005-04-28
I noticed 1 thing in this version:
to change the port it is working on I had to edit the file /usr/bin/nxloadconfig and change the SSHD_PORT to 8022 (my ssh server is working on port 8022 and freenx has to use this port also).

---

### Post by A-star on 2005-04-28
Ok,

Here is some more feedback.
I get the following error messages when I connect with the windows client (errors after I have succesfully logged in).
I use Gnome so I don't know if the same problem appears when you use KDE.
The previous version of Freenx that was in the staging repository didn't have this problem.
```
The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet".
```
and then I can choose to delete or don't delete it.

Same problem here:
```
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
```
```
The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
```
```
The panel encountered a problem while loading "OAFIID:GNOME_MultiLoadApplet".
```
```
The panel encountered a problem while loading "OAFIID:GNOME_WorkspaceSwitcherApplet".
```
```
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".
```
```
The panel encountered a problem while loading "OAFIID:GNOME_WindowListApplet".
```
```
The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet".
```
Kind regards
A-star

---

### Post by jimcooncat on 2005-05-04
Is this borked now, or should I help out with the testing?

Installed the debian version using instructions found here on my gf's (server) and my computer (client):
[http://oakley.bioinformaticsonline.co.uk/?q=node/18](http://oakley.bioinformaticsonline.co.uk/?q=node/18)

Works very slick. Too bad I had to lose her WinXP Home partition to do it.  ;-) 

Some usability issues I haven't found the answers to yet:

[list]
[*]Fullscreen works great, but I can't figure how to get back to my own workspaces. I'm stuck on her machine unless I log out.
[*]Forwarding individual applications is weird. It's like it doesn't pick up my /home dir on her machine. This is the functionality I really want to explore!
[/list] 

Want to set it up so I can play with my home computer from work, but NoMachine's client's not working so well on my Win98 work computer. I can't wait to switch to Ubuntu at work!

---

### Post by jdong on 2005-05-04
Heh, I cannot reproduce the error messages you guys are getting.

On my desktop and laptop, FreeNX for Hoary works beautifully. I've promoted it to stable for now, waiting for updated builds at kalyxo.org.

---

### Post by McQuaid on 2005-05-05
Ok, I installed freenx yesterday.  Just trying to play with it.

I wanted to see how the client looked so I ran nxclient, and I get:
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset


and then I'm left with a little box with just an ok button in a weird looking font.

Is the client gtk1?  I haven't installed any gtk1 libs yet.

Also, the howto on freenx is alittle lacking.  I used to use pcanywhere back in my win98 days and I've played with xp's remote desktop a little.  

From what I've read the server itself does not have a gui.  Just curious about actually starting stopping it, setting up compression settings etc.  I know it already compresses and I've read it's fast, just curious if there are settings to lower colour depth like other ones have to speed things up.  Also xp's remote desktop has audio video streaming, instead of playing media files on the host, does this do that?

I should probably get some of that info from freenx's site.  But if I could have a hand get this going and the basics on dealing with the server that would be great.

---

### Post by jdong on 2005-05-05
I've found that the client isn't working ,but the server's working fine...

Heh, time to bug Kalyxo again.

---

### Post by jimcooncat on 2005-05-08
[QUOTE=McQuaid]Also, the howto on freenx is alittle lacking.[/QUOTE]

I agree with McQuaid, documentation doesn't seem great, or it's not where I could find it after two hours of browsing NoMachine's site and my /usr/share/doc. A starting point in understanding it's inner workings:
[http://www.gnome.org/~markmc/a-look-at-nomachine-nx.html](http://www.gnome.org/~markmc/a-look-at-nomachine-nx.html)

This project would be much better if they would pick up some usability clues from other  projects. VNC has a lot more functionality in setting up sessions, and it's documentation is excellent.

I have a Debian port installed but I'm finding a lot of flakiness in its usage. I don't think initiating sessions on a LAN should be failing, I'm experiencing this 1 out of 4 times. I bet it's worse with a dialup connection. The red and white logo that comes up scares me it's so garish! Once connected, I do enjoy the speed, but reliability and good docs are worth more to me at this point.

I did find in their FAQ that you can get out of fullscreen mode by clicking in the upper right corner, or Ctrl-Alt-Shift-Esc. 

I'm thinking of bailing from this one for now until later this summer and going back to X forwarding on the LAN and VNC over the wire.

---

