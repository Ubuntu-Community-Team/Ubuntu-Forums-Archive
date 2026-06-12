---
title: "Secure web remote filesystem access"
date: 2010-07-24
forum: Server Platforms
---

### Post by YesWeCan on 2010-07-24
Hi. I would like to set up my Ubuntu 10.04 server so that I can securely browse its filesystem, or a subset of its filesystem, from a remote web browser over the public internet. I would like to be able to download and upload files. I assume it would run under https and require a password login for access. My server has Apache2 installed and SSL for Apache2.

I would be grateful for pointers to the necessary ingredients.
Thanks. :)

---

### Post by Ryan Dwyer on 2010-07-24
Is there any reason why you don't want to use FTP?

---

### Post by YesWeCan on 2010-07-24
Please elaborate.

---

### Post by drdos2006 on 2010-07-24
Yes, use Webmin. Here is a Howto I found very useful.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards

---

### Post by Ryan Dwyer on 2010-07-24
> **YesWeCan said:**
> Please elaborate.

You install FTP server software such as Pure FTP (sudo apt-get install pure-ftpd). Then on your client, you install an FTP client like FileZilla. You put in your server's hostname or IP as well as your username and password and then you can browse the files on your server and transfer them.

---

### Post by YesWeCan on 2010-07-25
@drdos2006, Thanks I'll take a look at that guide.

@Ryan Dwyer, That would work. I would like a system that does not require any software to be installed on the client. I would like to be able to use any web-attached client type; not necessarily owned by me. Since web browsers are ubiquitous that is what I thought I would use.

---

### Post by YesWeCan on 2010-07-25
That Webmin howto: 614 pages with no table of contents and no index. I shall be adding this to my "examples of user hostility in linux" Hall of Fame. :roll: For f's sake.
My impression of Webmin and its home page is that it is overkill and too complicated and too far up its own interface for me to make practical use of it within a reasonable timescale.

All I want is to access my servers filesystem using a web browser, and upload and download files, make directories and ordinary file operations. A web-based nautilus if you will. How hard can this be? (don't answer that).

---

### Post by terran698 on 2010-07-25
i also would like to know because i am enrolled in ivy tech for computer information tech and i cannot install programs on the schools computers but would like to be able to browse a home computer in case the flash drive bugs out (sometimes the schools av sees the sticks as a virus and wipes them.... damn norton)

---

### Post by cadriel on 2010-07-25
I would have thought WebDAV would be the way to go here.

You'll need Apache installed on your machine to accomplish this. Then all you need to do is setup a WebDAV site using Apache. You can then share a folder tree using WebDAV and access it through your browser.

Do a google on WebDAV & Apache.

--
Craig.

---

### Post by cadriel on 2010-07-25
An article to get WebDAV running. It should be mostly relevant for 10.04 too.

[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10)

Windows also has built in support for WebDAV - so you can essentially connect to it as a shared folder in Explorer for example.

--
Craig.

---

### Post by BenWuan on 2010-08-03
I totally disagree @ Yeswecan
Thank you @ drdos2006 for your advice
I found all [COLOR=red]**614 pages**[/COLOR] to be super helpful ! Thanks again, also this forum is the best, has taught me so much, thanks @ ubuntuforums.org !
~Ben

---

### Post by ahbart on 2010-08-03
Have a look at usermin then. [This is a link]("http://www.webmin.com/usermin.html")

---

