---
title: "Guidance for new &quot;secure&quot; webserver"
date: 2011-11-15
forum: Server Platforms
---

### Post by joker535 on 2011-11-15
I work for a small web design company that has a bunch of Windows webservers. One of the servers has a few dozen SSL secured e-commerce websites on it. We want to get away from Windows and have decided to deploy a Ubuntu 10.04 LTS 64 bit server to host just our SSL sites on a more secure platform. The server will have apache2, railo/tomcat, php, perl, and webmin/virtualmin on it. Database functions will be handled by another server that is only accessible from a backend connection. Websites and SSH traffic will be handled on a frontend connection with multiple static IPs (no NAT). We have a separate transparent bridge firewall server between the webservers and the internet.

We want the server to be reasonable secure but we don't want it to be a nightmare to administer. We will definitely use webmin/virtualmin as we have another box using it and we are happy with it. A couple of questions have come up relating to security and I hope you folks can give me some guidance here.

FTP server - Unfortunately, we have to give our customers FTP access to their files. We want to use webmin/virtualmin to administrate the FTP users for each domain but we want to make sure they can only browse their website files and nothing above the website folder. Is this do-able in webmin/virtualmin while maintaining security and not allowing users SSH access?

AppArmor - Do we need/want this? The box will be a dedicated webserver nothing more. Do we need AppArmor or is that just going to be a nightmare to administrate?

Thanks in advance for your help.

---

### Post by Dangertux on 2011-11-15
> **joker535 said:**
> I work for a small web design company that has a bunch of Windows webservers. One of the servers has a few dozen SSL secured e-commerce websites on it. We want to get away from Windows and have decided to deploy a Ubuntu 10.04 LTS 64 bit server to host just our SSL sites on a more secure platform. The server will have apache2, railo/tomcat, php, perl, and webmin/virtualmin on it. Database functions will be handled by another server that is only accessible from a backend connection. Websites and SSH traffic will be handled on a frontend connection with multiple static IPs (no NAT). We have a separate transparent bridge firewall server between the webservers and the internet.

We want the server to be reasonable secure but we don't want it to be a nightmare to administer. We will definitely use webmin/virtualmin as we have another box using it and we are happy with it. A couple of questions have come up relating to security and I hope you folks can give me some guidance here.

FTP server - Unfortunately, we have to give our customers FTP access to their files. We want to use webmin/virtualmin to administrate the FTP users for each domain but we want to make sure they can only browse their website files and nothing above the website folder. Is this do-able in webmin/virtualmin while maintaining security and not allowing users SSH access?

AppArmor - Do we need/want this? The box will be a dedicated webserver nothing more. Do we need AppArmor or is that just going to be a nightmare to administrate?

Thanks in advance for your help.

I'm not sure the level of administrator's that you have so honestly "nightmare to administer" is somewhat vague. That being said I'll try to answer your questions the best I can.

For the FTP make sure that each user is at least chrooted in their webroot without access to SSH. To do this in SSH the users will have to be in a group that doesn't have access to the service. For FTP follow your ftpd's documentation for chrooting (I recommend vsftpd or proftpd, in that order)

Apparmor is nice, and you probably want it, but you don't truly need it. You can however utilize Apparmor to enchance the confines given to your clients by the chroot, as chrooted environments can be rather trivial to break out of. 

Also consider a web application firewall if you're not already using one. 

The actual layout of the network you described above is a good start, just make sure your firewall is well configured, is it just a typical firewall or is it also IPS/IDS? This is something to consider.

Hope this helps

---

### Post by joker535 on 2011-11-15
> **Dangertux said:**
> I'm not sure the level of administrator's that you have so honestly "nightmare to administer" is somewhat vague. That being said I'll try to answer your questions the best I can.

For the FTP make sure that each user is at least chrooted in their webroot without access to SSH. To do this in SSH the users will have to be in a group that doesn't have access to the service. For FTP follow your ftpd's documentation for chrooting (I recommend vsftpd or proftpd, in that order)

Apparmor is nice, and you probably want it, but you don't truly need it. You can however utilize Apparmor to enchance the confines given to your clients by the chroot, as chrooted environments can be rather trivial to break out of. 

Also consider a web application firewall if you're not already using one. 

The actual layout of the network you described above is a good start, just make sure your firewall is well configured, is it just a typical firewall or is it also IPS/IDS? This is something to consider.

Hope this helps

There are just 2 of us who are going to administrate the server    but neither of us have time to go chasing down obscure fixes for mysterious things so we want to avoid them from the get go.

We had another recommendation for proftpd as it can handle the chrooting of the FTP users from the webmin gui. I found the documentation for what was recommended and I am building a VM to test it now. I hope it works as described.

We have foundeo fuseguard that will be running on the box itself and a PfSense firewall with Snort handling IDS/IPS so we are pretty much covered there. 

I think we are going to skip the SEL and AppArmor for now. If we have problems we can reload the box with one of them. 

Thanks

---

### Post by Dangertux on 2011-11-15
> **joker535 said:**
> There are just 2 of us who are going to administrate the server    but neither of us have time to go chasing down obscure fixes for mysterious things so we want to avoid them from the get go.

We had another recommendation for proftpd as it can handle the chrooting of the FTP users from the webmin gui. I found the documentation for what was recommended and I am building a VM to test it now. I hope it works as described.

We have foundeo fuseguard that will be running on the box itself and a PfSense firewall with Snort handling IDS/IPS so we are pretty much covered there. 

I think we are going to skip the SEL and AppArmor for now. If we have problems we can reload the box with one of them. 

Thanks

Sounds good keep us posted. 

Also I highly recommend the [emerging threat]("http://www.emergingthreats.net/")s rules for Snort if you're not using them already.

good luck !

---

### Post by Jonathan L on 2011-11-15
Hi Joker

Apart from the good advice of Dangertux for the various security software, another practice I highly recommend is the use of a separate server for logs, if you can manage it.  Then you syslog, pretty noisily, to this from your publicly visible machines.  Make it so you can't log in to it from any publicly-visible machine.

It's simply to do, and gives really good audit for what's happening on your public machines.

If you don't want to do that, you could at least make your system logs keep forever.

In passing: as you sure you want to have one box with all your websites on it?  I'd suggest several, as it's much easier to see if something is abnormal behaviour if you have several of them.  And it will help your growth and disaster recovery planning considerably.  Knowing that you have the ability to bring a new system up and into the mix without taking everything down adds enormously to the peace of mind.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by joker535 on 2011-11-15
> **Jonathan L said:**
> Hi Joker

Apart from the good advice of Dangertux for the various security software, another practice I highly recommend is the use of a separate server for logs, if you can manage it.  Then you syslog, pretty noisily, to this from your publicly visible machines.  Make it so you can't log in to it from any publicly-visible machine.

It's simply to do, and gives really good audit for what's happening on your public machines.

If you don't want to do that, you could at least make your system logs keep forever.

In passing: as you sure you want to have one box with all your websites on it?  I'd suggest several, as it's much easier to see if something is abnormal behaviour if you have several of them.  And it will help your growth and disaster recovery planning considerably.  Knowing that you have the ability to bring a new system up and into the mix without taking everything down adds enormously to the peace of mind.

Hope that's helpful.

Kind regards,
Jonathan.

I wish I had an extra box to send syslogs to. I think once we get more boxes converted to linux we will go that route. We are currently using a combination of nagios core and Spiceworks to monitor all the boxes. Spiceworks takes care of the Windows error logs and Nagios monitors the rest. We pump all of our website logs to a central NAS where they are processed by another server for traffic reporting. I hope to do something similar with the syslogs later on. 

As for spreading the sites out, that exactly what I am doing. We have about 800 sites on 2 very large Windows boxes. My intention is to split them out to mostly linux boxes with about 100 sites per box. I still have to keep a couple of MS boxes for ASP, Frontpage, and some dinosaurs using access databases but I intend to replace the bulk with smaller machines. Moving all the SSL sites is sort of a proof of concept project. As long as it goes well, we are going to move everything else that we can to similar boxes. We are tired of paying $800 a license for Windows.

Thanks

---

### Post by joker535 on 2011-11-15
> **Dangertux said:**
> Sounds good keep us posted. 

Also I highly recommend the [emerging threat]("http://www.emergingthreats.net/")s rules for Snort if you're not using them already.

good luck !

Yep. I added the ET rules right after my oinkmaster code started working. Love the PfSense setup. Our 100M connection runs at about 40-50 percent during the day and the atom box it is on does not even break a sweat. Its one of my favorite open source projects.

---

### Post by Lars Noodén on 2011-11-15
> **joker535 said:**
> There are just 2 of us who are going to administrate the server    but neither of us have time to go chasing down obscure fixes for mysterious things so we want to avoid them from the get go.

We had another recommendation for proftpd as it can handle the chrooting of the FTP users from the webmin gui. I found the documentation for what was recommended and I am building a VM to test it now. I hope it works as described.

We have foundeo fuseguard that will be running on the box itself and a PfSense firewall with Snort handling IDS/IPS so we are pretty much covered there. 

I think we are going to skip the SEL and AppArmor for now. If we have problems we can reload the box with one of them. 

Thanks

I'd recommend to skip [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) entirely and use SFTP instead.  Since you have SSH, you already have SFTP configured.  It is also easy to chroot and to prohibit shell access.  (See ChrootDirectory and ForceCommand in [sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html))

---

### Post by Jonathan L on 2011-11-15
Hi again Joker

> I wish I had an extra box to send syslogs to. I think once we get more boxes converted to linux we will go that route. We are currently using a combination of nagios core and Spiceworks to monitor all the boxes. Spiceworks takes care of the Windows error logs and Nagios monitors the rest. We pump all of our website logs to a central NAS where they are processed by another server for traffic reporting. I hope to do something similar with the syslogs later on.Have you considered AWS or similar?  I find it's really a great way to deal with this kind of thing.

> As for spreading the sites out, that exactly what I am doing. We have about 800 sites on 2 very large Windows boxes. My intention is to split them out to mostly linux boxes with about 100 sites per box. I still have to keep a couple of MS boxes for ASP, Frontpage, and some dinosaurs using access databases but I intend to replace the bulk with smaller machines. Moving all the SSL sites is sort of a proof of concept project. As long as it goes well, we are going to move everything else that we can to similar boxes. We are tired of paying $800 a license for Windows.Sounds like you're on a good track there.  It's not specifically the money for the licence which is so costly, it's the fact you have to keep auditing everything and putting serial numbers and keys all over the place just for the OS.  But then the management time is where the costs really go, and it makes you inflexible.

And again, even if you have good reasons to do your own hosting, have you considered AWS for experiments?  I use it for testing configs on freshly-installed boxes all the time.  You might find it's a good way to figure out some of your configuration developments without any capex, and as it only takes 61 sec to launch a new instance, you can try things really quickly, and multiple experiments at the same time. I think it really adds to the flexibility of your armoury.

Just some thoughts, hope they're of use.

Kind regards,
Jonathan.

---

### Post by joker535 on 2011-11-16
> **Jonathan L said:**
> Hi again Joker

Have you considered AWS or similar?  I find it's really a great way to deal with this kind of thing.

Sounds like you're on a good track there.  It's not specifically the money for the licence which is so costly, it's the fact you have to keep auditing everything and putting serial numbers and keys all over the place just for the OS.  But then the management time is where the costs really go, and it makes you inflexible.

And again, even if you have good reasons to do your own hosting, have you considered AWS for experiments?  I use it for testing configs on freshly-installed boxes all the time.  You might find it's a good way to figure out some of your configuration developments without any capex, and as it only takes 61 sec to launch a new instance, you can try things really quickly, and multiple experiments at the same time. I think it really adds to the flexibility of your armoury.

Just some thoughts, hope they're of use.

Kind regards,
Jonathan.

We have a co-location deal with a local phone company and we just pay a fee for unlimited use and 3 full racks. It costs us nothing but the hardware cost to drop another linux box out there and we like to keep everything but email in house. 

Thanks

---

