---
title: "Managing users in Ubuntu"
date: 2006-08-10
forum: The Cafe
---

### Post by ubuntu_demon on 2006-08-10
from [http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu) :
> 
I think a lot of people new to GNU/Linux don’t understand the whole “users thing”. This short, practical guide to user management in Ubuntu and GNU/Linux will make it all clear.


A related wiki page : [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

I added (exactly) this to my blog. I might update it if I find relevant links :
[http://ubuntudemon.wordpress.com/2006/08/11/managing-users-in-ubuntu/](http://ubuntudemon.wordpress.com/2006/08/11/managing-users-in-ubuntu/)

---

### Post by ComplexNumber on 2006-08-10
**ubuntu_demon**
i bet you read digg.com  :p

---

### Post by ubuntu_demon on 2006-08-10
> **ComplexNumber said:**
> **ubuntu_demon**
i bet you read digg.com  :p
Yeah I do. There are lots and lots of articles over there. Some are interesting :).

---

### Post by ComplexNumber on 2006-08-10
> **ubuntu_demon said:**
> Yeah I do. There are lots and lots of articles over there. Some are interesting :).
i agree :). i glance at the stories on digg almost every day because i find many of them interesting. i tend to ignore the user comments, though, because i find 80-90% of them to be puerile. i saw the story that you linked to over at digg about 2 hours ago ;).

---

### Post by ubuntu_demon on 2006-08-10
> **ComplexNumber said:**
> i agree :). i glance at the stories on digg almost every day because i find many of them interesting. i tend to ignore the user comments, though, because i find 80-90% of them to be puerile. i saw the story that you linked to over at digg about 2 hours ago ;).
If anyone (including you) knows a nice story feel free to PM me or post the link in the thread about my blog : [http://www.ubuntuforums.org/showthread.php?t=206527](http://www.ubuntuforums.org/showthread.php?t=206527)

---

### Post by ubuntu_demon on 2006-08-10
Let's get a bit back on topic :)

Does anyone know about (similar) articles about managing users ?

Any comments on the article / wiki ?

---

### Post by nalmeth on 2006-08-11
Was there really demand for this? Or was it just done for the sake of documentation? I always thought gnome really streamlined this, so common sense might guide a user to the right place.

I suppose for KDE it is warranted, or if people want to go commando

It's very easy to read, except the pics are a *little* fuzzy. I suppose some people will make use of it

---

### Post by neveceral on 2006-08-11
I don't think, that files sharing between local users is so simple. Look here [http://www.ubuntuforums.org/showthread.php?t=231934](http://www.ubuntuforums.org/showthread.php?t=231934). I can set up the permissions for group of users for "pub" folder, but there is a problem, that i need to set up it manualy for every created subfolders, because the new subfolder don&#8217;t inherit (?) the permissions from parent folder. ACL isn't solution, because there are problems with permissions by cp to "pub" folder.
I still don't know, how to do it simply? I mean, that there are only two solutions - samba or some scripts recursively changing permissions of folders and files. 
Anybody knows better solution?

---

### Post by ubuntu_demon on 2006-08-11
> **neveceral said:**
> I don't think, that files sharing between local users is so simple. Look here [http://www.ubuntuforums.org/showthread.php?t=231934](http://www.ubuntuforums.org/showthread.php?t=231934). I can set up the permissions for group of users for "pub" folder, but there is a problem, that i need to set up it manualy for every created subfolders, because the new subfolder don&#8217;t inherit (?) the permissions from parent folder. ACL isn't solution, because there are problems with permissions by cp to "pub" folder.
I still don't know, how to do it simply? I mean, that there are only two solutions - samba or some scripts recursively changing permissions of folders and files. 
Anybody knows better solution?
Currently the best way to do recursive permissions is using the commandline (chown , chmod).

Luckily Gnome 2.16 included in Edgy will have recursive permissions.

---

