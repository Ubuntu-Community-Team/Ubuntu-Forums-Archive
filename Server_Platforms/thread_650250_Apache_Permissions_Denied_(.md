---
title: "Apache Permissions Denied :("
date: 2007-12-26
forum: Server Platforms
---

### Post by Syndacate on 2007-12-26
Gah,

I had a PHP upload script (because I don't know anything about MySQL databases), and now it's throwing some error - and it's the same exact way it was on my windows machine where it was working fine.

Ubuntu is blocking write access from some place and I can't figure out where nor why.

This is the error it's returning.
```

Warning: move_uploaded_file(files/invisiblebreasts.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in /var/www/upload/upload.php on line 14

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpDJ6H4D' to 'files/invisiblebreasts.jpg' in /var/www/upload/upload.php on line 14

```

Line 14 is the "<?" (end) of the code.

There's no directory nor file in //tmp/ - Gah, why is it doing this? lol.

Is this the point where I should turn to databases instead of using a PHP script to upload files?

PS:  The setup is:
in /var/www - there is a folder called "upload" (xyz.com/upload/) - in that directory is an HTML form with a "post" method which uses the PHP script (also in /upload/) (that I stole from somebody) and drops it into a directory in /upload/ (upload/files)

:(

Databases look/sound so hard...but it seems with a good file manager the extents are SO much more advanced...

---

### Post by chippy99 on 2007-12-26
Looks like a file permission problem. Who is the owner of the files directory ?
Can you post the php code that is being executed ?

---

### Post by cdenley on 2007-12-26
Did you give the full destination path for the move_uploaded_file argument (/var/www/xyz.com/upload/files/invisiblebreasts.jpg)? What are the permissions on that directory (ls -d -l /var/www/xyz.com/upload/files)?

---

### Post by Syndacate on 2007-12-26
> **chippy99 said:**
> Looks like a file permission problem. Who is the owner of the files directory ?
Can you post the php code that is being executed ?

I am the owner of the computer, directories, so on and so forth, I am the only user (sudo admin), etc. etc.  This is my personal computer, I simply have a server on it as an easier means of transferring files as most "everyday" people don't have an FTP client.  Not to mention for Windows users if they have DAP (download accelerator Plus), which is free, they can resume HTTP downloads.

As for the PHP code, I'll put it here, but I've been using it for almost a year on my Windows machine without a single problem, the code it-self is fine.

```

<html>
<head>
<title>Upload Successful/Unsuccessful Page</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>

<body>
<br><br>
<center><font size="+2">
<?php
$target = "files/";
$target = $target . basename( $_FILES['uploaded']['name']) ;
$ok=1;
if(move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
{
echo "The file ". basename( $_FILES['uploadedfile']['name']). " has been uploaded successfully";
}
else {
echo "An error occured while uploading your file.  Please contact Greg Fotiades at boostedSOHC@gmail.com.";
}
?>
<br><br><br><a href="/upload/">Upload another file.</a></font>
</center>

</body>
</html>

```

[quote=cdenley]Did you give the full destination path for the move_uploaded_file argument (/var/www/xyz.com/upload/files/invisiblebreasts.jp g)? What are the permissions on that directory (ls -d -l /var/www/xyz.com/upload/files)?[/quote]

I gave the "**/www/upload/**", and "**/www/upload/files**" directories full read-write permissions for all, all in group, and myself.  I had a person try uploading the file again - and it failed, same error.

I don't get it, this script worked 100% fine on my apache server which had the same setup (**"/apache2.2/htdocs/upload/"**) and ("**/apache2.2/htdocs/upload/files**").  This whole UNIX file permission thing is nice in terms of versatility, but it really fu8ks with you sometimes, like in scenarios like today.

Would it be smarter to dump this PHP script and start looking at MySQL DB's?  I really don't know anything about them, but it seems as though there's a lot more versatility with them, and i can password protect the database of /files/ and such so people can upload but not see what's been uploaded...but I should be able to do that with file permissions as is anyways.  It worked 100% for almost a year in Windows, PHP5 is still PHP5, so I don't get why it's doing this :(.  All the folders and their parent directories all the way up to /var/ have full read/write capabilities for all.

Somebody's had to run into this problem before...

---

### Post by cdenley on 2007-12-26
If you change

$target = "files/";

to

$target = "/www/upload/files/";

does it work? I'm not sure what the default working directory is.

---

### Post by Syndacate on 2007-12-26
> **cdenley said:**
> If you change

$target = "files/";

to

$target = "/www/upload/files/";

does it work? I'm not sure what the default working directory is.

No, it doesn't work.

This has to do with permissions some place, and I'm not sure where, nor why.

---

### Post by cdenley on 2007-12-26
That's funny, because I installed apache, copied your script, got your error, made my change, then it worked.

```

sudo apt-get install apache2 libapache2-mod-php5
sudo mkdir /www
sudo mkdir /www/upload
sudo mkdir /www/upload/files
sudo chmod 777 /www/upload/files

```

```

cdenley@cdenley:~$ ls -ld /www /www/* /www/*/*
drwxr-xr-x 3 root root 4096 2007-12-26 20:32 /www
drwxr-xr-x 3 root root 4096 2007-12-26 20:32 /www/upload
drwxrwxrwx 2 root root 4096 2007-12-26 20:56 /www/upload/files

```

I'm guessing that I'm confused about what paths you're giving, and that you are using web server paths instead of actual system paths. Either that, or you didn't give the directory or one of it's parents access (+x) permissions for the www-data user.

To set permissions, assuming the full path to the directory you're uploading to is /www/upload/files:
```

sudo chown -R root /www
sudo chgrp -R root /www
sudo chmod -R 755 /www
sudo chmod 777 /www/upload/files

```
This will give everyone write access to /www/upload/files, but not for any parent directories. To test whether it is a permissions problem, you can try
```

sudo bash
su www-data
echo>/www/upload/files/test

```

By the way, the directory you move uploaded files into does not need to be web accessible. It can be any directory on your system that the www-data user can access and write to.

---

### Post by Syndacate on 2007-12-27
> **cdenley said:**
> That's funny, because I installed apache, copied your script, got your error, made my change, then it worked.

```

sudo apt-get install apache2 libapache2-mod-php5
sudo mkdir /www
sudo mkdir /www/upload
sudo mkdir /www/upload/files
sudo chmod 777 /www/upload/files

```

```

cdenley@cdenley:~$ ls -ld /www /www/* /www/*/*
drwxr-xr-x 3 root root 4096 2007-12-26 20:32 /www
drwxr-xr-x 3 root root 4096 2007-12-26 20:32 /www/upload
drwxrwxrwx 2 root root 4096 2007-12-26 20:56 /www/upload/files

```

I'm guessing that I'm confused about what paths you're giving, and that you are using web server paths instead of actual system paths. Either that, or you didn't give the directory or one of it's parents access (+x) permissions for the www-data user.

To set permissions, assuming the full path to the directory you're uploading to is /www/upload/files:
```

sudo chown -R root /www
sudo chgrp -R root /www
sudo chmod -R 755 /www
sudo chmod 777 /www/upload/files

```
This will give everyone write access to /www/upload/files, but not for any parent directories. To test whether it is a permissions problem, you can try
```

sudo bash
su www-data
echo>/www/upload/files/test

```

By the way, the directory you move uploaded files into does not need to be web accessible. It can be any directory on your system that the www-data user can access and write to.

Yeah, I finally got it.

The "**/upload**" directory has to have EXECUTABLE access on it or you can't "run" the PHP script inside :-\.

I dont' like doing so but for the /upload/, /upload/files/, and index.php, I gave full permissions to all.

I think I can take away read permissions to "others" on /upload/files/ without affecting the script, right?

---

### Post by cdenley on 2007-12-27
The upload directory and all it's parents need "access" permissions for the www-data user. The upload directory also needs "write permissions" for the www-data user. These are the minimum required permissions for apache to move uploaded files there:

```

d--x------ 3 www-data root 4096 2007-12-27 07:52 /www
d--x------ 3 www-data root 4096 2007-12-27 07:52 /www/upload
d-wx------ 2 www-data root 4096 2007-12-27 07:58 /www/upload/files

```

x=access for directories
x=executable for files
```

man chmod

```
> 
execute (or access for directories) (x)


www-data only needs read access for all your php scripts.
```

-rw-r--r-- 1 root root  274 2007-12-27 07:52 index.php
-rw-r--r-- 1 root root  670 2007-12-27 07:52 upload.php

```

---

### Post by Syndacate on 2007-12-27
> **cdenley said:**
> The upload directory and all it's parents need "access" permissions for the www-data user. The upload directory also needs "write permissions" for the www-data user. These are the minimum required permissions for apache to move uploaded files there:

```

d--x------ 3 www-data root 4096 2007-12-27 07:52 /www
d--x------ 3 www-data root 4096 2007-12-27 07:52 /www/upload
d-wx------ 2 www-data root 4096 2007-12-27 07:58 /www/upload/files

```

x=access for directories
x=executable for files
```

man chmod

```


www-data only needs read access for all your php scripts.
```

-rw-r--r-- 1 root root  274 2007-12-27 07:52 index.php
-rw-r--r-- 1 root root  670 2007-12-27 07:52 upload.php

```

Yes, but when somebody connects to the server, aren't they an "other" - so wouldn't I need to give "others" read access?

---

### Post by cdenley on 2007-12-27
Apache runs as user www-data (who belongs to group www-data). Any processing done by apache, including writing uploaded files to /tmp then moving them to a specific directory, is done by www-data with that user's permissions. Any files created by apache will be owned by www-data. With file permissions, there is an owner and a group. You can set specific permissions for that owner, that group, then everyone else. "Everyone else" will include www-data, as well as any other user such as nobody. If you don't give "everyone else" access and write permissions, then you need to make the directory's owner or group www-data, then give the owner or group access and write permissions. This would restrict other users or services from writing to the directory, but probably isn't necessary.

---

### Post by Syndacate on 2007-12-27
> **cdenley said:**
> Apache runs as user www-data (who belongs to group www-data). Any processing done by apache, including writing uploaded files to /tmp then moving them to a specific directory, is done by www-data with that user's permissions. Any files created by apache will be owned by www-data. With file permissions, there is an owner and a group. You can set specific permissions for that owner, that group, then everyone else. "Everyone else" will include www-data, as well as any other user such as nobody. If you don't give "everyone else" access and write permissions, then you need to make the directory's owner or group www-data, then give the owner or group access and write permissions. This would restrict other users or services from writing to the directory, but probably isn't necessary.

Gotcha, thanks.

---

