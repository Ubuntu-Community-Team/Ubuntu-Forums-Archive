---
title: "sub directories permissions"
date: 2012-08-27
forum: Server Platforms
---

### Post by conradin on 2012-08-27
Hi all,
I have an Apache http server on the 10.04 version of ubuntu. Users who set up a public_html have webpages. but, if they create directories, anything within the directory will get a fobbiden warning when someone tries to navigate to any content in a folder of the public_html folder. 

whats going on here? And how do I fix it? 

heres the stat info about my public_html folder if it helps:
```
$ stat public_html/
  File: `public_html/'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 806h/2054d	Inode: 917795      Links: 4
Access: (0755/drwxr-xr-x)  Uid: ( 1000/     jay)   Gid: ( 1000/     jay)
Access: 2012-08-26 21:19:15.224785613 -0400
Modify: 2012-08-26 21:19:03.933282665 -0400
Change: 2012-08-26 21:19:03.933282665 -0400
```

---

### Post by conradin on 2012-08-30
I solved it, 
I verified that everything was set up right with this article:
[http://askubuntu.com/questions/50493/setting-up-a-web-server-using-multiple-user-accounts](http://askubuntu.com/questions/50493/setting-up-a-web-server-using-multiple-user-accounts)

then saw that in the folder, I had: 
```

$ ll
total 316
drwxr-xr-x 2 jay jay   4096 2012-08-26 23:02 ./
drwxr-xr-x 4 jay jay   4096 2012-08-27 21:48 ../
-rw-r--r-- 1 jay jay    193 2012-08-26 23:03 index.html
-rw------- 1 jay jay 146473 2012-08-26 23:02 linuxchix.html
-rw-r--r-- 1 jay jay 147456 2012-08-26 22:51 .linuxchix.php.swo
-rw-r--r-- 1 jay jay  12288 2012-08-26 21:46 .linuxchix.php.swp


```

I guess I mush have had some problem the last time I was using vim, and changed the permissions or something. ...
got rid of the .swp and .swo files, and did chmod +r to the .html. and it worked. When I tried the copy to another directory I didn't bother to check the file permissions. 

--argh. 
lol

---

