---
title: "Configure FTP on Linux server which has static IP"
date: 2012-04-18
forum: Server Platforms
---

### Post by pavi_elex on 2012-04-18
I am using ubuntu 11.10 as a server. It has its static public IP. I want to access this server using filezilla (ftp client) from outside LAN.
I can access this server by sftp inside LAN using filezilla but I want to access this server outside LAN.
How can I access this?

---

### Post by oboyledk on 2012-04-18
Can you ping your public IP?

Is there a firewall of some kind on your server that prevents connections?

You should be able to just enter the public IP.  

This is a pretty solid walkthrough on VSFTP setup that I've used:
6. Installing FTP Server (VSFTP)

You will need a simple ftp server to upload and download your web files. i specially like vsftp server because not only it is very easy to configure but also runs faster than other ftp peers with good connection speed.

apt-get install vsftpd

Configuration file is located at: /etc/vsftpd.conf

Change the following settings in /etc/vsftpd.conf so that you allow local users and allow write using ftp.

# Uncomment this to allow local users to log in.
local_enable=YES
# Uncomment this to enable any form of FTP write command.
write_enable=YES

Before you connect using ftp client, you will need to create local users and group. Do not upload files using root.

# CD to /home/<user> and create a symbolic link to /var/www as this is the public html folder. 
ln -s /var/www www

#change ownership /var/www to user
chown -R <user> /var/www

#Change to 755 permissions 
chmod -R 755 /var/www

Now you can connect to ftp and upload files. Once you upload all necesarry files in the public html folder, make sure all the files have 755 permission as otherwise you will get permission denied/forbidden error from apache.

Pulled from: 
[http://mysql-apache-php.com/#ftpserver](http://mysql-apache-php.com/#ftpserver)

---

### Post by Lars Noodén on 2012-04-18
> **pavi_elex said:**
> I am using ubuntu 11.10 as a server. It has its static public IP. I want to access this server using filezilla (ftp client) from outside LAN.
I can access this server by sftp inside LAN using filezilla but I want to access this server outside LAN.
How can I access this?

You can access via SFTP using FileZilla.  That would be a much safer idea than using FTP.  

Your router needs to forward port 22 (SSH) for you to do that with SFTP.  The specific vary from router to router.

[http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

If it's not a matter of port forwarding, and you actually have a static public IP, then you need to have the filewall allow incoming connections on port 22.

---

