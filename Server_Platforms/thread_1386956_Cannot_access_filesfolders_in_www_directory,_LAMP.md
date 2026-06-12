---
title: "Cannot access files/folders in www directory, LAMP"
date: 2010-01-21
forum: Server Platforms
---

### Post by Zigon on 2010-01-21
Just installed lamp, I can access phpmyadmin mysql is set up and everything. When I try to view a directory ([http://localhost/folder/index.php](http://localhost/folder/index.php)) I get an access denied error.

EDIT: I changed the permissions of the "folder" folder itself, I can access everything in that directory now but not any other folders in it. Do I really need to go through every folder every time and change the permissions?

---

### Post by gobbledigook on 2010-01-21
pretty much.... but you should use the -r/-R operand so it chmods the dirs recursively.

---

### Post by dwhitney67 on 2010-01-21
With the little information you provided, I have no idea whether you shot yourself in the foot, or slapped a band-aid on it.

If you need to change all of the permissions, or ownership, on a folder that contains many sub-directories and/or files, use the -R option with the chmod/chown commands, or alternatively use the find command.

For example, to change ownership of the 'www' directory, and all of its contents to root:
```

chown -R root:root www

```

Permissions, are a little trickier, because you want folders to have one type of permissions, and files another.  This might be what you want:
```

#changes permission on all directories within www
#
find www -type d -exec chmod 755 {} \;

#changes permission on all files within www
#
find www -type f -exec chmod 644 {} \;

```

---

### Post by ttoilleb on 2010-01-21
Another option, edit /opt/lampp/etc/httpd.conf then look for

```

User nobody
Group nogroup

```

In my httpd.conf, they were about 1/3 of the way in.

Change them to reflect your user and Group  root.  This assumes your user is in group root.

Last, if required, chmod the directories to your user and group root as others have described.

Doing this gives you the advantage that you can edit the files in your directories without having to sudo/gksu.

---

### Post by Zigon on 2010-01-21
Alright thanks everyone!

---

