---
title: "Login to access files via web browser"
date: 2011-03-01
forum: Server Platforms
---

### Post by Sqwirtle on 2011-03-01
I am currently new to all of this and not even sure if I am in the right place.

But I am currently running a server with OpenSSH.

When you go to my site's homepage, I have a link that redirects you to my files that I will be sharing.

They are currently access denied as I do not want the public to be able to download.

My question is how would I go about having a login box to pop up when they clink on the link on my homepage to access the files folder.

Currently I have accounts set up and it works when going through Filezilla with SFTP but I'm not sure how to give access to use via a web browser.

If you need any more information, I'd be glad to provide.

Any help is appreciated.

---

### Post by volkswagner on 2011-03-01
A simple solution may be to use Apache auth with an .htaccess file in root shared directory.

Other options may include ajaxexplorer, or setup a webdav server.

Sorry no links, posting from my phone.

---

