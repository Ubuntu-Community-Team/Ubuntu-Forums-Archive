---
title: "Problem downloading from remote server to my File System"
date: 2008-07-12
forum: Server Platforms
---

### Post by masoud23 on 2008-07-12
Hi

I use FileZilla to up and downloading files o my remote server. Uploading go well but downloading is problem. I want to download to a map under File System and get this message:

Failed to open "/opt/lampp/htdocs/web/FCKeditor/bilder/pil.gif" for writing

my files has to be in this map: htdocs in lampp for my localhost to work. how  can i get FileZilla permission to download or is there another way to fix this problem?

---

### Post by straps on 2008-07-12
I think you don't have write permissions on /opt/lampp/htdocs/web/FCKeditor/bilder/

You can change add write perm or change the folder owner

To add write permission, open a console (Applications->Accessories->Terminal) and write
```
**sudo chmod -R o+w /opt/lampp/htdocs/web/FCKeditor/bilder/**
```
if asked, type your password
**-R** means recursive
**o+w** means 'assign **w**rite permission to **o**thers (non owners and not in the same group owner)

If you want to become the folder owner, type
```
**sudo chown -R 1000 /opt/lampp/htdocs/web/FCKeditor/bilder/**
```
If you are the only user, 1000 sould be your user id, and you will become the folder owner with write privileges

Bye

---

