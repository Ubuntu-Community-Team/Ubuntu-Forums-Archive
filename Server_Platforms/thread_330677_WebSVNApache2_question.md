---
title: "WebSVN/Apache2 question"
date: 2007-01-03
forum: Server Platforms
---

### Post by razialx on 2007-01-03
I am sorry to post here, but I am finding the Collabnet/Subversion website to be insane.

I am using a VMWare appliance for a Subversion server, and it comes installed with:
Ubuntu 6.06
subversion
apache2
websvn

It is the one by young software.


Anyway, I have subversion setup and configured perfectly. The problem I am having is with WebSVN. Since I have security on my repositories, you can not view them. I wanted to make it ask for a login to get credentials to view the repositories, so I took to google and did some hacking of the apache2.conf file.

I tried what few things I found on google, including installing libapache2-svn to get the mod_dav_svn and mod_authz_svn modules installed.

All I want to do is, be able to use the repository conf files for authentication in Apache2.

I am assuming this is possible. 

My repository structure is as follows:
/repo
____/conf
________/svnserve.conf
________/passwd
________/authz
I can access my repo perfectly through svnserve.
the repo is located in 
/var/svnroot

The svnserve.conf file has the following settings:
[general]
anon-access = none
password-db = passwd
authz-db = authz

The passwd file has the following settings:
// These are of course dummy entries
[users]
admin = adminpassword
teacher= teacherpassword
unix000= unix000
unix001= unix001

The authz file has the following settings:
[groups]
administrators = admin
teachers = teacher
[/]
@administrators = rw
@teachers = rw
[/unix000]
unix000 = rw
[/unix001]
unix001 = rw

Simple enough, right.
Everything works great with svnserve. The student accounts can only access their own areas. Teachers and administrators can access anything. 

Now, would anyone be able to help me figure out what needs to be installed into apache2 and how it should be configured to allow those files to determine access to the repositories through WebSVN.


I have tried a variety of things. They all cause a login box to appear but it does not accept any logins.
Alias /WebSVN /var/www/WebSVN
<Location /WebSVN>
   AuthType Basic
   AuthName "Subversion Repository"
   AuthzSVNAccessFile /var/svnroot/repo/conf/authz
   AuthUserFile /var/svnroot/repo/conf/svnserve.conf #Tried passwd as well
   Require valid-user
</Location>

After installing libapache2-svn I was able to start apache2 (previously, AuthzSVNAccessFile threw error of unknown, for good reasons). But, nothing I do will get me logged in. Nothing is logged as far as errors parsing files goes in the /var/log/apache2 directory. It does log the access attempts saying user not found. I feel as though it is something very small I am missing. 


Thank you very much if anyone can help me with this. 
Tim Reynolds

---

### Post by razialx on 2007-01-05
Well, we decided to just skip the WebSVN portion. 

Thank you all that read this, 


Tim

---

