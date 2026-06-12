---
title: "How to transfer files from windows client to a ubuntu server?"
date: 2008-04-06
forum: Server Platforms
---

### Post by aaron792 on 2008-04-06
Hello everyone!
I am using a windows XP client to upload hundreds of thousands of small-sized files to a ubuntu7.04 server. Due to  the giant amount graphical tools can not help(actually it often lost responses after I expanded some directories). I try to use the prompt command like:

```
scp -r C:\testFile.txt 192.168.69.144:/home/ailabir/data/
```

but ssh reponds:

```
ssh: C: Name or service not known
```

I tried some other forms like:
 
```
scp2 -r C:\testFile.txt ailabir@192.168.69.144:/home/ailabir/data/  
```

but it stll can not work. And sometimes it returned strange uninterprettable characters(may be because I am from foreign China :)).
My hard disk is ntfs format. And the graphical tool can work properly.
Can someone show me the correct command?
Thanks!

---

### Post by netlogic on 2008-04-06
Please tell us which ssh package for windows that you are using.

> scp2 -r C:\testFile.txt ailabir@192.168.69.144:/home/ailabir/data/

Shouldn't this be,

```
scp testFile.txt ailabir@192.168.69.144:/home/ailabir/data/
```

you can always 

```
sftp ailabir@192.168.69.144
lcd C:\
cd /home/ailabir/data/
mput *.*

```

---

### Post by aaron792 on 2008-04-06
:)Thanks for your reply, netlogic!
I've followed your suggestion. Seems it is quite near to the success.
I am using SSHSecureShellClient-3.2.9 version and I can connect to the server through VNC.
I tried your command:
```
ailabir@ailabir-desktop:~$ scp testFile.txt ailabir@192.168.69.144:/home/ailabi
r/data/
ailabir@192.168.69.144's password: 
testFile.txt: No such file or directory
```
Seems that I should change the current directory to the storing directory of testFile.txt.
Can u show the command, I am a very beginner.
Thanks!

---

### Post by koenn on 2008-04-06
the command your looking for is 'cd', as in
```
cd "c:\documents and settings\ailabir\My Documents"
```
or (linux)
```
cd /home/ailabit/data
```
but you could also include the path in the scp command, like you did before ( scp2  "c:\documents and settings\ailabir\My Documents\MyFile.txt ....... )

---
strange : you say you want to copy **from** a Windows XP machine, but 'ailabir@ailabir-desktop:~$ " looks like a bash prompt. Do you run bash on Win XP ?

---

### Post by aaron792 on 2008-04-06
I am very confused now. I am using SSH on a windows XP OS to connect to a ubuntu7.04 server. After I quick connect the server, the prompt becomes "ailabir@ailabir-desktop:~$ "
I try to use
```
ailabir@ailabir-desktop:~$ scp 192.168.69.167:c/testFile.txt /home/ailabir/data

```
192.168.69.167 is my windows client IP. But it doesn't work.
```
ssh: connect to host 192.168.69.167 port 22: Connection timed out
```

---

### Post by koenn on 2008-04-06
> **aaron792 said:**
>  After I quick connect the server, the prompt becomes "ailabir@ailabir-desktop:~$ "
That's because that "quick connect" opens a session on the server.
you shouldn't do that. just run something like 'scp  testfile   server:/destination ' from a Windows cmd prompt - scp by itself will handle any connection it needs and probably ask for passwords etc. 

post the excact commands + their output in case you have trouble with this, so that people here can look for syntax errors and other mistakes (I have places to go and people to see right now, so I can't walk you trough it)

---

### Post by aaron792 on 2008-04-06
Koenn, I must give u a THANKS first!
Follow your instructions. Job done.
I will brief general procedures in a later reply.
Hope this can help somebody who encounters the same problem.

---

### Post by aaron792 on 2008-04-06
When u want to transfer some files from widows client to a ubuntu server
1)Install ssh on both machines. Make sure the connection is ok.
2)Add your_install_path\SSH Communications Security\SSH Secure Shell to your classpath variable in system variables.
3)Open a cmd window, change the directory to where your files store.
4)Use command like:
```
  scp2 -r directory user@server:/directory
  scp2 file user@server:/directory
```
Hope this can help.

---

### Post by harrybazeegar on 2008-04-06
try this:

SSHSecureShellClient
[http://www.mediafire.com/?50j2ddm5n5b](http://www.mediafire.com/?50j2ddm5n5b)

this program gives you an intuitive file transfer program.. and also a terminal login.... u'll know when u see it.

I used this once and never looked to anything else... i'm sure u will love it

---

### Post by hyper_ch on 2008-04-06
why not zipping it, upload it and extract it on the server through the shell?

---

