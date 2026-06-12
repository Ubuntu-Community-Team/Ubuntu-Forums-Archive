---
title: "Samba with openSSH Permission Problems"
date: 2010-02-22
forum: Server Platforms
---

### Post by thecaligarmo on 2010-02-22
So I can't seem to get something like the following scheme to work:
People accessing the server through samba would have read/write/execute privileges while those coming through openSSH would have only read/execute privileges. Is there a way to make that possible?

My current permission scheme:
root:samba drwxrwx--- /fileserver

I have it setup so that whenever a user accesses the server through samba and creates any files then it will automatically be created as:
user:samba -rwxrwx--- /fileserver/file

And for each member that I want to have openSSH access I created a new group sftp such that each member of sftp is also a member of samba (but each member of samba is not necessarily a member of sftp).

So what happens is that while logging in through openSSH as a 'dual' user (ssh and samba access) then I can read and download all files (due to my samba permissions) and I'm also able to write any file I want onto the server (again through samba permissions)

BUT The issue is that when a 'dual' user uploads using ssh then it creates the file as:
user:user -rw-r--r-- /fileserver/file

Im looking for one of 2 solutions:
1) Allow it so that a 'dual' user cannot upload files when connected through ssh (write access disabled) but can upload while connected through samba (write access enabled). Or:
2) Have openSSH have a 'forced' permission scheme in which I can force it to have samba be its group and its permission scheme to be 0770.
(Or an option 3 if you have any ideas)

Any ideas/suggestions/help would be greatly appreciated! Thanks!!! (if you need any data files just let me know which ones and I'll try and get them to you)

---

### Post by thecaligarmo on 2010-02-23
*bump*

---

### Post by thecaligarmo on 2010-02-25
*bump* Does really no one know a way to do this?

---

### Post by thecaligarmo on 2010-03-01
*bump*

---

### Post by thecaligarmo on 2010-03-02
*bump*

---

### Post by thecaligarmo on 2010-03-03
*bump*

So I've been looking around for a while (as you can tell with the number of *bumps*!) but I still can't find anything. I'm thinking a 3rd option would be to make it so that if a user enters through openSSH they automatically have write access disabled, so they can't upload anything. Since it seems no one knows how to the previous things or no one is willing to answer, I was wondering if anyone know how to incorporate this:
3)Allow openSSH read access but not write.

The users would again be the same in openSSH as samba.

---

### Post by NullHead on 2010-03-03
Why do you want to disable write access to that users's samba share if they're logged in with ssh?

---

### Post by thecaligarmo on 2010-03-09
It's not that I necessarily want to disable it, it's more that it is one of the options I'm considering to solve the main problem which is:

While logged into openSSH and I create a file it gives the following permission scheme:
-rw-r--r-- user:user /fileserver/file

Whereas if they're logged in through samba and they create a file they get the permission scheme:
-rwxrwx--- user:samba /fileserver/file

I want the two methods of entering the fileserver have the same effect when creating a file. As a minimum for security I need to permission scheme to look like the latter of the two, and can't seem to get it to work that way.

In order to get around the discrepancy we are willing to disable write access through openSSH because we don't want that permission scheme to be active ever within our files (since then none of the other users can then go in and edit the files, etc.)

That make sense as to the why?

---

### Post by NullHead on 2010-03-09
In that case, you can add "create mask = ###" and "directory mask = ###" to your samba share.

---

### Post by thecaligarmo on 2010-03-11
I already have a mask for samba, but for some reason when I enter through SSH it doesnt pick up the samba mask.

I'm assuming this is because samba is accessing the network internally through a router whereas the ssh is entering outside the network and accesses everything differently. 

Is there a way to force the ssh to have the same mask as samba?

(Samba is giving the correct mask through the create mask I created, its the ssh one I want changed)

---

### Post by NullHead on 2010-03-11
I don't think it works like that ... the create mask for samba only sets the file permissions, like chmod 775 for a directory. You can use [this](http://jeffhowden.com/code/javascript/chmod/) chart to learn how the numbers work. 

You could have it so your users are in the same group as samba, so you can set 664 to the files and your users can still access them, whereas nobody unauthorized will be able to.

---

### Post by thecaligarmo on 2010-03-12
Exactly, samba sets the users file permission while the user is accessing the server through samba, but for some reason when the user accesses it through openSSH it is not giving the permissions that I set for the users in samba, it is giving the default ones.

The user is already in a samba group, hence that is not an issue

I dont want to sit and manually modify EVERY TIME a user uploads a file onto the server to the proper permissions.

And yes, I know I can set the users into a samba group (I already have it set up that way) and yes, I know that you can change permissions through chmod... Like I said, samba IS ALREADY DOING WHAT I WANT with permissions. The issue is not with permission schemes through samba, it is with permission schemes through openSSH.

openSSH is not grabbing the permission scheme setup through samba and I can't find a way to modify openSSH to force permission schemes through it (or disable write access, which is an acceptable alternative)

And adding users to a group wont also help considering that openSSH is BY DEFAULT making the owner and group of the file the user. If there is a way to change the default group of a file that would help too, but I can add all the users I want to a samba group, but that still won't fix the openSSH issue.

---

### Post by NullHead on 2010-03-12
Okay, lets start with looking at who the owner and group is on the shared folder is. 

Do this inside the shared folder:```
ls -la /shared/file
```

This will list the owner and group as well as the permissions set. There may be an issue with the group set for samba, or there may be an issue with how samba is setting the permissions. 

I've had my samba setup have the files owned by the group "nobody" before. That could be the issue.

---

