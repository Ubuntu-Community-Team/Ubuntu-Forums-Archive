---
title: "backing up a system."
date: 2007-12-19
forum: Server Platforms
---

### Post by hockey97 on 2007-12-19
Hi  how in ubuntu can I make a secure backup of everything on my system like all files so that if somthing goes wrong  I can use the backup files to be loaded on they system so I can recover where I last took off.

Also I have another computer their is 2 computer one already has ubuntu and windows dual boot. I have another computer that has windows on it, I am planning to use it as a backup server just in case the main one goes haywire.

How can I make an exact same system as the main one. Like the database and stuff.

How would you guy's go about's creating a backup system.?

---

### Post by HermanAB on 2007-12-19
Rsync is you friend.

You can run rsync over ssh and if you have Cygwin on Windows, then you can do it cross platform.

Note that with a database, you typically need to export the data before backing it up, but I guess you know that already.

Cheers,

Herman

---

### Post by hockey97 on 2007-12-19
what is Rsync?  is this a way I can make a back up to my other comptuer that has windows?

I am planning to turn that other computer to just  ubuntu and might think to make that my main server. and then have my  computer for personal usage and also as a back up if that main server have problems I can switch it to my personal computer which is the one that has the dual boot already has ubuntu 7.10 and windows xp. 

but I want to also be able to sync my 2 comptuers like at the end of the day I will update my back up server like the database and any new uploaded files.

Also would I be able to save the stuff on a re writable cd or ddvd-rw.

so every night I can pop in the same dvd-rw cd and update the info on that cd so it would have some what  a current back up so that if both my servers are not working or something happend that both my servers lose data  so I can have a solid back up.where that cd I can depend on that cd to save me if a data loss occurs.

but I want to have a back up of the whole system all the config's evertyhing even the databases and all info for dns.  So I don't need to re-install ubuntu and go thought the painstakly proccess of installing all servers ect apache2 bind9 ect and config it properly and test it if it works and then start my website again with a huge data loss so it's like starting all over again.

---

### Post by twistedtwig on 2007-12-20
Try this guide i use it and its brill

[http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup)

also you can get Rsync app for windows I **think**, this might make it easier to copy to the windows machine

---

