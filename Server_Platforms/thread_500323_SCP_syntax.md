---
title: "SCP syntax?"
date: 2007-07-13
forum: Server Platforms
---

### Post by 56seeker on 2007-07-13
I'm having a lot of problems getting scp to work.

Can any one spot where I'm going wrong? I'm trying to copy a file from my server (virtual-fake: 192.168.2.90) to my laptop (fd-portable: 192.168.2.100)
[HTML]seeker@fd-portable:~$ scp myfile seeker@192.168.2.90:/vm-data/text.txt
seeker@192.168.2.90's password: 
myfile: No such file or directory
seeker@fd-portable:~$ scp /vm-data/test.txt seeker@192.168.2.90:myfile
seeker@192.168.2.90's password: 
/vm-data/test.txt: No such file or directory
seeker@fd-portable:~$ 
seeker@fd-portable:~$ ssh 192.168.2.90
seeker@192.168.2.90's password: 
[seeker@virtual-fake seeker]$ cd /vm-data/
[seeker@virtual-fake vm-data]$ ls
base  lost+found  serverfarm  test.txt
[seeker@virtual-fake vm-data]$ scp test.txt seeker@192.168.2.100:myfile
ssh: connect to host 192.168.2.100 port 22: Connection refused
lost connection
[seeker@virtual-fake vm-data]$ [/HTML]

Thanks a lot!

---

### Post by Mr. C. on 2007-07-13
> **56seeker said:**
> I'm having a lot of problems getting scp to work.

Can any one spot where I'm going wrong? I'm trying to copy a file from my server (virtual-fake: 192.168.2.90) to my laptop (fd-portable: 192.168.2.100)
[HTML]seeker@fd-portable:~$ scp myfile seeker@192.168.2.90:/vm-data/text.txt
seeker@192.168.2.90's password: 
myfile: No such file or directory

There is no file named **myfile** in the current directory.

> **56seeker said:**
> 
seeker@fd-portable:~$ scp /vm-data/test.txt seeker@192.168.2.90:myfile
seeker@192.168.2.90's password: 
/vm-data/test.txt: No such file or directory

There is no file named **/vm-data/test.txt** on the local machine

> **56seeker said:**
> 
seeker@fd-portable:~$ 
seeker@fd-portable:~$ ssh 192.168.2.90
seeker@192.168.2.90's password: 
[seeker@virtual-fake seeker]$ cd /vm-data/
[seeker@virtual-fake vm-data]$ ls
base  lost+found  serverfarm  test.txt

This proves there is a **/vm-data** directory and the files within that directory shown above on the remote host (192.168.2.90), but earlier you were using a command that implied the directory resides on your fd-portable.


Scp's basic syntax is :

scp src_file dst_file

Look at ls' output of src_file before you scp - what does it show ?

MrC

---

### Post by 56seeker on 2007-07-14
Thanks for the help; although I'm afraid I'm not much clearer about where I'm going wrong.

"Scp's basic syntax is :

scp src_file dst_file"

Well, that's what I thought I was doing with :

[PHP]seeker@fd-portable:~$ scp /vm-data/test.txt seeker@192.168.2.90:myfile[/PHP]

Doesn't that show that I'm logged on to the lap top; requesting a file called "test.txt" which resides in a folder called "vm-data" and belongs to seeker on 192.168.2.90 and that I want it copied to the local machine and renamed "myfile"?

Seeing as ls proves the file is there:

[PHP][seeker@virtual-fake vm-data]$ ls
base lost+found serverfarm test.txt[/PHP]

Why do I get file not found?

---

### Post by koenn on 2007-07-14
> **56seeker said:**
> 
[PHP]seeker@fd-portable:~$ scp /vm-data/test.txt seeker@192.168.2.90:myfile[/PHP]

Doesn't that show that I'm logged on to the lap top; requesting a file called "test.txt" which resides in a folder called "vm-data" and belongs to seeker on 192.168.2.90 and that I want it copied to the local machine and renamed "myfile"
No, it shows that
- you are logged on as 'seeker' on a computer named "fd-portable'
- you want a file  /vm-data/test.txt copied to computer 192.168.2.90, ...
- having the file renamed to 'myfile' in the process
- and you will use the account "seeker" on computer 192.168.2.90 to gain access to that computer

You should also specify a directory on 192.168.2.90 where you want 'myfile' to be put, eg ... @192.168.2.90:**/home/seeker/**myfile

With all that, re-read Mr.C's comments on missing files, they'll begin to make sense to you now  ;-)

---

### Post by Mr. C. on 2007-07-14
Your problems are being caused by the ambiguous commands you are using, and your confusion about relative pathnames.

We cannot see the name of the current directory you are in, and hence your **ls** output is of little use (other than to tell us there some file named **test.txt** *somewhere*).  Here's what you need to do to start clarifying things to yourself.... *use full pathnames* until you get the hang of relative pathnames.  Eg: 
```

ls /vm-data
ls /vm-data/test.txt
scp /vm-data/test.txt othermachine:/tmp/test.txt
```

and show the current host's name and current working directory

```
hostname
pwd
```

Your default prompt, if configured correctly, and is operational, gives hints, but does not provide proof of your hostname, and only gives the last directory component of your current working directory.

MrC

---

### Post by 56seeker on 2007-07-19
Thanks; I think I've got it sorted out now!

---

