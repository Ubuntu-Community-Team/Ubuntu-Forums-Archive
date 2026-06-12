---
title: "Crazy Attributes given on file creation"
date: 2019-07-19
forum: Server Platforms
---

### Post by lorchris on 2019-07-19
I am not sure if this is the right section to ask this question but I hope it is.

I have a remote server running Ubuntu 14.

Everything has been fine for a long time but recently whenever a file is created it gets crazy random attributes.
For example one file will have 5010 ( --S--x--T), another will have 10 ( -----x---).
It also happens if I FTP a file to the server.

Before the files were always 644 (-rw-r--r--).

The files are created by the same user.
If the files are directed to be created on one of my other servers they are created with the correct attributes.
Which shows the problem is only with this server.

I have spent days trying to find this problem on the internet but cannot see any thing mentioned about it anywhere!

I do not want to reformat the server and install the OS again because I have nearly 15TB of data and nowhere to back it up to!

Hope someone can help.

---

### Post by wildmanne39 on 2019-07-19
Hello and welcome to the forum!

*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by volkswagner on 2019-07-21
Ubuntu 14 has reached end of standard support.
You should rebuild your server with a currently supported version.

Hmm, no backup? I guess you don't value your data ;)

FTP is not secure and should be avoided. Hopefully you are
using a VPN to route the FTP stream.

If you ssh directly and create a file and/or directory, does the
symptom occur? Is the issue limited to a certain directory?
Is the issue limited to a particular user?

---

### Post by SeijiSensei on 2019-07-21
The UMASK determines the permissions for newly-created files and directories.  It is the "octal-complement" of the permissions you want. By default it is set to 022 which translates to permissions of 644 on files and 755 on directories.

It is set in the file /etc/login.defs.  Most people would never touch this value, so I'm puzzled why you're getting the results you report.  You need to edit that file with sudo.

You can change the umask on the fly in a shell session by typing the command "umask 022" at the prompt.  If you change the UMASK parameter in login.defs, you will need to log out and log back in.

It's possible you have some squirrely umask set for the user you are FTPing as.  Take a look at .bash_profile and .bashrc in the home directory of that user and see if there is a umask command.  If so, and you didn't change it yourself, I'd be worried about who did.

---

### Post by TheFu on 2019-07-26
Being the pessimist that I am, I'd assume a server out of support for even 1 month has been hacked and the group/person who did it doesn't really know Unix.
Or, the better situation would be file system corruption or some hardware failure.  Boot from alternate media and run **fsck** on the file system. While you are there, it would be good to check the disk SMART data for any issues.

The umask stuff is a viable explanation. I would never have thought of it, since it means someone modified at least 1 file that I didn't know about.  If that is true, we are backed to being hacked.

No backups? Ouch.  I fear you'll have to learn the same lesson I did long ago, the hard way. I still remember the empty feeling in my gut when I finally gave up hope of getting my data back.  BTW, a 64G flash drive is like $15. I got a used 250G spinning disk at a local retailer for $9 about 2 yrs ago. There really isn't any excuse not to have a backup.  

I also agree with the FTP concerns. sftp provides the same interface, just encrypted and with strong authentication that doesn't use passwords, if you like.  Almost every Linux file manager will support sftp:// URLs and if you have ssh keys setup between the desktop and the hacked server, then you won't be hassled for login credentials.  Better security AND more convenient?  That never happens, right?

---

