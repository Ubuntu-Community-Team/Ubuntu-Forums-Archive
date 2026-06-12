---
title: "How do i make the apache folder writable from my user?"
date: 2005-10-12
forum: Server Platforms
---

### Post by hansoffate on 2005-10-12
I want to be able to write to my apache folder /var/www/   Its a hassel to sudo everything espeically because im a begginer.  Also im trying to extract a php web portal content manager and i ccan't because I don't have permission to.  Can anyone help me out?

Thanks again, 
Hans

---

### Post by adwait on 2005-10-12
You could change the permissiosn on /var/www. Just change the permissions to 775
```
 chmod 777 /var/www 
```

EDIT: TRY IT NOW, THERE WAS A MISTAKE I REALISED!

---

### Post by hansoffate on 2005-10-12
I did that. but it says i still don't have permissions to it wehn trying to extract it there.  Perhaps it only allows root user to access it?  Can i change that?  

Thanks for your help,
Hans

---

### Post by pit0rz on 2005-10-12
Don't know if this is the preferred method but it worked for me.

sudo su
chgrp -R admin /var/www
chmod -R g+w /var/www

I used the admin group as my account was included in it.

I'm a complete n00b to linux so if this is not the preferred way to go, please!! someone speak up.

-PIT

---

### Post by adwait on 2005-10-12
Look at my first post (edited it)........

---

### Post by hansoffate on 2005-10-12
Awesome, Thanks so much.  The first post is the one that worked for me if anyone else that needs to know.

One last quick question, some of my files, i don't have the permission to delete.  can i add that too?  The user its registered to is root.

thanks agian,
Hans

---

### Post by wylfing on 2005-10-12
If you really need to, you can use the command 'chown' to change the owner of a particular file (or group of files). Try [FONT="Courier New"][COLOR="DimGray"]chown user file[/COLOR][/FONT] where "user" is whomever you want to assign as the owner and "file" is the file name.

If you are the owner of the files, you can do whatever you like to them.

---

### Post by LordHunter317 on 2005-10-13
You should **never, ever** set anything 777.  It's just wrong.

The correct policy for your webroot is to change it's ownership to your own user, or whoever will be editing the files there.  Then, just remember to give world read access, and Apache will still be able to serve the files.

Can we make this note sticky so this bad advice and correction isn't repeated ad-nasuem every week or so?  It's rather old, I think.

---

### Post by adwait on 2005-10-13
hmm....ok sorry :p

but if you change the user, what if apache needs to write something to that directory? It won't be able to, since it is not the owner......

---

### Post by LordHunter317 on 2005-10-13
Apache shouldn't **ever** need to write, which is the whole point.

Ok, but what if you have a site that supports uploads?  Doesn't it need to write those files somewhere?  Ok, yes, and here's what you do:[list][*]You place the uploads directory outside the webroot, if all at possible.  This way, no one can see what is in the uploads directory from the web, and if it's altered in a compromise, you won't have people seeing "OMG HAX0rD R US" for a frontpage.[*]You set it so Apache owns that directory and has write access.  If everyone must be able to write for some god-awful reason (which is almost never true) then you make the perms 1777, so people won't be able to mess with others files[/list]

But as a general rule, Apache shouldn't ever have to write to files/directories in the webroot.  That's true for the overwhelming majority of applications.

---

