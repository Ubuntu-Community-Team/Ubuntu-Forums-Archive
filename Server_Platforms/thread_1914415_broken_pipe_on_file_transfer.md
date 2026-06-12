---
title: "broken pipe on file transfer"
date: 2012-01-24
forum: Server Platforms
---

### Post by Anime4Me on 2012-01-24
I transfered a 640 MB file.tar.gz from a remote server to my local computer using sftp.  Terminal output showed that 100% of the file was transferred but also threw a broken pipe error.  The file exists on my computer but I get "an error occurred while loading the archive", so clearly the transfer wasn't successful.

How do I find out what caused the broken pipe error? How do I fix it?

---

### Post by rubylaser on 2012-01-24
I would just rsync the the file from the remote computer to your local computer, something like this.

```
rsync -avz root@remote_ip:/path/to/file/file.tar.gz /path/on/local/machine/file.tar.gz
```

If you want to be super thorough, you could md5sum the files on each side to ensure they're identical.

```
md5sum file.tar.gz
```

The pipe error may be in your logfiles, but I would guess the connection had a hiccup and rsyncing them will fix your problem.

---

