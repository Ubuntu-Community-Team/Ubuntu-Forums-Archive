---
title: "[SOLVED] How to point rsync to an id_rsa key"
date: 2007-11-15
forum: Server Platforms
---

### Post by victorbrca on 2007-11-15
Hi there,


  I want to use the "-i"  ssh option to point to an id_rsa key when backing up with rsync. Is there a way of doing this?

  I have 4 diferent id_rsa files that I use to connect to my different servers.

  The backup would eventually be added to crontab.


Thanks,

Vic.

---

### Post by jtc on 2007-11-15
You want to use the -e switch to specify a more detailed remote shell.

```

rsync -e "ssh -i /path/to/rsa_key" ...

```

---

### Post by MJN on 2007-11-15
<Post removed - JTC beat me to it! :)>

---

### Post by victorbrca on 2007-11-15
Thanks !!!  :)


Vic.

---

