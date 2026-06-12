---
title: "Suspicious Activity - My computer is a zombie?"
date: 2011-01-12
forum: Security
---

### Post by Ellume on 2011-01-12
I am running ubuntu 10.10, and fairly new to ubuntu. I've started to pursue computer security as a hobby and hopefully a career later on, but I am still new to most of this stuff.

I ran etherape and I realized I had a very suspicious connection open with 200+kbps activity continually. I am not downloading or uploading anything to my knowledge, don't have any torrent programs running. So I'm starting to wonder if my computer may be a zombie. I'm kinda hoping I can use this experience to learn a little bit about this stuff and what I can do besides simply formating and reinstalling everything.

After a while of having etherape up I noticed a second large connection going for awhile. But as of typing this that second connection has stopped while the first larger one continues.

Any advice?

Pictures from EtherApe
[http://i152.photobucket.com/albums/s200/Ellume/suspicious.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious.png)
[http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png)

---

### Post by Ellume on 2011-01-12
I am running ubuntu 10.10, and fairly new to ubuntu. I've started to pursue computer security as a hobby and hopefully a career later on, but I am still new to most of this stuff.

I ran etherape and I realized I had a very suspicious connection open with 200+kbps activity continually. I am not downloading or uploading anything to my knowledge, don't have any torrent programs running. So I'm starting to wonder if my computer may be a zombie. I'm kinda hoping I can use this experience to learn a little bit about this stuff and what I can do besides simply formating and reinstalling everything.

After a while of having etherape up I noticed a second large connection going for awhile. But as of typing this that second connection has stopped while the first larger one continues.

Any advice?

Pictures from EtherApe
[http://i152.photobucket.com/albums/s200/Ellume/suspicious.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious.png)
[http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png)

---

### Post by Ellume on 2011-01-12
I tried to post this and I received a Proxy Error. It also seems that my trying to post managed to start a thread with no content, which of course was not my intention. I tried to reply to the thread but just received another error. Hopefully this doesn't cause any issues. Here is what I'm trying to post:

I am running ubuntu 10.10, and fairly new to ubuntu. I've started to pursue computer security as a hobby and hopefully a career later on, but I am still new to most of this stuff.

I ran etherape and I realized I had a very suspicious connection open with 200+kbps activity continually. I am not downloading or uploading anything to my knowledge, don't have any torrent programs running. So I'm starting to wonder if my computer may be a zombie. I'm kinda hoping I can use this experience to learn a little bit about this stuff and what I can do besides simply formating and reinstalling everything.

After a while of having etherape up I noticed a second large connection going for awhile. But as of typing this that second connection has stopped while the first larger one continues.

Any advice?

Pictures from EtherApe
[http://i152.photobucket.com/albums/s200/Ellume/suspicious.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious.png)
[http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png)

---

### Post by pl@yer on 2011-01-12
First thing I would do would be to see what daemon/process and port are responsible for the connection. 
 
```

sudo netstat -atunop|egrep -i 'estab|list'

```

That should provide PIDs and port numbers for established and listening connections. Also you should look into fuser, rpcinfo -p and lsof -i.

You could kill any unwanted process and disable the daemon from starting automatically. Look into sysv-rc-conf.

Then you could use something like guarddog to configure iptables to deny connections to the unwanted port.

---

### Post by Ellume on 2011-01-12
Sorry for the multiple threads. I was receiving a Proxy Error when I was trying to post. Feel free to close this thread.

EDIT: Thanks for merging the threads.

---

### Post by cariboo on 2011-01-12
I've merged your 3 threads, please report the posts you want deleted.

---

### Post by Ellume on 2011-01-12
Thanks cariboo907. I guess you can scrap the first and second post if that works. Sorry about the mess, not sure what was going on there.

THanks pl@yer I will give that a try and see if I can't figure something out.

---

