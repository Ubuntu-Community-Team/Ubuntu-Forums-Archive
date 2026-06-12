---
title: "Home Server with Private Site"
date: 2013-05-11
forum: Server Platforms
---

### Post by mobo on 2013-05-11
I am planning to deploy a second Ubuntu Server in the next couple of weeks and would like to have some suggestions on the configuration of the hosting sites setup. I want to use this server as a document, file server for all my files and my Children's files. I want them to have the ability to access their files from school or wherever. I want to access software files on the server in the event that I do some housecall tech support / repair. What type of solution could best serve that need. I do have samba file serving currently on one server so thats not an issue. The tricky part for me is having a domain setup that can be reached by web browsers but not the files, unless by one of the family members.

Thanks for your help

---

### Post by SeijiSensei on 2013-05-11
The easiest solution would be to build a web server.  You can protect the directories with usernames and passwords, and you can also create groups that have group-wide permissions.  If the server remains in your home, you'd either need to obtain a static address from your provider or use a DNS service like no-ip.com.  You can install a self-signed SSL certificate on the server and your client browsers if you want to enforce encrypted communications.

Web servers do not work well for two-way file transfers, though.  From the applications you describe, that should not be a major limitation.  Otherwise you should consider secure solutions like SFTP or SCP.  The [WinSCP]("http://winscp.net/") client, for instance, requires only that you can make an SSH connection to the server to transfer files. Ubuntu machines can also connect directly to remote machines via SSH from filesystem browsers like Nautilus and Dolphin.  SCP, like SSH in general, uses the server's authentication and permission systems.

You will also need to forward one or more ports through your router.  If you use a web server, you'd need to pass traffic back to port 80 and/or port 443 (HTTPS) on the server; for SSH-based services, you need to forward back to port 22.  Note there is no requirement that the publicly-exposed port be the same as the one actually providing the service.  You can set the router to accept traffic on port 22222 and forward it back to the SSH port 22 on the server.

---

### Post by mobo on 2013-05-11
> **SeijiSensei said:**
> The easiest solution would be to build a web server.  You can protect the directories with usernames and passwords

Do you mean htaccess ?

---

### Post by SeijiSensei on 2013-05-11
.htaccess is a solution that grants people limited control over the server's operations.  It's designed for hosting situations where someone else runs the server, and you have control of only the directory where your website resides.  If you are running your own server, the usual practice is to place any Apache directives that would be in an .htaccess file in the server configuration itself.  Usually these are placed in a <Directory> container in the server configuration file.  On Ubuntu, these files reside in /etc/apache2/sites-available/.  If you install apache2 on your machine, take a look at /etc/apache2/sites-available/default to see the layout of the default web server that delivers the contents of /var/www.

For more details on Apache authentication, read [this](http://httpd.apache.org/docs/2.2/howto/auth.html#gettingitworking).  More generally, I recommend perusing the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/").

---

### Post by mobo on 2013-05-11
Thats great...Got some work to do...
Thanks

---

### Post by SeijiSensei on 2013-05-11
If I were you, I'd start by installing **openssh-server** on the box if it is not installed already, passing a port through to port 22, and giving WinSCP a try.  It may be the simplest solution of all, especially if you have already set up user accounts and groups on the server.

---

### Post by snathan99 on 2013-05-13
Try installing a subversion server.  It gives you multiple benefits:

* Version control (of course)
* Ability to access files from multiple computers and send updates back from each
* Offline access - You can edit local copies and commit when done. Quick refresh of all files to get local copies
* No accidental file version overwrites - all commits are tracked
* SVN has a very small learning curve
* Can (should) be password protected

Cons:
* If you get into merging it can get complicated
* Need to remember to commit!

---

