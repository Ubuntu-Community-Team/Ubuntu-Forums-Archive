---
title: "add-apt-repository = bad command"
date: 2011-01-21
forum: Server Platforms
---

### Post by 2boats on 2011-01-21
Simple question and hopefully a simple answer.

I'm trying to install gnumed on a server (Maverick 10.10 - clean install as open SSH server). 

 Step one is-  copy this command: sudo apt-get install python-software-properties

I get "E: Unable to loacte package python-softwear-properties

What I'm trying to load is -  sudo add-apt-repository ppa:gnumed/ppa

and of course I get sudo: add-apt-repository: command not found.

How do I fix this?    

Thanks in advance!

---

### Post by endotherm on 2011-01-21
well, I can assure you, add-apt-repository is a valid command. be sure to check your spelling.
you are using ubuntu desktop edition, right?
```

Lucid:~$ add-apt-repository -h
Usage: add-apt-repository sourceline

add-apt-repository is a script for adding apt sources.list entries. 
It can be used to add any repository and also provides a shorthand 
synatax for Launchpad PPA (Personal Package Archive) repositories via
ppa:user/repository

Options:
  -h, --help  show this help message and exit

```

---

### Post by 2boats on 2011-01-21
I'm using the server edition NOT the desk top.

I just typed in "add-apt-repository - h"  
response -  The program 'add-apt-repository' is currently not installed. you can install it by typing:
sudo apt-get install python-softwear-properties.
I did that and the read out is:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package python-softwear-properties

All spelling has been checked and double checked prio to postin - I also have searched forums and googled to try to solve this before asking for help.  uUsually I find a solution but this time I seem to be stumped!

---

### Post by 2boats on 2011-01-21
Really, the spelling is right!

---

### Post by drs305 on 2011-01-21
This is the second post in which "software" is misspelled. Are you typing "software" or "softwear" when trying to add the package? It doesn't apply directly to the ppa issue, but please check your spelling in all commands and cut/paste if necessary.

---

### Post by brookie on 2011-01-21
> **2boats said:**
> I'm using the server edition NOT the desk top.

I just typed in "add-apt-repository - h"  
response -  The program 'add-apt-repository' is currently not installed. you can install it by typing:
sudo apt-get install python-**softwear**-properties.
I did that and the read out is:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package python-**softwear**-properties

All spelling has been checked and double checked prio to postin - I also have searched forums and googled to try to solve this before asking for help.  uUsually I find a solution but this time I seem to be stumped!

could be spelling? python-**software**-properties, not python-**softwear**-properties

oops someone already posted about sp?

---

### Post by endotherm on 2011-01-21
> **2boats said:**
> Really, the spelling is right!
software != softwear

[http://packages.ubuntu.com/search?keywords=python-software-properties](http://packages.ubuntu.com/search?keywords=python-software-properties)
[http://packages.ubuntu.com/en/lucid/python-software-properties](http://packages.ubuntu.com/en/lucid/python-software-properties)

the package is part of Gnome, so since you don;t have a desktop installed with server edition, the package is not there by default. you may be able to install it individually, but it may depend on more gnome packages, or even refer to the entire ubuntu-desktop metapackage.

---

### Post by 2boats on 2011-01-21
Oops, that would be too easy -   on the terminal I have typed softwear.  (I'm in the foot business and  work with footwear)  
Thanks for the correction - I can't believe I missed that.   

I knew the answer had to be simple...  

I really appreciate you time.  
Thanks again!

---

### Post by endotherm on 2011-01-21
> **2boats said:**
> Oops, that would be too easy -   on the terminal I have typed softwear.  (I'm in the foot business and  work with footwear)  
Thanks for the correction - I can't believe I missed that.   

I knew the answer had to be simple...  

I really appreciate you time.  
Thanks again!
happens to the best of us sir. glad it worked out for you, and stop on back by anytime.

---

### Post by Chaosekie on 2011-10-20
Hi I have this same error though I don't believe mine is spelling related, I am running 10.10 Maverick I have added a screenshot maybe my spelling is up to $h....

Thanks

---

### Post by drs305 on 2011-10-20
> **Chaosekie said:**
> Hi I have this same error though I don't believe mine is spelling related, I am running 10.10 Maverick I have added a screenshot maybe my spelling is up to $h....

Thanks

I just checked my copy of Maverick and the *python-software-properties* is available in the "main" repository. My server is currently in the US: gtlib .... 

Make sure the main server is enabled (software-properties-gtk run as root) and you might try changing your server and running "apt-get update" to make sure you computer is properly connecting to the server.

---

### Post by Chaosekie on 2011-10-20
Hi,

Did you mean install software-properties-gtk?

The attachment shows what I did.

---

### Post by Chaosekie on 2011-10-20
hell knows why but after running "apt-get update" I can install the program that I wanted to add another repository for, so I don't really need to add a new repository anymore.

PS. the program I tried to install was transmission

---

### Post by Kurtosis on 2012-03-18
Just to clarify, in case anyone else stumbles on this thread looking for a solution to this problem:

Ubuntu Server does **not** include /usr/bin/apt-add-repository or /usr/bin/add-apt-repository by default.  Those commands are in the package [python-software-properties]("http://packages.ubuntu.com/oneiric/all/python-software-properties/filelist"), which must be manually installed.

> sudo apt-get install python-software-properties

---

