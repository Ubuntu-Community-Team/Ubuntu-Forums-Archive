---
title: "PHP Problem"
date: 2006-04-07
forum: Server Platforms
---

### Post by guttley on 2006-04-07
Hi,

Ive recently upgraded my dev server to mysql 5, php 5 and apache 2.2.0 
all compiled from source.

However i have a small problem that im not sure how to fix.
Basically if i have a php page ie index.php this works fine however if i append query name/value pairs ie index.php?page=main i get a download popup box (firefox) asking me to download index.php.
im sure that apache is not recognising this as a php file now, but im unsure what settings need to change to rectify this.

Any help appreciated.

---

### Post by dermotti on 2006-04-07
Are you sure your index.php isnt just "appearing" to work fine? It might just be a cached copy. I reccomend you create a page called yourdomain.com/phpinfo.php

with just one line in it, **<? phpinfo(); ?>** and see if that works properly.

Make sure the lines are uncommented in your http.conf also, and restart apache

# AddType application/x-httpd-php .php
# AddType application/x-httpd-php-source .phps

change to


 AddType application/x-httpd-php .php
 AddType application/x-httpd-php-source .phps

---

### Post by guttley on 2006-04-07
Hi,

Yes i already tried the phpinfo to check it wasnt cached and the httpd.conf file is setup for php.

Thanks for the reply.

---

### Post by MJN on 2006-04-07
I'm guessing here but could the appending of the query name/values be changing the apparent file extension thus the *AddType* directive is not recognising that it's a php file?

If so, I would expect the mime_magic module to mitigate this as it will recognise the php file by its contents as opposed to the extension.

As I said, just a guess however in the absence of anything stronger I thought it might be useful. Having said that, one would expect this to be a common issue if it were the case and one would also expect that the ? character serves to act as a delimiter anyway, so I won't be betting any money that I'm right.... ;)

Mathew

---

### Post by guttley on 2006-04-08
Hi,

Thanks for that.

What i have done is removed the AddType directive and interestingly enough if i say try phpinfo.php ill get <? phpinfo() ?> returned as text (as you would expect) however i try phpinfo.php?aVal=1 it still outputs the text, again this is expected.

if i then try my index.php again its as you would expect and outputs the text.
however if i try index.php?page=login for example i then get the download prompt. i think ill have to take a long look at what this is doing but, iirc it just includes the other php files with a header/footer.

---

### Post by guttley on 2006-04-08
Got it!!

Just needed to clear firefox's cache!

---

