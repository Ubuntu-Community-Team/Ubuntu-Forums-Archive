---
title: "Help testing server security"
date: 2011-06-29
forum: Security
---

### Post by clegends on 2011-06-29
Hi folks, I'm running a 10.04 Ubuntu server 64 bit edition. It's on a mini-itx box I built, and currently drawing less the 60 watts. I'm using it for hosting an xhtml website, two wordpress blogs, a citadel email service, funambol server, ampache media server, project pier installation, encrypted filesystem backups, and mysql database. 

Recently here in Australia we've had a number of sites hacked and crashed... while I know I'm unlikely to be able to protect myself from everything, I'd love some help from a few knowledgeable people about how to make my server as secure as possible. Other than that, my plan is to keep regular backups, and learn how to reinstall quickly if needed.

As well as the above services, I use ssh to gain access to my server. I have turned on password authentication, but ONLY with the correct certificates, which resides on 2 netbooks. They are infrequently online, with the /home parition of one encrypted.

I don't currently use ftp, and while I have webmin installed, I've configured it so the only way to login is wirelessly through my local network. So yes, if you knew my root password, and were standing out side of my house with a netbook, you could log in as root. Currently this is disabled for any traffic coming from the internet, so I'm not as concerned. 

That said, I would love some tips about security, and how to avoid the crash and burn that seems to come from recent attacks on other servers. Would be happy to point some people at my server to see how many security vulnerabilities you can help me uncover. I have already done a lot of reading, so would appreciate targeted help with my particular installation. Thanks in advance for your help. Cheers. 

~clegends

---

### Post by guzjd on 2011-06-29
Please reference the offical server Security documentation at [https://help.ubuntu.com/10.04/serverguide/C/security.html](https://help.ubuntu.com/10.04/serverguide/C/security.html).
 
Also feel free to look at the community supplied content at [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by clegends on 2011-06-29
Yes, I believe I said I've already done lots of reading. I have seen those links already, but what I'm hoping for is more targeted advice for my particular installation. Thanks.

---

### Post by guzjd on 2011-06-29
You may have done some reading but you didn't state what you have read, so I started with the Ubuntu content. Sounds like you need a hardening guide for your server. 
 
You have done a lot of good things and some other things I wouldn't have done unless necessary. 
 
Ultimately, I don't think we are qualified to help you harden your server as you know your environment and requirements best.
 
However, I would say to better understand how to secure your server you should perhaps research Threat Identification, Risk Management, Application Security (per application) and Incident Response. I gather that you are Australian, but I know the U.S. has a lot of Cyber Security, and Information Assurance groups, like the US-CERT, NIST, and NSA as an example. 
 
This site appears to be similar to the US-CERT: [http://www.auscert.org.au/](http://www.auscert.org.au/)

---

### Post by Dangertux on 2011-06-29
> **clegends said:**
> Hi folks, I'm running a 10.04 Ubuntu server 64 bit edition. It's on a mini-itx box I built, and currently drawing less the 60 watts. I'm using it for hosting an xhtml website, two wordpress blogs, a citadel email service, funambol server, ampache media server, project pier installation, encrypted filesystem backups, and mysql database. 

Recently here in Australia we've had a number of sites hacked and crashed... while I know I'm unlikely to be able to protect myself from everything, I'd love some help from a few knowledgeable people about how to make my server as secure as possible. Other than that, my plan is to keep regular backups, and learn how to reinstall quickly if needed.

As well as the above services, I use ssh to gain access to my server. I have turned on password authentication, but ONLY with the correct certificates, which resides on 2 netbooks. They are infrequently online, with the /home parition of one encrypted.

I don't currently use ftp, and while I have webmin installed, I've configured it so the only way to login is wirelessly through my local network. So yes, if you knew my root password, and were standing out side of my house with a netbook, you could log in as root. Currently this is disabled for any traffic coming from the internet, so I'm not as concerned. 

That said, I would love some tips about security, and how to avoid the crash and burn that seems to come from recent attacks on other servers. Would be happy to point some people at my server to see how many security vulnerabilities you can help me uncover. I have already done a lot of reading, so would appreciate targeted help with my particular installation. Thanks in advance for your help. Cheers. 

~clegends

Keep in mind I have not done an in depth analysis of your implementation of any of this so any information I give is going to be basic at best. Security is in the details. Something which I don't have access to here. 

Right off the bat though, I see some problems. 

+ Separation of resources, you are running an aweful lot of services on one machine. While I understand that this might be intuitive toward the economic decision to build a home server, security wise it is best to not put all your eggs in one basket.

**Possible Improvement :** Use multiple machines, or virtualization to separate your resources.

+ The next big thing I see is the root login, while I know you say the person has to be on your network to log in ,that is not necessarily true. The person has to APPEAR that they are on your network. Which does not necessarily mean that they have to be in your front yard. 

**Possible Improvement :** Consider disabling root login, use strong passwords, use rsa keys to authenticate. 

+ You have a wireless network. This in and of itself isn't bad, but is obviously an easier entry route then a wired network.

**Possible Improvement :** Make sure you're using WPA not WEP, preferably with non public shared key method (if your router supports it). If not, make sure you are using a STRONG pass phrase, at least 32 characters, not based on dictionary words, containing , numbers, upper case letters, lower case letters, and special characters.

+ You have not mentioned anything about firewalling (at least not directly). Which of your services if any are exposed to the internet?

**Possible Improvement :** Make sure only services that NEED to be accessible from the Internet are, use iptables/netfilter to control access. As well as server specific bindings. Example : Your MySQL server does not need to be visible to anything but the process accessing it. SSH can stay internal as well unless you have a need to access the system remotely.

+ You are running a webserver.

**Possible Improvement :** Make sure you harden your web server, there are many good Apache hardening guides just google one. Are you forcing SSL for all logins and any user input? If not configure SSL , particularly for those blogs.

+ About those blogs, Wordpress is notoriously exploited. The current version is reasonably secure.

**Possible Improvement :** Keep Wordpress up to date, beware of Widgets and Wordpress addons, the coders who write them don't always validate user input. Audit them yourself, if you don't know how, I suggest learning PHP it's great knowledge if you are planning on securing a web server.

+ You are running an email server

**Possible Improvements : ** HARDEN IT, I suggest spending most of your time here, email servers are HUGE targets. Make sure if nothing else you're not running as an open relay.

+ Operating System Hardening , do it well and do it often. Keep up to date on the latest Ubuntu security advisories. 

**Possible Improvements :** Keep regular updates if you are not. Harden sysctl.conf if you haven't already. Consider installing a "secure" kernel, create Apparmor profiles for everything you run. (Or SELinux if that is your poison of choice). VERIFY YOUR FILE PERMISSIONS, I can't stress this enough, you need to know what can read and write where, and make sure it is appropriate.

+ Familiarize yourself with the latest threats, you're running a server now. You will spend the vast majority of your "Administrative Time" looking at the latest exploits. If you're security conscious you will anyway.

**Possible Improvements :** Educate yourself better on how exploitation works, learn to pen-test your own server. At least run vulnerability scanners against it. These are my suggestions.

- Port Scans and footprinting : nmap 
- Web Vulnerability Checking : Skipfish
- Additional Vulnerability Scanning (this is a catch all for the two above but nice tool to have) : Nessus , it is free for home use, not for corporate. 

Also , add an IDS to your list of services so you can accurately determine what attack methods apply to you from a statistical standpoint. This will allow you to have a more targeted approach in your security measures, instead of just scattergun hardening and hope you plug most of the holes.

For now those are my suggestions, if you post more information I will help as much as I can.

---

### Post by clegends on 2011-06-30
Wow, Thanks so much for that. I've got a lot of work to do...lol. I will definitely post back later, but for now I have enough to do trolling through the info you've given me. Thanks heaps.

---

### Post by wacky_sung on 2011-06-30
You can make your server secure but you can never beat DDOS least you run cloud servers with plenty of bandwidth to defeat it.

In additions, you must know how to isolate your network for each of the service you wanna incorporated so that if one get affected it will not cause an impacted to another.

This is just my recommendation.

---

### Post by clegends on 2011-06-30
My understanding is that DDOS attacks ping your server repeatedly until it crashes... under such a situation, what other damage can it do? I.e, if I just reboot, (assuming the attacks don't continue) will there be any other effects and/or damage. Keeping in mind I run a single server that (currently) I have access to most of the time... it is fairly easy for me to reboot, and/or plug a monitor and keyboard into it if I can't ssh into my box.

Virtualization is an interesting concept, however for my uses I wonder about the resource useage. I.e., I have one relatively low-powered server... 1.6 Ghz dual-core processor, and 2 Gb of Ram. While for my uses I would never use all of that, if I virtualized each process in a seperate instance of a virtualized server... here is where my knowledge of servers leaves me... with my desktop experience I would say this wouldn't be too efficient, however servers are a different beastie...

I have wondered about creating a chroot jail for different services though. I know that apparmour runs by default, so perhaps a better choice would be working with that first. Re separating all my services... under my current setup, that would be difficult. In particular I'm thinking about my Mysql databases, kept in one instance of a running Mysql server. If someone hacked into this, or even if it crashed, I'd be in trouble, but as I'm keeping backups of this I'm not as concerned.

I'm interested in hardening my server as much as possible, given the confines I've listed above. That said, it's small enough, and local enough, that my worst case scenario should be restoring it all (or reinstalling, if it comes to that) from an external disk drive. 

Re ssh, I use this over the internet, as well as from my home network. As well as needing a password, I have set access to ONLY being available with the correct certificates, located on 2 other devices. What security risks are possible with this setup? And advice above taken about webmin... and the root password. I'm uninstalling it, as the only thing I've been using it for has been for my iptables firewall. Love the GUI for that, but will find another option. Everything else I do is through the commandline.

---

### Post by wacky_sung on 2011-07-01
> My understanding is that DDOS attacks ping your server repeatedly until it crashes... under such a situation, what other damage can it do? I.e, if I just reboot, (assuming the attacks don't continue) will there be any other effects and/or damage. Keeping in mind I run a single server that (currently) I have access to most of the time... it is fairly easy for me to reboot, and/or plug a monitor and keyboard into it if I can't ssh into my box.

It will just make you unable to access your internet at all even after your countless reboot until the attacks stop. All your system resources will be hitting to the maximum.Probably you need a good experience being hit by zombies, then you will understand what i meant.As for current solution to defeat zombies attacks is big pool of bandwidth running in cloud servers.

---

### Post by cprofitt on 2012-04-01
I just completed a red-team blue-team exercise this weekend and one of the issues that caught the blue-team was the fact that webmin allowed the following?


port 10000

login user:  admin
password:  blank

check 'remember me'

this allowed the red-team to change the root password and then login via other services.

I still have to test webmin on Ubuntu since I am not sure if this was the particular setup of the exercise or a default initial configuration.

---

