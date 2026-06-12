---
title: "Help Securing a VM Server"
date: 2012-11-06
forum: Security
---

### Post by drmrgd on 2012-11-06
For a side project that I've been working on, I've setup an Ubuntu Server (10.04 LTS) in a Virtual Machine running on my standard Kubuntu install.  Since this is work related and I often need to check in on things from work, load new data into the server from work, and whatnot, I've opened up 80 and 22 on the my home router to outside traffic (80 since the regular user interface is web based, and 22 for obvious reasons), and am forwarding it to my VM.  Since I only have a consumer level router, I set up SSH on my main machine on a different port, and 80 is not open on that side.  

I am completely ignorant when it comes to networking in general, let alone network security, and although the VM actually comes from a company that "should" have somewhat hardened the server, I do want to make sure that's the case.  Since it's just a VM, I don't necessarily care if it gets hosed as I can just reload a new image.  It would be very suboptimal (to say the least) as I'm sure I'll end up losing some of my work.  But, some of my big concerns are attackers being able to get to my main box from there via ssh, problems with my ISP due to illicit traffic, and things like that.  The big problem is that I'm completely in over my head when it comes to the coding that I'm trying to do, and I've had to spend every free minute I can trying to figure out and learn the scripting necessary, and really don't have enough brain cells left to process this networking and network security language.

I've tried to read up some on the network security stuff out there, and to be honest, a lot of it is over my head.  I've been monitoring the log files, and I see tons of failed ssh attempts, with occassional big warning like (the source URL completely cracked me up!):

```
Nov  4 07:29:25 TSVMware sshd[24507]: reverse mapping checking getaddrinfo for webserver.1800hairextensions.com [206.217.199.18] failed - POSSIBLE BREAK-IN ATTEMPT!
```

Apart from only having needed ports open on the server VM, and only having 80 and 22 open on my router, plus a fairly strong password on all my systems, what can I do to make sure I at least make it somewhat challenging for an attacker to get in and do something bad?  I know that UFW is inactive on the system currently.  However, I'm not quite clear on what that would do that my router would not.  I've also had a look, and it seems that the vendor has not setup any iptables rules.  I had a look at the Community Docs ([https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)), and again, it's a little over my head at the moment.  It seems it would be better to configure this, I would imagine, but I'm really not too sure about how to go about this.

Another thing that I thought of is that maybe it's bad to use an ssh key rather than a password between my server VM and my host machine.  The two have different passwords, and I'm thinking that it may be more secure to have to use a password to get through to the host rather than being able to automatically connect if one can guess the user name.  Would that make sense?

I've also find this nice guide to some security tools and settings that one should consider.  However, I feel like I completely lack the time and the knowhow to learn all of this and appropriately set it up:

[http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics)

Can anyone offer some advice on the best way to make sure this VM server is somewhat safe, maybe an abject and total moron's (a few steps below idiot I would imagine) guide to Ubuntu Server Security?  Apart from actually changing the Ubuntu Server version, I think (or probably hope is more like it) that I should be able to do what needs to be done without affecting the rest of the setup.  I sincerely appreciate anyone who can point me in the right direction!

---

### Post by papibe on 2012-11-06
Hi drmrgd.

A few thoughts:

If you really want to secure your VM, don't make it directly available from the Internet. That would be:
[LIST]
[*]Don't bridge the interface, but use the regular NAT to hid it behind your host machine.
[*]Secure your host machine instead. Use keys with a long passphrase, iptables, etc.
[*]Map a port from your host machine to your ssh port on your VM so you can connect locally to it.
[*]In order to connect from the internet, you would have to connect to the host first, and then jump to the VM.
[/LIST]
Just my thoughts. Let us know how it goes.
Regards.

---

### Post by drmrgd on 2012-11-06
Thanks for the suggestions, although you kind of went the complete opposite way of what I was thinking.  Currently, I do have ssh open on my host, which I could technically close if need be.  I opened a semi-obscure port to ssh there so that I can spin up the VM if need be.  The VM is the one exposed, and since it's an image that I can backup and easily recover it I absolutely had to, I sort of think that would be a better front line than the host machine.  

Still, though, if I'm going to secure one Ubuntu system or the other, I would imagine the process being very similar with the exception that the server is running Apache2, Tomcat, Postgres and things like that.  So, I guess there's more to think about?  Aside from that, though, I've taken a couple minutes to have a look at iptables docs, and I'm thoroughly lost.  

I also see some stuff on denyhosts, which looks promising and fairly easy to run.  Would this be beneficial at any level?

---

### Post by drmrgd on 2012-11-07
So, after seeing a crazy (to me anyway) amount of activity in my auth logs for all kinds of stuff over ssh, I installed denyhosts and set it up.  It was a million times easier than I thought it was going to be (I think setting up rsnapshot was actually harder!).  Assuming I've set that up correctly, I guess this is a pretty solid layer of defense here as I guess an attacker would either have to figure out how to dupe the system or guess correctly in a really limited window of tries (I think I actually set it to like 3 tries for everything since I'm just about the only person that will access this server).  With a solid enough password, I would imagine this is near impossible.

Looking at the error.log in Apache2, I see lots and lots of entries.  Almost all are from "Tastypie" which looks to be some kind of DJango API, that may be semi-misconfigured by the developers of the system.  I think I did find a couple entries that seemed suspicious, but can't really make heads or tails of them, other than it looks like someone is trying to access some proxy php script that doesn't seem to exist where they're looking:

```
[Wed Nov 07 04:35:42 2012] [error] [client 58.218.199.250] script '/var/www/proxyheader.php' not found or unable to stat
[Wed Nov 07 10:58:41 2012] [error] [client 58.218.199.250] File does not exist: /var/www/proxy
[Wed Nov 07 12:52:08 2012] [error] [client 58.218.199.227] script '/var/www/proxy.php' not found or unable to stat

```

So, I guess the next question in my adventure here is, what do I need to do to secure the Apache2 server from attacks.  I noticed that Fail2Bam specifically suggests it's useful to securing Apache servers in a similar way to denyhosts.  I don't seem to see this kind of support with denyhosts.  Should I have installed Fail2Ban instead, or is this something that one would run concurrently?

---

