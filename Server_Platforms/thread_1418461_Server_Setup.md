---
title: "Server Setup"
date: 2010-02-28
forum: Server Platforms
---

### Post by jsriz on 2010-02-28
Well at our college we are under fortiguard-a web filtering service 
I respect  my colleges internet policy but torrents are blocked which is our biggest pain.
At my house I have a unlimited broadband connection but with dynamic ip and also an old system which is running xp.
Could any one please help me to set up an ubuntu server on that system so that i can ssh into it from my college and download my files and then scp the files to my system.

---

### Post by hhacckerr on 2010-02-28
You could probably use Ubuntu desktop with SSH installed. However, for server, just follow the [step-by-step guide]("https://help.ubuntu.com/9.10/serverguide/C/installation.html"), and install openssh.

[DynDNS]("http://www.dyndns.com/") will provide you with a domain name for your dynamic ip, they should have a perl script that you can use.

You also might be interrested in SSH tunnelling so that you can torrent on your school computer, without having to scp the files.

---

### Post by junke1990 on 2010-02-28
lol don't get me started about school policy xP

Just set up an Ubuntu client or server.

SSH server with blacklists, Screen for wrapping session so the session will stay alive after you disconnect and DenyHosts for blocking attacks.

```
sudo apt-get install openssh-server openssh-blacklist openssh-blacklist-extra screen denyhosts

```

Check out PHProxy, it encrypts your URL so you can bypass the url filter. PHProxy are only 3 files which you can place in your www directory.

Or ssh to your server with -D 8080 as parameter, this will create a dynamic tunnel. So you can use your server as a real proxy server through ssh. 

I do it all the time, ssh [email]junke@my.server.com[/email] -D 8080 and in firefox set your proxy setting, SOCKS-host, to localhost port 8080. 

Should it be that your school is blocking port 22 for ssh then run the server on port 443, they never block that since it's the default port for https traffic. 

search for Port 22 and add, port 443 on a new line, or change it to 443

the file you need is /etc/ssh/sshd_config
after editing, remember to restart your ssh server, /etc/init.d/ssh restart

(at the top of the config most of the time)

---

### Post by jsriz on 2010-02-28
> **hhacckerr said:**
> 
You also might be interrested in SSH tunnelling so that you can torrent on your school computer, without having to scp the files.
There is a really fast server for our branch also under fortiguard(the web filter) i used to use putty to tunnel and it worked but since the usage increased they have done something:P and firefox says that connection was reset.Could you plese tell what to do
The server runs ubuntu .

---

### Post by junke1990 on 2010-02-28
scan the server with nmap? preff with -A as param

---

