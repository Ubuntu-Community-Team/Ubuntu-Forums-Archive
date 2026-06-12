---
title: "How to setup fileserver for remote access"
date: 2010-05-19
forum: Server Platforms
---

### Post by aubie8 on 2010-05-19
I am very new to Ubuntu (any Linux) evironment. And it has been a long long time since I have dealt with seting up servers.  I have done alot of searching but haven't found exactly what I THINK I am looking for.
 
I want to create a file server (I have created my Ubuntu server cd) and add it to my home network (all windows pcs). 
 
I need to be able to access it when away from home ( I work away from home mostly). I will be accessing this with a Windows 7 laptop.
 
What do I need installed on the server? Samba for the file server part. What else for the remote access? I also would rather not access the data via FTP. I would like it to come up as a drive in my Windows Explorer. If not, I remember back in college (20 years ago) when I could open a little window (XWindow maybe) on the other server.
 
An issue I see that might not be an issue. I have a static IP from my ISP. It comes into my home via their modem. I attach to the modem with a router. All my laptops connect to it wireless and this server will be wired. How do I hit the server and not one of the laptops with only having the one IP address? Each of these plus my external harddrive and printer have their own internal IP address' that I have assigned. If I was host a web server, would I have this same problem? I think so! But how to fix?
 
Thanks for your help!

---

### Post by cariboo on 2010-05-19
Probably the best way to access files on the server remotely, is via sftp/scp. You need to setup openssh-server on the server, and use putty to access the server. For a howto on setting upd ssh have a look [here]("https://help.ubuntu.com/7.04/server/C/openssh-server.html").

You will then have to forward port 22 to your open in order to access the server.

---

### Post by mikewhatever on 2010-05-19
For accessing a server remotely, the first first thing that comes to mind is ssh. You'll need to install openssh-server on the Ubuntu server, and [PUTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") is a popular choice as an ssh client for Windows. As for hitting the right IP on your LAN, use port forwarding function in your router. Ssh uses port 22 by default, which can, and probably should be changed.

[more info on ssh]("https://help.ubuntu.com/community/SSH")

---

### Post by Groodles on 2010-05-21
Sounds like you require a typical road-warrior configuration.

On your server at home, you'll need:

Samba for the File Server
OpenSSH for remote administration (CLI)

For remote access to your file server you need some sort of VPN terminator.  Since you're using a Window7 client I'd recommend using standard PPtP as it works with the standard (built-in) windows client.  There are other options (OpenVPN, OpenSwan, Hamachi) but they are generally more complex to setup.  This link [http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/) is a resonable guide for setting up PPtP on a linux box for use with a Windows client.

Assuming that your home internet connection is ADSL/Cable where your IP address may change, you'll also need to setup some sort of DynamicDNS solution.  (no-ip, dyndyn, etc)  Some routers have the functionality to handle updates built-in, if yours doesnt there are linux clients which can do it as well.

---

