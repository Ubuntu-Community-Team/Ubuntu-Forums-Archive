---
title: "mount --bind cmd deletes my folders"
date: 2011-03-04
forum: Server Platforms
---

### Post by Foeburner on 2011-03-04
ubuntu 10.10

I'm trying to mount and bind a certain public folder onto my home folder but when I do, it deletes all my folders inside my home folder, i.e. desktop, documents, etc. and nothing is mounted. 

this is the command I'm using

```
sudo mount --bind /Publicfolder /home/user

```

When I did the cmd above, I found my home folders in the "public" folder and everything in my home folder was deleted. 

What am i doing wrong?

Here's the background. I'm setting up vsftpd and need all users to access their home folder. I need to link another folder, "public" in each user's home folder so they can place files in there to share with others. I read that the only way you can do this with vsftpd is to mount and bind the "public" folder.

All help is appreciated!!

---

### Post by Foeburner on 2011-03-10
bump? I reinstalled ubuntu because all sorts of problems started arising. After anew 10.10, I did the mount --bind command again and guess what... it deleted all my folders in my home folder.

bug?

---

### Post by bab1 on 2011-03-10
> **Foeburner said:**
> bump? I reinstalled ubuntu because all sorts of problems started arising. After anew 10.10, I did the mount --bind command again and guess what... it deleted all my folders in my home folder.

bug?

Lack of understanding.  When you have files in the directory you are using for the mount point they will be hidden until you unmount the folder.  They're not deleted, only hidden.  :-)

Create a mount point (directory) with nothing in it and mount the folder there.

Edit: Why are you using mount --bind ?

---

### Post by BkkBonanza on 2011-03-10
The previous post is correct. When you mount something it hides the content there until the mount is removed. Use **umount /home/user** to remove the mount and you will see it is there still.

You need to create a directory in the user's home and bind mount to that. I presume you are using --bind so that you can mount that public folder in many user's home's at the same time.

eg.

mkdir /home/user/public
mount --bind /Publicfolder /home/user/public

Now any content in Publicfolder will also appear in the user's home public and they can add files in there (or if permission allows remove them). You'll want the Publicfolder to have open permissions too.

Another way to do this is with a symlink. 
eg. this just points the user home public to the ftp public.

ln -s /Publicfolder /home/user/public

Not sure which is preferable or more efficient.

---

### Post by Foeburner on 2011-03-11
YES!!! FINALLY!! google wasnt producing any results. You guys are awesome!!

now i understand! I'll give this a try and will post the results!

thanks!

---

### Post by Foeburner on 2011-03-15
ok so I got it working and noticed that I completely misunderstood what mount --bind does. 

I mounted and binded "MeetingRoom" to my home's public folder. That worked. so then I did the same to another user's home folder but realized that it takes over the mounted folder. What ever changes I make on my home folder is no longer seen in this "meetingRoom" folder. It only shows the other user's mounted folder. 

What I need to do is mount a common folder on everyone's home/Public folder so that they can drag and drop files into this "MeetingRoom" folder so that they can share files with others that go into that meeting room folder. This will be used with vsftp so that when people log in to the ftp, they see their home folder where they can store their stuff and drag files over to the MeetingRoom folder for others to see. 

Is there another way to make this work?

All the help is greatly appreciated!

Thanks!

---

### Post by Foeburner on 2011-03-15
Should I create another thread for this as well?

---

### Post by bab1 on 2011-03-15
> **Foeburner said:**
> ok so I got it working and noticed that I completely misunderstood what mount --bind does. 

I mounted and binded "MeetingRoom" to my home's public folder. That worked. so then I did the same to another user's home folder but realized that it takes over the mounted folder. What ever changes I make on my home folder is no longer seen in this "meetingRoom" folder. It only shows the other user's mounted folder. 

What I need to do is mount a common folder on everyone's home/Public folder so that they can drag and drop files into this "MeetingRoom" folder so that they can share files with others that go into that meeting room folder. This will be used with vsftp so that when people log in to the ftp, they see their home folder where they can store their stuff and drag files over to the MeetingRoom folder for others to see. 

Is there another way to make this work?

All the help is greatly appreciated!

Thanks!
If you are sharing files then you will always have a *one to many* situation.  The "MeetingRoom" folder is shared to each user.  So yes you will need to set every user up with the ability to use that folder.

I have a dedicated host (NAS) for just sharing folders and files on my network.

Edit: If you use Samba the users can browse the network and map their  own mount points.  Then there would be no need for you to manually edit fstab (mount) for each user.

---

### Post by BkkBonanza on 2011-03-15
You should probably just use a symbolic link. It can point any number of folders to the one common folder. Then you need to make the public folder have permissions either for the whole group or everyone.

ln -s /MeetingRoom /home/user/public

Note with symbolic links when you do a directory listing you need to add the trailing / or else it will just show you the link not the contents.

eg.
cd /home/user
ls -ls public    (shows the link only)
ls -ls public/   (shows the target contents)

---

### Post by Foeburner on 2011-03-21
Bab1, I tried mounting in samba but I could not get it to mount. 

bkk -- This works perfectly!

---

