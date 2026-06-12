---
title: "Virtual server naming convention"
date: 2016-07-15
forum: Virtualisation
---

### Post by Aphexlog on 2016-07-15
I am the new sysadmin for an IT company that has asked me to come up with a naming convention for all the servers within a vmware configuration. These are all Ubuntu 14.04 servers (not that it matters).These are the required details to be integrated in the name convention:- environment- number- and preferably the name of the person that requested it (this will not always be applicable)- the client name (Disney, Levi, etc.)... but not always applicable.As a side note, the location of the servers are not relevant due to them being virtual.I would greatly appreciate any suggestions for name conventions.

---

### Post by Habitual on 2016-07-15
Naming the entities in VMware or naming the hosts themselves?
I'm confused.

---

### Post by Aphexlog on 2016-07-15
The objective would actually be to match the name of the host to the name of the VM in VMWare - they would both use this convention

---

### Post by MAFoElffen on 2016-07-15
As a Systems Admin, a Database Admin, Developer: "Naming Standards and Naming Conventions" are usually something that are agreed upon between those that are going to be using them. For that to be known, between others you may have to work with, that convention needs to be documented/published.

For me, i use something That I can remember and makes sense to me. I try to keep it short, so that I don't have to type something 50 characters to touch something, but also quickly identifies what it is, when you see it. For me, it ends up like an interface API language. So in your sys admin administrative scripts, that you, are doing this to this... and it makes sense.

---

### Post by Habitual on 2016-07-15
Sorry, I don't have any experience in this area.
My boss names them, Sets the A Record.
I edit PS1 to make it say what I want.
I deal with IPs, not hostnames on a daily basis.
What something is called, well now, we all have more than one identifier, now don't we?

I tend to name things that somehow reflects their purpose in the name.

In the 43 Folders fashion, I'd guess I'd use or try to
disney-web_
disney-dns_
disney-ftp_

Levis-web_
Levis-dns_
Levis-ftp_

Something along those lines.
Just free-balling it here.

---

### Post by MAFoElffen on 2016-07-16
For machine HostName and VM Manager (whatever the host's Hypervisor is), the VM guest Name and the Vm Guest's OS hostname do not need to match, but it is a good practice if they did resemble each each in some way.

The a limit that you do have is that each has to be "unique"... In your Hypervisor Manager, the machine guest names have to be unique to each other. That name as created determines the file names of the machine config file and it's intitial disk image file. So you can imagine the conflict that might cause if you try to create a machine that already exists. Next, between VM Guests that exist In the machine OS, hostnams, as they show up in DNS as FQDN, or Fully Qualified Domain Names... which breaks down as HostName.DomainName... those hostnames need to be unique throughout the domain. So there cannot be two hosts with an FQDN of host1.mydomain.local

---

### Post by Aphexlog on 2016-07-20
I have started implementing a name convention like so:
x5tst-connect01 = on host ESX5, test environment, the service that it is hosting is connect, and it's the first one with that name
x7trn-engage03 = on host ESX7, training environment, the service that it is hosting is engage, and it is the third with that name

These are hosting customer supporting databases and applications

---

