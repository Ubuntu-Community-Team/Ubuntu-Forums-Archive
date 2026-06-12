---
title: "Automatically delete files older than 6 months in folder"
date: 2010-03-27
forum: Server Platforms
---

### Post by rado3105 on 2010-03-27
I have server running ubuntu. There is folder /var/netflow and I have there files, which creates every 5minutes new ones(monitoring traffic on network). And I need to delete files older than 6 months manually. Can you help?

---

### Post by CharlesA on 2010-03-27
I actually had this bookmarked somewhere...

Check [here]("http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/").

---

### Post by fang0654 on 2010-03-27
You can use the find command for that:

```

find /var/netflow -ctime +180 -delete

```

This will delete any files created over 180 days ago in the /var/netflow folder (and all subfolders).

Add this to a cron job and it will be automatic.

---

