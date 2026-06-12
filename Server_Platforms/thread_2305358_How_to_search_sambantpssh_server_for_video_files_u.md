---
title: "How to search samba/ntp/ssh server for video files using Web interface?"
date: 2015-12-05
forum: Server Platforms
---

### Post by rado2 on 2015-12-05
Hi I have samba/ftp/scp...server with audio, video files. I am looking for some web interface to search this files on intranet. Is that possible? can you recommend somethng?

---

### Post by matt_symes on 2015-12-05
I have moved your thread to **Server Platforms**.

This is be a better area to get a response to your query.

---

### Post by matt_symes on 2015-12-05
Hi

> **rado2 said:**
> Hi I have samba/ftp/scp...server with audio, video files. I am looking for some web interface to search this files on intranet. Is that possible? can you recommend somethng?

Can you supply more information such as what you want to do with the files when you have found them ?

Can you give details of your use case.

That may help you get better suggestions.

Kind regards

---

### Post by SeijiSensei on 2015-12-05
If all the files are in the same directory, or a directory and its subdirectories, you could just install the Apache web server and point the DocumentRoot to the top directory where the files are stored.  You'll need to enable indexes, but if you do, you'll get a list of the files and directories if you point a web browser at the server.

In /etc/apache2/sites-available/000-default.conf you would make these changes:

Change the DocumentRoot
```
DocumentRoot    /path/to/the/media/directory
```

Enable indexes
```

<VirtualHost *:80>
[stuff]
DocumentRoot /path/to/the media/directory
<Directory "/path/to/the/media/directory">
Options +Indexes
</Directory>
[stuff]
</VirtualHost>

```

The media directory should have world-readable privileges.

---

