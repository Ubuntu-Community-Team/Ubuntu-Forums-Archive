---
title: "First time server development"
date: 2007-07-13
forum: Server Platforms
---

### Post by dlp21 on 2007-07-13
OK, so I recently put together a system which I want to dedicate to being a server.  All hardware works and is compatible with Ubuntu Server.

So my requirements include being a media/file server, serving up mostly movie files and music files.  Also because I have multiple HDD I want it to appear to the Windows user that there is only one folder....even though it will span multiple HDD.  I also do not want to use a RAID 0 as if one of the HDD fails the data on both is no longer useful to me.  ****In time I will add more HDD's and configure a RAID 0+1 or maybe a RAID 5**** Also, the files need to have read access but not right/copy/delete.  Another requirement is to use the server to perform backup's of select Window's PC's.  My final requirement is to develop a LAMP enviorment to do Web Development in.

My proposed solution is to install Ubuntu Server Edition, then add VMware Server to create 3 separate virtual servers, I will also use openSSH to allow remote access with PuTTy and from the terminal in Ubuntu Desktop. ****All Ubuntu solution's are 7.04****  

One dedicated to being a media/file server.  I will use Samba to add interoperability for my Window's PC's.  I will also add MySQL, PHP, Apache, along with Jinzora to allow access to the files through a Web Browser.  However I still don't know how to make it look like one HDD

The second virtual server will use backupPC and will backup the selected computer's, some Window's and some Ubuntu Desktop.

The third will be a default LAMP Ubuntu Server installation.

My resources are Google, these forums, Samba.org etc.

I realize that using a GUI would make my life easier but I want to use the CLI to get used to it.

Any suggestions are welcomed.

---

### Post by erwall on 2007-07-14
Check out [http://www.howtoforge.com](http://www.howtoforge.com)

Lots of solid step by step howto's!

---

### Post by nix4me on 2007-07-14
I wouldn't bother with vmware.  It is horribly slow and consumes huge resources.  You could easily do all of your desired tasks with 1 server.

nix4me

---

### Post by NuttyBrown on 2007-07-15
> **nix4me said:**
> I wouldn't bother with vmware.  It is horribly slow and consumes huge resources.  You could easily do all of your desired tasks with 1 server.

nix4me

Why wouldn't you use vmware? :confused:  According to their documentation it isn't supposed to be hard on the resources.

---

