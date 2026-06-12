---
title: "boot issues"
date: 2010-09-10
forum: Server Platforms
---

### Post by davtom on 2010-09-10
Using Ubuntu Server 10.04, I was adding a new file system to mount today. I made a mistake editing the fstab folder for mounting a new partition, and now I can no longer boot. I attempted to use a live disc to edit correctly, and did so, however I still get errors on boot. I have included a screenshot of what I get on screen while trying to boot. Can anyone help me?

---

### Post by gobbledigook on 2010-09-10
this is why you should always make a backup of files before editing...

```
sudo cp /etc/fstab /etc/fstab_backup
```

;)

the messages you are getting in that screen grab are to do with your network interfaces not to do with fstab?


i don't know what those errors mean so... try [googling]("http://www.google.co.uk/search?hl=en&q=ureadahead-other+main+process+terminated+with+status+4&meta=&aq=f&aqi=g2g-m4&aql=&oq=&gs_rfai=") the error and readign up about it :)

---

