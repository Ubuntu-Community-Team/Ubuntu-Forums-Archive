---
title: "What is the best way to transfer 50GB of images from one Vultr instance to another?"
date: 2017-03-01
forum: Server Platforms
---

### Post by toni12 on 2017-03-01
I have Vultr 8GB instance in Paris datacenter.


I would like to transfer my site from Paris to Frankfurt.


But I have a website that has 40GB of images.


What would be the fastest and the best way to transfer 40GB of images between two Vultr datacenters??


Regards
A.I.

---

### Post by TheFu on 2017-03-01
"Best" is highly subjective.  Fastest isn't always best, since the fastest way would be highly insecure and would have your credentials shown.

```
$ rsync -avz {source} {target}
```

Setup ssh-keys between the accounts on each system - rsync uses ssh tunnels by default.  rsync needs to be installed on both systems.

rsync and ssh are in my top 10 greatest computing inventions of all time. Learn them. Know them. Love them.

---

### Post by toni12 on 2017-03-01
How long this would take approx?

---

### Post by ian-weisser on 2017-03-01
How would we know?
Try a test run and see.

---

### Post by TheFu on 2017-03-01
> **toni12 said:**
> How long this would take approx?

Depends on many factors, mainly internet network speed, but also disk and CPU performance.

The good news is that rsync can be restarted and it picks up where it left off.

---

### Post by toni12 on 2017-03-01
That is good news.

---

### Post by TheFu on 2017-03-01
Dude, rsync is one of those amazing tools worth learning.  The manpage is pretty good, but there are some tricks.

The command I provided recursively copies (syncs) all the files and directories from the source to the target, assuming read access is possible on the source-side. Be cautious about using trailing / on directories for the source. It matters.  Test it out on some small directories locally to see how it works with and without the /.

---

### Post by Habitual on 2017-03-01
[http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

---

### Post by volkswagner on 2017-03-01
+1 for rsync. 

I suggest first launching a screen session so you can disconnect and keep the sync going.

---

