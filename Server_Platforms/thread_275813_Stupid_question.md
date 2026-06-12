---
title: "Stupid question"
date: 2006-10-11
forum: Server Platforms
---

### Post by anthw27 on 2006-10-11
Ok guys, now this prolly a stupid noob question but I gotta ask it.

So I do up a test lamp server k, all going well can reach it on the lan, thats cool and can see default apache page .

Now I want host my own site, so I figure it would be easiest to 
replace the defualt files in the apache defualt directory but I dont have permission.

So if I create a new virtual server in webmin will I have permision to copy over my own content?

I am already an admin level user but I dont have rights to work with the files in tha default apache directory.](*,)

---

### Post by az on 2006-10-11
> **anthw27 said:**
> Ok guys, now this prolly a stupid noob question but I gotta ask it.

So I do up a test lamp server k, all going well can reach it on the lan, thats cool and can see default apache page .

Now I want host my own site, so I figure it would be easiest to 
replace the defualt files in the apache defualt directory but I dont have permission.

So if I create a new virtual server in webmin will I have permision to copy over my own content?

I am already an admin level user but I dont have rights to work with the files in tha default apache directory.](*,)

/var/www is owned by the www-data user.  You shuold be able to write there as sudo and chnge the permissions to whatever you want.  Just so long as it's readable by www-data.

---

### Post by anthw27 on 2006-10-12
Cheers for that. I figured that would be the case.
A pity that you cant drag and drop via the file manager though.

---

### Post by rastilin on 2006-10-12
You can. Just use "sudo nautilus" to start the file manager as root.

---

### Post by PriceChild on 2006-10-12
You could always also add yourself to the www-data group?

---

### Post by pelle.k on 2006-10-14
Oh, but the www folder has 0755 permissions (i installed lighttpd though...) so to do this you must change permissions to 775, and that isn't really recommended right?

---

