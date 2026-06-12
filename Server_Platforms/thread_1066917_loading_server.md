---
title: "loading server"
date: 2009-02-11
forum: Server Platforms
---

### Post by wordmaster on 2009-02-11
Hello,

I have my new server up and running and am ready to start experimenting. I have it hooked to my current network, but so far have not been able to connect it to my current server.

The current server is running Netware 3.11 and the workstations are running windoze 98se and DOS 6.2. 

As I am not yet familiar with the commands and the command structure, I am running a GUI on the server. I know that is a controversial subject, but as a newbie it is helpful in getting started. I expect to use the command line more and more as I go along. 

I worked with command lines for years before windoze came along, but not with unix or linux command lines. 

My goal, once I understand this thing better is to replace my present server with the new Ubuntu server.

Will this connect to the Netware 3.11? If so, how?

I have a DOS program that I need to be able to access and run and I have a windows accounting program I need to be able to access and run.

Any help you can give on how to get these programs onto the Ubuntu server and how to access them and run them from the 98se and DOS workstations would be greatly appreciated.

---

### Post by unixeducation on 2009-02-11
As far as accessing files from your Ubuntu server via Windows clients, you'll want to install and configure Samba. You may want to refer to this thread for information on connecting with older clients: [http://ubuntuforums.org/showthread.php?t=815382](http://ubuntuforums.org/showthread.php?t=815382)

If your Netware server is new enough, you can connect to file shares on it using the smbmount utility at the command line. You'll need to be sure you have the package "smbfs" installed to use it; a simple "sudo apt-get install smbfs" will satisfy this requirement. Then you can "man smbmount" to get the right command syntax for your needs.

I hope this helps!

---

