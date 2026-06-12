---
title: "need folder for users"
date: 2012-01-09
forum: Server Platforms
---

### Post by Rakeshvijayan on 2012-01-09
Hi I have some question today that my boss asked

1) he need a folder on our server to store his data and he need to access that folder on every computer on our network .

2)folder must be password protected , if he access that folder, need password access data 


Friends is it possible to configure on our server ,we use  ubuntu 11.10 .if it possible how to configure it or give me an Idea 

Thanks

---

### Post by elliotbeken on 2012-01-09
In my opinion i would use a FTP server for this. I know accessing the server is a little bit harder/longer but it is simple fast and easy.

---

### Post by Rakeshvijayan on 2012-01-09
if I installed vsftpd how can i access ftp in windows.Is it have gui

---

### Post by elliotbeken on 2012-01-09
No the server configuration is text based but the server can be accessed by a FTP client such as FileZilla.

---

### Post by Buntumatic on 2012-01-09
If he wants just to access it, then http is hard to beat.
Fire up a lightweight http server, you can use any port that is not used or even port 80. I'd recommend webfs, it can be configured to ask for password and do directory listing, even logging is supported.

 [http://linux.bytesex.org/misc/webfs.html](http://linux.bytesex.org/misc/webfs.html)

---

### Post by Lars Noodén on 2012-01-09
Take a step back for a moment.  The poster above probably meant [SFTP instead of FTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SSH_File_Transfer_Protocol_.28SFTP.29).  FTP has been around since the early 1970's and is well-proven but it is incurably insecure.  It's been replaced by SFTP, which is designed from the beginning to be secure.  

You can still use clients like FileZilla, Nautilus and Dolphin with SFTP.  There are even fancier tools like SSHFS which make the remote system look like a normal local folder.

SFTP is part of SSH.  So if you have OpenSSH-Server already installed, you already have SFTP and need no configuration.  In that case you can safely uninstall the old FTP server and forget about it. 

As far as sharing write access goes, you need to do that by managing group permissions.  Make a group and then add people to that group, then make sure to add the group to the folder.

The example below shares the folder /var/www with the group "webmasters"

```

sudo addgroup webmasters

sudo gpasswd --add rakeshvijayan  webmasters
sudo gpasswd --add colleague1  webmasters
sudo gpasswd --add colleague2  webmasters
# etc.

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

Edit: here is the Ubuntu documentation on SSHFS: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by volkswagner on 2012-01-09
If your boss wants to be able to edit the files directly on each workstation, I suggest using SAMBA.  It may not be as simple as an FTP server but in my opinion once setup it's more user friendly.

It may be less work in fact.  Depending on the number of workstations, you'll need to install an SFTP client on each.

With SAMBA the share can be browsed using Windows File Explorer.  You boss can also map it as a network drive on his workstation.

If he needs access to the share outside the office than SAMBA is not the solution, as it is best to use it on LAN.  If he uses RDP to access his office machine than SAMBA will be a good fit for remote work as well.

Check the sticky at the top of the Server Forum for help.

The following will get you started with no security.  
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

Once you get the above working you can secure it:
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html)

If you need any additional help, post your specific questions here.

---

### Post by Buntumatic on 2012-01-09
In actuality, there is no reason you couldn't combine the advises you've got and have it served over http so he can access it from anywhere and over sftp or scp from certain hosts to allow editing.

---

### Post by Rakeshvijayan on 2012-01-09
> **Lars Noodén said:**
> Take a step back for a moment.  The poster above probably meant [SFTP instead of FTP]("http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SSH_File_Transfer_Protocol_.28SFTP.29").  FTP has been around since the early 1970's and is well-proven but it is incurably insecure.  It's been replaced by SFTP, which is designed from the beginning to be secure.  

You can still use clients like FileZilla, Nautilus and Dolphin with SFTP.  There are even fancier tools like SSHFS which make the remote system look like a normal local folder.

SFTP is part of SSH.  So if you have OpenSSH-Server already installed, you already have SFTP and need no configuration.  In that case you can safely uninstall the old FTP server and forget about it. 

As far as sharing write access goes, you need to do that by managing group permissions.  Make a group and then add people to that group, then make sure to add the group to the folder.

The example below shares the folder /var/www with the group "webmasters"

```

sudo addgroup webmasters

sudo gpasswd --add rakeshvijayan  webmasters
sudo gpasswd --add colleague1  webmasters
sudo gpasswd --add colleague2  webmasters
# etc.

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```Edit: here is the Ubuntu documentation on SSHFS: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)


will you give me whole steps to install and configure sftp , I think this advice is better for me .but ([https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)) for adavaced users .Yesterday I installed samba and give a folder to him .It just only  for temporary . waiting for your replay

---

### Post by Lars Noodén on 2012-01-10
> **Rakeshvijayan said:**
> will you give me whole steps to install and configure sftp , I think this advice is better for me .but ([https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)) for adavaced users .Yesterday I installed samba and give a folder to him .It just only  for temporary . waiting for your replay

Step 1) Install package [OpenSSH-Server](apt://openssh-server/). SFTP is part of SSH.

Step 2) Ready.  Connect with FileZilla or other SFTP client.

---

### Post by Rakeshvijayan on 2012-01-10
> **Lars Noodén said:**
> Step 1) Install package [OpenSSH-Server]("apt://openssh-server/"). SFTP is part of SSH.

Step 2) Ready.  Connect with FileZilla or other SFTP client.


do I need to add those user fuse befor added to group , am testing it on virtual box and Thanks for quick replay

---

### Post by Rakeshvijayan on 2012-01-10
This is the message that I got when I try to connect to server ,which port that I want to use

---

### Post by Lars Noodén on 2012-01-10
> **Rakeshvijayan said:**
> do I need to add those user fuse befor added to group , am testing it on virtual box and Thanks for quick replay

It is not needed.  To install [sshfs](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sshfs.1.html) on the client just add the package [sshfs](apt://sshfs/).  Otherwise use FileZilla or Nautilus.

> **Rakeshvijayan said:**
> 
This is the message that I got when I try to connect to server ,which port that I want to use

The screen shots show you trying port 21.  That is for [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  We are setting you up for SFTP, which is port 22.  Try port 22 (SSH) instead.

---

### Post by Rakeshvijayan on 2012-01-10
> **Lars Noodén said:**
> 

The screen shots show you trying port 21.  That is for [FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp").  We are setting you up for SFTP, which is port 22.  Try port 22 (SSH) instead.

Connection refuse messege again do I need to edit anything on server

---

### Post by Rakeshvijayan on 2012-01-10
I tried it again and the result is same entire configuration that I did can explain the picture, I can login to the same system

---

### Post by Lars Noodén on 2012-01-11
The last screen shot gives the relevant error, "no route to host"  Are you sure the ip number is 10.0.2.15?  Also, it is the remote machine that has to have the package openssh-server not the local machine.

---

### Post by Rakeshvijayan on 2012-01-12
> **Lars Noodén said:**
> The last screen shot gives the relevant error, "no route to host"  Are you sure the ip number is 10.0.2.15?  Also, it is the remote machine that has to have the package openssh-server not the local machine.


Thanks for the great help form you friend .and a doubt is it possible to publish the file that we uploaded to group members ?

---

### Post by Lars Noodén on 2012-01-12
Yes, see the setting proposed in #6 above.  They should allow a group of people to share write access to the default web directory.  If you have changed the defaults, adjust the instructions in #6 accordingly.

---

