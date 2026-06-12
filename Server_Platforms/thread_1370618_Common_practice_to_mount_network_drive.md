---
title: "Common practice to mount network drive"
date: 2010-01-02
forum: Server Platforms
---

### Post by dinuzz on 2010-01-02
Hey there
I have the following scenario:
- Server installed in wired network. The server has a static IP. It has Ubuntu Server 9.10 installed.
- I have two Ubuntu notebooks (Ubuntu Desktop 9.10)  and I want them to connect (mount) to the server on bootup (fstab or equal) if the network is available.
- I don't want to store the password in cleartext in the fstab file. So what other options do I have?
What would be the most common practice here?
Many thanks for your advice.
Thanks - Cheers

---

### Post by Vegan on 2010-01-02
You could change the permissions to make it accessible only to the root.

Take away read privileges.

---

### Post by volkswagner on 2010-01-02
You should not need your password with NFS setup, since the server looks at it's own export file.

I have used [this how-to]("http://ubuntuforums.org/showthread.php?t=249889").  Bookmarked!

---

### Post by dinuzz on 2010-01-03
Thanks for that dude. I am able now to connect to the server by mounting the share. But now, the share is not writeable by the client. Here are the respective entries:

Server /etc/exports:
```
/home/username     192.168.1.0/255.255.255.0(rw,sync,no_root_squash,no_subtree_check)
```
Client /etc/fstab:
```
192.168.1.150:/home/username    /media/server   nfs rsize=8192,wsize=8192,timeo=14,intr
```When I open the share now on the client with nautilus, I can't write to it, only read it. Any idea, what might be wrong here?

Many thanks - cheers

---

### Post by TwiceOver on 2010-01-03
Someone please correct me if I am wrong...

NFS cannot overwrite permissions on a local folder.  So even though the folder is mounted as read/write (the rw switch in the mount), the user still needs permissions to write to the folder.

Is your username/passwords set up the same on the laptop and server?  If not, you will need to add the laptop's username to the server and give that user write permissions to the /home/username folder.

---

### Post by dinuzz on 2010-01-03
yeah, username and passwords are the same on the server and on the notebook. ls -ls from the server attached bellow:

```
4 drwxr-xr-x 4 username username 4096 2010-01-03 00:19 username

```and here's the ls from the mount directory on the client, dunno about the 1001 user:
```
4 drwxr-xr-x 4 1001 1001 4096 2010-01-03 00:19 server 
```

---

### Post by volkswagner on 2010-01-03
I am not sure about the NFS rules.  I have had no problem writing to shares with the same user name even with different passwords.  

I am far from schooled on users, groups and permissions, but I think the username is secondary to the user id #.  When I do an install I always add my username first, so I get user id # 1000.

For both machines I have working NFS shares with, I can verify my user id as 1000.

```
cat /etc/group
```

Shows the group containing my username has one member "1000".

Perhaps you need to chown the mount on the client to match the username for the server.

Try 

```
ls -alt /media/server
```

EDIT:  Um, I think I am way off on the above mention of id#, I don't think that is between machines, but only on the same machine.  Shutting up now 'till an expert chimes in.

---

### Post by dinuzz on 2010-01-04
hi there
 
yeah, indeed, the UID # do not match on the server and the client. only the usernames and passwords are the same... could that be the problem?
 
on the client, the username has the ID# 1000, and on the server, it has the ID#1001...
 
what could I do to test it to solve the problem? any more experts with knowledge of NFS and ID#'s? thanks
 
EDIT: holy cow! I just mounted (added that users home directory to the exports file) the home directory from the user with the same ID#, and now, I can even write to it, this looks like an issue to me, unless NFS authentication is based on user ID#? doesn't make sense to me... any suggestions?
 
EDIT: NFS user permissions are based on user ID (UID). UIDs of any users on the client must match those on the server in order for the users to have access. Closing this thread.

---

