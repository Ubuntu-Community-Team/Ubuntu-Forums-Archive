---
title: "Server issue - uploaded file permissions in vbulletin"
date: 2010-02-25
forum: Server Platforms
---

### Post by LudachrisGSX on 2010-02-25
I'm having an issue with file uploads through our vbulletin script - specifically avatars. We have our vbulletin installation setup to allow custom avatar uploads. Recently, we moved the avatars to the file system and started having trouble with file permissions. It appears all new avatar file permissions are being uploaded with chmod 600. Since vbulletin doesn't specify permissions for these files, I've been told that it's a server setting I need to check. 

I've made sure the upload_tmp_dir  is set to "/tmp" and that it's writable. I've also been told to check the $uploaded_file setting but not sure where that is or if it will fix the issue. Any other ideas I should look into?  

We're using MySQL version 5.0.51a-3ubuntu5.4-log, PHP version 5.2.4-2ubuntu5.6, and Apache version Apache v2.2.8 (cgi-fcgi), if that helps.

---

