---
title: "Is youtube-dl safe?"
date: 2012-10-01
forum: Security
---

### Post by Stonecold1995 on 2012-10-01
I have a program installed called youtube-dl, and it's a python script.  It requires root privileges to update itself, but the code itself is obfuscated.  The first two lines of the file are like this when opened with vi:
```
#!/usr/bin/env python
PK^C^D^T^@^@^@^H^@Ú<9c><Av²9ûã^]^@^@ù_^@^@^Q^@^\^@FileDownloader.pyUT   ^@^C«àeP<97>
```

I don't really trust running something like this as root if I don't know the source (I'm not too good at writing Python but I can read it well enough to tell if it's malicious).  If it's legal to do so, is there any way I can reverse the obfuscated code, or is this just compiled for speed (.pyc or something)?

So does anyone know of youtube-dl is safe to use?  I downloaded it with apt-get, but I'd still like to make sure.

---

### Post by rookcifer on 2012-10-01
Probably a byte-code file (.pyc as you said).  If it is from the repos it is doubtful it is malicious, though.  If you're interested in reading the source, it is on [Github.]("https://github.com/rg3/youtube-dl/")

---

### Post by Stonecold1995 on 2012-10-02
> **rookcifer said:**
> Probably a byte-code file (.pyc as you said).  If it is from the repos it is doubtful it is malicious, though.  If you're interested in reading the source, it is on [Github.]("https://github.com/rg3/youtube-dl/")

Thank you!

---

