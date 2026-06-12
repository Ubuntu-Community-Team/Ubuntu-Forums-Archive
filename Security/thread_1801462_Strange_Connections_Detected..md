---
title: "Strange Connections Detected."
date: 2011-07-10
forum: Security
---

### Post by Snowboi on 2011-07-10
Hey community, got some weird connections on ubuntu today
Ubuntu 10.04
Started noticing memory running out somehow... Without my consent. When i ran 

```
netstat -ln
```
There is one at the top (that i left out) but i believe that its just my regular internet connection

```

tcp6       0      0 ::1:631                 :::*      LISTEN                        
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:58016           0.0.0.0:*                          
```

Only one internet connection, no VNC or SSH connections.
Samba is installed im not sure if its by default in ubuntu 10.04.
Getting kinda worried here ubuntu community :confused:
Please Help!

Edit : Also what is 
```
/org/freedesktop/ConsoleKit/Session2
```
I found that in my auth.log apparently it gained temporary root permissions something to do with software center?
Im guessing its just to install with aptitude or to download and install a program.

---

### Post by Dangertux on 2011-07-10
> **Snowboi said:**
> Hey community, got some weird connections on ubuntu today
Ubuntu 10.04
Started noticing memory running out somehow... Without my consent. When i ran 

```
netstat -ln
```There is one at the top (that i left out) but i believe that its just my regular internet connection

```

tcp6       0      0 ::1:631                 :::*      LISTEN                        
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:58016           0.0.0.0:*                          
```Only one internet connection, no VNC or SSH connections.
Samba is installed im not sure if its by default in ubuntu 10.04.
Getting kinda worried here ubuntu community :confused:
Please Help!

68/udp - dhcp/bootp 
631/tcp - cups
5353/udp - avahi-daemon
58016/udp - unassigned used for an arbitrary service.

Try 
```

sudo netstat -alnp

```Might help determine what program is using each

---

### Post by Snowboi on 2011-07-10
> **Dangertux said:**
> 68/udp - dhcp/bootp 
631/tcp - CUPS 
5353/udp - avahi-daemon
58016/udp - unassigned used for an arbitrary service.

Try 
```

sudo netstat -alnp

```

Might help determine what program is using each

Alright thanks i guess there is not that much to worry about :)
Still does not answer two of my questions tho 

> 
Started noticing memory running out somehow... Without my consent. When i ran 

Could be possible temporary files from browsers, but in any case is there any logs that i can use to track where data has recently been put or stored?

And

> 
Samba is installed im not sure if its by default in ubuntu 10.04.

Found out that it is a cross platform printing program ?
Is there any need for this since i am using a desktop computer and do not need any wireless connections ?

---

### Post by The Cog on 2011-07-11
Your memory usage probably isn't as bad as you think. Linux likes to use unused memory as disk cache. This isn't a problem because if it's needed for something else like a running program wants memory, it just reduces the size of the cache again. In fact it's a good thing because otherwise all that memory would be wasted, completely unused.

When you look at the output of the command **free**, the top **Mem:** line shows memory usage including memory that's being used as disk cache. The free memory tends to get very small as more spare memory gets used towards disk caching. If you want to know how much memory is free if a program should want it, you should look at the second line, **-/+ buffers/cache:** which shows memory usage as though the disk caching wasn't happening. 


Samba is a file and printer sharing program for sharing with windows servers. But it doesn't seem to be running on your machine (the ports aren't showing in your netstat output). What makes you think is is installed?

---

### Post by Snowboi on 2011-07-12
> **The Cog said:**
> Your memory usage probably isn't as bad as you think. Linux likes to use unused memory as disk cache. This isn't a problem because if it's needed for something else like a running program wants memory, it just reduces the size of the cache again. In fact it's a good thing because otherwise all that memory would be wasted, completely unused.

When you look at the output of the command **free**, the top **Mem:** line shows memory usage including memory that's being used as disk cache. The free memory tends to get very small as more spare memory gets used towards disk caching. If you want to know how much memory is free if a program should want it, you should look at the second line, **-/+ buffers/cache:** which shows memory usage as though the disk caching wasn't happening. 


Samba is a file and printer sharing program for sharing with windows servers. But it doesn't seem to be running on your machine (the ports aren't showing in your netstat output). What makes you think is is installed?

I understand how linux uses cache, but its a strange jump from around 1.7gb free space to 1.1gb of free space :confused:

Samba-common and samba-common-bin is installed.

---

### Post by karlson on 2011-07-12
> **Snowboi said:**
> I understand how linux uses cache, but its a strange jump from around 1.7gb free space to 1.1gb of free space :confused:

Samba-common and samba-common-bin is installed.

You can use top for memory to see the biggest users.  Just sort the output by the VIRT column.

---

### Post by The Cog on 2011-07-13
> I understand how linux uses cache, but its a strange jump from around 1.7gb free space to 1.1gb of free spaceWell, I don't think that's at all strange. If anything reads anything on the disk, then those disk contents are retained in the cache in case they are wanted again. Anything reading the disk - check for updates reads the apt database, there is a file indexing utility that reads the entire directory structure occasionally, etc.

---

### Post by Snowboi on 2011-07-14
> You can use top for memory to see the biggest users. Just sort the output by the VIRT column.

Talking about hard drive space =/, top just displays running processes.

> Well, I don't think that's at all strange. If anything reads anything on the disk, then those disk contents are retained in the cache in case they are wanted again. Anything reading the disk - check for updates reads the apt database, there is a file indexing utility that reads the entire directory structure occasionally, etc.

alright, seems effective. I will monitor my computer and possibly try to expand my partitions again. (sadly have a wubi install, need to create a seperate partition). Thanks.

---

### Post by CharlesA on 2011-07-14
You can check disk usage with:

```
df -h
```
```
du -h
```

---

### Post by Snowboi on 2011-07-15
> **CharlesA said:**
> You can check disk usage with:

```
df -h
```
```
du -h
```

Well thanks guys iv had my question answered ill post a new topic for a different question thanks for answers guys. :)

---

