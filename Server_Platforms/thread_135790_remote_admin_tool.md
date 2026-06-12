---
title: "remote admin tool"
date: 2006-02-24
forum: Server Platforms
---

### Post by tenoca on 2006-02-24
My thoughts on a server are that servers ought to have a Remote admin tool, a little application that you can open and configure your server from there.

I know there is webmin, but I'm not really thinking about something like this, though I currently like it and use it.

I'm thinking something like the MacOS X Server admin tool.

[http://www.apple.com/support/downloads/serveradmintools104.html]("http://www.apple.com/support/downloads/serveradmintools104.html")
[http://www.computerworld.com/softwaretopics/os/macos/story/0,10801,87384,00.html?macsurfer]("http://www.computerworld.com/softwaretopics/os/macos/story/0,10801,87384,00.html?macsurfer")

I'm thinking about an integrated remote tool to configure:

[LIST]
[*]File and print
[*]windows services
[*]open directory /ldad
[*]mail services
[*]web hosting
[*]collaboration services
[*]groupware
[*]workgroup
[*]netboot
[*]software update (create local repositories)
[*]networking
[*]VPN
[/LIST]

now we don't have to limit ourselves to what apple does or do it how apple does it, but if Ubuntu Server were to have a tool like this and maybe more features, modules for web hosting, etc. where was I , ohh yes, If Ubuntu Server were to have a tool like this, I would readilly kick the pants off MS server

Maybe also a similar web based admin, taht is newbi friendly

Any thouhgts?

---

### Post by earobinson on 2006-02-24
ssh is a good one because then you can conect to the comptuer and do anything you want.

VNC also if you like guis

---

### Post by grendelkhan on 2006-02-25
Webmin, along with a host of modules is out there as well.

---

### Post by Rollo Tamasi on 2006-02-25
[QUOTE=earobinson]ssh is a good one because then you can conect to the comptuer and do anything you want.

VNC also if you like guis[/QUOTE]

hi earobinson, i have a quick question about ssh. 
is it just a simple case of opening up port 23 for inbound and bound connections
on the box and then connecting with putty or something similar? Is there anything else that needs to be installed?

---

### Post by kharyett on 2006-02-25
I would really suggest that if you are going to use SSH, then you do if with keys instead of passwords. Much more secure. Its fairly simple and is eplained quite well on the putty site.

Use putty-keygen to create the keys (or generate them in Ubuntu). Put the public on the server, change the ssh config to not allow passwords, use pageant, load the key, login with putty.

Quick, secure and easy. 


You can then setup a VNC server, and connect through port forwarding on your ssh connection for an encrypted connection.

---

