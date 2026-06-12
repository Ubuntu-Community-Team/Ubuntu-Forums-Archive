---
title: "My Ubuntu server got hacked!"
date: 2008-09-16
forum: Security
---

### Post by gnucracker on 2008-09-16
I noticed today that my Ubuntu server got hacked. The server is located at university campus and some 200 people have access to it (via ssh). Server was running Ubuntu Hardy Heron (server edition) with all security patches applied (including latest kernel). I need your help because i have no idea how they compromised my box. I was browsing my file system (for fun) and i noticed a suspicious file (Z.tar.gz) lying in /var/tmp folder. I immediately listed the contents of Z.tar.gz and then extracted it to my home folder. There were many folders inside. In one of those folders was a modified OpenSSH server that logged passwords to /dev/.tmp so i listed the contents of /dev/.tmp and there were a lot of encrypted stuff inside (usernames,passwords and hosts i guess). Another folder in Z.tar.gz contained a source tree for private version of boxer /dev/mem rookit. I ran Rkhunter and it detected nothing suspicious (not a big surprise). I can't understand how the attacker elevated their privileges to root level. They must have used a private local root exploit because i'm the only user with admin rights and my password is VERY complex and i don't use that password anywhere else. I haven't found anything suspicious
from log files and shell histories.

---

### Post by cdenley on 2008-09-16
> **gnucracker said:**
> I noticed today that my Ubuntu server got hacked. The server is located at university campus and some 200 people have access to it (via ssh). Server was running Ubuntu Hardy Heron (server edition) with all security patches applied (including latest kernel). I need your help because i have no idea how they compromised my box. I was browsing my file system (for fun) and i noticed a suspicious file (Z.tar.gz) lying in /var/tmp folder. I immediately listed the contents of Z.tar.gz and then extracted it to my home folder. There were many folders inside. In one of those folders was a modified OpenSSH server that logged passwords to /dev/.tmp so i listed the contents of /dev/.tmp and there were a lot of encrypted stuff inside (usernames,passwords and hosts i guess). Another folder in Z.tar.gz contained a source tree for private version of boxer /dev/mem rookit. I ran Rkhunter and it detected nothing suspicious (not a big surprise). I can't understand how the attacker elevated their privileges to root level. They must have used a private local root exploit because i'm the only user with admin rights and my password is VERY complex and i don't use that password anywhere else. I haven't found anything suspicious
from log files and shell histories.

Was the modified sshd installed?
```

md5sum /usr/sbin/sshd

```
Did you enable the root account?
```

sudo getent shadow root|grep !

```
Are you running any other servers?
```

sudo netstat -tulnp

```
Have you had dictionary attacks on your ssh server lately?
```

grep "authentication failure" /var/log/auth.log|less

```
Have you been using fail2ban or denyhosts?

Giving users you can't trust shell access (even with limited privileges) is a little dangerous. I would use a more restrictive shell and/or chroot them.

---

### Post by gnucracker on 2008-09-16
Was the modified sshd installed?

1. Yes. (and modified ssh client was installed too) I already said that passwords were logged to /dev/.tmp :)

Did you enable the root account?
2.Root account was disabled. I was using sudo.

Are you running any other servers?
3.Only OpenSSH and Apache2 were running.

Have you had dictionary attacks on your ssh server lately?
4.Not lately.

fail2ban was running and configured properly.

---

### Post by cdenley on 2008-09-16
> **gnucracker said:**
> Was the modified sshd installed?

1. Yes. (and modified ssh client was installed too) I already said that passwords were logged to /dev/.tmp :)

Did you enable the root account?
2.Root account was disabled. I was using sudo.

Are you running any other servers?
3.Only OpenSSH and Apache2 were running.

Have you had dictionary attacks on your ssh server lately?
4.Not lately.

fail2ban was running and configured properly.

Then I agree that they must have had local access through one of your 200 ssh accounts, then used a local exploit to escalate privileges. Local vulnerabilities are much more common than remote vulnerabilities. Either that, or they had physical access.

It's hard to believe that they would be able to find a local vulnerability before a security update has been released for it, but wouldn't be smart enough to delete their hack tools to cover their tracks.

Obviously, I would setup your server again from scratch (if you haven't already) since you don't know what else they did.

> 
I already said that passwords were logged to /dev/.tmp

You said there was "encrypted stuff". You did not say where it came from, but apparently assumed it was from sshd. I guess they couldn't have created that file without root, so they probably could have and probably did install it.

---

### Post by eldragon on 2008-09-16
do you know how the approximate time of hacking? it appears it was done by one of the 200 account owners. otherwise fail2ban would have caught them. (remember there is a bug on the repo's fail2ban binary which will fail to start during boot if you dont create /var/run/fail2ban folder manually).

one long shot is to scan the 200's users bash history files to find suspicious commands. if the attacker didnt cover his tracks well, he would have left that too.

---

### Post by gnucracker on 2008-09-16
> **eldragon said:**
> do you know how the approximate time of hacking? it appears it was done by one of the 200 account owners. otherwise fail2ban would have caught them. (remember there is a bug on the repo's fail2ban binary which will fail to start during boot if you dont create /var/run/fail2ban folder manually).

Intrusion happened two weeks ago according to timestamp of Z.tar.gz

> **eldragon said:**
> 
one long shot is to scan the 200's users bash history files to find suspicious commands. if the attacker didnt cover his tracks well, he would have left that too.

I think that the attacker was wise enough to type unset HISTFILE :(
(I have already checked bash history files)

---

### Post by gnucracker on 2008-09-16
> **cdenley said:**
> Then I agree that they must have had local access through one of your 200 ssh accounts, then used a local exploit to escalate privileges. Local vulnerabilities are much more common than remote vulnerabilities. Either that, or they had physical access.

It's hard to believe that they would be able to find a local vulnerability before a security update has been released for it, but wouldn't be smart enough to delete their hack tools to cover their tracks.

Obviously, I would setup your server again from scratch (if you haven't already) since you don't know what else they did.


It's not possible that they had physical access.. server was located in safe (locked) place. I think that the intruders were skilled hackers because i had latest security updates installed and they were still able to elevate their privileges. I guess that they just forgot Z.tar.gz to my hard drive.

> **cdenley said:**
> 
You said there was "encrypted stuff". You did not say where it came from, but apparently assumed it was from sshd. I guess they couldn't have created that file without root, so they probably could have and probably did install it.

Z.tar.gz contained full source tree for their ssh trojan and while examining the source i noticed that the trojan was using /dev/.tmp
for storing passwords etc. I have already decrypted (by using their decrypter) the /dev/.tmp file and it contained usernames and passwords for over 70 users :(

---

### Post by moonpup on 2008-09-16
Apparently you have a serious problem since you are unable to determine how this crack happened. You need to clone the exisitng drive for further forensic analysis and disconnect this compromised server from the network.

Leaving this connected to the network is a bad idea, no matter how bad the interruption to the user community is. This server will definitely need to be re-built, but not before you clone the drive to some other media.

Keep us posted on anything you find.

---

### Post by FakeOutdoorsman on 2008-09-16
I'm going to regurgitate one of my prior posts because I'm a lowly post recycler:

*Bleh!*

> I highly recommend reading the [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/").  It's up to date and comprehensive, yet easy to follow.

This article give some good info.  For example, how to properly image the drive for forscenic analysis.
[Dead Linux Machines do Tell Tales]("http://www.giac.org/practical/GCFA/James_Fung_GCFA.pdf") [link to pdf]

Corn?  When did I eat corn?

---

### Post by Chayak on 2008-09-17
Keep in mind that once you give people shell access on a box it's only a matter of time for a determined individual to root the box.  It's a lot easier once you have a shell.

Remember that not everyone who finds vulnerabilities publishes them so developers can write patches.  Get all of the logs and use something like splunk to search for segfaults and such.  The application that was exploited is of course going to be of interest to discover and patch.

---

### Post by gnucracker on 2008-09-18
I have disconnect the server from network (and installed Ubuntu again from the scratch). But this is getting worse.. i got today an anonymous email to my university email address. The email is from a finnish hacker who claims that he "rooted" my box using a private exploit that works against kernel > 2.6.24. He claimed that he has compromised many servers on our network by using that same exploit. :(

---

### Post by moonpup on 2008-09-18
> **gnucracker said:**
> I have disconnect the server from network (and installed Ubuntu again from the scratch). But this is getting worse.. i got today an anonymous email to my university email address. The email is from a finnish hacker who claims that he "rooted" my box using a private exploit that works against kernel > 2.6.24. He claimed that he has compromised many servers on our network by using that same exploit. :(

WOW! If that's the case, then you seriously (as I stated before) need to duplicate that disk to other media for forensic analysis. Also, you will most likely need to enlist the help of outside security experts.

If this is really an unknown exploit, you need to find out how this happened. The fact that he even let you know is a bit arrogant, instead of lying low. It sounds as though he wants to see if you can actually kick him out of your network and make a game of it.

You better be very careful before you proceed and consult legal and law enforcement first before doing anything. This is a much larger problem than first thought.

---

### Post by FakeOutdoorsman on 2008-09-18
I agree with moonpup.  Keep us updated.  This is intéressant.

---

### Post by ruik on 2008-09-18
Was the mail sent using a Finnish SMTP server? Or do you have any Finnish IPs that were used in this? I'd be happy to contact any Finnish ISP about this if needed. They usually react quickly.

---

### Post by gnucracker on 2008-09-18
> **ruik said:**
> Was the mail sent using a Finnish SMTP server? Or do you have any Finnish IPs that were used in this? I'd be happy to contact any Finnish ISP about this if needed. They usually react quickly.

The mail was sent using a Canadian SMTP server :(

---

### Post by moonpup on 2008-09-19
I'd like to see this alleged email from the hacker. Are you able to post it here?

---

### Post by Dave_Connor on 2008-09-20
Yeah I would hire a security personal to help with finding this exploit with the kernel and then contact law enforcement with the header of the email.

---

### Post by moonpup on 2008-09-23
So, what's the status with the intrusion? Have you found anything else out? Please keep us informed as we are interested in what you find out.

---

### Post by nubdora on 2008-10-01
Maybe the new flavor of the month? 

[http://searchsecurity.techtarget.com/news/article/0,289142,sid14_gci1332898,00.html](http://searchsecurity.techtarget.com/news/article/0,289142,sid14_gci1332898,00.html)

---

### Post by moonpup on 2008-10-01
Interesting, but I'd still like to hear back from the OP as to what they have discovered in this so called hack and see some proof. So far, I consider it FUD as he has never responded back to post any further info or proof.

---

