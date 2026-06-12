---
title: "Apache2 NameVirtualHost derective failing hard"
date: 2011-07-08
forum: Server Platforms
---

### Post by nearlymagicman on 2011-07-08
Hey guys,

currently i am trying to set up an apache2 name based virtual host, but apparently the Name directive is misunderstood by apache2. The normal name like [www.domain.com]("http://www.domain.com") is not resolved, but only a file is offered for download. But if I add an "/index.php" at the end of the domain, suddenly it works. But this condition is not acceptable.

This is my config file. Hopefully someone gets the error:

```

<VirtualHost *:80>
          ServerName www.domain1.de
          Documentroot /to/the/root/direct
          ErrorLog /to/the/root/direct/log/error_logs
          CustomLog /to/the/root/direct/log/access_logs combined
</VirtualHost>

<VirtualHost *:80>
          ServerName www.domain2.de
          Documentroot /to/the/root/direct
          ErrorLog /to/the/root/direct/log/error_logs
          CustomLog /to/the/root/direct/log/access_logs combined
</VirtualHost>

```
PHP5 and apache2 are installed and updated!

---

### Post by SeijiSensei on 2011-07-08
What do you see in /etc/apache2/mods-enabled/dir.conf?  Mine reads:

```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
```

This directive tells Apache to use one of these files to present the directory's "index" when the root URI is used.  Do you also have an index.html file in the DocumentRoot?  That will take precedence over index.php since it's at the beginning of the list in DirectoryIndex.

---

### Post by nearlymagicman on 2011-07-08
It does show the same as yours, so this cannot be the problem, and yes on both Hosts I do have a index.php with content.

As it does run all on a virtual system and network I tried to access it via a Windows system and it does work, so it must have something to do with Ubuntu and not with apache2.

---

