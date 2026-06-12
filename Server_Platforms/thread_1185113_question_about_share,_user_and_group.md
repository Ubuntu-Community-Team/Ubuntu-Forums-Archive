---
title: "question about share, user and group"
date: 2009-06-11
forum: Server Platforms
---

### Post by chuugokujin on 2009-06-11
I have three users on my system:
user      group
A          sales
B          sales
C          managers

and a samba share folder /share that allows sales and managers to edit.
/share is at the mode 775.

now, when user A creates a folder called /share/fA,it belongs to user A, and group A, not group sales. same to any user, the folder belongs to the group in their own names. I ran command groups and find out sales is the only group that A belongs.  

My questions:
1) how to set up to make the file(folder) belongs to A:sales instead of A:A, whenever user A creats it? In that way user B can edit it.
2) if question #1 solved, /share/fA now belongs to group sales, then how to make user C edit it? managers are supposed to have higher privileges than sales.

In any way would suid/sgid help?
Sorry if I made it complex. Thanks,

---

### Post by mbeach on 2009-06-12
not sure I fully follow, but I think the "force group" setting may do what you are after.  Look in the ```
man smb.conf
``` file for specifics on the force group setting.

---

### Post by Vegan on 2009-06-12
You can configure SAMBA to use Linux permissions or you can use it to simplify configurations. 

One book on SAMBA I have seen documents all of the capabilities. There are no good general books though that I have seen yet.

---

### Post by bab1 on 2009-06-12
> **Vegan said:**
> ...There are no good general books though that I have seen yet.

Have you read [**_Samba by Example_**]("http://us6.samba.org/samba/docs/man/Samba-Guide/") ?  It starts from very simple sharing and ends up at AD integration.  I found it very helpful.

Most of the documentation at [**_samba.org_**]("http://us6.samba.org/samba/docs/") is pretty thorough.  

What type of guide are you looking for?

---

### Post by Iowan on 2009-06-12
My (somewhat antiquated 2000) Samba Unleashed book goes into detail about service group vs. effective group... but does have some plain English. Regarding **force group=**> This means that any new file created in the Samba session on the share has the forced group.

---

### Post by bab1 on 2009-06-12
> **Iowan said:**
> My (somewhat antiquated 2000) Samba Unleashed book goes into detail about service group vs. effective group... but does have some plain English. Regarding **force group=**

Indeed.  I add all my users to a group called smbusers on the Linux server hosting Samba.  It does not have to be the users primary group either.  When you use "force group" Samba elevates the user to the smbusers as the primary group.  Here is a directory listing e.g., a share:```
-rw-------  1 bruce  smbusers    111K 2009-03-11 11:39 Bruces-SWConfirm.pdf
drwxrwsr-x  2 louise smbusers 4.0K 2009-03-21 12:01 ConversionPlease
drwxrwsr-x  9 bruce  smbusers 4.0K 2009-05-09 13:03 Cooking
-rw-r--r--  1 bruce  smbusers 211K 2009-04-10 08:45 Deck North Handrail 2009.pdf
drwxr-sr-x  4 bruce  smbusers 4.0K 2009-04-05 18:14 Docs_&_Manuals
drwxrws--T 11 louise smbusers 4.0K 2009-05-16 15:47 eloisa
drwxrwsr-x  2 louise smbusers 4.0K 2008-10-23 13:21 PixAdd
drwxr-sr-x  8 bruce  smbusers 4.0K 2009-05-26 15:59 Medical
drwxr-sr-x 30 bruce  smbusers 4.0K 2009-06-11 16:25 Pictures
drwxr-sr-x  4 bruce  smbusers 4.0K 2009-05-26 15:54 ERD  Final
drwxrwsr-x  2 bruce  smbusers 4.0K 2009-03-16 21:38 URDC-benefits
drwxr-xr-x  3 louise smbusers 4.0K 2009-03-18 22:54 wallpaper

```

In this directory the user can write files and others may read them but not modify or delete them.

---

### Post by chuugokujin on 2009-06-13
Thank you all,the force group=+sales works perfectly for me! Now I need to make managers able to do whatever the sales can do, how to set up?

---

### Post by Iowan on 2009-06-15
Reaching a bit... but can you make the managers members of the sales group? I haven't done in-depth study of users/groups, but a li'l research might reveal if you can have one group as a member of another. So the managers group might be a member of the sales group - without needing to add the members individually.  Dunno if it'll work - just an idea.

---

