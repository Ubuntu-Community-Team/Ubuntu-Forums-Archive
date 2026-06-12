---
title: "how to run a shell command as another user?"
date: 2011-04-26
forum: Server Platforms
---

### Post by alrave on 2011-04-26
Hello, I've been trying to figure out how to do this the whole day. 

The short version: I have to manage some virtual machines using php shell_exec function, so far I cant do this because apache is run by the user www-data and virtualbox by the user vboxuser


From what I've read so far, I've thought of 3 possible solutions: 
1.- Create a script on my vboxuser that I can call from php to manage the Virtual Machines.
2.- Change the apache user from www-data to vboxuser so I can manage the Virtual Machines through php
3.- Reinstall VirtualBox, this time using www-data as my user. 

I'm not sure if any of these will work and I'm not too sure of which would be the best solution. Any suggestions/ideas? 

Thanks in advance.


Now the longer more detailed version:

I have a remote server running Ubuntu 10.04.2, in that server I have set up VirtualBox so I can run several instances of WinXP to perform different tasks. 

Everything is setup and I can manage the virtual machines through SSH. If I want to run them as a different user than the one that created them (a user that so far only has been used to create the Virtual Machines) I have to do sudo -u vboxuser.

Now, I need to create a PHP script to manage these virtual machines (I know about phpVirtualBox, but it's not what I need). If I try to run the virtual machines using shell_exec() from php, I get no answer at all (And I have tested that shell_exec is working on my server).

---

### Post by thinmintaddict on 2011-04-27
VirtualBox installs for all users, not just the initial user. This means that you can always use the hack-ish solution of creating a new VM as www-data, and point it at the virtual disk created by vboxuser.

The only other option I can think of would be to give www-data password-less sudo privileges so that you can use sudo -u vboxuser in a bash script as www-data, but this is extremely insecure, so I would avoid this option if you can.

I have very little experience calling scripts from php though, so hopefully someone else can come up with a less hack-ish solution.

Hope this helps,

TMA

---

### Post by HermanAB on 2011-04-27
Howdy,

The su command is what you are looking for, not sudo.

---

### Post by Lord_ on 2011-04-27
You can create small shell scripts for php's shell_exec() to call which contains the tasks. On those shell scripts, you can owner to root with the suid set (chmod 4755 - I think) then make sure they are in a path which www-data can reach.

I've had a similar problem a couple of time in the past, and I think thats how I got round it.

Needless to say, it does open a bit of a security risk, as all users will be able to run the script as root, so be careful what's inside, and check only root can change.

---

### Post by HermanAB on 2011-04-27
```
SU(1)                            User Commands                           SU(1)

NAME
       su - run a shell with substitute user and group IDs

SYNOPSIS
       su [OPTION]... [-] [USER [ARG]...]

DESCRIPTION
       Change the effective user id and group id to that of USER.

       -, -l, --login
              make the shell a login shell

       -c, --command=COMMAND
              pass a single COMMAND to the shell with -c
```

---

### Post by Lars Noodén on 2011-04-27
> **HermanAB said:**
> Howdy,

The su command is what you are looking for, not sudo.


**sudo** will do it also, if you use the **-u** option.

---

### Post by alrave on 2011-04-27
Thanks for the replies, I think I'm going to try and create a shell script I can call from php. If that fails I'll try to create the VM's using www-data, although I tried to log as that user but have no idea of it's password, but I'm sure a google search should get me that.

---

