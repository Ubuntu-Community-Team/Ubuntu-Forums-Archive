---
title: "Apache svn under maverick"
date: 2011-01-07
forum: Server Platforms
---

### Post by vortmax on 2011-01-07
I'm attempting to get svn over apache running on maverick server.  

Here is my site config
```


<VirtualHost *:80>
        ServerName  common.subversion.xxx.xxx
        ServerAdmin xxxxxxx
        DocumentRoot /var/www/SVN

        AddExternalAuth pwauth  /usr/sbin/pwauth
        SetExternalAuthMethod pwauth pipe

<Location />
  DAV svn
  SVNParentPath /data/.repos
  SVNListParentPath on
  SVNIndexXSLT "/repos-web/view/repos.xsl"
  AuthType Basic
  Require valid-user
  AuthName "xxxxxxxxxxxx"
  AuthBasicProvider external
  AuthExternal pwauth
</Location>


</VirtualHost>

```

With this configuration, when I attempt to connect to the repo, it fails and I get the following error message:

```

(20014)Internal error: Can't open file '/data/.repos/code/format': Permission denied

```

I double and triple checked the permissions, and confirmed they were correct (I have this setup working fine on a different server running Lucid).

I managed to find some stuff on a redhat forum that this error is common with Selinux enforcement preventing Apache2 from accessing files outside of the document root.  So I tried to chcon the repo with:

```

chcon -h system_u:object_r:httpd_sys_content_t /data/.repos
chcon -R -h root:object_r:httpd_sys_content_t /data/.repos/*

```

After that didn't work, I verified that this is in fact the issue by moving the repo directory inside /var/www.  Of course, it worked just fine.  Right now, I managed to work around the issue by symlinking the repo in /data to /var/www/repos.  

While this works, I would rather actually fix the issue.  

While the redhat posts indicated selinux, when I checked it with sestatus (after first installing sestatus), it came back disabled.  So what is locking down the /var/www directory?

---

### Post by vortmax on 2011-01-08
Turns out the solution was fairly simple.  I just had to add a 

```

<directory /data/.repos>

</directory>

```
block to grant apache rights to access the directory.

---

