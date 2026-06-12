---
title: "Basic server setup advice"
date: 2011-11-16
forum: Server Platforms
---

### Post by Warthaug on 2011-11-16
My apologies if this is the wrong section of the forums for this.

I am a new immunology professor/scientist, and am in the process of setting up my first lab.  I've used ubuntu as a desktop system for 5+ years, managed a small ubuntu-based cluster for the past 3 (which I did not setup, btw), and as such am fairly familiar with ubuntu as a desktop environment.

As part of my lab setup process I am putting in place a minimal server.  The main purpose is file storage (we'll generate a few TB of data every year), but I also want a wiki (for experimental protocols) and backup capacity.  because there server will be lightly used (file storage/access being the major thing; with less than a dozen users), I was planning on using modest computer running ubuntu as a front-end, and rack-mounted RAID for expandable storage (i.e. devices like these):
[http://eshop.macsales.com/shop/hard-drives/RAID/Rack_Mount/FireWire_USB3_eSATA_1U](http://eshop.macsales.com/shop/hard-drives/RAID/Rack_Mount/FireWire_USB3_eSATA_1U)

The server will be managed primarily (hopefully solely) via remote desktop.

My goal for the server is fairly minimal; I want to:
1) Run a file server, accessed internally via SAMBA/CIFS
2) Provide external access to these files via SFTP or another protocol
3) Run a Wiki
4) Backup lab computers nightly to the server
5) Mirror the server nightly onto a secondary (backup) server

The actual amount of traffic will be quite small (a dozen or so users, maximum, accessing from a handful of computers).  I have been looking at some options, and aside from the backup portion, turnkey linux seems to be an easy way to get these things up and running.  That said, having never used turnkey before I am not certain this is the route I want to go.

So now for my questions:
1) Is turnkey the easiest way to implement this?  If not, what would you recommend?
2) Which "flavor" of linux would be best for the server (I was leaning to a less resource-hungry distro like xubutu or lubutu - I would like to keep the GUI, btw)?*
3) Does anyone know of a good guide to lead me through the general process of setting up a server with these types of capacities?
4) With turnkey, can multiple "units" be installed within the same server, or do I have to virtualize?**

EDIT: 
* This is only a concern if the answer to Q4 is that visualization is my only option

** Q4 was poorly written.  Turnkey is setup to be run as a VM, but I ***believe*** you can also install as a stand-alone OS.  If this is possible I was thinking it would be the better option because of my minimal needs.  But I still need two turnkeys - i.e. I'd have to somehow install both (i.e. install one; then add the packages for the second?), or install one and virtualize the second, or install a base OS and virtualize both (the later being how things are usually done).

Any other advice is appreciated

Thanx

Bryan

---

### Post by Dangertux on 2011-11-16
> **Warthaug said:**
> My apologies if this is the wrong section of the forums for this.

I am a new immunology professor/scientist, and am in the process of setting up my first lab.  I've used ubuntu as a desktop system for 5+ years, managed a small ubuntu-based cluster for the past 3 (which I did not setup, btw), and as such am fairly familiar with ubuntu as a desktop environment.

As part of my lab setup process I am putting in place a minimal server.  The main purpose is file storage (we'll generate a few TB of data every year), but I also want a wiki (for experimental protocols) and backup capacity.  because there server will be lightly used (file storage/access being the major thing; with less than a dozen users), I was planning on using modest computer running ubuntu as a front-end, and rack-mounted RAID for expandable storage (i.e. devices like these):
[http://eshop.macsales.com/shop/hard-drives/RAID/Rack_Mount/FireWire_USB3_eSATA_1U](http://eshop.macsales.com/shop/hard-drives/RAID/Rack_Mount/FireWire_USB3_eSATA_1U)

The server will be managed primarily (hopefully solely) via remote desktop.

My goal for the server is fairly minimal; I want to:
1) Run a file server, accessed internally via SAMBA/CIFS
2) Provide external access to these files via SFTP or another protocol
3) Run a Wiki
4) Backup lab computers nightly to the server
5) Mirror the server nightly onto a secondary (backup) server

The actual amount of traffic will be quite small (a dozen or so users, maximum, accessing from a handful of computers).  I have been looking at some options, and aside from the backup portion, turnkey linux seems to be an easy way to get these things up and running.  That said, having never used turnkey before I am not certain this is the route I want to go.

So now for my questions:
1) Is turnkey the easiest way to implement this?  If not, what would you recommend?
2) Which "flavor" of linux would be best for the server (I was leaning to a less resource-hungry distro like xubutu or lubutu - I would like to keep the GUI, btw)?*
3) Does anyone know of a good guide to lead me through the general process of setting up a server with these types of capacities?
4) With turnkey, can multiple "units" be installed within the same server, or do I have to virtualize?**

EDIT: 
* This is only a concern if the answer to Q4 is that visualization is my only option

** Q4 was poorly written.  Turnkey is setup to be run as a VM, but I ***believe*** you can also install as a stand-alone OS.  If this is possible I was thinking it would be the better option because of my minimal needs.  But I still need two turnkeys - i.e. I'd have to somehow install both (i.e. install one; then add the packages for the second?), or install one and virtualize the second, or install a base OS and virtualize both (the later being how things are usually done).

Any other advice is appreciated

Thanx

Bryan

I really hate to answer your very detailed questions with a short answer, however in my opinion this is what I would do.

1 - Turnkey is pretty simple and is a standalone distro, you can virtualize it or install it on bare metal. Each module can be added as necessary so I'm not sure why you'd need more than one.

2 - I wouldn't recommend turnkey, it seems a little overkill since you're saying you only need a few services, a standard Linux system would be sufficient. I would actually recommend Ubuntu 10.04 LTS or Debian since you are already familiar. If you wanted to learn something new I would recommend CentOS. 

3 -That being said here is the server guide for 10.04 : [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

The tips there could be followed on a desktop installation as well if you want to maintain a GUI, though ultimately the learning curve on what you're trying to do is not that hard, and since you're wanting to use a modest system I would just forgo the GUI for now and learn the CLI. It shouldn't be that difficult.

4 - I pretty much answered this in 1 and 2 but no you don't have to virtualize.

Hope this helps.

---

### Post by 2F4U on 2011-11-16
If you want to run a server, I would suggest you use a server distribution. Besides CentOS and ScientificLinux, there is also a Ubuntu Server edition.

[http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download)

If you are serious about your server and intend to use Ubuntu Server, I would recommend the LTS version,

---

### Post by boast on 2011-11-16
First, [http://www.howtoforge.com/](http://www.howtoforge.com/) has a lot of good setup guides for servers and stuff. 

Second, are you sure about installing a "GUI" on the server? I would try and avoid it. If it is for administration purses, web interfaces like "webmin" are better.

My recommendation would be to install CentOS (and then disable the SELinux and the firewall for now).

Is the lab linux or windows computers?

Are there going to be logins for each individual users, or anyone with access to the lab computers should be able to access shared directories on the server?

---

### Post by Warthaug on 2011-11-16
Thank you everyone for your rapid replies.  I should have been more clear as to why I wanted this somewhat "non-standard" server setup.

The reason for maintaining a GUI is simply because I am far too busy to maintain the server, and as such need a system that any modestly competent student can go into and start/stop services, manage users, update, etc.  Between teaching and maintaining my lab I simply don't have the time myself, and since the student segment is fairly fluid, I also won't have a full-time, long-term individual who can run it.  Ergo easier = better, even if it means a bit more resource consumption.  GUI= easy in most circumstances.

As for the lab itself, its mostly windows due to application requirements; many of the proprietary programs we use are windows only and lack linux/opensource alternatives.  The only exception to that is our matlab workstation, which runs linux (and the server, once up and running).  That said, students bring into the lab their own laptops, so a few macs are kicking around as well.  This is why I wanted to use the Samba/CIFS file server; most (all?) OS's can connect.

I haven't decided about multiple users as yet.  On the FTP end there will be at least 2 users - lab members (who would have access to the entire data directory) and a "collaborators" account who would have access to only one sub-directory.  I do like the idea of individual accounts for everyone (for security, and the ability to specifically lock out one unhappy individual without forcing everyone else to learn a new password), but I'm worried the managerial overhead may become excessive.

In response to DangerTux specifically, I'm happy to hear individual modules of turnkey can be installed side-by-side without virtualization.  While overkill for my purposes, I've gravitated that way due to the simplicity of setup & operation that turnkey offers.  As I said above, I'm looking for as easy an implementation as possible, and turnkey seems to offer just that.  Please correct me if I am wrong about that.

Thanx again,

Bryan

---

### Post by drdos2006 on 2011-11-16
If you want a GUI on the server then check out Zentyal.

Zentyal will get your machine running in your environment while you learn the more detailed operations of a server. [http://www.zentyal.com/](http://www.zentyal.com/)

Here is a HOWTO which I found comprehensive and invaluable as a server novice. Uses Webmin to allow your browser to connect and modify your server settings.  You can also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

