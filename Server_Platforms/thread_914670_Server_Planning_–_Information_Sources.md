---
title: "Server Planning – Information Sources"
date: 2008-09-09
forum: Server Platforms
---

### Post by expatCM on 2008-09-09
I am going to update my server, I know approximately what I want but I do not know how / what I need to install.  So at this stage I need to do a lot of background reading.  Could anyone please tell me the places to look as follows - 

Existing sever runs Ubuntu 7.10 with Webmin.  Squid, file server, print server, ssh, firewall.  A couple of SATA drives and that is about it.  Four users, all Ubuntu 8.04. No contact at all with Windows.   All very straight forward and only crashes when I run out of disk space.

In addition to the above, what I would like to do is - 

1.Install two more SATA drives and set up a software RAID 5.  How to set up a RAID 5?

2.Allow my children secure remote access from school.  So if I give them an ASUS EEE each then they can access the server to get their files or upload from school.  What is this called, I do not mean FTP....  I think ....  (so that I can find out what to set up)?  I also need to keep them off my files – so restrict access to specific directories.

3.Host a website (for family use).

4.Work out how to get a static IP (services like dyndns I guess).

I may be missing something of course  .... my mind is open.  Email is left out since google offer a free service even where you use your own domain ...  and that is very efficient in dealing with spam and good enough for our needs.

Any suggestions of places where I should start reading up would be appreciated.  I have looked on google to a point but it is a bit difficult to look if you are not sure what you are looking for ...

---

### Post by cdtech on 2008-09-09
Here is a great howto on the Ubuntu 8.04 server that I used.
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I also use the [[COLOR="DarkRed"]Wordpress[/COLOR]]("http://wordpress.org/") for my home website.

Hope this helps.......

---

### Post by expatCM on 2008-09-09
I think I used Falko's earlier guide in part when I set up my server the first time round.   Thanks for reminding me it is there.

I had not even thought of WordPress for the home website, I was thinking of Joomla ....

---

### Post by cdtech on 2008-09-09
Yes, I use Wordpress and have a photoblog so everyone in my family can upload pic's. I'm using dyndns.com:
> DNS Inc has operated DynDNS as a brand of services starting with a free Dynamic DNS services because some Internet users have IP addresses that change. We created a method that allows users to update the IP address associated with a hostname that we provide, enabling users to serve content or keep connected to their computer.
No need for a mail server; too many problems with my ISP and spam. I just use a gmail relay setup, just to email log files.

Good luck....

---

### Post by schettj on 2008-09-09
I've just moved to drupal from twiki for my home CMS for web. That works well too. Whatever you do, brace yourself for the endless worm probes and rootkit attempts via your web server. mod_security is your friend.

As for secure access for your kids, if you are outsourcing email, why not outsource that as well?

[http://www.xdrive.com/](http://www.xdrive.com/) - 5GB free
[http://skydrive.live.com/welcomemoreinfo.aspx?provision=1](http://skydrive.live.com/welcomemoreinfo.aspx?provision=1) - 5GB free

There are of course ways to provide access to your own machine, but the only one I would trust is ssh based scp, with preshared keys, text login disabled, running on a non-standard port and/or being watched by fail2ban. But then, I'm a little conservative. For a kid, better to just set them up with one of those 5GB in the sky things and be done with it. That, and/or a couple gig usb stick should do it for school.

---

### Post by expatCM on 2008-09-09
I have probably got this wrong but I thought that there was a small problem with the "free" on-line storage solutions. It is free to upload and store but I thought that there was a small daily download limit which is not very adequate ...  this may be increased on payment of a fee .... 

This is how many people get caught out ... they back up their data and their system crashes.  They think they are fine until they need to restore the data and then find out that yes they can but not in the time frame that they need .....

---

### Post by cariboo on 2008-09-09
You can use sftp to up and download files remotely, that way you would only need ssh port forwarded on your router and for protect use denyhosts to stop others from trying to access your ssh server. To use sftp and Nautilus (Places-->Home Folder) in the location bar type:

```
sftp://user@server
```

They will then have access to their home directory.

Jim

---

### Post by schettj on 2008-09-10
> **expatCM said:**
> I have probably got this wrong but I thought that there was a small problem with the "free" on-line storage solutions. It is free to upload and store but I thought that there was a small daily download limit which is not very adequate ...  this may be increased on payment of a fee .... 
After posting the above, I found adrive.com - 50GB free. No limits. Just needs java in a browser, no throttling I could see anywhere.

I set one up for myself, it looked so good ;)

Anyway, indeed you can use ssh, but I really would consider using preshared keys only, no text login setting. Port 22 is one of the favorite brute-force password guessing ports.

---

### Post by expatCM on 2008-09-10
schettj - I must say that adrive.com looks quite amazing.  50GB of file storage for free without restriction.....  that really is good.  I cannot help but wonder what is their business model ....  perhaps it is selling enterprise storage and this is a way of attracting attention.

I think I have heard of pre-shared keys before but really I will need to learn ....  the following link seems to be quite helpful
[http://www.openfsg.org/index.php/Ssh_without_passwords](http://www.openfsg.org/index.php/Ssh_without_passwords)

cariboo907 - thanks for your comment ... it seems like you are thinking along the same track as well ....

---

