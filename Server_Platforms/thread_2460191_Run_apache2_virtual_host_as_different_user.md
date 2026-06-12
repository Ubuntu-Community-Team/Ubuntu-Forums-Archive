---
title: "Run apache2 virtual host as different user"
date: 2021-04-04
forum: Server Platforms
---

### Post by dam034 on 2021-04-04
Dear users,

happy easter!

Meantime, I'm delighting to set up a virtual host on apache2 server. My VPS has ubuntu server edition.

I have a directory which will be the root directory of a website. That is **/srv/sites/fish**

The VH configuration file is this:

```
User chandelier
Group chandelier

<Directory /srv/sites/fish/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port t$
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName mywebsite.com

        ServerAdmin me@here
        DocumentRoot /srv/sites/fish

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/fish.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

And the directory is this:

```
root@myvps:/srv/sites/fish# ls -ahl
total 16K
drwxrw----  3 chandelier chandelier    4,0K apr  4 17:52 .
drwxrwxr-x 13 peter  admin    4,0K mar 29 00:37 ..
-rwxrw----  1 chandelier chandelier   88 apr  4 17:50 index.htm
drwxrw---- 15 chandelier chandelier    4,0K apr  3 14:07 wiki
```

Now when I try to visit my website from browser, I get 403 error. I want to run apache2 as chandelier user in this virtual host.

I think this is a permission error. I did a mistake, but I don't know where.

How can I fix?

Thanks

---

### Post by TheFu on 2021-04-04
what userid is apache running under now?
Generally, it is a bad idea from a security standpoint to alter daemon accounts to be shared by login accounts. Why change it?

---

### Post by dam034 on 2021-04-04
This is a snippet of envvars:
```
export APACHE_RUN_USER=peter
export APACHE_RUN_GROUP=admin
```

I gave a virtual host to a friend. He can upload files in a directory, which is the root directory of his website.
For security reason, I don't want to run apache in his VH with my user/group, but with his username (chandelier).
A bit like shared hosting companies do.

How can I do?

Thanks

---

### Post by TheFu on 2021-04-04
I expected to see the apache processes running in the process table - filtered **ps -eaf** output.  

I really don't know how hosting companies do it. I've used a VPS where I had root. I had a login to a shared hosting provider about 25 yrs ago and could see all the files for the other 3000 websites on the same server, but the world was very different back then and I didn't know any better at the time. It wasn't very secure.

I'm pretty sure that shared hosting companies don't allow users to restart apache or control their own apache server - definitely not on the standard ports which require sudo/root to restart.

It is all normal Unix permissions, I'd expect. They may have a program that lets users request that apache be restarted every 2-5 minutes. I can think of a number of different ways to accomplish that which don't require webmasters to have direct control over apache at all.

There's a website with guides for "The Perfect Server" .... which is probably how many shared hosting companies setup their servers.  
[https://www.howtoforge.com/tutorial/perfect-server-ubuntu-20.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-20.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)
That could provide ideas for securing different users, but I don't know.

Perhaps someone else will answer?

---

### Post by dam034 on 2021-04-06
I don't even know how hosting companies do.

I simple want to give a virtual host to a friend, using his own username to access ssh and to run apache. So his username can only read/write files is his directory and I don't have to worry about the security of the rest of the server.

Thanks

---

### Post by TheFu on 2021-04-06
> **dam034 said:**
> I don't even know how hosting companies do.

I simple want to give a virtual host to a friend, using his own username to access ssh and to run apache. So his username can only read/write files is his directory and I don't have to worry about the security of the rest of the server.

Shared hosting companies don't run different apache versions for each customer.  They provide a shared apache setup and customers allow the userid running apache file access using normal POSIX permissions and groups.  How to allow multiple different user-accounts to work together is a normal Unix permissions thing - used by hundreds of millions of users daily around the world.  [https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965)  has an explanation for how to set this up.  

It assumes that you already understand about 90% of how Unix permissions work and are controlled. If you don't have that knowledge already, you'll need that first.  There are lots and lots of tutorials for Unix permissions on the internet and video websites and in every beginning Unix/Linux book.  Every popular OS uses those permissions (except 1), so it isn't a waste of time to learn how OSX, iOS, Android, Linux, and every Unix permissions work.  Spend the time now, about 30 minutes, to avoid hours, days, months, perhaps years, of frustration in the future.  It is an elegant design.
If you need a book to learn, here's a free, no-hassle, download: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) . It has a chapter on permissions, but that really needs the userid and groupid introduction too.   That is one problem with Unix skills.  They all build from fundamentals. If we don't understand groups, then we can't understand permissions. If we don't understand permissions, we can't setup methods for different users to work together safely or understand how different daemons (like apache) work.  

On Unix-like systems, all security begins with file permissions.  You may have heard "everything is a file on Unix."  That means that since files have permissions to control access, the same permissions are used to control access to partitions, disks, mice, keyboards, webcams, and any other "thing" connected to a Unix system.  Permissions and groups are the core for everything Unix/Linux.  BTW, everything is a file ... except running processes ... but everything else is a file.  So directories are really files too. ;)

BTW, you haven't posted the requested output. Without that, I can't help.

---

### Post by SeijiSensei on 2021-04-06
You could create a virtual host within a domain you control, e.g, myfriend.mydomain.com. Use a <Directory> statement to point to a directory in his home that he can manage.

---

