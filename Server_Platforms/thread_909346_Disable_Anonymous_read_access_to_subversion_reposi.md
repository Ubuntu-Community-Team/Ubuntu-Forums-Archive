---
title: "Disable Anonymous read access to subversion repository"
date: 2008-09-03
forum: Server Platforms
---

### Post by vital101 on 2008-09-03
Hello everyone,

I've been following a guide on how to set up Apache2 + SSL + Subversion.  All is well and good, and I've been able to do so.  The problem is that by default, the authentication scheme in the guide allows for anonymous reading of the repository.  It requires authentication to commit changes, but I want authentication for both read AND write.

Here's my dav_svn.conf file.
*Please note that SVNParentPath is also defined, but for some reason it won't show up in the forum.  It is defined and working correctly.

```

<Location /svn>
                                                                       
  DAV svn
                                                                                                      
  AuthType Basic
  AuthName "Subversion Repository"
  AuthUserFile /etc/apache2/dav_svn.passwd
                                                                                 
  <LimitExcept GET PROPFIND OPTIONS REPORT>
    Require valid-user
  </LimitExcept>

</Location>
                                   

```

Thanks ahead of time.
/vital101

---

### Post by cdenley on 2008-09-03
> **vital101 said:**
> Hello everyone,

I've been following a guide on how to set up Apache2 + SSL + Subversion.  All is well and good, and I've been able to do so.  The problem is that by default, the authentication scheme in the guide allows for anonymous reading of the repository.  It requires authentication to commit changes, but I want authentication for both read AND write.

Here's my dav_svn.conf file.
*Please note that SVNParentPath is also defined, but for some reason it won't show up in the forum.  It is defined and working correctly.

```

<Location /svn>
                                                                       
  DAV svn
                                                                                                      
  AuthType Basic
  AuthName "Subversion Repository"
  AuthUserFile /etc/apache2/dav_svn.passwd
                                                                                 
  <LimitExcept GET PROPFIND OPTIONS REPORT>
    Require valid-user
  </LimitExcept>

</Location>
                                   

```

Thanks ahead of time.
/vital101

Just a guess
```

<Location /svn>
                                                                       
  DAV svn
                                                                                                      
  AuthType Basic
  AuthName "Subversion Repository"
  AuthUserFile /etc/apache2/dav_svn.passwd
                                                                                 
  [B]<Limit>
    Require valid-user
  </Limit>[/B]

</Location>

```

---

