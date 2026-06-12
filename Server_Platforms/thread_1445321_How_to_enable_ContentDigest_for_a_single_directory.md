---
title: "How to enable ContentDigest for a single directory"
date: 2010-04-02
forum: Server Platforms
---

### Post by osx on 2010-04-02
I have a folder just for download files (e.g., application update files). I would like to send the Content-MD5 http header for each file a user downloads. However, there is a warning the apache documentation that says enabling ContentDigest could cause performance issues (see [http://httpd.apache.org/docs/1.3/mod/core.html](http://httpd.apache.org/docs/1.3/mod/core.html)).

So, is there a way to send ContentDigest header for the contents of a specific directory only?

The apache documentation makes it sound like I can set a context so that it applies to a directory only, but I can't figure out how this is done if this really is an option.

Can anybody tell me if I am interpreting the documentation correctly and, if so, how to set apache to work this way?

Thanks.

---

### Post by Bachstelze on 2010-04-02
Just put it in the .htaccess file of that directory (and make sure you have the proper AllowOverride in your server config).

Alternatively, you can also create a <Directory> entry for that directory in your config, and define ContentDigest there.

---

### Post by osx on 2010-04-02
> **Bachstelze said:**
> Just put it in the .htaccess file of that directory (and make sure you have the proper AllowOverride in your server config).

Alternatively, you can also create a <Directory> entry for that directory in your config, and define ContentDigest there.

Is one method better than the other for this specific case?

If I understand you correctly then, if I enter this into /etc/apache2/apache2.conf then it should work?

> ### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#
<Directory /var/www/portal/updates>
   ContentDigest on
</Directory>

---

### Post by Bachstelze on 2010-04-02
> **osx said:**
> Is one method better than the other for this specific case?

It really depends how your system works. For example, if users can access the dirctory via FTP, it might be better to hardcode the option in your Apache config rather than in a .htaccess file in the directory, so that users can't just change it from FTP.

> If I understand you correctly then, if I enter this into /etc/apache2/apache2.conf then it should work?

Yes, though it migt be better style to put it at the bottom of the file, or even inside your VirtualHost directive if you have one.

---

### Post by osx on 2010-04-02
> **Bachstelze said:**
> It really depends how your system works. For example, if users can access the dirctory via FTP, it might be better to hardcode the option in your Apache config rather than in a .htaccess file in the directory, so that users can't just change it from FTP.



Yes, though it migt be better style to put it at the bottom of the file, or even inside your VirtualHost directive if you have one.

Ok, well, I'm not using FTP so I created a blank .htaccess file in the directory and simply added

> ContentDigest On

It's returning the Content-MD5 header only for files coming out of that directory and none other so everything appears to be working.

Thanks for the help.

---

