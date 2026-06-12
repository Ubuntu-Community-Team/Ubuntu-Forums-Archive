---
title: "Apache, DNS, subdomains, help!!!"
date: 2007-12-08
forum: Server Platforms
---

### Post by brooksbp on 2007-12-08
Hello, so I am developing a web application.  It is big enough that we need a developers version of the site... something to preview live without actually pushing to our production server... though, we would like to run this dev version on our production server just as a different virtual site under apache or something similar.

Right now, our site is [http://ncf.colorado.edu/](http://ncf.colorado.edu/)  So in essence our site is already a subdomain.  Is it possible to create something like [http://dev.ncf.colorado.edu/](http://dev.ncf.colorado.edu/) for our dev needs??  If so, what would be the best solution to do this, do we need to run our own DNS server? Virtual host?  If not do you guys recommend any other way of setting up a dev version of the site like stated above on the same box?

Thanks

---

### Post by gpredrag on 2007-12-09
In any case, if you would like to setup name based virtual host, you will have to set up appropriate address or alias record in DNS zone for  colorado.edu, whether it is just "test" (for i.e test.colorado.edu) or  dev.ncf for (dev.ncf.colorado.edu), which would create subdomain.
So you should ask/request/beg person responsible for maintaining colorado.edu zone (according to SOA record his/her email is [email]postmaster@boulder.colorado.edu[/email]. ) to set appropriate record for you.
You would need separate DNS server if you would like to be delegated responsibility for subdomain ncf.colorado.edu so you would be able to autonomously add records like anything.ncf.colorado.edu.

---

### Post by rsw686 on 2007-12-12
Yep contact the maintainer for colorado.edu. If they can I would go for ncfdev.colorado.edu for ease of use. I would not run your own DNS unless you have two separate DNS servers. In apache you create a virtual host 

<VirtualHost *:80>
ServerAdmin [email]webmaster@ncfdev.colorado.edu[/email]
DocumentRoot /locationtowebroot
ServerName ncfdev.colorado.edu
</VirtualHost>

---

