---
title: "Building Multi-purpose multi user server"
date: 2008-12-21
forum: Server Platforms
---

### Post by ashaiba on 2008-12-21
I have a server built, and I put Ubuntu on it


I put proftpd; apache2; and webmin on it

What I need is to set it up so that I can access this server anywehre from the world. So i did that, i opened the port, and i could do it with my username...

Now; I want to create about 5 other usernames so that my friends can use the server as well, but i don't want them prying through my stuff, so i want them to only see there own files


How can i make it so that I can make multiple usernames and each username has a certain folder they can see.
Digg this postDel.icio.us this postReddit this post Stumble this postFacebook this post
Reply With Quote

---

### Post by HermanAB on 2008-12-21
Proftpd will allow access to the user directories only, by default.

Apache is a different matter, but you can use simple password security using .htaccess in different directories.

---

### Post by cariboo on 2008-12-21
When seting up your users for proftpd make sure you have this line uncommented. Change the line from this:

```
# DefaultRoot			~ 
```

to this:

```
DefaultRoot			~
```

This locks the user in their own home directory.

Jim

---

### Post by ashaiba on 2008-12-21
Thing is. I have folders in my 1TB External Drive which i want them to access, but i want certain folders that only certain people can access, not just their user folder but certain folders in the TB

---

### Post by killerdragon on 2008-12-24
> **ashaiba said:**
> Thing is. I have folders in my 1TB External Drive which i want them to access, but i want certain folders that only certain people can access, not just their user folder but certain folders in the TB

I am pretty sure you can use protfpd to use PAM accounts. If this is the case, and proftpd will honor file permissions, you can set different groups for different folders.

Example:
Folder1
Folder2

You want Joe and Jim to access Folder1 but only Jim to access Folder2.
Assign group1 (you might want to call it something different but this is just an example) to Folder1. Put Joe and Jim in group1, and give group rights rw to Folder1 (don't forget to change the group of Folder1 to group1).
Now, make another group Folder2 and put only Jim in it, and change the group rights to rw on Folder2 and change the group owner to group2.

Now Jim and Joe have access to Folder1, but only Jim has access to Folder2.

Is that what you were looking for?
And again I don't know if proftpd will honor file permissions, but it should. When in double option 2 will work.

Option 2:
In each users home directory you can use mount with the bind option (don't forget to add it to fstab if you don't want to add it every reboot!).

Example:

/home/Joe/
/home/Jim/

/stuff/Folder1
/stuff/Folder2

You want both Joe and Jim to be able to access Folder1.
# mkdir /home/Joe/Folder1
# mkdir /home/Joe/Folder2
# mount --bind /stuff/Folder1 /home/Joe/Folder1
# mount --bind /stuff/Folder2 /home/Joe/Folder2

# mkdir /home/Jim/Folder1
# mount --bind /stuff/Folder1 /home/Jim/Folder1

# = root account (sudo will also work)
Note: Proftpd will not 'follow' folders that are "linked" this is why you need to use the mount option with bind.

---

