---
title: "A noob with an Ubuntu Server 21.10 on a Rpi 8gb running Nexcloud!"
date: 2022-04-16
forum: Server Platforms
---

### Post by greyacid on 2022-04-16
[I]Hi all!
It was recommended to post the below question on the ubuntu forums as well, I hope I have found the correct sub forum![/I]


Noob here, tried to create a nextcloud instance for about a month now, following various guides and failing.
Found Learn Linux TV’s guide so I installed Ubuntu 21 on my Pi and went to town.
It worked! :D


But I have a few questions and I’m hoping you could help me with it:


1) In my previous attempts (following addicted2tech.net’s pi guide) I stated an instance of NGINX and linked a certificate for my home domain to cloudflare.
    I’ve installed portainer and Cloudflare DDNS to keep the update of IP so it should work a-ok.
    When I followed learn linux’s guide my domain is still padlocked.
    If I add a certbot and an SSL cert to my apache2 then I can’t connect to my nextcloud as it’s redirecting too many times (I’m assuming - the warning is ‘something went wrong’).
    How can I get rid of the HSTS warning without an SSL certificate?
    I’m assuming my nextcloud is safe thanks to the padlock and the link being proxied through cloudflare but when I add the *Header always set Strict-Transport-Security “max-age=15552000; includeSubDomains”* it doesn’t get rid of the warning.
    Any thoughts?


2) CalDev, Calddar…
    If I understand correctly you need to add a redirect to the ssl file again?
    TBH I don’t need either a caledar or contacts details - I’ve already removed them - but the warning is still there :#
    How can I dismiss them?


3) SMTP!!
    I don’t want the mail ability to be honest, any password changes will be done locally and I don’t want to provide mail as everyone in my house is happy with gmail for now (that’s different battle that I just don’t have the knowledge to fight!).
    How can I give Nextcloud simple mail access?
    A thunderbird program in my windows desktop?
    My personal GMail account?
    Does it need it?
    And how would I secure it with no SSL??


4) I would like to add four hard drives in a raid 5 config to store my family’s photos and documents (via nextcloud), could anyone recommend a simple to follow guide for changing the data store path to the raid instance I will create the mdadm?
    
5) I also have a HDD I want to use as a backup for everything - the server, the data in nextcloud, everything. Could someone recommend a simple to follow guide for copying the contents of both the HDD of ubuntu and the raid of nextcloud once it’s set?


Sorry for a lot there, but thank you for any help to the above, it will be very much appreciated as I am a complete novice at this but enjoying the ride!  :cool:
All the best.

---

### Post by TheFu on 2022-04-17
I run nextcloud, but not on a raspberry pi.  I have 2 Pis, but I don't put data on them. They are client-only devices - basically music and video players. They get content over the wired network from real computers and real storage.  With that said ... 

The only containers I use are LXD.  My nextcloud instance runs inside a full VM, though I've been planning to move it into an lxd container for about 5 months.  Life gets in the way and LXD has some problems that don't make me happy (snap packaging mainly).  As for the container technology itself, I prefer lxd over all the others, but that could be just because it is most like a VM.

I like Cloudflare's DNS, but don't use their stuff for anything else.  Sorry.

As for certs, I use Let's Encrypt, but terminate my TLS (don't use SSL!!!!) connections on a reverse proxy, not on the nextcloud system. My reverse proxy runs nginx. I use **acme.sh** to manage the LE certs there.  The other LE cert managers I looked at either didn't work quickly or had some dependency I didn't want to load. acme.sh is pure bash. I like that.  Simple and works.

Strict-Transport-Security is a warning I see too.  But I don't allow access to nextcloud from the internet, without running either a full VPN that I host or using a SOCKS5 proxy over ssh.  Both require authentication to access the network and both are considered secure enough for internet use.  No way would I put nextcloud on the internet for all the hack at day and night.  BTW, TLS/SSL don't provide security. They just ensure that the communications between the client and server are unmolested.  All versions of SSL and TLS v1.2 and earlier have been cracked.  Only TLS v1.3+ are not believed to be cracked today.  Using v1.2 means that someone else, if they can get the packets, then they can read them.  Gotta keep those family recipes secret, right? /s

I don't use CalDAV on Nextcloud.  I have a communications server that holds all my contacts in an LDAP directory.  That server has been running 10 yrs longer than nextcloud here, so I don't plan to change.

I tried to get email in nextcloud connected to my email server. Sometimes it worked, but so much more often it didn't so I gave up and removed the mail addon from nextcloud.

Not that this will help you, but my main use of nextcloud is for an RSS feed consolidation server. My tablet, phone, and computers all have the same view of news stories and if any of them 'read' the story, it isn't shown on any other client.  That helps me stay sane.1

I barely use the 'Files' part of nextcloud.  There are better tools, IMHO, like sftp or sshfs.  Both are easily supported on any Linux desktop from anywhere in the world.

Notes - this is where I put tiny tidbits like shopping lists - by store - and copies of the US Constitution, stuff I'd like to refer back to on a whim.  When I'm the lunch guy - going out to pick up food for everyone, I'll put their orders in a Note and ensure it is sync'd with my phone before leaving. (I don't have a data plan on my phone).

Photos/Gallery is flashy, but not the best tool.  Over a slow connection, it is painful to use.  Because I don't really trust NC, my photos are in a different gallery system and read-only access is provided to nextcloud using NFS.

Audio/Music files ... the nextcloud apps really suck. Who wants to playback very limited audio files in a full web browser?  Again, the audio files are read-only to nextcloud. I much prefer using either mpd servers at home (my raspberry pis both run mpd) or I'll download 20G of music to the tablet/phone for trips.

NC-Talk is amazing!  It is a way to have a teleconference with family and friends. I doubt a raspberry pi has sufficient power to handle this. Basically, it is a private video/audio conferencing solution with clients on every platform or a webrtc capable browser works.  Because I'm running the server, I know the encryption for the video and control who gains access based on their current IP address, since not everyone I might invite will have ssh or VPN access into my network.

NC-Contacts - is fine. I dumped my LDAP contact database to a form that the Contact NC app could import. There is an android NC-contacts app. It works, I suppose.  To me, much better than allowing google or any other contact manager access to all my friends and family.  That would be rude to hand over all that data to someone else without permission, right?

NC-Calendar - I tried to get this connected to my communications server where I keep my real calendar. Don't think it ever worked.  OTOH, that other suite of programs can connect to 50 other calendars, 200 other email addresses (including gmail), and allow me to access all of those from a central location. Plus that other suite works and has worked for nearly 15 yrs.

Some other NC apps I have loaded - PhoneTrack, GPXTracks, GPXMotion ... these use gps tracking either live or from gpx track files during trips to capture where the device has been.  I'm a bit of a GPS nerd and love hiking all over the world.  Having a group of gpx files from Japan, Alaska, Patagonia, Africa, Turkey, Central America, Nepal, Thailand, and all over the USA ... plus lots of other locations, is something I find enjoyable.  These apps can play back the track on a map at almost any speed.

RAID over USB is a bad idea.  Just saying.  Be certain you still have normal backups for the data. RAID never replaces backups. Never.

When setting up backups, use a real backup tool.  1 copy isn't sufficient. Having versioned backups is important. There are lots of tools for this. Really need to open a completely separate thread just for backups.  And be 100% certain you can restore those backups.  That's the most important aspect.  Every time I think something is simple, someone else points out that it isn't, so I won't recommend anything.  I've posted a number of scripts here for doing backups, but they aren't the be-all, end-all for anyone. They are just a place to start. Noobs tend to not be able to use them - they haven't made the mind shift to think in the Unix way, so some concepts aren't automatically understood by them. They have too much MSFT baggage in the way.

For all the stuff you seem to want, you'll need a vast skill set that no single person is likely to have.  The best place to get good guidance that I know is to join a virtual LUG and see of those people aren't willing to help.  My LUG meets weekly both online and at a local restaurant. There are monthly meetings with presentations, but the weekly ones are more about 1-on-1 help.  All experience levels are welcome, so that shouldn't be any barrier.  What most LUGs will easily provide is warning about what can be done and what should be done. Those don't always overlap.  There are some things that lots of people do, which are really bad ideas (RAID over USB).

And I just saw this ... does nextcloud need email?  No.
SSL/TLS are not security. It is a very common misconception. They don't block bad guys from hacking your system or prevent botnets from gaining remote access.  Learn that now.  [https://www.youtube.com/watch?v=eRWbNno4sN4](https://www.youtube.com/watch?v=eRWbNno4sN4) explains what TLS is and why it is important, but it definitely is NOT security.

---

### Post by greyacid on 2022-04-17
Thanks for the reply! 
Much appriciated!

> I run nextcloud, but not on a raspberry pi.  I have 2 Pis, but I don't put data on them. They are client-only devices - basically music and video players. They get content over the wired network from real computers and real storage.  With that said ...

Hmmm... you've given me food for thought mate.
 I think I was so doggedly determined to get nextcloud working I never stopped to ask if it's what I wanted in the first place.
All the positives you'v experienced are things I don't want, and the negatives are things I *do!*
I want a simple cloud storage solution and a place for my family to sync their phone photos so it can be backed up once a week - I only looked at internet access to allow connection to apps.
Maybe I should take a moment to reconsider this entire approach.

I would hate to start again, *yet again*, and the ability to google <problem> + ubuntu is refreshing, do you know of a lite photo backup program that would work on ubuntu (and that has an app?)
If not then maybe I should go back to rasbian...

> Strict-Transport-Security is a warning I see too.  But I don't allow access to nextcloud from the internet, without running either a full VPN that I host or using a SOCKS5 proxy over ssh.  Both require authentication to access the network and both are considered secure enough for internet use.  No way would I put nextcloud on the internet for all the hack at day and night.  BTW, TLS/SSL don't provide security. They just ensure that the communications between the client and server are unmolested.  All versions of SSL and TLS v1.2 and earlier have been cracked.  Only TLS v1.3+ are not believed to be cracked today.  Using v1.2 means that someone else, if they can get the packets, then they can read them.  Gotta keep those family recipes secret, right? /s

*Oh... *Here I was thinking it would be relatively safe :lolflag:


> RAID over USB is a bad idea.  Just saying.  Be certain you still have normal backups for the data. RAID never replaces backups. Never.
Yeah I've read that so hopefully I have it covered! I use the raid for redundancy of access and use an attached hdd for storage.
I read that Rsync was a good method, but honestly I'm open to suggestions as I'm still new to all this!

> For all the stuff you seem to want, you'll need a vast skill set that no single person is likely to have.  The best place to get good guidance that I know is to join a virtual LUG and see of those people aren't willing to help.  My LUG meets weekly both online and at a local restaurant. There are monthly meetings with presentations, but the weekly ones are more about 1-on-1 help.  All experience levels are welcome, so that shouldn't be any barrier.  What most LUGs will easily provide is warning about what can be done and what should be done. Those don't always overlap.  There are some things that lots of people do, which are really bad ideas (RAID over USB).
I see...
So a quick and easy solution to keep the family happy might be out of the question after all! :P

> And I just saw this ... does nextcloud need email?  No.
Swish! One less problem!

---

### Post by CharlesA on 2022-04-17
> **greyacid said:**
> 1) In my previous attempts (following addicted2tech.net&#8217;s pi guide) I stated an instance of NGINX and linked a certificate for my home domain to cloudflare.
    I&#8217;ve installed portainer and Cloudflare DDNS to keep the update of IP so it should work a-ok.
    When I followed learn linux&#8217;s guide my domain is still padlocked.
    If I add a certbot and an SSL cert to my apache2 then I can&#8217;t connect to my nextcloud as it&#8217;s redirecting too many times (I&#8217;m assuming - the warning is &#8216;something went wrong&#8217;).
    How can I get rid of the HSTS warning without an SSL certificate?
    I&#8217;m assuming my nextcloud is safe thanks to the padlock and the link being proxied through cloudflare but when I add the *Header always set Strict-Transport-Security &#8220;max-age=15552000; includeSubDomains&#8221;* it doesn&#8217;t get rid of the warning.
    Any thoughts?

Are you proxying through Cloudflare with their SSL enabled? I ran into a similar issue to that when I moved my site and put cloudflare in front of it. I don't remember what the root cause of the issue was, but it had something to do with DNS.


> 3) SMTP!!
    I don&#8217;t want the mail ability to be honest, any password changes will be done locally and I don&#8217;t want to provide mail as everyone in my house is happy with gmail for now (that&#8217;s different battle that I just don&#8217;t have the knowledge to fight!).
    How can I give Nextcloud simple mail access?
    A thunderbird program in my windows desktop?
    My personal GMail account?
    Does it need it?
    And how would I secure it with no SSL??

My take on doing local SMTP is: Don't. My ISP blocks outbound mail, so I just use a third party to handle my mail.

If I need to set up email notifications from my server, I send them through as a relay to that service. I'm not sending it to different users, though.

Mail as a whole is a whole other ball of wax.. especially when you start to deal with mail actually getting delivered and not getting flagged as spam. If you don't need email with NextCloud, I would skip it tbh.

---

### Post by TheFu on 2022-04-17
Whether nextcloud is safe or not cannot be answered in a vacuum.  

How safe anything is on the internet is extremely dependent on the abilities of the team running the services, recognizing issues, and closing each either before making it available over the internet or setting up a few other layers of protection.

BTW, you do realize that support for 21.10 ends in July, right?   No more patches when that happens.

---

### Post by DuckHook on 2022-04-18
> **greyacid said:**
> &#8230;I think I was so doggedly determined to get nextcloud working I never stopped to ask if it's what I wanted in the first place.
All the positives you'v experienced are things I don't want, and the negatives are things I *do!*
I want a simple cloud storage solution and a place for my family to sync their phone photos so it can be backed up once a week - I only looked at internet access to allow connection to apps.
Maybe I should take a moment to reconsider this entire approach&#8230;

&#8230;So a quick and easy solution to keep the family happy might be out of the question after all&#8230;
I love my Nextcloud. It solves so many problems that I had no answer for in the past. But it is only useful if implemented properly. In no particular order, here are things of especial note below:

Re: RPi

I highly discourage RPi's for Nextcloud. NC is not a lean platform. It's meant to act as a cloud replacement: essentially, to allow us all to be our own Google. This is heavy stuff and running it on a toy atop a SD card is like strapping a rocket engine to a tricycle. It's a poor foundation for real world use and will eventually sour you on NC for reasons that are not NC's fault. Use a serious server for this serious platform.

Re: RAID over USB

I can personally attest to how bad an idea this is. Recently, I did this as a lark which resulted in nothing but predictable data loss and much wailing and gnashing of teeth. USB is unreliable, brittle and incomplete. It is categorically unsuitable for a server environment. You cannot even properly check drive health over USB and using it for purposes as critical as server use is most unwise. Again, this is a result of you using a RPi. Switch to a real server and this limitation disappears.

Re: Nextcloud tutorial and setup

You've already done your setup, so the following may just muddy the waters unnecessarily. However, I thought you still might like to know about an alternative.

After a number of false starts, I set up my Nextcloud using the following tutorial: [https://www.linuxbabe.com/ubuntu/install-nextcloud-ubuntu-20-04-apache-lamp-stack](https://www.linuxbabe.com/ubuntu/install-nextcloud-ubuntu-20-04-apache-lamp-stack)

LinuxBabe has a large number of implementation tutorials. They are not the simplest, but I've found them to be complete and to give the fewest post&#8209;installation problems. For example, many NC tutorials do not properly address HTTPS and most entirely skip optimization (redis, PHP memory, file size limits).

I found that other tutorials led me down the wrong path, which I only discovered after the fact. Example: there is an install script from Nextcloud itself that I tried first. While the script did successfully install NC, I found out later that it used PostgreSQL instead of MariaDB. Why on earth would NC's quasi&#8209;official script use a database that is not supported in their official docs? It's a waste of time and energy to discover shortcomings only after you've completed an install and started depending on it. But because LinuxBabe's tutorials start out more complete, many of those shortcomings are either forestalled or can be planned around from the outset. 

Re: Containment

Just to confuse you further, I installed NC into a LXD container. This has given me far more power, flexibility and security than installing on bare metal. However, this adds another layer of complexity (and difficulty) to the install. Once done though, the added functionality is very rewarding: it is now a piece of cake to clone NC (including its contents, database and all data) across separate machines for a high level of redundancy.

Re: your choice of Impish

Why are you running NC (which requires the stability of an LTS) on a standard release? Stick to LTS. It's the only proper way to run a long term server.

Re: NC and E-mail

It depends what you mean by email. It is useful to have just the client set up. This is NC's default behaviour and will allow it to send system alerts, etc out to the admin. It is also useful for initial signups. However, it is not necessary to run a full SMTP server and that's where I fully agree with my betters: fully fledged email is a can of very squiggly worms.

Re: Security

We all have different risk tolerances and security profiles.

I run NC not just for myself but for a select group of family. They in turn are not geeks and connect to it through an assortment of mobile devices. Therefore, offering it through tight security like VPNs is not practical.

On the other hand, the fact that they are now free of commercial data vampires&#8212;whose cloud offerings are merely fronts for their real data&#8209;slurping agenda&#8212;constitutes a gain in privacy and data sovereignty that dwarfs the security risk posed by Nextcloud.

You can take further precautions like sandboxing, proper versioned backups, fail2ban, 2FA, enforced complex passphrases and geo&#8209;restricting IPs, but at some point, it has to be convenient enough to be usable. Otherwise, what's the point in running it in the first place?

---

### Post by TheFu on 2022-04-18
Rocket engine on a Trike?  [https://www.youtube.com/watch?v=mNf2WmH7mFU](https://www.youtube.com/watch?v=mNf2WmH7mFU)  - not exactly a toy.  <rbg> As a rocket scientist, felt I had to put that video in.  The original point is valid.  Some r-pi systems can boot from USB and don't need a microSD, however.

LinuxBabe - I've used a few of her setup guides and found them to be mostly complete, but she can't know your network or your environment to address issues that happen there.  Once I made a suggested edit and she included it in her guide.  I suspect it was for the nextcloud guide, but I don't recall. Sometimes I just use her stuff for some not-so-clear stuff that I've missed to get things working.

I like the LXD container for Nextcloud, but still need to migrate my NC install into it.  I did pull a wallabag install from the NC virtual machine and placed it into a wallabag dedicated LXD container on slower, older, hardware. It is definitely faster than it was inside a VM, even though the VM has 40% faster hardware. Wallabag used to take 5 seconds to save a 'bagged' webpage. Now it is sub-second.  FYI, wallabag is like the, now dead, Google Reader ... just self-hosted without all the tracking that cloudy solutions do.

> You can take further precautions like sandboxing, proper versioned backups, fail2ban, 2FA, enforced complex passphrases and geo&#8209;restricting IPs, but at some point, it has to be convenient enough to be usable. Otherwise, what's the point in running it in the first place? 
Very well stated.
If running nextcloud on your home LAN, please setup a different LAN subnet for internet-facing services. Don't allow wifi or other desktops on the same subnet as internet-facing servers.  Please.

```
internet-Router
|____LAN1 (10.40.1.x/24)
|    |____desktops (wired ethernet)
|    |____trusted_systems
|    |____internal_Servers
|____LAN2  (172.20.1.x/24)
|    |____external_Servers
|    |____nextcloud
|____LAN3 (192.168.60.x/24)
     |____gaming-systems
     |____chromecast
     |____roku
     |____IoT-junk
     |____wifi-n-untrusted-devices
```

Then setup the firewall rules on the router to only allow the exact connections required between each subnet.  Security begins with network security.  It is very hard to apply retroactively.  Assume someone hacks into the nextcloud server.  They shouldn't be able to get to any other LAN from there.

IoSh*t stuff (commonly called IoT), needs to be on an untrusted LAN, far away from your trusted systems.  This is an FBI and NSA recommendation.
[https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/](https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/) is a reference for that claim.

---

### Post by DuckHook on 2022-04-18
> **TheFu said:**
> …not exactly a toy.  <rbg>
Was that you piloting the trike? I wouldn't put it past you…  :P
> 
```
internet-Router
|____LAN1 (10.40.1.x/24)
|    |____desktops (wired ethernet)
|    |____trusted_systems
|    |____internal_Servers
|____LAN2  (172.20.1.x/24)
|    |____external_Servers
|    |____nextcloud
|____LAN3 (192.168.60.x/24)
     |____gaming-systems
     |____chromecast
     |____roku
     |____IoT-junk
     |____wifi-n-untrusted-devices
```

Then setup the firewall rules on the router to only allow the exact connections required between each subnet.  Security begins with network security.  Assume someone hacks into the nextcloud server.  They shouldn't be able to get to any other LAN from there.
Thanks to you and kevdog, this is almost exactly how I have my VLANs segmented.

---

