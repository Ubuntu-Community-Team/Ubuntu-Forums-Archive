---
title: "How to remote SSH into my home server"
date: 2011-08-07
forum: Server Platforms
---

### Post by frotzed on 2011-08-07
Over the past two weekends I've been determined to set up my first Linux server in my home.  With the help of these forums as well as several others, it has been a HUGE success.

Now, I have a question.  If I wanted to SSH into my server from a remote destination, it seems I would have to take the following steps.  Please tell me if I'm mistaken.

1) In lieu of getting a static IP from my ISP, sign up with Dynamic DNS and use it instead.

2) My home server is not at the gateway.  So I would have to forward port 22 (at the router) to my server's LAN static address.

3) Access my server via SSH remotely by going to \\xxx.xxx.xxx.xxx:22 where the "x's" stand for the static IP address given to me by DynDNS.

Does this sound correct?  If not, I'm not asking for hand holding, but a point towards a tutorial or how-to would be helpful.

Edit: Or... am I going to have to set up a VPN to SSH into the server?

---

### Post by alarme on 2011-08-07
Don't forget to install ssh server!!!
apt-get install ssh

to access from command line (linux box)

ssh [email]user@your.public.ip[/email]

where user is a valid username for the server host
no need to specify port

from nautilus:
ctrl+L to gain access to address bar
then, write:
ssh://user@your.public.ip

for windows, search for putty

If your router has firewall, configure it properly.

---

### Post by arrrghhh on 2011-08-07
The VPN is not necessary, but another step to get into your system if you're concerned about security.

Step 1&2 are spot on.  Step 3 is where you drift from what needs to be done - instead of \\xxx.xxx blah (that would be for file sharing/samba if the client is a Windows machine!)

You would actually need an SSH client - Putty is a good (free) version for Windows.  Linux has an SSH client built-in.

But assuming you have the port open, you should then be able to ssh from any machine on the internet to your home computer.  Since you're exposing SSH to the world, I would highly recommend disabling password logins, and using SSH private/public keys.  This is a much more secure method to using a basic password to login to your server.

Back to the VPN topic - this is entirely unnecessary, but if you want to access *everything* that your home server provides abroad, this would be the way to go.  It would also add another layer of security over SSH, assuming you put the SSH service behind the VPN.

---

### Post by papibe on 2011-08-07
Your are mostly correct. Except you don't really need to pay for an static IP. Take a look at this [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It helped a lot when I setup remote access to my server. Although it is from the point of view of a Windows user, it explains very well all concepts needed.

If you use well-known dynamic DNS service (like Dyndns), the client in the repositories works very well (ddclient). You'll have to create your dyndns account first (it's free!).

There's an alternative. Some routers have an integrated dynamic DNS client. That would be not only the easiest but a bit more efficient.

Note that in the case of Ubuntu (all Linux really), just by installing openssh server, you'll have both remote access and file services (using sftp). For the last one you can use graphical clients, like Filezila both in Windows and Ubuntu, WinSCP for Windows (I recommend this one), or the multiplataform FireFTP add-on for Firefox.

Another tip I can think of is changing the default port for ssh from 22 to some very different number. It add a bit of security, but also covers the situation in case your ISP blocks standards ports.

Good Luck!

---

### Post by volkswagner on 2011-08-07
+1 for what alarme mentioned.

DynDns.com does not give you a static ip.  You can get a free domain name such as mydomain.dyndns.com.  Then Dyndns has a client software you can run, even some routers have built in dyndns support.  What you get is a dns updater client that will change the dns records to match your public ip.

Once setup you would then use the domain name or your public ip from your isp.

ie:

```
ssh username@mydomain.dyndns.com
```

or

```
ssh username@123.123.123.123
```

Substituting your public ip above.  

You can easily find your public ip from your router page, or go to canyouseeme.org.  Once you feel SSH is setup, then you can verify port 22 is open by using canyouseeme.org from inside your LAN.

---

### Post by YesWeCan on 2011-08-07
Hi. I use OpenVPN. This advice is good for SSH which just gives you a remote terminal on one port. What VPN does is give you an all-ports tunnel which is like having your remote client connected to your server by a LAN cable (and it's encrypted). So you can do everything you could do if you had a direct connection, albeit slower. It is more complicated to set up than SSH, tho.

---

### Post by frotzed on 2011-08-07
Awesome advice!  Thank you all SO much.  It's working as intended now.  Completely awesome.

---

