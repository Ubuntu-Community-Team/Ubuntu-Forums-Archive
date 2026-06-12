---
title: "SSLRequireSSL, Satisfy Any, with fine-grained permissions on svn repository"
date: 2010-08-07
forum: Server Platforms
---

### Post by minashokry on 2010-08-07
Hello guys,

I am setting up an SVN repository behind apache http daemon.

What I want to do is that.
[LIST=1]
[*] Repository is accessible only by https. All http requests should be denied.
[*] Repository is anonymously accessible (read-only).
[*] Committers have to authenticate.
[*] Some directories are accessible only by some users.
[/LIST]

First, I don't have problems with setting per-directory permissions. I know how to write dav_svn.authz file. My problems are with the first 3 requirements.

My dav_svn.conf file contains these
```

<Location /svn>
...
SSLRequireSSL
Satisfy Any
Require valid-user
...
</Location>

```

This satisfies requirements 2, 3 well. but when trying to access the repository with http, it asks for credentials and if I provided right credentials, it opens which I don't want. I want all http requests to get denied.
Besides that, sometimes I get a 403 or 400 responses when I try to commit.

Can anyone help?
Thanks in advance.

---

