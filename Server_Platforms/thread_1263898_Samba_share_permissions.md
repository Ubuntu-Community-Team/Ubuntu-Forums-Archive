---
title: "Samba share permissions"
date: 2009-09-11
forum: Server Platforms
---

### Post by Vunutus on 2009-09-11
Alright, I thought I had this figured out but apparently not.

I'll start by laying out what I want to accomplish here.

-A home share for each user that is only accessible to the user that owns it
-A share called "public" that all users can read, but only the "managers" group can write to
-A share called "manager" that only the "managers" group can read or write to

Here is my smb.conf:
```

[global]                                         
   workgroup = TWINOAKS                          
   server string = ToR Files                     
   wins support = yes                            
   hosts allow = 192.168.1.                      
   security = user                               
   dns proxy = no
   guest ok = no

[homes]
   comment = Home Directories
   browsable = no
   writeable = yes
   valid users = %S

[public]
   comment = Storage (public files)
   path = /var/samba/public
   public = yes
   writeable = yes
   create mask = 0774

[manager]
   comment = Private manager files
   path = /var/samba/manager
   public = yes
   writable = yes
   create mask = 0770

```

I have my "managers" group set up and all required users belong to it. All my shares reside in "/var/samba". I changed the group of each share folder to "managers". As far as I can tell, the home and public shares work fine. The manager share, on the other hand, has some issues. If I go to one of our Windows machines and create a text document on the M: (manager) drive, it works fine. If I go to another workstation and open the M: drive, I can see the document but get a "permission denied" when trying to open it. 

Now, I assume this is because of the permissions are set to 770. I did this with the reasoning that all managers in the office will belong to the "managers" group and since the group has full access to this folder, they should be allowed to read/write all files. If I do a ls -al in the folder I see that the newly created file is assigned to the user's default group, not "managers". I assume this is the cause of the problem.

How can I set up the permissions to achieve my desired result? Is there any way to ensure that all files in a certain folder belong to a certain group?

Also, if anyone happens to spot any other flaws in my setup, feel free to point them out!

---

### Post by Vunutus on 2009-09-12
Bump

---

### Post by abaden on 2009-09-12
You need to set a groupid for the directory. In this case, you would need...
```

chmod g+s manager

```
This will force all new files to be owned by the group of the parent directory, and not by the group of the user.

For more info see this [site]("http://www.udel.edu/topics/os/unix/general/groupsharing.html").


Alex

---

### Post by Vunutus on 2009-09-14
> **abaden said:**
> You need to set a groupid for the directory. In this case, you would need...
```

chmod g+s manager

```
This will force all new files to be owned by the group of the parent directory, and not by the group of the user.

For more info see this [site]("http://www.udel.edu/topics/os/unix/general/groupsharing.html").


Alex

Thanks, that seems to have done the trick! 

Now, I assume that only affects new files. The public drive already has working files in it assigned to the wrong groups. Am I correct in assuming that I can do the following to resolve this problem?

```

cd /var/samba/public
sudo chgrp -R managers 

```

I'm pretty sure this will work, but I always like to be extra-careful before I execute recursive commands (this wouldn't be the first time I destroyed a box with sudo and the -R switch lol)

---

### Post by abaden on 2009-09-14
> **Vunutus said:**
> Thanks, that seems to have done the trick! 

Now, I assume that only affects new files. The public drive already has working files in it assigned to the wrong groups. Am I correct in assuming that I can do the following to resolve this problem?

```

cd /var/samba/public
sudo chgrp -R managers 

```I'm pretty sure this will work, but I always like to be extra-careful before I execute recursive commands (this wouldn't be the first time I destroyed a box with sudo and the -R switch lol)

Yup, that's correct. You can also do 
```

sudo chown -R :managers /var/samba/public/managers

```

The difference between chown and chgrp is chgrp allows an privileged user to change a file's group, provided they are a member of that group and own that file. For example, if I own the file "test" and the permissions are set to "abaden:abaden", and I happen to be a member of the admin group, I can change the permissions of the file to "abaden:admin". Furthermore, I can change the permissions of a file set to "abaden:othergroup" to a group I am a member of. 

Chown can change the ownership of a file to a member and/or group. You just leave out the appropriate part (for example, :managers would change to group managers, obviously). I usually use chown myself.

Best of luck,
Alex

---

### Post by sherl0k on 2009-09-15
also up near the top of the smb.conf there's a line that says "security=user" set that for "security=share" and see if that makes a difference.

---

