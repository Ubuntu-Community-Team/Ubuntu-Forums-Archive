---
title: "Ubuntu + Apache + ProFTP - where to put vhost files?"
date: 2008-02-16
forum: Server Platforms
---

### Post by Poleh on 2008-02-16
Hi, so as the topic says, I have installed and am using Apache and ProFTP on Gutsy Server.

Be default Apache is using /var/www to store files for the web server - the default htdocs if u must.

I am going to be hosting a smallish number of vhost sites ( < 100) on this box and would like some advice on what user/folder structure to use to accomplish this.

Obviously there are fairly strict permissions on /var/www which will influence this.

My thoughts so far involve two different approaches, and I would appreciate feedback on them from anyone who's done this before.

[list=1]
[*]**Standard Linux Users + Store everything under /var/www in vhost folders**

The username will be the domain, e.g. [www.swaziboy.com](www.swaziboy.com)

vhost folder locations will something like this:
/var/www
/var/www/www.swaziboy.com
/var/www/mail.swaziboy.com
....etc (no pun intended!)

The obvious problem here is the restrictive permissions on /var/www and getting users access to these folders easily with ProFTP. I had thought of linking to the folder from their home folders to accomplish this but am having a few issues doing so as this is ALL new to me (ex Windows Admin).

**Pro's/Con's ?**

[*]**Standard Linux Users + htdocs (or similar) in their home folder**

The username will be the domain as per above, e.g. [www.swaziboy.com](www.swaziboy.com)

there will be a /logs and /public_html in the user's home folder which will be configured in the vhosts for apache. This isn't too difficult to accomplish I think, but is it the best way to do it?

I also know there is a way to secure these users so they can't log in via shell/ssh which I have seen around the place and can setup once I have done some research.
**Pro's/Con's ?**[/list]

Any comments and help would be appreciated - I have trauled the forums, but not found anything that answers my rather specific questions (which is not to say they're not there, just that I am a TERRIBLE search engine user...)

Thanks in advance ....

---

### Post by Poleh on 2008-02-16
*bump* anyone got some input?

---

### Post by soulresin on 2008-02-16
> **Poleh said:**
> 

[*]**Standard Linux Users + htdocs (or similar) in their home folder**

The username will be the domain as per above, e.g. [www.swaziboy.com](www.swaziboy.com)

there will be a /logs and /public_html in the user's home folder which will be configured in the vhosts for apache. This isn't too difficult to accomplish I think, but is it the best way to do it?

I also know there is a way to secure these users so they can't log in via shell/ssh which I have seen around the place and can setup once I have done some research.
**Pro's/Con's ?**[/list]



Thanks in advance ....

#2 is the way I go about it.  chroot the ftp users into their home directories, and set their shell to /bin/false or /sbin/nologin and you're set.

---

### Post by Poleh on 2008-02-17
> **soulresin said:**
> chroot the ftp users into their home directories.

Thanks for the response ... but, as a linux newb how does one go about that? I have done some searching and there seem to be hundres of types of chroot'ing ... I get the /bin/false thing now that I have done some reading...

---

### Post by soulresin on 2008-02-17
> **Poleh said:**
> Thanks for the response ... but, as a linux newb how does one go about that? I have done some searching and there seem to be hundres of types of chroot'ing ... I get the /bin/false thing now that I have done some reading...

I don't use proftpd myself, but if I remember right, you can do something like add a ftpuser group to the server and add the ftp users to that group.  Then add something like

DefaultRoot ~ ftpuser

to the proftpd configuration file to have everyone in the ftpuser group chrooted to their home directory.

---

### Post by Poleh on 2008-02-18
> **soulresin said:**
> I don't use proftpd myself, but if I remember right, you can do something like add a ftpuser group to the server and add the ftp users to that group.  Then add something like

DefaultRoot ~ ftpuser

to the proftpd configuration file to have everyone in the ftpuser group chrooted to their home directory.

Ah ok, so chroot them from a FTPPro perspective rather than an OS perspective - makes sense I guess since they have no shell access...

Thanks for your help chap, appreciate it!

---

