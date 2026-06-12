---
title: "apt-p2p faster than the repos?"
date: 2010-03-08
forum: The Cafe
---

### Post by sandyd on 2010-03-08
I recently encountered a huge slowdown when downloading stuff from the repos (the main one). It would just sit there at 5kb/s.

I got fustrated cause I knew no matter how much I bugged comcast, they wouldnt fix my internet.... so I switched to apt-p2p.
To my suprise, It downloaded at 5mb/s. 
Which was faster than my normal repo downloading speed.

what???

---

### Post by NightwishFan on 2010-03-08
Delta debs would be great as well.

p2p downloads well with more users.

---

### Post by 2hot6ft2 on 2010-03-08
> **carlee said:**
> I recently encountered a huge slowdown when downloading stuff from the repos (the main one). It would just sit there at 5kb/s.

I got fustrated and switched to apt-p2p.
To my suprise, It downloaded at 5mb/s. 
Which was faster than my normal repo downloading speed.

what???
I saw that in synaptic the other day and was wondering how well it worked.
Thanks, it's all setup on this machine now.

---

### Post by juancarlospaco on 2010-03-08
1)Backup
2)backup
3)On the /etc/apt/sources.list replace the "http://" with "ftp://", 
replace "XX.archive.ubuntu.com" with the IP, 
ping to XX.archive.ubuntu.com to know the fixed IP that the server uses.
i.e. *deb [ftp://200.200.200.200/ubuntu](ftp://200.200.200.200/ubuntu) main universe multiverse*

:)

---

### Post by koleoptero on 2010-03-08
I guess I'm lucky my ISP mirrors the repos.

---

### Post by BuffaloX on 2010-03-08
Wow 5 MB/s! That's a very fast connection you got there.
I didn't even know there's a p2p option.
That should be default IMO.
Local servers here suck, so I use main.
Mostly I get about 1.5 Mbyte/s which is what my line can handle.

Does p2p use compression?

---

### Post by sandyd on 2010-03-08
> **BuffaloX said:**
> Wow 5 MB/s! That's a very fast connection you got there.
I didn't even know there's a p2p option.
That should be default IMO.
[B]Some ISPS still block and detest bittorent, or rather the concept of "seeding" "peers" and "filesharing".
however, [http://brainstorm.ubuntu.com/idea/14040/](http://brainstorm.ubuntu.com/idea/14040/)
[/B]
Local servers here suck, so I use main.
Mostly I get about 1.5 Mbyte/s which is what my line can handle.

Does p2p use compression?
**dont think so**
.

---

### Post by forrestcupp on 2010-03-08
But I thought P2P is illegal because it is *always* used for pirating. ;)

---

### Post by NightwishFan on 2010-03-08
> **forrestcupp said:**
> But I thought P2P is illegal because it is *always* used for pirating. ;)

At least one person will take this seriously.

---

### Post by forrestcupp on 2010-03-09
> **NightwishFan said:**
> At least one person will take this seriously.

Lol.  I guess you were wrong.  Nobody cares.

---

### Post by swoll1980 on 2010-03-09
If you switch the default repo to one of your choosing it may help. I got about 150Kb/s from the default, but I get 800+ from the one I choose.

---

### Post by NightwishFan on 2010-03-09
Aww, all the trolls are gone. Well on topic apt-p2p + delta deb will blow other updaters in the water.

---

