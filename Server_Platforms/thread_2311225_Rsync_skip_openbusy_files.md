---
title: "Rsync skip open/busy files"
date: 2016-01-25
forum: Server Platforms
---

### Post by nerdtron on 2016-01-25
Hi All,

I have a server in which a windows share is mounted. I have a nightly script to do an rsync copy from that mounted partition to a local folder of Ubuntu. The problem is, some users of that shard folder forgot to close their files and leave them open overnight. Rsync encounters and errors on backing up those open files. Thus my script will fail to proceed since the exit code for rsync command is not zero. Meaning it did not copy everything.
Is there a way to tell rysnc to exclude the open files and let my script move forward after the rsync command?

Rsync command
```

rsync -avvrhu --log-file=logfile.txt --delete --partial /mnt/source/ /root/backup/destination/ > /dev/null

```

Sample error
```

2016/01/26 00:29:34 [6496] rsync: send_files failed to open "/mnt/source/file-open.QBW": Text file busy (26)
2016/01/26 00:29:35 [6496] rsync: send_files failed to open "/mnt/source/file-open.QBW.TLG": Text file busy (26)
2016/01/26 00:29:40 [6496] total: matches=0  hash_hits=0  false_alarms=0 data=0
2016/01/26 00:29:40 [6496] sent 343.05K bytes  received 38.25K bytes  26.30K bytes/sec
2016/01/26 00:29:40 [6496] total size is 17.40G  speedup is 45626.00
2016/01/26 00:29:40 [6496] rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1039) [sender=3.0.6]

```

---

