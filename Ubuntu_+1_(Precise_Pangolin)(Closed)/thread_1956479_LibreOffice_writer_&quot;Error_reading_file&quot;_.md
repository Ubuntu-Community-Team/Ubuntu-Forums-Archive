---
title: "LibreOffice writer: &quot;Error reading file&quot; when password-protected"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bovender on 2012-04-11
In the current Precise Beta 2, I cannot open password-protected .odt files with LibreOffice writer. After entering the password, LibreOffice complains: "Read-Error. Error reading file."

When I boot my system from an old Ubuntu 11.04 USB stick, I can perfectly open the file from my harddisk, so it's not that the file is corrupt or I forgot the password or anything.

'dpkg -s libreoffice-writer' gives:

```
1:3.5.2-2ubuntu1
```

---

### Post by Elfy on 2012-04-11
Looks like this bug [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/919659](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/919659)

---

### Post by bovender on 2012-04-11
I don't think so. It's a different error message. Plus, I can save and open newly created files with password protection just fine. In the bug report, people were able to open their files with root privileges. In my case, the problem persists even when using 'sudo libreoffice'.

---

### Post by Elfy on 2012-04-11
File a new one if you think it's different.

---

### Post by bovender on 2012-04-11
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/978680](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/978680)

---

