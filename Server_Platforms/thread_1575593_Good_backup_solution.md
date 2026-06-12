---
title: "Good backup solution?"
date: 2010-09-16
forum: Server Platforms
---

### Post by CaptSaltyJack on 2010-09-16
I have an Ubuntu server I run for various stuff (web server, SVN server, etc). The hard drive has crashed before, and I lost some stuff, and I'd like to have a backup this time. Ideally I'd like to have some sort of intelligent backup system that will back up config stuff in /etc, my SVN repositories (I suppose it would do an svn dump and back up the resulting dumps), back up home directories, and push all that off to some off-site server. Or at least my desktop Mac, just somewhere where it's safe in case the Linux server dies.

Any suggestions?

---

### Post by CharlesA on 2010-09-16
> **CaptSaltyJack said:**
> I have an Ubuntu server I run for various stuff (web server, SVN server, etc). The hard drive has crashed before, and I lost some stuff, and I'd like to have a backup this time. Ideally I'd like to have some sort of intelligent backup system that will back up config stuff in /etc, my SVN repositories (I suppose it would do an svn dump and back up the resulting dumps), back up home directories, and push all that off to some off-site server. Or at least my desktop Mac, just somewhere where it's safe in case the Linux server dies.

Any suggestions?

I'd suggest rsync, but you'd have to manually tell it what to backup.

It can send files over ssh to remote machines as well.

---

### Post by CaptSaltyJack on 2010-09-16
So you'd recommend just writing a shell script to tar up stuff, dump Subversion repositories, etc., and use rsync to copy files to another machine via ssh?

---

### Post by TiBaal89 on 2010-09-16
I use rsync, it's worked really well for me.  My server is a few websites, a few databases, and some file stuff.  

I set up a script to sql dump all my databases to my home directory on the server.  Then I've got a script on my Mac at home which calls the sql dump thing, then backs up my home dir and all the directories I'm interested in.

Incidentally I use rsync to keep my Mac and Linux home machines backed up and/or sync'd to one another, so really my server stuff is being backed up twice in my home (it's not very large).  Absolutely no problems, really loving rsync.

---

### Post by CharlesA on 2010-09-16
> **CaptSaltyJack said:**
> So you'd recommend just writing a shell script to tar up stuff, dump Subversion repositories, etc., and use rsync to copy files to another machine via ssh?
It would seem the easiest way to go about it. :)

---

### Post by BkkBonanza on 2010-09-16
This informative page was posted on another rsync thread. It takes you from the basics right up to incremental snapshots if you want them. He has example scripts (that are fairly involved) and lots of links to other source info. It is a bit dated but still works.

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

The nice thing about rsync is it only needs to copy changed files, so backups can be quite fast. Rsync will use ssh automatically if going to another machine. Set up key auth (easy) and it can all be done in the background, and automated.

If you do tar first it should still work quite well as it only copies the portions of the file that are changed.

---

### Post by CaptSaltyJack on 2010-09-16
Thanks, guys! That was easy. I'm using rsync with options -Cavz to copy files to another machine on the network, and set up an SSH key with a blank password so it can connect without needing intervention. Not sure if that's the most secure, but someone would have to break in as root to access my Mac without a password, and SSH doesn't allow logins as root.

---

### Post by CharlesA on 2010-09-17
> **CaptSaltyJack said:**
> Thanks, guys! That was easy. I'm using rsync with options -Cavz to copy files to another machine on the network, and set up an SSH key with a blank password so it can connect without needing intervention. Not sure if that's the most secure, but someone would have to break in as root to access my Mac without a password, and SSH doesn't allow logins as root.

You could probably just use a key with no passphrase. That would be a tiny bit more secure. :)

---

### Post by CaptSaltyJack on 2010-09-17
> **CharlesA said:**
> You could probably just use a key with no passphrase. That would be a tiny bit more secure. :)

Er.. yeah. That's what I said. :) It's an SSH key with no password/passphrase. Well, I know I said "blank" but.. the important part was "SSH key." It's not like someone can just SSH or telnet in and hit 'enter' for the password. :)

---

### Post by CharlesA on 2010-09-17
D'oh! All I read was "blank" and I guess I figured you meant password. :lolflag:

Glad it's working out for you. :)

---

### Post by CaptSaltyJack on 2010-09-17
Haha, no worries, I can see how it was slightly confusing.

Yeah, it works quite well. I just had to spend some time thinking about security. The Linux server is open to the world, which I'm fine with since it's pretty damn secure. My main computer (Mac), however, is sealed off from the world of course. If someone compromised my Linux box, I definitely wouldn't want them to access my Mac. So like I said, they'd have to actually gain root access and root cannot log into the machine at all, and technically I don't even think there's a password for root (not that it's blank, you just can't log in). They'd have to actually log in as me and use sudo to cause damage, and my password is completely not guessable and never transmitted over the net unless encrypted.

I love Linux for its security. :)

---

### Post by CharlesA on 2010-09-17
You could always just lock down what has access to the linux server from outside, by using iptables.

The root account is locked by default in Ubuntu, so there is no password on it and it can't be used to login.

But yeah, my server is only accessible from the net via SSH and it's locked down with keys only. Good luck getting connected.

---

### Post by CaptSaltyJack on 2010-09-17
> **CharlesA said:**
> You could always just lock down what has access to the linux server from outside, by using iptables.

The root account is locked by default in Ubuntu, so there is no password on it and it can't be used to login.

Hmm, you seem to know way more than me about this. :) Right now I've got denyhosts running which will auto-block fools (bots?) trying to SSH into my Linux box. I don't wanna block outside SSH access, though.. I have friends who use it, and I like the ability to use it as a secure tunnel if I'm out on the road.

What would you recommend, to tighten security on my Linux machine? How would I go about using iptables to tighten things up? I believe the only ports I have open are for SSH, HTTP, and HTTPS.

---

### Post by CharlesA on 2010-09-17
If you are using keys and denyhosts, you should be fine.

As for me, I'm just running iptables and ssh using keys only.

The rule I have for iptables is to drop any traffic on port 22 from a certain ip address if there are 8 "hits" in a minute. It doesn't log anything (I don't care about the info, since they aren't getting in anyway)

Here's the rule:

```
# 10 minute lockout if trying to bruteforce
-A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
-A INPUT -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH  --rsource -j DROP

```

Throw it in a file and use iptables-apply or iptables-restore to apply it.

---

### Post by CaptSaltyJack on 2010-09-17
Cool, thanks!

---

