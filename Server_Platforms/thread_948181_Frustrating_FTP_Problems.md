---
title: "Frustrating FTP Problems"
date: 2008-10-15
forum: Server Platforms
---

### Post by winrowc on 2008-10-15
Ive been having some trouble using FTP with ISPConfig in Ubuntu, and could really use some help. 

I checked out howtoforge and their forums but unfortunatly their help hasnt been effective in solving my problem

Okay So I decided to go with what I know, so I am running an Ubuntu server, and using Dreamweaver in a Virtualbox machine on another Ubuntu (desktop) machine, to access the files. The problem is that FTP in Dreamweaver comes up with an error that the folder can't be found. I had the same problem when the server was run with Fedora 9, but that system had a lot of problems, this Ubuntu Server is a fresh install.

Heres what I know:
I only have one site created. Its in /var/www/ which is where it should be. In /var/www/ there is a web1 folder in that directory (my ISPConfig client username is web1_admin) and there is also a [www.example.com](www.example.com) shortcut folder which links to the web1 folder. I am sure that port forwarding, DMZ and everything on the router end is set for the server's static IP (192.168.1.9). The server computer doesn't show up on the router, but that is natural because it is not being assigned a DHCP address.  The nameservers are correct with the domain (Im using name.com), and I gave the user web1_admin has administrator preferences in ISPConfig. Ubuntu doesn't have a firewall so nothing is blocking it. It seems as though I've done everything imaginable for this to work, yet it still doesn't.
So I am trying to access the site via FTP from my local network. Web-FTP in ISPConfig sees the folders, so I assume that works. I have tried passive and normal FTP in Dreamweaver, but it has no affect.

In dreamweaver I should be able to type in "192.168.1.9" as my ftp host right? Not my public IP because that would only be for out of the network correct? Should I try like ftp.thesitename.com or something?
"Web1_admin" and my client password should be the ones I use not my ISPConfig control panel admin login...
The host directory should be /var/www/web1

I've tried it with and without passive ftp
ISPConfig says all services are up and running. What could the problem possibly be? IS this dreamweaver's fault? I don't have any non homeserver websites to test Dreamweaver's FTP, and besides Dreamweaver has always worked great in the past.

Any help would be much appreciated as I would love to get my server up in running after this irritating hurdle.

---

### Post by koenn on 2008-10-15
> **winrowc said:**
> 
In dreamweaver I should be able to type in "192.168.1.9" as my ftp host right? Not my public IP because that would only be for out of the network correct? Should I try like ftp.thesitename.com or something?
"Web1_admin" and my client password should be the ones I use not my ISPConfig control panel admin login...
The host directory should be /var/www/web1



probably the address is coreect, but the folder should just be web1

/var/www/web1 is the path as it is known to your linux system, with a filesystem starting at /
for your ftp server, /var/www is it's root (/), i.e. you are (or should be) taken to /var/www when you connect to ftp, and all dreamweaver needs to know that it has to go to web1, the path from the ftp-server's point of view is just /web1

you should be able to test this by ftp-ing to the server, ask what the currect directory is, and ask for a directory listing:
```

x:~$ ftp ftp.server.xx

Name : BillyTheKid
331 Password required for BillyTheKid
Password:
230 User BillyTheKid logged in.
Remote system type is UNIX.
Using binary mode to transfer files.

ftp> pwd
257 "/" is current directory.

ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxr-sr-x   2 ftp      ftp           512 Mar 15  2003 somedirectory
drwxr-sr-x   6 ftp      ftp           512 Mar 15  2003 someotherdirectory

//(you should see web1 here)

```

If this doesn't work, it means that your ftp server is probably not set up right, particularly re. the root (or home) directory for the ftp users.

---

### Post by winrowc on 2008-10-16
Oh my god you have saved my life. That worked perfectly, you gave a great explanation. All i needed was to point it to / instead of /var/www. Thanks again.

---

### Post by koenn on 2008-10-16
one more life saved - OK.

:)

---

