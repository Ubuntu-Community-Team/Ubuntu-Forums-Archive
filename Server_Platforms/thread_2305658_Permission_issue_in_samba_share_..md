---
title: "Permission issue in samba share ."
date: 2015-12-08
forum: Server Platforms
---

### Post by gardenair on 2015-12-08
hi,
       In my Ubuntu box I have just configured samba server. I have created a new partition mount it in /etc/fstab on the path /mnt/pdc-share. The partition name is " pdc-share" which is mounted inside  /mnt folder.

with the following command I can see the partition is mounted inside /mnt folder
```
# df -h
/dev/sda6 140G  33M 140G 1%  /mnt/pdc-share 
```

I create a group "pdc" 
```
# groupadd pdc
```


Add the existing  user “smith” into the group
```
#usermod  -g  pdc smith
```


Change the permission
```
#  chmod -R 775 /mnt/pdc-share
```

To change its ownership of  the folder “pdc-share “ to  pdc```

 # chown  -R root:pdc  /mnt/pdc-share

```

the /mnt folder still has root user and root group

# ls -l
```
drwx r- x r-x  3 root   root  7 Dec 7  15:38  mnt 
```

Inside mnt 

```
# ls -l mnt
drwxr-xr-x. 3 root pdc 16 Dec  8 10:46 pdc-share
```

and If I move inside pdc-share
```
# ls -l mnt/pdc-share
drwxr-xr-x. 3 root pdc 16 Dec  8 10:46 pdc-share

```



The issue is "/mnt " in my opinion It does not change it self  the group name. See the attachment 


kindly guide me.
thanks

---

### Post by darkod on 2015-12-08
How is the share defined in smb.conf? Post its configuration so someone can have a look. I don't think it's /mnt permissions issue since /mnt has r-x for everyone, which should allow read and directory search (open).

Also, the way how you added user smith to the pdc group is not how you usually add a user to additional group. If you want to add a user to a new group and keep membership of all previous groups, you need to use usermod -aG <newgroup> <user>.

Double check in /etc/passwd and /etc/group if the users really belong where you think they belong.

---

### Post by gardenair on 2015-12-08
Thanks " [COLOR=#000000]darkod " for your kind reply. Well I first create a new user and then create a new group with the command as I have mentioned .

[/COLOR]```
#usermod  -g  pdc smith
```

I think that I have to detele the user ad then again add the user into group. [COLOR=#000000]usermod -aG <newgroup> <user>[/COLOR]

My group file shows

```
# cat /etc/group
pdc:x:1001:smith
smith : x : 1002:

```

The passwd file

```
# cat /etc/passwd
smith:1001:1001::/home/smith:/bin/bash
```


My smb.conf file  share Defination

 ```
[PDC Share]
        comment = PDC Stuff
        path = /mnt/pdc-share
        valid users = @pdc
        public = yes
        writable = yes



```

---

### Post by darkod on 2015-12-08
When you create a user with adduser by default it creates its group same as the username. That's why in /etc/group you have a group called smith. But because you used usermod with -g you removed smith from group smith and put it into group pdc. Which is not a problem, as long as you are aware of that and if you are OK with it (group smith being empty).

For example, and for the future, if you want to create users for your share(s) directly into the correct group, you can use something like:
```
sudo useradd -g pdc <newusername>
```

The thing is that useradd is the "original" command to add users in linux, and if you look at its man page it has many different options because of that. The adduser is sort of a "shortcut" in ubuntu, but by default it creates a new group named the same as the username. If you want to avoid this, you can create users with useradd -g to tell them to belong to the correct group from the start. This way you avoid creating groups named by the users, which you don't need.

To go back to your problem, the share config looks correct to me. The windows machine you are trying to connect from is working with the smith username, right? When opening shares from windows it automatically tries to use the user from the windows session, so if you are logging into windows with jack and you have samba configured to allow smith, it will not let you in.

PS. I looked at adduser man page in more details now, and it recommends using this command on debian/ubuntu rather than useradd. You can still put users directly into the needed group on creation, but the syntax is little different. According to the man page, you would need to use something like:
```
sudo adduser --ingroup pdc <newusername>
```

That should create the user directly into pdc group, and using the ubuntu recommended adduser command.

---

### Post by gardenair on 2015-12-09
Well I have check all things ,it is ok  (as to my expertise) Well one thing I forget to mention that when I use *ls* command for /dev/sda6 which is new partition for samba share it show me the output

```
# ls -l /dev/sda6

brw- rw- ---. root disk  8, 6 Dec 9 10:50[COLOR=#000000]/dev/sda6[/COLOR]
```

Here it show the group "disk " and the word "[COLOR=#FF8C00]/dev/sda6"[/COLOR][COLOR=#000000] is in Yellow color.I try to show but it will not  visible here with white background . [/COLOR] i think that is why i am not accessing my share ? please guide me

---

### Post by bab1 on 2015-12-09
> **gardenair said:**
> Well I have check all things ,it is ok  (as to my expertise) Well one thing I forget to mention that when I use *ls* command for /dev/sda6 which is new partition for samba share it show me the output

```
# ls -l /dev/sda6

[COLOR="#FF0000"][SIZE=4]b[/SIZE][/COLOR]rw- rw- ---. root disk  8, 6 Dec 9 10:50[COLOR=#000000]/dev/sda6[/COLOR]
```

Here it show the group "disk " and the word "[COLOR=#FF8C00]/dev/sda6"[/COLOR][COLOR=#000000] is in Yellow color.I try to show but it will not  visible here with white background . [/COLOR] i think that is why i am not accessing my share ? please guide me

This is the block device (the raw partition).  See the notation in red!!!!!  You never need to deal with the device permissions for a user.  Look at the file system permissions.  As a matter of fact Samba does not share block devices.  The shared resource is only the directory somewhere in the file system.

---

### Post by gardenair on 2015-12-09
Well thanks for guiding me ,It is a new thing for me .I am not aware how can I fix the issue ?](*,)

---

### Post by bab1 on 2015-12-09
> **gardenair said:**
> Well thanks for guiding me ,It is a new thing for me .I am not aware how can I fix the issue ?](*,)
I've tried to help you before.  I think you need to follow the advice already given.  Search on my name in this forum.  Read the introductory books on Ubuntu system administration; carefully!

---

### Post by gardenair on 2015-12-09
Well I know "[COLOR=#000000][FONT=Ubuntu Mono] chmod" for permission and "chown " for ownership changing and "chgrp"[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] as well .In my case it is drive and I have google and it show i get [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]"[/FONT][/COLOR]Universally unique identifier" using
 "# sudo blkid"

blkid is  new...
[COLOR=#DDDDDD][FONT=monospace]
[/FONT][/COLOR]

---

### Post by ch43 on 2015-12-09
blkid gives you a unique identifier (uuid = universally unique identifier) that is assigned to your devices. So instead of referring to sda1 as /dev/sda1, you will refer to it as UUID="2cf26b03-d061-46a5-a0ff-6add57a0c6f6". Block devices may change names as you add/remove/modify partitions and filesystems, but the UUIDs will always refer to the correct device.

---

### Post by darkod on 2015-12-09
First, you work only with the mount point, in this case /mnt/pdc-share.

Second, if you suspect /mnt is making issues in this case, you can create new mount point like /pdc-share and use that one instead. No need to use /mnt at all.

Third, looking at the ls -l /mnt/pdc-share you have r-x for the group permissions which means group members will not have write rights too. As it is, only root has write rights. I'm sure this is not what you want.

However, that should not be a reason for the share not to open at all. Did you confirm the user you are trying to use from windows corresponds with the username on the samba server? It has to match.

Also, you might need to add it as samba user with something like:
```
sudo smbpasswd -a <username>
```

One of the options is to start testing things one at a time, to find the problem. For example, forget about the valid users limitation at the moment. Try to access it as guest user. For that purpose add to the share definition:
```
guest ok = yes
```

In this case even if the user doesn't match with valid users, it should open the share as guest. That will rule out linux file permissions.

---

### Post by bab1 on 2015-12-09
> **ch43 said:**
> blkid gives you a unique identifier (uuid = universally unique identifier) that is assigned to your devices. So instead of referring to sda1 as /dev/sda1, you will refer to it as UUID="2cf26b03-d061-46a5-a0ff-6add57a0c6f6". Block devices may change names as you add/remove/modify partitions and filesystems, but the UUIDs will always refer to the correct device.The blkid (UUID) not applied to the device.  It is applied to the formatted partition on the devce.  For example if you partition the device so you have 2 partitions (e.g. sda1 and sda2) you will have 2 UUID's.  One for each partition.

The mkfs operation creates the UUID for the partition when the file system is created (formatted).  

Referring to  the device name (sd(x)) when mounting a file system via fstab not a safe thing to do.  The use of the partitions formatted UUID is more consistent.

---

### Post by gardenair on 2015-12-10
ooooh ....Every thing work fine now.  :popcorn:

One thing more for the smbpasswd I want that the user should give himself the passwd.one thing is i shold use putty in windows and when it prompt for 

# smbpasswd -a user1

The user himself write the passwd. Is it is the way or any other method to do it ?

At last "[COLOR=#000000]bab1" and "[/COLOR][COLOR=#000000]darkod ".Many many many thanks for help me.Appreciate you :) How can I mark this post as solve ? I want to mark it as solve.[/COLOR]

---

### Post by darkod on 2015-12-10
Standard users can't use smbpasswd -a because only admin users can do it. Otherwise users would be able to add whom ever they want as share user.

For the linux account, a user can log in and change his own password with passwd. Once the admin gives them the initial password, they can change it themselves.

I am not sure how smbpasswd works in details. Maybe someone with more experience can comment how to avoid typing a password for it. From the man page all it said was that pressing Enter will keep the current password for the user. Maybe that's what you need.

The users should use the linux users, the samba smbpasswd is used only to allow them share access.

PS. This says the same: [http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/](http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/) But it does not mention specifically whether you enter password when adding the samba user too or not.

---

### Post by bab1 on 2015-12-10
> **darkod said:**
> Standard users can't use smbpasswd -a because only admin users can do it. Otherwise users would be able to add whom ever they want as share user.

For the linux account, a user can log in and change his own password with passwd. Once the admin gives them the initial password, they can change it themselves.

I am not sure how smbpasswd works in details. Maybe someone with more experience can comment how to avoid typing a password for it. From the man page all it said was that pressing Enter will keep the current password for the user. Maybe that's what you need.

The users should use the linux users, the samba smbpasswd is used only to allow them share access.

PS. This says the same: [http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/](http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/) But it does not mention specifically whether you enter password when adding the samba user too or not.
Regular users can use smbpasswd.  When used this way```
smbpasswd <user>
```...the user can change their Samba password.

From the smbpasswd man page```
 When run by an ordinary user with no options, smbpasswd will prompt them for their
       old SMB password and then ask them for their new password twice, to ensure that the
       new password was typed correctly. No passwords will be echoed on the screen whilst
       being typed. If you have a blank SMB password (specified by the string "NO PASSWORD"
       in the smbpasswd file) then just press the <Enter> key when asked for your old
       password.

```
Of course this assumes that the user can login (via ssh) or can invoke the terminal from a GUi interface (ctrl+t).

You do have to watch out for libpam-smbpass which will try and sync the user password with the Samba password.

---

### Post by gardenair on 2015-12-11
Thanks for the reply. Well one thing more which I am facing during assigning ownership to the user is  that when I create a directory say "smith" inside "/mnt/pdc-share " add users "smith" ,change their group from "root" to "pdc" assign them assign it own user "smith" it works fine.Steps are below

Create a dir with name "smith"

```
# mkdir Smith
```

```
# ls -l
drwxr-x r-x.  2 root root 6 Dec 8 10:46 Smith
```

Add user "smith" into group pdc

```
# useradd -M -g pdc smith
```

then

```
# usermod -a -G pdc smith
```

Assign the group name of the directory "smith"

```
#chown -R root : pdc /mnt/pdc-share
```

Change the user of the directory "Smith" from root to smith. Note"- The first "smith" is the user name and the second "Smith" is the Directory name.

```
# chown -R smith Smith
```

List the user.

```
# ls -l
drwxr-x r-x.  2 smith pdc 6 Dec 8 10:46 Smith

```

With the same steps I make user "jack".

```
#ls -l
drwxr-x r-x.  2 smith pdc 6 Dec 8 10:46 Smith
drwxr-x r-x.  2 jack pdc 6 Dec 8 10:46 Jack
```

Now suppose I create a new user "Mikel"  user all above steps when I use the command

```
#chown -R root : pdc /mnt/pdc-share 
``` 

It change previous user ownership to root

```
#ls -l

drwxr-x r-x.  2 root pdc 6 Dec 8 10:46 Smith
drwxr-x r-x.  2 root pdc 6 Dec 8 10:46 Jack
drwxr-x r-x.  2 root pdc 6 Dec 8 10:46 Mikel
```

[U]So the ownership of each Directory has been change  with the command #  chown -R root : pdc /mnt/pdc-share
[/U]
Where technically i am doing mistake ? How can I fix the issue?

thanks

---

### Post by darkod on 2015-12-11
The second command from the end. Why are you running chown -R root : pdc /mnt/pdc-share again? You set the folder ownership earlier and no need to do it again. Plus the -R means recursive, and that command changes ownership of all folders inside /mnt/pdc-share to root : pdc.

What you need to do is after creating the user folders, change ownership only on that folder. For example:
```
sudo mkdir /mnt/pdc-share/Mikel (this will create it with owner root)
sudo chown mikel:pdc /mnt/pdc-share/Mikel (this will change the ownership to mikel:pdc)
```

Inmy second command I didn't use -R because the folder after creation is empty. No need to use recursion. You use -R only on folders that have content, and only if you want your command to affect that content too.

---

### Post by gardenair on 2015-12-12
Thanks for your detail reply.The thing  as I understand *there is no need to use " -R "  with chown because when the user "Mikel"  is the owner and is the member of group "pdc" then the file,directory created will automatically belong to that user.*


The bad approach which i use

#chown -R root : pdc /mnt/pdc-share

[I]The professional way which u have mentioned.
[/I]
```
# sudo chown mikel : pdc /mnt/pdc-share/Mikel
```

2- Regarding to guest.I add in my samba share guest = ok

```
[PDC Share]
                comment = PDC Stuff
                path = /mnt/pdc-share
                guest = ok
                valid users = @pdc
                public = yes
                writable = yes
```

When I try to login from guest from windows it not logon from it,as it seams that it need passwd for Guest ! Does gust account need smbpasswd if so i may create  ?

3- The 3rd thing which I want to confirm that when we create a folder in side /mnt/pdc-shhare and pdc-share has further sub directories in this care is it batter to create in side /mnt

```
# mkdir -p pdc-share
```

The reason is pdc-share have further sub directories. In my case I not use "-p" switch when creating the directory # mkdir pdc-share.

Need your valuable opinion about these.

thanks once again for guiding.

---

### Post by gardenair on 2016-01-22
hi,
    My samba server is working fine but some users complain in the common share that they can not move there files or folder to other folder of the group.I keep the permission to the folder " /mnt/pdc-share " as 755 .

Suppose smith create a file and jack is his boss . Now jack say to keep the file or folder into his directory. When the user "smith" try to move  or copy the file in "jack" folder it show "Permission Denied" massage. If i allow 775 then the user can delete file or folders of each other. So is there any middle way to fix the issue ?

---

### Post by darkod on 2016-01-22
There is no middle way. You are allowing 7[COLOR=#ff0000]5[/COLOR]5 which means the group only has read and execute permissions. When the jack folder has 755 only jack has rwx (7) and other group users have rx (5). That's why smith can't create/move files to jack folder.

If you don't wanna use 775 what you could do is create a common (shared) folder for the group with 775, smith can put the file there and jack can get it from there. But that involves both of them, which the boss might not like if he wants smith to do all the work... :)

---

### Post by bab1 on 2016-01-22
> **darkod said:**
> There is no middle way. You are allowing 7[COLOR=#ff0000]5[/COLOR]5 which means the group only has read and execute permissions. When the jack folder has 755 only jack has rwx (7) and other group users have rx (5). That's why smith can't create/move files to jack folder.

If you don't wanna use 775 what you could do is create a common (shared) folder for the group with 775, smith can put the file there and jack can get it from there. But that involves both of them, which the boss might not like if he wants smith to do all the work... :)
+1

As you say the folder is a "shared" area.  The user should only add data that they expect will be manipulated by other users.  If that user is paranoid, they should keep a copy of the data in their own private area.

---

### Post by gardenair on 2016-01-27
Thanks for the reply.Well i want one more little changes, a user system-admin  is also created I want that he should have full rights here in the common share.
By default it also has 755  permission. I have change the permission to 

```
# chmod 775 -R System-Admin

```

But I can not delete other files or folder which are unnecessary made by the users in the common share. Is there any way that system-admin should gain have full rights.

---

### Post by darkod on 2016-01-27
Why don't you add it to the sudo group and it will have full rights using sudo in front of any command? To add existing user to sudo group you can do (as a user that already has sudo rights):
```
sudo usermod -aG sudo <username>
```

For example:
```
sudo usermod -aG sudo system-admin
```

That should be enough without going into the permissions specifics.

PS. Note that this would give sudo rights for the whole server. If you only wanted an admin for the shared folder, this is not the correct way because it presents a danger that user to run other sudo commands.

---

### Post by bab1 on 2016-01-27
> **gardenair said:**
> Thanks for the reply.Well i want one more little changes, a user system-admin  is also created I want that he should have full rights here in the common share.
By default it also has 755  permission. I have change the permission to 

```
# chmod 775 -R System-Admin

```

But I can not delete other files or folder which are unnecessary made by the users in the common share. Is there any way that system-admin should gain have full rights.
I don't understand your problem.  By default all directories created have 775 permissions.  The only exception to that is when the root user creates a directory.  Then the default permissions are 775.  Explain your situation.  It sounds like you are creating directories while acting as root or you have the file share misconfigured.

---

### Post by bab1 on 2016-01-27
> **darkod said:**
> Why don't you add it to the sudo group and it will have full rights using sudo in front of any command? To add existing user to sudo group you can do (as a user that already has sudo rights):
```
sudo usermod -aG sudo <username>
```

For example:
```
sudo usermod -aG sudo system-admin
```

That should be enough without going into the permissions specifics.

PS. Note that this would give sudo rights for the whole server. If you only wanted an admin for the shared folder, this is not the correct way because it presents a danger that user to run other sudo commands.

Any user that you add to the sudoers group becomes a system administrator.  That is the only difference between a regular user and a system admin.  You can also use the sudoer file to allow a user to use a singe command as root also.

---

### Post by gardenair on 2016-02-08
I really Appreciate all for helping me. Things are going fine. :)

---

