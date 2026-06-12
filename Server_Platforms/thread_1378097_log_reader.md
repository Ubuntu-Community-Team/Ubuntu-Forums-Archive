---
title: "log reader"
date: 2010-01-11
forum: Server Platforms
---

### Post by cong06 on 2010-01-11
I'm looking for a command line tool that does a good job of following logs.

I run squid and apt-proxy, and whenever logrotate cleans up the logs, I have to restart "tail" to continue following the log.

Is there any tool I can use that automatically detects logrotate and switches to the new file?

I guess at the very least, a tool that crashes when the file "disappears" so that I can restart it instead of stare and wonder why the log isn't updating...

---

### Post by Lars Noodén on 2010-01-11
> **cong06 said:**
> 
I guess at the very least, a tool that crashes when the file "disappears" so that I can restart it instead of stare and wonder why the log isn't updating...

Are you sure that tail is not noticing?
tail: /tmp/x has been replaced, reopening.

---

### Post by cong06 on 2010-01-11
yeah... I'm sure. Mostly because the log simply hangs, and I have to kill tail and restart it.

I wonder if log-rotate does something that regular replacing files doesn't do...

Here. Try this.
```

touch /tmp/log

```
and in another terminal
```

tail -f /tmp/log

```
then run
```

echo "dump1" >> /tmp/log
mv /tmp/log /tmp/log.2
touch /tmp/log
echo "dump2" >> /tmp/log

```

tail shows the "dump1" and then hangs after the file is switched.
Maybe if logrotate would copy and then delete, it would work, instead of move and then replace... (Well, I think that's what it does anyway)

---

### Post by BkkBonanza on 2010-01-11
Are you using the -F option in tail? It tells tail to follow the name and not the file descriptor. Probably when the file gets replaced the descriptor becomes invalid. By following the name it should continue with a new file with the same name.

Note: -F not the same as -f.

---

### Post by cong06 on 2010-01-12
> **BkkBonaza said:**
> Are you using the -F option in tail?

Sweet!
Maybe I should more fully read man-pages. Yet again Ubuntu forums makes up for my inadequacies.

Thanks.

---

