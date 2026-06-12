---
title: "Remote access to machine that is behind VPN"
date: 2012-09-08
forum: Security
---

### Post by joshmcc on 2012-09-08
Hi, I'm a relative beginner to Linux and Ubuntu so try to keep any replies easy to read :)

Also, I apologise if this thread is in the wrong place, but it seemed the best place I could find.

I plan to set up an always-on file server/bittorrent client at home, using a lot of help from this guide:
[http://ubuntuforums.org/showthread.php?t=1895084]("http://ubuntuforums.org/showthread.php?t=1895084") 

I'd like the server to be as secure as possible without being beyond my capabilities to set up, and the security measures outlined in this tutorial seem to be as much as I'll need.

However, I plan to also route all of the server's internet traffic through a  commercial VPN provider using OpenVPN for privacy and security issues.
What I'd like to know is, how does using a VPN in this way affect my ability to access the machine remotely?

I'd like to be able to control the server remotely from both inside and outside my home network, largely to access a GUI web interface or CLI for my chosen torrent client (probably either transmission or deluge) without compromising the VPN connection.

In other words, I'd like to be able to control the system remotely from outside my home, whilst ensuring that anyone else on the internet who connects to my server only sees the IP address provided by the VPN service.

Would this be achieved by simply setting the VPN service to forward certain ports that are being used for SSH access or the web interface of the bittorrent client or is there something else I'd need to do?

Apologies for the long-winded explanation but I just wanted to make myself as clear as possible.

---

### Post by Laiquendi on 2012-09-08
There may be some official way like establishing some secure forwarded connections, but to keep it simple I would use TeamViewer, with access code hard-set. It's free.

---

### Post by wacky_sung on 2012-09-08
I think i don't get what you meant by setup a BT server. First of all, are you going to use to BT server to serve on the Website which also run by you. If so, even you go behind a commerical VPN server, people are still able to trace you through your domain name. Otherwise most of the VPN server does not allow you to use their service running as a server which will cause overload to their server. Plus you may breach their terms and conditions serving pirated things.

Upon that, you actually do not need any BT server as BT has also introduce [magnet link]("http://news.softpedia.com/news/BitTorrent-Magnet-Links-Explained-132536.shtml") which do not need any server/site to serve the torrent file. Most [BT clients]("http://en.wikipedia.org/wiki/Comparison_of_file_sharing_applications") has also equipped with magnet link recognition.  

I strongly advise you to reconsider your intents.

---

### Post by joshmcc on 2012-09-10
> **wacky_sung said:**
> I think i don't get what you meant by setup a BT server. First of all, are you going to use to BT server to serve on the Website which also run by you. If so, even you go behind a commerical VPN server, people are still able to trace you through your domain name. Otherwise most of the VPN server does not allow you to use their service running as a server which will cause overload to their server. Plus you may breach their terms and conditions serving pirated things.

Upon that, you actually do not need any BT server as BT has also introduce [magnet link]("http://news.softpedia.com/news/BitTorrent-Magnet-Links-Explained-132536.shtml") which do not need any server/site to serve the torrent file. Most [BT clients]("http://en.wikipedia.org/wiki/Comparison_of_file_sharing_applications") has also equipped with magnet link recognition.  

I strongly advise you to reconsider your intents.

I'm sorry, I must have not been very clear. What I meant was to set up an always-on fileserver on my home network that is always running a bittorrent client. I'd like to tunnel the bittorrent traffic (or all traffic) through a VPN whilst still being able to remotely monitor downloads from outside my home network.

---

### Post by Stonecold1995 on 2012-09-11
> **joshmcc said:**
> I'm sorry, I must have not been very clear. What I meant was to set up an always-on fileserver on my home network that is always running a bittorrent client. I'd like to tunnel the bittorrent traffic (or all traffic) through a VPN whilst still being able to remotely monitor downloads from outside my home network.
So like, a seedbox, behind a VPN, being controlled through SSH?

---

### Post by joshmcc on 2012-09-11
> **Stonecold1995 said:**
> So like, a seedbox, behind a VPN, being controlled through SSH?

Exactly, only the machine would be running on my home network, rather than renting space on a remote seedbox. Ideally, I'd rather control it from a web GUI, such as that provided by transmission but if that's not possible when the machine is using a VPN or is less secure, then SSH would suffice.

---

### Post by wacky_sung on 2012-09-11
Actually it can be done but it need for you to do some work to configure it. Beside that, it also depend on how you wanna do it.

---

### Post by joshmcc on 2012-09-11
> **wacky_sung said:**
> Actually it can be done but it need for you to do some work to configure it. Beside that, it also depend on how you wanna do it.

Could you possibly elaborate on that please? I'm not sure exactly what you mean. perhaps point me in the direction or some useful information or guide?

---

### Post by wacky_sung on 2012-09-12
Use a free dns service such as [DNSdynamic]("http://www.dnsdynamic.org/") or others to run your dynamic ip to use a static domain name through your router. Then configure your remote login through SSH / others depending what is your preference. Even you went behind a VPN server and you are still able to remote login to your local system from outside.

Pardon me, i am too lazy to write down nor print screen to you steep by step. Do some reading and i am sure you will be able to do it.):P):P):P):P):P):P

---

### Post by joshmcc on 2012-09-12
> **wacky_sung said:**
> Use a free dns service such as [DNSdynamic]("http://www.dnsdynamic.org/") or others to run your dynamic ip to use a static domain name through your router. Then configure your remote login through SSH / others depending what is your preference. Even you went behind a VPN server and you are still able to remote login to your local system from outside.

Pardon me, i am too lazy to write down nor print screen to you steep by step. Do some reading and i am sure you will be able to do it.):P):P):P):P):P):P

I think I understand how to do that.
Are you saying that even if the machine sends all traffic over the VPN and blocks all other traffic, I'll somehow still be able to remote login to it?

---

### Post by wacky_sung on 2012-09-12
The VPN you using which you wanna remain anonymous while using your BT connection. Then the dns service configuration in your router is help you to remote login through SSH or others due to your dynamic ip.

---

### Post by joshmcc on 2012-09-12
> **wacky_sung said:**
> The VPN you using which you wanna remain anonymous while using your BT connection. Then the dns service configuration in your router is help you to remote login through SSH or others due to your dynamic ip.

Yes, but surely if I've set all traffic to go over the VPN, then when I try to remote login, the computer sees the traffic as not originating from the VPN and blocks it?

---

### Post by wacky_sung on 2012-09-12
> **joshmcc said:**
> Yes, but surely if I've set all traffic to go over the VPN, then when I try to remote login, the computer sees the traffic as not originating from the VPN and blocks it?

Then this is your firewall issues in which you need to configure it to allow the remote access.

---

### Post by daz1uk on 2012-09-14
Joshmcc, did you get anywhere with this, I'm trying to attempt a similar scenario, just without a seed box ;)

---

### Post by joshmcc on 2012-09-14
> **daz1uk said:**
> Joshmcc, did you get anywhere with this, I'm trying to attempt a similar scenario, just without a seed box ;)

Not yet :( this is really frustrating me! There must be a simple enough way to only route certain processes trough the VPN (i.e. transmission), or bypass the VPN on a per-port basis, such as the port assigned to SSH. 

So far the best solution I've found is to run the VPN client on a DD-WRT router and put the seed box behind this router. It would allow easy remote access from any computer using the same router, but wouldn't do anything to solve the problem of remote access when away from home.

---

