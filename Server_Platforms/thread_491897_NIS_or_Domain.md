---
title: "NIS or Domain"
date: 2007-07-04
forum: Server Platforms
---

### Post by renzokuken on 2007-07-04
Hi, this may be a stupid question but hopefully someone can help

Whats the difference between a NIS server and a Domain server/controller?

we have several XP computers connected to a linux server, basically as a filestore. we want people to be able to log onto the server and access their home folders (personal storage) from any computer on the network/domain.

which setup would be better? i was thinking domain but i heard someone mention NIS and i am really unsure of the difference or even what a NIS server is.

thanks

---

### Post by darkog on 2007-07-04
Well, Microsoft make "Windows 2003 server" which contains [Active Directory]("http://www.microsoft.com/windowsserver2003/technologies/directory/activedirectory/default.mspx"). When you install it -- it becomes a "domain controller". 

[NIS]("http://docs.sun.com/app/docs/doc/806-2904/6jc3d07gd?q=customizing&a=view") is the old Sun Yellow Pages app which is currently at ver 3 (i think!). Called NIS+ which is NIS with added security features. 

Both are directory servers -- though AD uses DNS as well.

If you are using Windows hosts, obviously AD will be easier to setup. NIS+ will be a pain. 

You might want to look at [OpenLDAP]("https://help.ubuntu.com/community/OpenLDAPServer") or [FDS]("http://directory.fedoraproject.org/wiki/Howto:DebianUbuntu").

Thought, for what you want to you, I think you want to look at  [Samba]("https://help.ubuntu.com/community/SettingUpSambaPDC?highlight=%28samba%29") with [roaming profiles]("http://wiki.samba.org/index.php/Samba_&_Windows_Profiles").

---

### Post by renzokuken on 2007-07-04
thanks darkog, much appreciated

---

