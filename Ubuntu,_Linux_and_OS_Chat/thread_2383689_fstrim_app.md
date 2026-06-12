---
title: "fstrim app"
date: 2018-01-28
forum: Ubuntu, Linux and OS Chat
---

### Post by j3984 on 2018-01-28
There are thousands of young coders on these forums.....could one of you please write an app suitable for the repos that runs an SSD trim command  

"sudo fstrim -v / "    from a one clik desktop icon...  it would be great...

---

### Post by cruzer001 on 2018-01-28
You should already have a weekly cron job with the -a switch on.  Is that not good enough?
```

cat /etc/cron.weekly/fstrim
```

[https://www.digitalocean.com/community/tutorials/how-to-configure-periodic-trim-for-ssd-storage-on-linux-servers](https://www.digitalocean.com/community/tutorials/how-to-configure-periodic-trim-for-ssd-storage-on-linux-servers)

---

