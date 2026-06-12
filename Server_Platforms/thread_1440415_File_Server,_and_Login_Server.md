---
title: "File Server, and Login Server"
date: 2010-03-27
forum: Server Platforms
---

### Post by caribacey on 2010-03-27
Hi,

I followed a link from this forum on how to do a file server.
([http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver))

I maintain a network of 60 computers for a small school.
At the moment I run a Windows 2003 Server, with all the junk loaded for login authentication, etc.
However, the main purpose of the server is as a fileserver for the students to save documents, and as a login authenticator.

I do not want a domain controller, DNS server, etc, that Win Server forces upon the user. I do not want a domain of something.somethingelse.com. This is a purely internal school network
I want a way to assign rights to certain classes (groups) at login.
I want the same server to be a file server.

Is this possible with Ubuntu and variants?

Thanks.

---

### Post by ken22 on 2010-03-27
Yes, look into openldap. You should be able to auth off ldap for the file server. ldap can also be used to group people for the purposes of administration.

---

### Post by ken22 on 2010-03-27
I should point out that you would want to use Samba if the school machines are Windows.

---

