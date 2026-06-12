---
title: "Securing SVN repository"
date: 2011-07-26
forum: Server Platforms
---

### Post by minashokry on 2011-07-26
Hello everyone, I have svn running behind apache using dav_svn module. My repository has some open dirs and some dirs can't be seen without login. I already handle this well with dav_svn.authz.

For security, I want all svn access to be done on SSL. I also want if a user tried to access using http to be redirected to the same address but on https. Everything is almost working fine now. Except that I suspect that when a user tries http,they will be taken to authenticate and then redirected to https. which means the authentication wasn't secure. I want the authentication to be made over SSL too. Here is my current dav_svn.conf file

```

<Location /svn>
  RewriteEngine on
  RewriteCond %{HTTPS} off
  RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

  DAV svn

  SVNPath /var/svn
  AuthzSVNAccessFile /etc/apache2/dav_svn.authz

  SSLRequireSSL
  Satisfy Any
  Require valid-user

  AuthType Basic
  AuthName "Credentials to access The Subversion Repository"
  AuthUserFile /etc/apache2/dav_svn.passwd
</Location>

```

Any suggestions?

---

