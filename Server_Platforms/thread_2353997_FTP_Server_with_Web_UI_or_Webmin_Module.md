---
title: "FTP Server with Web UI or Webmin Module"
date: 2017-02-27
forum: Server Platforms
---

### Post by voyto on 2017-02-27
Hi All! Feel like I'm always asking for help on here - hopefully I'll be able to contribute soon!

Migrating from Windows Server to Ubuntu Server 16.04 has been great. Everything just behaves as it should!

The only thing I'm struggling to find, is a good alternative to Filezilla Server. I have a few media folders I like to share with a handful of family members which I've always done with Filezilla Server. It integrates with their Windows operating systems easily without them needing additional software. Security (as long as I can set read only permissions) is not a concern. 

I'm looking for something with a GUI (Webmin or WebUI as I have no Desktop with Ubuntu Server), has the ability to throttle bandwidth, easily add users and see a log of which files users have been downloading.

I tried ProFTPD that was included with Webmin, but couldn't find a way to throttle bandwidth / view user history. Are there any other's you guys would recommend? :-k

---

### Post by howefield on 2017-02-27
Thread moved to the "*Server Platforms*" forum, probably a better fit for quicker help.

---

### Post by mastablasta on 2017-03-01
samba server integrates seamlessly with Windows.

since you are just setting up, have a look at Nextcloud or Owncloud and Seafile as alternative solution. personal clouds also integrate relatively well into Windows. they also offer web browsing of the media.

if you are using FTP for file transfer and filezilla client for browsing, then a good option is to use OpenSSH, add keys and then use Filezilla client to access the server. now sur eif oyu can use file Explorer to Access sFTP or FTP. i think maybe you can already do that.

if media is mostly photos, then Piwigo is a descent galery webserver

---

