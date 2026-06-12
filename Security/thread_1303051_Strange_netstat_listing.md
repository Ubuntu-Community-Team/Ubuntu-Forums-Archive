---
title: "Strange netstat listing"
date: 2009-10-27
forum: Security
---

### Post by lavajumper on 2009-10-27
(This was originally posted in Networking & Wireless)

This is something that's been bugging me for years. When I do a netstat -anutp, I get a number of entries like the ones here:

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:41993           0.0.0.0:*               LISTEN      -               
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:44209           0.0.0.0:*                           -               

```

Note the PID being listed. I assume there is not anything 'wrong' as this has been happening on every Linux installation I've seen, It's just that a listen socket with no process id makes me nervous. Can anyone shed some light on this?

---

### Post by The Cog on 2009-10-28
> **lavajumper said:**
> (This was originally posted in Networking & Wireless)

This is something that's been bugging me for years. When I do a netstat -anutp, I get a number of entries like the ones here:

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:41993           0.0.0.0:*               LISTEN      -               
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:44209           0.0.0.0:*                           -               

```

Note the PID being listed. I assume there is not anything 'wrong' as this has been happening on every Linux installation I've seen, It's just that a listen socket with no process id makes me nervous. Can anyone shed some light on this?

Normal users aren't allowed to see the command arguments of other users, I think. **sudo netstat -anutp** will show you the missing info.

---

### Post by lavajumper on 2009-10-28
Thanks for responding. I ran the command both sudo'd and as root, same result. I'm curious if anyone else gets similar entries?

---

### Post by The Cog on 2009-10-28
> **lavajumper said:**
> Thanks for responding. I ran the command both sudo'd and as root, same result. I'm curious if anyone else gets similar entries?

Odd. I gather port 2149 is reserved for NFS. Are you running NFS? I don't, so I can't tell if it is normal NFS behaviour.

---

### Post by The Cog on 2009-10-28
I found this with google - seems like it's normal behaviour:
[http://lkml.indiana.edu/hypermail/linux/kernel/0101.0/0365.html](http://lkml.indiana.edu/hypermail/linux/kernel/0101.0/0365.html)

---

