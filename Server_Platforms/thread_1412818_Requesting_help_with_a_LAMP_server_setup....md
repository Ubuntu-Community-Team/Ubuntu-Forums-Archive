---
title: "Requesting help with a LAMP server setup..."
date: 2010-02-21
forum: Server Platforms
---

### Post by Cheewha Palen on 2010-02-21
Hello all,

I am running 9.10 server edition with the lamp setup. I will be using this server to host a simulator from the open sim project ([http://opensimulator.org](http://opensimulator.org)). 

I have a few questions please and would appreciate any help.

1) I need to configure my server to run a static connection instead of dchp (dhcp? Dynamic, lol). This is so that I can connect a viewing client on another machine to access the server and view and interact with the simulator. I need advice please on how to do this.

2) I am hoping someone can point me to a "map" of the file system for my server package. Since server operation is "blind" and I am new to this (my first server) I am having trouble visualizing "where" my stuff is and lack understanding as to what exactly is offered in the package. a road map of sorts would be greatly appreciated for navigation.

I currently have the simulator up and running and can "see" it operating, and I know how to access this file to turn it on and off, etc. I need to set up a mysql data base for storage related to items contained within the simulator, etc. I do not know "where" the mysql files are or how to get to them.

3) When I list the contents of a folder using "ls" I get a very long list of content and can only see the tail end of said list. Is there a command to break up the list such as with windows I remember adding a -p or a -w to the list commands to page through the listing. This would be helpful.

4) I need to figure out how to add repositories and access them. 

I have read the installation guide for server edition which helped me get up and running though these few items mentioned are stumping me at the moment. I am very new to this and receptive to help, criticism, etc. and hope you are patient with me in this matter. 

Thank you

---

### Post by Barriehie on 2010-02-21
> **Cheewha Palen said:**
> Hello all,

I am running 9.10 server edition with the lamp setup. I will be using this server to host a simulator from the open sim project ([http://opensimulator.org](http://opensimulator.org)). 

I have a few questions please and would appreciate any help.

1) I need to configure my server to run a static connection instead of dchp (dhcp? Dynamic, lol). This is so that I can connect a viewing client on another machine to access the server and view and interact with the simulator. I need advice please on how to do this.
You can get a free 'redirect' via dyndns or no-ip.com.  I've used both and they work well.  Basically you download their app. that will update their server with your IP and any requests for *yourserver.whatever* will be directed to your machine.

> **Cheewha Palen said:**
> 2) I am hoping someone can point me to a "map" of the file system for my server package. Since server operation is "blind" and I am new to this (my first server) I am having trouble visualizing "where" my stuff is and lack understanding as to what exactly is offered in the package. a road map of sorts would be greatly appreciated for navigation.
Can't help you here...

> **Cheewha Palen said:**
> I currently have the simulator up and running and can "see" it operating, and I know how to access this file to turn it on and off, etc. I need to set up a mysql data base for storage related to items contained within the simulator, etc. I do not know "where" the mysql files are or how to get to them.
My experience with SQL is via webpages, it can be done through the CLI but you've got a bit of reading ahead of you.  Some docs can be found [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

> **Cheewha Palen said:**
> 3) When I list the contents of a folder using "ls" I get a very long list of content and can only see the tail end of said list. Is there a command to break up the list such as with windows I remember adding a -p or a -w to the list commands to page through the listing. This would be helpful.
pipe the command into more:
```

ls | more
```

> **Cheewha Palen said:**
> 4) I need to figure out how to add repositories and access them.
Repo's are listed in /etc/apt/sources.lst 

> **Cheewha Palen said:**
> I have read the installation guide for server edition which helped me get up and running though these few items mentioned are stumping me at the moment. I am very new to this and receptive to help, criticism, etc. and hope you are patient with me in this matter.

Thank you

HTH

---

### Post by cariboo on 2010-02-21
> 1) I need to configure my server to run a static connection instead of dchp (dhcp? Dynamic, lol). This is so that I can connect a viewing client on another machine to access the server and view and interact with the simulator. I need advice please on how to do this.

I just disable the dhcp3 client (uninstall it) then setup a static ip address using /etc/network/interfaces, this is what mine looks like:

```
cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address	  192.168.1.250
	netmask	  255.255.255.0
	broadcast 192.168.1.254
	gateway	  192.168.1.1
```

> 2) I am hoping someone can point me to a "map" of the file system for my server package. Since server operation is "blind" and I am new to this (my first server) I am having trouble visualizing "where" my stuff is and lack understanding as to what exactly is offered in the package. a road map of sorts would be greatly appreciated for navigation.

The server file-system layout is exactly the same as the desktop file-system layout, the files are located in the same places.

> I currently have the simulator up and running and can "see" it operating, and I know how to access this file to turn it on and off, etc. I need to set up a mysql data base for storage related to items contained within the simulator, etc. I do not know "where" the mysql files are or how to get to them.

The best way if you aren't familiar with working with mysql from the command line is to install phpmyadmin, and do all your database admining from a web browser.

> 3) When I list the contents of a folder using "ls" I get a very long list of content and can only see the tail end of said list. Is there a command to break up the list such as with windows I remember adding a -p or a -w to the list commands to page through the listing. This would be helpful.

Use the command:

```
ls -l | less
```

> 4) I need to figure out how to add repositories and access them.

You can edit the /etc/apt/sources.list using nano:

```
sudo nano /etc/apt/sources.list
```

All of the above assume that you have at least the basic knowledge of Linux system administration, [This]("http://www.ubuntupocketguide.com/index_main.html") may help if you don't.

---

### Post by Cheewha Palen on 2010-02-21
Thank you everyone for your replies. I appreciate your help!

---

