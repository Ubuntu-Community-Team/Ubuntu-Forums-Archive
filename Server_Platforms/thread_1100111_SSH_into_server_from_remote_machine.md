---
title: "SSH into server from remote machine?"
date: 2009-03-18
forum: Server Platforms
---

### Post by ItecKid on 2009-03-18
Hello all,

I recently installed Ubuntu server edition to my computer.  Presently, I can access it via ssh if type:

```
ssh username@server_ip_address
```

My question is, can I make it so that I can access the server by typing in the server name rather than the IP address?  For example;

```
ssh username@servername
```

Thanks for your help.

---

### Post by uberlinux on 2009-03-18
You need local DNS.  DNS converts IP addresses to hostnames.  The real, big DNS servers that you use now are owned by your ISP, and those won't know about your server.  You need to set up your own DNS server.  Doing so is kind of involved, but you can set it up on that server that you just loaded.  Google "Ubuntu BIND tutorial".

---

### Post by squaregoldfish on 2009-03-18
Assuming you're running your SSH client under Linux, the easiest way to do this is to edit your /etc/hosts file.

Add a line of the form:

<ip address>   <hostname>


Save the file, and you should be good to go.

Windows also has a hosts file, but I can't remember where you'd find it. Google probably knows though.

Steve.

---

### Post by Mud.Knee.Havoc on 2009-03-18
If you're interested in some added functionality, you can sign up (for free) at dyndns.org... this will give you a whatever.dyndns.org address which (via software you install on the machine) is constantly updated with your changing IP address.

This is cool because you just have to remember this address and you can access your computer from anywhere (as long as you've got your firewall configured correctly).

Just a tip, though... regardless of how you're using ssh, make sure to take the necessary precautions: use a non-default port and/or install denyhosts or fail2ban so people can't brute force your ssh login.

---

