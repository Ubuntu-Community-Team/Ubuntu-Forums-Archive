---
title: "Snort installation"
date: 2010-09-02
forum: Security
---

### Post by PHANTOM X on 2010-09-02
I need some help installing Snort. I tried the sticky, but it wasn't overly helpful. Got pdf off here
[http://www.symmetrixtech.com/download.html](http://www.symmetrixtech.com/download.html)

Having trouble using tar command to extract the files. I get the following errors.

```
sudo tar zxvf jpgraph-1.27.1.tar.gz
tar: jpgraph-1.27.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
```The file is under desktop. I installed Ubuntu Server 64 bit and installed all features(dns server, mail server, presql, virtual machine hosts ect)and did all updates and installed Ubuntu Desktop. I also have the snort.gz archive downloaded.

---

### Post by cariboo on 2010-09-02
Why not just double click the file, and let file roller extract it?

---

### Post by PHANTOM X on 2010-09-02
I guess I could do that, but I'm not sure where each files go.

Edit: NVM. I didn't realize I could double click and extract to the created folder. Still learning.:p

---

### Post by uRock on 2010-09-02
sudo apt-get install snort will get it installed, unless you are trying for a newer or customized version.

---

### Post by PHANTOM X on 2010-09-02
By using the apt-get will it install the rules?

---

### Post by uRock on 2010-09-02
Yes, when you install the repo version it installs a huge set of rules.

---

### Post by PHANTOM X on 2010-09-02
Cool. Thanks.:)

---

