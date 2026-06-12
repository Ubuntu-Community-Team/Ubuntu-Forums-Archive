---
title: "Setting a 'Domain Name' during 13.10 home server install - is it essential?"
date: 2013-12-14
forum: Server Platforms
---

### Post by Chris of Arabia on 2013-12-14
I've ended up starting from scratch with my home server again, and have got to a prompt during the install that I don't recall seeing on previous iterations. It reads as follows:

>  [!] Configure the network

The domain name is part of your Internet address to the right of your host name. It is often something that ends in .com, .net, .edu, or .org. If you are setting up a home server network, you can make something up, but be sure you use the same domain name on all your computers.

Domain name:

_____________________________________________________________________

<Go Back>                                                                                           <Continue>

There are other computers on the local network, a mix of Windows, Android and iOS devices, but I've never done anything on those to set them up within a local domain. Does this option matter for the purposes of setting up this server whether I leave it blank, or do I have to put in something, in which case are there any common approaches to what that should be?

---

### Post by nerdtron on 2013-12-14
After the hostname, the installer asks for a domain name. I think it is optional since I don't set it most server install and not having any problems. Plus the installer will continue without a hostname so I guess it is really optional.

---

### Post by frankmorris2 on 2013-12-14
Hello,

For my personal network at home, I have never set the domain name. I use a network with static IP addresses and I connect to the machine with its IP. If I need to set an alias for the machine IP, I add a line in the file /etc/hosts. I have only 4 machines connected.

I guess a domain name is more useful when the network grows larger.

Have a nice day.

---

### Post by Chris of Arabia on 2013-12-14
Thanks both. That's what I was guessing at. I've always just connected via IP, or set a hosts file too, so looks like I'm good to go.

---

### Post by CharlesA on 2013-12-14
I've always used the .local domain for my home network but that is mostly because I needed some way to tell the machines what suffix to look for when doing name resolution.

---

