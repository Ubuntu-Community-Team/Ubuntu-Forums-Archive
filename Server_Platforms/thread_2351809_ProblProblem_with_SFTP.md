---
title: "ProblProblem with SFTP"
date: 2017-02-07
forum: Server Platforms
---

### Post by lochness123 on 2017-02-07
In attachment is the screen of my problem. Can you help help me please?

---

### Post by &amp;KyT$0P# on 2017-02-07
1) Do you have the [FONT=Courier New]openssh-server[/FONT] package installed?

2) Why are you running [FONT=Courier New]sftp[/FONT] as root?

---

### Post by wildmanne39 on 2017-02-07
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-02-07
To check if openssh-server is installed and running try:
```
sudo netstat -plunt | grep 22
```

I am using sudo because I assume you will be running commands with your admin user, not as root. And don't forget that by default in ubuntu ssh as root is disabled so that might be why sftp reports an error when you are trying to run it as root.

You should use your admin user, not root.

---

### Post by lochness123 on 2017-02-07
Openssh server is installed and running. What I would do if I want run sftp in root user?

---

### Post by darkod on 2017-02-07
Connect with your admin user (or any enabled sftp user) and upload what you want to upload to its home folder or another allowed folder, depending on your setup.

Then use ssh session with your admin user and from inside the server you can copy the file you uploaded to the destination where you want it.

In my opinion that's the best way. sftp or ftp are not designed to open the whole server for you, they are just to upload/download files. Then the administrators should move the files around. Otherwise if someone breaks in they would also have full access to the whole server, etc... And especially allowing ssh or sftp for root is not recommended.

---

### Post by lochness123 on 2017-02-07
Thank you

---

