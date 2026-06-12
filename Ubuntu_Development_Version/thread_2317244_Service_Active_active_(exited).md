---
title: "Service Active: active (exited)"
date: 2016-03-14
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-03-14
After a reboot I always have to restart the Plexconnect service as it start as
```
Active: active (exited)
```
and doesn't work. After restarting the service it works fine
```
Active: active (running)
```
Plexconnect is a custom service made by a script following this guide: [https://forums.plex.tv/discussion/156534/install-on-ubuntu-server](https://forums.plex.tv/discussion/156534/install-on-ubuntu-server) <-- thank you!
I have a suspicion that the reason for this is that Plexconnect is dependent on plexmediaserver. And if they start at approximately the same time there will be a problem. (My boot time is less than 10sec).
Is there a way to delay the start of a service or a way to set the order in which they start? (Or better yet, a way of setting dependencies, like plexmediaserver has to be running for plexcennect to start?
Any thoughts ?

---

