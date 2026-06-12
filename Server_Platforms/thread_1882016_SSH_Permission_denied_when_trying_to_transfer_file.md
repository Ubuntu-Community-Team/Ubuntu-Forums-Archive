---
title: "SSH Permission denied when trying to transfer files"
date: 2011-11-16
forum: Server Platforms
---

### Post by ScottG89 on 2011-11-16
Hey guys I recently setup a web server and I have ssh on it also so I can work on one computer and transfer the files over to the server. I downloaded gftp and tried transferring the files that way, but it does not work. It connects to the server no problem, but I cannot transfer the files. I also tried scp in terminal but I get a permission denied also. Do I have to configure something to allow file transfer?

Thank you,
Scott

---

### Post by Lars Noodén on 2011-11-16
You have to have write access to the directory that you are uploading to.  Is that all set?

---

### Post by ScottG89 on 2011-11-16
No I didn't set anything. I just did apt-get install openssh-server. How can I set that?

Thank you

---

### Post by ScottG89 on 2011-11-18
do I just have to do chmod -r 744 /var/www? or is there something in the sshconfig file?

---

### Post by Lars Noodén on 2011-11-19
> **ScottG89 said:**
> do I just have to do chmod -r 744 /var/www? or is there something in the sshconfig file?

If you're not sharing /var/www with any other users, then you only need to worry about access for yourself.

```

sudo chgrp -R scottg89 /var/www
sudo find /var/www -type d -exec chmod g=rwxs {} \;
sudo find /var/www -type f -exec chmod g=rws  {} \; 

```

If you are sharing access among several users, then make them members of a group and substitute that group for 'scottg89' above.

---

