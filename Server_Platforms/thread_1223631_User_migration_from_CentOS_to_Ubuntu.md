---
title: "User migration from CentOS to Ubuntu"
date: 2009-07-26
forum: Server Platforms
---

### Post by fakrulalam on 2009-07-26
Hi,
I have one mail server running on CentOS 5.1 which contain around 8000 users. I like to migrate the server to Ubuntu Server. Usually when I install new server I just copy /etc/passwd, /etc/shadow & /etc/group files; which takes all the users with password. As far
as I know, CentOS shadow file and Ubuntu shadow file password algorithm
is not same. Is there any way to take the password/shadow from CentOS and use it in the Ubuntu? I have tried to copy past the password, shadow & group file, but it doesn't work.

BR

Fakrul Alam

---

### Post by Vegan on 2009-07-26
The hash is not the same so there is no way to copy the users easy. You will have to do it the hard way.

Offer both servers, and let users create and migrate their files on their own.

I have often seen this kind of problem. This is why many operations have several servers.

Migration is a real headache for even the best IT specialists.

---

