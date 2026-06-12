---
title: "Apache Homepages Server???"
date: 2007-06-19
forum: Server Platforms
---

### Post by 919Guy on 2007-06-19
Let me preface this by saying that this may belong in the "newbie" forum, and if so, mods, please feel free to move it.

Anyhow, I'd like to get a LAMP server up and running for an HTML class I'm teaching here at school.  (Got this done as well) There's a couple initial requirements, and then one that may be a little ways out there (as far as time goes).  

[INDENT]1.  First of all, I'd like to have dynamically created virtual hosts for each student in the class (i.e. www.<studentname>.<domain>.com.  I *think* I've got this figured out.  I'm not totally opposed to going the www.<domain>.com/~<studentname> route though.....

2.  Secondly, obviously I'd like to have an FTP server running on the same box that the students could upload their pages to.  

3.  Finally, and this is the wish, set up some type of reverse proxy (squid) on another box to allow these pages to be accessed externally by whatever the end result of #1 is.  

Also, to pull all this together, is webmin (with the appropriate plugins) the easiest way to manage this?[/INDENT]
I view it as basically an ISP-ish setup minus the DNS, e-mail, etc.  Any direction that can be thrown my way will be more than appreciated.

---

### Post by dfreer on 2007-06-19
Here's some steps I'd follow.

(1) install LAMP from a server CD
(2) make sure apache is working correctly
(3) I'd create a directory for each student, like /var/www/jsmith and /var/www/achapman
Then create a new file in /etc/apache2/sites-available/, for each user name (so /etc/apache2/sites-available/jsmith for example). Set up your virtual host information in there, makiing each documentroot for each user mapped to their folder on /var/www/ and the servername set to username.testsite.com or whatever. you can also define a seperate errorlog for each student this way (so you can see which site is messing up and why). make sure to reload the server afterwards.
(4) I can't help you with the FTP server, I use sftp and ssh mostly.
(5) reverse proxy might be a bit of an overkill, you could make a simply DNS server and map all the testsite.com to the web server's IP. Then, when your users type [http://username.testsite.com](http://username.testsite.com) from any machine on the LAN, the request would go to the DNS server, which would point it to testsite.com, and then the virtualhosts will kick in.


no need for webmin unless you can't handle the CLI very well. good luck and let us know if you have any questions, I left things a little vague. but it is a good game plan :)

---

### Post by Frosty Cold Drink on 2007-06-20
> **dfreer said:**
> (3) I'd create a directory for each student, like /var/www/jsmith and /var/www/achapman
Then create a new file in /etc/apache2/sites-available/, for each user name (so /etc/apache2/sites-available/jsmith for example). Set up your virtual host information in there, makiing each documentroot for each user mapped to their folder on /var/www/ and the servername set to username.testsite.com or whatever. you can also define a seperate errorlog for each student this way (so you can see which site is messing up and why). make sure to reload the server afterwards.

This is crazy. Its too much work for that there is no justification for doing in your case. Add users to your system for the students. If you want them to only FTP, give them the false shell. Whatever FTP server you use will likley have an option to lock users in thier home directories. Use it.

If you want users to be able to store stuff out side of the document root (a good idea when dynamic stuff is involved) leave things as is. If you want to simplify, use the UserDir directive in Apache to map the user directories to the plain old home directories. (I don't advise this.) The directive would look like this.

```
UserDir /home/*
```

If you want to do VHosts...

```
VirtualDocumentRoot /home/%2/public_html
```
(Or drop the /public_html if you want to server directly out of home directories. (Again, I don't advise this.)

%n a posistion in the broken-apart host name. %1 is the first part, %2 is the second part, and so on. %0 is the whole thing. %2 lets you use www.<USERNAME>.domain.tld . Ick. Why not just use %1, and drop the www.

As far as the log goes, just make sure the host name is in the log if you use virtual hosts. If you want students to see logs, you can give them all read access to it. They shouldn't have anything sensitive in the logs anyway.

---

### Post by dfreer on 2007-06-20
Sounds better than my solution. I didn't know you can use the %n to specify virtual hosts, that's why I went the route I did. Although with FTP, I didn't think you could specify user directories, I thought you had to use a common folder like /home/ftpusers/ (maybe that's with anonymous FTP?). 

Anyways, did any of this help, 919Guy?

---

### Post by 919Guy on 2007-06-20
It's helping.  I'm still trying to get my head around the getting the FTP Upload directory for each user to coincide with the VirtualDocumentRoot....

---

### Post by Frosty Cold Drink on 2007-06-20
> **dfreer said:**
> Sounds better than my solution. I didn't know you can use the %n to specify virtual hosts, that's why I went the route I did. Although with FTP, I didn't think you could specify user directories, I thought you had to use a common folder like /home/ftpusers/ (maybe that's with anonymous FTP?).

Yeah that would be for anon FTP, and the %n thing is sweet. What people sometimes do is set things up as
```
/var/www/%-2.%-1/htdocs
```
so that domain.tld and [www.domain.tld](www.domain.tld) are served from the directory, and admins can farm out hosting like its nothing.

[quote=919Guy]It's helping. I'm still trying to get my head around the getting the FTP Upload directory for each user to coincide with the VirtualDocumentRoot....[/quote]
Thats why you server out of home directories and subdirectories of it. In ProFTPD
```
DefaultRoot ~
```
will set the root for a user to thier home directory.

I don't know how to do it in anything else since ProFTPD is what I use.

---

