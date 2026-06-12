---
title: "ERROR | You don't have permission to access /index.html on this server. | HELP PLZ"
date: 2007-05-27
forum: Server Platforms
---

### Post by sam1981 on 2007-05-27
THIS IS THE ERROR WHAT I AM GETTING WHEN I BROWSE MY WE I PUT THE WEB FILES TO /VAR/WWW
AND DELETE THE APACHE2 DEFAULT FOLDER

You don't have permission to access /index.html on this server.

---

### Post by ryanVickers on 2007-05-27
Um, I can't understand a single word of that, so I won't dare to help at this point, but if you can clarify a bit, 
I'd be more than happy to offer my advice.

---

### Post by dfreer on 2007-05-28
post the output of this command:
```
ls -l /var/www/
```

the problem is most likely that you do not have read permissions set correctly. if so, this will fix the problem:
```
sudo chmod a+r /var/www/index.html
```
of course, if any of the other pages on the site have incorrect permissions, you will need to change them as well (which is what the first command will show us)

you should keep all of your posts about a specific problem in the original thread, no need to create multiple threads. also try not to type in all capital letters, it gives the impression that you are shouting at us.

---

### Post by Dylnuge on 2007-05-28
> **ryanVickers said:**
> Um, I can't understand a single word of that, so I won't dare to help at this point, but if you can clarify a bit, 
I'd be more than happy to offer my advice.

Ditto. Advice:

1. Include nothing important in the title that is not in the text iteslf.
2. Don't write in all CAPS. It is considered rude online, and hard to read.
3. Punctuate.

---

### Post by Alterax on 2007-05-30
Sounds like a permissions problem to me.  

Go into the terminal (it won't bite, I swear) and type this command.  This will allow everyone to read the index pages, but only the owner of those files will be able to write to them:

sudo chmod -R 644 /var/www

To break this down:  sudo lets you do this as an admin.  -R means Recursively, so it means it does this to the files you specify and every file in every directory inside of them.

644 is a permissions designation.  It's three single digits from 0-8 each: Owner, Group, Everyone.  4 is the ability to read it, 2 is the ability to write to it.  1 is the ability to execute it (since these aren't binaries or shell scripts, you don't need the 1 here).
So you figure out how to do this by adding up the numbers for the permissions, and putting them in the right place:
So that means the Owner gets to Read (4) + Write (2) = 6 (Read and write, not execute).
People in the same group as the owner get to Read it (4) = 4 (Read only, no execute).
Ditto with everyone else (4= Read Only, no execute)

The final bit is the path to where you want to start; in this case /var/www  .  So it'll change the permissions for this directory and every file included inside it so everyone can read it (in a nutshell), but only the user that owns the file can write to it. (so people don't mess with your site).

Good luck!

--Alterax

---

### Post by Shadowmeph on 2007-06-01
> **Alterax said:**
> Sounds like a permissions problem to me.  

Go into the terminal (it won't bite, I swear) and type this command.  This will allow everyone to read the index pages, but only the owner of those files will be able to write to them:

sudo chmod -R 644 /var/www

To break this down:  sudo lets you do this as an admin.  -R means Recursively, so it means it does this to the files you specify and every file in every directory inside of them.

644 is a permissions designation.  It's three single digits from 0-8 each: Owner, Group, Everyone.  4 is the ability to read it, 2 is the ability to write to it.  1 is the ability to execute it (since these aren't binaries or shell scripts, you don't need the 1 here).
So you figure out how to do this by adding up the numbers for the permissions, and putting them in the right place:
So that means the Owner gets to Read (4) + Write (2) = 6 (Read and write, not execute).
People in the same group as the owner get to Read it (4) = 4 (Read only, no execute).
Ditto with everyone else (4= Read Only, no execute)

The final bit is the path to where you want to start; in this case /var/www  .  So it'll change the permissions for this directory and every file included inside it so everyone can read it (in a nutshell), but only the user that owns the file can write to it. (so people don't mess with your site).

Good luck!

--Alterax

hmm I am a complete noob at this but I am willing to learn, so if I have a file( etwolf) that is locked how would I open it so I can change a couple of things?

---

### Post by dfreer on 2007-06-01
either open it with sudo or change the permissions/ownership.

chmod will change the permissions of a file, and chown will change the owner of the file.

---

### Post by orozcovision on 2007-06-03
> **Alterax said:**
> Sounds like a permissions problem to me.  

Go into the terminal (it won't bite, I swear) and type this command.  This will allow everyone to read the index pages, but only the owner of those files will be able to write to them:

sudo chmod -R 644 /var/www

To break this down:  sudo lets you do this as an admin.  -R means Recursively, so it means it does this to the files you specify and every file in every directory inside of them.

644 is a permissions designation.  It's three single digits from 0-8 each: Owner, Group, Everyone.  4 is the ability to read it, 2 is the ability to write to it.  1 is the ability to execute it (since these aren't binaries or shell scripts, you don't need the 1 here).
So you figure out how to do this by adding up the numbers for the permissions, and putting them in the right place:
So that means the Owner gets to Read (4) + Write (2) = 6 (Read and write, not execute).
People in the same group as the owner get to Read it (4) = 4 (Read only, no execute).
Ditto with everyone else (4= Read Only, no execute)

The final bit is the path to where you want to start; in this case /var/www  .  So it'll change the permissions for this directory and every file included inside it so everyone can read it (in a nutshell), but only the user that owns the file can write to it. (so people don't mess with your site).

Good luck!

--Alterax

I tried "sudo chmod -R 644 /var/www" and resulted in Permission Denied for All Users and Groups! Even if I tried "ls -l", I would get "Permission Denied."  I had to use "chmod -R 755 /var/www to quickly correct the problem... but I would like to know which ### actually gives the owner Read/Write access, and +r to everyone else.  

Any help is greatly appreciated. Thanks in advance

---

### Post by dfreer on 2007-06-03
you could always run chmod this way, I find it's a heck of a lot easier than using the octal bits:
sudo chmod u=rwx,g=rx,o=rx /your/file/here
sudo chmod a+r yourfile.txt
sudo chmod u=rw,g-rwx,o-rwx folder/thisotherfile

where a = all three
where u = user (owner)
where g = group
where o = others (everyone else)

But here's a quick rundown on those
7 = rwx
6 = rw
5 = rx
4 = r
3 = wx
2 = w
1 = x

211 = the 2 is changing the owner's permissions
121 = the 2 is changing the group permissions
112 = the 2 is changing everyone else's (other's) permissions

eh?

so your 644 works on files, changing them to the appropriate permissions. Also note, in order to navigate a folder, you have to have the x permission set. Seriously, this messed me up alot I don't quite understand it, but folders need at least 555 set in order to view the contents.

Basically, you'll want to set folders as 755, and files as 644. You don't want all of your files being 755, as this lets them be executed (not a good idea)

---

