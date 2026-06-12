---
title: "Apache config for cgi-bin"
date: 2012-06-19
forum: Server Platforms
---

### Post by theDaveTheRave on 2012-06-19
I have a strange problem in configuring my apache2 httpd.

this is a brief version of my httpd.conf 

```
LoadModule cgi_module /usr/lib/apache2/modules/mod_cgi.so
LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so
ScriptAlias /cgi-bin/ /usr/local/apache2/cgi-bin

<Directory "/usr/local/apache2/cgi-bin">
	options ExecCGI
	SetHandler cgi-script
</Directory>
```

but I can't run scripts from this location on my disk?

I can copy the script to the "default" location of /usr/lib/cgi-bin and they work fine.

I know that the server is reading my httpd.conf file because if I put in errors (point to a non existant module) I get an error about being unable to locate the module when I do an
```
apache2ctl restart
```



In case you are wondering why I chose the location of /usr/local/apache2/cgi-bin it is what they use in the [apache CGI howto docs]("http://httpd.apache.org/docs/2.4/howto/cgi.html").

I've chmoded the file to 777, but don't know what else to try.

Any help is really appreciated.

David.

---

### Post by stmiller on 2012-06-20
Yeah the directory /usr/local/apache2/cgi-bin is unfortunately problematic. It's a permissions thing.

It is best to use /usr/lib/cgi-bin for Ubuntu or Debian.

---

### Post by theDaveTheRave on 2012-06-22
> **stmiller said:**
> Yeah the directory /usr/local/apache2/cgi-bin is unfortunately problematic. It's a permissions thing.

It is best to use /usr/lib/cgi-bin for Ubuntu or Debian.

OK cool.

Just to be sure I'll test it out on another direcotry.

If it is known to be a 'permissions thing' how come it isn't documented anywhere on the debian or ubuntu apache howtos (or at least not that I've noticed). I'm guessing it lies in being able to access the files in the drive or something? yes?

david

---

