---
title: "chroot newbe"
date: 2016-01-17
forum: Server Platforms
---

### Post by matt18 on 2016-01-17
I am making a FTP(or ssh and will use some sort of gui to transfer and log in) server and samba as well. However, on the ftp side of things, i want it set up very specifically. I want each user to be jailed to a user folder that matches there user name, and inside said folder is other directories such as Images, Docs, PDFs. I want admin to be able to browse all user folders. Each user will have the ability to upload/download files from any of their directories and also delete if needs be. 

I have only one user account and thats admin. I was hoping to create a folder in my home directory labeled "FTP" and inside the FTP directory are the folders matching the usernames. Im not sure if this is how it works or will i have to log into each user and create the folder structure im looking for??

I have not had to do anything this extensive on linux before so i have no idea where to start, how to add said users or new future users, how to jail them to their own directory or how to actually setup FTP correctly. I do want them to have a username and password. 

By the way, this is a test system. no REAL users besides me will be using it. Im learning how this all works. 

thanks

Matt

---

### Post by matt_symes on 2016-01-17
Hi

Install vsftpd.

```
sudo apt-get install vsftpd
```

Take a look at the option:

```
chroot_local_user=YES
```

in the file */etc/vsftpd.conf*

Also you may find in the man page....

```
man 5 vsftpd.conf
```

... these options useful

```

local_root
user_sub_token
```

FTP is insecure though (password sent in plain text) and has had many problems over the years.

I would advise against using it.

sftp is a more secure option.

Kind regards

---

### Post by matt18 on 2016-01-17
i may actually go with either sftp or ssh. Its the chroot thing im new at and seem to be confused about haha. 

Do i just use the CLI to make all the users and then log in as that user through the CLI and create each directory?

thanks

EDIT

Just realized i said either sftp or ssh. I meant either scp or sftp via ssh. But most likely SFTP since im dealing with files of large sizes

---

### Post by cariboo on 2016-01-17
Not really a network thread, moved.

---

### Post by matt_symes on 2016-01-18
Hi

> **matt18 said:**
> i may actually go with either sftp or ssh. Its the chroot thing im new at and seem to be confused about haha. 

That's a slightly different method than using FTP only and you need to edit one of the ssh config files.

> Do i just use the CLI to make all the users and then log in as that user through the CLI and create each directory?

If you use the command

```
sudo adduser
```

then the user's home directories will be populated with the files in /etc/skel.

According to the man page for adduser

> If the file /usr/local/sbin/adduser.local exists, it will be executed after the user account has  been  set  up  in order to do any local setup.  The arguments passed to adduser.local are:
       username uid gid home-directory

You should be able to create the users home sub directories in that script (you'll need to create the script) if you want the process fully automated of adding sub directories to the users home directory.

Kind regards

---

### Post by nerdtron on 2016-01-18
I'll also add if you go with SFTP, you can disable the users login via ssh by changing their default shell. This way, they won't be able to use ssh and the the bash shell commands when they login via the command line.

```
sudo useradd --shell /bin/sftp -c "Name User" username
```

---

### Post by matt18 on 2016-01-18
wow, thanks for all the info guys. I have been reading aton on this subject to make sure all my ducks are in a row. I will be editing the conf file so that only the users in the group filetransfer, will be able to upload/download and will not be binded to a shell. this way it keeps them from somewhat snooping around my system. Im also jailing them to their home directory. 

I do want it password protected and still use RSA. However, i know passwords are the weakest link, is there a way to make a requirment list that the passwords must follow in order to log in? if not thats cool.

thanks

---

### Post by matt_symes on 2016-01-18
Hi

> **nerdtron said:**
> I'll also add if you go with SFTP, you can disable the users login via ssh by changing their default shell. This way, they won't be able to use ssh and the the bash shell commands when they login via the command line.

```
sudo useradd --shell /bin/sftp -c "Name User" username
```

An excellent suggestion.

Just to mention that if using *adduser* as opposed to *useradd*

```
sudo adduser  --shell /bin/sftp <...>
```

Kind regards

---

### Post by matt_symes on 2016-01-18
Hi

> **matt18 said:**
> I do want it password protected and still use RSA. However, i know passwords are the weakest link, is there a way to make a requirment list that the passwords must follow in order to log in? if not thats cool.

Are you asking about sftp and RSA keys ? Have you jumped topics ?

Kind regards

---

### Post by matt18 on 2016-01-18
My bad. I was just watching a cbt course for ssh and i accedently added that RSA part in the mix. What i ment to say was this:

is there a way to make a requirment list that the passwords must follow in order to log in? if not thats cool.

to much info going through my head at the moment haha. I have calc 3, chemistry, CCNP and now this all going on at once haha

---

### Post by nerdtron on 2016-01-18
> **matt18 said:**
> My bad. I was just watching a cbt course for ssh and i accedently added that RSA part in the mix. What i ment to say was this:

is there a way to make a requirment list that the passwords must follow in order to log in? if not thats cool.

to much info going through my head at the moment haha. I have calc 3, chemistry, CCNP and now this all going on at once haha

You mean password policies like minimum length of password, etc?
Read the password policy section here: [https://help.ubuntu.com/lts/serverguide/user-management.html](https://help.ubuntu.com/lts/serverguide/user-management.html) 
The rules are defined on the /etc/pam.d/common-password file.

---

