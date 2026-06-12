---
title: "mirroring servers"
date: 2006-11-01
forum: Server Platforms
---

### Post by chris hyperstring on 2006-11-01
urm help 1 of my bosses has just told me to try and set up a server i managed to do it with a bit of help and now he wants to mirror it with the other server? im 19 years old i know of mirrioing but i havn't got the foggyest where to start! and im slamming my head on my desk ](*,) please can someone help?

---

### Post by homegrown on 2006-11-01
what function does the machine perform? Are you doing this for disaster recovery or high availability?

---

### Post by chris hyperstring on 2006-11-01
well its to keep 3 backups of our software safe and secure but it might be easier to set up a mirror than to have to keep transporting through mysql, any help?

---

### Post by homegrown on 2006-11-01
I'm still not 100% sure of the requirement, but if you want to run a machine in sync with the server you could have a look at [http://www.linux-ha.org/]("http://www.linux-ha.org/").
If it's just the DB you're after then it might be easier to just take a dump of the database & move it somewhere else (tape or network storage)

Give some more detail & I'll try to help.;)

---

### Post by homegrown on 2006-11-01
Here's one that might help with the database replication -- this is written for debian, but should be work -- I've not tested it myself, but looks sane 
[stepBystep]("http://howtoforge.org/mysql_master_master_replication")

---

### Post by chris hyperstring on 2006-11-01
well we have our main server with an external drive, and we have a back up server incase something happens to the main server i.e: it dies, is stolen or is hacked badly! and for convenience we want to mirror them so automatically when something is changed on the main server then it is saved on the back up server

---

### Post by homegrown on 2006-11-01
If you want the two machines to be exactly the same I'd investigate the Linux HA project -- this won't be the easiest to do unfortunately. 

What application/s does the machine run?

---

### Post by chris hyperstring on 2006-11-02
thanks for the reply, sorry its taken a while i was dragged home by my other boss! its running "lewis" which is running our windowing website which lewis was built by my boss.

we want a way of having this other pc as our backup server so incase of maintenance we need to take the main 1 down then this 1 will keep our website up and online.

thanks, Chris

---

### Post by dannyboy79 on 2006-11-02
what about a raid solution? doesn't raid take EVERYTHING on the hard drives and duplicate it onto another? I am not sure if that is raid 1, 3, or 5 since I have never used raid but looked into a long time ago.

---

### Post by chris hyperstring on 2006-11-03
yeah we are thinking of setting up a bank of raid servers but not right now, bosses orders, but its probably the simpleist way of doing it, but we only have 2 mini servers! we are getting bigger and better one's but not right now, don't ask me why its the boss! 

thanks anyway.
        chris

---

### Post by dannyboy79 on 2006-11-03
> **chris hyperstring said:**
> yeah we are thinking of setting up a bank of raid servers but not right now, bosses orders, but its probably the simpleist way of doing it, but we only have 2 mini servers! we are getting bigger and better one's but not right now, don't ask me why its the boss! 

thanks anyway.
        chris 
          [http://www.hyperstring.net]("http://www.hyperstring.net")

well if that's the case, then you should just look into using rsnapshot, it uses rsync and takes exact copies (snapshots) of what you tell it and puts them where you tell it. i don't use it but I have looked into using it and it appears as though it would server your purpose.

---

### Post by dannyboy79 on 2006-11-03
heres a website talking about creating a backup server and then even an offsite of the lan backup server for the lan backup server. there is even a script which backs up /data1 folder to the offsite backup server, in your case you could just change the folder or stuff to  backup to being your whole server which I think is "/". I hope that one of these options works for ya, oh, this option just uses rsync which is basically the same thing as rsnapshot ezxcept I think rsnapshot does incremental backing up hence the name snapshot. good luck by the way, i checked out your website. i like that software you guys came up with so that the web pages have movable, minimizable, windows etc etc.

ha I realized I forgot to paste the link, [http://www.linuxjournal.com/comment/reply/8590](http://www.linuxjournal.com/comment/reply/8590)

---

### Post by homegrown on 2006-11-05
Chris 
Sorry I've not been in touch, but I'm doing a server room upgrade, so work odd hours & sleep when I'm not working -- If it's just a directory structure you need to sync you can use [unison]("http://www.cis.upenn.edu/~bcpierce/unison/") - there's even a fronted for it in the ubuntu repo's

---

### Post by chris hyperstring on 2006-11-10
thanks guys sorry i havn't replyed my pc has been crashing alot lately about 10 times this week i recall, i was fin with ubuntu 6.06, then the boss wanted 6.10 when it first came out but thats when my problems started oh well these things are sent to try us! thanks i'll check the links out when i can get a chance as work has been getting very busy with hyperstring.net, we have been aswell building a website called prompt payer! must get on,
thanks,
    chris

---

### Post by rabideau on 2007-04-09
Hi all,

I'm attempting to create backup copies of my websites (from the web) on to a local Ubuntu PC.  Ideally I'd like to copy both the MySQL and Files.  Minimally I need to copy the files.  I hope to be able to run this via a script automagically.

Any recommendations and Guides for a NOOB?

:lolflag: 

Thanks!

---

