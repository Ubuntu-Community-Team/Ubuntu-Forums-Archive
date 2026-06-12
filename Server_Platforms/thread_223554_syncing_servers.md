---
title: "syncing servers"
date: 2006-07-26
forum: Server Platforms
---

### Post by stormblue on 2006-07-26
Hello,

I've switched over to Ubuntu from windows exclusively.  I previously used DW for webdesign, although, I never really used the WYSIWYG features much, so I'm not going to miss those.  What I do miss is the ability to sync between servers.

I'm using bluefish and I like it rather well, but I was wondering what others are using to sync between servers. Ideally what'd I like to do is run a sync command and grab the files that have changed on the webserver and put them in a folder on my local computer, and then when done editing and testing run a sync that will upload files that have changed.

I would be happy with either some program for linux or using some shell script.  I'm unsure of my options, and would appreciate being pointed in the right direction.

I've looked into rysnc, but I only have FTP access, so this all has to be over FTP.  The solution doesn't have to be quick.  Any ideas on a client that supports a sync feature?

---

### Post by lamego on 2006-07-26
I never found such a tool and I don't believe there is much development happening for FTP based tools. (Most people use SSH/SFTP for security sake).
There is an utility which allows you to mount remote ftp sites as if they were local filesystems, with this you would be able to use rsync or any other local file based synchronization tool.

Have a look at:
[http://ftpfs.sourceforge.net/](http://ftpfs.sourceforge.net/)

I believe the Ubuntu package which provides this is: lufs-utils

Please note that I have never used ftpfs, I hope it will help you.

---

### Post by stormblue on 2006-07-26
Thanks! I'll look into it.  My host also supports SFTP are you suggesting that there may be a tool that does this over SFTP?

---

### Post by lamego on 2006-07-26
Ops,
decided to give a quick look into the  lftp manual, it does have a "mirror" command which is expected to do what you need.
```
sudo apt-get install lftp
lftp
help mirror
```

---

### Post by stormblue on 2006-07-26
That looks to be exactly what I'm looking for. 

Thanks for the help.  It is much appreciated.

---

