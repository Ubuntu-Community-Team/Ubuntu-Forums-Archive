---
title: "Apache2 DocumentRoot error restart"
date: 2012-01-12
forum: Server Platforms
---

### Post by Loggy on 2012-01-12
10.04 LTS virtual server (KVM).

It is possible for a user to accidentally or otherwise rename or delete the document root.  When Apache2 tries to reload or restart, it will fail and all virtual sites will be disabled.

In a shared hosting environment, such a missing DocumentRoot (or other config error) is therefore a security issue.  How do I get Apache to issue a warning rather than fail to restart?  

Any clues would be very helpful.  I have spent most of this morning looking for an answer and found one person who has pointed to the same problem but there was no answer to him either.  But he had another (Debian) server where only a warning was issued so it must be possible.

(I restart on my VPS to flush some of the bloating - maybe there is a better way of doing that as well.  I try to keep the Apache configuration clean and minimalist.  After all we are not in Windows are we???:-))

---

### Post by Lars Noodén on 2012-01-12
If this failure can be made to happen consistently by following a set of steps, then it is a very good idea to submit a bug report about it.

---

### Post by Loggy on 2012-01-12
Lars

My feeling is that it is not so much a bug as some setting.  

But though I have trawled through the apache docs as well as burnt out google, I have only found the one question [http://www.webhostingtalk.com/showthread.php?t=868358](http://www.webhostingtalk.com/showthread.php?t=868358) that raised the issue and wasn't answered.  That question was rather old so I have asked the originator whether they found a solution.  

I am pretty sure it is nothing to do with my setup and it has happened a few times (actually my bad rather than anyone else's bad).  So I realised it is a potential issue.

If I don't get any response though I will start a bug report.

---

### Post by Lars Noodén on 2012-01-12
Right but it from what it sounds like, if the document root for one virtual host is missing then the whole server fails even for other virtual hosts that have a complete document root.  Do I have that right?

---

### Post by Loggy on 2012-01-12
I've just seen that from Apache2 2.2.17 and on there is a -T option that skips the DocumentRoot check on start or restart.  Perhaps the solution is to upgrade but it is not in the 10.04 repos I think (2.2.14).

Perhaps this could be back-ported to the LTS version...?  Could that be a bug report topic?

---

### Post by Lars Noodén on 2012-01-12
> **Loggy said:**
> I've just seen that from Apache2 2.2.17 and on there is a -T option that skips the DocumentRoot check on start or restart.  Perhaps the solution is to upgrade but it is not in the 10.04 repos I think (2.2.14).

Can you point to a link?  I have 2.2.21 on Precise and the manual page does not list a **-T** option.  It would be useful to have in the context of running multiple virtual hosts with different system administrators.

---

### Post by Loggy on 2012-01-12
Lars

I found it at 

[http://httpd.apache.org/docs/current/programs/httpd.html#page-header](http://httpd.apache.org/docs/current/programs/httpd.html#page-header)

The webhostingtalk thread was quite old (6/12/2009) so I don't expect an answer but it is the only lead.  Clearly ConeMan was running an older version on his working server. :-)

---

### Post by Ryan Dwyer on 2012-01-12
The problem is that users are able to delete their document roots, not that Apache is refusing to start when it encounters a configuration error. Try removing the write permission for the site user from the directory containing the document root.

For example:
dr-x------ sitea sitea /var/www/vhosts/sitea.com
drwx------ sitea sitea /var/www/vhosts/sitea.com/public_html

If the user needs a place to put files outside of the document root, they won't be able to write directly to sitea.com using these permissions. In that case, create another directory next to public_html called something like "private" with the same permissions as public_html.

By the way, I haven't tested this. I'm just guessing.

---

### Post by Loggy on 2012-01-12
Ryan

You sometimes need write permissions for a directory in which the document root exists - if you want to add other files or directories for example.   So while your fix may work, it is not the ideal solution.  

For example I always mount a documentroot inside a www folder in the user's directory.  This would enable them to include a database config file within (say) their CMS config which couldn't be found directly by Apache.  I think quite a lot of people do this (hopefully the indexing has also been blocked!).

---

### Post by Ryan Dwyer on 2012-01-12
That's the purpose of the "private" directory: For storing files that need to be outside of the document root but can still be included by Apache scripts.

---

### Post by Loggy on 2012-01-12
OK but I'm sure it is not the only case where you may want to allow write access to the directory.....

---

