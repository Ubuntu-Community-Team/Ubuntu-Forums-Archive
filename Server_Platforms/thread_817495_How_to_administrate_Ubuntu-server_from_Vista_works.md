---
title: "How to administrate Ubuntu-server from Vista workstatio"
date: 2008-06-03
forum: Server Platforms
---

### Post by volmark on 2008-06-03
I’m very novice in Linux environment and despite my experience with computer technology I have still naive questions about Linux. 
I have just installed Ubuntu-server with LAMP but cannot find out how to administrate it. 
For ex. I don’t know how to administrate Ubuntu-server standing remotely from Vista workstation??

---

### Post by tymewyse on 2008-06-03
Install Webmin ( [www.webmin.com](www.webmin.com) ) and go that route. Being that I have been migrating from Windows servers to Ubuntu, Webmin is very easy and has been VERY helpful.

Jeff

> **volmark said:**
> I&#8217;m very novice in Linux environment and despite my experience with computer technology I have still naive questions about Linux. 
I have just installed Ubuntu-server with LAMP but cannot find out how to administrate it. 
For ex. I don&#8217;t know how to administrate Ubuntu-server standing remotely from Vista workstation??

---

### Post by hyper_ch on 2008-06-04
normally you log into your linux server through SSH and do all the administration from the command line.

All the configuration stuff is stored in files and you do configuration by altering them.

In order to SSH into your box you need to:
(1) install ssh server
```

sudo apt-get install openssh-server

```

(2) Get a windows SSH client
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

(3) Run putty, enter the ip of the server and username/password of your user and log into it.

---

### Post by volmark on 2008-06-04
Thank you very much for the quick response

Now I can move my noisy host down to the basement and manage it from my room. 

Now I need some tools to administrate MySQL, PHP and Apache, something like phpMyAdmin control panel.

Besides that I nee to install reliable FTP server &#8230;

Any suggestions??

Thanks in advance

---

### Post by hyper_ch on 2008-06-04
```

sudo apt-get install phpmyadmin

```

What do you need a ftp server for?

---

### Post by volmark on 2008-06-04
I&#8217;ve just installed vsftpd but could not logon. I think it something with configuration. The anonymous access is ON. Additionally I couldn&#8217;t find the root directory for FTP. I&#8217;ve looked at vsftpd.conf but no references to FTP root in it. 
I need FTP server just as standard utility for the file transfer from the most popular FTP clients (FileZilla f. ex.)
It could be great to have separate FTP directory for each user.

---

### Post by hyper_ch on 2008-06-05
sftp/scp would not work?

---

### Post by gtdaqua on 2008-06-05
In any case, learn CLI. You will find this really more comfortable than any web-based management. But you've to get used to CLI to appreciate it though.

---

### Post by volmark on 2008-06-05
I’m not pretty comfortable with CLI but I would like to learn it. I need some guidelines, f. ex. how to effectively use docs and where I can find the commands divided by functionality groups instead of alphabetical lists. As a rule I’m searching for the command syntax because of my immediate needs and than after curiosity to the system. 
I really like your advice about Putty and its simplicity and reliability

---

### Post by hyper_ch on 2008-06-05
Here's a little cheat sheet with the most important stuff:

[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

and then learn bash here:

[http://www.linuxcommand.org](http://www.linuxcommand.org)

and if you want to know more about a command:
```

man COMMAND

```

as for file transfer I'd still think sftp/scp would be good :)

---

### Post by volmark on 2008-06-05
Thanks for the guidelines.
Could you please to name some advantages of sftp/scp in comparison with vsftpd?? It’s because I would like to minimize the set of tools that I’m going to use. I prefer to learn deeply one tool and use it effectively. 
Thank in advance for using your time …

---

### Post by hyper_ch on 2008-06-05
sftp/scp is ftp over a ssh connection so you only need openssh-server installed. However you need system accounts setup.

I restrict the access with mysecureshell (that's a little addon) and you just change the default login shell from bash to mysecureshell and have them restricted pretty much in their confinement.

It's actually quite simple ;)

---

### Post by sfreed on 2008-06-05
If you want a windowing environment, install the vnc server under ubuntu and install the client on your Vista machine.

I prefer the command line, but sometimes a GUI is handy.

--
steve.

---

### Post by volmark on 2008-06-05
There is no GUI (Gnome or KDE) environment on my installation. Can I manage the remote system with no GUI desktop and VNC on Windows client??

---

### Post by volmark on 2008-06-05
I could connect to the host with SSH FTP (SFTP) and it works fine. The OpenSSH was installed by default and I used FileZilla as a client.
What&#8217;s the reason to additionally install mysecureshell??

---

### Post by windependence on 2008-06-06
> **volmark said:**
> There is no GUI (Gnome or KDE) environment on my installation. Can I manage the remote system with no GUI desktop and VNC on Windows client??

You can manage the entire server without a GUI. You would need to install some kind of X server anyway to use VNC, and therefore I wouldn't recommend it. If you absolutely have to have some kind of visual interface you could run Webmin. It it was me, I would still get to Webmin by using an ssh tunnel into my remote host, and then access Webmin by going to [https://localhost:10000](https://localhost:10000), but then I am a bot paranoid about security.

It is certainly possible to do everything you need to do with the server from a simple ssh terminal. There are some things like WinSCP that make life a bit easier, but you really don't technically need them.


-Tim

---

### Post by hyper_ch on 2008-06-06
> **volmark said:**
> There is no GUI (Gnome or KDE) environment on my installation. Can I manage the remote system with no GUI desktop and VNC on Windows client??
A gui is not required to administrate a linux user... what do you want a graphica user interface for when all the configuration is done by editing config files?

> **volmark said:**
> What’s the reason to additionally install mysecureshell??
As SSH access requires a system user you want to limit what that user can do. E.g. you don't want the user to look around outside his home folder, you want that user in his own chrooted jail, ....

> **windependence said:**
> If you absolutely have to have some kind of visual interface you could run Webmin. It it was me, I would still get to Webmin by using an ssh tunnel into my remote host, and then access Webmin by going to [https://localhost:10000](https://localhost:10000), but then I am a bot paranoid about security.
Webmin is nice but I think it's also overrated... I used it back on my first server but meanwhile I see no reason for it anymore.


> **windependence said:**
> It is certainly possible to do everything you need to do with the server from a simple ssh terminal. There are some things like WinSCP that make life a bit easier, but you really don't technically need them.
The only thing, IMHO, that WinSCP makes easier it transfer lots of files (plus you can also run commands on the server from WinSCP)... but it is more a file management tool between different computers as an administrative interface.

---

### Post by osjak on 2008-06-06
volmark, I was in your shoes not too long ago - a somewhat novice trying to administer a server. Here are my thoughts:

1. Don't get used to the webmin, Plesk and other systems. They give you comfort of not having to learn, but greatly limit you in to what extent you control the system. Plus, it's just another piece of software on your server that is exposed to the world and can be compromised. Just try to learn that command line as you go and you'll be glad you did. Ubuntu is a great system to start with and has a very powerful and easy command line system for managing software. Installs, unistalls and upgrades are just a breeze with *apt*.

2. PuTTY - Windows SSH client, you've got the link from one of the posts above or you may use [this one]("http://portableapps.com/apps/internet/putty_portable") (I like portable versions). This is your best friend. You need to install the SSH server on your server to use it.

3. WinSCP - SSH client for transferring files back and forth, think of it as secure FTP client. I like using it to work with my website - transfer files, open several files at the same time for editing etc. [Portable version of it]("http://portableapps.com/apps/internet/winscp_portable"). It works over SSH, so you don't need to install anything else on your server, and no need to open any additional ports.

Those two tools above will allow you to do anything you want with your server.

If you are the only one working in your server, there's no need to chroot your user. But if you let other people use it over WinSCP or PuTTY, you will be safer with a chrooted user that those other people login under. That's something I never had to do, so I cannot advise you on setting that up.

---

### Post by rustic on 2008-06-06
You can also use FileZilla (filezilla-project.org/) for your file transfer (read:  ftp/sftp) needs.

I find this tool to be better than WinSCP for the simple sake of speed.  This may be a "what flavor of Kool-Aid do you prefer" statement, and if so, I like FileZilla.

With that said, PuTTy + FileZilla = powerful, complete and flexible server control.

---

### Post by volmark on 2008-06-06
Thanks friends
I’ve red some manuals and found that command promt gives the unified way to work with the system. By the way it is great manual on Ubuntu site and I can copy-and-paste the commands directly to Putty. 
Now I’ve removed all the peripherals and cables(display, keyboard and mouse) and manage the system remotely. I like this way. 
You are absolutely right, that PuTTy + FileZilla are complete set of the tools that covers all the needs. 
I still missing kind of structured manuals and tutorials but thanks God we have Google and forums like that.
I’m definitely coming back with other questions :o)
Thanks a lot

---

