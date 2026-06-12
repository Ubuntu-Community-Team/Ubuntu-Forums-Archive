---
title: "vsftpd problems"
date: 2010-01-30
forum: Server Platforms
---

### Post by antitalented on 2010-01-30
Hello,

I am trying to set up a file server on Ubuntu. This is the structure I have. All directories have 755 permissions.

[B]user@localhost:/tmp/ftp-root$ ls -R

backup  download  upload

./backup:

./download:
a.txt b.txt

./upload:[/B]

I can download from the server with wget (wget [ftp://localhost/download/a.txt](ftp://localhost/download/a.txt)) but cannot upload using wput.

[B]user@localhost:~$ wput -v ./yyy [ftp://localhost/upload/](ftp://localhost/upload/)
--16:32:21-- `yyy'
    => [ftp://anonymous:xxxxx@127.0.0.1:21/upload/yyy](ftp://anonymous:xxxxx@127.0.0.1:21/upload/yyy)
Connecting to 127.0.0.1:21... connected! 
==> AUTH TLS ... failed (Please login with USER and PASS.).

Logging in as anonymous ... Logged in!
==> CWD upload
==> SIZE yyy ... failed.
==> TYPE I ... done.
==> PASV ... done.
==> STOR yyy ... Send Failed. Skipping this file
FINISHED --16:32:21--
Transmission of 1 file failed.
[/B]

Below is my config file.

[B]anonymous_enable=YES
anon_root=/tmp/ftp-root/
no_anon_password=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to FTP service.
listen=YES[/B]

I have read through several posts that talk about creating 'ftp' user and using vsftpd through xinetd instead. None of that worked.

Any pointers?

---

### Post by Lars Noodén on 2010-01-31
> **antitalented said:**
> ...

[B]user@localhost:~$ wput -v ./yyy [ftp://localhost/upload/](ftp://localhost/upload/)
--16:32:21-- `yyy'
  ...
Any pointers?

Yes. The server guide has information quite out of date, some of it by a close to ten years.  

The package [openssh-server](http://packages.ubuntu.com/karmic/openssh-server) has a built-in sftp subsystem.  You can then connect to it, out of the box, with any sftp client.  That includes Filezilla, Nautilus, Dolpin, and Konqueror.

---

