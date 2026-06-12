---
title: "Allow user to only access /home/user"
date: 2010-09-06
forum: Server Platforms
---

### Post by metallicamaster3 on 2010-09-06
I am renting out space on my server and I want them to not be able to read or write to anything but their /home/user folder. How can I accomplish this? At the moment I chmod'd my own /home/mm3 folder to 0700 so that only I and can list its contents. Is this suffice?

I guess what I'm trying to accomplish is to allow myself and root to still be able to access /etc, /var, /home, but not allow any other users to do so. 

Thanks in advance!

---

### Post by 0004tom on 2010-09-06
If your planning on doing it with FTP, most ftp servers/daemonds allow for chrooting "jail" using.

---

### Post by metallicamaster3 on 2010-09-06
Not FTP, SFTP (SSH).

---

