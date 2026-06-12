---
title: "Remote access"
date: 2021-08-19
forum: Ubuntu, Linux and OS Chat
---

### Post by peter-1984 on 2021-08-19
Hi,
What is the good way to remotely access machine with Ubuntu 18.04 version?

---

### Post by scorp123 on 2021-08-19
SSH

[https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/]("https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/")

---

### Post by sudodus on 2021-08-19
> **scorp123 said:**
> SSH

[https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/]("https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/")

+1 I agree. Use ssh, make it an ssh server by installing the package openssh-server

---

### Post by &amp;KyT$0P# on 2021-08-19
> **peter-1984 said:**
> Hi,
What is the good way to remotely access machine with Ubuntu 

Remotely access for what?

> **scorp123 said:**
> SSH

+1

If SSH doesn't by itself provide what you need, you can tunnel something else through SSH for added security.

---

### Post by peter-1984 on 2021-08-19
Hi,
To be able to access the machine via SSH, the machine should be with one public IP, right?

Other than SHH, is there any other way to remotely access Ubuntu server?

---

### Post by zebra2 on 2021-08-20
All internet devices have a local Ip and a network IP.  If you want ssh over the net to be comfortable you would need a static IP. That can be pricey in todays world because of the vast number of users. That is why there are other options such as Teamviewer, but a dynamic Ip can still be used so long as you know what the current IP of the remote actually is. It will usually float between a range on the domain but will stay the same so long as  the remote hasn't been rebooted and of course could still be the same even if it is. If you want to use a point and click utility with the ssh tunnel Remina would be the common choice. I only use ssh locally but at least locally you can install the ssh server on both ends. I just use it for file sharing, I you have two computers and wifi it would be easy to setup on your local network just to learn the nuts and bolts.

---

### Post by TheFu on 2021-08-20
> **peter-1984 said:**
> Hi,
To be able to access the machine via SSH, the machine should be with one public IP, right?

Other than SHH, is there any other way to remotely access Ubuntu server?

Since Linux Servers don't have GUIs, ssh is the only real solution.
This is a solved problem and ssh is extremely convenient AND considered secure when ssh-keys or ssh-certs are used.

There are lots of other ways, but they are all non-secure. That means they shouldn't be used, EVER.

A public IP is only necessary if the computers involved aren't on the same network and have to traverse part of the internet.  Actually, the "server" doesn't necessarily need a public IP, but the WAN router will need to have some port opened and forwarded to the LAN IP of the ssh-server.

---

### Post by DuckHook on 2021-08-20
> **peter-1984 said:**
> Hi,
To be able to access the machine via SSH, the machine should be with one public IP, right?
If by "one public IP", you mean a static IP, then the answer is:

Not necessarily, but the workaround is not trivial.

A technology exists called Dynamic Domain Name System (DDNS). Basically, you set up your router so that it pushes its current WAN address to a central server, especially whenever the WAN address changes. Should you wish to access your server from the internet, you do not go directly to your ever shifting IP. Instead, you point your app/session to the domain name assigned by the DDNS service. This service then relays your DNS query to your current IP address. The technical details are more involved and beyond the scope of a forum like ours. Here's a resource that explains the workings of DDNS: [https://www.howtogeek.com/66438/how-to-easily-access-your-home-network-from-anywhere-with-ddns/](https://www.howtogeek.com/66438/how-to-easily-access-your-home-network-from-anywhere-with-ddns/)
> Other than SHH, is there any other way to remotely access Ubuntu server?
In the interest of strictly answering your question, there are lots of alternatives to SSH, but they are almost all bad. There's plain old Telnet. Only a fool would install it because it is so broken that it is a security joke.

It may be presumptuous of me, but I sense a Windows user here who is used to doing things the GUI way and may be allergic to the command line. I do understand the sentiment: when I was starting out, the command line was dreadfully intimidating. It took me a long time to deal with the learning curve. But once mastered, there was no going back. It is orders of magnitude more versatile and more powerful. However, I have not forgotten the need for some hand&#8209;holding and a known anchor&#8209;point when first starting out. In that spirit, I hesitantly point you to Webmin: [https://webmin.com/](https://webmin.com/)

The reason I'm so hesitant making this recommendation is that most users will quickly proceed to install this package without the slightest regard for safety or security. Frankly, running it without tunnelling through a SSH tunnel is almost as dumb as installing Telnet. But if you tunnel properly, then you are already SSH&#8209;ing anyway, so aside from the pretty GUI overlay, what have you gained? Webmin has been hacked in the past (a bad one, in fact, though now patched), so you layer on a ton of overhead, security exposure and complexity for a bit of initial hand&#8209;holding. But if you can only get things done through a GUI, it's an option.

Whatever you do, do ***NOT*** install a full-blown desktop environment on your server, then do some form of RPC/VNC into it. That way lies madness. RPC/VNC is full of more security holes than a colander and drags in so much garbage that it defeats the whole point and purpose of running a Linux server. If you insist on that, you may as well stick with Windows Server which at least has had years to deal with its myriad security holes and has some handle on it.

In the final analysis, my best advice is to learn the command line and stick to a properly configured SSH. When it comes to servers, keep it simple, keep it plain vanilla. You will thank mine and all similar recommendations on this forum when you get past the learning curve and eventually join the ranks of those who avoid getting pwned or held up to ransom.

---

### Post by TheFu on 2021-08-20
Canonical has a new webmin-like option called **cockpit**.  [https://cockpit-project.org/running#ubuntu](https://cockpit-project.org/running#ubuntu) I'm not a fan.  Also, to access it securely, it really needs an ssh-tunnel.  Cockpit should only be setup to work from 'localhost', never from a any IPs other than 127.x.x.x/8.

See how everything comes back to using ssh?  ssh is how computers communicate, securely.  It is extremely powerful in ways that Windows people just don't know.  
> ssh is enough for
[LIST]
[*]    secure remote CLI/shell access to systems with plain ssh
[*]    secure remote access to files via sftp / scp
[*]    secure remote filesystem access via sshfs
[*]    secure remote desktops via x2go
[*]    secure remote file replication with rsync (ssh is the default rsync tunnel protocol)
[*]    secure port forwarding of selected ports (SOCKS5 proxy for browsers)
[*]    secure remote editing with vim/gvim and other editors
[*]    pseudo-VPN with sshuttle
[*]    secure, versioned, backups with one of 20+ backup tools built using ssh; rdiff-backup, rsnapshot are examples.
[/LIST]

Setup ssh-keys and all that access is both highly secure AND extremely convenient.

---

### Post by DuckHook on 2021-08-20
> **TheFu said:**
> Canonical has a new webmin-like option called **cockpit**.
I just skimmed through the site and may be wrong, but my reading of Cockpit is that it requires javascript, which is enough in my books to disqualify it out of hand. No way will I permit another scripting language/attack vector in something as critical as my server.

---

