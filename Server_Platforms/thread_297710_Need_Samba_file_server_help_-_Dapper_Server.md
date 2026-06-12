---
title: "Need Samba file server help - Dapper Server"
date: 2006-11-11
forum: Server Platforms
---

### Post by j1mc on 2006-11-11
Hello all,

I need some help setting up a Samba file server on an old PII-400 box that someone sold me for $20.00.  :)  This server will just support one desktop ("okdesktop") and one laptop ("okthinkpad").  

I've searched over much of the documentation, but I'm not really sure where to begin.  I want this to be a headless server that I can administer via ssh (and configure samba via webmin), so I set up a basic Dapper server install with samba, smbfs, apache2, webmin, and open-ssh on it.

The server uses DHCP to obtain an IP address from my router (I don't have a static IP, but the IP address doesn't change frequently.)  The server name is "okserver" and I would like the domain name to be "oknetwork".  I've been able to SSH into the server using my username on that machine and the machine's IP address . . . 

I've heard some reference to how samba uses NETBIOS to coordinate things, so I won't need a fixed IP address to make this work.

One thing I noted was that, when I restart Apache, it gives me a message, "Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName," so maybe I'm missing a bit of detail.  Would I need to set something up in my /etc/hosts file?

Also, trying to access the webmin interface via [https://okserver:](https://okserver:)[my port number] doesn't work.  (localhost, or the localhost IP address didn't work, either)

I know that I need to modify my smb.conf file, but I'm not sure what changes to make there.  I would like to set up one file repository that would be at least readable by all authenticated users, with at least one of the users able to write to the file server.  Really, all of the authenticated users should have read/write access . . . 

Sorry to be such a noob.  I've been running pretty much only Linux since May of this year, but this is my first foray into networking.  Your help would be greatly appreciated.  Thanks!

---

### Post by emkamau on 2006-11-11
Hi
I've just been doing this today and managed to get my server up and running.First bit of advice. Go to [www.webmin.com](www.webmin.com) and download the webmin deb from there and install that. I've never been able to get the Ubuntu Dapper webmin to do anything. Once you do that check that webmin is running. In a terminal type:

ps axu |grep webmin

you should get some output with miniserv.conf at the end. If not yoy can start it by typing into the terminal

sudo /etc/init.d/webmin start

then you should be able to [https://serverip:10000](https://serverip:10000) to get in. Use your regular user name and password to get in.

You should not have to directly edit your smb.conf file if all you want is to set up a headless server.

Hope that helps

emk

---

### Post by j1mc on 2006-11-11
Ah, sweet!  Thanks!!

Your comment was helpful.  I had installed webmin just via their tarball, and I was missing a dependency which was identified by installing the .deb package.  I'm in now, and now I'll just have to figure out how I want to configure this.

---

### Post by rickyjones on 2006-11-13
Quick note: It might make your life easier if you also set up the server as a static IP on your LAN. Just a thought.

---

