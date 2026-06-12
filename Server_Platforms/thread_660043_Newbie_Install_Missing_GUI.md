---
title: "Newbie Install Missing GUI"
date: 2008-01-06
forum: Server Platforms
---

### Post by paiwacket on 2008-01-06
Dell Dimension 4600 512MB/160GB

I am new to Ubuntu Server, & am excited to try it. Downloaded & installed successfully Server 7.10. Proceeded thru install process. Installed, in addition to core OS, LAMP, Samba & Print Server.

When I restart, tho, there is no GUI, just command line; I can login alright w/ the uid created during install. Looked thru online docs & could find nothing relating to this. I thought the GUI was installed by default.

What am I missing, & how can I solve this?

Thanx,  -Barry

---

### Post by luisromangz on 2008-01-06
Ubuntu server doens't install any GUI by default, just as the desktop version doesn't install any server server.

You can solve it by installing the ubuntu-desktop or kubuntu-desktop packages, for example.

---

### Post by paiwacket on 2008-01-06
Is there possibly a GUI that will install on the server edition?

I am really not that CLI oriented.

-Barry

---

### Post by paiwacket on 2008-01-06
Addl Googling has revealed the following:

  sudo aptitude install x-window-system-core gnome

But in running the code above results in a prompt stating that "gnome-dbg" is not installed.  Do I wish to leave it unresolved?

Tried doing that, but attempts to start gnone

  /etc/init.d/gdm start

resulted in  "could not find directory."

Am I getting closer?

---

### Post by johnwillis on 2008-01-06
Hiya!

The best thing you can do is log into the system using your username and password.

Then from a command line (if you are in the basic GUI) or if not from the CLI run the following command:

"sudo apt-get install ubuntu-desktop"

Running this command will install all the needed files for a GNOME desktop. It will resolved any problems it finds with your system.

It is worth noting that if your are just tinkering with Servers it can all be done from the Desktop CD too. :)

Once everything is downloaded and install you'll need to reboot the server for your changes to take effect. (Press CTRL-ALT-BACKSPACE)

If for what ever reason you still have no GUI then try logging in and issuing the command "startx".

If you still have issues. Please post back :)

John

---

### Post by HermanAB on 2008-01-06
People always get confused by the desktop versus server thing.

Linux is Linux is Linux.  There is no inherent difference between a desktop and server version of Linux.  The differences are all superficial.

A server is meant for use in a dark, dank data centre where the machines don't have screens and keyboards.  Machines are administered remotely using SSH.  If this is what you got, then you should install a server version of Linux.

If you want a machine with a GUI desktop then you have to install a desktop version of Linux obviously.

If you have a hybrid situation, where you wish to administer your server using a GUI, then install a lightweight desktop version, such as Xubuntu.  

If the hybrid machine usually just sits in a dark corner doing something unspeakable, then you could switch it to run level 3 (no X) and when you wish to administer something, switch to run level 5 (X) to get a GUI desktop.  However, the Linux memory manager is very good and will swap stuff out that are not used if the memory is needed, so you could just as well leave a server in run level 5.

Cheers,

Herman

---

### Post by paiwacket on 2008-01-07
Thx for all the help. 

  sudo apt-get install ubuntu-desktop  got me to a GUI desktop. 

However, even tho I specified installing LAMP. Print Server; & Samba during install, none of these seems to be accessible thru the GUI. Even if I perorm a search thru the Add/Remove feature. Or am misunderstanding the Gesstallt of the add/remove feature?

thx again,  -barry

---

### Post by paiwacket on 2008-01-07
Alright, I figured out how use the CLI to install LAMP, on the presumption that they were not installed at the initial install. HOWEVER, well, what I did is below.

---------------------------------
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
[sudo] password for popeye:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
php5-mysql is already the newest version.
libapache2-mod-php5 is already the newest version.
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
---------------------------------
So, the software is already installed? How do I actually _access_ them? Tjhe search thru Add/Remove showed nothing; neither did control-F. 

thx again, -Barry

---

### Post by MJN on 2008-01-07
> **HermanAB said:**
> People always get confused by the desktop versus server thing.
 
Linux is Linux is Linux. There is no inherent difference between a desktop and server version of Linux. The differences are all superficial.
 
I would disagree that the differences are 'all superficial' - the default kernel option differences can be significant.
 
I do concede however that at the level being discussed here in this thread they are of less(er) importance.
 
Mathew

---

### Post by johnwillis on 2008-01-07
To access your server config files you need to open the conf files with root permission,

At a CLI type "sudo gedit /etc/apache/httpd.conf"

This opens the apache config file

At the CLI type "sudo gedit /etc/samba/smb.conf"

This opens the Samba config.

There are other ways to do it though.

To access the samba options look under "System --> Administrator --> File Sharing/Samba"

To see if the servers are actually installed look for an option under your preferences/administration called "Services" down that list at the bottom you should see "Web Server" make sure it's ticked.

And your services should also show the "File Sharing (Samba)"

Make sure they are on the list if not you can install them using the following:

sudo apt-get install apache2 samba-common samba-client

This will install everything you should need.

Let me know how it goes and good luck!

---

### Post by elvinatom on 2008-01-07
Please forgive me for finding that amusing, not that i know much more than you but i guess that little extra makes a big difference; here's my opinion:
you need to do some major learning if you wanna set up a linux server, because it just doesn't work as "smooth" as in windows (like klick here, fill in the share there, enable, -would you like me to have dns installed for you?- yes, enable: done!).  in linux the server apps need to be installed (which is nothing) and then configured (which can be nasty).  linux server apps are generally all cli maintained; you can however use graphical tool that get this task done for you, but the problem is that you need to know how your services work (samba, cups, bind9 ...) or else you look at the tools of your choice and start guessing what all the boxes and tabs mean.  I've been where you are half a year ago and i tried it the graphical way.  now i wouldn't install a gui on my server if you paid me ;-).  It's not as bad as it seems.  Start with samba (windows file sharing), that's fairly simple or follow some complete server howtos.  Here are a couple to get you started:

ubuntu's guide (might need some patience)
[https://help.ubuntu.com/7.10/server/C/]("https://help.ubuntu.com/7.10/server/C/")

Serving Your Home Network on a Silver Platter with Ubuntu (it's for 7.04 but works fine with 7.10)
[http://www.tldp.org/LDP/LGNET/141/lazar.html]("http://www.tldp.org/LDP/LGNET/141/lazar.html")

There are many guides and many different methods, you might wanna google for sonethinf that works for you - for me the silver platter worked quite well, but judge it yourself.

---

### Post by paiwacket on 2008-01-09
My first priority is to configure Apache. I was able to bring up the file "sudo gedit /etc/apache/httpd.conf" but the file seems to be blank.

Is this correct? I had expected some default configuration. Is there no GUI available for these  items?

Thx for the continued help.  -Barry

---

### Post by MJN on 2008-01-09
Apache's main config file (on Debian-based distros, of which Ubuntu is one) is /etc/apache2/apache2.conf. The config is further refined, on a site-by-site basis, in /etc/apache2/sites-available/* and /etc/apache2/mods-available/* (and other places believe it or not). The reason it's no longer in a single file, i.e. it's now 'modularised', is because Apache config can grow and grow and so it makes sense to split it down into more function-specific containers (don't worry though, most of it you won't touch).
 
Thinking back to when I first started my advice to you is not to dive straight in - read around, get confused, ask a few questions etc, as there can potentially be a lot to take in - and it's usually difficult as a beginner to work out what aspects are the most important to get you up and running. This is further compounded when those of us who just happen to be further down the path than you forget how bewildering things can be.
 
There are GUI-based tools to help configure Apache (e.g. Webmin) but I don't like them - learn things the 'hard way' through knowledge and experimentation and I guarantee you will be end up with a far better understanding of how it all works (and hence how to fix it when it breaks). You will learn more by your mistakes than immediate successes.
 
I wish I could refer you to some specific HowTo's and guides etc but I'm way out of the loop on that side of things - hopefully someone else might be able to recommend based in similar recent experience.
 
Good luck, and don't give up!
 
Mathew

---

