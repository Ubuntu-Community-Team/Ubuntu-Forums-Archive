---
title: "Apache2 and Index.html and Index.php"
date: 2008-12-15
forum: Server Platforms
---

### Post by ericinwisconsin on 2008-12-15
I'm running Ubuntu 8.04. Here's my odd little issue...

I'm running Apache2 on my home computer for my intranet. The server displays index.php just fine, but any directory with index.html gives me a 403 error.

My /etc/apache2/mods-enabled/dir.conf looks like this:

```

<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

```
A search with

```

find . -exec grep "index.php" '{}' \; -print

```
verifies that the only places "index.php" appears in my /etc/apache2 directory and subdirectories is in mods-available/dir.conf and mods-enabled/dir.conf.

I have verified, with a phpinfo.php file, that mod_dir is running. I haven't tested index.cgi or index.pl, as cgi scripts are not enabled for my main web directory (/var/www).

Any idea why the server likes index.php but not index.html?

---

### Post by MJN on 2008-12-15
Are the permissions okay on the index.html file(s)?
 
Mathew

---

### Post by wizard10000 on 2008-12-15
The 403 error hints at a permissions issue.  Are you sure there isn't a conflicting instruction in httpd.conf?

---

### Post by ericinwisconsin on 2008-12-15
Yep, the permissions are 644, which is the same for both index.html and index.php files.

My httpd.conf file is there, but it's blank.

---

### Post by Coreigh on 2008-12-15
Do you have index.html defined as a usable index file in httpd.conf?

If you type the full URL with the index.html does it display then?

i.e. - "http://servername/directory/index.html"

In my /etc/apache2/httpd.conf there is a line like this:
> DirectoryIndex  index.html index.htm index.php

It defines what default pages are available and in what order to show them if two or more exist in a directory.

---

### Post by ericinwisconsin on 2008-12-15
Yep, the permissions are 644, which is the same for both index.html and index.php files.

My httpd.conf file is there, but it's blank.

---

### Post by MJN on 2008-12-15
Ownerships too?

As Coreigh said, can it be reached directly?

Does the error log say anything?

We could also do with seeing your config (site specific, and apache2.conf if changed)

Mathew

---

### Post by Coreigh on 2008-12-15
I always forget about my log files.

located in /var/log/apache2 there is a a series of files for each access and error logs. They can tell you what is being denied.

---

### Post by ericinwisconsin on 2008-12-15
Here's the only real error from my error.log file:

```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

Not related, I'm sure.

Wow, my config files? All of them? Rather than do that, let me say that it's a standard Kubuntu 8.04 installation and the only change I've made to Apache so far is to add a virtual host in the site-enabled/000-default file, so that I can access the server across the Internet (without having to worry about my ISP changing the IP address). Here are the lines I added:

```

<VirtualHost *>
   DocumentRoot /var/www/websites/mydomain.xxx.org
   ServerName mydomain.xxx.org
</VirtualHost>

```

---

### Post by ericinwisconsin on 2008-12-15
> **Coreigh said:**
> Do you have index.html defined as a usable index file in httpd.conf?

If you type the full URL with the index.html does it display then?

i.e. - "http://servername/directory/index.html"

In my /etc/apache2/httpd.conf there is a line like this:


It defines what default pages are available and in what order to show them if two or more exist in a directory.

Nope, it still doesn't process the html file properly.

---

### Post by MJN on 2008-12-15
So nothing appears in the error log when the user receives a 403 error? What about the access log?

Post the ls -l output of an affected directory.

Come on Eric, your laziness is really not helping solve your problem.

Mathew

---

### Post by MJN on 2008-12-15
Just a thought, make sure your error log really is active by requesting a URL you know not to exist. Does it get logged?

Mathew

---

### Post by Coreigh on 2008-12-15
Also what is the exact error message? You said it was a 403 but which one, can you post the exact message?

---

