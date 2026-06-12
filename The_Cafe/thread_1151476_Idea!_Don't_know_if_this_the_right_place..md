---
title: "Idea! Don't know if this the right place."
date: 2009-05-07
forum: The Cafe
---

### Post by anti_microsoft on 2009-05-07
Hello all,

I had a brainstorm tonight and was thinking about upgrading to Jaunty, but with this nice setup I have, I don't know if I want to (8.04).

I keep a separate partition for my /home. As we all know after some use this can get really loaded with all kinds of hidden folders that hold the config setting for a lot of programs. Not to mention the important info you may have located here that you may not want to lose (I know backup(I do) not my point). So instead of having to comb though tons of hidden folders to clean /home, is there a script that with let you do something like this?

Example:
```

sudo apt-get install foo
sudo foo
Welcome to foo, foo is checking system for installed programs
foo has found ## programs on (x)(k)Ubuntu
foo is checking how many of these programs you have installed
foo found 52 programs that you have installed
would you like to generate a script to download these 
programs on your new install y/n? y
Generating script
thank you for using foo you script has been saved in you
home directory

```

Now I copy the script to my thumb drive. Install latest and greatest Ubuntu. Copy over the script to my home.

```

sudo sh foo.sh
Thank you for running foo running apt-get update please wait!
Would you like to restore your applications now? y/n? y
Downloading please be patient....
Congratulations all your applications are now installed! 

```

It could save the original config files and let you choose what to overwrite (this could be in the program).

Now I don't code but like the idea. Does this exist or is it possible? Would be awsome!

---

### Post by monsterstack on 2009-05-07
You don't have to nuke your hard disk with every new version of Ubuntu, you know. There is also an upgrade feature.

---

### Post by Eviltechie on 2009-05-07
No you don't have to nuke it, but after a few upgrades, a dozen servers and other things, your install can get crufty. This happens with windows too. I did a fresh install from 8.10 to 9.04 for that very reason.

As for your program, I was thinking of something along the same lines as that.

---

### Post by anti_microsoft on 2009-05-07
> **monsterstack said:**
> You don't have to nuke your hard disk with every new version of Ubuntu, you know. There is also an upgrade feature.

Yes, but those of us who run linux for years on end end up with a really full drive with worthless crap on it. With this you could do a fresh install and have a nice clean slate to start with.

---

### Post by FuturePilot on 2009-05-07
I always upgrade myself, but if you ever find yourself in such a situation 

```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```

That creates a file called package_list that contains the name of every package installed on your system.

Then on a fresh install you can
```
sudo apt-get update
cat package_list | xargs sudo apt-get install -y
```

That will install all the packages from the file created earlier. Just don't forget to take the package_list file with you to your new install. ;)

---

### Post by Skripka on 2009-05-07
> **anti_microsoft said:**
> Yes, but those of us who run linux for years on end end up with a really full drive with worthless crap on it. With this you could do a fresh install and have a nice clean slate to start with.

How does your drive accumulate "worthless crap"?  I don't understand.  If you tidy up after an uninstall of a software, things are just like they were before you installed it in the 1st place.

---

### Post by monsterstack on 2009-05-07
whoops

---

### Post by anti_microsoft on 2009-05-07
> **Skripka said:**
> How does your drive accumulate "worthless crap"?  I don't understand.  If you tidy up after an uninstall of a software, things are just like they were before you installed it in the 1st place.

Bound to happen in any upgrade situation after many. No OS is perfect at being completely able to rid itself of every little piece of old software and it can be very cumbersome trying to track down.

---

### Post by Skripka on 2009-05-07
> **anti_microsoft said:**
> Bound to happen in any upgrade situation after many. No OS is perfect at being completely able to rid itself of every little piece of old software and it can be very cumbersome trying to track down.

If it is installed by package, and not loose source code, it is actually quite easy.  Apt keeps a database of everything there is--so long as the config files are updated correctly it should go fine.

---

### Post by anti_microsoft on 2009-05-07
> **FuturePilot said:**
> I always upgrade myself, but if you ever find yourself in such a situation 

```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```

That creates a file called package_list that contains the name of every package installed on your system.

Then on a fresh install you can
```
sudo apt-get update
cat package_list | xargs sudo apt-get install -y
```

That will install all the packages from the file created earlier. Just don't forget to take the package_list file with you to your new install. ;)

That is nice to know. I just ran that and the only problem is it gets every program on my system. I trust Ubuntu to give me a good base install, this program would would only give programs I've installed.

I do like that though, nice to know indeed.

---

### Post by anti_microsoft on 2009-05-07
> **Skripka said:**
> If it is installed by package, and not loose source code, it is actually quite easy.  Apt keeps a database of everything there is--so long as the config files are updated correctly it should go fine.

Even if we call that moot, there is still the issue of doing a fresh install on a new machine (or this machine because of data lose).

---

### Post by CarpKing on 2009-05-07
Torrenting the CD + installing fresh + installing packages is usually faster for me than upgrading (though the last step can suffer from the same problems).  It also just feels cleaner somehow.  

I've been using the command mentioned earlier, but I do have to spend some time deleting entries that are no longer available; I am also concerned that I might be pulling in obsoleted dependencies.  I wonder if it would be possible to filter out all dependencies of ubuntu-desktop from the list for a start.  Optimally it would be nice to create a list of only explicitly installed packages and let apt handle their dependencies in the new Ubuntu version.  If anyone has any neat commands to do stuff like this, post away.

---

### Post by anti_microsoft on 2009-05-07
> **CarpKing said:**
> Torrenting the CD + installing fresh + installing packages is usually faster for me than upgrading (though the last step can suffer from the same problems).  It also just feels cleaner somehow.  

I've been using the command mentioned earlier, but I do have to spend some time deleting entries that are no longer available; I am also concerned that I might be pulling in obsoleted dependencies.  I wonder if it would be possible to filter out all dependencies of ubuntu-desktop from the list for a start.  Optimally it would be nice to create a list of only explicitly installed packages and let apt handle their dependencies in the new Ubuntu version.  If anyone has any neat commands to do stuff like this, post away.

I really think this would be why a script or something of some sort like I said would be neat. This program could erase version names and only include what you have installed (I noticed in the aforementioned command it had firefox-3.0 as a result of that command). 

The whole point of *buntu is to remain easy, this would make upgrading a painless effort (namely fresh installing).

---

### Post by Saint Angeles on 2009-05-07
> **monsterstack said:**
> You don't have to nuke your hard disk with every new version of Ubuntu, you know. There is also an upgrade feature.
i would say an important reason for doing a fresh install of jaunty is reformatting using ext4 instead of ext3.

woot!

---

### Post by 3rdalbum on 2009-05-07
Packages get renamed or obsoleted every so often, so while your idea is a good one, it would take a bit of work to actually get it running well.

---

### Post by Kareeser on 2009-05-07
Give your idea a whirl at [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)!

---

### Post by Skripka on 2009-05-07
> **Saint Angeles said:**
> i would say an important reason for doing a fresh install of jaunty is reformatting using ext4 instead of ext3.

woot!

You could have upgraded your ext3 partition to ext4, rather than outright reformat ;)

---

### Post by aysiu on 2009-05-07
The correct place to post brainstorms is Brainstorm:
[http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

---

