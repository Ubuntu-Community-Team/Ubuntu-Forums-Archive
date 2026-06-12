---
title: "Restricted Driver Manager in Ubuntu 7.10 Server"
date: 2007-12-01
forum: Server Platforms
---

### Post by blk97tt on 2007-12-01
Hi.  I am running GNOME desktop on Ubuntu 7.10 Server.  I am trying to use Restricted Drivers Manager.  I get a message saying : 

"You need to install the package linux-restricted-modules-2.6.22-14-server
for this program to work"

I can't find this package anywhere.  How can I get this to work?

Thanks

---

### Post by phimurh on 2007-12-01
> **blk97tt said:**
> 
"You need to install the package linux-restricted-modules-2.6.22-14-server
for this program to work"

try this:

sudo apt-get install linux-restricted-modules-2.6.22-14-generic

if that does not work type:

apt-cache search linux-restricted

that will give you a list of like results if you find one you like type
sudo apt-get install *found program useing apt-cache*

---

### Post by blk97tt on 2007-12-01
> **phimurh said:**
> try this:

sudo apt-get install linux-restricted-modules-2.6.22-14-generic

if that does not work type:

apt-cache search linux-restricted

that will give you a list of like results if you find one you like type
sudo apt-get install *found program useing apt-cache*

Thanks for the quick reply.  I tried both suggestions and neither resolved the issue.  I still get the same error message.  Any other ideas?

Thanks

---

### Post by bmathis on 2007-12-02
did you enable all of the repositories in /etc/apt/sources.list ?

---

### Post by monahan1399 on 2007-12-24
How do you enable the repositories?

---

### Post by silviur on 2007-12-24
Systemm --> Administration --> Software sources, select main, universe, multiverse, etc., then do the commands in the posts above, and you should be ok :)

---

### Post by jimmydorsey on 2007-12-25
Same issue here.  I can't find linux-restricted-modules-2.6.22-14-server, nor can I get Restricted Driver Manager to start without that message.

I have reloaded all the restricted packages I can find.  I also reloaded all my repos.

No luck.  Did anyone ever get a solution to this?

thanks,

stephen.

AMD64 ubuntu-studio 7.10 (64 version)

---

### Post by lns on 2008-02-08
I'm also having this issue since I updated my kernel today. Can't find the '-server' restricted drivers package.

Using Gutsy i386.

---

### Post by 12jewels on 2008-02-17
Has anyone solved this problem? I also received this error, but only after installing vmware-server. now my sound and my video doesn't work.

---

### Post by steve_c on 2008-04-30
Does anyone know if this issue is resolved in 8.04 Server?

---

