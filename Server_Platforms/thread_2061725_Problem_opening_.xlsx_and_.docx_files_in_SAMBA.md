---
title: "Problem opening .xlsx and .docx files in SAMBA"
date: 2012-09-23
forum: Server Platforms
---

### Post by Jorel on 2012-09-23
Hi guys,

My SAMBA File server is running fine but i noticed that when i open a file with an extension of .xlsx and .docx, it says that "Read only",, but no one is opening that file except me.. most of the post are outdated and not in Ubuntu Distro so im doubting to try...

regards..

---

### Post by volkswagner on 2012-09-23
Are you sure it is not a permission issue?

Are the permissions any different from documents you can edit?

```
ls -alt /location/of/sharedfolder/
```

---

### Post by Jorel on 2012-09-23
Hi,

I did something like this in my setup:

find /location -type d -exec chmod g=rwxs "{}" \;
find /location -type f -exec chmod g=rws "{}" \;

so everyone who's in the "Group" of that file has the ability to create file, folder etc... but the weird part is some old file .xlsx and .docx are having that problem but some new files with that file extension are working properly...

drwxrwsr-x 2 jorel admin 4096 .
drwxrwsr-x 2 jorel admin 4096 ..
-rwxrwSr-- 1 jorel admin 13872 file.xlsx

regards

---

### Post by volkswagner on 2012-09-23
According to the file permission:

```
-rwxrwSr-- 1 jorel admin 13872 file.xlsx
```

Only user/group jorel and admin have write access.

How are you accessing the file?  Are you using a windows client?  Are you sure you are logging into SAMB with username jorel?

jorel can't write to file.xlsx?

What does the smb.conf section for the file share look like?

---

### Post by Jorel on 2012-09-23
This is the setup that i did:

[Folder]
browseable = yes
guest ok =yes
path = /location/folder
valid users = jorel, user1, user2, @admin
write list = jorel, user1, user2, @admin
create mask = 0755

user1 and user2 are already in the group so i also add myself to the admin group:
gpasswd --add jorel admin

and:
chmod 0775 /location/folder

the Server is almost a month working and everyone that i wanted to have a read and write access or read only is implemented...

yes i'm accessing jorel account and using Windows machine to access it.

---

### Post by volkswagner on 2012-09-23
Have you seen this [thread]("http://lists.samba.org/archive/samba/2011-January/160316.html")?

Likely as you may already know, this issue is probably MS Office can't create the necessary temp file.

From the above link, you may try to use the force group option.

While you are at it, to help with possible future (users creating directories) issues you may also want to add the directory mask option.

Also from the link, verify the ACl option is not enabled in smb.conf.

---

### Post by Jorel on 2012-09-23
I haven't tried what's on that thread yet,, probably tomorrow when i got to the office,, 

I included ACL already in:
/etc/fstab in the mount of /location

/location     default,acl    0  2

i really dont know what the figures means... XD

---

### Post by volkswagner on 2012-09-23
The way I read the linked thread, is using ACL can _add_ to the problem.  Since you have it enabled outside of SAMBA I'm not sure how this helps/hurt the problem.

---

### Post by Jorel on 2012-09-24
Hi, 

Would you know where to put the "nt acl support = no" or will i add it to the [global] just as that line...

and also would you know where does these files come from?

-rw------- user1 admin 0 date Time smbprn..gZ14q2

is this a virus generated files or just a temp file?

regards.

---

### Post by volkswagner on 2012-09-24
You can put that in the share definition if you don't think this issue will occur outside that share.

Check out this [thread]("http://userssuck.com/2007/03/13/samba-file-permission-issue-with-microsoft-office/").

Are you using roaming profiles?

As far as that odd file, I'm not sure what that is.  According to [this thread]("http://us.generation-nt.com/answer/samba-printing-issue-after-update-3-6-1-help-206184222.html"), it may be related to CUPS/print.

---

### Post by Jorel on 2012-09-24
hi volkswagner,

you really nailed my problems.. problem solved here..

Thanks a lot...

---

### Post by volkswagner on 2012-09-24
That's great.

Please mark thread as solved using "Thread Tools"

---

### Post by Jorel on 2012-09-24
yup, i forgot,,

and also last thing i found out just recently that if you are the owner of the folder, somehow it will bypass that problem, i needed to set some folders to share on a group that's why it gone crazy on me.. hehehe anyway thanks again....

---

