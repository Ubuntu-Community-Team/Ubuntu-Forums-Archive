---
title: "access ubuntu box behind a firewall from multiple points"
date: 2008-06-03
forum: Security
---

### Post by TorchlightJay on 2008-06-03
Hello,

So I have a notebook and a desktop and don't want to go through all the effort of putting files and folders on both of them and trying to sync the two up you know. MY desktop has a much larger hard drive but I want to keep it safe so I have firestarter running on it. It's been working pretty well. Well I want to be able to access the files on my desktop from my notebook. The problem is the firestarter. It blocks any IPs it doesn't recognize (as it should). I am not always at the same place twice and use a variety of IP addresses. How can I set it up to where Firestarter recognizes my machine and accept it regardless of what network I am on? Thanks.

---

### Post by The Cog on 2008-06-03
At times like that, you cannot just use a whitelist to allow selected IP addresses. You need access to a service from anywhere. 

I would suggest running an SSH server on an unusual port number, up in the many thousands. Configure SSH either to use key-based authentication only, or configure AllowUser to only allow your username (in /etc/ssh/sshd_config) and make sure you have a good strong password. 

SSH allows remote file access - put an address in the nautilus address bar in this format: 
ssh://username@1.2.3.4:10000/
and ssh also allows shell login.

---

### Post by TorchlightJay on 2008-06-03
That is cool for ssh. I was wondering, what if I have other services I need. Example, I want to put stuff on a mysql server and what not. I do not know how to do that to where I can access it remotely through my firewall from a variety of locations and IPs. i guess I can change the port number to a high thousands number but I'd like to do it another way. Any ideas?

---

### Post by The Cog on 2008-06-03
You can do tunneling of TCP over SSH for just one other service, but if you want to lot of services, perhaps you should be looking at using OpenVPN. It is good and secure and will provide full connectivity between the machines. The HOWTO on the OpenVPN website gives full and detailed instructions.

---

### Post by TorchlightJay on 2008-06-03
So let me make sure I am hearing right. I can do openvpn and log in and that will solve most all of my problems? What about logging into openvpn, won't my firewall block that? What's the best way to set this up?

---

### Post by kevdog on 2008-06-03
Can you just give us some ideas about how many services you would like to run or need access to?  OpenVPN is a full-blown high resource solution, however a simpler solution may be more applicable for your situation depending on exactly what you want to do.

---

### Post by hyper_ch on 2008-06-04
and changing SSH port won't secure you in any way... use a strong password and an auto-ban program for brute-forcing.

---

### Post by TorchlightJay on 2008-06-04
Okay, well this is what I want to accomplish

1) I have a lot of documents and I want to keep them in sync. Naturally it can get tedious trying to remember which ones I have changed and make sure to copy over right ones. If I edit one of my notebook and my desktop, well that causes a problem. I want to have most all of my documents on my desktop and access them that way. SSH or OpenVPN can work for that I am sure. 

2) I want to keep all of my music in a MySQL database and pull it with Amarok. I have like 15 Gigs of music and that is a lot to keep up with. If I can centralize that, it would make a difference. That and there are a few other things I want to put onto a MySQL database.

3) I want to do something with Apache. I want to have a decent web interface for everything and make it easy to develop web apps on my desktop and access them at anytime. 

That is really it in a nutshell. If anything else comes up, I'll tackle it then but that's the bulk of it.

---

