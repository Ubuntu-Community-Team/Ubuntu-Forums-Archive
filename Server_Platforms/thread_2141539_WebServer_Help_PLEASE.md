---
title: "WebServer Help PLEASE"
date: 2013-05-02
forum: Server Platforms
---

### Post by TechWreck on 2013-05-02
I am making a WebServer with Apache and I don't really know how to take my html files from my PC through DreamWeaver and my other files for my webpage to put on my Ubuntu Server. How do i go about putting the files in the WebServer Hard Drive. I am also wondering how to make it so that people don't have to delete their cache to see what is new.

---

### Post by CharlesA on 2013-05-03
Mash F5? You should only need to mess with the cache if you are serving php files and I'm not sure if you can adjust the time those are cached.

Why not just use sftp to transfer the files? Dreamweaver supports it and you should have SSH installed if you are working on a server.

---

### Post by brent1975 on 2013-05-03
To copy files to your server you have a few options. The most common is to use SSH through filezilla. Its actually sftp. Connect using the IP with port 22 if you haven't changed the ssh port. As far as Dreamweaver goes unless there is settings to connect to a server to copy the files in the program you will have to .manually do it.   I personally run samba and share my site directory so I can map the drive in either in Linux or windows and can drag and drop my files.

---

### Post by SeijiSensei on 2013-05-04
You can disable caching with the Apache "headers" command.  You send a bunch of HTTP header commands to the browser telling it not to cache the content.  For an example, see [http://stackoverflow.com/questions/11532636/prevent-http-file-caching-in-apache-httpd-mamp](http://stackoverflow.com/questions/11532636/prevent-http-file-caching-in-apache-httpd-mamp).

If you are running PHP applications, you can set the headers there instead like this:
```

header("Expires: -1");               
header("Cache-Control: no-cache");               
header("Cache-Control: must-revalidate");               
header("Pragma: no-cache");               

```

There are a variety of these to handler both current and older browsers that conform to earlier standards.

These commands must be executed before any content is sent to the browser or PHP will throw an error.  Also make sure there is no leading or trailing whitespace in the file containing these commands.

---

