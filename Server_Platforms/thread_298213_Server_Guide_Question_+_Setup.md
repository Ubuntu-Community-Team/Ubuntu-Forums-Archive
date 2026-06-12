---
title: "Server Guide Question + Setup"
date: 2006-11-12
forum: Server Platforms
---

### Post by FrozenPixel on 2006-11-12
So far the guide seems to be pretty straight forward but is there a guide for setting up the server from start to finish for a first time user? Right from the beginning it states that they assume the users using the guide have a working knowledge of Ubuntu.

At the moment all I am trying to do is have a Windows user log in and have access to their respective directory and authenticate through a domain. So of course I would have to configure DHCP and install SAMBA and configure it, that I am pretty sure about.

I'm not interested in any internet access at this time, I will add features once I have set up the basic network.

To this point all I have done is install the LAMP option on 6.06 server, connected the server to a router(disabled DHCP on that unit and connected the windows user to the router as well so the wiring portion is in place.

Should I now go through the procedure of installing DHCP, configure etho0, and install and configure SAMBA?

If I am on the right track or out in left field please leave any comments or suggestions where to proceed.

Thanks for your patience.:-k

---

### Post by elst on 2006-11-12
Yes, you need Samba for this. The "samba-swat" package adds a Web interface for configuring and managing Samba - if you point your Web browser to port 901 of the server you can then set it up from there.

You only need one DHCP provider on the network, so if you have a router or similar you don't need to install a DHCP service on Ubuntu.

If Ubuntu seems like overkill for your needs, it may be worth considering that specialized distributions exist to convert PCs into dedicated routers or network storage appliances, so you don't necessarily have to learn Linux to setup basic servers.

---

### Post by FrozenPixel on 2006-11-12
Thank you. What I am trying to accomplish is mimic our server at work so in case something goes wrong I have an idea of where to look, so hence the DHCP server, if I had a hub I would use that but I just disabled the routers DHCP service so I can set it up. I'm just beginning since I don't want to look like a dufus when they look at me to help on the network.

Theres a browser in the server version, I thought it was command line?

---

### Post by elst on 2006-11-12
Ahh, I see. FWIW, I'm a big fan of virtualization, and do all my experimenting on VMware virtual machines. The snapshot/rollback facilities can be a real time-saver. The Workstation edition simulates complete networks as well individual machines.

The most complete Linux server guide that I know of is RUTE, which actually complies with the LPI curriculum spec. You can get it online, or install it on Ubuntu with the "rutebook" package, and read it by pointing a browser at /usr/share/doc/rutebook/html/index.html.

IIRC, the Web browser on Ubuntu Server is a text-mode browser. It looks a bit odd, but it lets you access HTML files and Web applications from the server itself without needing another system around.

---

### Post by FrozenPixel on 2006-11-12
Ah thanks elst, will go have a look.

---

### Post by FrozenPixel on 2006-11-12
I tried to install SAMBA by executing the command:

sudo apt-get install SAMBA

But it ends up asking:

Media change: please insert the disc labeled 'Ubuntu-Server 6.06.1 _Dapper Drake_ -Release i386 (20060807.1)'

I put in the disc I created from the ISO but that doesn't help. I searched for this problem and I understand it being a problem if I don't have an internet connection but I was able to ping yahoo.com
succesfully.

Should it just install everything off the internet anyway and not ask for any cd?

---

### Post by elst on 2006-11-12
You'll need to edit the /etc/apt/sources.list file. By default Ubuntu uses the CD as a package source to avoid unnecessary downloads, but you can disable that (by adding a # comment marker in front of the relevant line in the file). The sources.list file also defines the network/Internet repositories that your system will use for all software operations.

---

### Post by FrozenPixel on 2006-11-12
Ok so I can just execute:

sudo nano /etc/apt/sources.list


Will waiting I thought maybe the apt-get and aptitude were too old so I executed:

sudo apt-get update
sudo aptitude update

So I'm just waiting for aptitude to do its thing.

Thank you

---

### Post by FrozenPixel on 2006-11-12
Oh man your so clever elst, thanks. It worked perfectly. 

So I take it that its a bit of a safety concern so I will return the source file back to its original version including the CD.

---

### Post by elst on 2006-11-12
Everything I know I learned by reading what smart people put on the Internet :).

Use "sudoedit" to automatically open a file in the default text editor with root privileges:

sudoedit /etc/apt/sources.list

The use of the network repositories isn't unsafe as such - all Ubuntu packages are digitally signed. It can be more convenient to use the CD, though, especially with low-bandwidth connections.

It's also kinder to the overworked Web servers to not download packages when you already have copies. Most managed networks maintain their own local package repositories, and so only ever pull packages from the main repositories once.

---

