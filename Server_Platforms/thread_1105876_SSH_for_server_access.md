---
title: "SSH for server access"
date: 2009-03-25
forum: Server Platforms
---

### Post by happyhacker on 2009-03-25
I have just setup dyndns to my server and would like to use ssh. I have an ssh server running. How do I link the ssh server in so that all connections from outside use ssh encryption? Or maybe it's not necessary?

---

### Post by aurelieng on 2009-03-25
If SSHD is the only daemon running on your server or if your modem is set up to forward only the port 22 to the local IP/port 22 of your server, then all incoming connections to port 22 will be handled by SSHD, and others will be ignored.

Btw, it's probably worth changing the default listening port to avoid script kiddies (see /etc/ssh/sshd_config)

---

### Post by happyhacker on 2009-03-25
Thanks, I don't know if this is the only "deamon" running but it is shown as one of many things/processes running under root. I have OpenSSH_5.1. I will go and read their advice on how this all works. In the meantime I did accidentally reveal my external IP address on a forum and forwarding is to port 80. Am I right in thinking that I should change the SSH listening port from 22 to 67890 (or something) and then configure my router to forward all incoming to that. Then presumably I will be locked out unless I configure some password or setup an SSH key (which has to be paid for at dyndns). Am I on the right lines here?

---

### Post by BkkBonanza on 2009-03-25
I think you have some confusion about ssh and it's use.

First, just to be clear about your setup. You have a server on your local lan that is running a web server and ssh server. It sees the outside world via your router. So anything coming to your server from outside has to be passed through your router first.

I think we just finished talking about how to get your web server visible to the world by forwarding port 80 from your router to the local server. You can access ssh via port 22 by doing the same thing. In your router you can forward port 22 to your local server. If you want to change the port for outside access then go ahead - forward some other port, say 2211 to port 22 on your local server. Then you can come in to port 2211 from the web and it will be directed to port 22 on your server, where sshd will answer. You can also change the setting in sshd_config but then you forward accordingly using that chosen port number. Changing the port number is not going to stop anyone with intent but it does help with most of the script_kiddies.

In the simplest case you use ssh to access the console on your server. You can also get into your router that way too but for most typical uses it's easier to just use the web panel for that. The router won't answer on port 22 on the public side unless you enable "remote admin". It's less safe to have that open than to only access from inside your lan.

Now regarding running your other connections through ssh. If you want the public to see your web server then you don't run it through ssh. If you intend for the web server to be visible within your own lan and want outside use only by authorized users (secure!) then you can route it through ssh using a simple technique called "ssh tunnelling". This is like a simple form of VPN and gives you security at the expense of a bit of configuring. It's not at all suitable or useful for general public access to your server.

BTW a "daemon" is just a program that runs in the background on your machine. There are many like cron, apache, sshd and more.

You don't want to forward your http (web) to ssh. If you intend for private access only then that's a different thing and I can tell you how to do that.

A ssh key is something you can create easily on your machine for free. No need for paying dyndns. You are probably thinking of SSL certificates. While they are similar they are not the same and serve different purposes. Start by using a password with ssh - as you are likely doing now. Later you can get more secure by generating a key and installing that. There are tutorials that show that step by step for ssh use.

Don't worry about people knowing your public ip address. Most servers on the net get continually hit by scanners looking for a way in. Just knowing your ip doesn't mean much, especially if only a couple ports for ssh, http and https are open. 

Hope that helps for now.

---

### Post by happyhacker on 2009-03-25
That's cleared it up fine. Thanks for taking the time to do that. We intend to install a Client Management System running under Drupal. Now I am not sure if this should go through SSH but it will have its own logon system so maybe that's secure but I suspect that using a key with SSH and the website logon to the CMS will be better because the data will be sensitive.

So I would like to know how to link the Apache website to the SSH mechanism. No doubt I will be using the apache virtual method as we may have more than one website. If you know of a tutorial.

---

### Post by BkkBonanza on 2009-03-25
For sensitive material your web site should either be entirely served on https (ssl) (which means port 443, certain other apache settings, along with creating or buying a certificate) or if that seems like a lot of work (and it can be for new admins) you can also use ssh or a vpn. 

If you decide to use ssh or a vpn then you would close port 80 on your router and not forwardnit as we have been doing. Your website is no longer public. Or if you need a public site and a private site then you can serve the private site on another port that is closed on your router.

For either a vpn or ssh you would have a suitable port open and forwarded for this service and then through this service you would authenticate first before getting access to the web server.

I don't use a vpn myself but I do use ssh like this and can comment on that kind of setup. Each user authorized to access the CMS would have their machine configured to enable access. There are quite a few tutorials out there but not one I have in mind. I can write a few notes about it so you have a basic game plan.

------

For users on your local lan they access the CMS system normally using a local name or ip address. 

For users outside the network they first open a tunnel using ssh to get to your server (via a forwarded port on the router) and then ssh will forward the connection to the actual web server. Users will need a user/pwd (or for more security a authentication key) to get in via ssh.

There are two ways to use ssh for this - both are called tunnelling.

1. You set up a specific tunnel just for the web server.
2. You open a socks proxy tunnel which gives the user more access (similar to as if they were sitting in the office at their machine).

To open the tunnel you type a command or have a script on the home/remote machine and the command is different for method 1 or 2.

example commands, assumin default port 22:

1. ssh -f [email]user@my_public_name.com[/email] -L 80:localhost:80 sleep 60

(which opens a tunnel from port 80 on your home machine to port 80 on your office server and if it is inactive for 60 seconds then closes it)

2. ssh -D 8080 [email]user@my_public_name.com[/email]

(which opens a socks proxy to your office server, and you need to tell your browser to use a socks proxy at localhost port 8080)

You can also use this method easily from Windows machines outside your lan. A good program for making one click tunnels in WinXP is Tunnelier.

Method 1 is more controlled but method 2 is more flexible. With 2 the user can check mail and run other programs that would use the network as though they were on the office lan by setting their program to use the proxy just like their browser.

There is lots of info out there. Just try google "ssh tunneling". I would also look into VPN as it's also secure. Hope this helps you figure it out.

---

### Post by happyhacker on 2009-04-22
Right that's a lot of info, thanks. I do not want my only (so far) website (the CMS) to be used by public but do need admin access myself and users to log in (eventaully). So it appears I need to configure the SSH server (I do not know what it's being used for right now - I don't as far as I know) and install something on my windows machine to access it. I also want to control the server with webmin remotely as I do locally now. I will forward port 22 for now but will want to change that later. Any further comment welcome but I guess it's down to me to play.

---

