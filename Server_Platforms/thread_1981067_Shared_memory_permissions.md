---
title: "Shared memory permissions"
date: 2012-05-16
forum: Server Platforms
---

### Post by Alan87i on 2012-05-16
I'm having an issue with Zoneminder and shared memory. 
I have increased the shmall and shmax to beyond what the system has in it 2 GB. 
And normal usage shows 256 Mb or so almost all the time. 

Errors are 
05/15/2012 19:36:23.784376 zmwatch[5089].ERR [Can't get shared memory id '7a6d3014', 20: No such file or directory]
05/15/2012 19:36:23.784767 zmwatch[5089].INF [Restarting capture daemon for New, shared memory not valid]

Too me this is saying the user does not have access or the rw permissions it needs to use the key. 

I have no clue how to fix it. 
system is 8.04.4 And I don't want to upgrade. 

```
allan@allan-cameras:~$ ipcs -s

------ Semaphore Arrays --------
key        semid      owner      perms      nsems

allan@allan-cameras:~$ ipcs -m

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status

```
But if I'm is a root terminal I get 
```

root@allan-cameras:/home/allan# ipcs -l

------ Shared Memory Limits --------
max number of segments = 4096
max seg size (kbytes) = 1048576
max total shared memory (kbytes) = 33554432
min seg size (bytes) = 1

------ Semaphore Limits --------
max number of arrays = 128
max semaphores per array = 250
max semaphores system wide = 32000
max ops per semop call = 32
semaphore max value = 32767

------ Messages: Limits --------
max queues system wide = 16
max size of message (bytes) = 8192
default max size of queue (bytes) = 16384

root@allan-cameras:/home/allan# ipcs -s

------ Semaphore Arrays --------
key        semid      owner      perms      nsems
0x00000000 0          www-data  600        1

root@allan-cameras:/home/allan# ipcs -m

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status
0x7a6d3008 917504     www-data  700        9217188    2
0x7a6d300d 950273     www-data  700        9217188    2
0x7a6d300c 983042     www-data  700        9217188    2
0x7a6d300e 1015811    www-data  700        9217188    2
0x7a6d3009 1048580    www-data  700        9217188    2
0x7a6d300a 1081349    www-data  700        9217188    2
0x00000000 262152     root      600        393216     2          dest
0x7a6d300b 1114122    www-data  700        9217188    3
0x7a6d3014 1146891    www-data  700        14132228   0

```

The 8 www-data's are all for cameras's or monitors 7 of them are cctv from a capture card. the last one 0x716d3014 is from an IP cam witch will not work.And is showing the above error in the logs. 

Thanks for any help.

---

