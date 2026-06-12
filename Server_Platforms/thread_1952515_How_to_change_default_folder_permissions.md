---
title: "How to change default folder permissions"
date: 2012-04-04
forum: Server Platforms
---

### Post by kmcclure on 2012-04-04
We have a server that is running 10.10.  There is an application on it installed in /var/opt/newdirectory.  The umask of /var is 0022, resulting in default permissions of 755 for all directories.  There is a directory with a path of /var/opt/newdirectory/users that needs to have permissions of 777 for that directory and everything below it.  How do I set the default permissions of /var/opt/newdirectory/users to 777 without affecting the upper level directories?

Thanks!

---

### Post by SeijiSensei on 2012-04-04
```

cd /var/opt/newdirectory
sudo chmod 777 -R users

```

However before you do this, you might want to think about more secure arrangements than letting all the users trash each others' files by giving them all write permissions to all directories in the "users" tree.  Can the users be assigned to groups with different permissions?  Are they writing the files themselves, or is the application doing it?  If the latter, is the application running as a separate user the way, say, Apache does?  If so, you may want to grant write permissions to the group the application pseudo-user is in, but not give write permissions to the users themselves.  Giving everyone read/write/execute everywhere should always be the very last option.

---

### Post by Morbius1 on 2012-04-04
I may be reading the original post incorrectly but it sound like you want to set the default umask to 000 for only one specific directory such that all new subfolders of users will be 777 and all new files within that folder will be 666. I don't know if you can do that as specified - at least not using standard Linux permissions. You can achieve this by doing something completely different however:

Install the following package:
```
sudo apt-get install bindfs
```And run the following command:
```
sudo bindfs -o perms=0666:+D /var/opt/newdirectory/users /var/opt/newdirectory/users

```That's going to need some explanation since it looks like a typo. What you are doing is using bindfs to mount a directory to itself with a "view" that has permissions defined in the bindfs statement. So all files will be 666 and all folders ( the +D part ) will be 777. 

[COLOR=Blue]****** [COLOR=Black]Note that this is a view of that folder.[/COLOR][/COLOR] If you were to unmount it:
```
sudo umount /var/opt/newdirectory/users
```All the subfolders will be 755 and all the files will be 644.

If that works for you then you can add that line ( without the sudo ) to rc.local to have it run at reboot. You can also set up your own Upstart job to do this.

**[COLOR=Blue]**[/COLOR]** Also note that this will work for Ubuntu up to and including 11.04 and so far it looks like it works for 12.04. It will not however work for 11.10 because of a sophomoric mistake in the dependencies for the bindfs package.

---

### Post by kmcclure on 2012-04-04
Morbius1,

Thanks for the input.  You did read the question correctly.  I will look in to that.

---

