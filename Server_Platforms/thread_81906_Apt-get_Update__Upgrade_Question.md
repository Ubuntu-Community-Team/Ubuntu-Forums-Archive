---
title: "Apt-get Update / Upgrade Question"
date: 2005-10-25
forum: Server Platforms
---

### Post by Breaks on 2005-10-25
Well, when apt-get update & upgrading i got the following update information:

```

The following packages will be upgraded:
  gksu libcurl3 libgl1-mesa libgl1-mesa-dri libglu1-mesa libgphoto2-2 libgphoto2-port0 libnspr4 libnss3 libssl0.9.7 wget
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.1MB of archives.
After unpacking 3174kB disk space will be freed.

```

So indeed i said to continue, but then i got this warning:

```

WARNING: The following packages cannot be authenticated!
  gksu libgphoto2-port0 libgphoto2-2 libnspr4 libnss3 libgl1-mesa-dri libglu1-mesa libgl1-mesa

```

Just checking that these are fine and legit updates, so, are they lol?

Thanks in advance.

Breaks.

**:: Edit ::**

Ooook after doing this update im now getting this whenever i apt-get update:

```

W: GPG error: http://gb.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

I do the update command again and that error goes until every 5 times i run the update command... any ideas?

---

### Post by mlomker on 2005-10-25
There is a way to install the GPG key, but I just ignore it.

---

### Post by Breaks on 2005-10-26
Ahh so im definately not the only one getting this error then? well at least i know its not an issue my end :)... if its not that big a deal then ill just ignore it as you do. Thanks for your reply.

Breaks.

---

