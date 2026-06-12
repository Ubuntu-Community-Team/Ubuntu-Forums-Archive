---
title: "VirtualHost wildcard?"
date: 2005-08-26
forum: Server Platforms
---

### Post by invalid on 2005-08-26
Maybe someone can help me out..
I am no apache expert, and I am having some trouble.

I have a virtualhost set up that looks like this:

```
DocumentRoot /var/www/test         
ServerName *.test.mydomain.net      
<Directory "/var/www/test">
 allow from all                       
 Options +Indexes             
</Directory>
```

If it does not make sense (which apache seems to think it doesn't), here is what I am trying to do..

I want all addresses that match *.test.mydomain.net to goto /var/www/test
example: abc.test.mydomain.net 123.test.mydomain.net etc..

Now when I try a location like this - it does not follow this virtualhost, and goes straight to directoy of my default (mydomain.net (/var/www)).

Is there a proper way to achieve this?
I hope this made some sense..

Thanks,
Cb

---

### Post by tonym on 2005-08-27
i don't think you can have a wildcard on Servername.  Try this:

ServerName test.mydomain.net
ServerAlias *.test.mydomain.net

Regards

Tony

---

