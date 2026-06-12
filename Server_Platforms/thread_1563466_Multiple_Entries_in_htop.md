---
title: "Multiple Entries in htop?"
date: 2010-08-29
forum: Server Platforms
---

### Post by Jose Catre-Vandis on 2010-08-29
Running 9.04 Xubuntu desktop as server and development environment. I turn off gdm once booted up.

When sshing in for other computer I ran htop, and found the following multiple processes:

```
2381 root      21   1  8108  4008  2520 S  0.0  0.3  0:00.13 /usr/sbin/bandwidthd
2382 root      21   1  8108  3996  2516 S  0.0  0.3  0:00.18 /usr/sbin/bandwidthd
2383 root      21   1  7976  2524  2480 S  0.0  0.2  0:00.09 /usr/sbin/bandwidthd
2386 root      21   1  7180  2524  2480 S  0.0  0.2  0:00.04 /usr/sbin/bandwidthd

2751 root      20   0  7212  1284  1000 S  0.0  0.1  0:00.13 /usr/sbin/nmbd -D
2752 root      20   0  7212  1120   868 S  0.0  0.1  0:00.00 /usr/sbin/nmbd -D
2756 root      20   0 13040  1892  1596 S  0.0  0.1  0:00.01 /usr/sbin/smbd -D
2772 root      20   0 13040   216   212 S  0.0  0.0  0:00.00 /usr/sbin/smbd -D

5835 www-data  20   0 21384  3076   552 S  0.0  0.2  0:00.00 /usr/sbin/apache2 -k start
5836 www-data  20   0 21384  3076   552 S  0.0  0.2  0:00.00 /usr/sbin/apache2 -k start
5837 www-data  20   0 21384  3076   552 S  0.0  0.2  0:00.00 /usr/sbin/apache2 -k start
5838 www-data  20   0 21384  3076   552 S  0.0  0.2  0:00.00 /usr/sbin/apache2 -k start
5839 www-data  20   0 21384  3076   552 S  0.0  0.2  0:00.00 /usr/sbin/apache2 -k start

6326 user       20   0  5936  3184  1436 S  0.0  0.2  0:00.13 /bin/bash
6330 user       20   0  5936  3180  1436 S  0.0  0.2  0:00.13 /bin/bash
6338 user       20   0  5936  3180  1436 S  0.0  0.2  0:00.14 /bin/bash 
```

Is there any good reason why I have multiples of these, or conversely is there a problem by having them? Everything works OK. Apache is only serving up my web development pages which I work on now and then, so its not having to handle external traffic. The server is port forwarded on port 80 through the router.

---

### Post by scorp123 on 2010-08-29
Hard to tell. I'd recommend you switch to tree view? Besides, troubleshooting stuff like that using "htop" isn't really useful, I'd recommend good ol' "ps". What does "ps" say about those processes? Can you please post the output of this command:

```
ps -efH
```

This should list all processes in a hierarchical fashion, so you'd see which process spawned which other process ... Usually it goes like this e.g. init spawns apache, apache spawns multiple copies of itself (so it can handle a bunch of incoming requests at once), and so on.

Very small and shortened output example from my system here:
```

...
root       699     1  0 12:08 ?        00:00:00   /usr/sbin/sshd
root      2086   699  0 19:19 ?        00:00:00     sshd: rdj [priv] 
rdj       2177  2086  0 19:19 ?        00:00:00       sshd: rdj@notty  
rdj       2178  2177  0 19:19 ?        00:00:00         /usr/lib/openssh/sftp-server
root      2621   699  4 20:14 ?        00:00:00     sshd: rdj [priv] 
rdj       2713  2621  0 20:14 ?        00:00:00       sshd: rdj@pts/0  
rdj       2714  2713 23 20:14 pts/0    00:00:00         -bash
rdj       2732  2714  0 20:14 pts/0    00:00:00           ps -efH
...

```

You see that? root's "sshd" with PID 699 spawned a SSH session "rdj@notty" with PID 2177 ... so it's a session without terminal. And that one spawned SSH's "sftp-server" (PID 2178) for file transfers. And it's correct because I really am using FileZilla right now and transferring a bunch of files. Another SSH daemon with PID 2621 spawned yet another login: "rdj@pts/0" with PID 2713; so we can tell it's an open remote terminal. Inside that terminal a "bash" shell was spawned (PID 2714) and in that shell the command "ps -efH" was executed (PID 2732) ... so you can really see 'who started whom' here.

The entire output is far far longer ... but if you take a look at your system's own **"ps -efH"** output a few things might be easier to understand .... 

Hope this helps? :D

---

### Post by Jose Catre-Vandis on 2010-08-29
Here is the ps -efH output for those processes, not sure it helps?

```

root      2381     1  0 10:51 ?        00:00:12   /usr/sbin/bandwidthd
root      2382  2381  0 10:51 ?        00:00:12     /usr/sbin/bandwidthd
root     20939  2382  0 21:11 ?        00:00:00       [bandwidthd] <defunct>
root      2383  2381  0 10:51 ?        00:00:12     /usr/sbin/bandwidthd
root     20400  2383  0 20:51 ?        00:00:00       [bandwidthd] <defunct>
root      2386  2381  0 10:51 ?        00:00:13     /usr/sbin/bandwidthd
root      2390  2386  0 10:51 ?        00:00:00       [bandwidthd] <defunct>
root     21053  2381  0 21:18 ?        00:00:00     [bandwidthd] <defunct>

root      2751     1  0 10:51 ?        00:00:01   /usr/sbin/nmbd -D
root      2752  2751  0 10:51 ?        00:00:00     /usr/sbin/nmbd -D
root      2756     1  0 10:51 ?        00:00:00   /usr/sbin/smbd -D
root      2772  2756  0 10:51 ?        00:00:00     /usr/sbin/smbd -D
root     10573  2756  0 14:10 ?        00:00:05     /usr/sbin/smbd -D
root     10574  2756  0 14:10 ?        00:00:00     /usr/sbin/smbd -D
root     10878  2756  0 14:27 ?        00:00:00     /usr/sbin/smbd -D
root     10880  2756  0 14:28 ?        00:00:22     /usr/sbin/smbd -D

root      3307     1  0 10:51 ?        00:00:00   /usr/sbin/apache2 -k start
www-data  5835  3307  0 11:24 ?        00:00:00     /usr/sbin/apache2 -k start
www-data  5836  3307  0 11:24 ?        00:00:00     /usr/sbin/apache2 -k start
www-data  5837  3307  0 11:24 ?        00:00:00     /usr/sbin/apache2 -k start
www-data  5838  3307  0 11:24 ?        00:00:00     /usr/sbin/apache2 -k start
www-data  5839  3307  0 11:24 ?        00:00:00     /usr/sbin/apache2 -k start
www-data  7732  3307  0 12:20 ?        00:00:00     /usr/sbin/apache2 -k start

user       6326  6325  0 11:31 pts/1    00:00:00     /bin/bash
user       6330  6325  0 11:31 pts/2    00:00:00     /bin/bash
user       6338  6325  0 11:31 pts/3    00:00:00     /bin/bash
user       6348  6325  0 11:31 pts/4    00:00:00     /bin/bash
user      21056  6348  0 21:18 pts/4    00:00:00       ps -efH
```

---

### Post by scorp123 on 2010-08-29
Apache looks normal ... but you got a few zombies up there. All those processes marked with "***<defunct>***" are zombies. See here:
[http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

... No, they don't bite. And they don't "infect" other processes. It's just that those processes should be dead ... but instead they are still walking around in your process table. This indicates that something is wrong with that ***bandwithd*** process ... misconfigured perhaps?

Also I see that you logged in like 4 x times ... Is that correct? You can check who is logged in via the "**who**" command.

---

### Post by Jose Catre-Vandis on 2010-08-29
Hi scorp123, thanks for your help.

I'll have a look at bandwidthd and see what is going on. Quite likely I am logged in 4 times - at the server, by ssh and with screen running four sessions (that's the four showing up, maybe this is causing the multiple entries? (yes - for logins)

Tried killall on bandwidthd and then restarted the daemon, only to get 7 processes back up and running (no zombies!) :) Oh Well.

---

