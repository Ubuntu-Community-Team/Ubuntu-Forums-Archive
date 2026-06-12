---
title: "How to enable osc"
date: 2018-12-10
forum: Server Platforms
---

### Post by creco on 2018-12-10
Sorry, Community,
I have try to connect Iannix with Supercollider per OSC.
This wouldn't do anything.
So I have try to connect Supercollider to his self.
This would do nothing too.
And it wouldn't get some error-messages.
So I think:
Is the OSC server running????

And that's now my problem.
1.) Is the server already running ???
1a.) Or is there nothing install any OSC server.

I'm running the newest version on Ubuntu Studio.

For all informations in advice thank's
CreCo
Thomas Lahme

:(:confused::(

New I have found this Web-Site:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
It explains that the newer versions on Ubuntu disables OSC.
This means there should be nothing a OSC server running already.
So it will be up to me, to install a OSC server.
Can anybody help me to do this.

So I heave try to do both steps. To install Open-Sound-Control, to do it by deb and to do it by source.
But both steps have terminated by error.
This are the errors:
1.) In file included from ossdevlinks.c:33:
```
#../../kernel/framework/include/oss_config.h:29:10: fatal error: os.h: Datei oder Verzeichnis nicht gefunden
by source
```
2.)```
 dpkg: Abhängigkeitsprobleme verhindern Konfiguration von oss-linux:i386:
 oss-linux:i386 hängt ab von binutils.
 oss-linux:i386 hängt ab von gcc.
```

```
dpkg: Fehler beim Bearbeiten des Paketes oss-linux:i386 (--install):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Trigger für man-db (2.8.4-2) werden verarbeitet ...
Fehler traten auf beim Bearbeiten von:
 oss-linux:i386
```
by automatical deb installation

Please.:
I see it will be that Ubuntu say's OSC is out of time.
But Iannix and Supercollider will need it to work together.
So I'm in a pit of pain, and I need OSC.
Is there no anybody who knew a solution.
I beg for help.
:confused:

---

### Post by creco on 2018-12-11
So is a bed missunderstanding from me:
The Documentation for Ubuntu say's to me that OSC will not longer understand by Ubuntu.
This a the wrong advice, OSC all ready has a OSC-Server already.
The Problem has been at a nother place. A place I have not seen even if I ware eyeglasses.
You must put the electric plug in the socket. So you must enable OSC in Supercollider.
You must do that by:
Language -> Server Dump OSC.

So it was my stupid missonderstanding, what would are going here.

CreCo
Thomas Lahme

---

