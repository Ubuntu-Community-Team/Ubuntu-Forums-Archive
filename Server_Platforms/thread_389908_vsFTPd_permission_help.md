---
title: "vsFTPd permission help"
date: 2007-03-21
forum: Server Platforms
---

### Post by kramerkeller on 2007-03-21
So I have my FTP server set up.  I currently have the umask set to 002 in vsftpd.conf.  The reason for this being, I am using the FTP server to upload and edit files for an at home webhost (use dreamweaver, etc).

So first I set my server file to chmod 775 and did chmod g+ws

I created a group called webadmin which myself and another person are apart of

I would like to make it so that any new files under the /srv folder are owned by webadmin, I found that the g+s command makes the group owner of any new files the same as that of the parent group owner.  So everything seems to work from SSH, if he or I edit or add files we can both edit those files because we are both in the webadmin group and each new files belongs to webadmin and the permissions allow that group to edit write, etc.

However, with ftp - something goes screwy and I think it is because of the umask 002 in the vsftpd file

is there a way to also add the g+w command or something to vsftpd?

I am confused

---

### Post by Mr. C. on 2007-03-22
> So first I set my server **file **to chmod 775 and did chmod g+ws
I think you meant **directory**, not file.

Are your users local or virtual users, or anonymous ?

The default file creation mode is 0666.  This is set via:

```
file_open_mode
```

So all new files with your umask would be created as 664.  If the file already exists, vsftpd won't change the permissions.

MrC

---

### Post by kramerkeller on 2007-03-23
I did mean directory.  In the vsftpd.conf file you can set the umask options to 002.  This way anyone accessing creating files, editing files, etc can do so with the above permissions.  These are local users that I have this set up for.  I do not have write enabled for anonymous, only read enabled for anonymous.

So the thing here is - if I log in as Kramer - part of group webadmin

and my friend logs in as Ryan - part of group webadmin

The goal would be that we both can upload, edit, create files and directories, and then because we are apart of the same group we can both edit, modify etc, each other's files.

So if the permissions are 002, this works pretty well.  The pages can be accessed via the web and group and owner can do whatever.  This is assuming that each file created is created under group webadmin.  I think g+s makes it so that each new file is created under it is owned by the group of itself.  Does that make sense because I might have it wrong.  If file "a" is owned group owned by webadmin and I want all files below it to also be owned by group admin, then I would do chmod -r g+s correct?

However, things work a little differently for me in vsftpd.  When uploading I think it only sees the 002 I put in the conf file.  I am not sure if I can add the g+s in the conf file.

---

### Post by Mr. C. on 2007-03-23
You have it correct.

If a directory has perms g+s, and is group-owned webadmin, all new files/directories will be group-owned webadmin.  Only root can chown/chgrp to another user/group, so your base web directory must be setup before you start your FTP transfers.

New files and directories will be created based upon the following:

1) the file_open_mode configured in vsftpd.conf
2) the local_umask specified configured in vsftpd.conf
3) the users current umask when running ftp

Both 2 and 3 are combined.  If the local_mask is 007, but the user running ftp has a umask of 022, then the combined umask will be 027.

Make sense?
MrC

---

