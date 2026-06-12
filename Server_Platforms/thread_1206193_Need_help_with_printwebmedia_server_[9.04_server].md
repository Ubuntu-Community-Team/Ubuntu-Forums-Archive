---
title: "Need help with print/web/media server [9.04 server]"
date: 2009-07-06
forum: Server Platforms
---

### Post by blsmit on 2009-07-06
Hi all, 

I am interested in creating a print/web/media server using a MSI wind nettop 100 with ubuntu 9.04 jaunty server 32-bit edition. I want to be able to host test websites to see how they look, listen to music on any computer, and print from any computer. Also connecting via ssh would be helpful if I want to change and am away. I am currently connecting: cable modem -->Linksys WRT54G -wired->MSI Wind.  My ISP does not allow static IP's and I don't mind using dyndns.org.  I am new to ubuntu but can 'terminal' and feel comfortable 'sudo'ing. 

Here are my questions:
1) Is this even possible or am I crazy?
2) Are there directions /Howto's for what I'm after?
   2.1) I've googled, and searched howtoforge.com, ubuntuforums.org, ubuntu community notes etc.
3.) Can I set up something similar to abc.dyndns.org/media, .../web, .../print?
4.)Finally, what about security?
  4.1)I can handle secure passwords, and I don't have anything of value.

Thanks in advance to anyone who replys,
blsmit.

---

### Post by cariboo on 2009-07-07
If you system will run Ubuntu, you can run a server. For web pages you will probably need to install LAMP, for file sharing and media streaming you will need to install Samba, for a print server you will need to install Cups.

This assumes you will install the server version, without a gui. From the prompt type:

```
sudo tasksel
``` 

Select LAMP, Openssh-server, Samba and Print server from the menu, then tab to OK. Once everything is installed, I would suggest you install [Webmin]("http:///www.webmin.com/") for web based server administration. 

To access your web server, you will need to setup a static ip address on the server and then use port forwarding on your router.

---

### Post by blsmit on 2009-07-07
cariboo907, 

Thank you for the fast response, I will attempt your suggestions this morning.

Why must I set up a static IP on the server?  Can I use ddclient to update the IP on dyndns.org?

Thanks, 
Blsmit

---

### Post by blsmit on 2009-07-07
So heres what I did.

I reinstalled Ubunut server edition 9.04
When prompted to install packages, I chose: LAMP, Samba, Print, Openssh
once in I followed [these]("http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html") directions to install webmin (which I can't figure out how to set up)
I also changed my eth0 to be static under /etc/network/interfaces
```

auto eth0
iface eth0 inet static
address 192.168.1.123
netmask 255.255.255.0
network 192.168.1.0
braodcast 192.168.1.255
gateway 192.168.1.1
```I can ping and have successfully pinged to [www.google.com]("http://www.google.com")
my router port settings look like this
```

Applications    start    end    protocol    IP address    
name1            22       22       both        192.168.1.123
name2            21       21       both         192.168.1.123
webmin          1000    1000    both        192.168.1.123
http               80        80        both         192.168.1.123

```I can remote in on my mac $ssh administrator@192.168.1.123
I can access my ipadress and see that apache2 index.html is viewable
However I can not access 192.168.1.123:1000 or 192.168.1.123:80

**NOTE**: This is all within the network (cable modem->linksys-wireless-> mac)

I tested this outside the home network: AKA: I went oncampus and used wireless.  
I can access xxxx.homelinux.org, but not 192.168.1.123.
I got the IP address of the server for xxxx.homelinux.org- resloved to 70.15.83.210
I couldn't ssh to IP address 192.168.1.123
I can ssh 70.15.83.210.


Set up ProFTPd with standalone, used username and password from macbook pro to connect via cyberduck. under 70.15.83.210 and xxxx.homelinux.org/
So its working just not the way I want it to work.

Whats going on?


Ben

---

### Post by cariboo on 2009-07-07
The reason for a static ip address on the server, is that if you are using dhcp and the server  reboots for some reason, it may get a different ip address, then port forwarding will no longer work.

Your setup seems to be working the way it is supposed to. THe ip addresses  behind your router are non-route-able and can only be access locally. To access webmin remotely, you need to enter:

```
xxxx.homelinux.org:1000
```

I hope that is a typo as by default webmin runs on port 10000.

---

### Post by blsmit on 2009-07-07
That makes sense.  Thanks for the information.

That must have been a misread on my part (It still doesn't work, and I'm not concerned.)

So I have my ftp set up which means I should have the web server working.  Thanks to ubuntuforums.org

I've ran into an issue I installed Jinzora2 as my media server program. I followed the directions [here]("http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access"). 
I put my file is /var/www/media/jinzora2.  Which means the index.php I'm supposed to follow is accessed at xxxx.homelinux.org/media/jinzora2/index.php.
When I visit this I receive the following message
```

**Forbidden**

 You don't have permission to access /media/jinzora2/index.php on this server.
  Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at xxx.homelinux.org Port 80


```
Wheres my error now, and how do I fix it?  I rebooted the sever after this error but am receiving the same error.

Thanks, 
blsmit

---

### Post by cariboo on 2009-07-08
Check the ownership and permissions of the jinzora2 directory and contents, the owner should be root or www-data and the permissions should be 755.

I should caution you about running all the services and making them available to the world, especially ftp. Make sure you have really strong passwords on all the services. If it was me I would disable the ftp server, and use scp/sftp to transfer files. Scp/sftp are installed automatically when you install openssh-server, and if running Ubuntu on the desktoop, just open nautilus and in the location bar enter sftp://user@servername, this will open your home directory on the server. Winscp is a free client available for Windows.

To check what ports are open on the server, I use nmap:

```
nmap localhost
```

on my server, that is inward facing I get this output:

```
nmap willy

Starting Nmap 4.76 ( http://nmap.org ) at 2009-07-07 22:56 PDT
Interesting ports on willy (192.168.1.250):
Not shown: 992 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql
```

nmap is in the repositories.

---

### Post by retatkcid on 2009-07-08
Webmin problems???

Judging from your router config, you might not be forwarding anything because of using the wrong port number.  Edit your router's port forwarding accordingly.  My local Webmin URL is:

[https://lampuntu:10000/](https://lampuntu:10000/)

NOTE the secure server protocol:

https NOT http

NOTE port number (of zeros):

Webmin's port should be 10000 NOT 1000

So if Webmin is running and you have set up your user access, you should be able to use the following URL (or reasonable facsimile thereof) to access Webmin's login page:

[https://xxxx.homelinux.org:10000](https://xxxx.homelinux.org:10000)

There's a nice PDF Webmin manual floating around if you know where to look.  I recommend snagging a copy.  <:-p

---

### Post by blsmit on 2009-07-08
@retatkcid: I changed the port on the router to 10000, and used https:// but still no joy. 
I also found the manual and will be reading my way through that.

@cariboo907: I took your advice and uninstalled proftpd, and am able to access my server using sftp://username@xxxx.homelinux.org.  However I am still unable to upload files, I am perfectly capable of downloading. 
The error is 
SSH Error: Upload failed
/var/www/Untitled.html
The user does not have sufficient permissions to perform the operation.
Whats going on here?
 Also I will be generating random 12 character passwords and changing every other day.  I hope that suffices to the security issue.
I downloaded an ran nmap localhost heres the results
```

nmap localhost

Starting Nmap 4.76 ( http://nmap.org ) at 2009-07-08 09:45 EDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 993 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.27 seconds

```The interesting part to me is the "Warning: Hostname localhost resolves to 2 IPs. 
I took the liberty to nmap 192.168.1.xxx (my static IP)
```

nmap 192.168.1.xxx

Starting Nmap 4.76 ( http://nmap.org ) at 2009-07-08 10:09 EDT
Interesting ports on 192.168.1.xxx:
Not shown: 996 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.28 seconds

```and my websites IP
```

Starting Nmap 4.76 ( http://nmap.org ) at 2009-07-08 10:11 EDT
Interesting ports on 70.15.83.xxx.res-cmts.blo.ptd.net (70.15.83.xxx):
Not shown: 998 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

```Why are there not more ports open on the websites IP?
Also i went back and ran code
```

chmod 755 configure.sh

```as per the directions from [here]("http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access").  Still no joy.  Am I missing something.

Thanks once again for helping me through this mess.

Blsmit

---

### Post by blsmit on 2009-07-09
bump

---

### Post by blsmit on 2009-07-10
bump??

---

