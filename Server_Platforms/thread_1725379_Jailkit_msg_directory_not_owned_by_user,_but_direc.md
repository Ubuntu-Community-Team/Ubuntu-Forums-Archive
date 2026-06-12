---
title: "Jailkit msg: directory not owned by user, but directory IS owned by user"
date: 2011-04-09
forum: Server Platforms
---

### Post by holiday on 2011-04-09
I'm trying to jail a sftp user. All I want is for my daughter-in-law to be able to download pictures of my grandson on his step-uncle's motorcycle. 

But I don't want her browsing around. She's not a techie, but she's smart enough to catch on how WinSCP is looking at my files. 

I've set up the jail using jk_init, adding ssh, sftp, bash, netutils, basicshell, jk_lsh.

The physical root of the jail is owned by root, as are all the binaries loaded by the jk_init. The user's home directory is owned recursively by the user and is writable only by the owner. The passwd and group files are in the jailed /etc and populated by the user's lines. Shell is bash, and bash is there too. 

The error message must be coming from some other problem that's not notifying, but what?

Ideas?

---

### Post by holiday on 2011-04-14
I have made progress.

I was getting that error because my /etc/passwd setting was incorrect.

The /etc/passwd setting for the user's home directory must point to the jailed home directory, as so:

prisoner:x:1010:1010:prisoner,,,,:/home/jail/./home/prisoner:/usr/sbin/jk_chrootsh
(faces not intended - some forum feature out of control)

Note that the /home/jail/. points to the jail, and the rest is the prisoner's home directory within the jail. I'd missed that part. The error message was telling me that the home directory specified by the physical /etc/passwd was not the prisoner's home directory. 

But now I have another problem.

I'm getting "bad interpreter" on logging in. 

I suspect this is because /bin/sh in Ubuntu points to dash whereas Jailkit is expecting bash. So I created a <thejail>/bin/sh link to point to <thejail>/bin/bash.

Didn't work.

So what's the problem? Any ideas?

---

### Post by espressobeanie on 2011-04-15
Impossible logic. Why don't you give her a seperate user account, put the picture in /home/yourusername/Pictures and 'chmod 755 -R /home/' and chown root -R /home/'? Or if you're worried about her finding your personal files, chmod 600 -R the foldernames. Then log off root and tell her happy browsing.

Chmod 600 -R (directoryname) locks the directory so that root can only read.
Chown 600 -R (directoryname) locks the privileges so that root can only change the permissions.

It sounds like you were trying to do some chroot. Please refer somewhere that this is in reference to SSH or SFTP Server, whichever you're running.

---

### Post by holiday on 2011-04-15
I see the wisdom in strictly defining access to data I consider private, and I thank you for raising that point. I have a naive faith in the Ubuntu defaults, I suppose. Is there any reason to not set my home directory to 700? Now that you ask, I can't think of one.

On the other hand, I have been interested in chroot jailing ever since I first heard of it. It is perhaps the simplest implementation of a virtual machine. 

Once I get it figured out.

I know I know. I could use Virtual Box, and I do. I could set up a vm with a static ip and its own special ssh port and forward my router right to it.

But I want to learn the jail. 

Thanks again for talking about taking control of permissions. That's a good point.

---

### Post by holiday on 2011-04-16
Fixed it with the following:

# jk_init -v <the jail> basicshell
# jk_init -v <the jail> extendedshell

I didn't have a shell defined through jailkit. Although the shell was specified through the passwd file, I had not copied all the files required by the shell. The jk_init knew more than me.

---

