---
title: "Backup Minecraft to Amazon Glacier"
date: 2015-03-10
forum: Server Platforms
---

### Post by GeddiGuy on 2015-03-10
Hi guys & gals,

At [GeekZone]("http://geekzone.org.uk"), we are starting to run a minecraft server so that people across the world can join our events. We therefore need to back up the data frequently in case something goes wrong. We don't want to interrupt the server or its players while the backup is running.

Here's the process that I was thinking would be good to follow

[LIST=1]
[*]notify world with minecraft say command - ```
/say auto backup will start in 5 minutes
```
[*]wait 5 minutes
[*]notify world with minecraft say command - ```
/say auto backup is about to start so lag might ensue
```
[*]save minecraft world with minecraft command ```
/save-all
```
[*]wait for world save to finish with waitsilence
[*]turn automatic world saves off with minecraft command ```
/save-off
```
[*]tarball world directory with name format gzmc-main-YYYY-MM-DD--hh-mm-ss.tar.gz (where YYYY = year, MM = month etc)
[*]copy tarball to glacier with glacieruploader
[*]delete tarball from local storage
[*]turn automatic world saves on with minecraft command ```
/save-on
```
[*]notify world with minecraft say command - ```
/say auto backup has finished. thanks for your patience!
```
[/LIST]

I have found [glacieruploader]("https://github.com/MoriTanosuke/glacieruploader") which should be able to copy from our virtual server to amazon glacier. I have also found [waitsilence]("https://github.com/pwaller/waitsilence") which should allow us to wait until the world save has finished before continuing.

What I'm not sure of is;
[LIST]
[*]How do you send commands to minecraft via an instance of screen?
[*]How do you put all of the above into a script?
[*]How do you get that script to run every hour?
[/LIST]

Thanks everyone!

James

---

