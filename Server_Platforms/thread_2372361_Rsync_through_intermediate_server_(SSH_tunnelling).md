---
title: "Rsync through intermediate server (SSH tunnelling?)"
date: 2017-09-24
forum: Server Platforms
---

### Post by dudumomo on 2017-09-24
Hello,

I need to rsync a project (torproject) on my server (Stockage) but using an intermediary. (another server)

Without the intermediary, I simply need to run:
```
rsync -rt --delete rsync.torproject.org::amnesia-archive /media/Stockage/Mirrors/Tails
```

Now, with the intermediary, I'm facing difficulties.

I have created a ssh key and I can connect now from my Stockage server to the intermediary without issue, but now I want to run the Rsync command and it does not work.
I would like to do it in 1 command line, to use only when needed.

I've tried this:
```
rsync -rt --delete --progress -e "ssh user@intermediate.server ssh" rsync.torproject.org::amnesia-archive /media/Stockage/Mirrors/Tails
```

But I got:
```
ssh: connect to host rsync.torproject.org port 22: Connection refused
rsync: did not see server greeting
rsync error: error starting client-server protocol (code 5) at main.c(1666) [Receiver=3.1.2]
```

Obviously the syntax looks incorrect.

Any idea what it should be?

Thank you

---

