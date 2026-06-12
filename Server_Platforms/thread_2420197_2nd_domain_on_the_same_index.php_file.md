---
title: "2nd domain on the same index.php file"
date: 2019-06-01
forum: Server Platforms
---

### Post by Heeter on 2019-06-01
Hi All

I have added a 2nd domain to my webserver, domain1 has been working properly for the last couple of years. 

I currently use an index.php file to redirect domain1 http traffic directly to https immediately. 


Can I add domain2 to the same file to redirect to ""https://domain2.com"""?

If so, how will the index.php file output look like?

Regards

---

### Post by SeijiSensei on 2019-06-01
I'd take a different route.

Rather than redirect traffic through a script, I'd do it in the configuration file.  Do you have a separate configuration for domain1 in /etc/apache2/sites-available with a link to it from ../sites-enabled?

I'd create a separate configuration file for each domain.  For domain1, create /etc/apache2/sites-available/domain1.conf like this:
```

<VirtualHost *:80>
ServerName     www.domain1.name 
ServerAlias    domain1.name

Redirect / https://www.domain1.name
<VirtualHost>

<VirtualHost *:443>
ServerName   www.domain1.name
ServerAlias  domain1.name

DocumentRoot "/path/to/domain1/files"

[etc.]
</VirtualHost>

```

Then create a parallel configuration for domain2.  Put both in sites-available, then run

```

sudo a2ensite domain1
sudo a2ensite domain2

```

The code at the top of the configuration intercepts HTTP requests and redirects them to the HTTPS site.

You should read this if you haven't already: [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

---

### Post by Heeter on 2019-06-01
Wow Thank you so much SeijiSensei

Really appreciate it, it worked

I didn't know about the help.ubuntu docs, will read through them

Regards

---

### Post by SeijiSensei on 2019-06-01
Glad I could help!

---

### Post by Heeter on 2019-06-06
Hi 

My apologies about reupping a thread here, I do have one more question: a virtualhost sites-available file for a subdomain

going along how you mentioned to setup my other domain vhost files, wouldn't a subdomain vhost file look like this:

```

<VirtualHost *:80>
ServerName     subdomain.domain.name

Redirect / https://subdomain.domain.name
<VirtualHost>

<VirtualHost *:443>
ServerName    subdomain.domain.name

DocumentRoot "/path/to/subdomain/files"

[etc.]
</VirtualHost>

```

I think that I am doing something wrong, because during testing the browser goes to the root domain.

Regards

---

### Post by Heeter on 2019-06-06
Duh,

Actually I figured out my error,

Thank you!!!!!!

---

