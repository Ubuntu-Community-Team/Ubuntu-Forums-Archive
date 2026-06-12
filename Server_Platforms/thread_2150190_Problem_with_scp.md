---
title: "Problem with scp"
date: 2013-05-31
forum: Server Platforms
---

### Post by Mariane on 2013-05-31
Hi, 

I copied a zip file (to install prestashop) using:
```

scp prestashop_1.5.4.1.zip administrator@mysite.com:

```

It took a while then said it had copied 17M of data. Then the computer hanged for 2 or 3 minutes, before giving me the command prompt again. 

Then I went to the /var/www directory on the server and looked for the file. It was not there. 

What should I do, please?

---

### Post by Mariane on 2013-05-31
Ooops, I'm so sorry, it was in ./home/administrator/prestashop_1.5.4.1.zip

---

### Post by rubylaser on 2013-05-31
By default, the way you scp'd that zipfile would have put the files in the admin user's home directory (likely /home/administrator) not in /var/www.  If you want to have the file go to /var/www you can either ssh in and move the zip file to the appropriate location.
```

mv /home/administrator/prestashop_1.5.4.1.zip /var/www/[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
```

Or, you can scp it over properly like this.
```

scp prestashop_1.5.4.1.zip administrator@mysite.com:/var/www/

```

This requires that the administrator user has the privileges to write to /var/www.

---

