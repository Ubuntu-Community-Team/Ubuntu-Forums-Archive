---
title: "Apache2 + PHP5 and Fileuploads via POST &gt; 1GB"
date: 2010-02-22
forum: Server Platforms
---

### Post by cyberio on 2010-02-22
Hi all !

my server :
ubuntu jaunty 9.04 32bits
apache2 2.2.11-2ubuntu2.5
php5 5.2.6.dfsg.1-3ubuntu4.5

I have a problem uploading large files :
from 0 to 1 048 576 000 octet (1000mega) : OK
greater... KO... i mean even no file uploading temporaly in /tmp

I have tried using "jyraphe" or "openupload" in the server part and from mozilla or IE in the client part.... always the same thing...

php.ini :
post_max_size = 5G
upload_max_filesize = 5G

I even set "LimitRequestBody 10000000000" in /etc/apache2/sites-available/default thinking the default value (not set OR 0) didnt work but...

ALWAYS THE SAME THING grrrrrr !

Please help me (even the openupload dev is interrested in the answer)

CYBERIO

---

### Post by jahservant on 2010-02-22
Perhaps there is an apache setting???  Are you getting any timeout messages (if it's more than your default setting [usu. 30 seconds] then the script will time out).
Try adding:
[PHP]
<?php
ini_set('max_execution_time',0);
?>[/PHP]or

[PHP]
<?php
set_time_limit(0);
?>[/PHP]to the top of your PHP script.

I would also recommend NOT using PHP for this.  If you are uploading files much more than a few MB in size (total), it takes time to upload, and from the user's perspective they are sitting around watching an "uploading" wheel spin for (possibly) minutes - maybe even more.

Try Perl.  You can split the file up and upload it it fragments (a few hundred KB at a time) and then reconstruct it on the server. Google has a good selection of examples:

[http://www.google.com/search?q=perl+ajax+file+upload&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=perl+ajax+file+upload&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

hope that helps...

---

### Post by cyberio on 2010-03-01
max_execution_time ?

Well this seems more an hard limit to me... remember what i have said :
"even no file uploading temporaly in /tmp" !!

less than 1go : file immediatly uploading temporaly in /tmp
more... nothing !!

??? im getting crazy with this thing lol

but the perl test could be a way to separate php problem from apache ones... can u give me a link to a simple scipt for uploading via perl ? i tried your google link but im not a perl expert....

---

### Post by cyberio on 2010-03-01
news !!

testing with a simple perl script i CAN upload files more than 1Go...

I am i right if i say that this means that PHP is the guilty apache extension for this bug ?

---

### Post by cyberio on 2010-03-01
RESOLVED !

In fact it s a 2Go 32 bit hard limit

Setting those parameters to 5Go while only make php to go to default value... 1Go...

grrrr

---

