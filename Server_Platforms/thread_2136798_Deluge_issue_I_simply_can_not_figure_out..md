---
title: "Deluge issue I simply can not figure out."
date: 2013-04-18
forum: Server Platforms
---

### Post by Archyriel on 2013-04-18
Okay. Ive been a linux user for a long time now, and in the past two weeks I've had to move from transmission to deluge (i needed libevent 1.4.2 and transmission requires 2+) so i havn't had a single problem installing and running deluge. my problem lies with the webui. For some reason it will not apply changes or even save them upon a restart of the daemon. It wont even do this when i run it as a user with its own config folder.
I have search high and low for a fix or even a file permissions issue, the closest thing i have come across is adding "?dev=true" to the end of the url. still nothing.

at the moment I have compiled and install it from the git source hope that it was a bug with the apt-get version, but still none the less.
I have configured the deluge.conf and nothing, it is as if the daemon is operating ignoring my rules. perhaps ive configured the wrong conf, perhaps ive missed something really silly and stupid when im looking for a complicated fix... I dont know.
the logs are blank.

can someone offer even a suggestion it would be greatly appreciated!

---

### Post by Archyriel on 2013-04-20
As i said i knew i was missing something, the first problem was the 'deluged' wasn't starting because of a file permissions error in the /usr/lib/python2.7 so once that was cleared up(apt-get purge then install again) the next issues was having it actually start as my user, that was solved very quickly and the final tiny issue was in the init.d script and the daemon and webui flags and now everything is working perfectly.

---

