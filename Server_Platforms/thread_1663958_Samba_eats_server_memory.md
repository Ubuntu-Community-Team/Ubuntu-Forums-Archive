---
title: "Samba eats server memory"
date: 2011-01-10
forum: Server Platforms
---

### Post by konnorrigby on 2011-01-10
ok, so ive got a small server running. i host a web site for me and a few of my friends just for kicks. i have samba which puts an external Hdd on the network so i have all my music videos and media on every computer. but when issuing 
```
 free -m 
```

it tells me i only have like 5 or six megs free when samba is running and being used. so i tell it to empty cache 
```
 sync; echo 3 > /proc/sys/vm/drop_caches 
```

but it just goes rite back down again. how can i fix this? its making slower which sucks..

---

### Post by CharlesA on 2011-01-10
Post the output of free -m :)

---

### Post by konnorrigby on 2011-01-10
```
root@Connors-Server:~# free -m
             total       used       free     shared    buffers     cached
Mem:           488        269        218          0          1         26
-/+ buffers/cache:        241        246
Swap:         3151          0       3151
root@Connors-Server:~#

```

this is after running the free memory command...

And then it just goes down from there... not cool.

---

### Post by CharlesA on 2011-01-11
That looks about right for the base server install. Does the cached memory increase?

Here's what my free -m looks like:

```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       5934         46          0        [COLOR="Red"]173       3582[/COLOR]
[COLOR="Blue"]-/+ buffers/cache:       2179       3802[/COLOR]
Swap:        17523          0      17523

```

Check how much memory is being used by cache. That's "free" memory, that the system is using for disk caching, it'll be freed up automatically if needed.

EDIT: Here's what free -m looks like on one of my machines running Ubuntu Desktop:

```
charles@lucid:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        466         30          0         16        138
-/+ buffers/cache:        312        185
Swap:          894        171        723

```

---

### Post by konnorrigby on 2011-01-11
Ohhh. ok i just must have slow network tthen. any way to speed up my server?. ill check from school and its kinda( ALOTA) slow

---

### Post by CharlesA on 2011-01-11
Depends on what you are doing with it.

Are you trying to access files remotely?

---

### Post by konnorrigby on 2011-01-11
ive got samba and a web server on it,

---

### Post by CharlesA on 2011-01-11
It should be able to handle that.

If you are accessing files from the web server, it'll be limited by the upload speed of your connection.

---

### Post by konnorrigby on 2011-01-12
Thanks for the info im new to this whole server thing and i thought itd be fun and it turns out that a different computer on the network was downloading a fairly large torrent :O but its up to speed now. got my games and music mounted on every computer (and xbox) in the house :) thanks man.

---

