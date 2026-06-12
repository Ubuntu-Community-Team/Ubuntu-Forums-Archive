---
title: "iptable rules for ftp server"
date: 2011-06-22
forum: Security
---

### Post by nmxdaven on 2011-06-22
Hey guys, I have a few questions for people better at using iptables than I am.  I recently set up a ftp server in my house running a dyndns service so I can get to it from the outside.  I called my isp to get some help in setting up the router to forward port 21 from the outside to that box, and in short we had some problems.  Long story short, they ended up bypassing the router itself, and now the line running to the box is its own fixed external ip. Naturally I want a pretty darn good iptables setup for this.  The box runs proftpd and so far my iptables only accepts local loopback and port-21. (I left port 80 closed as its only purpose is to be a standalone ftp server) But I know there must be a safer rule for port 21, as right now its just wide open. Anyone have any ideas on how to make this a bit safer?   Also would that command be fine for any of the linux machines im connecting to it from the outside too?  Thanks guys! nmxdaven

---

### Post by cariboo on 2011-06-22
Due to the insecurity of ftp, I'd suggest using sftp instead, the only thing you need to do is install openssh-server, then set up private/public keys to access it instead of using a password. There is a howto [here]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html").

You can then use nautilus, filezilla, or many other ftp clients that support sftp. If you want to acces the server using Windows, have a look at WInscp, it's free.

---

### Post by Lars Noodén on 2011-06-22
[FTP is insecure](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#Background_of_FTP) and you will also have to manage two ports (20 and 21) and the relation between them.  Faster and more secure to use SFTP.  

So I second the suggestion made above by cariboo907.

If you are worried about bots hammering away at your site, you can use iptables to limit the rate at which new connections are allowed:

```

   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;

   # add host to "recent" list
   ip6tables -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;
   iptables  -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;

   # allow finite number of new connections per time limit
   ip6tables -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT
   iptables  -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT

```

---

### Post by nmxdaven on 2011-06-22
awesome guys, thanks for the help! Looks like that's what I'll be setting up.

---

