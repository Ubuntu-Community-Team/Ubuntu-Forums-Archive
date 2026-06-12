---
title: "Help with /var/www permissions"
date: 2010-12-28
forum: Server Platforms
---

### Post by dhtseany on 2010-12-28
[Mods, sorry for the dual post but I believe I posted my questions in the wrong category, under Networking and Wireless. **Please remove the other post**. Thanks!]

First, I've been Googling this all morning and I'm not finding the right answers so I figured I'd throw up a post about this.

Running UB 10.10 Server with LAMP successfully running and well as openssh-server for shell access and SFTP for file transfers.

I'm trying to allow multiple users to access the /var/www directory. At first I could browse the contents of the folder, but attempting to write to the directory gives a permission denied error. After some research, I found that I could take ownership of the directory using
```

sudo chown {username} /var/www

```

and gain write access, however that's not really what I'm trying to do. While my username can now write to the directory via SFTP, I'd really like the members of the www-data group to be able to have inherint write permissions and set ownership back to it's default (aka my UN won't *own* /var/www anymore) since (in the near future) I'll have upwards of 5 PHP developers working out of this box. 

I did find mod_userdir, but that isn't how I want this to work. Ideally, I'd really like each user to only see the WWW folder via SFTP, user's home folders don't matter to me since this will strictly act as a web dev box.

Can anyone make some suggestions as to A) how to do this or B) give me some fresh ideas for what I should be searching for?

Thanks in advance!

Peace
Sean

---

### Post by lungten on 2010-12-28
One way I know of is to use SGID. 

1. You could add users that needs to write to the web directory to www-data group and give the group write permission on the web directory
2. Create a new group and add those users to the group. Then change the group for the web directory to that group and give that group write permission on that directory. AFAIK, its not necessary that the group www-data be set on each of the web directories.

Then you can turn on the SGID ( chmod [-R] g+s ) bit on that directory so that the every file and directory created inside does not belong to a particular user and cause permission problems.

---

### Post by aceofspades686 on 2010-12-28
I'm going to assume you already know how to get everyone in the www-data group, from there what you would need to do is
```
chmod -R 775 /var/www
```
The problem with this is that you'll need to do this and change the group of the file to www-data everytime someone opens up a file, which is of course a hassle.

My suggestion would be to look into access control lists or acl.  It allows you set folder specific permissions that stick and gives you fine-tuned control over how permissions are assigned.  I unfortunately just found out about acl myself, so I can't give a whole lot of tips on how to use it, but this should at least get you going in the right direction.

---

### Post by dhtseany on 2010-12-28
Alright, after some more research I think what I want to do is:

1) Return /var/www's ownership to the correct owner. Anyone know who that was?
2) Set write permissions for /var/www for whoever is in the www-data group. What CLI command would I use?

Thanks,
Sean

---

### Post by lungten on 2010-12-28
> **dhtseany said:**
> 1) Return /var/www's ownership to the correct owner. Anyone know who that was?

It is usually owned by the root
```
chown root:root /var/www
```
> **dhtseany said:**
> 
2) Set write permissions for /var/www for whoever is in the www-data group. What CLI command would I use?

```

chgrp www-data /var/www
chmod g+w /var/www
```

---

### Post by dhtseany on 2010-12-28
Thanks for the help! Well, your commands processed without error, however I'm kind of back where I started. First, I verified that my user was part of the www-data group however when I attempt to write to /var/www I'm again told (via Filezilla)
```

Command:	mkdir "/var/www/New directory"
Error:	        mkdir /var/www/New directory: permission denied

```

I feel I'm so close to what I want to accomplish, just a few commands away from success! Any suggestions on how to proceed?

Thanks again for the help! This is why I've tried other distros but keep ending up back with Ubuntu! :-P

Peace
Sean

---

### Post by lungten on 2010-12-28
I cannot tell you exactly how it should be but I guess you'll have to check your FTP server logs.
It may be that when you login to the FTP server, you need more than just the permissions for your user. 

I am sure you will have logs for the error messages with user names in them somewhere. From there you can find out which user tried to create the directory. Accordingly make sure that user has the necessary permissions.

Good luck.

---

### Post by egpetrich on 2010-12-29
First, verify that you can, in fact, create a directory under "/var/www" from your shell login:
```
mkdir -p /var/www/new_dir_from_shell
```
This is a nice sanity check before worrying about what SFTP is doing.

If you added your username to the "www-data" group while your SFTP connection was open, you may need to close the SFTP connection and open it again. (I know that you have to do this with login shells, but I don't know how FTP and SFTP handle the matter.)

On a related note, do you get permission problems when attempting to upload a regular file to "/var/www"? I would expect that you will either be able to create both files and directories or have problems with both.

I'd recommend setting the set-group-id bit on "/var/www", as discussed earlier:
```
chmod g+s /var/www
```
Then all directories and files that you create under "/var/www" will inherit the "www-data" group. (If your users are going to share data, you probably want this. If you don't want to give your users the option of stomping on each other's data, then you don't want this.)

---

### Post by Joeb454 on 2010-12-29
You could add a link to the /var/www folder to each home users directory with ```
sudo ln -s /var/www /home/**user**
``` Replacing **user** as appropriate.

As for group ownership, you should be able to do ```
sudo chown :www-data /var/www/
sudo chmod g+w /var/www/
```

That would change the ownership to the www-data group, and give write permissions to the group.

---

### Post by kidders on 2010-12-29
Hi there,

One option would be to make all your developers members of a developer group. Supposing you did something like ...```
*Create a group*
# groupadd phpdev

*Tweak the ownership of /var/www and everything in it*
# chgrp -R phpdev /var/www

*Grant write access for all pre-existing files to phpdev*
# chmod -R g+w /var/www

*Grant ownership for all new files to phpdev*
# find /var/www -type d -exec chmod g+s {} \;

*Grant ownership for all new files to phpdev*
# find /var/www -type d -exec chmod g+s {} \;
```
For convenience, you might want to set everyone's umask to something like 0002, so developers get write access to new files by default.

I hope that helps.

Edit: Just a quick note ... Your www-data group should have no human members. Running **sudo chown :www-data /var/www/** is dangerous, and should be used with great care.

---

### Post by che-hai on 2011-01-02
Have anyone used quota permission in var/www/ for www-data user/group?
Thanks!

---

