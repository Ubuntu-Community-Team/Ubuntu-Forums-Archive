---
title: "a2enmod userdir 404 error"
date: 2009-10-17
forum: Server Platforms
---

### Post by ShizzlePDX503 on 2009-10-17
I got apache2 installed from the repos and I enabled userdir but when I put a test index.html inside $HOME/public_html/ I get a 404 error not found

phpmyadmin is accessible from localhost and I get the "It Works!" message when I goto [http://localhost/](http://localhost/)

but when I goto [http://localhost/username/index.html](http://localhost/username/index.html) i get the 404

any ideas?

---

### Post by ShizzlePDX503 on 2009-10-17
I also use Rapache and this is in my userdir module configuration:
I am using the default site of /var/www 

```

<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>

```

---

### Post by Lars Noodén on 2009-10-18
> **ShizzlePDX503 said:**
> I got apache2 installed from the repos and I enabled userdir but when I put a test index.html inside $HOME/public_html/ I get a 404 error not found

phpmyadmin is accessible from localhost and I get the "It Works!" message when I goto [http://localhost/](http://localhost/)

but when I goto [http://localhost/username/index.html](http://localhost/username/index.html) i get the 404

any ideas?

You may be missing the tilde (~) in the URL.   So unless you set up some other options, you should be able to find the directory using this URL:
[http://localhost/](http://localhost/)**~**username/


The index.html goes without saying, unless the default for Indexes is changed for that directory.

---

### Post by ShizzlePDX503 on 2009-10-18
thanks that did the trick! I thought that the ~ was optional in the configuration. Thanks again!

---

