---
title: "UID and GID for apache"
date: 2009-03-28
forum: Server Platforms
---

### Post by rzj on 2009-03-28
Several references on apache configuration recommend creating a specific user for apache and putting it in the httpd.conf file.

some sources suggest that it should specifically have uid=48 and gid=48 and that it should be --system and --disabled-login.

Is this sound advice?

Is there a list of reserved gid's and uid's?

What does --system do?

My 8.10 server install currently has no User and Group in the apache config so does this mean it will run as root?

Thanks,
Ray

---

