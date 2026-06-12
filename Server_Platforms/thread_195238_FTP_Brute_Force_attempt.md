---
title: "FTP Brute Force attempt"
date: 2006-06-12
forum: Server Platforms
---

### Post by Randomskk on 2006-06-12
Hey
I was checking my auth.log (you know, as you do) and I found it spammed absolutely **full** of these two strings:
Jun 11 15:12:32 randomskk ftpd: (pam_unix) check pass; user unknown
Jun 11 15:12:32 randomskk ftpd: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=211.100.27.101

My FTP logs are full of this:
Sun Jun 11 16:56:08 2006 [pid 24090] [Administrator] FAIL LOGIN: Client "211.100.27.101"

From this it looks like someone is trying to log in as Administrator and guessing passwords. That's an invalid username, so they'd never succeed - plus it seems they think it's a windows system (which makes sense, long story) while it's not.

Looking into the IP reported, it belongs to the website 100tv.com, and they seem to run Apache 2.2.0, and OpenSSH 3.6.1. This is a fairly old OpenSSH, and the site itself doesn't seem too bad, so my guess is that someone else has hacked their site before running the FTP brute force.

As I don't speak chinese, I don't think emailing the site would do much, and besides it doesn't seem to be them.

I'd like to follow this up, seeing as being brute forced is always somewhat annoying - not to mention spams up the logs - but I realise that doing so may not be easy.

At this point, where should I start, or should I just drop it?

nb: for some reason, snort didn't see this on the server or on my firewall, so I'm guessing it can't see brute forces?


Thanks

---

### Post by Randomskk on 2006-06-13
Ok, update:
Today I was being hit again, again with someone trying the "Administrator" account.
This time it's a new IP, 61.152.96.230, which belongs to ANOTHER chinese website.
This host has a tcpwrapped server on port 22, plus SSH 1.2.27 on port 512, and Apache 2.0.53 with PHP 5.0.4 (same Apache type as well - ((Unix))), plus a telnet and CUPS server.

There seems to be some sort of sendmail running on port 465, too.

As far as I can see, then, there are two similarities: both have an old SSH daemon, and both have Apache ((Unix)) with PHP installed, in both cases an old PHP.

If this was the same person, would it appear they are specifically targetting me, or just randomly selected a host running windows FTP?
Or it could be that the IP in the logs is the person actually attacking me.

Same questions as above, what should I do if I want to follow this up?

---

### Post by Randomskk on 2006-06-13
Ok, update again:
ANOTHER IP is at it, again chinese but now without Apache.
This host also has OpenSSH 3.6.1, the exact same version as the first host and possibly the same as the tcpwrapped second host.

I imagine whoever is doing this has a 3.6.1 ssh vuln, but it's getting annoying.
I'm adding the IPs to hosts.deny and I've removed the line allowing any user FTP access in hosts.allow, to no luck. It's still continuing now :/

---

### Post by zuus on 2006-06-15
Heh, interesting. I occasionally get the odd hack attempt wherein they try creating a whole bunch of random directories for some reason, but very rarely. 

If you keep trying to get brute forced like this, maybe try to setup your FTP server to only listen for a few trusted IP's or turn it off for a while, IF that's possible.

---

### Post by H.E. Pennypacker on 2006-06-16
> plus it seems they think it's a windows system (which makes sense, long story) while it's not.

Please share that story.  They think it's Windows?  Well, didn't you just say that you are running Windows:

> or just randomly selected **a host running windows FTP?**

In any case, please do share the story.

---

### Post by Randomskk on 2006-06-16
Well, I like being paranoid with my server, which means I do as much as I can to disguise, deceive and secure it.
As an example, my VSFTPD banner line says this:
Microsoft FTP Service

Which, funnily enough, exactly matches a version id line in nmap 4+ that identifies the FTPd as Microsoft. Thus, any nmap scan shows it to be microsoft, plus plenty of other scans that use a similar method to detect version.
I've done the same thing to my postfix and Apache servers, and am doing it to BIND (although this is hard, because it needs non-printable chars).

As a result, it would appear that the FTP is running windows, and the person brute forcing it is pretty much destined to fail, since Administrator is not a valid username :)

---

### Post by cidica on 2006-06-21
[QUOTE=Randomskk]Well, I like being paranoid with my server, which means I do as much as I can to disguise, deceive and secure it.
As an example, my VSFTPD banner line says this:
Microsoft FTP Service

Which, funnily enough, exactly matches a version id line in nmap 4+ that identifies the FTPd as Microsoft. Thus, any nmap scan shows it to be microsoft, plus plenty of other scans that use a similar method to detect version.
I've done the same thing to my postfix and Apache servers, and am doing it to BIND (although this is hard, because it needs non-printable chars).

As a result, it would appear that the FTP is running windows, and the person brute forcing it is pretty much destined to fail, since Administrator is not a valid username :)[/QUOTE]


Hehe, man I feel your pain. There for a while I was getting brute forced by a Haliburton IP. It was insane. I'm sure good ol Chaney wasnt doing it. Just a system that was comprimised. But I started getting hits from different Haliburton IPs all across the board. Did you know these guys have a **CLASS A** address?? I about fainted. Why do they need 126 networks with 16,777,214 host PER network!? Well its just something that has always stuck out to me. I just thought I would share it. 8)

---

### Post by MJN on 2006-06-22
A Class A is ***one*** network of 16,777,214 hosts... :)

Mathew

---

### Post by Ride Jib on 2006-06-22
[QUOTE=Randomskk]Ok, update again:
ANOTHER IP is at it, again chinese but now without Apache.
This host also has OpenSSH 3.6.1, the exact same version as the first host and possibly the same as the tcpwrapped second host.

I imagine whoever is doing this has a 3.6.1 ssh vuln, but it's getting annoying.
I'm adding the IPs to hosts.deny and I've removed the line allowing any user FTP access in hosts.allow, to no luck. It's still continuing now :/[/QUOTE]

Honestly, I wouldn't be concerned about it. I see this stuff everyday. Snort should be picking it up unless you don't have proper signatures to do so. Just drop the traffic at the perimeter and move on. Or if you only let a few people access, then just deny all  and permit a few select hosts (which is how it should be done).

---

### Post by DirtDart on 2006-06-29
[QUOTE=Randomskk]I'm adding the IPs to hosts.deny and I've removed the line allowing any user FTP access in hosts.allow, to no luck. It's still continuing now :/[/QUOTE]

Not sure how widely used your ftp server is, but you can always add just the IP address ranges to the hosts.allow, then deny everything else.

> This host also has OpenSSH 3.6.1, the exact same version as the first host and possibly the same as the tcpwrapped second host.

It's been my experience that most attacks like that come from compromised systems.

---

### Post by Randomskk on 2006-06-29
For some reasons, using the hosts. wrappers doesn't seem to work on vsftpd :/

Still, the attacks seem to have stopped, and it's not like they were ever gonna work.

---

### Post by Fireal on 2008-01-23
You could look into [fail2ban]("http://www.fail2ban.org/wiki/index.php/Main_Page").  You can set it to deny ip addresses that unsuccessfully log in a set number of times for a set period of time, or indefinitely (I think).  It works with several other services also (i.e. ssh); works great for my proftpd.

---

