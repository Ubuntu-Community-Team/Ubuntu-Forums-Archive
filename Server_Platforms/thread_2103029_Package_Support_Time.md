---
title: "Package Support Time"
date: 2013-01-09
forum: Server Platforms
---

### Post by PierreRobiquet on 2013-01-09
Hello,

I'm currently running Ubuntu 12.04 on my home server, however I'm trying to fin the command that will tell me how long each package will be supported for. I remember seeing it before and it said "X Y Z packages will be supported until 2014" and "A B C packages will be supported until 2013".

Does anyone know the command I'm referring too?

Thanks,

---

### Post by savvdm on 2013-06-25
I think you may use something like 

$ apt-cache show linux-image-generic | grep ^Supported
Supported: 5y

Took from here: [http://askubuntu.com/a/237087](http://askubuntu.com/a/237087)

---

### Post by snowpine on 2013-06-25
April 2017 according to the Ubuntu wiki.

---

### Post by Lars Noodén on 2013-06-25
You might be looking for something like ubuntu-support-status

```

ubuntu-support-status --show-all | less

```

---

### Post by gordintoronto on 2013-06-25
ubuntu-support-status did not help in Ubuntu 13.04. It said I had 132 unsupported packages, including cheese and gdebi -- and gave no hint about how long Ubuntu 13.04 would be supported.

---

