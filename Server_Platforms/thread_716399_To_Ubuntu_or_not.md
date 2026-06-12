---
title: "To Ubuntu or not?"
date: 2008-03-05
forum: Server Platforms
---

### Post by gfunkdave on 2008-03-05
Hi all-

I'm our company's unofficial IT guy (though it's really not my job - I just know more about computers than anyone else in the company).

We're thinking of getting a fileserver to replace our hosted Sharepoint service. I'd like to run Ubuntu on it, but I'm wondering what that would entail. I don't want to have to spend lots of time administering it. I'd say my level of Unix knowledge is somewhere between beginner and intermediate. 

This would be a server mainly used as a network resource to store files on. I'd also like it to be a domain controller, but could be talked out of that. 

Also, it would need to be publicly accessible since we'd need to let consultants and assorted outside people access it. Given my level of Unix knowledge, is it wise to have me administering such a server?

I'd go with Windows, but Windows Server is ridiculously expensive for our needs.

Thanks for any advice.

---

### Post by steveneddy on 2008-03-05
Ubuntu Server Edition should do the job.

As far as the details, I'll leave that to someone else.

Although, most of this info should be available on the web.

You may[ look here]("http://doc.gwos.org/doku.php/doc:admin").

---

### Post by Dr Small on 2008-03-05
I would say that you would have trouble at the command line, since you said you are a beginner or intermediate. Ubuntu can do it, but you would certainly need to understand the command line.

Alternately, you could install Xorg and your favorite lightweight window manager and control the whole system with SSH from another system, which would make it somewhat simpler and give you a GUI so you can "see", so to speak.

It is really up to you, if you are up for the challenge. I have my own file / ftp / http / mysql / ssh / stream server, and basically control it all from ssh in the command line, but do have Xorg with IceWM loaded on it.

It's really not that difficult if you know what you are doing, but if you don't know much it could be quite frustrating.

Dr Small

---

### Post by jcwmoore on 2008-03-05
> it would need to be publicly accessible since we'd need to let consultants and assorted outside people access it.

Your internal requirements are simple enough, SAMBA isn't that bad to figure out for document storage... but what about the people outside your company?  If they are using Windows, and they more than likely are, and need to see "windows only" data, I think you would have a horrible time setting that up.  if you just need to give these people access to some databases, or word files then you should be ok with a linux server, but if you have data like Reporting Services reports, or other data that uses MS software to generate (as I do where I work) then you probably need to pay the "business tax" to MS and us windows server.  Sorry but MS is way to entrenched in the business world, unless you are starting from scratch it is hard to get out of it...

---

### Post by gfunkdave on 2008-03-05
Thanks all...the server just needs to dish out files to people. It doesn't need to do Reporting Services or anything fancy like that.

I'm not quite sure how I'd get users outside our intranet to access things...I guess I'd run sftp or something, Or figure out some sort of web access.

I'm pretty comfortable with command line, though I prefer GUI. I have Ubuntu on another laptop, and I'm running Samba and GSAMBAD on it to play around. Should I do LDAP too?

My main concern is that I don't want to spend a week setting the thing up. I know I'd get a Windows Server machine up and running in no time. But I also feel Ubuntu would be more secure.

---

### Post by dmizer on 2008-03-06
> **gfunkdave said:**
> Also, it would need to be publicly accessible since we'd need to let consultants and assorted outside people access it. Given my level of Unix knowledge, is it wise to have me administering such a server?

this would be the clincher for me.  if critical files must be accessible across the internet, even as a moderately experienced linux network admin, i would defer to more experienced help.

in my opinion, everything else you want to do is peanuts compared to this.

---

### Post by gfunkdave on 2008-03-06
Well, let me ask this (and probably show just how naïve I am). My understanding is that, out of the box, Linux is just much more secure than Windows. Is that not the case? 

If I were to put the Linux box behind our firewall, and just open port 22 for SSH to it, wouldn't that be pretty secure?

Mods may want to think about moving this to the How To section now. :)



> **dmizer said:**
> this would be the clincher for me.  if critical files must be accessible across the internet, even as a moderately experienced linux network admin, i would defer to more experienced help.

in my opinion, everything else you want to do is peanuts compared to this.

---

### Post by dmizer on 2008-03-06
linux is much more secure out of the box.

but any time you poke holes in your firewall and expose your clients files to the raw internet (even with a properly configured sftp server) you've opened yourself to a logistical and security nightmare.  to be sure, it's less of a problem than windows, but it's enough of a problem that i wouldn't suggest risking it unless you REALLY knew what you were doing.

and yes ... _just_ opening port 22 to forward ssh would also place you at risk for hacking.  to protect yourself from attack over ssh, you would need to set up secure key authentication as well as move the access port to an obscure, high numbered ssh port just to avoid script kiddies.

if you want any machine to be exposed (with any port) to the internet, your directly exposing your server, it's content, and even other comptuers on the network ... to hackers, and the hacker crowd has all the necessary tools to take advantage of any unpatched hole, any improperly configured option, any forgotten account, any mistake you make.

setting up your own sftp server or webserver for personal use and experimentation is one thing.  but any time you want a production environment exposed to the internet, you want someone EXTREMELY knowledegable and vigilant at the helm.

i have been hacked.  and yes, it can happen to you.  and yes, it IS a very real danger.

---

### Post by gfunkdave on 2008-03-06
Duly noted. You've convinced me. If we do get a fileserver (now we're using hosted Sharepoint, whose lack of SSL also irks me), I'll keep it behind the router and outside users will need to set up a VPN tunnel.

:)

---

### Post by Dr Small on 2008-03-06
> **dmizer said:**
> linux is much more secure out of the box.

but any time you poke holes in your firewall and expose your clients files to the raw internet (even with a properly configured sftp server) you've opened yourself to a logistical and security nightmare.  to be sure, it's less of a problem than windows, but it's enough of a problem that i wouldn't suggest risking it unless you REALLY knew what you were doing.

and yes ... _just_ opening port 22 to forward ssh would also place you at risk for hacking.  to protect yourself from attack over ssh, you would need to set up secure key authentication as well as move the access port to an obscure, high numbered ssh port just to avoid script kiddies.

if you want any machine to be exposed (with any port) to the internet, your directly exposing your server, it's content, and even other comptuers on the network ... to hackers, and the hacker crowd has all the necessary tools to take advantage of any unpatched hole, any improperly configured option, any forgotten account, any mistake you make.

setting up your own sftp server or webserver for personal use and experimentation is one thing.  but any time you want a production environment exposed to the internet, you want someone EXTREMELY knowledegable and vigilant at the helm.

i have been hacked.  and yes, it can happen to you.  and yes, it IS a very real danger.
I beg your pardon, but by opening up port 22 for SSH is no more insecure than the man in the moon. While you are allowing script kiddies and crackers to access port 22, that does not mean that there are holes in the SSH daemon that would allow them to crack your server.

All they can possibly do, (and I have seen them do it on my server) is try dictionary attacks on logins. If you have an obscure username and random / tight password, then you are very secure. The least they can do is flood your server with random dictionary attacks.

But there is generally nothing insecure with the services you run, and that's why they are opened to net by most people. If you would be running some other web daemon that wasn't secure or popular, then that would be a security risk, if it had exploits in the software.

Dr Small

---

### Post by Oldsoldier2003 on 2008-03-06
> **Dr Small said:**
> I beg your pardon, but by opening up port 22 for SSH is no more insecure than the man in the moon. While you are allowing script kiddies and crackers to access port 22, that does not mean that there are holes in the SSH daemon that would allow them to crack your server.

All they can possibly do, (and I have seen them do it on my server) is try dictionary attacks on logins. If you have an obscure username and random / tight password, then you are very secure. The least they can do is flood your server with random dictionary attacks.

But there is generally nothing insecure with the services you run, and that's why they are opened to net by most people. If you would be running some other web daemon that wasn't secure or popular, then that would be a security risk, if it had exploits in the software.

Dr Small
Don't forget deny hosts :)  deny hosts and properly configuring your firewall makes the chance of a successful brute force attack on ssh a lot less likely.

---

### Post by moonpup on 2008-03-06
I second the motion for the DenyHosts script. I use it on my internet facing shell server and it's great. Granted I don't use port 22 for ssh as I select a much higer arbitrary port. Even with that, I still see hosts getting periodically denied trying to run dictionary attacks. A simple nmap -sV -p 1-65535 on a host will find your ssh port amongst other things :)

Install DenyHosts, setup ssh pubkey authentication and you'll be good to go. Also, as you noted a VPN would be the right way to do this for your external clients. Good luck!

---

### Post by Oldsoldier2003 on 2008-03-06
> **moonpup said:**
> I second the motion for the DenyHosts script. I use it on my internet facing shell server and it's great. Granted I don't use port 22 for ssh as I select a much higer arbitrary port. Even with that, I still see hosts getting periodically denied trying to run dictionary attacks. A simple nmap -sV -p 1-65535 on a host will find your ssh port among other things :)

Install DenyHosts, setup ssh pubkey authentication and you'll be good to go. Also, as you noted a VPN would be the right way to do this for your external clients. Good luck!
yep security by obscurity only stops the real lazy script kiddies.

---

### Post by dmizer on 2008-03-06
> **Dr Small said:**
> I beg your pardon, but by opening up port 22 for SSH is no more insecure than the man in the moon. While you are allowing script kiddies and crackers to access port 22, that does not mean that there are holes in the SSH daemon that would allow them to crack your server.

All they can possibly do, (and I have seen them do it on my server) is try dictionary attacks on logins. If you have an obscure username and random / tight password, then you are very secure. The least they can do is flood your server with random dictionary attacks.

But there is generally nothing insecure with the services you run, and that's why they are opened to net by most people. If you would be running some other web daemon that wasn't secure or popular, then that would be a security risk, if it had exploits in the software.

Dr Small
gfunkdave asked if there would be an issue with safety if port 22 is forwarded to the server.  gfunkdave made no indication of further hardening the server (secure/random password, obscure username, deny hosts, or public key auth was not mentioned).  simply forwarding port 22 to an unhardened server is inviting attack.  further action MUST be taken in order to protect the server from attack.  ESPECIALLY one that is providing a sensitive service like internal company file sharing.

my thinking was not that it is unsafe to forward ssh to a server.  i simply felt that it was a good illustration for why i thought more experience was necessary in order to expose a server to the internet.  because all of you who have posted have suggested things for hardening out-of-the-box ssh.  ssh is not secure out-of-the-box, you need experience to realize that further action must be taken to secure out-of-the-box ssh server.  and i also believe that you're kidding yourself if you think that a random password and obscure username are enough to prevent unauthorized access via ssh.

i was answering to a small point that gfunkdave made in the OP about not wanting to take a lot of time administering and setting up the server.  even if you know a lot about administering a server, forwarding ports to a server from the web requires experience and vigilance (ssh or otherwise).

---

### Post by Dr Small on 2008-03-06
I was certainly not kidding. SSH out of the box is secure (with it's default settings) and adding a tough username and password makes it impossible to crack.

Do you think that SSH has holes in it? If it does, then the rest of it's security has holes too.. I ran SSH on my old system with my weak username & password, on the default port with no extra security (such as denyhost, Key based Auth and such) and most likely had lots of attacks, and my system was never cracked.

The point is, and I'm not trying to tear you down for recommending more security (because it is vital and important), that SSH is secure out of the box with default settings. If your username was "admin" and had a password as "password", a simple dictionary attack would leave your system wide open.

Is this a flaw with SSH? No, by golly. It's a security breach with the user.
If you run SSH on the default settings (out of the box) and have a strong obscure username & password, then you are basically safe. Have you tried hacking a SSH box lately?

Dr Small

---

### Post by dmizer on 2008-03-06
i didn't say that ssh was flawed.  but when any port is forwarded, security implementation is only as good as the administrator behind it and that was the point i was addressing more than a discussion on the security or insecurity of ssh specifically.

trusting the security of a server to a username and password alone is a risk.  and in my opinion, it is a risk that should not be taken when you are entrusted with the protection of someone else's critical data.  real security comes from hardening beyond username and password alone, and that's the difficult part when a port is forwarded.

---

### Post by Dr Small on 2008-03-06
Yeah, I realize that by doing that, everything hangs on the username & password, but all I was saying, was that SSH is secure by default.

But I am a security analist, and that is certainly not how I run my boxes, nowadays.
Simply enabling Keybased Auth and turning off Password Auth makes it secure, and then changing ports and other stuff makes for a secure box. :D

Dr Small

---

### Post by dmizer on 2008-03-06
> **Dr Small said:**
> Simply enabling Keybased Auth and turning off Password Auth makes it secure, and then changing ports and other stuff makes for a secure box. :D

Dr Small

yes, but then the problem is getting the customer and other outside users configured with a secure key.  which also means that the OP will need to take time to configure each existing client, each new client for their keypair, as well as upload the public key to the server.

again, from what i read in the original post, gfunkdave was looking for a no frills, low maintenance solution.  once you step beyond the confines of a firewalled intranet, server security is no longer "low maintenance".

---

### Post by moonpup on 2008-03-07
I agree, once you open up your network to the outside you better know what you are doing and do it correctly. If you feel you are not comfortable setting something up like this, then I recommend you find someone who can.

It is not worth it to play around with a production environment and risk getting cracked due to a misconfiguration or a misunderstanding of what you are trying to accomplish.

Implement a VPN solution and do it correctly the first time around :) If you want to try different things or learn how to do something then play around in a lab environment.

---

### Post by moonpup on 2008-03-07
> **Dr Small said:**
> I was certainly not kidding. SSH out of the box is secure (with it's default settings) and adding a tough username and password makes it impossible to crack.


Are you sure about that?? Have you ever installed Red Hat Enterprise linux?? SSH root logins are still permitted by default! Still wondering when they are going to address that one...

---

### Post by Dr Small on 2008-03-07
> **moonpup said:**
> Are you sure about that?? Have you ever installed Red Hat Enterprise linux?? SSH root logins are still permitted by default! Still wondering when they are going to address that one...
RootLogins are default for all openssh-server installs, but on Ubuntu, the Root user is disabled because of sudo. Of course, I always disable it also.

---

### Post by moonpup on 2008-03-07
> **Dr Small said:**
> RootLogins are default for all openssh-server installs, but on Ubuntu, the Root user is disabled because of sudo. Of course, I always disable it also.

Good point on the Ubuntu install, but this leads me back to your original statement about ssh being secure by default.

With root logins permitted by default, I would have to disagree. This is bad security practice and should be disabled by default. Any security person knows about the least privileges rule and this should apply to something like ssh.

Cheers! :p

---

### Post by dmizer on 2008-03-07
> **moonpup said:**
> Good point on the Ubuntu install, but this leads me back to your original statement about ssh being secure by default.

With root logins permitted by default, I would have to disagree. This is bad security practice and should be disabled by default. Any security person knows about the least privileges rule and this should apply to something like ssh.

Cheers! :p

actually, you're still right:
```
$ uname -r&&cat /etc/ssh/sshd_config | grep Root
2.6.22-14-generic
PermitRootLogin yes
```
which means that this is possible with an out-of-the-box ubuntu and ssh install:
```
$ ssh me@192.168.0.5
Last login: Fri Mar  7 22:55:29 2008 from 192.168.0.2
me@ubuntu:~$ sudo su
[sudo] password for me:
root@ubuntu:/home/me# 
```

---

### Post by Dr Small on 2008-03-07
I didin't think that was what a RootLogin was.
I thought it was more or less:

```
sudo ssh host
```
Because I see alot of attempts for "root" in the logs and my root login is disabled on mycroft, yet I can still use:
```
sudo su
```

To obtain root, if I want it.

Dr Small

---

### Post by lespaul_rentals on 2008-03-07
> **Dr Small said:**
> I didin't think that was what a RootLogin was.
I thought it was more or less:

```
sudo ssh host
```
Because I see alot of attempts for "root" in the logs and my root login is disabled on mycroft, yet I can still use:
```
sudo su
```

To obtain root, if I want it.

Dr Small

Well yes, you can do that if you want to obtain root privileges, but that is different than logging in as root.  Logging in a root means you use "root" as the username.  What you're doing there is just escalating yourself to admin rights.

If you want to prevent that, you should remove the SSH account from the admin group.  Then anyone who logs in won't be able to use sudo.  They may be able to bruteforce the SSH account, but once in, there's nothing they can really do.

[QUOTE=moonpup]Good point on the Ubuntu install, but this leads me back to your original statement about ssh being secure by default.

With root logins permitted by default, I would have to disagree. This is bad security practice and should be disabled by default. Any security person knows about the least privileges rule and this should apply to something like ssh.[/QUOTE]

Well, to be fair, they might enable root login by default on Red Hat Enterprise Linux because some network administrators might perform headless installs.  Stick the CD in, SSH into the box as root, and then do their work from there.  When finished, they can then disable root login or take preventative measures to keep people from bruteforcing the root account.

Plus, I think Red Hat assumes that those who will be using their servers know what they are doing.  Hopefully, the network administrators that use Red Hat know about such configuration issues, and are smart enough to not plug in the Ethernet cable as soon as the server powers up.  Red Hat isn't intended for the wannabe hax0r that thinks he's 1337 for using Linux.  It's for the people who know what they're doing.  That includes proper security measures.

Although, I will admit, Red Hat sure has a lot of other interesting default configurations...

---

### Post by gfunkdave on 2008-03-07
Interesting discussion going on here.

I am comfortable implementing public key authentication and a random port for SSH. Our number of outside users is small enough (and changes infrequently enough) that it shouldn't be a big deal. I can also plug the server into our router's DMZ port. I can also install DenyHosts. Good idea - I didn't know about it.

I suppose that having a publicly accessible server on the intranet proper is probably a bad idea. Still, I really want to implement a Windows domain for our users, and don't have the budget to buy two servers - especially not a Windows one. Right now, we have <10 users but that's projected to go up to ~100-150 in the next couple years. I'd like to make sure my solution scales.

Thanks for the ideas, all...

---

