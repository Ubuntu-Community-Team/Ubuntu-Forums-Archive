---
title: "[SOLVED] Apache authentication not working ?"
date: 2008-11-11
forum: Server Platforms
---

### Post by Jolly.Tall on 2008-11-11
I'm trying to protect a subversion repository, requiring a username/password to browse the files, and requiring membership of an 'admin' group to file any changes.

Guest user (read-only permissions) is 'user1', admin user (read-write permissions) is 'user2'. Both are defined in dav_svn.passwd file, but only user2 is defined in dav_svn.group, ie

# dav_svn.group
admin:user2

[httpd.conf] 
```
<VirtualHost *:443>
  <Location /svn>
    DAV svn
    SVNPath /path/to/svn
    AuthType Basic
    AuthName "Subversion Repository"
    AuthUserFile /etc/apache2/dav_svn.passwd
    AuthGroupFile /etc/apache2/dav_svn.group
    Require valid-user

    <LimitExcept GET PROPFIND OPTIONS REPORT>
       Require group admin
    </LimitExcept>
  </Location>
</VirtualHost>

```

Although all attempts to acces the /svn is greeted with the login box for both users, both users can commit changes to the repo, and the Apache access.log shows PUT, MERGE, CHECKOUT, DELETE, PROPPATCH, MKACTIVITY, etc entries for user1, who should not be able to do any of those things.

I tried putting 'Require valid-user' in a <Limit GET PROPFIND OPTIONS REPORT> block, but it didn't help.

It looks like the LimitExcept block is not taking effect, but I can't see where I might have mis-configured it. Any help appreciated.

---

### Post by Philio on 2008-11-11
There is another way you can do this which I use myself:

You will want something like this in your Apache config:

    <location /svn>
        DAV svn
        SVNPath /path/to/repo
        AuthType Basic
        AuthName "My Repository"
        AuthUserFile /path/to/userfile
        Require valid-user
        AuthzSVNAccessFile /path/to/accessfile
    </location>

You user file should be fine as is, then in the access file you will need something like this:

[svn:/]
user1=r
user2=rw

I've never tried it the way your trying to get it to work, but this method definately works!

I'd be surprised if there wasn't a way to configure groups in this manor too, if you don't want to configure it on a per user basis.

---

### Post by Philio on 2008-11-11
Have a read of this, it describes the access file options and how to define groups within the access file about 3/4 of the way down:

[http://svnbook.red-bean.com/en/1.1/ch06s04.html](http://svnbook.red-bean.com/en/1.1/ch06s04.html)

---

### Post by Jolly.Tall on 2008-11-11
Philio,

> **Philio said:**
> I've never tried it the way your trying to get it to work, but this method definately works!

Sure does: RA layer request failed: MKACTIVITY of '/svn/!svn/act/be257560-c2bd-8e93-94de-1fd048z815b7': 403 Forbidden

Many thanks :)

---

### Post by Jolly.Tall on 2008-11-11
Philio,

> [http://svnbook.red-bean.com/en/1.1/ch06s04.html](http://svnbook.red-bean.com/en/1.1/ch06s04.html)

Yeah, I did read that and used the basic authorization example as a basis for my httpd.conf, but managed to miss the AuthzSVNAccessFile section. What's that about RTFM? ;)

---

### Post by Philio on 2008-11-11
lol :)

You will fall asleep pretty quick if you read too much of the svnbook though!

---

### Post by Philio on 2008-11-11
It took me a while to set it up the first time. You have to setup all the htpasswd files, access control files, create the repos, configure apache etc etc.

If you ever need to add repos, move servers, expand it etc once you've done the leg work the first time it takes 5 seconds to copy/paste a bit of apache config or whatever is needed.

AuthzSVNAccessFile and AuthGroupFile are incompatible with each other I think, so if you use AuthzSVNAccessFile you must have your group declarations in there too. Makes you wonder quite what the pupose of AuthGroupFile is although this is all Apache's own functionality not specific to svn, just makes your svn work nicely.

If you haven't seen/used it before websvn is a nice web based repo browser, also Tortoise if your using Windows clients is great.

---

### Post by Jolly.Tall on 2008-11-11
> If you haven't seen/used it before websvn is a nice web based repo browser, also Tortoise if your using Windows clients is great.

No I hadn't seen websvn before, and was looking for something like that. Thanks. Best I found so far was ReposStyle ([http://www.reposstyle.com/](http://www.reposstyle.com/)) but it doesn't do log view (at least not without going through contortions with python bindings), so it looks promising. There's a Debian package available so I'll give it a whirl. I do all my dev. work on an Ubuntu VM these days so Tortoise is not an option.

---

