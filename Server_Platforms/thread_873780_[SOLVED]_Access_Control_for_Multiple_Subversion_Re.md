---
title: "[SOLVED] Access Control for Multiple Subversion Repositories"
date: 2008-07-29
forum: Server Platforms
---

### Post by zdunham on 2008-07-29
Hi, I have just recently set up Subversion 1.4.6 (will upgrade soon) and Apache2 on the newest Ubuntu version. My objective with it is to create a main repository with multiple sub-repositories that different users will have sole access to. I'm having trouble getting the access controls set up right so here is what I have.

/etc/apache2/mods-enabled/dav_svn.conf
```

<Location /svn>
   DAV svn
   #SVNPath /svn (used parent)
   SVNParentPath /svn

   AuthType Basic
   AuthName "Subversion Repository"
   AuthUserFile /etc/apache2/dav_svn.passwd
   AuthzSVNAccessFile /etc/apache2/svn_access_control

   Require valid-user
</Location>

```

I used htpasswd to create the users in dav_svn.passwd. Assume for purposes here I have user1 and user2.

/etc/apache2/svn_access_control
```

[/]
user1 = rw
user2 = rw

[/user1-work]
user1 = rw

[/user2-work]
user2 = rw

```

I created /svn with the mkdir command and I created /svn/user1-work and /svn/user2-work with svnadmin create. With that current setup, user1 and user2 cannot access /svn but each of them can access both user folders when they should only access their own.
Also, I performed these two commands on each of the three folders:
```

sudo chown -R www-data:www-data <folder>
sudo chmod -R g+ws <folder>

```

So then I tried this:
```

[/]
user1 = rw
user2 = rw

[/user1-work]
user1 = rw

[/user2-work]
user2 = rw
user1 = none

```

After that suddenly user1 could not access his own folder either. I have no idea what is going on help would be greatly appreciated. Thanks in advance.

---

### Post by tamoneya on 2008-07-29
I would do this with two separate location tags. one like this <Location /svn/user1> and the other like this <Location /svn/user2>.  Then you can have two separate auth files and you keep the two repositories separate.

---

### Post by zdunham on 2008-07-29
Thanks, good thought I'll try that now and get back on here in a few minutes.

---

### Post by zdunham on 2008-07-29
Thanks alot that worked! You saved me alot of headache.

---

### Post by tamoneya on 2008-07-29
no problem.  Mark as solved if you could.  Its in the thread options menu to the top right of the first post.

---

