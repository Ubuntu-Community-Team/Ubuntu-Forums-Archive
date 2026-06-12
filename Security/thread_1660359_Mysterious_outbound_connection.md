---
title: "Mysterious outbound connection"
date: 2011-01-05
forum: Security
---

### Post by P.T. on 2011-01-05
Good day,

Today I was busy with setting up some final things for an SSH server on my desktop. This is so I can do stuff with my pc while at school.
While testing the connection I had firestarter open and saw an interesting connection. At first I thought it was because of Vuze (since I was downloading). But after closing Vuze, the connection was still there.

I tried staring it away from the list in firestarter, but that didn't work, neither did putting it on the blacklist (though I haven't rebooted yet).
After logging out and back in I immediately started firestarter, but the connection was still alive. Wireshark told me it did nothing though.

Most annoying thing is that the connection goes to China.

So, is this something to worry about? Should I kill this connection, or try to find out what is causing it (and how)?

---

### Post by anomie on 2011-01-05
Let's see output from: 
```
$ sudo netstat -tnp
```

Perhaps it's just in FIN_WAIT, and taking a very long time to close (following your p2p activity).

---

### Post by P.T. on 2011-01-05
The output is empty :\. 

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name

```It's almost like some sort of ghost connection :p

---

### Post by anomie on 2011-01-05
I'm not familiar with firestarter, but I'd suggesting "restarting it" if possible. For whatever reason, it (really, iptables) may be tracking state on a connection that is long gone.

---

### Post by P.T. on 2011-01-05
I just rebooted my pc and the connection indeed is gone. (Side note, I also blacklisted the IP earlier without rebooting).

In another tread I read about firestarter not being maintained, so I'll have to take a look at ufw I guess!

Thanks for helping :p.

---

