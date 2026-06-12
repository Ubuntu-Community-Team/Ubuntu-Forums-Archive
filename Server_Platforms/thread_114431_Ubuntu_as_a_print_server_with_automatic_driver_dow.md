---
title: "Ubuntu as a print server with automatic driver download"
date: 2006-01-08
forum: Server Platforms
---

### Post by lionel_son on 2006-01-08
Hello,

I am currently using ubuntu server in my company and trying to replace every windows box that we have. 

One of our Windows server is acting as a print server. It has several network printers shared on it, and a IIS server running that allows user to install printers on their laptop via IPP, hence having an automatic driver download from the server, and and a smooth installation for users.

I was wondering is such a configuration could be done using ubuntu. Apache will be used of course, but I am not sure what to use to get the IPP feature for automatic download, ie cups or a samba printer shared.

Anyone has ever implemented such a solution ?

Thanks a lot for your advice

---

### Post by grendelkhan on 2006-01-08
if you find out how to set the windows drivers up for automatic download please post it here as I think a lot of people would want to know how to do this.

---

### Post by newbie2 on 2006-01-08
HowTo: Ubuntu File- And Print Server For Windows Workgroups (Samba Domain Controller)
> This is a detailed tutorial about the steps to set up a Ubuntu based server (Ubuntu 5.10 - Breezy Badger) to act as file- and print server for Windows workstations in small workgroups. This howto uses the tdb backend for Samba to store passwords and account information. This is suitable for workgroups for up to 250 users and is easier to setup than an LDAP backend.
[http://www.linuxelectrons.com/article.php/20060108075141900](http://www.linuxelectrons.com/article.php/20060108075141900)
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

### Post by LordHunter317 on 2006-01-09
It's simple, just setup a [print$] share, add the printer locally, and then add the drivers from a Windows machine.

If you want it fully automatic, it takes some more work, covered in the howto.

---

