---
title: "SAMBA Share Read-only"
date: 2013-05-02
forum: Server Platforms
---

### Post by icedragon34 on 2013-05-02
Hey guys second time posting about this but I have figured out that it is due to trying to share only on the second hdd that is in the server but in the end I still need to get this working. Windows is showing all the files that are under /samba/SHARENAME are read only when under ubuntu they are all 775. I have checked the mounts and even the create and they are all within the right settings where create is 775 and the disk mounted is 755 etc etc. I have looked into many things but no anvil all the same is there something wrong with samba I have set up the config properly to link to the mounted drive etc.

If you guy need me to post extra like script or screens I am willing to give so that i can get this done and keep working on this decrepit website left for me to work on...

---

### Post by darkod on 2013-05-02
What user are you using to connect from windows, the same as on the samba server?

Because 775 means RW only for Owner and Group. The last 5 means RO for all the rest.

The permissions are owner-group-all and the number is a sum of 1 - execute, 2 - write, 4 - read

So, if the third number is 5 that means read and execute for all, without write.

For share open to all you need 777. With 775 only the owner and the group would have RW.

---

### Post by icedragon34 on 2013-05-02
The user I am using from windows is an user that I have created to access all the files under the samba share and the user groups I have chowned it to are root:users if this is incorrect I will change but as far as i know this is what I want. Another thing is I did try to run it 777 but it still showed up as read only.

---

### Post by darkod on 2013-05-02
Windows might not be sending the user correctly too, especially if it doesn't work with 777 too. There is no way not to work with 777 regardless which user you use.

But does the user you create belong to the same <users> group? Because if you don't specify a different group when creating the user or add it later to the group, it will create a new group named the same as the new user.

You can see all users and groups with something like:
cat /etc/passwd
cat /etc/group

---

### Post by icedragon34 on 2013-05-02
The users will only show up in the groups while logged in correct? if not then I will have to add users to the users group (they should already be in the users group by default). also would allowing guest (I don't want to) to access files work?
What I really would like is for a group of people to be able to log into a share and work on files and save them to the share and have a share for a few people to see but they can get to the other files under the same account (I have it set up as users allowed and there are 2 users both can access the main files and one can get into the financials)

---

### Post by darkod on 2013-05-02
No, there is no users group. This is not Active Directory where each user goes to Users group by default.

In linux, if you add a user called dragon for example, with:
adduser dragon

That will create a user called dragon and a group called dragon. Not users. You will have to create a separate user/group and then add other users to it.

For example make it sambashare.

```
sudo adduser sambashare #(this will also create group sambashare)
sudo chown -R sambashare /path/share
groupadd user1 sambashare #(this should add the user user1 to the group sambashare if I got the syntax right)
```

After that all the users should have RW rights on the share since the user/group sambashare is the owner.

---

### Post by icedragon34 on 2013-05-02
The correct syntax is 
usermod user groupname #(this will add the user to a group)

Also don't forget to put user then group for chown ex.
sudo chown -R root:sambashare /path/share

I am not sure if this has fixed it but I need to restart to find out

---

### Post by darkod on 2013-05-02
Sorry, I don't use them often, don't know the syntax from the top of my head. You could have set owner to sambashare and that will allow it full control. Although as member of the group it should allow the sambashare user full control too.

And now thinking about it, for changing the group owning the folder it would actually be:
sudo chgrp -R sambashare /path/share

if I'm not mistaken again.

---

### Post by icedragon34 on 2013-05-02
Well i just tried this if I select multiple files they show up as non read only but when i select only one it shows up as read only also that did not seem to help

---

### Post by icedragon34 on 2013-05-02
I tried chgrp and the line had no sytax errors so I am restarting now

---

### Post by icedragon34 on 2013-05-02
yea no go on this still not working :( so frustrating

---

### Post by darkod on 2013-05-02
In the smb.conf in the share definition, do you have:
read only = no

---

### Post by SeijiSensei on 2013-05-02
If you do not need to track which users created which files, then you can use the "force user" and "force group" directives in the share definition in smb.conf to force all files to be owned by a single Unix user.  Create a user, say "admin," then give admin full privileges on the share.  Suppose you are sharing the existing directory /srv/share.  Then you would run:

```

sudo adduser admin
cd /srv
chown admin:admin -R share
chmod 750 -R share

```

Then in smb.conf add 
```

force user = admin
force group = admin

```
to the definition for the share.  Restart Samba.  

Now all file transactions will happen with admin as the owner regardless of the identity of the logged-in user.

For more complicated arrangements using groups, I suggest you read [this section of the Samba manual](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2611888) which covers all the various access control features of Samba.

---

### Post by icedragon34 on 2013-05-02
in the read only I have it set as no. One of the first things i tried. also when i tried to do the add user and force when logged in and it still didn't work.

---

### Post by Elfy on 2013-05-02
Please stop posting duplicates.

Your others have been jailed.

---

### Post by icedragon34 on 2013-05-02
I think I have found a solution when windows is trying to figure out the permissions for the user since there are non defined to windows it automatically assumes no control even if the user is root... not sure what is going on there but apperently samba isn't telling windows what is going on.

How I fixed it was by going into the security (tab under properties in windows) and granting full control over the admin user and group.

Thx For the help

---

### Post by icedragon34 on 2013-05-02
Elfy that was a mistake and is there a delete button? never saw it if there was one.

---

