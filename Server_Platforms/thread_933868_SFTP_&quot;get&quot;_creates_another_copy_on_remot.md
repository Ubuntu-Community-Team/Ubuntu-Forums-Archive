---
title: "SFTP &quot;get&quot; creates another copy on remote machine"
date: 2008-09-29
forum: Server Platforms
---

### Post by Shwick2 on 2008-09-29
I'm running ubuntu 8.04 with ssh server.  I do the following with putty from my windows machine:

1. connect/login to linux machine with ssh
2. login to sftp, "sftp user1@desktop", enter password
3. try to get a file, "get Desktop/testFile"
4. receive message, "Fetching /home/user1/Desktop/testFile to testFile"

 The file is transferred to another directory on the linux machine, it doesn't get to the windows machine.  It is copied from /home/user1/Desktop to /home/user1.

 I tried entering remote directories such as "get Desktop/testFile C:/testFile", but received an error: "Couldn't open local file "C:/testFile" for writing: No such file or directory".

 Command "get Desktop/user1 C:/" resulted in "Couldn't open local file "C:/" for writing: Is a directory".

 Any ideas on transferring the file?

---

### Post by cariboo on 2008-09-30
use Winscp it is a free download, no need to transfer files from the command line.

Jim

---

### Post by Shwick2 on 2008-09-30
I already installed WinSCP and it works properly, it can copy files from the linux machine to my windows comp.  

I just want to know how to do it with putty command line using sftp.  The help pages for sftp said issuing the get command would transfer the file but it doesn't.

---

### Post by cariboo on 2008-09-30
I found this command summary, perhaps it will help.

[http://www.cae.wisc.edu/linux-sftp](http://www.cae.wisc.edu/linux-sftp)

Jim

---

### Post by lykwydchykyn on 2008-09-30
With FTP get (and SFTP as well), you don't specify a destination that way.  When you specify a location like that, SFTP thinks that's just a second file you want to download from the server.

To specify the destination on the client, you need to set the local working directory with the lcd command.

---

### Post by Shwick2 on 2008-09-30
I found the problem, I was already logged onto ubuntu from ssh so the local directory was the ubuntu directory.  Use a sftp client like psftp, [http://the.earth.li/~sgtatham/putty/latest/x86/psftp.exe](http://the.earth.li/~sgtatham/putty/latest/x86/psftp.exe).

This thread helped me: [http://ubuntuforums.org/showthread.php?t=369221](http://ubuntuforums.org/showthread.php?t=369221)

---

