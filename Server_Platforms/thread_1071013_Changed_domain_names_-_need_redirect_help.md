---
title: "Changed domain names - need redirect help"
date: 2009-02-15
forum: Server Platforms
---

### Post by R.Bucky on 2009-02-15
I changed my domain name from [http://buckyspalace.net](http://buckyspalace.net) to [http://buckycomputing.net]("http://buckycomputing.net"). I am hosting the site, but want users that still visit buckyspalace.net to be redirected to my site. What would be the most efficient method of accomplishing this redirect?

~Mark

---

### Post by sowelie on 2009-02-15
Change the index page on the old site to do a 301 redirect to the new site.  This way search engines will know the url has moved permanently.

---

### Post by R.Bucky on 2009-02-15
I changed all of my configuration files to read to my new domain. So, there really is not an index page for the old site. The old index page is now my new domain name. A 301 would not work from my vantage.

---

### Post by volkswagner on 2009-02-16
As long as the old site is still pointed to the same server IP address, you can use an .htaccess file in the root directory for the 301 redirect.

[http://www.webconfs.com/how-to-redirect-a-webpage.php](http://www.webconfs.com/how-to-redirect-a-webpage.php)

---

### Post by R.Bucky on 2009-02-16
Well, I am not sure what did it. However, a redirect is attached to my domain. Here is what I did. I went to my account at Network Solutions and added a CNAME to buckyspalace.net to point to my new domain buckycomputing.net and kept the IP address pointed as it was. 

You might verify this, but I used a proxy to shoot back to buckyspalace.net and it redirected to my new domain. Someone want to verify?

---

### Post by cpetercarter on 2009-02-16
Yes - a call to your old domain is redirected to your new one.

---

### Post by R.Bucky on 2009-02-16
Thank your very much. I guess CNAME works for this issue.

---

### Post by volkswagner on 2009-02-17
I have the following bookmarked for verification redirect is search engine friendly.

[http://www.webconfs.com/redirect-check.php](http://www.webconfs.com/redirect-check.php)

You pass!

---

### Post by Phlee on 2009-02-17
You could always use a meta tag:

```


<html><head>
  <meta http-equiv="Refresh" content="0; url=http://www.example.com/">
</head><body>
  <p>Please follow <a href="http://www.example.com/">link</a>!</p>
</body></html>


```

---

