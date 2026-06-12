---
title: "SSH Files: Vista -&gt; Ubuntu?"
date: 2009-05-27
forum: Server Platforms
---

### Post by basicxman on 2009-05-27
Hello,
  I've setup an old computer with Ubunutu server edition 9.04.  My vista computer successfully SSH's it's way into it with the windows program PuTTY.  What I'm wondering is how can I copy my files in Vista computer (putty.exe is in C:\Users\Andrew) to my Ubuntu computer (copy to /home/compbackup)

could somebody please give me a sample command on how I would copy my files in C:\Users\Andrew\Pictures to /home/compbackup, I've tried the following command and I get the error message below

Command:
scp -r /Pictures/ backupuser@192.168.0.104:/home/compbackup

Error:
/Pictures: No such file or directory

Am I doing something wrong?  Thanks

---

### Post by dmizer on 2009-05-27
Try this:
```
scp -r /Users/Andrew/Pictures backupuser@192.168.0.104:/home/compbackup
```

---

### Post by basicxman on 2009-05-27
same error, tried sudoing the command, no luck either.  Any ideas? thanks so far

---

### Post by basicxman on 2009-05-27
Vista is setup to allow file sharing, etc BTW

---

### Post by dmizer on 2009-05-27
> **basicxman said:**
> Vista is setup to allow file sharing, etc BTW

Doesn't matter with ssh.

To use scp from Vista, you'll need winscp: [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) it works like an ftp client.

---

### Post by Jekshadow on 2009-05-28
Ubuntu to Vista:

Places -> Connect to Server
Then select "Windows Share" and enter the info.


Vista to Ubuntu:

Get WinSCP.
It is fairly simple

---

### Post by BkkBonanza on 2009-05-28
It sounds like you are logging in with putty and doing the scp command. This won't work because putty is just a terminal program - it doesn't have any access to Vista local files to support scp. You need something on Vista that can access and copy files. Last post regarding WinSCP is likely your best option and I've used that successfully. 

Another way is to install cwrsync which uses the cygwin linux libraries. This lets some linux utils like rsync work on Windows. Google cwrsync - the install package is fairly easy and it gives you command line tools like rsync and ssh which can be useful especially if you need to automate the file copies. rsync is similar to scp but probably more flexible. It is secure when run over ssh which only requires that you have sshd running on your server, usually true by default.

Deltacopy is also an rsync windows equivalent but I haven't used it.

---

