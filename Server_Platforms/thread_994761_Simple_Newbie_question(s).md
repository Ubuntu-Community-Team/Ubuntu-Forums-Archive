---
title: "Simple Newbie question(s)"
date: 2008-11-27
forum: Server Platforms
---

### Post by eddiela on 2008-11-27
Hi everyone,

I'm brand new to Ubuntu, played with Linux a few years ago, a little Unix experience, tons of Windows experience.  Here's what I want to do:  I have a old AMD Athlon 1.2 GHz, 1 GB or RAM, tons of hard drive space.  This thing is screaming home server!  I want to build a VERY simple and stable file and print server for my Windows desktops.  I would like to run this thing headless and administer it from one of Windows desktops.

Due to the lack of horsepower, I was thinking I could run Ubuntu Server 8.10 with the GUI off to save CPU cycles.  Am I correct in assuming that I can run with the GUI off and only turn it on when I need to administer it remotely? (not a huge fan of the CLI, but I realize that I will have to use it at least sometimes)

If that is possible, what do I need on my Windows desktop to administer the Ubuntu server?

Finally, am I on the right track, can Ubuntu server run efficiently on my dinosaur or do I need to look into something like FreeNAS?

---

### Post by obg123 on 2008-11-27
I think you are definately on the right track! Personally, I prefer administrating the Ubuntu Server through a plain ssh client. In the Windows world I can only recommend putty [http://www.putty.org](http://www.putty.org). To transfer files (at least before you get Samba up and running) use [http://www.winscp.org](http://www.winscp.org). If you still need to use X to administer your server, or run CS-apps like OpenOffice or similar, I'd recommend Cygwin from [http://www.cygwin.com](http://www.cygwin.com). Everything is free.

---

### Post by eddiela on 2008-11-27
> **obg123 said:**
> I think you are definately on the right track! Personally, I prefer administrating the Ubuntu Server through a plain ssh client. In the Windows world I can only recommend putty [http://www.putty.org](http://www.putty.org). To transfer files (at least before you get Samba up and running) use [http://www.winscp.org](http://www.winscp.org). If you still need to use X to administer your server, or run CS-apps like OpenOffice or similar, I'd recommend Cygwin from [http://www.cygwin.com](http://www.cygwin.com). Everything is free.

Thanks obg123!  So you think my old 1.2 GHz box is strong enough to do what I want to do?

---

### Post by m_l17 on 2008-11-27
I think it will serve for your purpose. I would install and give it a try it won't hurt and you will learn a thing or two ;) 
And I would administer through ssh like obg123 mentioned.

---

### Post by eddiela on 2008-11-27
> **m_l17 said:**
> I think it will serve for your purpose. I would install and give it a try it won't hurt and you will learn a thing or two ;) 
And I would administer through ssh like obg123 mentioned.

Thanks m_l17,

Ok, I am about to show my lack of knowledge here...  Am I correct when I assume that using SSH will only give me access to the Command Line, or can I fire up the GUI with it?

Sorry for my ignorance/lack of experience! :sad:

Thanks again for all the help!

---

### Post by cariboo on 2008-11-27
Ssh will only allow you to administer from the command line, but if you use X forwarding you can run gui apps that are installed on your server on you desktop computer. Log in to your server like this:

```
ssh -X user@server
```

Then for instance if you wan to run synaptic to install a program, at the prompt on your server type:

```
sudo synaptic
```

Synaptic will open on your desktop and you can add or remove programs from there.

I use the above on my server to use brassero to backup files, as I'm to lazy to do it from the command line. :)

Jim

---

### Post by eddiela on 2008-11-27
> **cariboo907 said:**
> Ssh will only allow you to administer from the command line, but if you use X forwarding you can run gui apps that are installed on your server on you desktop computer. Log in to your server like this:

```
ssh -X user@server
```

Then for instance if you wan to run synaptic to install a program, at the prompt on your server type:

```
sudo synaptic
```

Synaptic will open on your desktop and you can add or remove programs from there.

I use the above on my server to use brassero to backup files, as I'm to lazy to do it from the command line. :)

Jim

"as I'm to lazy to do it from the command line." Finally! I'm not the only one! :biggrin:

Thanks Jim.  I have just finished downloading 8.10 Server, looks like I know what I will be doing this weekend!

Thanks again to everyone here on the forum.  It's people like you that make migration to Linux possible in my opinion.  I really appreciate your help and advice!

---

### Post by outofnicks on 2008-11-28
Your machine is plenty powerful enough to run a full GUI of any distro so you have no worries there. I have Kubuntu Feisty running on an old P3 600 mhz Dell laptop with only 256 mb of RAM and it runs OK.

---

### Post by obg123 on 2008-12-01
> **cariboo907 said:**
> Ssh will only allow you to administer from the command line, but if you use X forwarding you can run gui apps that are installed on your server on you desktop computer. Log in to your server like this:

```
ssh -X user@server
```

Then for instance if you wan to run synaptic to install a program, at the prompt on your server type:

```
sudo synaptic
```

Synaptic will open on your desktop and you can add or remove programs from there.

I use the above on my server to use brassero to backup files, as I'm to lazy to do it from the command line. :)

Jim

First of all, I would use ssh -Y for a more secure connection. Second, as he wants to do this from Windows, he needs an X-server to handle the GUI stuff. There is one bundled in Cygwin, mentioned in my first post (above).

---

### Post by Iowan on 2008-12-01
> **eddiela said:**
> Due to the lack of horsepower, I was thinking I could run Ubuntu Server 8.10 with the GUI off to save CPU cycles.  Am I correct in assuming that I can run with the GUI off and only turn it on when I need to administer it remotely? (not a huge fan of the CLI, but I realize that I will have to use it at least sometimes)

Probably a li'l late, but...
You should realize (or have discovered after installation), the basic server installation comes without GUI.  One can be added afterwards.  As mentioned, your machine should have PLENTY of horsepower (none of my machines is as powerful as your "dinosaur".)

---

### Post by cariboo on 2008-12-01
This is not really on topic, but I always cringe a little bit when someone calls a computer that is less than five years old a dinosaur. There should be a banner somewhere on this forum stating that Linux will bring your old computers back to life. :)

Jim

---

