---
title: "JVM Tuning Problem"
date: 2009-11-14
forum: Server Platforms
---

### Post by martynemworks on 2009-11-14
This maybe more of a JVM problem ... I've got a set up that isnt all that common so there doesnt appear to be much support / documentation on google about this but here goes.

I have a VPS with ubuntu server installed. On this VPS, I have 512MB memory - not much I know but that's all I have to work with at the moment.

Anway I'm running tomcat on here with the following:
```

JAVA_OPTS="-Xms32m -Xmx48m -XX:MaxPermSize=16m -server"

```

After and hour or so of running, top reports the following usage:
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5173 martyn    20   0  325m 191m 8932 S  0.7 37.4   0:35.57 java

```

Why would 191m of memory be used when I specified only use 64m?

Thanks.

---

### Post by sicn on 2009-11-16
First of all, are you sure this is the only Java process. Second, are you running 64bit Ubuntu?

The VIRT is fairly normal since it includes everything associated with that process, file handles, shared libraries, everything... If it's 64bit, all handles and referenced libraries are twice as big and thus it can look like alot.

The RES is more interesting though, this should be close to what you've set as "Xmx".

If you are using 64bit and you use a new enough Java Runtime, you could try to decrease the memory usage by setting -XX:+UseCompressedOops as an additional parameter. A more detailed explanation about this parameter can be found here [http://www.mindbug.org/2008/11/cost-of-64bit-jvm.html](http://www.mindbug.org/2008/11/cost-of-64bit-jvm.html).

---

