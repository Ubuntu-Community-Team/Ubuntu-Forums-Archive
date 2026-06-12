---
title: "IPBlock error"
date: 2010-07-04
forum: Security
---

### Post by Seanlol on 2010-07-04
I can't get IPblock to start.  I keep getting an error that says

```
sean@Sean-Laptop:~$ DEBUG=1 sudo ipblock -s1
iplist[2750]: error: can't find level1.gz
ipblock[2736]: error: failed to start, cleaning up
```The Debug command returns the same thing. The other command that the FAQ says to enter returns
```

sean@Sean-Laptop:~$ egrep "iplist|ipblock" /var/log/syslog
Jul  4 13:31:15 Sean-Laptop iplist[1224]: error: can't find level1.gz
Jul  4 13:31:15 Sean-Laptop ipblock[1122]: error: failed to start, cleaning up
Jul  4 13:34:11 Sean-Laptop ipblock[1961]: error: update of level1.gz failed
Jul  4 13:34:13 Sean-Laptop ipblock[1961]: error: update of ads-trackers-and-bad-pr0n.gz failed
Jul  4 13:34:16 Sean-Laptop ipblock[1961]: error: update of edu.gz failed
Jul  4 13:34:18 Sean-Laptop ipblock[1961]: error: update of spyware.gz failed
Jul  4 13:34:20 Sean-Laptop ipblock[1961]: error: update of bogon.gz failed
Jul  4 13:34:35 Sean-Laptop iplist[2005]: error: can't find level1.gz
Jul  4 13:34:35 Sean-Laptop ipblock[1991]: error: failed to start, cleaning up
Jul  4 13:36:05 Sean-Laptop ipblock[2091]: error: update of level1.gz failed
Jul  4 13:36:07 Sean-Laptop ipblock[2091]: error: update of ads-trackers-and-bad-pr0n.gz failed
Jul  4 13:36:09 Sean-Laptop ipblock[2091]: error: update of edu.gz failed
Jul  4 13:36:12 Sean-Laptop ipblock[2091]: error: update of spyware.gz failed
Jul  4 13:36:14 Sean-Laptop ipblock[2091]: error: update of bogon.gz failed
Jul  4 13:37:24 Sean-Laptop iplist[2185]: error: can't find level1.gz
Jul  4 13:37:24 Sean-Laptop ipblock[2171]: error: failed to start, cleaning up
Jul  4 13:49:03 Sean-Laptop iplist[2385]: error: can't find level1.gz
Jul  4 13:49:03 Sean-Laptop ipblock[2371]: error: failed to start, cleaning up
Jul  4 13:58:21 Sean-Laptop iplist[2718]: thread[140420342499088]: info: logging to /tmp/ipblock.log
Jul  4 13:58:22 Sean-Laptop iplist[2725]: error: can't find level1.gz
Jul  4 13:58:22 Sean-Laptop ipblock[2711]: error: failed to start, cleaning up
Jul  4 13:58:22 Sean-Laptop iplist[2718]: info: User defined signal 1 signal caught
Jul  4 13:58:22 Sean-Laptop iplist[2718]: info: Terminated signal caught

```Any help fixing this? Thanks.

---

### Post by uljanow on 2010-07-05
Updating the following lists should work now 
[LIST]
[*]ads-trackers-and-bad-pr0n.gz   
[*]bogon.gz   	
[*]edu.gz  
[*]level1.gz   	
[*]spyware.gz
[/LIST]

If you get the message "iplist[2750]: error: can't find LIST" than it's due to a failed update. In that case just remove the list temporarily.

---

### Post by khopek on 2010-09-21
I'm also getting this error. Just heard of and installed this software today too.

---

### Post by trbooth on 2010-09-23
Just installed also. Same problem.

---

### Post by tafra on 2010-09-24
fine day for first post this is :) !

stumbled here searching for 
```
iplist[3221]: info: User defined signal 1 signal caught
```and it is your lucky day as i picked up solution for updated lists somewhere yesterday...

anyway, after each update do this:

```
cd /var/cache/iplist/
```and then:

```
sudo rename 's/\.php//' *.php
```first command gets you into folder where your new updates reside and
second comm does corection on files extensions removing .php part of .gz.php
extension thus allowing our iplist program to find them as it needs .gz files to do its magic...

anyway i hope this helps as it did help me and as i said i have read it somewhere
but i am still curious about this bit as it still keeps showing...

```
iplist[3221]: info: User defined signal 1 signal caught
```

---

### Post by uljanow on 2010-09-24
The signal information is normal and indicates the communication with the daemon process.

---

### Post by tafra on 2010-09-24
thanks uljanow,

so its a go,go,go... nice!

---

### Post by mlnease on 2010-10-11
> **tafra said:**
> fine day for first post this is :) !

stumbled here searching for 
```
iplist[3221]: info: User defined signal 1 signal caught
```and it is your lucky day as i picked up solution for updated lists somewhere yesterday...

anyway, after each update do this:

```
cd /var/cache/iplist/
```and then:

```
sudo rename 's/\.php//' *.php
```first command gets you into folder where your new updates reside and
second comm does corection on files extensions removing .php part of .gz.php
extension thus allowing our iplist program to find them as it needs .gz files to do its magic...

anyway i hope this helps as it did help me and as i said i have read it somewhere
but i am still curious about this bit as it still keeps showing...

```
iplist[3221]: info: User defined signal 1 signal caught
```

Brilliant, Tafra, thanks and thanks as always, Uljanow.

mike

---

### Post by dino99 on 2010-10-20
Hope to see the new release 0.29 on your ppa very soon, built on maverick too.

Thanks for your work.

---

### Post by mistypotato on 2010-10-30
error.....

**TOO MANY FILES**

Well, guess I have to delete at least one.  May have to combine some.

I wonder what the upper limit for IP ranges it can handle ?

---

### Post by ciobi on 2011-10-02
> **tafra said:**
> anyway, after each update do this:

```
cd /var/cache/iplist/
```and then:

```
sudo rename 's/\.php//' *.php
```I've run into a similar situation and I think something easier should work: after the first update go to **/var/cache/iplist/** and use the file names as keys in **ipblock.lists**, then update the **BLOCK_LIST** line in **ipblock.conf** accordingly. I expect your **ipblock.lists **file to have something like ```
level1.gz        http://some.site/some_path
```My suggestion is to first replace that with ```
level1.gz.php    http://some.site/some_path
```and then update **ipblock.conf**:```
BLOCK_LIST="level1.gz.php ..."
```Works for me ...

---

