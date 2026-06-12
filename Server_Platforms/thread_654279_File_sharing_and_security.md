---
title: "File sharing and security"
date: 2007-12-30
forum: Server Platforms
---

### Post by DSK on 2007-12-30
Hello All.  Thankyou for taking the time to read my post and hopefully answer some of my questions.  Sorry in advance for the length of this post.

My current network setup at home is that I have a router that has a server in a DMZ, 2 XP clients, 1 wireless Vista client, 1 wireless xp client, 1 awesome Ubuntu  client.

What I would like to do is use the server as a web server for 3 sites, file server both local network and internet, Voip (teamspeak or mumble), game server (MohaSP), Music server(Ampache), and photo server (Gallery 2). (both server and desktop are 7.10)

I currently have the sever performing all these functions but am concerned that I have a million security flaws due to my inexperience and lack of knowledge of method choices.  I am also using DyDNS in my router.

I follow the belief that any computer connected to the internet can be hacked no matter the security used.  But I also believe that doing things right will keep the script kiddies away which is my concern.  I know that each application I install has its own risks that I need to deal with. I just want to make sure from the OS standpoint that I have done things right or the best way.

Also I only need to access the server for local traffic and administration with my ubuntu machine as all the microsoft boxes are used for internet access/gaming.

I will list my questions out here for you:
1) How should I enable network shares from my server to my ubuntu box without the worry of the directories and files being exposed to the internet? (I would like to mount this share in nautilus so I can have a graphical way of moving files)

2)Simular to question 1. I would also like to have shares that I can mount locally and over the internet securily (with restricted access for those with a password and encrypted transfer).  I have read that ftp is not the way to go.

3) Is it better for me to install apps like TeamSpeak from the repository or from source?  I noticed that it works either way but the repo install uses differnt directiories for the files.

4) For apps like gallery2 or Ampache should they be installed outside the /var/www/ directory? Basically what files are meant to be stored in /var/www/ and what file types should never be in there?

5) Am I crazy for not having setup a firewall on the server?

6) I also plan on setting the server up to be a mail server.  Not sure if this impacts any of my aforementioned questions.

I have been searching the web and reading many threads here but still have these questions.  I would appreciate any suggestions or links.

DSK

---

### Post by Dngrsone on 2007-12-30
Having one computer act as a web server *and* internal server is asking for trouble.

My recommendation is to get a POS desktop from somewhere (PII with 512MB RAM and 4GB drive would work fine) and install [Smoothwall Express](smoothwall.org) in a RED GREEN PURPLE configuration.

This will put your web server in a DMZ, protecting your internal network from any possible intrusion via the web server.

Then I'd use a second computer as a server for the internal network, if need be.

Actually, now that I think about it, [ClarkConnect](http://www.clarkconnect.com/) acts as both firewall and server, though in my opinion it isn't as secure as a dedicated firewall.

---

### Post by los santos on 2007-12-31
2) sftp will allow you ftp-like access to your files but with the benefit of being encrypted. you can use the rssh program to restrict access so users will only be allowed to transfer files, not full shell access. [http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206) explains setting this up with a chroot jail which will limit the directories on your server a user can access.

4) /var/www usually contains files used by your webserver, i.e. the html/php/css/whatever 

/var/www would be the appropriate place for ampache, gallery2, etc.

5) It would be better to have a firewall on your server if it is in a dmz since anyone can access it. Alternatively you could keep it on your internal network, not in a dmz, and forward ports 80 and anything else to the server.

good luck.

---

### Post by koenn on 2007-12-31
quite a project you have there. IHere are some thoughts:

**5) Am I crazy for not having setup a firewall on the server?**
You ***need*** a firewall because your exposing a server to the internet. However, the firewall can be implemented on the server itself, or on the router, or even between the two. If your router does NAT, that's a start, because it will block connections to the LAN/DMZ. It should also block connections to itself eg you preferably shouldn't be able to log on to it from the internet-side. 

Also, find out what the router allows in terms of traffic WAN <-> LAN, WAN <-> DMZ, LAN <->DMZ and how configurable all this is. 

**1 & 2 : File sharing **
Having a server in a DMZ but wanting to block certain shares from the internet is indeed a risk. The server is publically accessible, you plan to set up  file sharing as a public service, yet there are things you don't want accessible - tricky. 
At least it's in DMZ and not on your LAN. keep it that way. 
Find out if you can tunnel the filesharing (eg through SSH portforwarding or OpenVPN)

If you only need the shares accessible from your LAN to use nautilus, skip the sharing, install a light file browser (with little dependencies) on the server and export its GUI to your desktop.


**4- /var/www**
I think /var/www is open to the public, and thus should only contain pages that your web server needs to serve up. All the rest belongs in its own dedicated directories, with references to it in the various config files, and accessible by the webserver's user account (usually www-data)


**3- source or repos**
I'd pick repos, because the software there is compiled with options that match the rest of your system. That's also the reason it installs in different locations.

**6- mail**
it will affect your network design and firewall configuration, obviously.

---

### Post by DSK on 2007-12-31
Thanks everyone for the replies so far, very informative.

I would do the 2 server setup except that I have 100 gigs of data that I want accessed on both the WAN and LAN.

I had been looking at IPCop ([http://ipcop.org/](http://ipcop.org/)) for my router using an old pc but decided to use a lynksys setup with DD-WRT([http://www.dd-wrt.com/dd-wrtv2/ddwrt.php](http://www.dd-wrt.com/dd-wrtv2/ddwrt.php)).  Very nice and robust I think.  So I have many options on setting up the WAN<->DMZ,LAN.

I have some reading to do about the suggestions so far.   Keep um coming and I will report back on some of the ideas.

---

### Post by Dngrsone on 2007-12-31
IPCop and Smoothwall started from the same base and went in different directions... accessing the web server form the protected LAN is allowed, sa I recall, just not the other way around without specifically creating pinholes to accomplish that.

---

### Post by HermanAB on 2008-01-01
Hmm, for WAN access, you have to use encryption and the easiest way to do encryption is with SSH.  So, install the openssh package and  to keep script kiddies away, be sure to run sshd on a non-standard port, otherwise the server will be hammered with bazillions of login attempts a few times per day.

Probably the best advice I can give you, is to ensure that you use long passwords of 9 characters or more for all accounts.  I use 16 character semi-pronounceable passwords and my servers haven't been hacked.

Cheers,

Herman

---

### Post by DSK on 2008-01-06
> **HermanAB said:**
> Hmm, for WAN access, you have to use encryption and the easiest way to do encryption is with SSH.  So, install the openssh package and  to keep script kiddies away, be sure to run sshd on a non-standard port, otherwise the server will be hammered with bazillions of login attempts a few times per day.

Probably the best advice I can give you, is to ensure that you use long passwords of 9 characters or more for all accounts.  I use 16 character semi-pronounceable passwords and my servers haven't been hacked.

Cheers,

Herman

Yikes you were correct.  I checked my log file and thank god the brute force did not work yet.
So far:
I set my ssh this way now:
Disallow root
Disallow password authentification
Require Keys with pass phrase
Unique port#

I have removed samba as I dont need windows access
using NFS exports only allowed for non-routable IP's on my LAN.

Ampache and Gallery2 serve the files I need exposed to the internet.

How am I doing?  I feel a lot more secure.  
Still need to iron out all my firewall settings.

I have not looked into creating pinholes and using NAT.

DSK

---

