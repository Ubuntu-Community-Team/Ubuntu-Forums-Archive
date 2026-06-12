---
title: "Ubuntu Server help"
date: 2013-05-23
forum: Security
---

### Post by rockymin on 2013-05-23
Hello,
   I have an Ubuntu 10.04 server that is hosting websites among other things.  I have recently been having issues with it where I can't connect to it or any websites or anything, when I check the server the disk activity light is steadily blinking.  I reboot the server and everything is ok again for a day or two.  I found some malware/viruses on it and removed the infected files but it still keeps happening.  I have also been checking logs but have found nothing that indicates what could be causing it.  It appears to be a DoS attack or something.  Can someone help me troubleshoot this issue?  I was trying to find a process log that might show what processes were running when the issue occurs but I haven't found anything yet.  Thanks for any help in advance.

---

### Post by SeijiSensei on 2013-05-23
What do you see in the Apache logs at /var/log/apache2?

I'm very puzzled by the malware comment.  Linux servers rarely have such problems.  Do you have a log of what malware was removed?  Did you consult any of the online databases to see what these little buggers might be doing?

If these were Windows viruses, then I think your server may have been compromised.  

I presume you are running a solid firewall, with only the ports you need open to the world?  If all this machine is doing is serving up websites, you shouldn't need to have any ports other than 80 and 443 open for web services, and perhaps 22 for SSH.  What kinds of "websites" are these?  Simple HTML pages only, or web applications in a language like PHP?  If these are home-grown applications, inexperienced coders can leave the application open for exploitation.  If these are packaged applications like WordPress, you need to insure you are running the most current versions at all times, since they are prime targets for exploitation.

I suggest scanning the machine across the Internet with **nmap** to see what ports are open.

---

### Post by tgalati4 on 2013-05-23
What is the status of your RAM and hard disk space?

```
free
df -h
```

If you run out of either, that could give the impression of denial of service.   Install *htop* and monitor your server from another machine by logging in via ssh.  Look for CPU%, IOWait, and any stuck processes.

---

### Post by matt_symes on 2013-05-23
Hi

> Can someone help me troubleshoot this issue?

Yes. Take the box off line and then..

Read up on how to lock your box down.

Read up on where the log files are.

Read up on what is normal activity for your box so you know what is abnormal activity.

Read up on app armor, tripwire, iptables, failtoban, mod-security, lowest permissions, minimal open ports, sysctl settings etc.

A good place to start is with the security stickies in the security sub forum. 

It seems to me that you have a box connected to the net and you are not sure how to lock it down and not sure how to find out if you are compromised. You have no idea what is normal activity and abnormal activity for the box.

Once you know how to lock down your machine, and what to look for in the event of a compromise, then connect it back to the Internet.

I may sound a bit harsh, however i really don't want to see you get compromised.

Kind regards

---

### Post by rockymin on 2013-05-23
> **SeijiSensei said:**
> What do you see in the Apache logs at /var/log/apache2?

I'm very puzzled by the malware comment.  Linux servers rarely have such problems.  Do you have a log of what malware was removed?  Did you consult any of the online databases to see what these little buggers might be doing?

If these were Windows viruses, then I think your server may have been compromised.  

I presume you are running a solid firewall, with only the ports you need open to the world?  If all this machine is doing is serving up websites, you shouldn't need to have any ports other than 80 and 443 open for web services, and perhaps 22 for SSH.  What kinds of "websites" are these?  Simple HTML pages only, or web applications in a language like PHP?  If these are home-grown applications, inexperienced coders can leave the application open for exploitation.  If these are packaged applications like WordPress, you need to insure you are running the most current versions at all times, since they are prime targets for exploitation.

I suggest scanning the machine across the Internet with **nmap** to see what ports are open.

It is behind a firewall with only needed ports open, in addition to Apache, it is running ftp and postfix.   The sites are using Wordpress and Joomla and the virus was found in some php files.  The malware detected was called php.backdoor.trojan.  I looked it up and did the necessary removals I found.  It looked like it was ok afterward but the issue ended up still happening.  Thanks again.

---

### Post by rockymin on 2013-05-23
> **matt_symes said:**
> Hi



Yes. Take the box off line and then..

Read up on how to lock your box down.

Read up on where the log files are.

Read up on what is normal activity for your box so you know what is abnormal activity.

Read up on app armor, tripwire, iptables, failtoban, mod-security, lowest permissions, minimal open ports, sysctl settings etc.

A good place to start is with the security stickies in the security sub forum. 

It seems to me that you have a box connected to the net and you are not sure how to lock it down and not sure how to find out if you are compromised. You have no idea what is normal activity and abnormal activity for the box.

Once you know how to lock down your machine, and what to look for in the event of a compromise, then connect it back to the Internet.

I may sound a bit harsh, however i really don't want to see you get compromised.

Kind regards


I really can't take it offline for any extended period of time.  I've been trying to read up on this but most of the stuff I have found is very confusing and all over the place.  I can't seem to find straight answers to any questions I have.  That is why I am here.  I am a 20+ year Windows engineer and new to Linux.

---

### Post by matt_symes on 2013-05-23
Thread moved to **security discussions**.

---

### Post by matt_symes on 2013-05-23
Hi

Do you have a known clean backup you can revert to ?

I would really suggest taking the site down until you know exactly what has been compromised.

It sounds like the exploit may have been in apache, php or ftp.

From what i have read, it seems that the backdoor may allow one to get a remote shell on the target machine. It's classed as a severe exploit.

I moved it to this subforum to get some eyes on it for you.

First of all, check out this site and check your php security settings.

[http://phpsec.org/projects/phpsecinfo/](http://phpsec.org/projects/phpsecinfo/)

FTP is insecure. Consider SFTP instead. Any reason you must use FTP ?

What security have you added to lock down the box ?

Kind regards

---

### Post by SeijiSensei on 2013-05-23
I just did a Google search for "php.backdoor.trojan" and found many articles about it.  It seems to be a problem with [insecure Wordpress sites]("http://www.warriorforum.com/programming-talk/643952-website-hacked-backdoor-trojan.html").

I just checked my WordPress site.  It is running 3.5.1 which is reported as the latest version.  If you are running an earlier version, you need to update.  Personally if it were me, and I had full control over the server, I'd install a fresh copy of 3.5.1 in a new directory.  Each site has only a few customizations like themes plus the contents of the associated database, so it should be possible to build a clean version by carefully selecting just the files you need from the current site(s).  

Some of the articles in the Google search reference tell-tale indications of this trojan like files named 404.php.

---

### Post by rockymin on 2013-05-29
> **matt_symes said:**
> Hi

Do you have a known clean backup you can revert to ?

I would really suggest taking the site down until you know exactly what has been compromised.

It sounds like the exploit may have been in apache, php or ftp.

From what i have read, it seems that the backdoor may allow one to get a remote shell on the target machine. It's classed as a severe exploit.

I moved it to this subforum to get some eyes on it for you.

First of all, check out this site and check your php security settings.

[http://phpsec.org/projects/phpsecinfo/](http://phpsec.org/projects/phpsecinfo/)

FTP is insecure. Consider SFTP instead. Any reason you must use FTP ?

What security have you added to lock down the box ?

Kind regards

Hi Matt,
     Thanks for the reply and sorry for not replying sooner.  I'll have to ask why they are using FTP instead of SFTP.  I'm not a developer and I didn't set the box up.  I have been looking into adding security beyond the normal stuff of changing passwords and things.  The machine is behind a firewall with only the needed ports opened.  Most of the security software I've seen for Linux seems complicated to install and has warnings that beginners shouldn't mess with it.  I'll have to speak with the developer regarding php.
    Also, the lockup problem may not have been a virus after all.  I found I had misconfigured a cron job last week and it was running many times in the process list.  I changed it to run once a night and it has been working well since then (knock wood).  However, I would welcome any security recommendations you might have, but remember I am a very new beginner with Linux and am afraid if I do or type the wrong thing I won't be able to fix it. 

Also, I was wondering if there is a way to monitor for file changes and maybe send an email when a file is changed, perhaps run as a cron job a couple of times a day?
Thanks.

---

