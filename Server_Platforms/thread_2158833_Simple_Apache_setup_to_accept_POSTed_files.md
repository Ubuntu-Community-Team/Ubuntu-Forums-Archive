---
title: "Simple Apache setup to accept POSTed files"
date: 2013-06-30
forum: Server Platforms
---

### Post by maurtis on 2013-06-30
Hi all,

Noobiest of noob questions, but I have been searching and experimenting for days without success.  For a project I am working on, I just need to set up a local test server that can accept files sent via HTTP POST (reports are being sent automatically via POST, I just need to verify the reporting mechanism is working properly).  So I set up Apache on my Ubuntu 12.04 laptop but cannot seem to get much farther.

I assume that I need to set up a script (php or otherwise) to allow the server to accept the files?  Security is not an issue, this is all done on the local network.  Any apache gurus mind setting me straight?

I found some php code and the associated html to allow me to upload a file using a simple web page, which works fine, so I know the apache setup can actually receive files.  But whenever I use curl to POST a file I just get back the text of the index.html.

Please help?

Thanks!

---

### Post by SeijiSensei on 2013-07-01
If you use the upload handler in PHP, read this:

[http://php.net/manual/en/features.file-upload.php](http://php.net/manual/en/features.file-upload.php)

---

### Post by maurtis on 2013-07-08
> **SeijiSensei said:**
> If you use the upload handler in PHP, read this:

[http://php.net/manual/en/features.file-upload.php](http://php.net/manual/en/features.file-upload.php)

Thanks for the help, I appreciate it!  I ended up ditching trying to do it with PHP and went with Tomcat and a java servlet and was able to code it pretty quickly that way.

Thanks again!

---

### Post by SeijiSensei on 2013-07-09
You're welcome.  Not knowing Java, that wouldn't be an option for me!

HTTP POST is an annoying protocol for an application to employ because you have to code a POST handler somewhere.  I much prefer writing files at the OS level and moving them securely with rsync, OpenVPN, or sshfs.

---

