---
title: "Copy and encrypt local files to mounted network share"
date: 2014-06-02
forum: Server Platforms
---

### Post by jackbrennan2008 on 2014-06-02
Hello,

I've been struggling getting this to work so i thought I'd throw this out here.

I have a network share mounted on my Ubuntu server. I'd like to copy the contents of my scripts folder from a local folder on the server to the mounted network share. The problem is that i want the files to be encrypted with GPG before they are written to the shared folder. 

I can't seem to get the GPG part to work.

As an example, I've tried:

```
find /home/user/Scripts/ -name "*" -exec cp {} /mnt/share | gpg --yes --batch --passphrase=1234 -c {} \;
```

But it's so messy and doesn't work :P.

So I'm hoping someone here might have a solution

Thanks.

---

