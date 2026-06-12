---
title: "Ownership and Permissions"
date: 2007-09-03
forum: Server Platforms
---

### Post by Dylnuge on 2007-09-03
Hello,

I have a simple scenario and was wondering what I needed to do. I am using Apache and a few other technologies to test websites on my PC. The /var/www directory is automatically owned by root, and I do not wish to change this. Instead,  I wanted to make everyone who logs on and should have access to the website tests have said access. I started by creating a group called web (number 1001 is OK, right? It won't interfere with when/if I create a user 1001?), then using this command:
```
sudo chgrp -R web /var/www
```
So far, so good. Now what I want to do is:
1. Make the group permissions on all files the same as the root permissions. There are some executables in there, so a simple chmod g+rw won't do the trick.

2. Make it so all files in there are automatically created as a part of the web group with rw or rwx access in the group permission.

Is there any way to do this?

Thanks,
Dylan

---

### Post by Dylnuge on 2007-09-03
Ok, it seems that this is not working the way I expected it to. Here are my permissions, as set on the /var/www directory:

drwxrwxr-x  8 root web   4096 2007-09-03 20:56 www

Now, according to this, the web group has rwx permissions for the directory. Unfortunatly, I don't have rwx permissions, just the standard r-x permissions everyone gets. I am in the web group, but I get a standard permission denied on a mkdir command inside the www folder. For example,
```
mkdir /var/www/test
```
returns:
```
mkdir: cannot create directory `/var/www/test': Permission denied
```

I want to run Aptana with the workspace set to /var/www/aptana, so that my code is immediately ready for testing, and so that I can link into my installed spry, MochiKit, and Ext libraries, in addition to TG and RoR apps I have created. If I get this working, so I do not need sudo to create files in the www folder, then I should be able to run aptana as user and still do this, correct?

And of course, I still need help with the original problem, once the group stuff is settled.

---

### Post by scxtt on 2007-09-03
what's the output of **cat /etc/group | grep $USER**?

---

### Post by Dylnuge on 2007-09-03
```
adm:x:4:dnugent
dialout:x:20:cupsys,dnugent
cdrom:x:24:haldaemon,dnugent
floppy:x:25:haldaemon,dnugent
audio:x:29:dnugent
dip:x:30:dnugent
video:x:44:dnugent
games:x:60:dnugent,root
scanner:x:104:cupsys,hplip,dnugent
netdev:x:112:dnugent
lpadmin:x:113:dnugent
powerdev:x:115:haldaemon,dnugent
admin:x:117:dnugent
dnugent:x:1000:
web:x:1001:dnugent,root

```

---

### Post by scxtt on 2007-09-03
is "web" your primary group?  what's **cat /etc/passwd | grep $USER** show?

group changes won't take effect until you login again ... so if you made those changes and didn't log out, that may be the only reason it's not working as expected.

my /var/www/localhost/htdocs/ directory is owned by apache:apache - i added myself to the apache group but couldn't make a test directory in htdocs until i logged out and back in ...

---

### Post by Dylnuge on 2007-09-04
I rebooted and it worked. Still need to know how to change everything to give group full read/write/(execute) privlages and mabe web the group automaticly for everything in the www folders.

Until I figure that out, I need to keep running the chgrp -R web www comand over and over, because I add more stuff contently. And no, my default group is dnugent, even though I am not a member. As it should be-I don't want other users to have access to my files (web users would have access to my files if my default group was web), but I need access to the /var/www folder.

---

### Post by Dylnuge on 2007-09-04
Anyone. If root creates a file, it is owned by root, and group is root, and if I create a file, owned by me, group is me. The thing is, I want to somehow be able to change this. The default owner is fine, but I need to make it so that all files in the /var/www directory are group web, and so that all owner permissions are granted to group. Constantly using chgrp and chmod gets tireing. Isn't Linux about automation?

---

### Post by scxtt on 2007-09-05
it's possible, i think you can set a "sticky bit" for /var/www that will make it so all files created there will be **$USER:web** when created.

do something like:

**sudo chmod 2775 root:web /var/www**

after doing that, any file created by users in "web" should be able to create files w/ user:group of $USER:web ... worked for me w/ a simple test ...

---

### Post by Dylnuge on 2007-09-05
Should that be something besides chmod? I get the error that there is no fle/directory named root:web.

If I do it without the root:web thing it works somewhat. All files created belong to me, but are in group web, which is right. Unfortunatly, the default permissions only give group users read access, which is not right. How do I change the default permissions?

---

### Post by scxtt on 2007-09-06
yes chmod is correct, but as you figured out for yourself, you don't need the **root:web** - i must have been combining two thoughts into one command :p ...

if /var/www has ownership **root:web** w/ the group sticky-bit set - any persons in that group should have the permissions given by the group setting of /var/www

---

### Post by Dylnuge on 2007-09-06
Great. Is there any way to change the default permissions for a file from rw(x) owner r-(x) group to rw(x) both, r others?

---

### Post by scxtt on 2007-09-06
set the umask for any user you want to have privs like that ... in the .*rc file for the shell they use (.bashrc. .zshrc, etc.) ... by default it's 022, looks like you want 002 ... you can also do it on a "per directory" scenario, but that might be overkill for this scenario ...

---

### Post by Dylnuge on 2007-09-06
Sorry, I can't seem to find what you want me to change in my .bashrc. Will this make it so that files in /var/www have the permissions rw-rw-r-- or rwxrwxr-- set automaticly?

---

### Post by scxtt on 2007-09-06
probably not a "change", more of an addition ... when you're in a terminal window, type **umask** - that will show you your current umask setting - if you've never messed w/ it, it's most likely 022 or rwx | r-- | r-- ... if you put **umask 002** in .bashrc and source it, when you type **umask** again, you should see a new value that will be used when creating files/directories ...

to source it, type:

. ~/.bashrc

this will work well when you're in front of the box, you may need to make sure you have .bashrc sourced in .bash_profile if you login remotely often ...

---

### Post by Dylnuge on 2007-09-06
Ok. Will this make it apply to every file, or just the ones in the web group?

---

### Post by scxtt on 2007-09-07
it's system wide for any user who has their umask set in any way ... so if a user has a umask of 002 and their main group is *web*, all files created should be rw- | rw- | r-- ... so a file in their home directory could also be read/writen by someone in the *web* group, depending on the execution permissions of their home directory ...

i was reading about umask in one of my o'reily books and it seems you can put a **.entry / .exit** file in directories that can set/reset umask settings by changing the way cd behaves ...

---

### Post by Dylnuge on 2007-09-09
Great, thanks!

(Sorry about the delay on reply).

---

