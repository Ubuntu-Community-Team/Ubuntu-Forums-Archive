---
title: "VirtualHost, doesn´t work when use www"
date: 2011-05-19
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-05-19
Hi everyone,

I´ve made a site on my Ubuntu server and link the folder where it is with VirtualHost.
The problem is, when i place mypage.com works, when try [www.mypage.com]("http://www.mypage.com") goes to the apache "It Works" page.

Any idea?

Thanks in advance!! :P

---

### Post by tapi0n on 2011-05-19
isn't that a dns problem?

---

### Post by volkswagner on 2011-05-19
If you are getting "It Works" your DNS is working.

You either need to disable the default site:

```
sudo a2dissite default
```

Or add the server alias directive to mypage.com virtual host file.

```
ServerAlias www.mypage.com 
``` 

You will then need to restart apache for either solution.

---

### Post by acastrolorenzo on 2011-05-19
Thanks, but, I have several domains on the same server. 

One of them works well with WWW and without. The others are the problematics with WWW.

I´ve the same VirtualHost file, changing the directory path obviously.
And the same DNS configuration.

So, I think it should be other problem. Maybe htaccess?, what do you think?.

Thanks a lot again

---

### Post by volkswagner on 2011-05-19
Without seeing your vhost file, I can't really say.

Perhaps you can post your vhost config for others to see if there is an error, you are not seeing.

Are you using .htaccess or any rewrite rules?

Do you have ServerAlias for WWW?

---

