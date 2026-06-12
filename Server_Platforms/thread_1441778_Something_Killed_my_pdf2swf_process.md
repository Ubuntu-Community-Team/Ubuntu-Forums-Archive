---
title: "Something Killed my pdf2swf process ?"
date: 2010-03-29
forum: Server Platforms
---

### Post by mech7 on 2010-03-29
I am running this command:

> serveradmin@lamp:/var/www/flipbook/protected$ php console.php convertpdf 32
pdf2swf -q -t -T 9 -G -p 1 -f /var/www/flipbook/public/upload/books/test/test.pdf /var/www/flipbook/public/upload/books/test/images/zoom/page_1.swf
Killed

Why does it gives back killed? It is a pretty heavy process and takes about 8 minutes. I do end up with a file which seems to work..

But then if i do:

> serveradmin@lamp:/var/www/flipbook/protected$ swfrender /var/www/flipbook/public/upload/books/test/images/zoom/page_1.swf -o /var/www/flipbook/public/upload/books/test/images/page_1.jpg
Killed


And no output :o Does anybody know why this process gets killed?

---

