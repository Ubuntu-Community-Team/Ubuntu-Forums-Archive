---
title: "Empty directory ecept certain files"
date: 2011-01-10
forum: Server Platforms
---

### Post by rmb938 on 2011-01-10
So I have this script in my cronjob to make a .tar.gz every hour

```
#!/bin/bash
tar czf /home/rmb938/worldbackup/world_"$(date)".tar.gz /home/rmb938/server/world/ 
```Now eventually that folder were its saving the tar will get to big and I would like to delete the files in the folder.

How would I go about emptying the folder but keep all the files that contain "yesterdays" date.

---

### Post by koenn on 2011-01-10
you can use 'find' to find the files, and rm to remove them

here's an example: [http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/)

---

### Post by rmb938 on 2011-01-10
oh wow that works. Thanks :)

---

