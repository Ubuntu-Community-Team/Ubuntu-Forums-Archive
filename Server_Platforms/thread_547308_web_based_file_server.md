---
title: "web based file server"
date: 2007-09-09
forum: Server Platforms
---

### Post by BostonBrother on 2007-09-09
I'm looking for a server that I can set up individual accounts on and have them accessed via a web-browser where users can easily upload and download files via their web-browser.  I've read severals post about webmin, but it looks  like a program that manages all aspects of a server.  I don't want to users to be able to do anything but upload and download and manage their files within their own accounts without having to know linux commands (I need a simple interface).  Can webmin do what I need?  Is their anything else that someone might recommend?  Any ideas?

---

### Post by scxtt on 2007-09-09
i've seen python scripts that use php to render webpages and provide an upload form where users can browse to a file on their PC and upload it ... i used it for a while, worked quite well ...

---

### Post by koenn on 2007-09-10
sounds like the "attachment" feature in webmail and forums : these also let you browse your local fs and upload files. 
Look at the source of those pages. eg for the ubuntu forums attachments, you'll see a html form, some javascript, and a call to a php script. The latter is going to be the hard one to figure out because normally you never get to see it unless there's a wayto get it from the server without it being rendered as html. 
I tried "wget http://ubuntuforums.org/newattachment.php" but that didn't work :(

---

### Post by joewilliams on 2007-09-11
There is a project [[COLOR="Blue"]here[/COLOR] ](http://extplorer.sourceforge.net/)which began as a component for the Joomla! CMS but which apparently can be used as a stand-alone file manager application.  I don't know much about it's use this way but it is an excellent file manager for Joomla!. I'm also interested in using it on my small office intranet  webserver.  Perhaps it would work for you...

-Joe

---

### Post by Brazen on 2007-09-11
Well, SSLBridge [http://www.sslbridge.com/](http://www.sslbridge.com/) will do exactly what you are wanting, though personally, I would use webdav on Apache (with https) to do basically this same thing.  Probably even before webDav though, I would use scp or ftp (depending on how concerned I am on securing the information, scp=verysecure ftp=notsecure)

---

### Post by bluemarvel on 2007-11-13
It sounds like you would like phpFileNavigator. It's open source and I'm running it successfully on my Ubuntu LAMP server.

[http://pfn.sourceforge.net/](http://pfn.sourceforge.net/)

---

### Post by HermanAB on 2007-11-13
Opendocman works well.  If you want something simpler though, use an anonymous FTP server and link to it from a web page.

---

