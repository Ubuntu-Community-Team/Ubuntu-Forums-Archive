---
title: "Set permissions, create a file but can't delete."
date: 2006-08-07
forum: Server Platforms
---

### Post by pertu on 2006-08-07
Hi,

I am trying to set permissions on a shared folder to allow users to create file, but to deny them the right to overwrite or delete any files in the folder (including the file they created). If someone is familiar with NTFS permissions, I am trying to give a permision identical to "Create Files / Write Data" in Windows 2000.

If anyone can help me, 
Thank you.

Olivier

---

### Post by louis_nichols on 2006-08-07
that will be a different thing. The permission to create files within a folder is created on that folder. So if you make it writable, other users will be able to create files within it. The only thing is, a file ceated by a user will be owned by that user, so he/she can do anything they want with it. It wouldn't really make sense any other way (I mean, someone could, say, create a document, but they won't be able to save any other changes to it, after that). It's not any different with NTFS, to my knowledge.

---

### Post by pertu on 2006-08-07
It make sense the way we work. We are creating files with a version number at the end, and if we want to modify the file, we just have to create a new file with a different version number.It works really well in NTFS using the "Create Files / Write Data" permission. I've heard of ACL in linux but I do not know if it is capable of doing what I want. Maybe there is a way to detect change in a directory, and when a new file is created a script runs automatically and change the file permissions to read only.

---

### Post by moma on 2006-08-07
Hello,

1) Study first howto use "sticky bit" on a directory. It will not solve you problem completly but may give a temporary solution.
$ sudo chmod 1777 directory
[http://www.linuxdevcenter.com/pub/a/linux/lpt/22_06.html]("http://www.linuxdevcenter.com/pub/a/linux/lpt/22_06.html")

Eg. Linux' /tmp directory must have the sticky 't' bit set.

2) Start to use extended file attributes (ACL, Access Control List)
[http://acl.bestbits.at/about.html]("http://acl.bestbits.at/about.html")

Google for "linux ACL"
This Fedora document is quite good: [http://www.vanemery.com/Linux/ACL/linux-acl.html]("http://www.vanemery.com/Linux/ACL/linux-acl.html")

---

### Post by pertu on 2006-08-07
moma,

Your solution to use the sticky bit would be great if I could set the owner of a file to be someone else than the creator of the file. 

E.g. Eric creates a file and the owner of this files is set to Olivier by default. So Eric cannot delete the file because he is not the owner.

So is this possible? Because that would solve my problem.

---

