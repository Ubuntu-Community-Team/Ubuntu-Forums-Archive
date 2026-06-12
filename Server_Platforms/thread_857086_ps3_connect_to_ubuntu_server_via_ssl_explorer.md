---
title: "ps3 connect to ubuntu server via ssl explorer"
date: 2008-07-12
forum: Server Platforms
---

### Post by twistedneck on 2008-07-12
Dear Ubuntu people, my goal is to be able to remote control my ubuntu server within the playstation 3 web browser.

i have sslexplorer running on my ubuntu linux server.  

I added the remote desktop app 'remote administrator' (sounded right?) i could have added puddy also and a few others..  

tryin to test it locally, when i launch the app there is no window that pops up allowing me to control the desktop remotely. it just shows me some messages within ubuntu itself 'opening local tunnel listener', launching ssl explorer agent, and some ports. its working just fine.

but all i get is this screen shot below - again, i'm testing it locally first before i use the ps3 web browser.  where is my remote control? where is my picture of the ubuntu desktop like terminal server or regular ubuntu remote desktop? 

Help needed - thanks again. Jeff

:confused:

UPDATE - see below, had to run VNC via sslexplorer and everything is fine now, except ps3 does not have java.. dang!

---

### Post by huwnet on 2008-07-12
This application is intended to help get an SSH shell. It runs in a java applet. While you could tunnel X to get a remote desktop I don't think this is quite what you want. Does the PS3 browser even have java?

Perhaps you'd be better off installing Linux on the PS3 [http://en.wikipedia.org/wiki/Linux_for_PlayStation_3](http://en.wikipedia.org/wiki/Linux_for_PlayStation_3)

---

### Post by twistedneck on 2008-07-12
> **huwnet said:**
> This application is intended to help get an SSH shell. It runs in a java applet. While you could tunnel X to get a remote desktop I don't think this is quite what you want. Does the PS3 browser even have java?

Perhaps you'd be better off installing Linux on the PS3 [http://en.wikipedia.org/wiki/Linux_for_PlayStation_3](http://en.wikipedia.org/wiki/Linux_for_PlayStation_3)

Thanks for responding huwnet.  My goal is to use the ps3 web browser to access the ubuntu machine while in a game..  that negates the ps3 linux option.

I did get sslexplorer running, and its an excellent portal to launch other apps like VNC. VNC is running great now via sslexplorer - problem is, like you said ps3 has no java support :(

when, oh when..

[http://www.sharewareconnection.com/ssl-explorer-community-edition.htm](http://www.sharewareconnection.com/ssl-explorer-community-edition.htm)

---

