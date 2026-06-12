---
title: "vsftpd fails for my user"
date: 2018-12-11
forum: Server Platforms
---

### Post by biterg on 2018-12-11
I cannot upload a file using SFTP using the user i setup, as it gives me a Server Error.
But, if i set my SFTP logon and password to the root user, files upload as expected.

I have set all CHOWN and CHMOD settings that I can find on the internet, but I still am unable to upload a file using my ftpuser that I setup.
root works OK, but ftpuser just results in a zero sized file with a server error message.

I could just use root, but that is just annoying to have to do it that way.

This is week two of trying this :-(

---

### Post by slickymaster on 2018-12-11
Support request

Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2018-12-12
I have documented the steps necessary to get [vsftpd working on Ubuntu Server 16.04](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=228).

Compare it with how you have yours setup and maybe you can find the problem.

My users are "rooted" into their own folder and do not have full access all over the server.  What they see is just what is in their folder.  The only "writable" folder is the "public" sub-folder in their account.

LHammonds

---

