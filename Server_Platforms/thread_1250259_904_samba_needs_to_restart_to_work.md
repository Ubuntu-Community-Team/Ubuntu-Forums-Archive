---
title: "9:04: samba needs to restart to work"
date: 2009-08-26
forum: Server Platforms
---

### Post by bladerunner6 on 2009-08-26
I seem to have an issue whereby I have to restart samba server for the ubuntu shares to show in windows etc.

the service is set to on during bootup.
my ubuntu 9.04 is fully updated and I used gadmin to configure the samba conf file (I am using in a normal workgroup and no domains)
I can post the contents here.

---

### Post by kamaji792 on 2009-08-26
Are you sure your samba is starting up?

Try the following in a console:
```
$ ps -ef |grep mbd
```

Just tried it on mine and the output was:
```

root      4448     1  0 16:16 ?        00:00:00 /usr/sbin/nmbd -D
root      4451     1  0 16:16 ?        00:00:00 /usr/sbin/smbd -D
root      4479  4451  0 16:16 ?        00:00:00 /usr/sbin/smbd -D
gavin     4552  4533  0 16:17 pts/0    00:00:00 grep mbd

```

atb :)

---

### Post by y2kboy23 on 2009-08-26
I too was experiencing this problem.  What I figured out is that UFW was blocking some communications with Samba.  Just added the "allow from 192.168.1.0/24" or whatever your local network is, and my Samba hasn't needed to be restarted yet.  Give that a try.

---

### Post by bladerunner6 on 2009-08-26
my output is 
root     23610     1  0 21:06 ?        00:00:00 /usr/sbin/nmbd -D
root     23612     1  0 21:06 ?        00:00:00 /usr/sbin/smbd -D
root     23615 23612  0 21:06 ?        00:00:00 /usr/sbin/smbd -D
root     24099 23612  0 21:06 ?        00:00:00 /usr/sbin/smbd -D
root     24102 23612  0 21:06 ?        00:00:00 /usr/sbin/smbd -D
z        24219 24202  0 21:07 pts/1    00:00:00 grep mbd

firewall also is set correctly,

i got to manually switch off the samba and on again

---

