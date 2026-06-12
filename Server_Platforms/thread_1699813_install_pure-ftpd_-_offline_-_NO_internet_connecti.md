---
title: "install pure-ftpd - offline - NO internet connection"
date: 2011-03-04
forum: Server Platforms
---

### Post by gabriel01 on 2011-03-04
Hi All,

I am trying to install pure-ftpd on ubuntu server without internet connection. 

so my question is, how can i accomplish that? I have already downloaded pure-ftpd file, but where and what directory do i place that file and how to run it?

also tried this:

#apt-get install pure-ftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package pure-ftpd




ps: Sorry i am a noob to ubuntu and any help is greatly appreciated.:(

---

### Post by Lars Noodén on 2011-03-04
If you are going to be publishing file read-only then Anonymous FTP is what you might need.  pure-ftpd can give that.  Web servers like nginx, lighttpd, or Apache can also give read-only access, but via HTTP instead of FTP.  

The simplest way is, if you want to be able to upload and not just download, is to take a second look at SFTP because it is already built into OpenS.SH server.  If you can log in via SSH, then you already have everything configured for SFTP.  Your system's file manager (e.g. nautilus or konqueror) supports SFTP transfers, that is they are built-in graphcial clients.

---

### Post by gabriel01 on 2011-03-04
> **Lars Noodén said:**
> If you are going to be publishing file read-only then Anonymous FTP is what you might need.  pure-ftpd can give that.  Web servers like nginx, lighttpd, or Apache can also give read-only access, but via HTTP instead of FTP.  

The simplest way is, if you want to be able to upload and not just download, is to take a second look at SFTP because it is already built into OpenS.SH server.  If you can log in via SSH, then you already have everything configured for SFTP.  Your system's file manager (e.g. nautilus or konqueror) supports SFTP transfers, that is they are built-in graphcial clients.

Thanks lars for your response.

My goal is to setup a standard ftp server. any ideas how can i add packages to repository as my server does not have internet connection hence i can't perform updates to get apps. I want to install pure-ftpd or anything smiler will do

Thanks again :)

---

