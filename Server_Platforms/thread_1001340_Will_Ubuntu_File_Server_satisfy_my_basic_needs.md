---
title: "Will Ubuntu File Server satisfy my basic needs?"
date: 2008-12-03
forum: Server Platforms
---

### Post by Mr_Pacman on 2008-12-03
Hi there,

I was hoping someone could answer my basic question. 

I have a extra laptop kicking around, and what I want to be able to do is plug it into my router at home and store all of my files on it. I don't want to use this machine for anything other than file storage (I have another laptop that I use daily).

I would like to be able to access the files on the "file storage laptop" remotely. So if I'm in California and want to access my files on the laptop at home, I can do so in a secure manner.

My friend was telling me about setting up my laptop with VMWare and to use it as a file server, but I was wondering if the Ubuntu File Server edition would work as well?

I'm running the regular Ubuntu on my daily work machine and prefer it over using any microsoft windows products.

Will the Ubuntu file server allow me to set up my extra laptop as a file server and allow me to access the files stored on it via anywhere in the world as long as I have an internet connection?

Any input would be greatly appreciated.

Thanks
James

---

### Post by Joel Duckworth on 2008-12-03
Sure Ubuntu server or desktop edition could do this for you, but the question is how are you going to access them remotely from the internet? ssh, web, vpn?

Probably the easiest way would be to do it via ssh, but you would also have to open port 22 on your router and forward that to the IP of the laptop. You'd also want to make sure that your IP on the machine is static or reserved in your router so that it won't change IP's and invalidate the port forwarding. 

To enable ssh access you just need to install the openssh-server package.

Then to access your files from anywhere on the internet you would just have to know the IP of your router at home (which may be static or dynamic) and ssh into it. By either command line or by going Places > Connect to Server... from Ubuntu desktop.

Hope that helps.

---

### Post by Mr_Pacman on 2008-12-03
Thanks for the reply Joel,

So, just to clarify, it doesn't matter if I'm using the standard Ubuntu or the "file server" edition?

regards,
James


> **Joel Duckworth said:**
> Sure Ubuntu server or desktop edition could do this for you, but the question is how are you going to access them remotely from the internet? ssh, web, vpn?

Probably the easiest way would be to do it via ssh, but you would also have to open port 22 on your router and forward that to the IP of the laptop. You'd also want to make sure that your IP on the machine is static or reserved in your router so that it won't change IP's and invalidate the port forwarding. 

To enable ssh access you just need to install the openssh-server package.

Then to access your files from anywhere on the internet you would just have to know the IP of your router at home (which may be static or dynamic) and ssh into it. By either command line or by going Places > Connect to Server... from Ubuntu desktop.

Hope that helps.

---

### Post by Joel Duckworth on 2008-12-03
Nope, actually unless you're quite used to using just a command prompt to do everything on the system, I'd stick with the desktop edition.

---

### Post by highfructose327 on 2008-12-05
Mr_Pacman, 
I use ssh with  my home server and laptop when I am out of town, it works great for me.  The three links talk about setting up and using ssh, sshfs and ddclient. If you look around the forums and Google there is quite a bit of info on ssh and Ubuntu file servers.  I have been quite happy using ssh. 
Good luck.


[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html]("http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html")

[http://www.ubuntugeek.com/update-ip-addresses-at-dynamic-dns-services-using-ddclient.html](http://www.ubuntugeek.com/update-ip-addresses-at-dynamic-dns-services-using-ddclient.html)

---

### Post by wkitty42 on 2008-12-06
> **Joel Duckworth said:**
> Probably the easiest way would be to do it via ssh, but you would also have to open port 22 on your router and forward that to the IP of the laptop.

FWIW: you don't have to open up port 22... you can easily use another port and forward that to port 22 on the internal machine... in fact, this is how you have to do things if you have multiple machines behind your protection that you want to SSH into...

i won't even mention that this is also one of the most safe things to do because most of the SSH attacks out there specifically target port 22 on the WAN facing box and don't even bother to try any other ports ;)

---

