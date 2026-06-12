---
title: "Help with vsftpd setup"
date: 2011-10-24
forum: Server Platforms
---

### Post by petsoukos on 2011-10-24
Hello,

I can't figure out how to setup the vsftp correctly. What I need to achieve is to have a user per Name-Based Virtual Host.

I'm using Ubuntu Server 10.04.3 LTS (VM physical network replication).

I have 2 Name-Based Virtual Hosts that work just fine with HTTPD (apache2) eg. domain1.lnx & domain2.lnx and I can access them from the Host machine and other machines connected on the network as well as the outside world (if that outside machine points the domains with the hosts file to my external IP).

I have installed the vsftpd with this command:
**sudo apt-get install vsftpd**
and I get:
vsftpd start/running. process ####

I can tell that it is working by accessing the machine from the network, and I get the login prompt in the browser.

Now this is were I'm getting lost.
How to create users and add them to the virtual hosts.

This is my file structure for the virtual hosts
**#1** sits in /srv/www/domain1.lnx/public_html/
**#2** sits in /srv/www/domain2.lnx/public_html/
**#3** ...
etc.

I need a user for example named **usr_domain1** to access the **/srv/www/domain1.lnx** <!-- folder _only_!
The others should follow the same naming conventions. (usr_domain2 for domain2.lnx, usr_domain3 for domain3.lnx)

I've searched around but I can't make it work.
Thanks!

PS. I'm doing all this to simulate working with a linux server, because I'm going to get my self a 512 Linode to host my sites and my client's sites and I wan't to be ready to setup that linode with ease.

---

### Post by Lars Noodén on 2011-10-24
If what you are looking to do is transfer files securely, then you should look at SFTP instead of FTPS.  It is part of the package [OpenSSH-server](http://packages.ubuntu.com/oneiric/openssh-server) and requires no additional configuration on the server side.  

On the client side, there are many SFTP clients like FileZilla and built-in ones like Nautilus and Konqueror.

---

### Post by HermanAB on 2011-10-24
Yup, ssh is what you should use.  It also has the ability to chroot a user to a specific directory.  So it can do what you want and it encrypts the connection.

---

### Post by petsoukos on 2011-10-25
Thanks for the replies.

I want FTP so I can add those accounts on Dreamweaver for quick edits on the files.

---

### Post by Lars Noodén on 2011-10-25
> **petsoukos said:**
> I want FTP so I can add those accounts on Dreamweaver for quick edits on the files.

In that case you can still use [SFTP](www.google.com/search?hl=en&q=sftp+dreamweaver) and not have to get dragged down into [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  FTP was fine back in the old days, but is unsafe for anything other than read-only downloads.

---

### Post by petsoukos on 2011-10-25
I've managed to add a user per Name Based Virtual Host. With some commands I found in this forum I gave permissions to specific folders.

sudo chown -R username /path/to/directory
sudo chmod -R 777 /path/to/directory

Seems fine but have some issues with the connection. If it stays IDLE for to long, when I try to open a Directory or refresh the current Directory I get:
[COLOR="Red"]Error:	Disconnected from server: ECONNABORTED - Connection aborted
Error:	Failed to retrieve directory listing[/COLOR]

The same happens when I edit a file with Dreamweaver, I get an error. I have to re-save for it to upload correctly.

Could this be an issue with Host and VMware communication? I haven't tried to access the server from another machine on the same network or external (internet).

---

