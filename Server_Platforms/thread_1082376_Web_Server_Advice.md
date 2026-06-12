---
title: "Web Server Advice"
date: 2009-02-27
forum: Server Platforms
---

### Post by jinskeep on 2009-02-27
I'm in need of a little advice on setting up a Ubuntu web server.

I'm going to be running several websites on this server, starting with 20 and growing from there.

Development is standard LAMP and we're in the process of implementing git for source control.

Currently, when starting a new site. I create a new user. Put a www folder in there, and then a htdocs folder in that. Drop the index in the htdocs. Add/Enable the file for apache and everything is set.

The problems with this is that we have several developers. Different developers work different ways (something I'm working on changing). Some SSH straight in and modify files. Some FTP down, change file and FTP back up. Some use git to pull, commit then push back up.

The problem is creating a new user for each site. On SSH, the person SSH's in, sudo's over to root and makes the changes. If it's a new file the chown it to the right permissions. If they are FTPing, they have to get the FTP username and password (new one for each website) ftp back up, then ssh in and change permission if needed. FTP is a huge pain.

What I want...

I want each developer to have their own user/password, and be able to add/delete/modify the websites. Then, if a developer leaves we can shut off their user and they won't have ssh, ftp or any access anymore.

I'm still a little new to Linux/Ubuntu systems. I've got a good understanding I'm just still a little green with setting up larger permission based systems.

Any advice or how you set up your web servers would be greatly appreciated!

---

### Post by martien on 2009-02-27
Well first of all, what interface do you want? Web or console based?
There are many web applications - webmin (example). You can add accounts for your developers.
If you look for something console based.. hmm.. i think its better to write something own and its better to be web based than console.
You also can configure your ftp server to use a database rather plain text files and so you will be able to manage your ftp users dynamically.  
You said something about the many folders you must create every time you add new user. Well, simply you can add everything you want to be directly set into new user's home dir by creating this files/folders in /etc/skel.
I wrote everything for a application, cause creating/using application is making all your work similar and in the same style. Good luck.

---

### Post by E_K on 2009-02-27
Just a note, installing webmin is a nice invite to all the hackers out there, it has major security problems.. look into it.

If you do decided to use it keep it local.

---

### Post by jinskeep on 2009-02-27
As of now, everything is console based. I will probably keep it this way as security is the main reason we are looking at this issue.

Basically, would would be the best way to manage a way for 10 developers to go in and modify the files for 20+ websites all set up on the same Ubuntu server.

---

### Post by Yashiro on 2009-02-27
Create a group called webadmin and add all the developers to it?

Assign the rights they need to directories/files and don't let them use sudo to gain root access.

---

### Post by jinskeep on 2009-02-27
I had thought about this but...

The rights for all of our files (and the default) is 755. To assign them to that group I would have to give all the files/files permissions of 775.

Is this general practice for a LAMP web server?

I assumed it was standard to give website scripts and files a permission of 755.

---

### Post by hyper_ch on 2009-02-28
> I want each developer to have their own user/password, and be able to add/delete/modify the websites. Then, if a developer leaves we can shut off their user and they won't have ssh, ftp or any access anymore.

I'd use mysecureshell to create system users and then lock them into /var/www

Then I would make it so that the files in there are owned by one user

And then I would just alias the other users to that one by giving them the same UID in the passwd file.

That way:
- each user can read/write to /var/wwww
- you can easily remove a user without affecting the others
- they are locked into /var/www

I'd also deny them SSH access and only give sftp capabilities.

---

### Post by jinskeep on 2009-02-28
I'm probably making this to complicated but....

"WebAdmins" need to be able to log SSH in and even sudo over to root. (we have a lot of custom cron jobs process that don't always run right and need to be manually fixed, ect.)

I need to give them full access (RWX) on all websites. (without having to sudo over to root).

Each WebAdmin needs to have their own username/password.

When a WebAdmin leaves, I want to be able to delete their username and remove there FTP, sFTP, SSH and git push/pull/clone access. (git I believe uses SSH).

I'm thinking more and more I'll have to create a group and add all webadmins to this group. I just worry about when new files are created and FTP/git pushed that they will have the wrong permissions.

---

### Post by hyper_ch on 2009-02-28
or do as I laid it out...

---

### Post by jinskeep on 2009-03-02
You plan doesn't completly work as I HAVE to give out admins SSH access with the ability to sudo over to root.

I like your idea about aliasing the users with the same UID. I didn't realize you could do that. Are their any potential problems with doing this?

---

