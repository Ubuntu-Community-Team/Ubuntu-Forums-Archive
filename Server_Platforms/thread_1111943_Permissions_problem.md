---
title: "Permissions problem?"
date: 2009-03-31
forum: Server Platforms
---

### Post by pitris2009 on 2009-03-31
Hi, 

I've developed a php application which among other things allows the users to upload a file. The whole thing is running in an Ubuntu system, of course.

The application runs fine when accessed from the same machine where the apache server is located. But when I try to upload a file from another machine in the same LAN, the application is unable to move the file from the temp directory into its final location. 

It looks like a permissions problem but I don't understand why does it work when accessed locally. Does apache use a different users when the pages are requested locally? 
Do I need to set any special permissions to the directory where the files should be written?

Thanks in advance, 
Pedro

---

