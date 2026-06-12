---
title: "&quot;Bad header line&quot;???"
date: 2005-04-16
forum: Repositories &amp; Backports
---

### Post by danj205 on 2005-04-16
What does this message mean?

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/b/beep-media-player/beep-media-player_0.9.7-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/beep-media-player/beep-media-player_0.9.7-1ubuntu1_i386.deb)  Bad header line [IP: 82.211.81.138 80]

I'm guessing it is on the server side, but I've been getting this problem since I installed Hoary (which was a few days after it's release). I originally used the localised servers (nz.archive.ubuntu.com) but tried the base ones to see if that made any difference.

Funny thing is, wget is happily downloading that package as we speak.

I also get this when downloading the perl dependencies for mysql-server.

Can anyone offer any help?

---

### Post by dataw0lf on 2005-04-19
Are you using a proxy ?

I'm a bit curious though.  Try a:

```
sudo apt-get -o Acquire::http::Pipeline-Depth=0 update 
```

for kicks.

---

