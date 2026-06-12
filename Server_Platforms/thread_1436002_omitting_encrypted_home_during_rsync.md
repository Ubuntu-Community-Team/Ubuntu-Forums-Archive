---
title: "omitting encrypted /home during rsync"
date: 2010-03-22
forum: Server Platforms
---

### Post by finite9 on 2010-03-22
I setup an encrypted $HOME dring installation of Ubuntu 9.10, and I want to do rsyncs of my entire $HOME to my server, but when I do this with

```
rsync -rt /home/andrew server:/home/andrew
```

Then it copies the contents of the encrypted folder as well in some way that im not really sure of, which means that I get a double copy of my $HOME unencrypted and also the encrypted contents.

I dont know how to identify what the folder is or how I can omit it?  I guess it's ecryptfs.  Can someone point me in the right direction?

At the moment i'm just rsyncing specific folders from within my $HOME, but I want to do the whole /home folder.

---

### Post by KB1JWQ on 2010-03-23
Not sure where the folder itself is, but once you find it you can --exclude 'PATTERN' easily enough.  For bonus points,  --exclude-from=FILE.

---

### Post by oldmankit on 2010-05-02
Do you want to send the encrypted or the unencrypted contents?

I think that the encrypted contents are at /home/.ecryptfs/<username> and these are mounting in an unencrypted form in /home/<username>.

Is that how it works on your system?

Edit: I notice from your command that  I must be wrong, as it would not include /home/.ecryptfs/andrew
rsync -rt /home/andrew server:/home/andrew

---

