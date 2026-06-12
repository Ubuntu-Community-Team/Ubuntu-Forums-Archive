---
title: "Post Install LAMP Question"
date: 2012-06-26
forum: Server Platforms
---

### Post by bward on 2012-06-26
I have setup a LAMP server for me to use.  I would like to allow a few people to have access to this server in order to host some of their content.  I do not want them to have full access to the box since I have personal content on there and run other services.

What is the best way to give them limited access?

Is there a default group that they should be added to in order to limit their access to the AMP portion of the server?

Do I jail ssh and sftp to /var/www and have them only upload the files that they need?

What are the best practices for this type of situation?

I'm used to being the only user on the system, so any insight the community can provide on this would be much appreciated.

---

### Post by LHammonds on 2012-06-26
There are probably a ton of ways to accomplish that goal and there are probably some best-practice papers out there too.

I have not done such a thing but if I were looking to do something like that, I would probably only allow them to upload to a user-specific folder (ftp or sftp) and then have an automated script that will process the folder and move them where they need to go.  I would also code in some checks for mischievous files...such as EXE files or virus/trojan files.

LHammonds

---

### Post by SeijiSensei on 2012-06-27
Create website directories for each user like /home/username/web.  Change the permissions on /home/username from 700 to 711 so the Apache "user" www-data can see their sites.  For each user, create a separate <VirtualHost> with a unique ServerName like user.domain.name and a DocumentRoot that points to /home/user/web.

Do you have a registered domain you can use?  Itwould certainly make things a lot easier if each site had a unique public name like user.domain.name.  In the DNS you could just have:

```

@     IN SOA   domain.name. root.domain.name (
      [stuff]

www   IN A     1.2.3.4
user1 IN CNAME www
user2 IN CNAME www
[etc.]

```

---

