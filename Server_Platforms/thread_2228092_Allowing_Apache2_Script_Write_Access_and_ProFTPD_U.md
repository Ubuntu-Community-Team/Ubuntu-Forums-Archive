---
title: "Allowing Apache2 Script Write Access and ProFTPD User Write Access On Same Folder"
date: 2014-06-05
forum: Server Platforms
---

### Post by Robin_Wilson on 2014-06-05
Hello

I want to be able to set up multiple websites so that scripts on the websites can upload files (i.e. PHP file upload scripts) but I also want the users to be able to upload files via FTP.

The folder structure is as follows:
/home/website1/public_html
/home/website2/public_html

Users are:
user1
user2

The only way I seem to be able to get this to work is to do the following
[LIST]
[*]Set the owner of public_html and everything below to www-data
[*]Chmod the public_html folder to 777
[/LIST]

Once this is done users can still connect via ftp and upload.
Is this rather insecure though?

I have tried adding user1 and user2 to the www-data group but it makes no difference and the only way I can get it to work is to set the owner to www-data and chmod the folder to 777.

Thanks
Robin

---

