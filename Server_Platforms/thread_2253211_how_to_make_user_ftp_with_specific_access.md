---
title: "how to make user ftp with specific access??"
date: 2014-11-18
forum: Server Platforms
---

### Post by herry_widnyana on 2014-11-18
[COLOR=#000000][FONT=Arial]hai,I am a new user in Ubuntu. I want to make ftp with vsftpd in UBUNTU, i want to make 2 user. 
User 1 can view, download, and upload file in ftp server, and than user 2 can view and delete,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]i was make 2 user, but how to make that users have specific access???

please, i need your help..[/FONT][/COLOR]

---

### Post by mastablasta on 2014-11-18
you give them specific permission for the folder/directory.
check chmod and chown command manuals. or if you have root access, you can use FTP file manager to set up permissions for the user.

---

### Post by Jonathan L on 2014-11-19
Hi Herry[COLOR=#000000][FONT=Arial]

You'll have to be quite clear what you want them to be able to do, but certainly vsftp is extremely flexible and offers possibilities beyond the basic Unix file permissions.

For example: Can U1 delete their own uploads?  Rename them?  Overwrite them?  Can U2 do any uploading? Renaming?  Can either user make new directories?

I was trying to work out what it was for: as it sounds a little unusual.  What use are you planning?

Kind regards,
Jonathan.
[/FONT][/COLOR]

---

