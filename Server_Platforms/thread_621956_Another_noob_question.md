---
title: "Another noob question"
date: 2007-11-24
forum: Server Platforms
---

### Post by johnswb on 2007-11-24
I have installed Ubuntu Desktop 7.10 on my workstation and Ubuntu Server 7.10 on an old server that I have.  My question is... how do I copy a file / folders /  from my workstation to my server?

---

### Post by HermanAB on 2007-11-24
Pick one of these:
a. Floppy disk
b. CDROM
c. USB memory stick
d. FTP,
e. SSH
f. Samba
g. NFS

---

### Post by johnswb on 2007-11-24
thx,

If I ssh to the server then how?

---

### Post by HermanAB on 2007-11-24
There are three aspects to SSH.  You can use it to log into a remote server and get a shell on the distant machine.  You can use it to copy files to/from a distant machine.  You can use it to set up encrypted tunnels between two machines.  

SSH is extremely flexible and therefore it can be a bit daunting at first, but usually, it 'Just Works'.

First test ssh.  Open a terminal and log into the remote server:
$ ssh username@serveripaddress
Password: userpassword
$ ls
(That should list the files in the home directory of the user.)

If that works, then you are all set and can use secure copy 'scp' to copy files (or whole directory trees).  

Open another terminal and do something like this:
$ echo "hello world" > test
(That will create a test file.)

$ scp test username@serveripaddress:~/.
Password: userpassword
(That will copy the file to the server)

Now go to the first terminal and verify that the file is there:
$ ls
(The file 'test' should be visible.)

Cheers,

H.

---

### Post by HermanAB on 2007-11-24
If you get stuck, send me a private message, since by default I don't subscribe to threads - too much junk mail.

---

### Post by johnswb on 2007-11-25
HermanAB,

That did it...

Thank you very much...

---

### Post by MJN on 2007-11-25
John,

Just a polite tip for next time - put something meaningful in the subject title then it helps others know what the thread is about (imagine if we all put 'Another noob question', 'Please help!', 'What's this?', 'Help a newbie' as the subject... the forums would be a right mess!) :)

In your case something like 'Copying files from one machine to another?' would've been better.

Mathew

---

