---
title: "Experimenting with Lucid"
date: 2014-08-23
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2014-08-23
Sorting through my .iso CD collection I came across my 10.04 Lubuntu,Ubuntu and Xubuntu .isos. I proceeded to install 10.04 Ubuntu on a DT. As usual it installed as expertly as ever and with the repos still updating/upgrading and all the bells and whistles from the USC.

  I spend most of my time in development testing but I do like to take a time out now and again and see that even the older, well, (we really can't call them older or legacy) but I would rather call them 'setted milestones' - can do with  non pae form factors what todays development releases cannot do. 

  This of course is due to the benevolence of Canonical as a whole and it's founder , Mark Shuttleworth, who has certainly changed the internet landscape as we see it. Doing a Lucid install also helps me appreciate how Ubuntu has developed over the past 4 years and I know for certain that there is ever oh so much to learn from this gem which used to be but a diamond in the rough.

Regards...

---

### Post by ajgreeny on 2014-08-23
10.04 only gets the updates which are still available for the server edition, as far as I know, so I don't think you will get updates to GUI programs, unless of course, the repos for those are still in the same place as before, and have not been moved to the EOL address.  

In that case you would have managed to get the one update of GUI apps from installation version to the last version that was in Lucid but I don't think you'll get any more.

---

### Post by ventrical on 2014-08-23
All the repos are intact from here and I can download at will from the USC. and thats Ubuntu desktop, not server.

---

### Post by ventrical on 2014-08-23
The most recent kernel upgrade was not so long ago.

```

ventrical@ventrical-desktop:~$ uname -a
Linux ventrical-desktop 2.6.32-64-generic #128-Ubuntu SMP Tue Jul 15 08:34:12 UTC 2014 i686 GNU/Linux
ventrical@ventrical-desktop:~$ 



```

---

### Post by ventrical on 2014-08-23
Well it certainly is interesting to read this:

[http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)

yet still getting kernel upgrade from only one month ago .. or perhaps this is the server version of kernel ?

Anyways .. this is not a support question .. just a note that the repos and USC for Lucid are still operating.

---

### Post by mörgæs on 2014-08-23
In case someone is following the thread: The observation that 10.04 desktop gets some updates is not an indication that it's updated. On the contrary, GUI related packages are left at the stage where they were in april 2013. Security holes are likely to exist.

One can of course play around in a 10.04 desktop but don't use it for anything important.

---

### Post by mörgæs on 2014-08-23
- and changed the title. 10.04 is certainly not a solid choice.

---

### Post by fireflower on 2014-08-23
10.04 is what I first used when I got into Linux. It's a solid iso. Nevermind the hell it put me through with wireless drivers being unavailable. I learned dammit.

---

### Post by ventrical on 2014-08-23
> **mörgæs said:**
> - and changed the title. 10.04 is certainly not a solid choice.

You misunderstood my title.  I said for "castaways" and non pae.

---

### Post by ventrical on 2014-08-23
> **mörgæs said:**
>  Security holes are likely to exist.



Can you document some here please?

Thanks..

---

### Post by QIII on 2014-08-23
Being beyond EOL, I wouldn't call it a solid choice for anything.

Older hardware?  Use a lighter version or a derivative like Bodhi.

---

### Post by QIII on 2014-08-23
> **ventrical said:**
> Can you document some here please?

Thanks..

Heartbleed

---

### Post by ventrical on 2014-08-23
Never happened here on any of my Lucid machines and the fact is that the Lucid SSL version is too old for Heartbleed to affect it.

[http://askubuntu.com/questions/445164/do-i-need-to-take-action-on-a-10-04-lts-server-to-avoid-the-heartbleed-vulnerabi](http://askubuntu.com/questions/445164/do-i-need-to-take-action-on-a-10-04-lts-server-to-avoid-the-heartbleed-vulnerabi)

Uhh .. just for the record ... I never said Lucid was a "solid choice" nor did I ever make that implication. I did state that it was a "setted milestone" and that's a fact. Sooo.. I'll still keep having fun experimenting with Lucid :) lol

My Lucid SSL version ( natually immune to Heartbleed) so Lucid still has some virtues after all :)

```

ventrical@ventrical-desktop:~$ openssl version
OpenSSL 0.9.8k 25 Mar 2009
ventrical@ventrical-desktop:~$ 


```

Regards..

---

### Post by ventrical on 2014-09-01
Just installed the latest dev RC kernel and it amazingly enhances Lucid.

```



ventrical@ventrical-desktop:~$ uname -a
Linux ventrical-desktop 3.17.0-031700rc2-generic #201408251935 SMP Mon Aug 25 23:56:25 UTC 2014 i686 GNU/Linux
ventrical@ventrical-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid
ventrical@ventrical-desktop:~$ 


```

---

