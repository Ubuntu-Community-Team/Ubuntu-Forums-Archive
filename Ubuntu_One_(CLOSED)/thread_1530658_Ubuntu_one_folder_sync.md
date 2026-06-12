---
title: "Ubuntu one folder sync"
date: 2010-07-13
forum: Ubuntu One (CLOSED)
---

### Post by su-37 on 2010-07-13
Hey last week i was able to sync folders like documents and so on to Ubuntu one. Now when i try to do it nothing happens. I right click , click synchronize on Ubuntu one and nothing happens. From memory isnt a green tick supposed to appear?
Thanks in advance:p

---

### Post by duanedesign on 2010-07-14
you can check the folders that have been added to your list of UDFs (User Designated Folders) by opening a Terminal and running the command:

```
u1sdtool --list-folders
```

EX:
  id=7f21890b-dafb-40c5-ba97-20929c5933d2 subscribed=True path=/home/duanedesign/Photos

NOTE: Make sure subscribed=True

If that checks out can you run the following command and post the output:

```
u1sdtool -s
```

You can check the number of items waiting to sync with:

```
u1sdtool --waiting-metadata | wc -l
```
and
```
u1sdtool --waiting-content | wc -l
```

You will be able to gauge progress because the numbers will get smaller over time.

thank you,
duanedesign

---

