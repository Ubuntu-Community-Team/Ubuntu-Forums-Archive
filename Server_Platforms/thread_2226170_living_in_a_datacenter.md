---
title: "living in a datacenter"
date: 2014-05-25
forum: Server Platforms
---

### Post by Vegan on 2014-05-25
I created a VM for my web appliance on Azure, its a single core with 1.75 GB of RAM, hosted by Hyper-V. Best they got is 8 cores and 56 GB RAM so I think I will have some elbow room.

So I was thinking SAMBA the old way is not going to work, so I need to figure out how to live in the cloud now

also a I was using vsftpd but I am not sure what is the option today?

when I installed LAMP it was so fast, they must have a super fast server that blows away my old box, took under 5 seconds to install it

---

### Post by CharlesA on 2014-05-25
What is the purpose of this machine?

---

### Post by Vegan on 2014-05-25
web hosting mostly

---

### Post by CharlesA on 2014-05-26
sftp/scp/rsync via ssh beats the crap out of samba or ftp imo. Easier to deal with and more secure too.

You should be fine with just running a LAMP stack and using sftp or rsync to transfer files to and from the server.

---

### Post by SeijiSensei on 2014-05-27
As a Kubuntu user, I take advantage of Dolphin's support for the "fish" protocol.  If I enter a URL into dolphin like fish://user@hostname/directory, it creates an sftp connection to the remote's filesystem and gives me all the rights associated with "user".  It makes moving files between a local machine and the remote server really simple.

I also suggest considering an [OpenVPN static tunnel]("http://openvpn.net/static.html") to the remote.

---

### Post by nerdtron on 2014-05-27
SFTP, FISH etc. You can also use FileZilla or just the default browser in Ubuntu to connect to your server and transfer files with a nice GUI.

---

### Post by nerdtron on 2014-05-27
SFTP, FISH etc. You can also use FileZilla or just the default browser in Ubuntu to connect to your server and transfer files with a nice GUI.

---

### Post by Vegan on 2014-05-29
I use Filezilla now and have some familiarity using it with Azure web sites already.

What should I do with these held back updates?

azureuser@LAMP:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-cloud-tools-virtual linux-headers-generic linux-headers-virtual
  linux-image-extra-virtual linux-image-generic linux-image-virtual
  linux-virtual
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
azureuser@LAMP:~$

---

### Post by SeijiSensei on 2014-05-29
If you use "sudo apt-get dist-upgrade" those packages will be installed.

---

