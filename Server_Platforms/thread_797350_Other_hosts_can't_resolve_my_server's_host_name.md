---
title: "Other hosts can't resolve my server's host name"
date: 2008-05-17
forum: Server Platforms
---

### Post by fizgig on 2008-05-17
Just installed 8.04 server on my box and I can't get the other two computers on my network (OSX and XP) to resolve the host name of my server though I can ping its IP address just fine.

I made sure winbind was installed and I changed the line in /etc/nsswitch.conf to

> :hosts:          files dns mdns wins

but no dice.  I've never had this issue on previous ubuntu server installs.  Not sure what I'm doing wrong.

---

### Post by Aearenda on 2008-05-17
I think you need to have samba installed for this to work.

---

### Post by fizgig on 2008-05-17
Sorry, samba is installed and I can browse the shares just fine if I use an ip address.  Still can't resolve the host name from other computers.  :(

---

### Post by bluefrog on 2008-05-17
either set the host name in windows and mac, or install a dns server on your ubuntu box and give this dns to windows and mac, or set up bind as a wins server (this I haven't tested for a long time)

James Dupin

---

### Post by fizgig on 2008-05-17
So you're saying to give up on the netbios functionality that has worked in previous ubuntu server installations and go through the hassle of installing a dns server on my ubuntu server?

No thanks - I'd rather get netbios name resolution working and keep my wireless access point as my gateway, dns server and dhcp server.

---

### Post by bluefrog on 2008-05-17
personally I don't mind what you are doing or not...

Then it is the wins server functionality which must be faulty I presume.

---

### Post by fizgig on 2008-05-17
I just don't like overkill solutions that require restructuring a network when there is an elegant way that should work.

Anyhow, I did get it to work by adding "netbios name = blah" in the smp.conf file.  No wins or dns server required.

I do appreciate your input though.

---

### Post by bluefrog on 2008-05-17
I am talking of the wins server functionality in smb.conf...

---

### Post by chiros on 2008-05-17
If you only have a small network then edit your hosts files; in windows located at C:\WINDOWS\system32\drivers\etc\hosts

Add a line such as:
192.168.0.xx 	[www.yourdomain.tld](www.yourdomain.tld)

I use that for my local websites, I would think it would work for your shares aswell

---

### Post by fizgig on 2008-05-17
That way would work but it sure is more convenient to use netbios as netbios is dynamic and doesn't require a server of any kind when all hosts are on the same subnet like mine (and I suspect most peoples') are.

If I stick to netbios host names in all my settings (such as my xbox for streaming movies from my server), that allows me to change IP addresses without breaking anything.

Using a wins server is necessary if you want to resolve host names between subnets, same thing goes for a dns server.  I'd rather use the server-less method of netbios but that's just my preference.

---

