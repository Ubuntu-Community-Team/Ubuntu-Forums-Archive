---
title: "Setting up private domain - is BIND the answer?"
date: 2007-05-21
forum: Server Platforms
---

### Post by Snuffleupagus on 2007-05-21
I have successfully set up an internal Feisty LAMP server that I can hit with my Ubuntu and Win XP laptops using the IP address. I'm using a Linksys wireless router which connects to outside through cable modem. It provides a fixed IP to the server and DHCP to all the laptops. 

What I *want* to do is create an internal domain name that will resolve from any of the laptops, so that I can create a fully developed web site internally before copying over to hosted servers. I've seen tutorials for BIND and other methods but I'm confused on the approach I should take. BIND seems complicated and overkill for my needs. Any suggestions? Thanks!

---

### Post by vbmds on 2007-05-21
Have a look at this, it might be useful: [http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10]("http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10")

---

### Post by EmmEff on 2007-05-21
While I've never used it, I understand that [Dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html) is decent for small networks.

I do agree that BIND is overkill, but I run it myself.  I've been thinking about 'downgrading' to Dnsmasq for simplicity.

---

### Post by rfreedman on 2007-05-21
For something really small-scale like this, it might be easier to just put an entry in the hosts file on the laptop.
For the linux laptop, it's /etc/hosts
For the windows laptop, I don't remember exactly, but it's something like \Windows\System32\Drivers\etc\hosts

---

### Post by DDuong on 2007-05-22
Dnsmasq is great for small networks, and it includes DHCP.  So your basically killing 2 birds with one stone :)

When I was setting up my network, I was using dnsmasq for a long time because of it's simplicity. But now I use BIND because I host my own mailserver, web server (re-building this own it's own box), and DNS server.  Learning BIND was fun too.

---

### Post by EmmEff on 2007-05-22
I would still go with Dnsmasq even with a few hosts.  Editing the hosts file is no fun when there might be the odd dynamic host (e.g. your friend's notebook, a computer you're working on for a friend/family member, etc).

There's something comforting about just letting DHCP do it's thing without having to intervene :)

---

