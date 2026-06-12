---
title: "Running proftpd with webmin"
date: 2008-10-23
forum: Server Platforms
---

### Post by SteveHillier on 2008-10-23
Hi guys & gals,
I am looking for a comfort zone.
I have a server with webmin installed and running proftpd as the ftp server.
The server is to be used for development work because as I use php files, I don't like developing and testing on a publicly accessible server.
So the server is built, running in our LAN, it gets switched off at night, we are using our Win 2003 domain server as the DNS server (for all sorts of reasons, it runs DNS for other purposes so why not?).  This makes it accessible through the LAN and if need be it could be made accessible through the WAN if I were feeling devilish.  This bit works because I can get up the default apache page on sites I have set up.
I have been able to create ftp users and when running my ftp client (FileZilla) I can log on to the home folder but I do not get a directory listing nor can I transfer anything to it - I get permission denied message.
At the moment I am trying to hang everything off /var/www.  This is because on our production server we use Plesk which drives everything from /var/www so I thought I was being clever.

From reading this forum I am getting the feeling that
a. I should not use /var/www/anything which means I should probably use the normal /home/username/something as the website home;
b. I would need to change the apache virtual hosts to these folders (oops - sorry - too much Windows - I mean directories);
c. I assume this will then sort out access permissions and it would remove the need to use symlinks as suggested in one of the posts.

I am just looking for some comfort that I am thinking in the right direction.

Thanks
Steve

---

### Post by SteveHillier on 2008-11-06
Hi folks,
Just to way, I have removed webmin, I have changed from ProFTPD to vsftp, I am manually configuring virtual hosts So this thread can die.
Steve

---

