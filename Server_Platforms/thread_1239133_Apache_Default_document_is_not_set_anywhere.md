---
title: "Apache Default document is not set anywhere?"
date: 2009-08-13
forum: Server Platforms
---

### Post by jezjones on 2009-08-13
er ...

---

### Post by bartos on 2009-08-13
Changing httpd.conf in /etc/apache2/.
You can set your webpages in any directory even /home/you/.look for <Directory "/home/<your user name here>/public_html/">

---

### Post by cdenley on 2009-08-13
You mean DocumentIndex, where you set whether index.php, index.html, etc. are used for requests to "/" or "/path/to/mydir/"?

```

nano /etc/apache2/mods-available/dir.conf

```

Also, you are not supposed to use httpd.conf in ubuntu. It will work, but it is not the standard way of doing things, and will make it difficult for us to help you in the future.

---

### Post by CaptConan on 2010-06-01
Thanks for posting, every other place was pointing to httpd.conf
Good to know...

---

### Post by Vegan on 2010-06-01
> **cdenley said:**
> You mean DocumentIndex, where you set whether index.php, index.html, etc. are used for requests to "/" or "/path/to/mydir/"?

```

nano /etc/apache2/mods-available/dir.conf

```

Also, you are not supposed to use httpd.conf in ubuntu. It will work, but it is not the standard way of doing things, and will make it difficult for us to help you in the future.

Actually the httpd.conf is meant for users to put configuration options in.

I use it all the time for vhosts.

---

### Post by cdenley on 2010-06-02
> **Vegan said:**
> Actually the httpd.conf is meant for users to put configuration options in.

I use it all the time for vhosts.

Actually, creating a new file such as /etc/apache2/conf.d/mysettings.local is a better way to add global configuration options if there isn't already a more appropriate place. Configuration options within a vhost belong in that vhost's configuration file in /etc/apache2/sites-available.

The file httpd.conf is included before /etc/apache2/ports.conf, /etc/apache2/conf.d/, and /etc/apache2/sites-enabled/, so anything you define in httpd.conf may be overridden.

/usr/share/doc/apache2.2-common/README.Debian.gz
```

**conf.d/**

	Files in this directory are included by this line in
	apache2.conf:

	# Include generic snippets of statements
	Include /etc/apache2/conf.d

	[B]This is a good place to add additional configuration
	directives. Packages should not use configuration
	files that start with 'local-' or end with '.local'.
	The local administrator can use these filenames to make
	sure that there are no conflicts with files provided by
	packages.[/B]

	If the local administrator is not comfortable with packages
	activating their config files by default, it is possible
	to change the 'Include /etc/apache2/conf.d/' in apache2.conf
	into 'Include /etc/apache2/conf.d.enabled/' and create that
	directory. He can then put symlinks to the files in conf.d
	which he wants to enable into conf.d.enabled.

[B]httpd.conf

	Empty file.[/B]

```

In an older release a few years ago, the default httpd.conf file actually contained a comment that said "This is here for backwards compatibility reasons".

---

