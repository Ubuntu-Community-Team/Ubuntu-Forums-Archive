---
title: "Does it make sense to use chmod 700 for directories like bin, root, usr, ...?"
date: 2011-10-02
forum: Security
---

### Post by newhere_m on 2011-10-02
One suggestion for making my personal files and folders is to use:
```
chmod 700 $HOME
```
I wonder whether it will be even better if I use the same command for all subdirectories in lowermost directory (/), i.e., for ./ ../, bin/, boot/, cdrom/, dev/, ..., tmp/, usr/, var/? I note root/, lost+found/ has all permissions for me, the user and all other dirs have mixed permissions. 

Another doubt, in the / directory, there are four entries:
> initrd.img -> boot/initrd.img-2.6.32-34-generic
initrd.img.old -> boot/initrd.img-2.6.32-33-generic
vmlinuz -> boot/vmlinuz-2.6.32-34-generic
vmlinuz.old -> boot/vmlinuz-2.6.32-33-generic 
what are these? In case it is good to apply the suggested permissions to other dirs, should I do the same to these four too?

---

### Post by ~!geek!~ on 2011-10-02
> **newhere_m said:**
> One suggestion for making my personal files and folders is to use:
```
chmod 700 $HOME
```I wonder whether it will be even better if I use the same command for all subdirectories in lowermost directory (/), i.e., for ./ ../, bin/, boot/, cdrom/, dev/, ..., tmp/, usr/, var/? I note root/, lost+found/ has all permissions for me, the user and all other dirs have mixed permissions. 

Another doubt, in the / directory, there are four entries:

what are these? In case it is good to apply the suggested permissions to other dirs, should I do the same to these four too?

 Visit this page about permissions in linux from [http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php) to learn about permissions of files n directories in linux. Will help you avoid many things you should not do! Also, Do you really have all permissions for directories namely /root, /lost+found ! It either means you have messed with chmod along with sudo command or you are logged in as root! See which case applies! Files with 'vmlinuz' in name, you mentioned, are the symbolic links (represented by `-> the location of link`) to the kernel file that is used to boot linux system, FWIK, The old n new in name of files are linked to appropriate files after you install new kernel update! I advice to let the default permissions already set to them i.e. rwxrwxrwx .

---

### Post by Rocket2DMn on 2011-10-02
You should almost definitely not be fiddling with permissions outside of your home directory unless you know exactly what you are doing.  Messing up these permissions can prevent you from accessing what you need and can prevent the software running on your computer from executing properly (e.g. background services).

Those symlinks at the root of the filesystem are to the two most recent kernels installed on your machine.  Not sure why they are there, but perhaps some bootloaders check the root of the filesystem if they cannot find what they are looking for (like if the bootloader gets misconfigured). Again, I wouldn't touch them unless you really know what you're doing.

---

### Post by newhere_m on 2011-10-02
Thanks for warning me not to go ahead.

However the issue with the directories root/ and lost+found/ is worth further investigation. I am sure I have not changed the permissions for these and I am not working as root. I have recently reinstalled ubuntu 10.04 LTS and I am sure about what I am saying. Note the result of ls -l for some directories and symbolic links (inside directory /):
> 
drwxr-xr-x 131 root root 12288 2011-10-02 21:52 etc
drwx------   2 root root 16384 2011-09-29 08:33 lost+found
drwx------  11 root root  4096 2011-10-01 21:14 root
drwxr-xr-x  10 root root  4096 2011-02-11 18:34 usr
lrwxrwxrwx   1 root root    30 2011-09-30 23:27 vmlinuz -> boot/vmlinuz-2.6.32-34-generic
It appears that I have access to directory root/ even if logged in as an ordinary user (confirmed by using the command whoami). However if I do "cd root", I am denied permission to the directory root/. Same with lost+found/. But I can access usr/, etc/ for example. I have no idea why this is happening. (Earlier I have used "chmod 700 $HOME" and even before that kept read permission to .bashrc and .profile to myself and revoked all permission for others.)

---

### Post by SeijiSensei on 2011-10-02
First, let me reiterate the most important piece of advice in this thread:

**Do not change permissions on any directories other than your own home directory unless you're an experienced user and fully understand the consequences!**

You can "enter" /root as an ordinary user with cd, but as you discovered you can't see or modify anything there.  That's the root user's home directory.

Directories like /usr are owned by user/group root and have 0755 permissions.  That means root can do anything to /usr and the directories below it; everyone else can list these directories and read the files therein.  If you change that 0700, ordinary users will no longer be able to run most of the programs on your machine (except for programs in /bin) because you will no longer have permission to execute /usr/bin/programname.

The permissions structure in Ubuntu is quite secure by default; you don't need to "improve" it.

---

### Post by nothingspecial on 2011-10-02
You shouldn't need to change the permissions on system files/folders even if you do know what you are doing.

---

### Post by SeijiSensei on 2011-10-02
> **nothingspecial said:**
> You shouldn't need to change the permissions on system files/folders even if you do know what you are doing.

I've changed permissions in /usr/local from time to time.  I changed the group on /usr/local/src to my own group and marked it writable so I can download source code tarballs directly into it for later compilation.  Issues arise with permissions on /var/www as well.  In cases where multiple users need to post files to the web, it's sometimes easiest to mark that directory as group-writable and assign the web developers to the www-data group.

But, in general, I agree entirely with your statement.

---

### Post by ~!geek!~ on 2011-10-02
> **newhere_m said:**
> Thanks for warning me not to go ahead.

However the issue with the directories root/ and lost+found/ is worth further investigation. I am sure I have not changed the permissions for these and I am not working as root. I have recently reinstalled ubuntu 10.04 LTS and I am sure about what I am saying. Note the result of ls -l for some directories and symbolic links (inside directory /):
It appears that I have access to directory root/ even if logged in as an ordinary user (confirmed by using the command whoami). However if I do &quot;cd root&quot;, I am denied permission to the directory root/. Same with lost+found/. But I can access usr/, etc/ for example. I have no idea why this is happening. (Earlier I have used &quot;chmod 700 $HOME&quot; and even before that kept read permission to .bashrc and .profile to myself and revoked all permission for others.)

 Let me first try to explain the result of ls -l / command for you.  >  drwx------ 2 root root 16384 2011-09-29 08:33 lost+found 
 drwx------ 11 root root 4096 2011-10-01 21:14 root 
 drwxr-xr-x 10 root root 4096 2011-02-11 18:34 usr   Lets start with 3rd line in quoted message. `root root` represents that the owner of the directory /usr is `root` (first `root`) and /usr belongs to a group named `root` (second occurence of `root` above). Now, Take a look at the first string of 3rd line in this quoted message. `d` represents that /usr is a directory. Next 3 characters represent that owner of the directory (root, in this case) has read, write and execute permissions over this directory. Next 3 characters `r-x` means that users associated with group /usr directory belongs to (root group, here) has read and execute permissions but no write permission over this directory. The rest of the string (r-x) is for other users which are neither owner of the /usr nor belongs to group /usr belongs to. (`root` group here)  
 If I have not made any mistake writing this && you are able to follow what I tried, you should understand that in second line of above piece of quoted message that /root is a directory, its owner is root and it belongs to group named root. Its owner (root, here) has rwx permissions over it. The group members (users belonging to the group `root` here) have no permissions (as represented by `---` ) i.e. none of read, write n execute. Similarly, rest of the users have no permissions (again, represented by `---` ). 
 Now lets talk about YOU! You are not root (as you verified using `whoami`, :) ) So you are not owner of /root diretory. Also you don't belong to group root, I assume. So group permissions aren't applicable for you. Therefore, you belong to the third category, i.e. `others`, who don't have any permission over this directory called `/root`. So you can't do anything with /root. If you attempt to do cd /root, it will say `permission denied` (as you mentioned). It will behave similary for ls command and any other command you want to try over this directory. 
 I hope I am making some sense to you!! 
 BTW, Seems like I wrote a lot this time! Phew!
P.S. - If this writing helps you, it implies you hadn't visited the link posted by me in previous reply and I suggest you again to visit that link!

---

### Post by nothingspecial on 2011-10-02
Let me say it again.

You do not need to change the permissions on any file/directory outside of /home.

If you go down that road you will most likely break your system.

---

### Post by bodhi.zazen on 2011-10-03
> **newhere_m said:**
> One suggestion for making my personal files and folders is to use:
```
chmod 700 $HOME
```
I wonder whether it will be even better if I use the same command for all subdirectories in lowermost directory (/), i.e., for ./ ../, bin/, boot/, cdrom/, dev/, ..., tmp/, usr/, var/? I note root/, lost+found/ has all permissions for me, the user and all other dirs have mixed permissions. 

Another doubt, in the / directory, there are four entries:

what are these? In case it is good to apply the suggested permissions to other dirs, should I do the same to these four too?

If you somehow feel the need to increase security beyond the default permissions the next step is to learn apparmor or selinux.

For learning purposes - go ahead, make a back up of your data or install Ubuntu into a VM. Then run chmod -R 700 /

Your next step after that command will be to either spend several weeks trying to fix your system, most quit after 4 weeks or so, but I have seen one success, or to reinstall Ubuntu and restore from back up.

---

### Post by newhere_m on 2011-10-09
What does the command "chmod -R 700 /" actually do? In any case with this I am changing permissions to directories present in /. So is this not similiar to what I asked in my question?

---

### Post by dave01945 on 2011-10-09
> **newhere_m said:**
> What does the command "chmod -R 700 /" actually do? In any case with this I am changing permissions to directories present in /. So is this not similiar to what I asked in my question?


this command will change the permission of **every** file and folder on the entire system so only the owner can do anything with them (read, write or execute) it's not a good idea as [COLOR=red]bodhi.zazen[/COLOR] said it will take a lot to put it back to how it was

---

