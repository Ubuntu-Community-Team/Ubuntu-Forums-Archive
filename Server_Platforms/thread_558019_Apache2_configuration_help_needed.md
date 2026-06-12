---
title: "Apache2 configuration help needed"
date: 2007-09-23
forum: Server Platforms
---

### Post by DGentry on 2007-09-23
I followed and installed the LAMP setup directions earlier. All seems to be pretty well except when I enter [http://localhost/](http://localhost/) as the url.

I get a webpage that says Index of /
Then under that is NAME    Last Modified     Size  Discription
There's a folder that says apache2-default 20 nove-2004-12:16 -
test.php 22-sept-2007 15:32 21

If I click on the apache2-default I get a page that says It Works?

I don't what in the world I'm doing but I seem to think this may be off a bit.

I can't really find any documentation on Apache2 configuration for Ubuntu.

When it's all said and done I'd like to create some webpages that linked to Mysql.

but for right now I'd be happy to create some testing webpages on my PC and see what I can do with some practice and learning.

Any help would be surely appreciated.

Thanks
Doug

---

### Post by James79 on 2007-09-23
Everything is working fine. The default page is too displayed from /var/www. Have a look in that directory, it should be identical to what it is you're seeing in your browser.

This is also where you would put your website files.

---

### Post by DGentry on 2007-09-23
Cool, So all I'd better do is just rename that one to indexold.html and then whatever I create name it index.html.

I'll see what I can get into now.

Thanks
Doug

At one time I had done this in Suse 10 and had to go into the apache conf files and redo a bunch of stuff. I was just leery that this was "too" easy?

---

### Post by James79 on 2007-09-24
Go ahead and create a file called /var/www/index.html and put some text in there, then refresh your browser.

I think you'll be pleasantly surprised ;)

---

