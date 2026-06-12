---
title: "Information required on hosting local data to access in LAN"
date: 2013-06-22
forum: Server Platforms
---

### Post by slkamath on 2013-06-22
Hi All,

How are you? Hope all are fine.

I am in search of hosting the local data into server to access LAN users  only [(as of now)(files are mostly consists of WORD, EXCEL, PPT, PDF,  PICTURES, etc)]. 
Below mentioned security required.
1. User authentication to access folders or files.
2. User copy protection.
3. User print protection.
4. User edit protection.
5. User delete protection.
6. If possible user logs (who are all accessed).
7. Only 2 to 3 users should have edit, copy, delete, insert, files.

So I am requesting you please suggest me what is the best I can use for   my scenario. I think on FTP, but I dont know it will fulfill my needs.

So please suggest me.

Thanks in advance.

Regards

Lokesh Kamath

---

### Post by newbie-user on 2013-06-23
How about samba?

---

### Post by slkamath on 2013-06-23
Thanks for your reply. BUt will my requirement be met in that?????

---

### Post by SeijiSensei on 2013-06-23
Yes, though I would only use Samba on a LAN.  If you need to grant remote users access, you are better off with something like SSH/SCP and controlling rights using regular Unix permissions.

Samba has very extensive and fine-grained [access controls]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html").

---

