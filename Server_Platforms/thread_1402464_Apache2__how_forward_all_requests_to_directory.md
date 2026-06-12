---
title: "Apache2 : how forward all requests to directory ?"
date: 2010-02-09
forum: Server Platforms
---

### Post by naspar on 2010-02-09
Hi All,

i have a small question which is making me mad :)

i have a web site and i need to forward all requests to the same page. Basically i would like to show a maintenance page while we are working with our database behind the application and in the meantime i would like to redirect all url in the root directory as following :

[http://www.mysite.com/login](http://www.mysite.com/login)  => [http://www.mysite.com/maintenance.html](http://www.mysite.com/maintenance.html)

[http://www.mysite.com/product](http://www.mysite.com/product)  => [http://www.mysite.com/maintenance.html](http://www.mysite.com/maintenance.html)

[http://www.mysite.com/company](http://www.mysite.com/company)  => [http://www.mysite.com/maintenance.html](http://www.mysite.com/maintenance.html)

[http://www.mysite.com/contact](http://www.mysite.com/contact)  => [http://www.mysite.com/maintenance.html](http://www.mysite.com/maintenance.html)

i tried to perform the action using mod_rewrite in this manner :

```


        RewriteEngine On
        RewriteRule . [http://www.mysite.com](http://www.mysite.com) [L]

        RewriteLog /var/log/apache2/maint/rewrite.log

        RewriteLogLevel 9

        DocumentRoot /var/www/maintenance/

```

but unfortunately i et the following error in goog chrome :

```

This webpage has a redirect loop.

The webpage at http://www.mysite.com/ has resulted in too many redirects. Clearing your cookies for this site or allowing third-party cookies may fix the problem. If not, it is possibly a server configuration issue and not a problem with your computer.

```

does anybody knows how to fix the problem ?

thank you so much

N

---

### Post by mushwars on 2010-02-09
what I&#12288;would do is change your document root in your conifg file, then have an .htaccess file ONLY&#12288;in that folder that will have a 404 redirect to maintenance.html

---

### Post by naspar on 2010-02-09
hi mushwars,
thanks for answering ..hmmm.. i dont understand very well .. do you think the .htaccess wil handle all address after the main url (/login,/support,/etc,/others) ?

how would you make the redirection ?
Do you have some example ? 

i was wondering if is possible to do everything in the Virtual Host config .. i have full access to the server and in the /etc/Apache2 directory as well

thank you

N

---

