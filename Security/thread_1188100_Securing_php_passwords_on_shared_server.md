---
title: "Securing php passwords on shared server"
date: 2009-06-15
forum: Security
---

### Post by statistic on 2009-06-15
So far the only real working solution to hiding a mysql password  in a php file on a shared server is by using CGI scripts. All my googling on the subject came up as such.

However I realised that on the server, all the users had been added to the group "students", which was the group ownership assigned to any files that we created. So I simply left the "other" permissions to be able to read my files, but group permissions don't let them touch anything.

I think this might be a better solution for users/sysadmins to come to agree on, as it takes little effort to set up, and can quickly secure documents from other users.

Please do correct me if I'm wrong, or if you have better solutions.

---

### Post by Boondoklife on 2009-07-03
Can you be a little more descriptive? I mean if you are all the same group and that group is needed for the webserver to see/execute it then really there is not a way around this. The best thing to do would be to make a jailed environment for the logged in users so they can not leave their directory.

---

### Post by statistic on 2009-07-04
Well in this case the webserver would be apache, and when it accesses files on the system it by fedault does so as the the user "nobody" and so will apply to the "other" permissions while every actual user on the system is part of a group that you can restict permissions to.

So essentially you give the permissions 705(rwx---r-x) so that users within the group are given no access priviledges, and are unable to shed being in that group.

However I find out the next day (after I thought this thread had slid down far enough to die, but I suppose it's still searchable) that this is not secure anyways, it only solves half the problem. Then a user can simply write a PHP document to read out your php document to them when the webserver runs their script as "nobody".

I was then informed about suPHP which would solve that half of the issue, as it gives each user their own personal instance of PHP when it is executed, allowing you to set 700(rwx------) permissons on it and feel much safer.


EDIT: Sorry I never really addressed your closing point. I've never liked jailed environments myself, I always go poking in the system to check for libraries and check how things are configured so I know what is available to me. A jailed environment reminds me of my high school computer systems; you couldn't format your floppy disk because they blocked any commands that allowed formatting out of fear.

---

### Post by Boondoklife on 2009-07-04
I do under stand your last point, but if this is to a managed server then the only real way to do it other than the jailed environment would be virtual servers which are alot of overhead if you dont need them.

Besides that if it is just a webdeveloper thing then why would they need to snoop?

One last thing, I dont think your idea for the 705 is quite right as I tried it on a box here and ANY user including the person that belongs to the group without rights can access the folder/files in the 705 directory.

---

### Post by statistic on 2009-07-04
You had me doubting myself so I ran a little test case:

```
mlindsay@SewagePlant:~$ ls -l test
-rwx---r-x 1 root mlindsay 6 2009-07-04 16:06 test
mlindsay@SewagePlant:~$ less test
test: Permission denied
mlindsay@SewagePlant:~$ 
```

Also in case using the username as the group is what triggers the access denied. For this test, I am already part of the admin group:

```
mlindsay@SewagePlant:~$ groups mlindsay
mlindsay adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
mlindsay@SewagePlant:~$ ls -l test
-rwx---r-x 1 root admin 6 2009-07-04 16:06 test
mlindsay@SewagePlant:~$ less test
test: Permission denied
mlindsay@SewagePlant:~$ 
```

EDIT: As for the jailed environment, I suppose I agree in the context of web developers not needing to go outside their home folders. I use my shell accounts for everything though, I just tinker around with the web space it makes available to me.I enjoy the freedom, since whenever I go to configure something on my home machine that I don't understand, I usually read the config files on the shell server I use to see how they did it, since I'm usually happy with the way they have things set up.

---

### Post by Boondoklife on 2009-07-04
> **statistic said:**
> You had me doubting myself so I ran a little test case:

```
mlindsay@SewagePlant:~$ ls -l test
-rwx---r-x 1 root mlindsay 6 2009-07-04 16:06 test
mlindsay@SewagePlant:~$ less test
test: Permission denied
mlindsay@SewagePlant:~$ 
```Also in case using the username as the group is what triggers the access denied. For this test, I am already part of the admin group:

```
mlindsay@SewagePlant:~$ groups mlindsay
mlindsay adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
mlindsay@SewagePlant:~$ ls -l test
-rwx---r-x 1 root admin 6 2009-07-04 16:06 test
mlindsay@SewagePlant:~$ less test
test: Permission denied
mlindsay@SewagePlant:~$ 
```EDIT: As for the jailed environment, I suppose I agree in the context of web developers not needing to go outside their home folders. I use my shell accounts for everything though, I just tinker around with the web space it makes available to me.I enjoy the freedom, since whenever I go to configure something on my home machine that I don't understand, I usually read the config files on the shell server I use to see how they did it, since I'm usually happy with the way they have things set up.

Huh well that is very counter intuitive. Guess I learn something new every day. I would think given the ownership is user/group/all that all would override the others if it allowed more rights o well.

---

