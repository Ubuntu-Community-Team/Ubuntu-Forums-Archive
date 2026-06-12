---
title: "Home server"
date: 2008-08-22
forum: Server Platforms
---

### Post by Tom--d on 2008-08-22
Hello,

I want to set up a home server for my home xD
All I want it to do is hold files. have computers on the network access to them. Thats all.
but I would love to monitor it and use it through VPN (i think thats it).
So that means I dont have to have a mouse/keyboard/monitor. Right?

Basically. I can have the laptop use the computer over the network and take FULL control of it.

Please help me on this.
Like were do I start?

Thanks
Tom

---

### Post by Mrwasab1 on 2008-08-22
This basic setup will do everything you just asked for.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

wont need to VPN, as you can use SSH.

---

### Post by az on 2008-08-22
You don't even need to install any "server" software on it other than ssh.

Install a base system (or a Desktop) and install the ssh package.  Route port 22 to your "server" and you will be able to log into your server from the net.  On a windows computer, use Putty to log in or filezilla to transfer files using ssh.

On a linux box, use the terminal to log is and use nautilus to transfer files.

---

### Post by windependence on 2008-08-23
> **Mrwasab1 said:**
> This basic setup will do everything you just asked for.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

wont need to VPN, as you can use SSH.

That might be a bit much for what he needs.

I would load Ubuntu server and install Samba and you should be good to go. OpenVPN if you need VPN access.

-Tim

---

### Post by thefekete on 2008-08-23
> **Tom--d said:**
> 
So that means I dont have to have a mouse/keyboard/monitor. Right?

My home server just has the power cord and a network cable attached. Your best bet is ubuntu server with ssh and samba servers installed (these can be selected during the install).

The only times you will need a keyboard/monitor/mouse is when things go [horribly wrong]("http://ubuntuforums.org/showthread.php?t=892281").

-dan

---

### Post by mellowd on 2008-08-23
If you're going to accessing it from your laptop, don't bother installing any gui.

Install the server platform, get ssh working and you're pretty much done (you can lock it down later)

To share files to your laptop set up samba (if you're using windows on that desktop)


make sure your router forwards the correct ssh port to your server, and then you'll be able to ssh in and do what you want from anywhere in the world

---

### Post by Tom--d on 2008-08-24
> **mellowd said:**
> If you're going to accessing it from your laptop, don't bother installing any gui.

Install the server platform, get ssh working and you're pretty much done (you can lock it down later)

To share files to your laptop set up samba (if you're using windows on that desktop)


make sure your router forwards the correct ssh port to your server, and then you'll be able to ssh in and do what you want from anywhere in the world

I'm not using Windows. I want Linux on it.
Also, its just for my Network. Nothing else. Not to the outside world.

---

### Post by Iowan on 2008-08-24
If you are asking about a remote desktop, I found [this]("http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/") article.

---

### Post by Krupski on 2008-08-25
> **Tom--d said:**
> Hello,

I want to set up a home server for my home xD
All I want it to do is hold files. have computers on the network access to them. Thats all.
but I would love to monitor it and use it through VPN (i think thats it).
So that means I dont have to have a mouse/keyboard/monitor. Right?

Basically. I can have the laptop use the computer over the network and take FULL control of it.

Please help me on this.
Like were do I start?

Thanks
Tom

It sounds like you want to build exactly the same kind of boxes I build (Network Attached Storage with just a power cord, a network cable, big hard drives in a RAID config, available on the network at a network share and remote administered via SSH and a terminal console [text, not GUI]).

If so, let me know and I'll tell you, step by step, what you need to do.

-- Roger

---

### Post by troutbum13 on 2008-08-25
If all you want to be able to do is access file shares on this machine,run samba or NFS (samba will allow windows users to browse to the share). I use NFS to serve files to my linux clients.

It sounds like you want to run this box headless and remote admin the machine, you have several options, if you are comfortable with CLI, use SSH you will install SSH on the server and then connect from your client command line.

you can install webmin, it is a web front end that will let you perform alot of admin functions from a web browser, you install it on the server and then connect from a client using the [https://yourserverIP:10000](https://yourserverIP:10000)

You can do a GUI install on the server and and remote into the server and have access to the the full desktop

hope that helps, SSH is the simplest way to do it, but you've got to feel comfortable at the CLI, or look into X11 forwarding. If you want ease of use go webmin.

---

### Post by Tom--d on 2008-08-26
I was thinking GUI but do I really need it?
And yes, I'm comfortable using the CLI :)

---

### Post by mellowd on 2008-08-26
> **Tom--d said:**
> I was thinking GUI but do I really need it?
And yes, I'm comfortable using the CLI :)

Don't bother with a gui! :)

---

### Post by Vivaldi Gloria on 2008-08-26
> **Tom--d said:**
> I was thinking GUI but do I really need it?
And yes, I'm comfortable using the CLI :)

No gui is better.

Also, you may not need the server cd. See the first link in my sig.

If you have windows computers on the network install samba to share folders. If you have only linux computers then I suggest you use sshfs. Read my posts here:

[http://ubuntuforums.org/showthread.php?t=894377](http://ubuntuforums.org/showthread.php?t=894377)

---

### Post by modzso on 2008-08-26
Hi!

I've just installed ubuntu server on a spare machine. 
It seems working fine. But I can't ssh from my desktop (Window XP) using Putty. What should I do? 
I am able to connect through samba, but also can't connect to mysql.

Thanks in advance,
Modzso

---

### Post by flatline on 2008-08-26
have you made sure ssh is installed/turned on?

try:

```
sudo apt-get install ssh
```

See this for a reference: _[http://element14.wordpress.com/2006/12/18/how-to-install-and-use-ssh-server-on-ubuntu-610/](http://element14.wordpress.com/2006/12/18/how-to-install-and-use-ssh-server-on-ubuntu-610/)_

---

### Post by modzso on 2008-08-26
> **flatline said:**
> have you made sure ssh is installed/turned on?


yes, I've installed OpenSSH. And I am able to login from localhost.

---

### Post by modzso on 2008-08-26
> **modzso said:**
> yes, I've installed OpenSSH. And I am able to login from localhost.

Sorry, I've misstyped the ip address.
Now with the correct address I am able to login.
Sorry again.

---

### Post by troutbum13 on 2008-08-31
> **Vivaldi Gloria said:**
>  If you have only linux computers then I suggest you use sshfs. 

I use sshfs over the WAN, but if you are on a secure LAN, it seems like nfs would be faster with less overhead? Do you use sshfs on your local network?

---

### Post by Vivaldi Gloria on 2008-08-31
> **troutbum13 said:**
> I use sshfs over the WAN, but if you are on a secure LAN, it seems like nfs would be faster with less overhead? Do you use sshfs on your local network?

Yes, I use sshfs in LAN. I find it fast enough. Probably disk speed is the limiting factor when it comes to speed in LAN rather then the encryption speed (depends on cpu) or the network bandwidth. But I'm just making a guess here. I wouldn't mind reading some benchmarks though.

---

