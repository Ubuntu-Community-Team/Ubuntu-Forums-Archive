---
title: "Proftpd and Winscp"
date: 2017-05-18
forum: Server Platforms
---

### Post by YaPaY on 2017-05-18
Dear all,

I configured my ftp to access every user to access spesific directories. It works under FTP protocols but &#304;f I connect via Winscp and set the conneciton type as SFTP or SCP I can access every location in server. How can I prevent this or disable the user accaount for those protokols (SCP, SFTP)

---

### Post by howefield on 2017-05-18
Support thread, so moved to the "*Server Platforms*" forum.

---

### Post by SeijiSensei on 2017-05-18
SCP uses SSH to connect, not the FTP protocol. You need to put users in "chroot jails" using the tools that come with openssh-server.

Just because people can see outside their home directories doesn't mean they can write to them.  If you're merely concerned that users not be able to browse other users' files, change the directories to have 700 permissions:
```
cd /home
sudo chmod 700 *
```

---

### Post by YaPaY on 2017-05-25
@SeijiSensei,

Thanks a lot for the solution

---

