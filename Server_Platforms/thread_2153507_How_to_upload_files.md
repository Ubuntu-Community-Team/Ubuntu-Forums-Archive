---
title: "How to upload files?"
date: 2013-06-11
forum: Server Platforms
---

### Post by harbimilan on 2013-06-11
Hi,
I'm new to Ubuntu Server (but familiar with Ubuntu). I installed Ubuntu Server 12.04 LTS for the first time today. I successfully installed apache, php, mysql, and vsftpd. So I can connect to [http://192.168.x.x](http://192.168.x.x) and [ftp://192.168.x.x](ftp://192.168.x.x) from my other computer.

So I'm trying to find a way to upload my index.php to the apache root folder of my server computer. How do I do this?
with SSH?
with FileZilla?

any would be great, I just need a direction. And I would love it if I can use a GUI on my desktop computer (like FileZilla drag&drop)

I'm aware that using GUI on the server leads to security risks, but using the GUI on my desktop (which will -hopefully- connect to my server) does not impose any security risks, right?

And one final question, (you can answer this by proposing a google search term :) ) I can connect to 192.168.x.x from my other computer (which is connected to same modem), but can I connect to my server from any other network? or is this only local? If the latter, how do I make it available for connection from the internet, and moreover, how do I make it host my domain name?

Thanks !

---

### Post by jonobr on 2013-06-11
Install ssh
sudo apt-get install openssh-server

Once done, you can use a program like winscp on your windows box to upload or download files using a secure copy mechanism

From another linux machine, the command line is a lot easier,

scp myfile user@ipaddress:/home/myhomedir/upload

to upload 

scp user@ipaddress:/home/myhomedir/upload/myfile

to download to the current directory

---

### Post by jonobr on 2013-06-11
For part two, just look for port forwarding .... its more to do with your router configuration .
For ssh you would port forward request on port 22 to a 192.168.1.x machine which is running ssh,
to connect to a web server on your internal network you would port forward port 80 to the ip address of your machine internally and so on

---

### Post by d4m1r on 2013-06-13
Sounds like you would be better off using a FTP program with a UI on your desktop to connect to your FTP service running on your server. Filezilla is an example of such a program with drap and drop functionality and no, doing so does not compromise your servers security.

---

### Post by adotomov on 2013-06-14
> **harbimilan said:**
> Hi,
I'm new to Ubuntu Server (but familiar with Ubuntu). I installed Ubuntu Server 12.04 LTS for the first time today. I successfully installed apache, php, mysql, and vsftpd. So I can connect to [http://192.168.x.x](http://192.168.x.x) and [ftp://192.168.x.x](ftp://192.168.x.x) from my other computer.

So I'm trying to find a way to upload my index.php to the apache root folder of my server computer. How do I do this?
with SSH?
with FileZilla?

any would be great, I just need a direction. And I would love it if I can use a GUI on my desktop computer (like FileZilla drag&drop)

I'm aware that using GUI on the server leads to security risks, but using the GUI on my desktop (which will -hopefully- connect to my server) does not impose any security risks, right?

And one final question, (you can answer this by proposing a google search term :) ) I can connect to 192.168.x.x from my other computer (which is connected to same modem), but can I connect to my server from any other network? or is this only local? If the latter, how do I make it available for connection from the internet, and moreover, how do I make it host my domain name?

Thanks !

You have several options here. First of all, do you have a static IP address? If you do, you can connect to the apache server from any location by simply typing [http://your_static_IP_address](http://your_static_IP_address). As for the domain name, you need to set up a DNS server to be able to do that. If you are new to linux, this might be a very difficult task. 
What OS are you running on your client PC - Windows/Mac/Linux? Also, if you want to access the files on your web server from outside your home network you need an internet connection with a static IP and I would suggest, for security reasons, to set up an ftp server and upload files via filezilla or any other ftp client. If you are accessing the server from a windows pc from your home network, then set up a samba share and point to the root directory of your web server. If you are using Linux, then you can access the file system on your server via sftp from nautilus (or any other file manager, depending on your distro). If you use nautilus, then open it, hit Ctrl+L and type sftp://ip_address_of_server and use your login data for the server.
Hope this helps. 
Cheers!

---

