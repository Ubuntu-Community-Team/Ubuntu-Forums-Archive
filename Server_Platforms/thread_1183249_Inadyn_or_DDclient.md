---
title: "Inadyn or DDclient?"
date: 2009-06-09
forum: Server Platforms
---

### Post by Extol11 on 2009-06-09
I'm doing a research on how to make my ubuntu server available to pcs outside my network and was recommended to use DynDns. Now they recommend using one of these two update clients: Inadyn and DDclient. I wanted feed back on which one works best and how to install it. I'm reading the DDclient instructions but they seem rather complex. I would appreciate any help you guys could give me.

---

### Post by smc18 on 2009-06-09
If you want to make you server available on the Internet, first you need to decide what it is that you want available.

If you want to gain access to shell.
1-Install OpenSSH-server and begin to configure it.  By default it uses port 22.
2-On your home router, you need to setup port-forwarding (many different names on different brand routers... could also be called a virtual server)
3-So on your router you need to forward all port 22 request from the outside to your server's inside LAN IP. (You set this up on the router)
4-If you are connected from your work... you need Putty, or another SSH client, and use your home's EXTERNAL IP address, and the SSH port you setup. (default is port 22)

Same rules should apply for ftp, telnet(shouldn't be using anyways) etc.

---

### Post by Extol11 on 2009-06-09
For now I just want outside computers to access my server. I'll work on setting up the shell and stuff later. I installed proftpd but it only lets me access my home directory. It won't let me upload stuff directly to the site's folder (/var/www). I know how to setup the router to let it access the pc I want to use as a server. I just set the DMZ zone to that IP. And it is indeed called port forwarding in my linksys router. But I need to be able to use one of those two programs to set keep the server reachable through a DNS service. I remember about two years ago when I setup Joomla, I used the internal ip for one part of the configuration process and then the website couldn't load from any computer outside of my network. I noticed that both programs are available on the ubuntu repository. Should I use these or download them and build them from source?

Also, how do I tell ubuntu to keep a static network address. It's using wireless againts my will because of physical limitations.

---

### Post by koenn on 2009-06-10
ddclient does what it's supposed to do and is trivial to set up.
There are some sample cinfig files on the dyndns website, you can use them almost without any modification (except your password, the domain name you choose, ...)

Just install from the repos, no need to make it more complicated than that.

---

### Post by Agent ME on 2009-06-10
> **Extol11 said:**
> Also, how do I tell ubuntu to keep a static network address. It's using wireless againts my will because of physical limitations.
Right-click the network manager, edit connections, and you can set the static IP + DNS there.

---

### Post by Extol11 on 2009-06-11
Thanks a whole lot, guys. I'm going to try that tonight because I've been doing a lot of stuff with my computers.

---

### Post by philtrim on 2009-06-12
Depending on the model router you have (and/or Firmware loaded on router) you can set the DYNDNS config in the router, and it will do all the work for you.  I am using a Linksys wrt54-gl router flashed with 3rd party firmware (Tomato) and I have mine setup this way.  

Really easy to configure.  Just create your account at DYNDNS web site, then go to your router config and plug in your user id and password that you setup with DYNDNS and the router does the rest!

---

### Post by artcancro on 2009-08-10
> **Extol11 said:**
> Now they recommend using one of these two update clients: Inadyn and DDclient. I wanted feed back on which one works best and how to install it.

For years I had a static IP at home, but I recently switched to Verizon FiOS (25/15 Mbps ... rock on!) and it comes with a dynamic IP.  I signed up for an account with dyndns.org and installed inadyn.

The problem I found with inadyn was that after a DHCP lease renewal, inadyn would often unbind itself and updates would stop working.  Then it would mysteriously start working again later.

I switched to ddclient and haven't had that problem anymore.  inadyn does appear to have more options -- including a "force update" which you can use to force it to send an update every week or two in case your IP address didn't change and you want to avoid the "your account is going to expire" notices.  As a workaround, I put an extra call to ddclient in crontab.

Don't worry about ddclient's complexity ... if you're using Ubu it'll walk you through the setup after you install the package.

---

### Post by dbyrd on 2010-05-07
Just installed ddclient from synaptic. A dialog popped up during the install that asked for the dyndns username and password. Couldn't be easier...

Note SSL updates are not enabled by default. The SSL option may have been presented via the dialog, but I didn't see it...

To enable SSL updates I to manually edited the config file.

[INDENT]gksu gedit /etc/ddclient.conf[/INDENT]

I added ssl="yes" on a new line after the protocal= line.

---

### Post by arrrghhh on 2010-05-07
ddclient for sure.  It's what I use, I had issues with inadyn.

---

### Post by vikrant82 on 2010-05-09
I use inadyn for simple reason ddclient takes up around 3mb of memory where as inadyn takes paltry 150k. 

I will just put, "inadyn -u username -p password -a host.dyndns.org --update_period 1800000 --background" in a startup script.

---

