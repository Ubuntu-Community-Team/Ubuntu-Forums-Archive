---
title: "How to disable anonymous checkout from the SVN"
date: 2009-05-26
forum: Server Platforms
---

### Post by roubele on 2009-05-26
Hi folks,

I installed an svn server on my ubuntu server and created a repository. But the fact is that I CAN do an anonymous checkout. And with the users I created as well.

Do you know where I can disable this feature?

Thanks!

---

### Post by lloyd_b on 2009-05-26
> **roubele said:**
> Hi folks,

I installed an svn server on my ubuntu server and created a repository. But the fact is that I CAN do an anonymous checkout. And with the users I created as well.

Do you know where I can disable this feature?

Thanks!

Assuming you're using svnserve (you don't specify), it should just be a matter of editing the svnserve.conf file, and changing```
anon-access = read
``` to ```
anon-access = none
```(I'm not certain, but svnserve may default to "anon-access = read" if you haven't given it any "anon-access" value.)

Lloyd B.

---

### Post by roubele on 2009-06-01
I'm running on apache... The line "anon-access = none" didnt change anything :/

---

### Post by lloyd_b on 2009-06-01
> **roubele said:**
> I'm running on apache... The line "anon-access = none" didnt change anything :/

Yes, that line was strictly for svnserve.  For Apache, in the config file, you should have a "<Location /svn>" block defined.  In that block, add "Require valid-user" to that block.  That should deny any access to the repo, except for the users that you have configured...

May I suggest bookmarking [this site]("http://svnbook.red-bean.com/en/1.5/index.html")?  It provides very clear instructions on how to do just about anything in regards to Subversion.

Lloyd B.

---

### Post by roubele on 2009-06-02
Yep, this is what I have in fact...
Here is my dav_svn.conf:

```

<Location /svn> 
  DAV svn 

  SVNPath /var/svn/foo 
  AuthType Basic 
  AuthName "Subversion Repository" 
  AuthUserFile /etc/apache2/dav_svn.passwd 
  Require valid-user 
</Location>

```

But I still can browse the repo without any login/password =)

---

### Post by lloyd_b on 2009-06-02
> **roubele said:**
> Yep, this is what I have in fact...
Here is my dav_svn.conf:

```

<Location /svn> 
  DAV svn 

  SVNPath /var/svn/foo 
  AuthType Basic 
  AuthName "Subversion Repository" 
  AuthUserFile /etc/apache2/dav_svn.passwd 
  Require valid-user 
</Location>

```

But I still can browse the repo without any login/password =)

Sorry, I'm out of my depth (I've used svnserve, but haven't actually run a repo via Apache).  According to the docs, your repository *should* be limited to just the defined users - the only difference between your Location block and the example is that they use "SVNParentPath" rather than "SvnPath", but that shouldn't make the slightest difference...

Hopefully, someone with actual experience with Apache/SVN will wander by and point out the problem...

Lloyd B.

---

### Post by John Cheng on 2009-06-03
The configuration is correct. Are you sure that config file is being loaded? 

What is the output of <PATH_TO_HTTPD>/httpd -t?

Intentionally misspell one of the directives, then run httpd -t again to validate that httpd is loading the right file.

---

### Post by karlw on 2009-08-09
> **roubele said:**
> Yep, this is what I have in fact...
Here is my dav_svn.conf:

```

<Location /svn> 
  DAV svn 

  SVNPath /var/svn/foo 
  AuthType Basic 
  AuthName "Subversion Repository" 
  AuthUserFile /etc/apache2/dav_svn.passwd 
  Require valid-user 
</Location>

```

But I still can browse the repo without any login/password =)

Are you restarting Apache after you change the configuration file?  I run:

```

sudo /etc/init.d/apache2 restart

```

But it could be different on your system.

---

