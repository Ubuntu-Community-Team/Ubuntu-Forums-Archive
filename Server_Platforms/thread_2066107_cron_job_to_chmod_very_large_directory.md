---
title: "cron job to chmod very large directory"
date: 2012-10-03
forum: Server Platforms
---

### Post by jamesa00789 on 2012-10-03
I have a problem, I need a cronjob to chmod a very large directory (with about 20,000 directories which sums up to about 20GB).

I'd would be nice to set the permissions for all files in the directories in real-time, but currently this is not possible.

I'm setting a cron job as:

```
# chmod all directories
ionice -c3 nice -n19 find /home/user/directory/ -type d -print0 | xargs -0 chmod 0777

# chmod all files
ionice -c3 nice -n19 find /home/user/directory/ -type f -print0 | xargs -0 chmod 0777
```

However this still consumed very large amounts of resources even with ionice and nice.

Does anyone have any suggestions?

---

### Post by markbl on 2012-10-03
The "solution" you are proposing here for whatever problem you are trying to fix smells bad.

However, without going into that, at least read the chmod man page and note the "-R" option. You don't need those two find commands.

While you are at it, read about "umask" in bash or whatever shell you are using to maybe better fix this problem.

---

### Post by Lars Noodén on 2012-10-04
Can you say a little more about why you are trying to do this or what you are trying to do?  The find solution does seem a little inelegant and there's probably a better way if we had more info.

---

