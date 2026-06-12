---
title: "[SOLVED] DirectoryIndex issues inside of cgi-bin subdirectory"
date: 2008-05-15
forum: Server Platforms
---

### Post by mvan83 on 2008-05-15
I'm having an extremely stubborn issue with Apache(2). I can't get it to load an index.pl file from inside of a cgi-bin directory. DirectoryIndex seems to respond correctly inside of a normal static page directory. However, inside of any directory under cgi-bin, trying to load a page by the directory gives me a 403 forbidden error and the error.log gives me a "attempt to invoke directory as script" error. I've searched these forums and elsewhere and tried everything I could find. I've tried htaccess files too and I couldn't get that to work either. Can anyone help? Thanks a ton, I've been banging my head against the wall trying to figure this out.

---

### Post by Thanoulis on 2008-05-15
Maybe [this]("http://hoohoo.ncsa.uiuc.edu/docs/tutorials/cgi.html") could help...

---

### Post by mvan83 on 2008-05-16
Thanks for the link. Didn't really help, but it did get me started on googling things related to cgi and htaccess files, etc. and I found something that works:
```

  <Directory "/var/www/fb/">
    Options FollowSymLinks MultiViews
    AllowOverride Options FileInfo Limit
    Order allow,deny
    allow from all
  </Directory>

```
The AllowOverride line being the key change. Then, in that directory, place this inside of the .htaccess file:
```

Options +ExecCGI
AddHandler cgi-script cgi pl

```

Oddly, simply placing those lines into the above section in the sites-available/default file didn't work :-k

So it turns out I didn't even need to change DirectoryIndex lines at all. Those specified in dir.conf work for me (falls through to index.pl) and through the steps above, it recognizes it's a script file to be executed instead of displayed.

---

