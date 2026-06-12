---
title: "Ubuntu Server with optional GUI"
date: 2008-07-27
forum: Server Platforms
---

### Post by amlife on 2008-07-27
Hello

I'm trying to install GUI on my server,however I don't want to have it running permanently all the time. as I would like to start it when I need and exit back to the command line when I need :)

is it possible to have it setup in this way ?

please provide me with the required commands :KS


is it possible to install the GUI with the minimal software packages installed?

Thanks tones :lolflag:

---

### Post by halitech on 2008-07-27
this will install the desktops

```
sudo apt-get install ubuntu-desktop
```

change ubuntu-desktop to kubuntu-desktop or xubuntu-desktop for your choice

I believe it is possible, just not sure at the moment how to do it

---

### Post by Joeb454 on 2008-07-27
The above will install all packages that come on a Default K/X/Ubuntu install, so unless you want that - I'd advise against it.

You would want to run something like ```
sudo apt-get install xserver-xorg xorg
``` then install a lightweight DE (lets say XFCE4) by running ```
sudo apt-get install xfce4
```

Anyway, I can't be much help, I don't use a GUI on my server. So I moved it to the Server sub-forum

---

### Post by hrod beraht on 2008-07-27
I don't use a GUI on my server either, which makes me wonder, what is it you are trying to accomplish with the GUI on your server setup?
There may be an easier way than installing a whole GUI/desktop environment, as a server doesn't really need constant interaction via a GUI.

Are you just wanting to use the GUI for something like transferring web pages to your Apache web server setup? If so, it may be easier to simply do a *Places --> Connect to Server (via SSH)* command on your desktop computer, which will give you a GUI window on your desktop computer into which you can drag and drop files over to your server computer without actually needing a full-blown GUI on your server.

Bob

---

### Post by steveneddy on 2008-07-27
> **hrod beraht said:**
> I don't use a GUI on my server either, which makes me wonder, what is it you are trying to accomplish with the GUI on your server setup?
There may be an easier way than installing a whole GUI/desktop environment, as a server, once up and running, doesn't really need constant interaction via a GUI.

Are you just wanting to use the GUI for something like transferring web pages to your Apache web server setup? If so, it may be easier to simply do a *Places --> Connect to Server* command on your desktop computer, which will give you a GUI window on your desktop computer into which you can drag and drop files over to your server computer without actually needing a full-blown GUI on your server.

Bob

That is actually a good idea.

But, if you have to run a GUI, then install

```

sudo apt-get install ubuntu-desktop

```

and then starting & stopping the GUI by

```
sudo /etc/init.d/gdm stop
```

or

```
sudo /etc/init.d/gdm start
```

---

### Post by wgregori on 2008-07-27
Bob,

I'm looking for a GUI on my server to help administer my web server, FTP server and DNS.  Something that makes it easier to create an account, give access rights, etc.

Thanks,
Wayne


> **hrod beraht said:**
> I don't use a GUI on my server either, which makes me wonder, what is it you are trying to accomplish with the GUI on your server setup?
There may be an easier way than installing a whole GUI/desktop environment, as a server doesn't really need constant interaction via a GUI.

Are you just wanting to use the GUI for something like transferring web pages to your Apache web server setup? If so, it may be easier to simply do a *Places --> Connect to Server (via SSH)* command on your desktop computer, which will give you a GUI window on your desktop computer into which you can drag and drop files over to your server computer without actually needing a full-blown GUI on your server.

Bob

---

### Post by chris.zeman on 2008-07-27
Check out Webmin ([http://webmin.com](http://webmin.com)). It is also available in the repositories.

Chris

---

### Post by amlife on 2008-07-27
Hello everyone 

I would like to thank all of you who took the time to answer my question. 

I love ubuntu server, I have no problem running it with no GUI, it is actually the way I want it. but some times I need the GUI to run some GUI applications like VMware, as well the most important thing is to have access to the packet manager where I can download additional packages like VMware Server edition without the need to go and install it manually. 

Thanks

---

### Post by hrod beraht on 2008-07-27
> **amlife said:**
> ...I need the GUI...to have access to the packet manager...

The Synaptic Package Manager is nice, that's true. But you can also do that kind of thing from the command line. For example, to install something:
```
sudo apt-get install **program_name**
```
For a list of apt-get commands, type:
```
apt-get --help
```
And if you want to search for a particular program, you can use:
```
apt-cache search **search_string**
```

Bob

---

### Post by chris.zeman on 2008-07-27
I'm not positive, but I THINK Webmin has a package manager module as well if you'd rather not install packages from the command line.

Chris

---

### Post by lifeheart on 2008-07-27
Thanks very much I will try that Bob !

---

### Post by cariboo on 2008-07-27
Aptitude has an ncurses interface to invoke it type:

```
aptitude -v
```

It's not quite a gui, but it has all the functions that synaptic has.

Jim

---

### Post by Ocelaris on 2008-09-16
> **hrod beraht said:**
> The Synaptic Package Manager is nice, that's true. But you can also do that kind of thing from the command line. 
And if you want to search for a particular program, you can use:
```
apt-cache search **search_string**
```

Bob

BINGO that's what I needed to know. Thanks!

---

