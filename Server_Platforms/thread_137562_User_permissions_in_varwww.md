---
title: "User permissions in /var/www"
date: 2006-02-28
forum: Server Platforms
---

### Post by gmclachl on 2006-02-28
Hi, 
     I am trying to set up a development server in the office. Everything is done apart from one last thing. I need to figure out the best way to set permissions for a folder inside /var/www 

 I currently have 3 users. So I created a group called developers and added the users to it.  I then created a folder in /var/www and ran

   chgrp -R developers /var/www/folder 
   then  
   chmod 764 -R /var/www/folder

  ls -la returns 
 drwxrwxr-x+  2 root      developers 4096 2006-02-28 13:16 folder

 So it appears as if the group have rwx permissions (even though i only want rw) 

However the users still can't create a file inside the directory. 
I then tried acl's and gave the group permission to rw 
 
 getfacl returns 
# owner: root
# group: developers
user::rwx
user:userone:rw-
user:usertwo:rw-
group::r-x
group:developers:rw-
mask::rwx
other::r-x

 Which still didn't work. 

 TBH I am not even sure i am going about it the right way (obviously not as it is not working) 

Any suggestions 
G

---

### Post by wylfing on 2006-02-28
Um, I don't know if it's as simple as it seems to me, but why not:
```
sudo chmod 774 /var/www/folder
sudo chmod g+s /var/www/folder
```

Despite what you might be thinking, you DO want execute permissions on directories that you need to traverse. Execute on a directory simply means you can 'cd' to it. So giving your directory group permission of 6 is probably a bad idea and might be affecting things even though 'ls' doesn't show it.

---

### Post by gmclachl on 2006-02-28
Hmm, almost...As soon as i do that the web server loses permission to view files. I suppose i could add www-data to the group as well. This is turning out to be a bit of a kludge, 

Thanks anyway.
 George

---

### Post by LordHunter317 on 2006-02-28
Here's the deal:[list][*]Apache must have permission to access the directory.  This means www-data must own, group own, have an ACL, or have world access.[*]You don't need ACLs for this, so I would remove them.[*]Here's what you want to do:```
find /var/www/dir -type d -print0 | xargs -0 chmod 775
find /var/www/dir -type f -print0 | xargs -0 chmod 664
chown -R /var/www/dir root:developers
```And everyone will have access.  The first one enables the right permissions and enables setgid propogation so that all new files and directories will be group owned by 'developers'.  The second fixes the files; third, the ownership.[*]Finally, make sure your umask is permissive enough for things to function, like 002.[/list]

---

### Post by gmclachl on 2006-02-28
> **LordHunter317]Here's the deal:[list][*]Apache must have permission to access the directory.  This means www-data must own, group own, have an ACL, or have world access.[*]You don't need ACLs for this, so I would remove them.[*]Here's what you want to do:```
find /var/www/dir -type d -print0 | xargs -0 chmod 775
find /var/www/dir -type f -print0 | xargs -0 chmod 664
chown -R /var/www/dir root:developers
```And everyone will have access.  The first one enables the right permissions and enables setgid propogation so that all new files and directories will be group owned by 'developers'.  The second fixes the files said:**
> Finally, make sure your umask is permissive enough for things to function, like 002.[/list]

 Thanks for the reply however...;-) when i try and run the first command I get an error saying I don't have permission even though I sudo.

I got round that by chow'ng it to a normal user and then running it, and it worked

The secome command I keep getting 
chmod: too few arguments

Thanks 
George

---

### Post by gmclachl on 2006-02-28
Ah...it's working now. 

Thanks
George

---

### Post by LordHunter317 on 2006-02-28
Wow, I was still asslep when I wrote that.  All thst commands should be prefaced with sudo, and the chown command has its arguments backwards.

---

