---
title: "looking for a web interface for samba"
date: 2013-01-01
forum: Server Platforms
---

### Post by lucas.robb on 2013-01-01
Hi All,

I'm looking for a web interface for my users to be able to access certain SAMBA shares remotely.  I would be looking for something like one of the two following scenarios.

1. User enters "weburl.com" and are faced with a page asking for login credentials, once supplied any and all accessible shares show up.

2. user enters "weburl.com" and are faced with a list of shares, then upon clicking on the share based on the permissions, are faced with a prompt for credentials, and then are shown the contents

I don't want to manage every single space, just my samba server and have the web interface just reflect the changes I make (for both user control, new shares, etc.)  I'm working with my local church and one of the things I'd like is to have a url at which all of the sermons would be found so that people could download them, but at this point I'm not looking for anything fancy, just a simple click and listen/download.

Thank you in advance,
Lucas

---

### Post by redmk2 on 2013-01-01
> **lucas.robb said:**
> Hi All,

I'm looking for a web interface for my users to be able to access certain SAMBA shares remotely.  I would be looking for something like one of the two following scenarios.

1. User enters "weburl.com" and are faced with a page asking for login credentials, once supplied any and all accessible shares show up.

2. user enters "weburl.com" and are faced with a list of shares, then upon clicking on the share based on the permissions, are faced with a prompt for credentials, and then are shown the contents

I don't want to manage every single space, just my samba server and have the web interface just reflect the changes I make (for both user control, new shares, etc.)  I'm working with my local church and one of the things I'd like is to have a url at which all of the sermons would be found so that people could download them, but at this point I'm not looking for anything fancy, just a simple click and listen/download.

Thank you in advance,
Lucas

Samba (SMB/CIFS) manages ***remote file systems*** that can be mounted to a *local machine*.  Your weburl.com scenario shouldn't need Samba at all.  You just need to manage a web server and create the page listing the downloadable files that you have stored on the server.

---

### Post by lucas.robb on 2013-01-02
> **redmk2 said:**
> You just need to manage a web server and create the page listing the downloadable files that you have stored on the server.

Forgive me if I forgot to mention, I do want a public share for the sermons to be downloaded, but I also wanted a password protected share for only certain users or a group of users to access.  For the latter I have considered FTP, but I think it might be just a little over the heads of my target clients (I.E. when we receive the VBS program it often comes with a CD, I wanted to make the content of that CD available to the volunteers so that they can download the content for their particular area of service, so an FTP site would work giving a username and password of vbs2013)

If I were to setup what you suggested a **page listing the downloadable files** would I be able to create a page that would auto populate based on the contents of a folder? IE copy over the sermon at the end of the service and have it show up in the list without me or anyone else having to edit the html file?  also considering this is for the public, could I make the page presentable? I have access to someone who completed a two year web-design course in post-secondary studies.

*Edit*
I would like to add that I already have a successful samba server setup with user accounts and proper access control on this machine

---

### Post by redmk2 on 2013-01-02
> **lucas.robb said:**
> Forgive me if I forgot to mention, I do want a public share for the sermons to be downloaded, but I also wanted a password protected share for only certain users or a group of users to access.  For the latter I have considered FTP, but I think it might be just a little over the heads of my target clients (I.E. when we receive the VBS program it often comes with a CD, I wanted to make the content of that CD available to the volunteers so that they can download the content for their particular area of service, so an FTP site would work giving a username and password of vbs2013)
Access over the public internet with a FTP like client is best handled by sFTP (SSH).  Windows clients can use [**_[COLOR="Blue"]WinSCP[/COLOR]_**]("http://winscp.net/eng/index.php").  Nautilus (GNOME) handles this natively.  If you insisted on Samba shares via the public internet then you should set up a VPN. Maybe [**_[COLOR="Blue"]OpenVPN[/COLOR]_**]("http://openvpn.net/index.php/open-source/overview.html")?> 

If I were to setup what you suggested a **page listing the downloadable files** would I be able to create a page that would auto populate based on the contents of a folder? IE copy over the sermon at the end of the service and have it show up in the list without me or anyone else having to edit the html file?  also considering this is for the public, could I make the page presentable? I have access to someone who completed a two year web-design course in post-secondary studies.
Anything is possible, but it would be a custom software solution (time+$$$).  There are no magic bullets here.> 

*Edit*
I would like to add that I already have a successful samba server setup with user accounts and proper access control on this machine
I think you are asking a lot for the benefits you will receive in the beginning.

If you just set up a SSH server and configure sFTP with an eye towards security you should have a secure directory that would hold the files that will be up and downloaded in a simple fashion.  That directory can be the Samba share.  You would have to control both the Linux permissions and the Samba permissions at the same time.  I would do that by using only the Linux permissions.  In fact it would be by group permissions.  The group should be inherited from the root of the Samba share,  By this I mean a group like ***sermonusers***  have rw rights. and the valid user would be @seremonusers.  If you want read only (ro) on the files then you can set that instead.  

There are many ways to construct this solution.  I would think it out a little more regarding what you want to provide your users,  This should include what you expect from them.  They may have to learn some new  skills (not entirely a bad thing).

---

### Post by volkswagner on 2013-01-03
> **lucas.robb said:**
> Forgive me if I forgot to mention, I do want a public share for the sermons to be downloaded, but I also wanted a password protected share for only certain users or a group of users to access.  For the latter I have considered FTP, but I think it might be just a little over the heads of my target clients (I.E. when we receive the VBS program it often comes with a CD, I wanted to make the content of that CD available to the volunteers so that they can download the content for their particular area of service, so an FTP site would work giving a username and password of vbs2013)

For the public share I would do as others mentioned with a simple web page listing files... more on this below.  For a secured share look into [OwnCloud]("http://owncloud.org/"), [webDav]("http://ubuntuguide.org/wiki/WebDAV") or similar if you don't want sFTP.


QUOTE=lucas.robb;12435161]
If I were to setup what you suggested a **page listing the downloadable files** would I be able to create a page that would auto populate based on the contents of a folder? IE copy over the sermon at the end of the service and have it show up in the list without me or anyone else having to edit the html file?  also considering this is for the public, could I make the page presentable? I have access to someone who completed a two year web-design course in post-secondary studies.
[/QUOTE]


You can simply create a rich landing page with a link to your files.  A link like [this]("http://cdimage.debian.org/debian-cd/6.0.6/i386/iso-cd/?C=M;O=A") pointing to Debians list of CD's.  Notice when you follow the link, files are listed by most recent first.  This is done by appending the link url with "?C=M;O=A" for the sorting.  There would be no additional html required once the link is functioning.

You can have folders on the file list page as well.  For example if you wanted only the most recent twelve sermons listed, you could have a file marked archive.  Your admin adding the sermons to the folder would simply move old files to the "archive" folder.  You could further add more folders inside the archive folder for "2010", "2011", etc.

QUOTE=lucas.robb;12435161]
*Edit*
I would like to add that I already have a successful samba server setup with user accounts and proper access control on this machine[/QUOTE]

Please understand, SAMBA is not secure to open to the world on the internet.  As mentioned if you are set to use SAMBA you'd need to use VPN access.

---

### Post by SeijiSensei on 2013-01-03
How do you authenticate users in Samba?  Do you simply have an smbpasswd file, or are you using an external method like LDAP or PAM?  If you want to authenticate users over the web, the simplest method is to use [HTTP Basic Authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html"), but that usually requires maintaining a separate username and password list.  It might be possible to cobble together a method of authentication that uses Samba (via the pam_smb module and a custom entry for Apache in /etc/pam.d).  Otherwise you might look into putting the users and passwords into a database and authenticating everyone against the database.  

If the userbase is relatively small and relatively static, then simply creating a parallel authentication system within Apache is probably the easiest approach.  If you have a lot of valid users, or users that come and go all the time, a database-backed system might be more effective.

---

