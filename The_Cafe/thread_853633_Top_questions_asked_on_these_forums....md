---
title: "Top questions asked on these forums..."
date: 2008-07-08
forum: The Cafe
---

### Post by dracule on 2008-07-08
I was wondering what the top questions asked on these forums were (in terms of frequency). I know dozens of the same question gets asked everyday, and i was just wondering what those top questions are. (i am talking in terms of software/hardware not working not generally linux questions like "is it virus free")

also, what do you think the most common command line based responses are (eg "sudo gedit /etc/X11/xorg.conf")

---

### Post by aysiu on 2008-07-08
For the record, the proper command is ```
**gk**sudo gedit /etc/X11/xorg.conf
``` not *sudo gedit /etc/X11/xorg.conf*

It's kind of hard to pinpoint what the most common questions are, since that changes from month to month. For example, when Firefox 3 came out, the most frequent questions had to do with how to upgrade to Firefox 3 from Firefox 3 RC in Ubuntu 8.04 or from Firefox 2 in Ubuntu 7.10.

When an update a couple of years ago broke people's X servers, the most frequent questions had to do with how to fix that problem.

Right now, there seem to be a lot of questions about Flash, now that Adobe has released a testing version of Adobe Flash 10 for Linux.

Whether Ubuntu "needs" antivirus or not is a top question that's been asked since its inception and will probably continue to be for the near future.

---

### Post by tamoneya on 2008-07-08
the most common that i see is: "help I lost my windows partition".  Then I always need to get a sense for their partitioning setup so I always ask people for the output of:```
sudo fdisk -l
```

---

### Post by keiichidono on 2008-07-09
> **aysiu said:**
> For the record, the proper command is ```
**gk**sudo gedit /etc/X11/xorg.conf
``` not *sudo gedit /etc/X11/xorg.conf*

It's kind of hard to pinpoint what the most common questions are, since that changes from month to month. For example, when Firefox 3 came out, the most frequent questions had to do with how to upgrade to Firefox 3 from Firefox 3 RC in Ubuntu 8.04 or from Firefox 2 in Ubuntu 7.10.

When an update a couple of years ago broke people's X servers, the most frequent questions had to do with how to fix that problem.

Right now, there seem to be a lot of questions about Flash, now that Adobe has released a testing version of Adobe Flash 10 for Linux.

Whether Ubuntu "needs" antivirus or not is a top question that's been asked since its inception and will probably continue to be for the near future.

Why is it gksudo instead of sudo, can you explain this to me? They seem both the same.

---

### Post by terry_gardener on 2008-07-09
answer to your question difference between gksudo and sudo at 

[http://ubuntuforums.org/showthread.php?t=312823](http://ubuntuforums.org/showthread.php?t=312823)

---

### Post by kevdog on 2008-07-09
Technically gksudo is a symbolic link to the executable known as gksu.  I wish people would just start using gksu rather than gksudo -- its two letters less to type!

---

### Post by chalewa on 2008-07-09
eh i would probably go with ```
lspci
```

---

### Post by aysiu on 2008-07-09
> **CalvinB said:**
> Why is it gksudo instead of sudo, can you explain this to me? They seem both the same.
They're not the same. I can't tell you how many people screwed up their Firefox profile by using *sudo firefox*. Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dracule on 2008-07-09
> **aysiu said:**
> They're not the same. I can't tell you how many people screwed up their Firefox profile by using *sudo firefox*. Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

lol why would u ever need to run sudo firefox?

---

### Post by aysiu on 2008-07-09
> **dracule said:**
> lol why would u ever need to run sudo firefox?
Well, you wouldn't ever need to run *sudo firefox*, but if you've installed the Mozilla (as opposed to the Ubuntu repositories) version of Firefox, you may have to run ```
gksudo firefox
``` in order to install updates.

---

### Post by dracule on 2008-07-09
> **aysiu said:**
> Well, you wouldn't ever need to run *sudo firefox*, but if you've installed the Mozilla (as opposed to the Ubuntu repositories) version of Firefox, you may have to run ```
gksudo firefox
``` in order to install updates.

ah. that explains it. I stick with the repos.

---

### Post by keiichidono on 2008-07-10
> **aysiu said:**
> They're not the same. I can't tell you how many people screwed up their Firefox profile by using *sudo firefox*. Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
:shock:](*,) I hope i didn't mess anything up by running sudo to run nautilus. Would that mess anything up? sudo nautilus? That's about the only graphical app i think i launched with sudo.

---

### Post by aysiu on 2008-07-10
> **CalvinB said:**
> :shock:](*,) I hope i didn't mess anything up by running sudo to run nautilus. Would that mess anything up? sudo nautilus? That's about the only graphical app i think i launched with sudo.
In many cases, running *sudo* with a graphical application will do no harm, but it's a good habit to get into to use *gksudo* instead.

---

### Post by keiichidono on 2008-07-10
> **aysiu said:**
> In many cases, running *sudo* with a graphical application will do no harm, but it's a good habit to get into to use *gksudo* instead.
I'll watch out for that from now on, thanks!

---

