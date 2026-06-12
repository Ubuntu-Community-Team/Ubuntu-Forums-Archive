---
title: "Uploading CRM to Web Host"
date: 2012-04-21
forum: Server Platforms
---

### Post by TOG182 on 2012-04-21
I am currently running a CLI LAMP server (Ubuntu 10.04.4 LTS) with SugarCRM Community edition Version 6.4.3 (Build 7673), I would like to upload the CRM to our current web host which is on Linux.I have ncftp installed on my server.

Can anyone help with which of the CRM or other files I need to upload to my web host and also which of the ncftp commands I should use.

Regards
tog182

---

### Post by DJ_Max on 2012-04-21
I've never used NcFTP, but its irrelevant what FTP client you use, as long as you can upload the files. I use Filezilla which has a GUI so no need for commands, just connect and drop the files.

As far as SugarCRM just upload all the files, and dump your local database. After you upload all the files import the sql file.

I dont know who your webhost is or whether you have a shared or VPS, nor do I know what setup they have so I can't tell you the specifics.

---

### Post by TOG182 on 2012-04-21
> **DJ_Max said:**
> I've never used NcFTP, but its irrelevant what FTP client you use, as long as you can upload the files. I use Filezilla which has a GUI so no need for commands, just connect and drop the files.

As far as SugarCRM just upload all the files, and dump your local database. After you upload all the files import the sql file.

I dont know who your webhost is or whether you have a shared or VPS, nor do I know what setup they have so I can't tell you the specifics.

The web host is 1&1, as far as I know we do not have a shared VPS

---

### Post by DJ_Max on 2012-04-21
I meant shared OR VPS.

Regardless shouldnt be much different from installing on your local host. Just you will need to import your database

---

