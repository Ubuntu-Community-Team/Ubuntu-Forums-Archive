---
title: "[SOLVED] Linux Permissions help ?"
date: 2007-09-22
forum: Server Platforms
---

### Post by syborfical on 2007-09-22
I have my hard disk partitioned into 2 drives.
The second partition is SDA2. its mounted at /media/stroage.
Linux Permissions help ?

I have my hard disk partitioned into 2 drives.
The second partition is SDA2. its mounted at /media/stroage.

Its pretty much my file share.

I have 4 users on the pc. 

what i would like to be able to do is have the users; root, me and upload to have full read write and execute access to the 2 nd partiion.

I would also like the user leech to be able to read and execute?

how do i set the permissions for these 4 users? 
Its pretty much my file share.

I have 4 users on the pc. 

what i would like to be able to do is have the users; root, me and upload to have full read write and execute access to the 2 nd partiion.

I would also like the user leech to be able to read and execute?

how do i set the permissions for these 4 users?

---

### Post by HermanAB on 2007-09-22
What you need to do: Make a group called 'share' and make all users members of 'share', then assign that group to the directory on the HDD and all files in it and make the directory permissions 'sticky'.

The Ubuntu wizards can be used to do that.  Otherwise read the groupadd, usermod and chmod man pages.

---

### Post by syborfical on 2008-02-25
This is why I love this forum. I can use --help :P but if I knew how to use CHMOD ext I wouldn&#8217;t bother posting here at all.. 
I just need some code examples .... 
pretty much a noobs guide to premssions a few examples then i can work it all out ..

It cant be that hard I have 2 users:
Share
Upload

One directory lets just say its /share
How do I make it so the share use can only read ? and upload and RWX?
Thank you

---

### Post by astrotech226 on 2008-02-25
> **syborfical said:**
> 
One directory lets just say its /share
How do I make it so the share use can only read ? and upload and RWX?
Thank you

If you create the group "share" like HermanAB suggested, and add the user "share" to the group "share".  Then do this:

```
sudo chown -R upload.share /share
sudo chmod -R 740 /share
sudo find /share -type d -exec chmod g+x {} \;
```

There are lot's of ways to do this, but this is done in three steps to show what is happening.  The first changes the owner to "upload" and the group to "share" for all of the files and directories inside /share".

The second command goes through and gives rwx to "upload" and read only to "share" and no permissions to everyone else.

The final command will go back through and give execute permission on all the directories to the group "share".  If it doesn't have that, the members of the group "share" won't be able to list the contents or cd into the directories.

---

### Post by syborfical on 2008-02-26
thank you i've got the basics now

---

