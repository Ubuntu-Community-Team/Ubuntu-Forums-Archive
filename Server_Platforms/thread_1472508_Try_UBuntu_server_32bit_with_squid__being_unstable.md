---
title: "Try UBuntu server 32bit with squid  being unstable..."
date: 2010-05-04
forum: Server Platforms
---

### Post by dr3x on 2010-05-04
hello all..last day i try for new LTS 10.4 32 bit at home..i install it with squid 2.7stable8 on it..after few hours my squid are freeze...so i have to reboot again and again..it never happen before with hardy. when i look on squid log...i cant find something wrong..but when i check wheter squid running or not.. squid wont auto running on start up..
then i look on system log..i got May  4 22:30:38 

"caesar squid[1042]: Squid Parent: child process 1045 started
May  4 22:30:38 caesar kernel: [  153.422428] warning: `squid' uses 32-bit capabilities (legacy support in use)"

can someone here give me any information how to solve this...thanks :popcorn:

---

### Post by ghost_ryder35 on 2010-05-04
you dont need to reboot to stop and start squid
```

foo@ubuntu:~$ service squid restart

```

On the other problem of it "freezing".  are you running out of disk space?  Squid will puke all over its self if it can not write to the disk.  Next time Squid stops working correctly run this command and paste the output.
```

foo@ubuntu:~$ df -h

```

---

### Post by jijiisme on 2011-07-04
yes i also face that problem my server version is 10.04.2 LTS 64 bit.

---

