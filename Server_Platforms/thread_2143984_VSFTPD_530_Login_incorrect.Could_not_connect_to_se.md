---
title: "VSFTPD: 530 Login incorrect.Could not connect to server"
date: 2013-05-10
forum: Server Platforms
---

### Post by maykino on 2013-05-10
Hello, everyone. I have a problem with accessing my server via ftp. It worked before but I couldn't modify any content so I started messing up with different chmod of my folder and suddenly it stopped working. Current owner of the folder is ftp and write_enable=YES and local_enable=YES are both set in the config file. I'm kind of new to this kind of setup so I apologize if I'm doing something stupid. What might be wrong?

---

### Post by d4m1r on 2013-05-13
Have you thought of uninstalling your FTP service, removing all related files, and reinstalling it so it gets the default permissions? If you edited them manually and don't know what they originally were, it's gonna be hard to fix...

---

