---
title: "Subversion on a subdomain"
date: 2010-10-21
forum: Server Platforms
---

### Post by defex on 2010-10-21
Hey all,

I'm in the process of setting up subversion, and want to set it up on a subdomain of it's own.

Could people who have done this before post examples of their virtual-host configuration?

[COLOR="Gray"]I'm sure I can slash something together, but I'm trying to be ultra careful this time and come out the other side with a server I'd be happy to keep running for years to come, rather than a botch of a configuration that will just confuse me next time I have to do anything on it.[/COLOR]

---

### Post by James78 on 2010-10-21
Create a VirtualHost subdomain, along with DNS, then read this.

[http://svnbook.red-bean.com/nightly/en/svn.serverconfig.httpd.html](http://svnbook.red-bean.com/nightly/en/svn.serverconfig.httpd.html)

... So.. For a subversion subdomain, you would do something like this (taken from the link)..
```
<VirtualHost 192.168.1.156:80>
  ServerName sub.domain.com
  <Location />
    DAV svn
    SVNParentPath /var/svn

    # how to authenticate a user
    AuthType Basic
    AuthName "Subversion repository"
    AuthUserFile /path/to/users/file

    # For any operations other than these, require an authenticated user.
    <LimitExcept GET PROPFIND OPTIONS REPORT>
      Require valid-user
    </LimitExcept>
  </Location>
</VirtualHost>
```
.. This is good and all, but you should understand what does what and why it does it, otherwise you'll probably not get the results you want. Again, the link will explain this. :)

---

