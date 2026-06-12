---
title: "DNS Spoofing"
date: 2010-05-19
forum: Security
---

### Post by Built_Well on 2010-05-19
Hi, I was a victim of DNS Spoofing over a year ago in late October, early November, 2008.  

This is what happened.  I have a remote UNIX FreeBSD shell account that I log into remotely from home using ssh.  My home computer uses Ubuntu Linux on the desktop.  At the time of the DNS spoofing, I think I was not running a firewall.  I now run a firewall all the time.  I don't think I had any servers running.  

I always used to log into my remote shell account by using its domain name,  like this: ssh [email]me@HappyDomain.com[/email] . Now I only log in using the IP address like this ssh  me@123.45.678.90.

I know the DNS spoofer/hacker compromised my remote FreeBSD account.  He  learned my password and changed it so I couldn't log in for 3 days.  I'm wondering if the DNS Spoofer also was able to compromise my  non-firewall home computer's Linux system?  For example, how was he able to learn the password of my remote FreeBSD account?  Was it a matter of him first hacking into my home computer and depositing some software there, and that software detected my remote password when I typed it in at my  keyboard?  Or was it a matter of the DNS Spoofer opening his own shell account at my remote FreeBSD server, and somehow listening in from there  whenever I tried logging into my remote shell account?  

I guess I'm wondering if my home Linux desktop was compromised too, in  addition to my remote UNIX shell account.  

I haven't used that home computer since then (over a year), but I would like to put that home machine back in service again if it's safe.  Thanks very much.

---

### Post by teh_drizzle on 2010-05-19
If you were a victim of DNS spoofing then it's more likely that the attacker compromised either your home router or workstation (to edit the DNS server/entries). Unless you manage the DNS entry for HappyDomain.com yourself and they compromised your (web) account for whatever service you use. (GoDaddy, a dDNS service, cPanel).  

This is why it's important to read the "WARNING - POTENTIAL SECURITY BREACH" or associated key-mismatch error when using ssh. :P (Might have saved your account on the remote HappyDomain.com host.)

I'm not an expert in the least but I'd say 60% chance your workstation was compromised originally.

---

### Post by Built_Well on 2010-05-19
> **teh_drizzle said:**
> If you were a victim of DNS spoofing then it's more likely that the attacker compromised either your home router or workstation (to edit the DNS server/entries).

Thanks.  I don't have a router, and just use one computer at a time at home--there's no  home network.  I would like to put that computer back in service without re-formatting the hard drive, but you seem to be suggesting that the hacker gained root access to my Ubuntu desktop, and changed the DNS server entries.

How might he have gained root access?  It is possible that I was surfing the web as root back then--not sure.

Would re-formatting the hard drive partitions, and re-installing Ubuntu make the system safe to use again?

---

### Post by cdenley on 2010-05-19
How did you determine you were a victim of DNS spoofing? Was it the nameserver for your domain that was attacked, the DNS server you were using to lookup domains, or a system on your LAN? Had you connected to that SSH server before? If so, your ssh client should have recognized that you're not connecting to the same server. If your domain was resolved to a server controlled by the attacker, and you provided your password to the attacker's SSH server, then that is how they retrieved your password. What else was that password used for?

I don't think a firewall would do anything to protect you from DNS spoofing.

---

### Post by Built_Well on 2010-05-19
> **cdenley said:**
> How did you determine you were a victim of DNS spoofing? 

I think it was a DNS Spoofing attack because I would receive the following error when using ssh: 

WARNING: POSSIBLE DNS SPOOFING DETECTED!
The DSA host key for HappyDomain.com has changed, and the key for the according IP address 123.45.678.90 is unknown.

So I guess I should reformat the partitions and reinstall Ubuntu?  Should that cure my other computer?  I haven't used it in over a year.  (It would be nice if I didn't have to reformat and reinstall, though..)  Thanks.

---

### Post by cdenley on 2010-05-19
> **Built_Well said:**
> 
WARNING: POSSIBLE DNS SPOOFING DETECTED!
The DSA host key for HappyDomain.com has changed, and the key for the according IP address 123.45.678.90 is unknown.


Was "123.45.678.90" the correct or incorrect IP address? Did you enter your password after receiving that message? How did you determine your password on the correct server was changed? Do you maintain the FreeBSD server, or is it possible the key was changed as the result of some maintenance?

---

### Post by doas777 on 2010-05-19
I think you may be experiencing a false positive. are you absolutely certian that no one on the server end regenerated keys, or rebuilt the server?
there was a big crypto bug last year (or was it '08?) in the openssh packages, that forced most admins to regen all their keys. if the server in question was administered this way, then you would recieve the message you mention. 

if you have ssh credentials, then you must know someone on site, right? perhaps have them confirm the server IP and ask if any maintenance has been preformed on ssh services.

---

### Post by doas777 on 2010-05-19
> **Built_Well said:**
> 
So I guess I should reformat the partitions and reinstall Ubuntu?  Should that cure my other computer?  I haven't used it in over a year.  (It would be nice if I didn't have to reformat and reinstall, though..)  Thanks.

NO! the problem is not on your PC per se. if the problem si that your PC is remembering an old key, then the fix is very simple.

ok, heres how it works:

1) you login to a server for the very first time via ssh
2) the server sends you a crypto key, that will identify the server in all future communications. this key is stored in ~/.ssh/known_hosts
3) next time you connect, the server sends it's key again. 

4)your pc compares the key to the one in known_hosts. if the key is the same, then you can be sure that the server you are connected to is the exact same one you were connected to last time. if they don't match, then there is a possiblilty that you are connecting to the wrong server (it has the right name, but the wrong key). this can be accomplished by "DNS Spoofing", hence your message. 

don't focus on the DNS spoofing; you are not likely encountering it. your problem is with ssh keys so focus on that for now. 

all that said, you can always "forget" an old/bad key, by deleting known_hosts. it will regenerate next time you create a connection.

---

### Post by cdenley on 2010-05-19
> **doas777 said:**
> 
there was a big crypto bug last year (or was it '08?) in the openssh packages, that forced most admins to regen all their keys. if the server in question was administered this way, then you would recieve the message you mention.

I thought that was specific to debian-based linux distros and wouldn't have affected FreeBSD servers.

---

### Post by doas777 on 2010-05-19
> **cdenley said:**
> I thought that was specific to debian-based linux distros and wouldn't have affected FreeBSD servers.

that sounds right, but the bug itself was in the openssh package (which I would assume is much the same on bsd as on linux of any flavor). 

it's just supposition, as you know. either he has a bad key memorised, or the server is in fact rogue. either way it doesn't really matter how the key was changed, just that it was.

---

### Post by cdenley on 2010-05-19
> **doas777 said:**
> it's just supposition, as you know. either he has a bad key memorised, or the server is in fact rogue. either way it doesn't really matter how the key was changed, just that it was.

Or possibly the domain was in fact spoofed. We would be able to tell if he posted the actual IP and domain. If it was spoofed, then that "POSSIBLE DNS SPOOFING DETECTED" would have given an IP address which that domain should not have resolved to. If the IP was correct, then it wasn't DNS spoofing, and was probably just a new key.

My guess is the FreeBSD server died, so they replaced it with a new server which had a new key, then it took a few days to restore everything, such as user accounts and passwords. Of course, we don't have much details to work with to determine exactly what happened.

---

### Post by doas777 on 2010-05-19
> **cdenley said:**
> Or possibly the domain was in fact spoofed. We would be able to tell if he posted the actual IP and domain. If it was spoofed, then that "POSSIBLE DNS SPOOFING DETECTED" would have given an IP address which that domain should not have resolved to. If the IP was correct, then it wasn't DNS spoofing, and was probably just a new key.

My guess is the FreeBSD server died, so they replaced it with a new server which had a new key, then it took a few days to restore everything, such as user accounts and passwords. Of course, we don't have much details to work with to determine exactly what happened.

thats what i meant by rogue. 
my suspicion is the same as yours, so we shall see what info the op can provide us.

---

### Post by Built_Well on 2010-05-19
> **doas777 said:**
> I think you may be experiencing a false positive. are you absolutely certian that no one on the server end regenerated keys, or rebuilt the server?

Thanks, but I was definitely hacked.  I couldn't log into my remote FreeBSD account for 3 days, beginning on a Friday.  I finally called the web host on the following Monday.  They changed my password for me on the phone because the hacker had changed it to his own password.

Also the unscrupulous hacker stole some intellectual property of mine while he was logged into my FreeBSD account.  Luckily, I was able to get the property back a couple days later by contacting the right companies.  It was not a pleasant experience being hacked.

Should I reformat the other computer's partitions and reinstall Ubuntu?  Will that make that computer reasonably safe again?  I no longer have that machine plugged into the net.  Haven't used it in over a year.  

I'd like to transfer some files from that computer to my other one, but I don't want to take the chance of any infection spreading--maybe the hacker deposited something on the other machine's hard disk?

---

### Post by cdenley on 2010-05-19
You still haven't answered a few key questions.

When you had the "POSSIBLE DNS SPOOFING DETECTED" message, what was the actual IP address it gave? Was it the IP that HappyDomain.com was supposed to resolve to? After receiving that message, did you enter your password? If so, was that password used for anything else?

Of course if you ever suspect a system may have been compromised, reformatting and using different passwords is always a safe bet, but you haven't told us anything yet that makes me think your personal computer was compromised. Were you running any servers on it?

---

### Post by Built_Well on 2010-05-19
> **cdenley said:**
>  Were you running any servers on it?

 I mentioned in the original post that I don't think I was running any servers on the Linux desktop home machine.   

I don't think I should reveal the actual IP address and the domain name.  I hope you understand. 

The hacker needed access to my email account on the remote FreeBSD server to steal the property.  He targeted me.  He knew from public records what I owned and the email address he needed to steal, so this piece of work targeted me specifically.  We think this hacker does not live in the western hemisphere, but I don't want to say exactly where.

---

### Post by bodhi.zazen on 2010-05-19
> **Built_Well said:**
> Thanks, but I was definitely hacked.


OUCH !!!

I would perform a fresh install. If you wish, make an image of the compromised server and perform forensics on the image at your leisure, but unless you were using some kind of a HIDS there is no way to know what could be on the compromised server.

Sounds as if you were the victim of what I call a "man in the middle" attack, may or may not have been DNS poisoning, hard to know for sure.

In the future, be very very cautions when you get those ssh alerts.

> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle  attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f2:92:1d:da:81:2a:d7:16:0a:48:f0:43:20:1c:f4:b5.
Please contact your system administrator.
Add correct host key in /home/bodhi/.ssh/known_hosts to get rid of this  message.
Offending key in /home/bodhi/.ssh/known_hosts:1

When you get that kind of a warning you need to stop and investigate. All too often people advise you simply delete your ~/.ssh/known_hosts file.

THIS IS VERY BAD ADVICE.

You would then ssh into the false server.

You need to contact the sys admin of the server and find out if the host keys have changed, verify the host name / ip address, etc, etc.

Assuming the host keys changed, only delete the bad key. In the message above it tells you it is the first key :

> Offending key in /home/bodhi/.ssh/known_hosts:**1**

If the sys admin changed keys, you would remove ONLY the first key.

You can do this with

```
ssh-keygen -R host_name
```

Or manually editing the file. The above command will make a back up , which is IMO very handy.

You can use sed if you like :

```
sed -i 1d .ssh/known_hosts
```

but again, I prefer ssh-keygen -R

---

### Post by cdenley on 2010-05-19
> **Built_Well said:**
> I mentioned in the original post that I don't think I was running any servers on the Linux desktop home machine.   

I don't think I should reveal the actual IP address and the domain name.  I hope you understand. 

The hacker needed access to my email account on the remote FreeBSD server to steal the property.  He targeted me.  He knew from public records what I owned and the email address he needed to steal, so this piece of work targeted me specifically.  We think this hacker does not live in the western hemisphere.

Was the IP address of the SSH server you connected to the incorrect one for your domain?!?! Did you provide your password to that server?!?!

---

