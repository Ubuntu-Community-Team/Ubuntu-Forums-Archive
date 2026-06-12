---
title: "Monitor website bandwidth used"
date: 2010-03-27
forum: Server Platforms
---

### Post by huggy77 on 2010-03-27
Not even sure if i am using the correct terminology...  I am hosting some websites and i want to monitor who is using more resources from a thoughput standpoint...  Would this be bandwidth monitoring.

Please point me in the right direction as to what i can use to monitor these sites...

I am using an uptodate version of apache2 and a single ip vhost setup.

Thanks in advance.

---

### Post by inphektion on 2010-03-27
you can pretty easily setup awstats.  I did and it gives you all stats from sites and bandwidth too.

---

### Post by dudumomo on 2010-03-27
Very interesting thread !!
I was looking for something like that.
I've tried cacti, but I don't really know how to set this up. (Too many features ;))

---

### Post by n0dix on 2010-03-27
Perhaps nethogs can help you.
```
$ sudo apt-get install nethogs
```

---

### Post by dudumomo on 2010-03-27
nethogs is very light and easy, but is it possible to get a historical graph ? It doesn't seem to..

---

### Post by n0dix on 2010-03-27
> **dudumomo said:**
> nethogs is very light and easy, but is it possible to get a historical graph ? It doesn't seem to..

Not it isn't , sorry for the suggestion. :(

---

### Post by joshwaaa on 2010-03-27
Hi,
 
I have found webalizer to be good [http://www.mrunix.net/webalizer/sample/index.html](http://www.mrunix.net/webalizer/sample/index.html)
 
cheers,
 
Joshwaaa

---

### Post by dudumomo on 2010-03-28
> **n0dix said:**
> Not it isn't , sorry for the suggestion. :(

Thank you for the suggestion. It doesn't suit me, but may be it does for someone else ;)

---

### Post by huggy77 on 2010-03-28
thanks guys.... looks good...

---

### Post by huggy77 on 2010-03-28
will nethogs give me a breakdown by url?

---

### Post by inphektion on 2010-03-28
> **huggy77 said:**
> will nethogs give me a breakdown by url?

awstats probably can.  
on the lines of cacti, munin will give you a nice graph of server processes, bandwith, cpu, mem etc.  awstats and webalizer are more towards your orig question though, I like awstats better, gives you more breakdowns.

---

### Post by n0dix on 2010-03-28
> **huggy77 said:**
> will nethogs give me a breakdown by url?

Is to use to see the bandwidth of each instance of browser and not by url.

---

### Post by dudumomo on 2010-03-28
What about ntop ?

Edit:
Oh, rrdtools sounds nice !
I will try this one as soon as I found how to do so xD

---

