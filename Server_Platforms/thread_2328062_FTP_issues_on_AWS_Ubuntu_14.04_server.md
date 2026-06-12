---
title: "FTP issues on AWS Ubuntu 14.04 server"
date: 2016-06-17
forum: Server Platforms
---

### Post by bevan2 on 2016-06-17
Hello,
I have a 14.04 running ISPConfig in an AWS server. All works well until I try and install a wordpress site. The install itself went fine, but changing themes brought up an error : cannot create directory.

So, I thought I'd FTP it up. Connects ok, navigates to folder ok, but will not upload anything, saying 553: Can't open that file: Permission Demied.

I tried to create a directory - same response. 

The FTP user is in ISPConfig
The FTP user can log in
The FTP User cannot ad or modify files.

I went to ssh and added the ftp user as a ubuntu user. That didn't work either.

Now what?

---

