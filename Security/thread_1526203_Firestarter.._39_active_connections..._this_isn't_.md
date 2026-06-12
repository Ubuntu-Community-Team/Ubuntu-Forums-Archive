---
title: "Firestarter.. 39 active connections... this isn't normal, is it ?? :-("
date: 2010-07-07
forum: Security
---

### Post by Onompoly on 2010-07-07
any input?? thanks

---

### Post by Onompoly on 2010-07-07
I'm quite concerned and I'm moving this from security to here, I need input.
Thanks every

---

### Post by Onompoly on 2010-07-07
I moved this to 
[http://ubuntuforums.org/showthread.php?p=9561066#post9561066](http://ubuntuforums.org/showthread.php?p=9561066#post9561066)

Sorry for basically duplicating, thanks for any input guys.

---

### Post by bodhi.zazen on 2010-07-07
You have not provided us with sufficient information to make any judgement. The number of connections is almost irrelevant.

You need to tell us what the connections are.

Show us the output of one or all of these commands "

```
sudo netstat -an | grep LISTEN | grep -v ^unix
sudo netstat -ntulp 
sudo lsof -i -n -P
```

---

### Post by cariboo on 2010-07-08
Please don't create multiple threads on the same subject, I have merged your two threads.

---

