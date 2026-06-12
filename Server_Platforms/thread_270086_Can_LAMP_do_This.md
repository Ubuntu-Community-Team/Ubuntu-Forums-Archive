---
title: "Can LAMP do This?"
date: 2006-10-02
forum: Server Platforms
---

### Post by Zephirus on 2006-10-02
I want to run a webserver...   Easy enough as I do have LAMP running and I have 3 virtual servers...


So I have 2 questions.   First I want to make this a DNS server also.  2nd I want to have users FTP to their directory ONLY like any webhosting service.  Finally, I want to have Frontpage extentions on the server...


Is all of this possible, and if so, can you point me in the right directions?  I just started working with the server yesterday.

---

### Post by sonic2000gr on 2006-10-02
Haven't done the DNS part yet myself, so I can't help you with that sorry.
Believe it or not, you will get what you need for Frontpage server extensions  here: 

[http://support.microsoft.com/default.aspx?scid=kb;%5BLN%5D;202198](http://support.microsoft.com/default.aspx?scid=kb;%5BLN%5D;202198)

For the FTP server to chroot users into their directories:

Assuming you use the ProFTP server, edit the /etc/proftpd/proftpd.conf file and add this to the <Global> section:

```
DefaultRoot ~
```

---

### Post by Zephirus on 2006-10-02
So I can have lets say 5 websites owned by 5 different companies and have a different FTP user for each that can ONLY access their folders?


Hmmm  small example maybe?

---

### Post by sonic2000gr on 2006-10-02
Exactly! 
You may also want to comment out the section marked <Anonymous ~ftp> so you don't have anonymous access at all (anonymous access points to another directory). All other unix users you create will be able to ftp to their own home directory ONLY. You can then configure you virtual servers in apache to read from these directories.

---

