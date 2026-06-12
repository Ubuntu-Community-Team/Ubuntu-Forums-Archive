---
title: "Hi from a Linux n00b - exploring ubuntu and terminal commands."
date: 2013-11-11
forum: Ubuntu, Linux and OS Chat
---

### Post by mike44njdevils on 2013-11-11
):P

Hi guys and gals! I finally decided to take the plunge and learn Linux.  Ubuntu seemed to be the most user friendly of the group, so here I am.  I'm completely brand new to terminal based commands, but I'm trying to use the terminal as much as I can when in the Ubuntu environment.  I must confess I had to have multiple web pages open to give me coding for all I've done so far, and even more confession, I'm not sure what 70% of the coding I did does lol (apt-get is nice).

One thing I can say is the operating system is blazing fast vs. windows 7.  I compared the time it took to download and install CPU-Z and RealTemp in windows to CPU-G and psensor (lol, I think).  It was a lot faster in Ubuntu.  I'm loving using the terminal.

Anywho, I'll most likely be asking very n00bish questions for a while.

---

### Post by deadflowr on 2013-11-11
> [COLOR=#000000]I'm not sure what 70% of the coding I did does lol (apt-get is nice)[/COLOR]

Firstly, welcome!

Secondly, tell us what codes/commands you ran, and people will be more then willing to help you understand what they are/do.

---

### Post by mike44njdevils on 2013-11-11
Here's the code I used to get and install cpu-g (cpu monitoring program, Linux' version of CPUID's CPU-Z):

```
sudo add-apt-repository ppa:cpug-devs/ppa
sudo apt-get update
sudo apt-get install cpu-g
```

I'm honestly not sure what "sudo" does...nor really what the first two lines do. I think I can figure out the third line :)

What does "apt-add-repository" actually do (yes I know I can google it)

---

### Post by deadflowr on 2013-11-11
> **mike44njdevils said:**
> Here's the code I used to get and install cpu-g (cpu monitoring program, Linux' version of CPUID's CPU-Z):

```
sudo add-apt-repository ppa:cpug-devs/ppa
sudo apt-get update
sudo apt-get install cpu-g
```

I'm honestly not sure what "sudo" does...nor really what the first two lines do. I think I can figure out the third line :)

What does "apt-add-repository" actually do (yes I know I can google it)

sudo is a command that gives the user root access.
In other words it allow non-root users the ability to manipulate the system.
Here's more
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ubuntu uses a packaging system called apt. It stands for advanced package tool.
The packages apt can get are inside what is known as a repository.
Ubuntu has a number of default repositories is can get packages from
Looky Here
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

However, some packages aren't available in the defaults, so you can simply add a third party repository.
That's where the add-apt-repository command comes in.

apt-get, as it would be assume, gets packages.
The update command updates the package list that the system can get.
If by chance after adding the apt repository, you skipped this step, the packages in the new repo would not show up.
The install command installs the packages you've selected to install.
You can learn a bunch of other stuff by simple running the command 'man apt-get'
in a terminal (q to quit)

Hope this helps, somewhat.

---

### Post by philinux on 2013-11-12
Moved to Ubuntu , Linux and OS chat. 
(Title amended)

---

### Post by oldos2er on 2013-11-12
There's some info explaining apt-get commands here: [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

And a more general terminal tutorial here: [http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)

You can use the *man* command to get help with commands, for example  ```
man apt-get
``` Some man pages can be rather heavy going for newbies (and oldbies too) so if you have further questions don't hesitate to ask.

---

### Post by Johan De Cauwer on 2013-11-12
There is one thing anyone starting linux and who wants to explore the terminal must know: the midnight commander.
```
sudo apt-get install mc
```
It's a usefull program based on the interface of the Norton Commander and it's invoked with mc

---

