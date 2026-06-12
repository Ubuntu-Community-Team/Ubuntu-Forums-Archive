---
title: "How to change the domain of website"
date: 2020-05-02
forum: The Cafe
---

### Post by satimis on 2020-05-02
Hi all,

Would it be possible to change the name of a subdomain website?

Say;
Running subdomain of the website - aaa.domain1.com

To be changed to;
aaa.domain2.com

If possible please advise HOW

Thanks

Regards
satimis

---

### Post by Hwæt on 2020-05-02
If we're talking external domains, it would require you to purchase domain2.com.

---

### Post by satimis on 2020-05-02
> **Hwæt said:**
> If we're talking external domains, it would require you to purchase domain2.com.
Hi,

Both domain1.com and domain2.com are owned by me.

Regards

---

### Post by sdsurfer on 2020-05-04
Presuming Linux based hosting with mod_rewrite enabled. Other server types have similar mechanisms.

If you just want to dump the whole schlamozzle over to domain 2, you can do this in your hosting by setting up domain 1 as an alias of domain 2. That has the same potential flaws as mentioned below. You may have to disable domain1 for it to all work, and wait for the DNS servers to propagate.

Otherwise use mod_rewrite: add a 301 permanent mod rewrite rule for the entire domain 1 to domain 2.

Both of the above will redirect all requests to the main page of domain 2. if domain 1 has any pages in the SERPS (and it is PAGES that rank, not WEB SITES) and you have any intent of maintaining rankings, it gets a little more complicated.

The way I would (hope to) set it up is if the pages on site 2 perfectly mirror site 1, your rewrite rule would be (paraphrased) domain1/(.*) domain2/$1 [R-301, L]. That is, any request for domain1/page1.html will be redirected to domain2/page1.html, and so on.

The 301 is important. It tells search engines this is permanently redirected, don't lose me! L means last rule to process (so, if you have a bunch of rewrite rules, you can bail and not process any further for this request, which is both efficient and avoids unexpected redirects.)

If that is not the case (and very often so,) you will have to go through domain 1, page by page, locate an appropriate redirect for each page on domain 2, and build a rewrite rule for it. If some of them are dynamic, as in a shopping cart with query strings in the URL's, it can get more complex but . . . . nothing is impossible. :-)

The way you would test your rules is to set up domain 1 in a local Apache server and hit all the links affected.


[https://httpd.apache.org/docs/2.4/rewrite/remapping.html](https://httpd.apache.org/docs/2.4/rewrite/remapping.html)

---

### Post by EuclideanCoffee on 2020-05-04
If you own the DNS record domain1 and domain2, then simply change the A/AAA value of domain2 to the same IP as domain1.

After you've done this, set up your virtual tables to point to the new address.

In [http://etc/apache2/sites-available/:](http://etc/apache2/sites-available/:)

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
ServerName example.com 
ServerAlias www.example.com
    DocumentRoot /var/www/html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

Finally activate it.

[COLOR=#545454][FONT=Consolas]sudo a2ensite [/FONT][/COLOR][COLOR=#545454][FONT=Consolas]example.com[/FONT][/COLOR][COLOR=#545454][FONT=Consolas].conf[/FONT][/COLOR]

---

