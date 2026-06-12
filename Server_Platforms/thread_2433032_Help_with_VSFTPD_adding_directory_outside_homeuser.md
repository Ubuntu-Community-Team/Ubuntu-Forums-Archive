---
title: "Help with VSFTPD adding directory outside /home/user"
date: 2019-12-12
forum: Server Platforms
---

### Post by dohm11 on 2019-12-12
Hi, was looking at this post about adding another directory to a ftp user. I am using vsftpd and the code that was presented is the following:

```
mount --bind /var/www/Testfolder/ /home/User/ftp/files
```

Now what this did is "hide" all my current files in ```
/home/User/ftp/files
```and created a test folder as I did:

```
echo "vsftpd test file" | sudo tee /var/www/Testfolder/test.txt
``` into it. 

What I am trying to do, and can't find the proper code is the following: 

I have around 1.2Terabites in the following location with folders and subfolders: ```
/home/User/ftp/files
```

My /var/www has a 1.8Terabite free space therefore I would love to create a folder in that section, which I already did aka "/var/www/Testfolder"

I need it to link and to have "User" have access to the Testfolder in my /home/User/ftp/files.

So when they "Filezilla" into the /home/User/ftp/files there will be another folder with Testfolder, which is in "/var/www" and will be able to view/delete/add data. 

Thank you so much, hopefully this will also help another.

Dohm

---

### Post by xavif on 2019-12-13
I'm interesterd to do this whit my server.
I try to put the root directory in vsftpd.conf in /media/*ubuntu-main-user*/1TB/FTP but the connection rejected with a 530 error
My ubuntu/linux skills are so limitated... I need a tutorial :D

Thx

---

### Post by The Cog on 2019-12-13
Try: 
```
mkdir /home/User/ftp/files/Testfolder
mount --bind /var/www/Testfolder/ /home/User/ftp/files/Testfolder
```

@xavif:
Welcome to the forums.
I don't know about that problem: I don't know enough about vsftpd. You would probably be better off starting a new thread with your problem - it's different to dohm11's problem with mounting.

---

### Post by dohm11 on 2019-12-13
I think this is awesome, it mirrors the information that is in the var/www/Testfolder &#8230; Test.txt = (Parent Folder: /var/www/Testfolder) this is what I needed... Plus I can have my two drive working as one... 

The Cog, thank you so much...

Dohm

---

### Post by The Cog on 2019-12-13
Beware, it's just a link from one folder to another. It means that your vsftpd users are able to delete or overwrite files from Testfolder as well as uploading files. Your using the word "mirrors" suggest maybe you didn't realise that.

---

### Post by dohm11 on 2019-12-14
I am not too worried as I am the only one that has access to the upload downloads... the users are me and the clients sends me requests. No one has access... Well for now. :)

The code works like a charm :)

Thank you again.

Dohm

---

