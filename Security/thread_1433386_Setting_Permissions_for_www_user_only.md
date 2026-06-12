---
title: "Setting Permissions for www user only"
date: 2010-03-19
forum: Security
---

### Post by Eng_A_Moktar on 2010-03-19
Hello all, 
I wanna make a small web server for local use ,
I've installed apache, every thing works fine 
I'm the root

I wanna protect the folder that contain the htdocs files (www), i don't want any users that not in root group to access (not even read)

I changed the permission of the htdocs folder as next
Owner: www (apache user)
per: creat , delete


group: root
per: creat , delete

other: none

it only works on the main folder that i changed its permissions ! not all sub folders and files !
were my steps right ? and are their anyway to change all folders and files at once ?
thanks

---

### Post by phildini on 2010-03-19
What command did you use to change the permissions? If you used chmod, it has a flag to change permissions on all the subfiles in a folder, chmod -R. Note that, in my experience, this will only change things once and may not apply to every file added to the folder. 

A possible better solution would be to restrict and password-protect through apache, although I am not familiar with the exact method for doing so. Good luck!

---

### Post by Eng_A_Moktar on 2010-03-19
Thanks for response, I used no commands , I used the visual interface (ubuntu-desktop 9)
> A possible better solution would be to restrict and password-protect  through apache,
that sound great, only if :
1- my site will work normally no matter which user is logged on 
2- no users can access my site's files (read,write) , but apache can instead 
thanks anyway , if there are more ideas ? that will be great ...

---

### Post by phildini on 2010-03-19
```
chmod -R [permissions] [directory]
```

Probably your best bet.

---

### Post by Eng_A_Moktar on 2010-03-19
phildini man, thank you very much ;)

---

