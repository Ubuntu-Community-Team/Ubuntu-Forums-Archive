---
title: "WebDAV PUT access: permission control"
date: 2012-08-11
forum: Server Platforms
---

### Post by dewdrop_world on 2012-08-11
Hi,

I'm very close to having a working WebDAV server (for org-mobile sync).

The remaining problem is: The only way at present I can PUT files into it is by granting everybody write access.

**drwxrwxrwx**  -- http PUT is OK
**drwxrwxr-x**  -- http PUT fails with "403 Forbidden"

I'd like to control the file system permissions better than that.

I tried creating a UNIX user with the same name as the Web service authentication user, and then I added the new user to the www-data group (which is the owning group of the webdav directory structure). No joy.

How to do it?

Thanks,
James

---

### Post by SeijiSensei on 2012-08-12
If you're using Apache mod_dav, the standard method for handling authentication and permissions is to use the <Limit> directive in Apache.  See [the documentation for mod_dav](http://httpd.apache.org/docs/2.2/mod/mod_dav.html) for details.

---

