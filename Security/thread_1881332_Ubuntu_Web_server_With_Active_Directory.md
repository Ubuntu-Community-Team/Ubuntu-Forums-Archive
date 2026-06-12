---
title: "Ubuntu Web server With Active Directory"
date: 2011-11-15
forum: Security
---

### Post by talkingtek on 2011-11-15
Hi,

I'm looking for a solution for one my small project on a local intranet.  I'm not sure if I'm on the right forum and is it possible, but I would really appreciate if someone could direct me to the right information.

Here's what I'm looking for.  I've create an intranet on Ubuntu 10.04 share .pfd files and forms.  Within the intranet, there's a folder was map from windows server which is a share folder call admin.  The admin folder was only access within the admins group in Windows.  

So I want to create a link on the web server (Ubuntu 10.04) and prompt for user name and password when users click on the link within the admin folders.  Is it possible?  I don't want to create new users, but I want use the Active Directory user name and password.  Can it be done since the web server is on Ubuntu and the Share Folder was on a Windows Server?  Is there any tutorial some where that walk me how to do it?

---

### Post by HermanAB on 2011-11-16
Yes, but no...

You can set up a server as an Active Directory client, using Samba Winbind or Likewise.

However, doing what you want is probably not so easy.

---

