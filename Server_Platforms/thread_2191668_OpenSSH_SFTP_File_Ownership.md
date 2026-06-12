---
title: "OpenSSH SFTP File Ownership"
date: 2013-12-03
forum: Server Platforms
---

### Post by mastermindg on 2013-12-03
I have SFTP setup using internal-sftp on OpenSSH. I'm chrooting into /var/www as a generic user. New files are created as the user. I'd like new files to be created as www-data for simplicity and security. How can I set this up so that new files are created with www-data?

---

### Post by Lars Noodén on 2013-12-04
The www-data user exists to provide privilege separation for the web server.  It provides an unprivileged user.  Making the files owned by www-data would give write access to that user and, as far as the file system goes, would eliminate the separation.  So having files owned by www-data in that context would actually greatly decrease security.

What are you trying to do?  There's probably a safe way to do it.

---

### Post by mastermindg on 2013-12-05
I'm not sure what your point is. My understanding is that Apache runs under www-data (by default) and for proper functioning of a web server all files/directories that need to be accessed should be owned by www-data. This is what I want to accomplish here. My setup is pretty typical: An SFTP setup to manage my web directories. The SFTP user is generic (not www-data). I want files/directories that are created under SFTP to be owned by www-data.

---

### Post by Lars Noodén on 2013-12-05
The point is that www-data should not have write access to any of the files that the web server will be serving.  For the web server to be able to publish your files, it is only necessary to have read access.  That would be o=r for the files and o=rx for the directories.  If the files or directories are owned by www-data, then the web server has write access to them, taking away one layer of security.  This is especially important protection if you are using PHP or Perl's HTML::Mason.  The principle of least privilege is involved as is a variant of write XOR execute.

What difficulty is being caused by the files and directories being owned by your generic SFTP user?  As long as the web server can read the files, they should be published just fine.

---

### Post by mastermindg on 2013-12-05
I'm running LAMP, and coding in PHP. There are some occasions where PHP needs to read and write to files. However I do see your point regarding permissions.

---

### Post by Lars Noodén on 2013-12-06
If you are just reading / writing data files using PHP, they can be stored outside of /var/www (or whatever you have for document root) and that would avoid the problem since the web server wouldn't be able to see them then.

---

