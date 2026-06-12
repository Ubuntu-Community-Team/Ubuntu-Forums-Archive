---
title: "First Ubuntu Home File Server: Plan of Attack"
date: 2008-11-16
forum: Server Platforms
---

### Post by falconed7 on 2008-11-16
Hey everyone!

I'm currently setting out a plan which will hopefully help me on my first home Ubuntu server (8.04.1 LTS) build.

What I would like from the server is:
[LIST]
[*]File storage (with access from the network and also over the internet, probably from uni)
[*]Stream media to my PS3
[*]Back-up files to my external HDD every 2 days or so
[/LIST]

I think I know most of the things I should install and the order I should set up the server:
[LIST=1]
[*]Obviously boot from the CD and follow the installation
[*]Configure partitions (stuck on this the most)
[*]Install OpenSSH and Samba (do I need anything else? DNS server, LAMP?)
[*]Configure network settings
[*]Install webmin (required to work with dyndns due to only having a dynamic IP)
[*]Install/configure rsync
[*]Install/configure Mediatomb
[*]Install/configure torrent client (which one?)
[/LIST]

So that's basically the steps I think I will need to take in order. Do you think I should change anything? And when should I install a firewall?

My main questions are:
- I have a 80GB and 750GB drive. I am planning to install the OS on the 80GB (one big partition) and use the 750GB for storage (possibly split into 3 partitions). Should I use the manual partitioning setup or the guided?
- In terms of setting up webmin and dyndns should I use the 'setup Dynamic DNS Service' in my router or just use a dynamic IP updating client on the server?
- In terms of remote access (overseas/uni) can I use webmin to access/upload files on my server?

Any help is greatly appreciated!
Cheers.

---

### Post by features on 2008-11-16
Hi,

I can't really help you with the network config:  I have a similar setup, but I haven't configured it for DynDNS, so it would be like the blind leading the blind.  BUT, I have a couple of recommendations that you might like to look at:

[LIST=1]
[*]dnsmasq (combined DNS and DHCP - can be used with DynamicDNS too, AFAIK.  See above ;) )
[*]torrentflux (web based bittorrent administration - it rocks!)
[*]backuppc (web based backup admin - can use rsync, powerful, but a bit of a pain to configure. )
[/LIST]

All of these are available in the repos.

Hope some of this is helpful.

Mark

---

### Post by falconed7 on 2008-11-16
Thank you for the reply.

I'll definately check out those 3 things now. I just hope the whole thing isn't a pain to configure, and considering it's my first go at ubuntu server (and I've only really used Ubuntu desktop for about 3 weeks) then it could turn out that way.

I'll go through that howtoforge guide and come here for any help!

Also if anyone has any input on my other questions it would help a lot.
Thanks.

---

### Post by falconed7 on 2008-11-16
I just came across eBox as a replacement for webmin.

Which one is better to use?

---

### Post by mike010 on 2008-11-18
i am a fan of eBox myself just seems to have worked better when i tried it...

---

### Post by falconed7 on 2008-11-19
> **mike010 said:**
> i am a fan of eBox myself just seems to have worked better when i tried it...

Thanks. It seems after reading the documentation of the two, Ubuntu supports eBox more.

Does any one know how I should setup a 80GB and 750GB HDD? Excuse my ignorance but should I plug both HDDs in (80GB as master - for OS; 750GB as slave - for data) and set them up via the 'manual' partitioning option in the Installation?

---

### Post by hyper_ch on 2008-11-19
Let me give you some general thoughts on the various points you raised:

(1) Partitions
The planing of partitions and how to setup the system is rather important. It gets the more important the longer you want to work under that established system. The last few days I have bothere jdong (Forum Admin) quite a lot on IRC about those things.
A few things that I considered are: (a) in case of a harddisk fail, how quickly do I need to get it up and running again (b) in terms of "drive space" do I need an unlimited partition (c) in terms of security, do I need to protect against unauthorized physical access?

(a) With a (software) raid setup you can make automatic mirror of harddisks. However the more raid you use, the more harddisks you need. For that small business where I plan to setup the server it is of importance to not have much downtime so I will setup there a raid1.

(b) This far disk usage is in that business not that important. In the last 5 years they accumulated just about 40gb of data (mostly docs and pdfs). So todays drives are by far large enough. However if you want to store lots of music and videos on there, you might want to consider a LVM setup.

(c) Just in case anyone ever breaks in I will setup a full disk encryption there.

(2) DNS Server
If you want to be able to access the server with the same address from inside and outside your network then you should setup a dns server.

(3) Dyn IP address
I'd suggest you set this up on the router and not on the server. Basically you just need to enter there your account details and every once your IP changes it will notify the dny ip service.

(4) rsync
Backups are important. Raid1 is also a "backup" already. However I prefer also to have a remote backup - you know, in case there's a fire and you have all backups in one place then you lose all your data. For me personally I setup a small server at my parents' home to which I rsync my documents and pictures. I don't backup movies and stuff there - as I don't see any importance to do so.

(5) torrent
I'd suggest you use rtorrent. It's a CLI based torrent and it's not really complicated. You can access is nicely through ssh from everywhere. There are also webinterfaces available for it. It's very light on system resources yet powerful.

(6) remote file access
When you setup a ssh server anyway, you want to you sshfs from overseas/uni. sshfs will allow you to mount a drive/folder no your server into your local filesystem. The connection is secured and encrypted by ssh.

---

### Post by falconed7 on 2008-11-19
> **hyper_ch said:**
> Let me give you some general thoughts on the various points you raised:

(1) Partitions
The planing of partitions and how to setup the system is rather important. It gets the more important the longer you want to work under that established system. The last few days I have bothere jdong (Forum Admin) quite a lot on IRC about those things.
A few things that I considered are: (a) in case of a harddisk fail, how quickly do I need to get it up and running again (b) in terms of "drive space" do I need an unlimited partition (c) in terms of security, do I need to protect against unauthorized physical access?
[...]
(2) DNS Server
If you want to be able to access the server with the same address from inside and outside your network then you should setup a dns server.

(3) Dyn IP address
I'd suggest you set this up on the router and not on the server. Basically you just need to enter there your account details and every once your IP changes it will notify the dny ip service.
[...]
(6) remote file access
When you setup a ssh server anyway, you want to you sshfs from overseas/uni. sshfs will allow you to mount a drive/folder no your server into your local filesystem. The connection is secured and encrypted by ssh.

Your post is extremely helpful! You answered almost everything I was curious about.

**(1) Partitions**

In terms of partitions, If a HDD fails I wouldn't be too stressed about getting the system back up quickly (if I have back up my files). And at the moment I really don't see myself exceeding 400GB let alone 750BG in the foreseeable future. Is it realtively easy to add another HDD when needed (without the use of software RAID1)?

I am considering software RAID1 (80GB - OS; 2 x 750GB - in RAID1), however, for myself I think a back up of the important files to an external HDD will be sufficient.

**(2)+(3) DNS server + Dynamic IP address**

This is probably what I'm most confused about. If I maybe set it out in steps it may help:
1. Upon startup I'm aware that Ubuntu sets up connect via DHCP. Several guides I have read tell me to set up a static IP. I assume this means reserve an IP address for the server itself within the router?
2. Sign up for a dyndns.com domain and place the settings in my router under 'Use a Dynamic DNS Service' and this will automatically detect me IP address and change it accordingly.
3. Next step? 

Am I missing any steps there or have I gotten any wrong?

**(6) Remote file access**

Does OpenSSH come with a simple to use web interface?

Once again thank you for the elaborate description of everything.

---

### Post by hyper_ch on 2008-11-19
> **falconed7 said:**
> **(1) Partitions**
In terms of partitions, If a HDD fails I wouldn't be too stressed about getting the system back up quickly (if I have back up my files).
If you don't need it up again asap after something fails and you have time to setup the system completely again, then you probably don't need raid... it's a personal choice. For that small business I setup raid1 so if sda fails, then someone in the small business can just open the server, unplug sda, and boot up the server again - of course at some later time sda will then be required to be replaced... but for a few days it will be ok.

> **falconed7 said:**
> **(2)+(3) DNS server + Dynamic IP address**
This is probably what I'm most confused about. If I maybe set it out in steps it may help:
1. Upon startup I'm aware that Ubuntu sets up connect via DHCP. Several guides I have read tell me to set up a static IP. I assume this means reserve an IP address for the server itself within the router?
2. Sign up for a dyndns.com domain and place the settings in my router under 'Use a Dynamic DNS Service' and this will automatically detect me IP address and change it accordingly.
3. Next step?
Well, as you are behind a router it means you have to "consider" two ip addresses.

You have a public IP address. This is the one your ISP assigns to your cable/adsl/...-modem. Most ISPs offer for an additional charge also static (permanent) IP addresses but it seems not to be a need in your case.
The router then translates requests coming from the public IP into the internal lan. By default you very likely are adressed ip ranges of 192.168.1.X or 192.168.1.X where your router normally has the IP of 192.168.0.1 or 192.168.1.1.
So when you want to offer services from within your lan also to the outside, then you need to setup a portforwarding.

E.g. direct all incoming webserver requests (port 80) from the internet to the lan machine with IP XXX.XXX.XXX.XXX (server). In that case you should assign your server a static IP address (there are other ways around but static IP is the simplest).

I personally setup on the router that DHCP is offered from xxx.xxx.xxx.20. This means I have 18 "static" IPs at my disposal (because xxx.xxx.xxx.1 is normally the router). You could then setup for example the server as xxx.xxx.xxx.2, your network printer as xxx.xxx.xxx.3, .... and DHCP clients will get assigned IP addresses automatically starting at .20.

As you said you want also to access the server by ssh you will also need to forward port 22 to your server.

When you're then at university you can then contact your server by just entering [http://MYDYNDNSNAME.dyndns.org](http://MYDYNDNSNAME.dyndns.org) (or whatever dyn ip server you use). The rest of your steps are correct - you only have to check what dyn ip service your router supports by default.

Equally you could then access your server through ssh by:
```

ssh USERNAME@MYDYNDNSNAME.dyndns.org

```
The dyn IP service will then translate the MYDYNDNSNAME.dyndns.org to your current ip address.


> **falconed7 said:**
> **(6) Remote file access**

Does OpenSSH come with a simple to use web interface?

openssh-server will setup a ssh server. This means you can connect to the server through ssh and act as if you are on that machine (e.g. you can run updates, install software, ...). It is a terminal interface (see above how to connect to it. "USERNAME" is the user on the server into which you want to log into).

SSH will just build a secured terminal session betwenn the computer you are using and the destination computer (server). However it can be expanded by using sshfs for example. SSHFS will give you the ability to mount a server folder into your local computer. You see it then as part of your computer. You can put on files, you can delete files (however up/download of large files will be slow - according to your internet connections).

---

### Post by falconed7 on 2008-11-19
> **hyper_ch said:**
> openssh-server will setup a ssh server. This means you can connect to the server through ssh and act as if you are on that machine (e.g. you can run updates, install software, ...). It is a terminal interface (see above how to connect to it. "USERNAME" is the user on the server into which you want to log into).

SSH will just build a secured terminal session betwenn the computer you are using and the destination computer (server). However it can be expanded by using sshfs for example. SSHFS will give you the ability to mount a server folder into your local computer. You see it then as part of your computer. You can put on files, you can delete files (however up/download of large files will be slow - according to your internet connections).

Would this be easy to operate for family members? And can I create user accounts for SSH with different privileges (ie. So family members don't break the server)?

---

### Post by Iowan on 2008-11-19
SSH is just a secure login, so if you set up accounts for family members, they have only the permissions they would have if logged in directly from the console.

---

### Post by neomaximus2k on 2009-01-15
I already have this kind of server setup at home along with a few extras, I have written a word document detailing the instructions and steps to be taken.

I'm looking at securing the system at present as it is fairly open however if you want the word document drop me a line.

---

### Post by hyper_ch on 2009-01-15
why not making it a howto and put it onto the forums?

---

### Post by kennyschiff on 2009-01-17
I wouldn't mind seeing your Word doc... can you email it to me: kenny at 3schiffs dot com

---

### Post by likebikes on 2009-01-21
> **neomaximus2k said:**
> I already have this kind of server setup at home along with a few extras, I have written a word document detailing the instructions and steps to be taken.

I'm looking at securing the system at present as it is fairly open however if you want the word document drop me a line.
Wouldn't mind a look at this document to please?

---

