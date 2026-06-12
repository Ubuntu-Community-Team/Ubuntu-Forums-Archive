---
title: "apt-get download method tweaking"
date: 2006-11-18
forum: Repositories &amp; Backports
---

### Post by pthanos on 2006-11-18
Hello all,

I recently had a problem with my apt not resuming downloads from were it was interrupted. That really made the apt system unusable for big downloads, since everytime some big package would "stall" while downloading.

I resolved that problem: it wasnt a problem of apt, but of the .dk mirror I was using. I wonder why the danish guys are not allowing download resume.

What I want to ask is: how can you tweak apt-get into not stalling?? For example with wget, you can set the write-timeout (or something like that) to 10sec for example. If nothing is written on the buffer for 10seconds, the download is considered to have stalled and it is restarted. This way you can easily finish a big file, without having to restart by hand or wait 200seconds for the default timeout to occur.

Is there something similar in apt-get? How does apt-get downloads its stuff? I couldnt find a config option for somehting like this. Apt by default just stops downloading when a timeout is reached.

Thanks.

---

### Post by pthanos on 2006-11-21
I really wonder why this is not interesting to anyone. Don't apt-get downloads stall for other people except me?

This is for sure a problem especially for unattended upgrades.

---

### Post by dbott67 on 2006-11-21
It's a good idea... 

I wouldn't say that others aren't interested or concerned about this.  The forums are a very busy place and good threads get buried all the time, so don't take a lack of response personally.

Perhaps a better approach might be to submit this as a feature request in Feisty Fawn.

-Dave

---

### Post by pthanos on 2006-11-21
Yes yes, of course this is busy forum. Though I think this is quite important, for example you leave your pc to dist-upgrade only to find out that it stopped midway cause the download of packet "whatever" stalled.

I would try poking around the source of course, but maybe somebody knew the way apt downloads.

---

### Post by cantormath on 2006-11-21
you can
download only
```
sudo apt-get -d install package
```
or
test
```
sudo apt-get -t install package
```
or
simulate
```
sudo apt-get -t install package
```
or
get src
```
sudo apt-get source package
```

is that what you mean?

---

### Post by pthanos on 2006-11-21
No, nothing to do with what I mean.

While you actually fetch whatever with apt, the download might "stall" meaning no data is comming so the socket remains open until some default TCP timeout happens or something like that. Apt will do nothing to recover from a stalled download and only report that there was a timeout and abort.

In wget on the contrary, you can set a read_timeout at, for example 10seconds. After the DL stalls and 10s pass,it will start the download over and resume from where it left off (assuming that the server supports resuming).

---

### Post by pthanos on 2006-11-21
I checked the code a bit and its not using any external tool. I had the impression that it could use wget or curl, but no. I also had the impression that it was written in Python, but no, C++. (Damn!)

---

