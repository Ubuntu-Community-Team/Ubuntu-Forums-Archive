---
title: "access control for website"
date: 2010-06-09
forum: Server Platforms
---

### Post by John Rivera on 2010-06-09
I am working on my "local area network server" project and now I ran into a problem.

Currently I do have only one subdomain available to my server and I would like to setup multiple websites. 
I came to conclusion to set those websites as sub directories.
Reason for that is that I need multiple websites in way that those are not visible for each other and are somehow logically arranged.

So my issue here is that I am wondering that what possible viable options I do have for setting up access control for my apache2 webserver

Directories on my server are like

/www/ (root directory) (no actual content more than redirecting)
/www/online (main website)
/www/projects (for various projects I work with) [also have specific projects as subsites]
etc.

I did read open Ldap server guide from ubuntu.com however I am not sure if it is up to date and can be used or not so I do not use it initially.

Also I am wondering what would be best suited method for access control if I do want to setup little more advanced stuff than just a website.

---

### Post by Vegan on 2010-06-09
Use any form and present user name and password then use a session cookie to use the site.

---

### Post by John Rivera on 2010-06-21
updated actual question to make it be more clear what I am trying to achieve.

---

### Post by John Rivera on 2010-07-05
Still no viable solution for problem and only answer I actually got was useless.

So what I need to know is how to make access control for apache virtual host sub directories, prefer other than .htaccess unless someone can tell how to make it reliable.

---

### Post by barnesey on 2010-07-05
You can use name based virtual hosting.
 
I had about 5 different websites running on my web server with dynamic domain names for each of them.
 
I had made the virutal hosts with the directery root to the users home dir and jailed them in to sftp so they only gain access to thier home dir not each others files.
 
Is this what you are trying to achive?

---

### Post by John Rivera on 2010-07-10
Kind of.

I got idea on my head what I try to get done, however writing that into sense making words can prove difficult at times, but I try.

Currently I do have port 80 open and redirected by my ISP and I also get a subdomain for my server so it has logical address from where it is accessible.

My web server is configured so that I do have one virtual host configuration made.
Now I would like to add multiple within subdirectories on my virtual host websites with access control that people who do not have account to website can't see a thing, prefered prior to actual website login, or so that those are one and same.

so basically setup would look like this

/var/www (virtual host document root)
/var/www/website (primary website)
/var/www/private (for closed audience intended website)

Currently I do need this kind of setup since I need multiple websites and don't have chance to get own dedicated server in some machine hall.

---

