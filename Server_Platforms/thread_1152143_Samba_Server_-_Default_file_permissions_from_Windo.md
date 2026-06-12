---
title: "Samba Server - Default file permissions from Windows"
date: 2009-05-07
forum: Server Platforms
---

### Post by uzi09 on 2009-05-07
Hey all.

So I setup Samba so we can save all our company files on the main file server. I'm running into a problem with permissions though.

**The Setup:**
People will have to just map a drive to the server (long story, but this is what we're sticking with at the moment) and to make this easier, I've just created a batch file for the users to run which will get them to AUTHENTICATE (don't forget this, maybe useful further down).

They get a new Z: and it gives them access to their home directories on the linux server. Now I wanted to have separate folders for each department which only employees of that department will have access to. Instead of having to map a number of folders, I thought it'd be neater to have links to various folders from their main home drive.

IE:
```

user@server:/home/user$ ls -l
lrwxrwxrwx 1 root   root     10 2009-03-24 14:50 dept_files -> /home/dept_files [COLOR="Red"](note: even if it was created by the local user, it still doesn't work)[/COLOR]

```

Now the user can get into the dept_files folder just fine and read everything, however, when they try to create a new folder through Windows (linux works fine of course ;)), they are unable to name it as anything other than "New Folder". Nor can they rename it later. They get the message:
```
Cannot rename New Folder: Access is denied.

Make sure the disk is not full or write-protected and that the file is not currently in use.
```

Here are the permissions of a new folder:
```

**uzi@server:/home$ ls -l**
drwxrws---  5 root   dept    4096 2009-05-07 14:16 dept_files [COLOR="Red"](note the SGUID is set here, this means anyone who creates a file/dir will automatically have its group changed to 'dept')[/COLOR]
**uzi@server:/home/dept_files$ ls -l**
total 12
drwxrws--- 2 root  dept 4096 2009-05-07 13:13 Documents
drwx--S--- 2 uzi dept 4096 2009-05-07 14:16 New Folder
drwxrws--- 2 root  dept 4096 2009-03-17 12:49 Programs

```

So the windows user is logged to the mapped drive (remember from before) and based on who he is logged in as, a new folder is created. As you can see in the 'New Folder' entry, 'uzi' created the folder & because of the SGUID it automatically had its group set to 'dept' as desired.

Problem is, when I try to change the name (even at the time of creation), the computer won't let me. An interesting thing I noted was that in Windows, when I checked the owner of the files, they were all set to 'Administrators' for some reason. I'm not sure what that's all about, but 'Administrators' is different from 'uzi' and the file permissions only give the owner ('uzi') write permissions (mind you I'm logged in with an account on Windows as 'uzi' AND mapped the drive with the appropriate user 'uzi').

Any help is much appreciated.

uzi

---

### Post by uzi09 on 2009-05-08
SOLVED:

I was basically trying to map one drive for the user so that his/her My Computer isn't filled up with drives to all sorts of folders.
I think the problem was that because the dept_files folder wasn't shared through Samba, this was causing problems.

The work around is to just create a shortcut to the server itself, and based on the user login, the appropriate files will show:

Right-click on desktop > New > Create Shortcut
and enter the path to the server itself -- **not to a particular drive**
```

\\server

```

This way, you can have fine-grain control over what folders are shared and who has permissions for what through the Samba config file (smb.conf).

Hope it helps someone...


On a similar note, people often ask how to disconnect from the particular user they logged in as the first time around since unlike mapped network drives you can't just right-click & disconnect.
Google helped me discover this little command:
```

net use * /d

```
It disconnects from all drives **with a prompt**.
And for all those script-kiddies ;)
```

net use * /d /yes

```
It disconnects from all drives **without a prompt**.

---

