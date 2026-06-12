---
title: "Home folder permissions issue"
date: 2012-08-09
forum: Server Platforms
---

### Post by shirike on 2012-08-09
Hi,

I'm very very new at Linux.

I've installed 12.04 Precise Pangolin on my microsover by following this guide: [http://www.havetheknowhow.com/Install-Ubuntu.html](http://www.havetheknowhow.com/Install-Ubuntu.html)

My first attempt at installing 12.04 went perfect - I could follow every step to completion and the environment worked fine. I'd installed openssh for putty access, installed VNC for remote GUI work and installed samba/webmin for administration of shares etc.

Everything worked fine.

Then I stupidly managed to delete some things I shouldn't have but wasn't too concerned - I'd just do it all over again.

However, I've hit a snag. I've followed the guides steps word for word but suddenly I can no longer create or even access the /home/chris folder within putty.

I am trying to create a folder in /home/chris so I can store cron scripts there.

When I type ```
cd /home/chris
``` I get:

```
chris@ubuntu:~$ cd /home/chris
chris@ubuntu:~$
```


When I type ```
cd /home
``` I get:


```
chris@ubuntu:/home$
```

From there if I type ```
cd /chris
``` I get:

```
chris@ubuntu:/home$ cd /chris
-bash: cd: /chris: No such file or directory
chris@ubuntu:/home$
```

If I type ```
ls
``` I get:

```
chris@ubuntu:/home$ ls
chris
```

Note: chris in the second line above is in [COLOR="Blue"]blue[/COLOR].

Weirdly if I try to make a directory called chris I get:

```
chris@ubuntu:/home$ mkdir chris
mkdir: cannot create directory `chris': File exists

```

When I try to view permissions of "chris" by typing ```
ls -l /home/chris
``` I get:

```
chris@ubuntu:~$ ls -l /home/chris
total 0
```

If I type ```
sudo -i
``` and log into root I am able to traverse the home folder fine.

```
chris@ubuntu:~$ sudo -i
[sudo] password for chris:
root@ubuntu:~# cd /home/chris
root@ubuntu:/home/chris#

```

I am sure I didn't have to log into root on putty to create folders in my first successful install.

Note: I have not encrypted my home folder. I've tried starting from scratch three times now and each time I have the same issue.

I'm sorry if I'm not providing sufficient or the right type of info. I've tried troubleshooting this myself and I suspect I have really cocked up the permissions by trying various chmod/chown commands.

I just can't figure out whether if the problem is with chris@ubuntu OR the /home/chris folder itself.

Any assistance would be greatly appreciated.

---

### Post by Frankincense93 on 2012-08-09
Just a guess, and this is probably not the problem atall.

By try 'cd chris' instead of 'cd /chris'

---

### Post by 2F4U on 2012-08-09
When you execute a command like

cd /folder_name

then folder_name is expected to be at the highest level. If folder_name is a subfolder of the folder you are currently in, then just type

cd folder_name

without a preceeding "/".

You could also type 

cd ./folder_name

to change into the subfolder.

---

### Post by shirike on 2012-08-09
That's the thing - when I type ```
ls
``` there are no directories showing.

So I typed ```
mkdir test
``` and then ```
ls
``` which showed I'd created a directory called test.

I typed ```
find .
``` to get the following:

```

chris@ubuntu:~$ find .
.
./.bash_logout
./.bashrc
./.bash_history
./test
./.cache
./.cache/motd.legal-displayed
./.profile
./.rnd
chris@ubuntu:~$

```

then ```
cd /home
``` and then ```
find .
``` to get:
```
.
./chris
./chris/.bash_logout
./chris/.bashrc
./chris/.bash_history
./chris/test
./chris/.cache
./chris/.cache/motd.legal-displayed
./chris/.profile
./chris/.rnd
chris@ubuntu:/home$

```

I'm confused - how come there is a test folder within chris? I've clearly just created it yet I can't navigate to it?

I type ```
cd /
``` then ```
ls
``` and get:

```
chris@ubuntu:/$ ls
bin   home            lib64       opt   sbin     tmp      vmlinuz.old
boot  initrd.img      lost+found  proc  selinux  usr      webmin-setup.out
dev   initrd.img.old  media       root  srv      var
etc   lib             mnt         run   sys      vmlinuz

```

---

### Post by thnewguy on 2012-08-09
It doesn't look like you've tried to navigate to the test directory at all based on your above example. After you typed

mkdir test

That created the directory. Next type

cd test

And you will be inside the test directory.
Usually I don't recommend books, but I think you might benefit from a textbook like "The Linux Command Line" ([http://nostarch.com/tlcl](http://nostarch.com/tlcl)). It's a good resource for starting you out and dealing with these sorts of operations.

---

### Post by shirike on 2012-08-09
^^ I'll give that a try. Like I said, I have very very basic knowledge. At the moment I'm going to install VNC. It may help me understand things if I can physically see the directories etc.

---

### Post by shirike on 2012-08-09
The penny has finally dropped. I can't cd into chris because chris@ubuntu is already there.

Installing VNC made it all so very clear to me.

D'oh.

---

