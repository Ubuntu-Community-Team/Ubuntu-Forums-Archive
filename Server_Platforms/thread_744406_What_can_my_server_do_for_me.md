---
title: "What can my server do for me?"
date: 2008-04-03
forum: Server Platforms
---

### Post by seepage87 on 2008-04-03
I've put in a lot of work building my server and now I want to get the most out of it  What kind of things can a server do for me?

This is what I've set up so far:
[LIST]
[*]A website including
[LIST]
[*]A wordpress blog
[*]A mediawiki wiki
[*]A Gallery photo gallery
[/LIST]
[*]Proftpd for FTP to access file remotely
[*]Jinzora for media streaming
[*]Torrentflux for a remote controllable torrent client
[/LIST]

I just want to know what else is out there.  An obvious example would be to set up a email server, but I can't guarantee the up time and super-reliability I would want.  What else can I do with the thing?  Are there better options than what I've chosen?

---

### Post by Endwin on 2008-04-03
Generally I don't run a FTP server preferring SSH because it is more secure and less prone to attacks. A SSH server is a must for remote administration at the command line, and installing fail2ban is helpful for anyone trying to brute force the passwords. 

As for other stuff, I personally run my IRC, and IM chats through my server (programs run on the command line) so that I can access them from anywhere. 

SSH also has the advantage that if you install sshfs on a laptop or other client computer you can then mount your server's files securely from anywhere with a net connection. 

Speaking of that File server is always fun place to have and store your personal files, though you may want to setup a RAID array of some kind in case a hardrive dies. 

Want to get really crazy you could get the hardware to plug in your phone line and setup an Astrix PBX server so that you can have personal mailboxes, delivery options like a company for you home phone...

---

### Post by angelmartinezn on 2008-04-03
You can install a jabber server. With a little customization you can make your server alert you via jabber-chat about all critical events in your home (webcam..., webserver performance,...) :)


An ssh forwarded proxy server is very usefull when someone allows you to surf internet  only by port 80.

Of couse, you can have a remote X session via vnc (or nx)

---

### Post by Dr Small on 2008-04-03
How about a MTA (Mail Transfer Agent) such as Postfix for a mailserver?
Also, a SSH server to have full power and control of the system :)

---

### Post by seepage87 on 2008-04-04
I have SSH, I didn't mention it because I thought it was sorta obvious.  I also have an array for my file server

My only concern with sshfs is for the other people who access my server.  Is there a good, easy windows client that could access it?  E.g. my girlfriend really can't handle much, but she'll still want access to her music and TV shows.

---

### Post by phil90 on 2008-04-04
Well what you can do for others and yourself is participate in Boinc which is a platform to compute data for different researches like development new medications...

Boinc

[http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)


According to the a single Linux server can compute the equivalent of thousands of cpus.


Well it not something that is going to give you results right away but it will help research by using your idle computer to cure diseases , predict global warming effects etc.

---

### Post by seepage87 on 2008-04-04
> **angelmartinezn said:**
> An ssh forwarded proxy server is very usefull when someone allows you to surf internet  only by port 80.
This is probably worth doing.  I'm tired of running into random things blocked.  I'll have to look into how to set this up.  Thanks.

---

### Post by hyper_ch on 2008-04-04
how about SSHFS? Mounting folders on your server into your local filesystem...

If you have enough upload speed on your server you could also setup a TOR server and provide a little share to the online anonymity :) Limiting it to 20-30 kb shouldn't impact too much and you'll do the community a favour.

---

### Post by andguent on 2008-04-04
WinSCP is an easy way to go for allowing Windows users access to remote files via SSH. If they can handle a full FTP client, WinSCP will be just as easy.

As for what I use my server for, the number one thing is backups. I like to grab any important file from any important computer, and save it on the raid. That way, three hard drives have to fail before I loose my data, not just one.

To take that a step further, I use Hamachi VPN from logmein.com. I run Hamachi on my server, and on my mom's computer which is 40 minutes away. Every night, my server backs up all important changed files on her computer over the vpn. Even if her house burns down (please no...), at least I can hand her all of her tax records from the last 8 years on a pen drive.

---

### Post by seepage87 on 2008-04-04
I'm afraid it's a little worse than that.  At least my girlfriend and a couple of my roommates really can't handle a full FTP client.  The most I could do is get them fireftp which they still think is just the web browser.

As for Tor, I've got maybe 80k/s up and am struggling as is if I want to stream music from work and have much anything else working.  When I move it will be somewhere they have FIOS and I'm pushing for the 15/15, then I'll spare some bandwidth for tor in a heartbeat.

As far as backup, I'm not allowed to take any data off my work computer, and I already keep my taxes and stuff there, but an automated solution would be better, so I don't have to think about keeping everything there too.  I'll have to look into that as well.

---

