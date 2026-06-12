---
title: "Any sort of file transferring for new guy?"
date: 2015-12-30
forum: Server Platforms
---

### Post by Shikhar_Baheti on 2015-12-30
Hey, I just got into Ubuntu, I've one Desktop Ubuntu (KDE) VPS from a hosting company. I want to host gamesevers on it, hosting gameserver is not the problem but the problem is to manage it. I've a small team of people who can script files for games. I don't want them to access everything on my server, I just want them to do stuff in their own folder. 

For example, I want them to do stuff in: /home/counterstrike/hld/dev, in that folder, I want them to do all that make new files, upload, download, and stuff, but I don't want them to go to the parent folder, that is HLD. 

I've been like searching this for months, I tried vsftpd, gadmin-proftpd, openssh, dropbox, samba etc but I couldn't get to me. I think it's very tough for new guy to learn chroot and stuff.

Can anyone recommend me anything that I could use to manage files and users permissions to do stuff?
Please try to be newbie friendly if possible.

Thank you very much!
Shikhar.

---

### Post by matt_symes on 2015-12-30
Thread moved to **Server Platforms**

This is a better forum for your query.

You may want to consider your decision to run a desktop UI on a server.

There are some good members who can advise you in this forum.

---

### Post by darkod on 2015-12-30
1. Why would you get a desktop VPS for a server? You need the GUI to administer? I also suggest using ubuntu server as the OS for the VPS, and learn to administer over ssh session and the command line. The basic stuff is not that difficult to learn.

2. You only need to give some users read-write access to single folder? That should be easy to do, either by plain ssh (they can use scp from linux or winscp from windows to upload files) or by some ftp client and limitation for browsing outside the target folder. FTP is in general less secure, if you could do it with ssh or sftp would be better.

---

### Post by Shikhar_Baheti on 2015-12-30
> **darkod said:**
> 1. Why would you get a desktop VPS for a server? You need the GUI to administer? I also suggest using ubuntu server as the OS for the VPS, and learn to administer over ssh session and the command line. The basic stuff is not that difficult to learn.

2. You only need to give some users read-write access to single folder? That should be easy to do, either by plain ssh (they can use scp from linux or winscp from windows to upload files) or by some ftp client and limitation for browsing outside the target folder. FTP is in general less secure, if you could do it with ssh or sftp would be better.


Answer to your questions:
1) Yeah... GUI helps me a bit, if you say, I can re-install vps again with ubuntu server, not a big deal, I don't have anything there. 
2) Not single folder, if it's possible, other's too. Well, what I tried was I opened Dolphin file explorer, made a folder, /home/something/somethingain, and gave something folder permissions of 'OTHERS' to forbidden. Then, I made a user, "hop", and later, I changed his home directory to /home/something/somethingain, but that didn't work as I some how logged in to /etc with WINSCP, and then I had to navigate to /home/something/somethingain, but I got permission denied at something. 

That's weird.

---

### Post by bab1 on 2015-12-30
> **Shikhar_Baheti said:**
> Answer to your questions:
1) Yeah... GUI helps me a bit, if you say, I can re-install vps again with ubuntu server, not a big deal, I don't have anything there. 
2) Not single folder, if it's possible, other's too. Well, what I tried was I opened Dolphin file explorer, made a folder, /home/something/somethingain, and gave something folder permissions of 'OTHERS' to forbidden. Then, I made a user, "hop", and later, I changed his home directory to /home/something/somethingain, but that didn't work as I some how logged in to /etc with WINSCP, and then I had to navigate to /home/something/somethingain, but I got permission denied at something. 

That's weird.
You have to configure the directory root that you want the user to start at when using SSH (SFTP (WinSCP)).  The same is true of Samba.  The directory you share with Samba is the root directory.  The user can't go up from there.  

Linux chroot is not a true jail such as a BSD jail.  If you need a Linux jail you should look at LXC (Linux Containers).  The choice is yours.  Samba is the most common (no nested shares) or  SSH (set up the conf file).  LXC is the most secure, but will be a pain for the new user.
[QUOTE=by you]Can anyone recommend me anything that I could use to manage files and users permissions to do stuff?  Please try to be newbie friendly if possible.[/QUOTE]
Samba will be the most newbie friendly.  There are GUI tools that you can use.  I don't use them at all.  The setup of Samba is really pretty simple with a terminal based test editor.  In addition this can all be done remotely via SSH.  Just remember that you should not nest one share inside another share.  You have to think about the file system structure to accommodate multiple shares.

---

### Post by darkod on 2015-12-31
Did you check the permissions of that directory to confirm they are what you expect? Also, note that simply assigning a home folder after creating the user I don't think the folder permissions are adjusted. You have to do that by hand.

Also note that you can simply use any created folder, no need to be inside /home, especially if that means inside another users /home folder. Simply create folder with mkdir, and use chown and chmod to control owner user:group and permissions. Then try again...

You can always check the parameters of any command with 'man <command>' or google it...

---

### Post by bab1 on 2015-12-31
> **darkod said:**
> Did you check the permissions of that directory to confirm they are what you expect? Also, note that simply assigning a home folder after creating the user I don't think the folder permissions are adjusted. You have to do that by hand.

Darko -- This is why one should use ***adduser *** instead of *useradd*.  The users complete configuration (including the home dir) is handled in a Debian style by scripts.

From the adduser man page```
DESCRIPTION
       adduser  and  addgroup  add  users and groups to the system according to command line
       options and configuration information  in  /etc/adduser.conf.   They  are  friendlier
       front  ends  to  the  low level tools like useradd, groupadd and usermod programs, by
       default choosing Debian policy conformant UID and GID values, creating a home  direc&#8208;
       tory  with  skeletal  configuration,  running  a  custom  script, and other features.

```

---

### Post by darkod on 2015-12-31
Yes, but is the owner/permissions change automatic? If you use adduser and do not specify otherwise, the default home folder created will be /home/user. Later you need to use usermod (not sure if adduser has the same option) to modify the home folder location. But does ubuntu change the owner of the folder or you need to do that manually?

Of course, all of this is different if you specify custome home location during user creation. Then owner is set right away and correctly. And this is probably what is best to be done. On user creation select custom home location...

---

### Post by bab1 on 2015-12-31
> **darkod said:**
> Yes, but is the owner/permissions change automatic? If you use adduser and do not specify otherwise, the default home folder created will be /home/user. Later you need to use usermod (not sure if adduser has the same option) to modify the home folder location. But does ubuntu change the owner of the folder or you need to do that manually?

The owner and permissions are set via the script and the /etc/skel provides the default structure.  The admin can move the existing  "home dir" and use *usermod * to make the change to the /etc/passwd file.  Unless you are me.  :-).  i just modify the /etc/passwd file directly.  Whether it is useradd or adduser the location of the home dir is configured in the /etc/passwd file.  It looks like this ```
<user>:x:uid:gid:<User Full Name>,,,:/home/dir/location:/bin/<shelll of your choice>
```
> 

Of course, all of this is different if you specify customer home location during user creation. Then owner is set right away and correctly. And this is probably what is best to be done. On user creation select custom home location...
Of course.  Most of the time this is all setup as the user is created.  You can use the */etc/adduser.conf* to set up a non-default location and setup so that you can just add a user with this command```
adduser <user>
```

Most of this is useful for high volume user creation.  If you have to add 10 or more users every day you might write a wrapper script to insert the users in bulk (adduser $NEWUSER).

---

### Post by Shikhar_Baheti on 2015-12-31
So... what should I go with right now? I can't seem to figure out Samba client on windows right now. I must get on command line to get stuff done. 

Can anyone please make me a little tutorial if I want an user to just access /home/cs/dev, just "dev" folder, and not go anywhere else than that?

---

