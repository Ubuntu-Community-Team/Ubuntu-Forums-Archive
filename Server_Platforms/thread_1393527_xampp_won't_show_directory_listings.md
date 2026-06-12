---
title: "xampp won't show directory listings"
date: 2010-01-29
forum: Server Platforms
---

### Post by RPMurph on 2010-01-29
Fresh install of ubuntu server 9.10 with all updates done and xampp 1.7.3a.

I want to see directory listings when no index.* file is present, but currently it gives "Access Forbidden!" under those circumstances.

In /opt/lampp/etc/httpd.conf I've tried
```
Options Indexes FollowSymLinks ExecCGI Includes
Options +Indexes FollowSymLinks ExecCGI Includes
Options All
Options +All
```

/opt/lampp/logs/error_log gives me
```
[error] [client 127.0.0.1] Directory index forbidden by Options directive: /home/murphy/www/images/
```

there are no .htaccess files in any of the folders I'm trying to access.

I thought maybe I'm editing the wrong httdp.conf file, but I changed the DirectoryIndex, and it worked.

Its seems I'm really missing something here...... Thank You for your help!

---

