---
title: "FTP SERVER Ubuntu"
date: 2010-03-22
forum: Server Platforms
---

### Post by bash321 on 2010-03-22
how do i edit the folder permissions on ubuntu

you know the drwdrwx thing?

specifically how would i do it on the folder, var/www for apache?

im not going to do it i just want to know how to edit recreate folder permissions

for a username sparky (As an example)

---

### Post by dudumomo on 2010-03-22
Hi.
To know which permissions have any file or folder, you can run the command:
```
ls -l
```

And to change the permissions, you can use the command "chmod"
For a folder, for example, to give full permission to every one (Read, exec and write) you can do:
```
sudo chmod 777 /my/folder
```
First digit is for the owner, 2nd for the group of the owner, 3rd for everyone else.
And 7 kind of permission for a folder:
0: no permission at all
1: Exec permission
2: Write
3: Write + Exec
4: Read
5: Read and Exec
6: Read + Write
7: Read, Exec and Write

So, to give full permission to the owner, only read and Exec to the owner group and no permission for the others,
simply run: 
sudo chmod 750 /my/file

Etc...

---

### Post by bash321 on 2010-03-22
Dont worry i see how you answered my second question!!!

THANK YOU!!!!!

ubuntu forums are the best!

---

