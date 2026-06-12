---
title: "Permissions"
date: 2010-01-05
forum: Server Platforms
---

### Post by mictamcody2000 on 2010-01-05
Hello, Ubuntu Community

I'm adding a new user to the computer. I don't want him to be able to access certain files. Mostly just some PHP files containing my MySQL users password because I run a webserver as well. How would I be able to restrict the other user from reading those files but have MySQL and PHP read them fine?

Thanks

---

### Post by Vegan on 2010-01-05
try

```
man chmod
```

This will give you the manual for changing permissions.

in brief if you want world+dog access including sub-directories.

```
sudo chmod +R 777 /path/file_or_folder
```

The man page as lots of examples.

---

### Post by mictamcody2000 on 2010-01-05
It won't let me do +R, this is what I'm getting:

```
sudo chmod +R 777 /var/www/
chmod: invalid mode: `+R'
```

---

### Post by BkkBonanza on 2010-01-05
You definitely don't want 777 permission for your web files!

It should be -R not +R - this indciates to recurse down subdirs.

You want files to be owned by admin and read-exec by user wwww but not by user fred... for example, assuming www is your apache/php user (use correct name if not)

sudo chown admin:www /var/www
sudo chmod -R 750 /var/www

If a file is owned admin:www then any other user not in group www is "public". Make sure user fred is not a member of www group and he won't be able to read those files. 

You can use different names here as you please but make sure the public permissions are 0 for any relevant files. That's the third digit above, or when listing with ls the third group of flags. 
eg. rwxrwxrwx means 777, rwxr-x--- means 750.

This knowledge is core material so rather than trusting info here you should read up a tutorial on permissions - google.

---

