---
title: "Deleted /etc/samba.. how to re install"
date: 2009-06-08
forum: Server Platforms
---

### Post by spinanicky on 2009-06-08
Hi, 

I thought I could delete /etc/samba and then simply reinstall it to "reset" all the configs but sudo apt-get install samba does not reinstall the files/folder :lolflag:

Advice on how to get them back would be great!

Cheers

---

### Post by capscrew on 2009-06-08
> **spinanicky said:**
> Hi, 

I thought I could delete /etc/samba and then simply reinstall it to "reset" all the configs but sudo apt-get install samba does not reinstall the files/folder :lolflag:

Advice on how to get them back would be great!

Cheers

I would purge samba.  Like this:```
sudo apt-get purge samba
```

Then reinstall: ```
sudo apt-get install samba
```

If you created your shares via Nautilus (GUI) the sahres are at /var/lib/samba.

---

### Post by cariboo on 2009-06-08
You should be able to find the samba package in /var/cache/apt/archives. I use mc to open .deb's and just copy the /ect/samba directory to the correct place. MC is in the repositories, and you can run it as root to copy files to directories your user doesn't have permissions for.

---

