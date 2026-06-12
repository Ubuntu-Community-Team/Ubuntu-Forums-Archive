---
title: "Filemanager online?"
date: 2005-11-20
forum: Server Platforms
---

### Post by Axios on 2005-11-20
Hi

I need some kind of system to exchange files with some people i study with.

At the moment we have a system with subversion running for latex and matlab code. But the windows user want to have something where they temporarily can put some files, .doc, .jpg, some documents that is temporarily.

I dont think that these files belong on the subversion system, I fear that those files will break the svn system.

The windows user would like it to be something like a web page, but the server we got is a virtuel private server, and with 32 mb of rams, it runs nicely with the subversion, but I dont know what will happen if I install an apache server with php.

Is there a smaller and simpler method for such a job than an apache server with a php-script?

Thanks

---

### Post by herrpoon on 2005-11-20
Hi, I can't think of anything else other a website, but to get around the memory issue you could try Lighthttpd ([http://www.lighttpd.net/)](http://www.lighttpd.net/)), haven't tried it myself but it's supposed to be a lot lighter (!) than apache and may work ok on your system.

---

