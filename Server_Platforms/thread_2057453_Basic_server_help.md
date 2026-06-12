---
title: "Basic server help"
date: 2012-09-13
forum: Server Platforms
---

### Post by Shea6892 on 2012-09-13
So this is my first time setting up a server, chose to go with ubuntu server 12.04 lts. I went through the set up and installed the OS, including some packages such as LAMP, openSSH, etc. Also set up my network configuration on the server to a static IP. I basically want to be able to access my server remotely from a windows comp. I am not sure if I want it to be a web server or a file server or what but I want to be able to add files to it while be able to access remotely as an admin, and as a user to view(possibly download) the files/web pages contained on the server. Having said all that, I'm not really sure what to do from here to add/view/download files to and from the server. Do I need a domain name and/or to use DynDNS to remotely access from outside the LAN. Oh and this is on a home network on a laptop that was just sitting around collecting dust. Thanks to anyone who can help it is much appreciated.

---

### Post by Bachstelze on 2012-09-13
What exactly do you mean by "add", "view", or "download"? To transfer files, since you have installed OpenSSH already, you can use its file transfer protocol (SFTP), with FileZilla or WinSCP. To access a command line, you can use PuTTy.

---

### Post by Shea6892 on 2012-09-13
> **Bachstelze said:**
> What exactly do you mean by "add", "view", or "download"? To transfer files, since you have installed OpenSSH already, you can use its file transfer protocol (SFTP), with FileZilla or WinSCP. To access a command line, you can use PuTTy.

Yeah I know I have putty to access the command line and okay I can use filezilla to transfer files, so basically I want to know if I need a domain name to access the server via a browser, or how would I identify the server in the URL bar?(since the IP would just give my router connection) correct? And thanks that response was instantaneous.

---

### Post by kennethconn on 2012-09-13
Have you read the documentation?
Have you searched the forums?

BEFORE posting here.

---

### Post by papibe on 2012-09-13
Hi Shea6892.

For steady access to your home server from outside, you would need to subscribe to a dynamic DNS service (there are several to choose from, see this list [here]("http://dnslookup.me/dynamic-dns/")). This service will give you a domain name, and it would let you access all your services by using different ports for each one.

In order to pass from your router to your server, you would need to forward the necessary ports from your router to your server (one port for each service).

Hope that helps. Let us know how it goes.
Regards.

---

### Post by Bachstelze on 2012-09-13
> **Shea6892 said:**
> Yeah I know I have putty to access the command line and okay I can use filezilla to transfer files, so basically I want to know if I need a domain name to access the server via a browser, or how would I identify the server in the URL bar?(since the IP would just give my router connection) correct? And thanks that response was instantaneous.

A domain name is only a "shortcut" to an IP address, so no, a domain name is not strictly necessary, you can access your server with the IP address only (but a domain makes it more convenient for a lot of things). You will need to setup port forwarding in your router, so that it forwards requests on port 80 (HTTP standard port) to your server.

---

### Post by Shea6892 on 2012-09-14
> **papibe said:**
> Hi Shea6892.

For steady access to your home server from outside, you would need to subscribe to a dynamic DNS service (there are several to choose from, see this list [here]("http://dnslookup.me/dynamic-dns/")). This service will give you a domain name, and it would let you access all your services by using different ports for each one.

In order to pass from your router to your server, you would need to forward the necessary ports from your router to your server (one port for each service).

Hope that helps. Let us know how it goes.
Regards.

Alright thanks guys. So I ran into a little problem. I am doing this at my GFs house and she has an olllllld router (linksys wrt50g) and apparently it only gives you the option to choose between dynDNS and TZO, both of which cost money. I have no problem spending money on it but I want to get more experience before I do. I mean it's probably worth while to upgrade my router and play around with the free services for a while right? And thanks papibe this post was real helpful.

---

### Post by papibe on 2012-09-14
Although the ideal way to setup a dynamic DNS client would be on your router, you can also set it up on the server itself. That is the way I have it set up on my home. 

Check the package 'ddclient'. It is on the repositories.

Regards.

---

### Post by Bcordrey on 2012-09-14
Also, depending on how comfortable you are with hardware, dd-wrt makes an alternative firmware for the wrt54g. It allows connections to most of the ddns hosts. Before doing anything with this route though, make sure you read everything available on your router and model on their forums. Choosing to do this can and will brick your router if you fail to research thoroughly and follow the instructions exactly.

---

### Post by SeijiSensei on 2012-09-14
In the short term, just put an entry into /etc/hosts on the server and on any clients that need to connect to it.  Something like "janet.local" would do.  Then if the client's [hosts file]("http://en.wikipedia.org/wiki/Hosts_%28file%29") has an entry for janet.local, you should be able to start start Apache and connect to [noparse]http://janet.local/[/noparse] with a browser to display the contents of /var/www.

If you think you will be trying to manage this system from your home, you should look into setting up a static-key OpenVPN tunnel between her machine and yours.  One of them will need to have a port forwarded through the router; the other can act as a client.  See [this documentation](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html) for details.

---

