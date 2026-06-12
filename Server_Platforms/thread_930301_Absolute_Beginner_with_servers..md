---
title: "Absolute Beginner with servers."
date: 2008-09-25
forum: Server Platforms
---

### Post by Tiersin on 2008-09-25
Alright guys, I'm very new to networking and not very good at it. I've been reading up on it but it seems that everything I can find is directed at building massive servers for large networks. I'm interested in setting up a simple home network with a main server, a few computers connected on a LAN, and a few on WAN. 

Right now, my setup looks like this:

cable -> modem -> linksys router -> (wired) 3 computers including server

(wireless) about 3 other computers.


These computers are running everything from linux, to Windows XP and Vista, to Mac OSX. I have the server set up to share to share files over the LAN using Samba, but nothing more. I would really like to get it set up so that I could:

1. Remotly access files from the web, either through ssh, or FTP.
2. be able to connect to it via the command like like "ssh [email]user@computer.loca[/email]tion like I can with the machines at my school.
3. Remote desktop if possible.

I know the first step is to set up a static IP, but I'm clueless as to how to do that. I've read "the perfect server" how to's and such at howtoforge.com and none of them do much explaining of the steps. I have no idea how to set up static IP's or anything to do with ports. Any help on where to get started would be greatly appreciated.

---

### Post by cariboo on 2008-09-25
Have a look at his guide:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

It walks you through the setup step by step. If you have to install a gui, install something light like wmaker or xfce. The other alternative to installing a gui is to just install the gui apps you need then use X forwarding to run the apps remotely with ssh:

```
ssh -X user@server
```

Once connected to the server you can then just run the qui app you need.

Jim

---

### Post by kamaji792 on 2008-09-26
Check out the following guide [_https://help.ubuntu.com/8.04/serverguide/C/index.html_](https://help.ubuntu.com/8.04/serverguide/C/index.html).

**ssh** access is easy to setup, just install OpenSSH

I assume by static IP you are talking about the IP address from your ISP.  Obviously you will have to talk to them to see if they can provide such.  Even if they can't there are ways of getting round this but sadly I don't know what thy are :P

Start by doning the remote connection on the local lan - that should be straitforward.

If you want to connect from outside the local lan you will probably have to set up port forwarding in your router.

All the best

---

### Post by freebeer on 2008-09-26
You don't need a static IP.  If you currently have a dynamic IP address from your ISP, head over to a service such as dyndns.org.  You can get a domain name from them that will point to your dynamic ip address.  That way you can always reference your home machine through the domain name without trying to remember what your current IP address is.  That's what I do and it works great.

If your IP address changes much, you'll need to update dyndns.org's entry for your IP whenever it changes (or every 30 days or so, so that they know you're still active.  Your router may already have this feature, or you can run a script which can also be found on their site.

Once you've got that functional, and have openssh server installed  on the target machine, you'll need to forward your ports in the router to the machine.  Typically ssh is run on Port 22, so you'll need to set up a port-forwarding rule in your router to direct such traffic to the IP address (internal) of the server.  It may sound a little complicated, but it's pretty straight-forward.  (No pun intended)  :D

---

