---
title: "Remote access to server via Internet"
date: 2014-10-21
forum: Server Platforms
---

### Post by scholzvojta on 2014-10-21
Hi,
   is there some solution to get remote access to my Ubuntu 14.04LTS 64-bit server via internet **_without_** **public IP adress**??? I tried TeamViewer, but it isn't work (No ID getted). Is there some else option?? Thanks ;)

---

### Post by irv on 2014-10-21
A good way to look at this is if you want to access your server from the Internet it must be unique (unique IP address). The static IP need to be setup on your Router.
I have a Web server with a URL (Domain Name) I access my server using
```
sudo ssh username@domainname
```
Then login with username and password.
You can use your IP in place of your domainname if you don't have one.
```
sudo ssh username@IP-Address
```
This is a secure way of doing it.
You also have to have an internal static IP set on your server.
Your ISP can issue you a static IP in place of your DHCP. Then all you have to do is setup your ports on your router.

You can also access your server by going to Nautilus and pressing [Ctrl] L and typing:
```
sftp://username@IP or domain
```
Again just login with name and password and you can access all your files on your server.

---

### Post by irv on 2014-10-21
Here is my router setup. I have a LinkSys Router.
[ATTACH=CONFIG]257423[/ATTACH][ATTACH=CONFIG]257424[/ATTACH]

My internal IP Address on my server is 192.168.1.105, so it is the only one I access from the Internet.

---

### Post by SeijiSensei on 2014-10-21
Are you saying your server doesn't have a static public address?  How does anyone reach it?

---

### Post by lukeiamyourfather on 2014-10-22
Using SSH is the de facto way to access a remote Linux server. If the machine doesn't have a public IP address the router for the network can be configured to let traffic through. If that router has a dynamic IP address (like most consumer internet connections) there are dynamic DNS services that will give you a publicly accessible URL but require a client on the network to report back the current dynamic address.

---

### Post by splintr on 2014-10-22
Hi,

To manage your system you need your WAN IP Adres, you can find it here [http://www.whatismyip.com](http://www.whatismyip.com).
Next thing if you don't have a gui installed you can use SSH (you need the ssh server) to remote login to your system terminal.

If you install a gui, you can use vnc server on your ubuntu machine and a vnc client to see the desktop and manage everything with the gui.

Hope this helps you in the good direction

---

