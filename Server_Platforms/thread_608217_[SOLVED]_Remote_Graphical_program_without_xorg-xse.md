---
title: "[SOLVED] Remote Graphical program without xorg-xserver"
date: 2007-11-09
forum: Server Platforms
---

### Post by Ashfire908 on 2007-11-09
Ok, I have a server that I own, (which is mainly a test server and a gateway for a PPP connection) that I have  LAMP, SSHd, ProFTPd, and a few other small things installed on it. Now, I used to have GNOME/Xfce4 on it, which a few months ago I reinstalled ubuntu and made it a command line interface only system, and I didn't reinstall ProFTPd.

Recently, I reinstalled ProFTPd, so I and a couple of users which have SSH access could use FTP to transfer files. The problem is that I don't have the patience to figure out how to configure the thing, and I would like to use gProFTPd for configuring it. Only problem is it's graphical and I'm not installing a full-blown xorg-xserver installation on my server. So,

I would like to install just enough (like almost nothing) so I can run it remotely (X11 forwarding with ssh would be nice) from my desktop. I've looked on the forums and in (parts) of the repository for something but i couldn't find anything.

Any ideas how I could do this?



I know SSH supports transferring files, but FTP is more of a universal protocal, and some of the users have windows and don't have anything nice like nautilus's SSH transfer support. I don't really want to make them install a bunch of stuff just to access the server.

---

### Post by HermanAB on 2007-11-09
Try this for a test:
$ ssh -X joesoap@server
password
$ gedit 
(or any other graphical program that you know is on the server)

La voila!

---

### Post by Ashfire908 on 2007-11-09
Well, I've tried running gproftpd, and GTK gave an error that it either could not open, start, or find a display. I'm sorry, I can't give you the exact error as I'm another computer on a different network. I'll be able to start posting the actual errors I get once it's free for me to connect to the Internet from my house.

---

### Post by Ashfire908 on 2007-11-10
While I was at my house before I could get on the internet I tried installing xbase-clients and that worked after I logged out then back in. gProFTPd is working fine! :)

---

