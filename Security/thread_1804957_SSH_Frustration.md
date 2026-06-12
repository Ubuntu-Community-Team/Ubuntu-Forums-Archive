---
title: "SSH Frustration"
date: 2011-07-15
forum: Security
---

### Post by micajah on 2011-07-15
My level of frustration is reaching new highs -- all thanks to ssh (really all thanks to em not knowing what I am doing)

First question is how do I update openssh to the most current version. I am showing that I have OpenSSH _5.5p1 Debian-4ubuntu5, OpenSSl 0.9.8o 01 June 2010 currently installed. I would like to update to OpenSSH 5.8 (most current version)

Now, onto the real issue.

I was setting up my account on GitHub and was having issues generating the keys. Via GitHub help page:

```
$ ssh-keygen -t rsa -C "your_email@youremail.com"
```

A commenter on this forum suggested I sudo the above command. This solved my access issues and I was able to continue with the GitHub tutorial. I put the public key in my GitHub Account - but I cannot connect. When I try to connect using 

```
$ ssh -T git@github.com
```

I get the reply 

```
Failed to add the host to the list of known hosts (/home/username (me)/.ssh/known_host)
```

The only thing I am uncertain about is the difference between having the key pair stored in /root/.ssh/id_rsa versus /home/user (me)/.ssh/id_rsa

The tutorial on the github help section shows /home/user (me)/.ssh/id_rsa

The public key is now in the root directory,  root@user




Furthermore, I am showing two ssh directories on my computer. One of them is a .shh directory (hidden) under my user account and the other one is a SSH directory under root. All the config files and keys are in this root SSH (not hidden).

Can anybody help me get all this ssh nonsense straightened out . Many thanks!!!

---

### Post by jramshu on 2011-07-15
Navigate to /home/username/.ssh and see if you have the file known_hosts and check the file permissions on it, also make sure that you own it. Check your permissions. Sometimes the file just doesn't exist and you may have to add it.

You may also have to add to your command the location of the private key in order to connect to look something like this
```
ssh -i /home/username/.ssh/nameofkey git@gethub.com
```

You may have to add the -v option to debug the problem that may be causing your problem logging in with keys.

---

### Post by HermanAB on 2011-07-15
Don't understand SSH?

Read the Snail Book:
[http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by The Cog on 2011-07-16
I don't think you should be messing around with root's keys - I think you should be doing it all under your own account. So you should be able to run ssh-keygen in your own account. However, running keygen under sudo might have created keys in your home folder that are owned by root and therefore unreadable to you. Try the command "ls -l .ssh" and see who owns the files. If root does, use this command ```
sudo chown -R micajah:micajah .ssh
``` to give ownership back to yourself (and using your proper username where I have put micajah of course).

---

### Post by 3ruce on 2013-03-01
> **The Cog said:**
> Try the command "ls -l .ssh" and see who owns the files. If root does, use this command ```
sudo chown -R micajah:micajah .ssh
``` to give ownership back to yourself (and using your proper username where I have put micajah of course).

Great, that sorted it out for me too - thanks...

---

