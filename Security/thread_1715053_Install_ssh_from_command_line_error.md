---
title: "Install ssh from command line error"
date: 2011-03-26
forum: Security
---

### Post by khcam on 2011-03-26
Hi all,

I am not familiar with Linix server, I have installed ubuntu server for study purpose.

Now I am facing problem when I install openssl from command line. This is the error message:

openssh-server : Depends: libwrap0 (>=7.6-4~) but it is not installable
E: Broken packages

I don't know how to fix this....

Thanks,

---

### Post by Cheesehead on 2011-03-26
```
sudo apt-get -f install openssh-server      # -f is the 'fix broken' flag 
```

---

