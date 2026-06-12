---
title: "How to enter /var/log/apache2 with SFTP"
date: 2017-02-22
forum: Server Platforms
---

### Post by sdhweb on 2017-02-22
Hello,

I have some trouble with disk space because the apache2 logs grow large. I'm then thinking to connect to /var/log/apache2 with a FTP-client using SFTP to download the existing files (as a backup). Then I'd like to truncate the content of the files. The problem is that I can't access that directory due to permissions. Using putty I can just do a sudo su - to enter /var/log/apache2 but that doesn't work with a FTP-client.

How can I solve this?

Is there any way to enable some kind of automatic log rotate on the logs files inside /var/log/apache2 ?

I'm using Ubuntu 12.04.5 LTS with no GUI.

---

### Post by howefield on 2017-02-22
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by darkod on 2017-02-22
You are on the right path. Check out the logrotate man/instructions/tutorials on the internet. You can rotate almost all logs, and surely you can do it for apache. Including compressing the older logs which will additionally save you space.

I would forget about the SFTP for the moment and concentrate on logrotate.

---

### Post by sdhweb on 2017-02-23
> **darkod said:**
> You are on the right path. Check out the logrotate man/instructions/tutorials on the internet. You can rotate almost all logs, and surely you can do it for apache. Including compressing the older logs which will additionally save you space.

I would forget about the SFTP for the moment and concentrate on logrotate.

OK, I will look into logrotate, thanks.

---

### Post by Habitual on 2017-02-23
Filezilla over sftp protocol.
Right click the file and select Edit and up pops kate, or gedit, or ....
Highlight all, hit delete, Ctrl+S saves it and should send it back to the server, empty

The usual method interactively:
```
sudo su -
> /var/log/apache2/{access,error}.log
sudo -k

```

---

