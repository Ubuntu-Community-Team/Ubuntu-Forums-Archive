---
title: "Owner/rights problem with apache"
date: 2004-12-30
forum: Server Platforms
---

### Post by Paco on 2004-12-30
Last week i installed Ubuntu on my server. It was supposed to be temporarily but after trying it I'm starting to reconsider that.. :)

Everything's been working great until a friend of mine installed a forum and a gallery, both running PHP. I now have this small but enormously disturbing problem!
Since he is the owner of hise home folder ha can upload and overwrite files using the FTP, and thats just how it's supposed to be. But while he is the owner of the folder apache can't edit the files it wants to when using the forum and gallery. It just keep making errors and complaining about not having the rights to edit config files and so on. This is starting to get on my nerves since I have to change the owner everytime he's going to do anything with his page..

Is there anyone here that has a simple answer to my problem? 

I hope you understand my problem. I'm not that great in english but I've given it a shot!  ;-)  :)

---

### Post by zeroK on 2004-12-31
[QUOTE=Paco]Last week i installed Ubuntu on my server. It was supposed to be temporarily but after trying it I'm starting to reconsider that.. :)

Everything's been working great until a friend of mine installed a forum and a gallery, both running PHP. I now have this small but enormously disturbing problem!
Since he is the owner of hise home folder ha can upload and overwrite files using the FTP, and thats just how it's supposed to be. But while he is the owner of the folder apache can't edit the files it wants to when using the forum and gallery. It just keep making errors and complaining about not having the rights to edit config files and so on. This is starting to get on my nerves since I have to change the owner everytime he's going to do anything with his page..

Is there anyone here that has a simple answer to my problem? 

I hope you understand my problem. I'm not that great in english but I've given it a shot!  ;-)  :)[/QUOTE]
 chmod 777 on any folder the PHP software has to write to. An alternative would be to install PHP as cgi with suexec ;-) Probably an overkill if you don't plan to make a hosting service out of this box *g*

---

### Post by Paco on 2004-12-31
[QUOTE=zeroK]chmod 777 on any folder the PHP software has to write to. An alternative would be to install PHP as cgi with suexec ;-) Probably an overkill if you don't plan to make a hosting service out of this box *g*[/QUOTE]


Okay. But isn't setting chmod 777 an security risk?

---

### Post by zeroK on 2004-12-31
[QUOTE=Paco]Okay. But isn't setting chmod 777 an security risk?[/QUOTE]
 For what does the software need write access? Avatars and things like that? 

True, 777 is a security risk on multiuser system but keep the rest of the server secured not really much should happen. Also keep the folders and files only as long as really necessary on 666 or 777. For example if your script only wants to create a config file during the installation you can change the permissions on this file afterwards again.

---

### Post by Paco on 2004-12-31
[QUOTE=zeroK]For what does the software need write access? Avatars and things like that? 

True, 777 is a security risk on multiuser system but keep the rest of the server secured not really much should happen. Also keep the folders and files only as long as really necessary on 666 or 777. For example if your script only wants to create a config file during the installation you can change the permissions on this file afterwards again.[/QUOTE]

Avatars and so on the forum and everytime they create a new album or you visit the gallery.
I'm only running 777 on the folders that is needed for it so hopefully it aint such a big security risk.

---

### Post by spn on 2005-01-05
I had the same problem, but rather than use 'chmod 777', I used 'chown nobody.users' so only apache had r/w rights to the folder.  That might be a better solution if the directory structure is accessed by Apache only.  And assuming Apache is set to the default nobody user on Ubuntu; haven't checked. 8-[ 

Steve

---

