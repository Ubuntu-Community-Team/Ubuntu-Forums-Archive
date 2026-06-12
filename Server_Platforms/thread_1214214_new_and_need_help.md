---
title: "new and need help"
date: 2009-07-15
forum: Server Platforms
---

### Post by TheShabz on 2009-07-15
Hi everyone, aspiring DBA and system architect here.

So I've decided to dive into the database world and have a few questions. Currently I have a laptop running Ubuntu 8.1 desktop. I have a few questions.

1. can i keep the desktop environment and still have a LAMP stack running?
2. what books would you recommend for Apache/MySQL/PHP? 
3. any tips or caveats? 

thank you in advance.

---

### Post by BkkBonanza on 2009-07-15
Yes, you can. Just use Synaptic to install the programs you need.
There are so many tutorials on the web for these topics that I'd say a book isn't really needed. If you like to spend money and have another book on your shelf then go ahead but truly everything is available via google.

On a side note. If you want to learn how to manage a server locally in prep for managing one for real in a data center then I'd suggest installing VirtualBox and then via that installing the Ubuntu server package into a virtual machine. Then everything you do to manage your VM is just like if it was located across the country in a data center. It becomes a distinct machine running inside your machine and the same methods/techniques are used as if it were a standalone server with no GUI.

---

### Post by TheShabz on 2009-07-15
thanks.

what does synaptic provide besides a gui replacement for the command line apt-get?

also, getting books is just a personal habit of mine. i enjoy having the information in print.

---

### Post by BkkBonanza on 2009-07-15
As far as I know - nothing. It's just an easy interface you have if you are using the desktop. On a server via SSH you would use apt-get.

---

### Post by cariboo on 2009-07-16
Synaptic also provides a description of the packages selected, as well as tools to repair broken packages and a history file, so you can go back and look at what you have installed, even if you have installed packages on the command line. It also has a filter that allows you to mark packages by task. It can tell you what dependencies are needed by the packages to be installed. I think synaptic is a wonderful tool.

---

### Post by kingnerd on 2009-07-16
> **cariboo907 said:**
> Synaptic also provides a description of the packages selected, as well as tools to repair broken packages and a history file, so you can go back and look at what you have installed, even if you have installed packages on the command line. It also has a filter that allows you to mark packages by task. It can tell you what dependencies are needed by the packages to be installed. I think synaptic is a wonderful tool.

Most of those things can also be done on the command line.  apt-cache show comes to mind for descriptions and dependencies.

---

