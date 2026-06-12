---
title: "Sharepoint on Ubuntu server."
date: 2008-12-19
forum: Server Platforms
---

### Post by EmanresuusernamE on 2008-12-19
What's a good alternative to Sharepoint for Ubuntu?  One of our customers wants something like Sharepoint, but not the cost.  From what I can tell, Sharepoint is really just a web based FTP server that you can download and upload to from easily.  Can Apache do something like this?

On another note, would something like rapache be usable to help implement this?  Or at least make Apache a little easier to use?

---

### Post by cdenley on 2008-12-19
I'm not familiar with any all-in-one solutions, but apache can certainly handle downloads and uploads.
[http://uber-uploader.sourceforge.net/](http://uber-uploader.sourceforge.net/)

I found projects that might work, but never tried them.
[http://phpfm.sourceforge.net/](http://phpfm.sourceforge.net/)
[http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)

Some groupware collaboration suites such as Zimbra allow you to upload and share files.

---

### Post by dperfors on 2008-12-19
> **EmanresuusernamE said:**
> What's a good alternative to Sharepoint for Ubuntu?  One of our customers wants something like Sharepoint, but not the cost.  From what I can tell, Sharepoint is really just a web based FTP server that you can download and upload to from easily.  Can Apache do something like this?

On another note, would something like rapache be usable to help implement this?  Or at least make Apache a little easier to use?

SharePoint is not "just a web based FTP server". It is a complete framework that enables you to create an interactive website in just a view clicks. It makes it possible to integrate a website with ActiveDirectory and Office.

I don't know whether there is something similar in the OpenSource world.

---

### Post by cdenley on 2008-12-19
I doubt it can integrate with AD or MS Office, but Drupal is an open-source content management system.

---

### Post by scorp123 on 2008-12-19
> **EmanresuusernamE said:**
> What's a good alternative to Sharepoint for Ubuntu?  Please see the discussion here:
[http://ubuntuforums.org/showthread.php?t=612292](http://ubuntuforums.org/showthread.php?t=612292)

---

### Post by cariboo on 2008-12-19
A quick search in Google comes up with these options

1. [o3Space]("http://o3spaces.com/")
2. [Alfresco]("http://weblog.infoworld.com/openresource/archives/2005/10/alfresco_the_sh.html")

Jim

---

### Post by scorp123 on 2008-12-19
> **cariboo907 said:**
> 1. [o3Space]("http://o3spaces.com/")
2. [Alfresco]("http://weblog.infoworld.com/openresource/archives/2005/10/alfresco_the_sh.html") Good finds! :)

---

### Post by scorp123 on 2008-12-20
Hmmm ...... I did not know this one before:  **Chandler**.

Article about chandler with links to the project's homepage:
[http://www.linuxjournal.com/content/quick-look-chandler](http://www.linuxjournal.com/content/quick-look-chandler)

Video tour:
[http://www.youtube.com/watch?v=JJBxajDwmLI](http://www.youtube.com/watch?v=JJBxajDwmLI)

---

