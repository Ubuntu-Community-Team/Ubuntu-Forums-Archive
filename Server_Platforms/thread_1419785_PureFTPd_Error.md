---
title: "PureFTPd Error"
date: 2010-03-02
forum: Server Platforms
---

### Post by pwn on 2010-03-02
When I try to login to pure-ftpd, it says "Sorry, but I cannot trust you". I read the FAQ from [http://download.pureftpd.org/pub/pure-ftpd/doc/FAQ](http://download.pureftpd.org/pub/pure-ftpd/doc/FAQ) and a few threads on this forum but they don't work for me.

I'm not sure how to fix this.

I'm trying to setup virtual users. My uid id is 1006 and gid is 1007 on this system is 

So I created a virtual user and ran the ftpd like below:

pure-pw useradd pwn -d /home/pwn/FTP -u 1006 -g 1007
pure-pw mkdb
pure-ftpd -S 1337 -c 5 -l puredb:/home/pwn/etc/pureftpd.pdb

I also tried adding a virtual user who doesn't have a shell on the system, and I get the same error.

---

### Post by pwn on 2010-03-02
I got it to work.

I recompiled it with --with-nonroot and it accepts my virtual users now. :)

---

### Post by FuturePilot on 2010-03-02
Usually this is because of MinUID. Adjusting /etc/pure-ftp/conf/MinUID and restarting pureftp should work. [http://ubuntuforums.org/showpost.php?p=7375383&postcount=2]("http://ubuntuforums.org/showpost.php?p=7375383&postcount=2")

---

### Post by pwn on 2010-03-04
I don't have root access on the server, so --with-nonroot did the trick for me.

---

