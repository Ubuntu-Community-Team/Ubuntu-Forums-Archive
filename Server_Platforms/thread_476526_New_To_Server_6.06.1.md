---
title: "New To Server 6.06.1"
date: 2007-06-17
forum: Server Platforms
---

### Post by pug2694328 on 2007-06-17
I've installed server 6.06.1 and am so excited to get started!  I'm not an experienced system admin, and I've noticed that a lot of the doc is written towards that audience.  My first goal is to setup a folder that I can access from my several windows boxes to dump files to the server (or retrieve them).

Step 2 will be creating the same, but for off site access... for example, I'd like to create a backup to my home server from my work windows box, how would I setup that type of access (while preventing access by uninvited guests).  Maybe that will entail an FTP service?  Maybe there's a better option.

I'd also like to be able to login to my new server from my work computer (windows).  Not sure how to set that up.

Is there a good doc already to explain these processes (keep in mind I'm command line only) for a newbie audience?

Might it be too much to ask for the windows side doc as well?

Thanks in advance for any help you might proffer!

ps, I didn't opt to install the web server (aka LAMP) version offered by the install tool as I'd prefer to only install things that I need, particularly as I'm ever concerned about security.

---

### Post by dmizer on 2007-06-17
for a samba file server (hosting files to windows computers), check the first link in my sig.

for an ftp server, check the third link in my sig.

to access your computer remotely (commandline only) you'll need openssh-server to be installed.  in windows you can use [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/) to access your server via ssh.  from linux the command would be similar to: ssh server_username@server-ip-address

you can install [webmin](http://www.webmin.com/) on your server in order to access, configure, and controll your server with a gui like web interface (security note: do not allow webmin access from outside your local network).  here's a howto for installing webmin on your server: [http://ubuntuforums.org/showthread.php?t=195093](http://ubuntuforums.org/showthread.php?t=195093)

---

