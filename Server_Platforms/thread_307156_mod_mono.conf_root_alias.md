---
title: "mod_mono.conf root alias"
date: 2006-11-26
forum: Server Platforms
---

### Post by gRoberts on 2006-11-26
Hi all,

I'm in need of some thinking help.

I was wondering if there is anyway to apply the mod_mono to the root directory (/var/www)

I tried adding 

```

Alias / "/var/www"
AddMonoApplications default "/:/var/www"
<Location />
SetHandler mono
</Location>

```

but when I reloaded apache I got:

```

gavin@EYCD:/etc/apache2$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server...                                   [Sun Nov 26 11:53:16 2006] [warn] The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Nov 26 11:53:18 2006] [warn] The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ ok ]
gavin@EYCD:/etc/apache2$ 


```

So then I tried using

```

Alias * "/var/www"
AddMonoApplications default "*:/var/www"
<Location *>
SetHandler mono
</Location>

```

and reload reported no errors but when I went to [http://localhost](http://localhost) I got 503 errors.

Is there ANYWAY to get mod_mono to parse the root directory without any errors?

The first example I gave works.

---

### Post by gRoberts on 2006-11-26
> **gRoberts said:**
> Hi all,

I'm in need of some thinking help.

I was wondering if there is anyway to apply the mod_mono to the root directory (/var/www)

I tried adding 

```

Alias / "/var/www"
AddMonoApplications default "/:/var/www"
<Location />
SetHandler mono
</Location>

```

but when I reloaded apache I got:

```

gavin@EYCD:/etc/apache2$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server...                                   [Sun Nov 26 11:53:16 2006] [warn] The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Nov 26 11:53:18 2006] [warn] The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ ok ]
gavin@EYCD:/etc/apache2$ 


```

So then I tried using

```

Alias * "/var/www"
AddMonoApplications default "*:/var/www"
<Location *>
SetHandler mono
</Location>

```

and reload reported no errors but when I went to [http://localhost](http://localhost) I got 503 errors.

Is there ANYWAY to get mod_mono to parse the root directory without any errors?

The first example I gave works.

Resolved::

I added


MonoApplications "/:/var/www"

<Location /var/www>
AddHandler mono .aspx .ascx .asax .ashx .config .cs .asmx
</Location>

to my httpd.conf

---

