---
title: "Vmware is killing me! Request help..."
date: 2007-03-26
forum: Server Platforms
---

### Post by goliant on 2007-03-26
Hey,

I am gonna 'splode... I would really appreciate it if any one can shed some light on this problem. I have a Edgy Server running VM Server, I installed the MUI as well. I can access the MUI VIA the [https://ip:8333](https://ip:8333) on XP Pro and setup the VM but when I try to power on the VM (Ubuntu Desktop), I get this message:

The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Directory "/home/goliant/.vmware" is not accessible: Permission denied.
Cannot proceed without directory "~/.vmware". It is needed to store user preferences and other information.

Failed to initialize VM.
End of error message.

Also when I "log" onto the MUI with my username I can't access the "options" tab. I get a goliant@scserver is not authorized to modify host configuration options error.

Any takers?!

Regards,
Brian

---

### Post by conjur3r on 2007-03-26
I guess the first point of call is to check the permissions you have on /home/goliant/.vmware

I assume you are logging in using the goliant user account from MUI (btw, what is a MUI)?  VMWare Server has built in remote administration where you can use the VMWare Server Console to manage remote servers.  Anyway, make sure goliant owns everything within /home/goliant/.vmware

---

### Post by goliant on 2007-03-26
Thanks - I just did the bare bones Ubuntu server install, the MUI is the VMware Managememt User Interface which allows me to access the server from Firefox.   

I get the same message using the console on my XP system. I can access and write files to the .vmware folder from XP. What would a command line be to check ownership of such a folder?

I also have SAMBA installed and I have read a few instances of people having difficulties with VMware, SAMBA and permisions. 

I believe it is a permissions issue i just don't know where to verify this. 

Thanks again

---

### Post by stalefries on 2007-03-26
In your home directory, please run this command:
```
ls -al|grep .vmware
```
and then paste the output here in [ code ] [ /code ] tags (without the spaces in the tags).
Then, cd to the .vmware dir and run 
```
ls -al
```
and paste that output here too.

---

### Post by goliant on 2007-03-26
This is the output of the ls -al|grep .vmware command:

```
drwxr-xr-x 2 root    root         4096 2007-03-24 23:10 .vmware
```

> ls -al
total 139172

```
drwxr-xr-x 4 goliant goliant      4096 2007-03-26 13:49 .
drwxr-xr-x 4 root    root         4096 2007-03-23 10:47 ..
-rw------- 1 goliant goliant      2705 2007-03-26 10:14 .bash_history
-rw-r--r-- 1 goliant goliant       220 2007-03-23 10:47 .bash_logout
-rw-r--r-- 1 goliant goliant       414 2007-03-23 10:47 .bash_profile
-rw-r--r-- 1 goliant goliant      2227 2007-03-23 10:47 .bashrc
-rw------- 1 root    root         1024 2007-03-26 10:13 .rnd
-rw-r--r-- 1 goliant goliant         0 2007-03-23 10:55 .sudo_as_admin_successful
drwxr-xr-x 2 goliant goliant      4096 2007-03-26 14:00 Ubuntu-6.10-desktop-i386
drwxr-xr-x 2 root    root         4096 2007-03-24 23:10 .vmware
-rwxr--r-- 1 goliant goliant  35719140 2007-02-20 17:44 VMware-mui-1.0.2-39867.tar.gz
-rwxr--r-- 1 goliant goliant 106598766 2007-02-20 17:50 VMware-server-1.0.2-39867.tar.gz
```

OK so this shows that only root has access to the .vmware folder correct? How do I change that?

Thank you very much for your help stalefries!

---

### Post by PilotJLR on 2007-03-26
Not to steal stalefries' thunder (he figured this one out), but here is how you change the owner:
```

sudo chown goliant:goliant -R .vmware/

```

That should take care of the directory and everything in it.

---

### Post by goliant on 2007-03-26
You people rock....that was fantastic response times! Thank you very much - that was the final peace of the puzzle (for today). I can now get some sleep!


All the best!

---

### Post by goliant on 2007-03-26
This was great - does any one have experience with the VMware MUI? When I try to choose the "options" tab beside the status monitor, i get a "not authoirized to modify host configuration options" error message.

I can sleep when I am dead...

---

### Post by goliant on 2007-04-04
I was able to resolve this by doing a search on dependinecies and installed everything I came accross. Including libx11-6 libx11-dev libxtst6 xlibs-dev libice-dev libsm-dev libxrender-dev libxi-dev. I then ran "/usr/bin/vmware-config.pl" so I did not have to reinstall.

good luck

---

