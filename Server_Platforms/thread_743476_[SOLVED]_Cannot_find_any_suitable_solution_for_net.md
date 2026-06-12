---
title: "[SOLVED] Cannot find any suitable solution for network shares"
date: 2008-04-02
forum: Server Platforms
---

### Post by MountainX on 2008-04-02
My LAN has about a dozen computers and a Windows Server 2003 file server. I'm converting all the client computers to Ubuntu (and planning on using Hardy because of LTS). 

All data resides on the file server.

I started a few months back with Gutsy on some client PCs. One issue I ran into was that gedit (and some other apps) will not edit files that are stored on Windows shares (and that's where all our data is). In Gutsy I worked around this by using smbfs instead of cifs. However, in Hardy, smbfs no longer works around this issue (I suspect because smbfs is now a wrapper for cifs, right?).

Due to the [gedit/cifs bug]("https://bugs.launchpad.net/gedit/+bug/34813"), I looked for alternatives. 

The alternatives I learned about are sshfs and nfs. Because I transfer large files a lot (2 GB), I went with nfs.

However, this has been a real disaster so far. For example, a user on a client PC who belongs to the admin group often cannot copy a file from the network share to the local file system. The situation today involved copying a script file from the network share to /usr/share/scite. This is a common thing that will be done many times every day.

With nfs, root is squashed on the server. So when a user needs to copy a file to a local folder owned by root from the network share, it cannot be done with a normal copy command.

The bottom line is that smbfs, cifs, nfs and sshfs don't provide smooth solutions. There may be some workarounds, but all of the ones I know of so far are so painful as to make Ubuntu no longer a viable solution <---- EDIT: when I said that I was very frustrated!

What the heck am I going to do?

---

### Post by netlogic on 2008-04-02
Samba works fine for me for 400 user network for one of my past client.

---

### Post by MountainX on 2008-04-02
> **netlogic said:**
> Samba works fine for me for 400 user network for one of my past client.

Based on the bug reports, it is my understanding that it doesn't work when the file server is a Windows machine and the clients are Linux users who will be using gedit, Geany, Cream, Vim and Eclipse or some other apps to edit files on the server. That's my situation and smbfs doesn't work in Hardy on the clients. I think the samba package must work exactly the same as using smbfs from fstab, right?

---

### Post by netlogic on 2008-04-02
> **MountainX said:**
> Based on the bug reports, it is my understanding that it doesn't work when the file server is a Windows machine and the clients are Linux users who will be using gedit, Geany, Cream, Vim and Eclipse or some other apps to edit files on the server. That's my situation and smbfs doesn't work in Hardy on the clients. I think the samba package must work exactly the same as using smbfs from fstab, right?

I really don't want to be rude, but where do you get your reports? I believe Samba has worked for thousands of companies. The codes are more mature than Windows 2008

---

### Post by MountainX on 2008-04-03
> **netlogic said:**
> I really don't want to be rude, but where do you get your reports? I believe Samba has worked for thousands of companies. The codes are more mature than Windows 2008

I'm not saying samba doesn't work. I am saying there is a specific combination of factors that produces problems. This problem affects a lot of people as you can read here:
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813)

The specific factors that combine to produce the problem are:

1. the network share must reside on a Windows file server (or maybe another non-Unix-type file system).
2. the network file sharing protocol is cifs (and/or sshfs according to other related bugs).
3. the Linux clients run gedit, Geany, Vim, Eclipse or any other Linux app that attempts to move/rename an open file.

And in Ubuntu Hardy, smbfs also seems to cause the same problem that cifs does.

I think the bug comments make it clear that the gedit devs don't plan to fix this bug. Neither do the cifs devs. Also, the bug comments indicate that at least one patch has been submitted but it isn't favored by the devs.

After encountering this bug, I decided to try nfs. However, now I have the situation where root squash (required for security) prevents convenient copying of files between network shares and local folders.

So, as I said in the original post, I don't know where to turn next. I know I am not asking a specific question, and in that sense it might sound like I'm complaining. I don't intend for this to be a rant against Ubuntu or samba or cifs. I am working to find a solution. My next step is to try to see if I can work around the nfs permissions issues while still maintaining adequate security.

---

### Post by koenn on 2008-04-03
> **MountainX said:**
> 
I think the bug comments make it clear that the gedit devs don't plan to fix this bug. .
The bug comments also make it clear that this possibly isn't even a bug. the gedit developers designed a certain behaviour about keeping backups, implemented the way they thought best, and it works. The cifs devs did likewise with the way cifs handles files. As it happens; the two are not completely compatible - in specific situations, as the ones you describe, the combination of the 2 programs is rather unfortunate. That's hardly a bug.

That doesn't solve your problem, of course. 
The obvious sollution, while waiting for gedit and cifs devs to come to an agreement on how to deal with this, is to get an other text editor. 

Or look for other file sharing solutions.
I suppose it's not impossible to find an nfs configuration that will work and still be secure. 
If not, you can also share files over ssh (with nautilus)
You might also want to review the way you work. I didn't quite follow  the 'copy a file owned by root' thing, but it may mean that you should have a closer look at yopur users, groups, and file permissions. 
Or us scp, which allows you to copy while authenticating as a different user, eg root@server. 


Or eliminate the need for editing files over file sharing protocols by editing them locally on the server - in an ssh session or by exporting X.

---

### Post by MountainX on 2008-04-03
> **koenn said:**
> ... it may mean that you should have a closer look at yopur users, groups, and file permissions. 


It is my understanding that the root squash option must be used on an nfs server for security. What this means is that if an attempt is made to access files as root, that request is interpreted as coming from an unauthenticated user.

When copying files to local locations that require root privileges, it creates a catch-22. Any suitable privilege on one end is unsatisfactory on the other end.

One solution is to copy the files in two steps. However, that solution and every other one I have been able to think or have been told about involve inconveniences that are impractical. 

Also, an important function of the LAN is to keep all important data files on the file server (raid, backed up, etc.). We certainly do not want to encourage users to keep these files on client machines.

Through the work of the last week I am understanding the problem better, and a solution might turn up -- but it hasn't yet.

(BTW, the problem is not limited to just gedit. And sshfs is reported to have the same problem... )

---

### Post by koenn on 2008-04-03
see, that's what i don't get - on one hand,  you talk about keeping files centralized on a server and nothing local, on the other hand you 're having a problem with "copying file to a local location". Sounds contradictory.

nfs should cover your file sharing needs for non-root operations just fine

for your catch 22 : have you tried something like
```
me@mypc:$ scp root@server:/etc/passwd /home/me/copy
```
that should copy the passwd file of the server to my home directory
(requires ssh + allow root ) 

EDIT : or the other way around : 
```
root@mypc:# scp john@server:/home/johndoe/somefile /root/copy_of_johns_file 
```

What I said about using ssh (not sshfs) is completely in line with your 'keep files on the server' policy : the files stay where they are, you use ssh for remote command execution or to open a secure shell so you have a session on the sever where you can do your text editing.
Or you run gedit on the server (so the gedit >< filesharing problem is out of the way) but export its GUI to your desktop (allowing you to work remotely). this might give a few ideas : 
[http://users.telenet.be/mydotcom/howto/linux/xremote.htm](http://users.telenet.be/mydotcom/howto/linux/xremote.htm)

---

### Post by doogy2004 on 2008-04-03
could you try mounting the samba (windows) share, using smbfs, to a local folder.  This would be similar to mapping a drive letter in windows.  This would allow the os and samba to handle the network interaction while gedit only talkes to the os like it would for any other local file.

---

### Post by MountainX on 2008-04-03
> **koenn said:**
>  Sounds contradictory.


Yes, it can be tough to describe all the requirements well in a short post. I probably did make it sound contradictory. But you still managed to give me some good ideas. Thanks.

---

### Post by MountainX on 2008-04-03
> **doogy2004 said:**
> could you try mounting the samba (windows) share, using smbfs, to a local folder.
That's what makes gedit, geany, eclipse, etc. stop working. And that's what led me to try nfs.

---

### Post by MountainX on 2008-04-03
> **koenn said:**
> 
nfs should cover your file sharing needs for non-root operations just fine

What I said about using ssh (not sshfs) is completely in line with your 'keep files on the server' policy

What you are suggesting is to use more than one file sharing protocol. I think this is probably the right solution. I think I can share the same folders on the server through both samba and nfs (or another protocol) and use samba when we need to copy files like I described and use nfs when we need to edit files on the server (which is the most frequent scenario). Only time will tell if that will work. If it becomes too confusing to know which Nautilus instance is connected via which file sharing protocol, then it won't be practical. But if it isn't confusing, then it could end up working well. 

Thanks for the ideas.

---

