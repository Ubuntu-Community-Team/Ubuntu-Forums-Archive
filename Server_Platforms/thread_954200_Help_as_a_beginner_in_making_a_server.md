---
title: "Help as a beginner in making a server"
date: 2008-10-20
forum: Server Platforms
---

### Post by crazydiver on 2008-10-20
Hello,

   It seems that I don't quite understand a few things with making a server. I am quite excited for all the learning opportunities involved for the main goal of making a web server to host my websites, but I do have problems and some doubts that exist. 


First, during the installation I am asked a host name... I really have no idea? Can I make one up or is there a set name to put? I put something in and it seemed to run with with no hassle but then again just to make sure...

Second, at the part where it asks for a proxy, do I need to have a proxy, especially if I want to build a webserver?

Third,  for software, I obviously would like to have LAMP... however, is there any other software that one would recommend i.e. DNS.  I believe that DNS is used for connecting a url to a website??? is that correct? What's an open SSH? After googling the information I get tells me that open ssh is needed for accessing from different computers... guess I need it. Is it?

Fourth, after reasonably installing the server to some extent, I up use sudo to update and upgrade the server... After... what do I do? How do I access the server via a remote computer and how do I upload website files to it. I know some stuff about FTP but how do I set up a control panel for hosting and etc...

I apologize for the many questions but these are just some questions and problems that I have come across.

All help is always appreciated and thank you for taking the time to read this. 

:popcorn::)

---

### Post by cariboo on 2008-10-20
First have a look here:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

It is a step by step walk through of installing a server.

As for your other questions, you don't need a dns server on a small network, dnsmasq or editing your /etc/hosts file is a lot easier. You don't need and FTP server as you can do everything with ssh, sftp and scp that you can running and FTP server. SSH is much more secure than ftp also. To activate ssh, install openssh-server:

```
sudo apt-get install openssh-server
```

once it is installed just open a terminal on your desktop computer and type:

```
ssh username@server
```

to connect, or open Natilus on your desktop and in the location bar type:

```
sftp://username@server
```

your file system on your server will be displayed in Nautilus.

I personally use mc on my server to do almost everything, copy, move and delete files, change ownership and permissions, even edit files. MC is availble in the repositories:

```
sudo apt-get install mc
```

For updates, I usually check once a week for updates, if there are any updates I use:

```
sudo aptitude safe-upgrade
```

to insure that the upgrades don't create a problem. As of right now there is a new kernel installed and ready to boot on my server, but I haven't found a good reason to reboot yet.

Jim

---

### Post by crazydiver on 2008-10-21
Hello Jim,


  Thank you very much! I highly appreciate your post towards my inquiries. I will definitely take a look at the link you gave me and follow your suggestions with the type of servers needed.

Thank you again!:)

---

### Post by crazydiver on 2008-10-22
I'm pretty new with all this networking...

I tried to use putty, but when it prompts for host name (ip address) I'm like... :confused::confused::confused:

I reviewed your post and saw your instructions to type:
ssh username@server in putty... however, I filled in the blank with "adminsitrator"@" my server name"  and I seem to get cannot find.  

Do I need to have my computer directly connected to the server with the ethernet line? or is it accesssible via my router? 

And is putty advisable to use? 

One more thing... what's up with the proxy information. Is that needed to get a server up and running on the internet? In addition, where do get the proxy information if I need it? 

This is definitely a great learning experience but I guess I'm still new with this kind of thing. But thank you all for reading.

---

