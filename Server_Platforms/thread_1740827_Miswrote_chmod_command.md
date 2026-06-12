---
title: "Miswrote chmod command"
date: 2011-04-27
forum: Server Platforms
---

### Post by nagisa on 2011-04-27
Well, I have made myself bigest problem, I could have, and so, I seek for your help.

Command that I made:
```
chmod -R 777 /*
```
Insted I wanted to do:
```
chmod -R 777 *
```

As you already figured out, I chmoded my whole system. There is one thing I want to do:
Get my files out of there.
And there's where new problem arises:
ssh_exchange_identification: Connection closed by remote host

I always used sftp for ftp service, so I don't have another service for file managing. Is there any way to get my files back?

---

### Post by arrrghhh on 2011-04-27
You can try to restore permissions one-by-one, but it won't be easy.

Honestly it would be best to backup any critical data that can't be easily recreated (config files, documents, etc) and wipe the server and start over, take it as a lesson learned.

Like I said you can try to restore all the permissions, but you'll spend a week doing so and still might not get it all correct.

---

### Post by Buntumatic on 2011-04-27
SSH finds insecure permissions on its config files and does not work.

I take this is a remote computer? It's time to drive there, or call a local tech.

---

