---
title: "pure-ftpd, mysql and directory sharing."
date: 2008-01-27
forum: Server Platforms
---

### Post by Thorning on 2008-01-27
Hello.
My question is not about pure-ftp installment, nor mysql installation/setup.
I have a working FTP with pure-ftpd and a mysql user database, working nicely. I can login and list whatever is in the home-dir for that user (which is created automaticly with proper ownership).
It's all very nice.

Question is:
If I want to share folders outside the home directory (which is the users root btw), for example folders of of my external hard drive, how do I do this?
I figured at first that I probably just had to make a symbolic link of that directory in the home-dir.
But this doesn't seem to work, even if I chmod the properties and/or ownership of the destination folder.

Example:

/home/blablahome/ln -s /blablastorage/Mp3 Mp3

I can then of course list my Mp3-folder through that link.

But when I try to access that dir from the ftp client:
Command:	CWD /Mp3/
Response:	550 Can't change directory to /Mp3/: No such file or directory
Error:	Failed to retrieve directory listing

---

