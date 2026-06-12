---
title: "Run Apache Under Group Owner"
date: 2009-01-27
forum: Server Platforms
---

### Post by etorvinen on 2009-01-27
I searched and found nothing, hope someone can help. 
Concidering switching back to windows! LOL

I installed ubuntu server edition. All went very well.
But, when I upload something using php to my webserver. It changes the owner to wwwdata. Basically, I want apache to run under the current user group site owner.

I run multi sites for friends/family. But, when you use php or perl to upload something. It changes the ownership to wwwdata. And if you have a webapp that edits theme files aka wordpress. wordpress screams. Saying that it does not have permissions to edit.
The only thing fixes is to change to chmod 777 but, I really do not want to do that. This is because wwwdata is the last 7. Public.

I tried to add SuexecUserGroup usernamesiteowner groupsiteowner. to the apache conf but still apache wants to change the ownership to wwwdata.

Is there any way to change this.. maybe a mod?


Can you use a varable in the conf file?
User $USER
Group $USER

---

### Post by volkswagner on 2009-01-27
You will want to add the user to the www-data group.  I don't know the commands off hand.  If your user is yourname than add yourname to the www-data group.

---

### Post by cariboo on 2009-01-28
You could use the adduser command eg:

```
sudo adduser <username> www-data
```

to add a user to the www-data group.

Jim

---

### Post by etorvinen on 2009-01-28
Thanks volkswagner and cariboo907, I was having one of thoes days.

Something so easy, yet it did not come to mind.
I will indeed try it.


I did as you requested, but the problem still persists.

I will give more detail of my conf.

Each User has its own group. by username.
and added www-data as a secondary group.

Using wordpress. The Editor does not like to edit the template files.

...

---

### Post by etorvinen on 2009-01-29
Ok I am still waiting for a response.
Any more ways.

I really do not want to chmod 777. 
Which is the worst advice i ever heard.
[http://ubuntuforums.org/showthread.php?t=9685](http://ubuntuforums.org/showthread.php?t=9685)

---

### Post by etorvinen on 2009-01-29
Is the developers on vacation or something?

---

### Post by etorvinen on 2009-01-30
I am probably going to switch to a windows server.
Ubuntu has to many issues

---

### Post by volkswagner on 2009-01-30
I am not familiar with wordpress.  Does it run as a user.  Perhaps you need to add the wordpress user to www-data also.

Administering a secure server often times requires changing file permissions.  Depending on FTP clients, upload methods, etc.  For file permissions to be preserved in the upload process, additional commands may be required. In the end whenever files are added, permissions need to be verified that group permissions are allowed for www-data.

---

### Post by etorvinen on 2009-01-30
Wordpress uses the php upload function.

so I guess I am looking for a way to make either apache run as the user or php.

I got suexec installed. with the default LAMP installation.
As i read other forums it says php needs to be run as CGI rather a apache module.

How do you convert this.

---

### Post by cariboo on 2009-01-30
If windows works better for you why not change?

Jim

---

### Post by etorvinen on 2009-02-01
Actually Ubuntu is running better... I was messing around.

After trying ubuntu. I am likeing it more.
Its just this minor issue.

I guess in the mean time. I have to run a chown manually.
Since I run a multi user system. I do not want to set 777.

also I have quotas set up. and set www-data to 10MB. make sure the server has a limit.

If anyone finds a way to make php or apache run as the current user. Let me know. I will post if I find anything else out.

---

### Post by inphektion on 2009-02-01
> **etorvinen said:**
> 
Each User has its own group. by username.
and added www-data as a secondary group.
...

I think you did it backwards.  From what you wrote it looks like you added www-data to the user's group.  
You want to add the user to the www-data group.  vi /etc/group and look for www-data.  at the end of the : just add your usernames separated by comma's.  
That works for me and should work for you.  I have same situation with php uploads.

---

### Post by etorvinen on 2009-02-02
So... make the www-data group as primary group and the usernames groups as secendary.

I have not tryied that yet.


This is what I did:

Added Users to www-data and [username] groups.
Then I changed the primary group from [username] to www-data.

I logged in to wordpress and proof editing themes in wordpress now enabled.

---

### Post by etorvinen on 2009-02-02
One step forward 2 steps back.

It works edits now works with php. but. forsome reasone the owner stays the same... as www-data does not change to [username] owner.

I have quotas enabled. and for every file the www-data has it counts.

www-data is limited to 10mbs.
[username] is limited to 2GB

So the issue occurs when people fills up the www-data quota. new uploads gets disabled.

---

### Post by brack on 2009-03-10
Yeah I would also like to see php created files be username:usergroup owned rather than www-data:www-data I could manage to do this if I use php5 fastcgi mode but setting this up with existing typo3... was complicated for me. This is separate topic, but I have followed some tutorials and set fastcgi fine and all things were working fine but typo3, so I moved back to mod-php5 and apache gives it's own user and group to all file created by scripts. 
Continue to look for solution.

---

### Post by etorvinen on 2010-02-18
just found out the main issue...

used chown the directory to www-data

sudo chown -hR www-data sitefolder
from that i read -hR it changes the owner and all files in a folder to the choosen. In my case www-data since apache and php was being run under that user account. It also seemed to fix wordpress's auto install.

sending what i found out... sorry for the lateness

---

### Post by mbehamin on 2010-02-18
By default all the file created in Linux has read permission for all the user! what exactly the problem?

---

