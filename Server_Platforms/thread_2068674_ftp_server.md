---
title: "ftp server"
date: 2012-10-09
forum: Server Platforms
---

### Post by micahpage on 2012-10-09
i am trying to access my ftp through the web browser

I installed vsftpd
i changed /etc/vsftpd.conf:
anonymous_enable=NO
write_enable=YES

i am able to connect via filezilla, but when i go via website it hangs, and eventually does nothing

What am i doing wrong?

---

### Post by Tralce on 2012-10-11
Are you specifying a username in your browser, such as [ftp://tralce@yourftpsite.com?](ftp://tralce@yourftpsite.com?) Since you have anonymous login disabled, poorly written FTP implementation in a browser can cause it to hang under these circumstances.

---

### Post by micahpage on 2012-10-13
I was unaware of using a username like that. 
I tried that solution but was unable I had the same happen.

---

### Post by Tralce on 2012-10-13
What browser are you using? What version? From what operating system are you trying to connect?

---

### Post by thnewguy on 2012-10-13
Some borwsers/FTP servers will choke if you don't specify both the username and password in the URL. For example

[ftp://myuser:mypassword@the-server.com](ftp://myuser:mypassword@the-server.com)

---

