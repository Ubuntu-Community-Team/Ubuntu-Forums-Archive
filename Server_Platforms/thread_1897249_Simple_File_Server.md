---
title: "Simple File Server"
date: 2011-12-18
forum: Server Platforms
---

### Post by nunkstop on 2011-12-18
Hi everdybody, my teacher want me create simple file-server serve for mini-lab in my school, server is running under Ubuntu-server and client access to server in Window, and file-server has some functionality as upload, download file to folder in file-server.

Detail : there's one folder for all user uploading file to that folder, but there's some restrict if user A is not owner of file , so that user not allow to view or download that file, just owner has that privilege.

Example : 

+user A upload file f-A into folder F
+user B upload file f-B into folder F

so user A not allow to view or download f-B and so on...

Because i'm new in Ubuntu platform, so i use simple solution i knew : 

In ubuntu server, i created folder F and shared it in network as i shared folder in Window platform. I also created group S to and added all user to group .I set privilege for group 

But it dont work. I cant access shared-folder when i use Explorer Network in Window to access.

Anyone could help me solve this problem? Or can suggest some idea to implement this? I just need some simple solution not difficult.

Thanks for helping! :)

---

