---
title: "Virtul users permision for created folders"
date: 2011-05-28
forum: Server Platforms
---

### Post by alfamuzjak on 2011-05-28
hi,
I have problem with virtual users in vsftpd...When they create folder they cant make another in than folder, or for example they cant see files they upload in that directory...That write permision i try to change in their config file, with every combination of local_umask and file_open mode values..

Can anyone tell me how can i handle that...I want that virtual user who creates directory (in their root directory) have all privilages to thot folder and all content in that folder. Cant someone tell me how to do that?

---

### Post by alfamuzjak on 2011-05-29
DO ANYONE HAVE ANY IDEA? pls help me

---

### Post by alfamuzjak on 2011-05-29
Any suggestions?!

---

### Post by ruffEdgz on 2011-05-30
Well, what are the values for your local_umask and file_open options? When a user logs into the vsftpd server and makes that new directory successfully, does the configuration settings you placed for vsftpd get set for that new directory?

If you could also go through the steps a person does using your vsftpd and the end result of the uploaded file/directory in this post, that might help in the problem. Also, does vsftpd have any logs in /var/logs/ that you can share?

Thanks.

---

### Post by Lars Noodén on 2011-05-30
> **alfamuzjak said:**
> Any suggestions?!

Well, my standard suggestion in this would be to consider using SFTP instead of FTP.  It's a lot more secure and far easier to configure.  Most basic activities can be done without any modification to the configuration file at all.  SFTP is part of the package [OpenSSH-server](http://packages.ubuntu.com/natty/openssh-server).

That won't solve the FTP problem per se, but it would solve the problem of allowing secure uploads.

---

