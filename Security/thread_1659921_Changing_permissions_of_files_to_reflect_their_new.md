---
title: "Changing permissions of files to reflect their new folder"
date: 2011-01-04
forum: Security
---

### Post by GregoryMA on 2011-01-04
I have a shared folder set up that allows all users on the computer to have access to all the music on the computer.  In the folder with all the music the group 'music' has permission to add and delete files and all users are members of 'music'.  This should allow all users to have complete access to these files, however, when I add files to the folder they retain their original permissions and do not take on the permissions of the folder.  I could change the permissions of the files to reflect the folder every time I add a cd.  But that is annoying.  What I am wondering is if there is any way to make files automatically reflect the permissions on the folder they are moved into.

Thanks, Greg

---

### Post by bodhi.zazen on 2011-01-04
Easiest solution is to change the permissions of the files so they are world readable (755).

Next is to change primary group of you users to 'music'.

Third option is to run a cron script to change ownership and permissions.

You could also use acl .

---

### Post by GregoryMA on 2011-01-04
Thanks Bodhi.zazen.  I decided to set up a script to change the permissions of the folder but I ran it on startup instead of with cron.  It works well.

For those interested:
-I created an empty script: ```
sudo gedit /etc/init.d/music_folder_permission_change
```

-I added the command to the file to make a functioning script.  The command I used was: ```
chmod 755 -R /music
```

-I made the script executable: ```
sudo chmod +x /etc/init.d/music_folder_permission_change
```

-I made it run on startup: ```
sudo update-rc.d music_folder_permission_change defaults
```

Greg

---

### Post by oldfred on 2011-01-04
I have not done it, but see the posts by boneKracker:

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

