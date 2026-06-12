---
title: "Apache redirect errors"
date: 2007-09-22
forum: Server Platforms
---

### Post by antisho on 2007-09-22
I have an Apache server on my comp. I need to make some files redirect to some other files. So, I put in a .htaccess, with

Redirect 301 /path/to/file /path/to/other/file

But, it doesn't work. Not thinking to check the error log, I think, maybe it has to go in the main apache2.conf. So I put it in a <Directory> there.

Apache doesn't work, and gives me an error:
```
Syntax error on line 694 of /etc/apache2/apache2.conf:
Redirect to non-URL
```

Change it to Redirect Permanent, same problem. Now, I know why this is occurring. But, because I might for example be on the computer and go to localhost or something, or be on another computer on the network, I don't want to use a URL, but rather a path.

So, following a friend's suggestion, I change it to Alias. It gives me
```
Syntax error on line 694 of /etc/apache2/apache2.conf:
Alias not allowed here
```

So I Google it. Someone says, it has to go in httpd.conf, but that gives the same error, for both Redirect and Alias. The rest of the first results page doesn't help.

Does anyone have a solution?

---

### Post by jtc on 2007-09-23
The destination path in a redirect is to be a full url. How about the following?

```
Redirect 301 /path/to/file http://domain.tld/path/to/other/file
```

[http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect)

---

### Post by antisho on 2007-09-23
> **jtc said:**
> The destination path in a redirect is to be a full url. How about the following?

```
Redirect 301 /path/to/file http://domain.tld/path/to/other/file
```

[http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect)
As I said, I want to use a path, rather than a full URL.

---

### Post by antisho on 2007-09-25
Bump... can anyone help?

---

### Post by MatthewMetzger on 2008-02-14
I have exactly the same problem. I'm looking for the answer but haven't found it yet.

How do I turn on Alias? I'm getting the same message in the apache logs "Alias not allowed here". I'd like to use Alias so that I can use a path instead of a url.

thanks for any help you can give.

Matthew

---

### Post by faulkes on 2008-02-14
As stated, redirection has to be a full URL, I'm not aware of any other way to use redirect for path to path.

One option may be to symlink and allow FollowSymlinks.

Faulkes

---

### Post by MatthewMetzger on 2008-02-14
Faulkes,

thanks so much for the quick response. I immediately tried your suggestion. It works, but not in the way that I want it to.

It works like a url rewrite directive. I would like it to forward a request for /current.pdf to /dated.pdf so that the link is always the same, but when requested it forwards to the schedule for the current week (I also want it so the downloaded file contains the date in the filename, even though the initially requestion file is always the same - current.pdf)

I guess that I really don't want the Alias function, I want the Redirect function with a path instead of a url.

the ln -s trick is useful and I may end up using it.

thanks,

Matthew

---

