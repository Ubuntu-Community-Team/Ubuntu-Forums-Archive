---
title: "Configure Apache to parse php in rtf files"
date: 2008-07-02
forum: Server Platforms
---

### Post by richard42 on 2008-07-02
Good morning/afternoon/evening,

I have some rtf files on my web server.  When I download them through a browser, my browser correctly recognises them as rtf files and runs them in a word processor.

Now I want to be able to put some php in the rtf file, and have apache parse it before it is downloaded.  For example:

<? echo "Hello World" ?>

within the body of the rtf file would parse to "Hello World" in the body of the downloaded rtf file when viewed through a word processor.

What configuration changes would I need to make to Apache in order to have the rtf file run through php, but still be correctly recognised as an rtf file by the browser?

Many thanks,
Richard

---

### Post by richard42 on 2008-07-02
I successfully resolved this myself.

In the file /etc/apache2/mods-available/php5.conf I replaced this line:
```
AddType application/x-httpd-php .php .phtml .php3
```

with:

```
AddType application/x-httpd-php .php .phtml .php3 .rtf
```

I then realised that I have to include this line at the beginning of the rtf document to ensure that it's understood correctly by the browser.
```
<?php Header('Content-Type: application/rtf')?>
```

If anyone knows how to automatically insert the text in front of all rtf files through the apache configuration then that would also be great.

I hope this is useful for someone else.

Thanks,
Richard

---

