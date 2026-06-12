---
title: "Access to Multiple Subversion Repositories"
date: 2009-02-14
forum: Server Platforms
---

### Post by r557 on 2009-02-14
I followed the documentation at [https://help.ubuntu.com/8.04/serverguide/C/subversion.html](https://help.ubuntu.com/8.04/serverguide/C/subversion.html) to get subversion up and running.  

By default, i connect through to one repository via http, [http://servername/svn](http://servername/svn).

 ```
<Location /svn>
  DAV svn
  SVNPath /path/to/repos
  AuthType Basic
  AuthName "Your repository name"
  AuthUserFile /etc/subversion/passwd
  <LimitExcept GET PROPFIND OPTIONS REPORT>
  Require valid-user
  </LimitExcept>
  </Location> 
```

That works for a test scenario, so if i wanted to create a new repository with a new url, do i just need to add a new repository with ```
svnadmin create /path/to/repos2/

``` and another set of tags such as above, but specify a different in my tag.

So if i wanted a new svn at [http://servername/newrepository](http://servername/newrepository), do i create another set of tags in my apache2.conf file such as:

```
 <Location /newrepository>
  DAV newrepository
  SVNPath /path/to/repos2/
  AuthType Basic
  AuthName "Your repository name"
  AuthUserFile /etc/subversion/passwd
  <LimitExcept GET PROPFIND OPTIONS REPORT>
  Require valid-user
  </LimitExcept>
  </Location> 
```

---

### Post by r557 on 2009-02-15
I have found a solution for the issue.  [http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-subversion-with-web-access-on-ubuntu/)

---

