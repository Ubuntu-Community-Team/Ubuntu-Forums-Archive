---
title: "My site has been hacked"
date: 2008-08-12
forum: Server Platforms
---

### Post by Mirrorball on 2008-08-12
Someone was able to modify .htaccess and redirect the browser to a malicious site. Should I assume the server has been compromised and reinstall the whole thing?

---

### Post by Vishal Agarwal on 2008-08-12
> **Mirrorball said:**
> Someone was able to modify .htaccess and redirect the browser to a malicious site. Should I assume the server has been compromised and reinstall the whole thing?

first of all stop the ssh server
> /etc/init.d/sshd stop

---

### Post by Mirrorball on 2008-08-12
Thanks, I just did that. And now what should I do?

---

### Post by hyper_ch on 2008-08-12
with the information given there's not much of advice to give to you... you'll have to go through the logs. Did you have any insecure php programs installed that could be abused... did the "hacker" get access somehow?
PHPBB2 for example was known to be full of security bugs... PHPNuke was known to be abused as spamming machine.... without any information there's nothing that can be advised

EXCEPT if you want to be sure, make a new install.

---

### Post by Mirrorball on 2008-08-12
I have vbulletin and custom scripts that have never been hacked before. I would hate to reinstall the server, then find out the server was fine and the site has been hacked through an insecure PHP script. Which logs do you think I should check? What should I look for? Sorry, I've never had a security problem before with any of my Linux servers.

---

### Post by Vishal Agarwal on 2008-08-12
check the log files in /var/log,

check the auth.log file with 

> cat /var/log/auth.log | more

to know who has logged into the server. check for any unknown user.

stop the ssh access from outside using iptables.

Also u can change the port for ssh login.

---

### Post by Master Chief on 2008-08-12
Are you using easy to guess or strong passwords?
What is the new destination (url)?
How are you (the server) connected to the Internet (DSL modem)?
Which PHP version are you using?
Which PHP modules did you enable/install?

---

### Post by Mirrorball on 2008-08-12
OK, the hacked file was uploaded by FTP. I'm going to change that account's password and hope for the best.

---

### Post by Mirrorball on 2008-08-12
Now I wonder how the hacker got my password...

---

### Post by osjak on 2008-08-12
> **Mirrorball said:**
> OK, the hacked file was uploaded by FTP. I'm going to change that account's password and hope for the best.
Mirrorball, I would suggest to ditch FTP all together. There is a way more secure alternative - use WinSCP over your SSH connection (assuming your desktop is Windows). It performs the same function as FTP client, but over a secure connection. You can uninstall your FTP server then, eliminating one open port to hack into your server.

---

### Post by Mirrorball on 2008-08-12
Someone else had logged in as another user and created a cron job.

---

### Post by Mirrorball on 2008-08-12
> **osjak said:**
> Mirrorball, I would suggest to ditch FTP all together. There is a way more secure alternative - use WinSCP over your SSH connection (assuming your desktop is Windows). It performs the same function as FTP client, but over a secure connection. You can uninstall your FTP server then, eliminating one open port to hack into your server.
My desktops run Linux and Mac OS X. I have the FTP server because it's easier for users to upload files. Apparently it's easier for hackers to upload files too. :(

---

### Post by osjak on 2008-08-12
> **Mirrorball said:**
> Someone else had logged in as another user and created a cron job.
Unfortunately, I personally would consider this server totally compromised at this point. You don't know if a rootkit was installed, or what happened to the system. Full reinstall is needed. This is my paranoid point of view. But then again, as I was pointed out at this forum, not everyone has as many enemies as I do :)

> **Mirrorball said:**
> My desktops run Linux and Mac OS X. I have the FTP server because it's easier for users to upload files. Apparently it's easier for hackers to upload files too. :(
Who are your users? If you have just a couple of people storing files at your server, it may be easier to help them switch to transfers over SSH (SCP). A decent Linux desktop client is gFTP; it naturally supports SCP transfers.

If you have really many users, then you probably need to read and learn secure FTP configuration. Those would be my ideas.

---

### Post by Mirrorball on 2008-08-12
I had just a couple of users uploading files. I'm going to tell them to switch to SSH. The cron job scared me too, although rkhunter didn't find anything. I think I'm going to reinstall everything as soon as I can. Thank you.

---

### Post by eXDee on 2008-08-12
Tell them to use Filezilla - its an awesome FTP client which supports SSH file transfer. Multiplatform too.

---

### Post by hyper_ch on 2008-08-12
you could also install mysecure shell and chroot those users to their own directory and prevent them setting up crons.

---

### Post by Mirrorball on 2008-08-12
> **eXDee said:**
> Tell them to use Filezilla - its an awesome FTP client which supports SSH file transfer. Multiplatform too.
Thanks, it's what I use too.
> you could also install mysecure shell and chroot those users to their own directory and prevent them setting up crons.
I'll make sure they won't be able to  set up crons from now on.

---

### Post by gtdaqua on 2008-08-12
one more point of view: try to rule out this is not an 'internal' attack. from what you say, users already have some privileges via ftp. Take out this possibility first. Many attacks originate from inside also - which obviously your edge firewalls cant block.

---

### Post by Mirrorball on 2008-08-12
> **gtdaqua said:**
> one more point of view: try to rule out this is not an 'internal' attack. from what you say, users already have some privileges via ftp. Take out this possibility first. Many attacks originate from inside also - which obviously your edge firewalls cant block.
I've already uninstalled the FTP server. Those users can still connect by SSH, but I've changed their passwords.

---

### Post by gtdaqua on 2008-08-12
> **Mirrorball said:**
> I've already uninstalled the FTP server. Those users can still connect by SSH, but I've changed their passwords.

what i meant was, rule out if the attack was performed by any of the internal users.

**If you are having openssh-server**, install 'denyhosts' and configure to monitor all open services. Denyhosts will block all brute-force attempts and ban the IP address. An email report can configured once an IP is banned.

An attacker outside would have to run a  brute-force to guess the password. His IP would definitely show up after 5 failed attempts.

Remember, security has some (or several) psychological features. Rule out the possibilites and do it all over again. Your greatest enemy will be in the last place you would ever loook.

---

### Post by Mirrorball on 2008-08-12
> what i meant was, rule out if the attack was performed by any of the internal users.
They don't have the new passwords, they are people that I trust, and I don't know how they could have gotten *my* password from their accounts. I'll restrict their privileges as much as I can after I reinstall the server and give them their new passwords, but I can't believe the attack came from one of them. Thanks for the denyhosts tip.
> Your greatest enemy will be in the last place you would ever loook.
This is scary.

---

### Post by MJN on 2008-08-12
What was your password? Could it have been vulnerable to a dictionary/bruteforce attack?
 
Mathew

---

### Post by windependence on 2008-08-12
> **MJN said:**
> What was your password? Could it have been vulnerable to a dictionary/bruteforce attack?
 
Mathew

Exactly what I was thinking. Neither my user names OR my passwords are dictionary words. Many people think if they use a lesser known word or if they just substitute numbers for letters that is secure. It isn't. Make them guess both the user name and the password. Don't use regular names for user accounts and don't enable root logins.

Just a tip, for your mac clients on ssh use Fugu. It's like WinSCP for the mac. This is why I'm so anal about installing FTP servers. It's not you, you need to worry about, it's your users. They mostly always don't understand good security, so many times you can get hacked using one of their accounts. Walling off their home directories as has been suggested is also good practice.

I am with what one poster said though, you can't be sure at this point what was compromised so a wipe and install is probably what needs to be done.

Also, think about running a good HARDWARE firewall. It would not have prevented this but there are other things like a DDOS attack where a software firewall will drop to it's knees just from the sheer volume of requests. That's what they intend to do. Don't let 'em. ;)

-Tim

---

### Post by Joeb454 on 2008-08-12
I'd recommend changing the port that the ssh server listens on. Especially if it's still on port 22, change it to something like port 27536 (not necessarily that on in particular, but you get the point ;))

---

### Post by windependence on 2008-08-12
> **Joeb454 said:**
> I'd recommend changing the port that the ssh server listens on. Especially if it's still on port 22, change it to something like port 27536 (not necessarily that on in particular, but you get the point ;))

Well although I agree, it doesn't do too much. Read this post by Lars. He is right on the money.

[http://ubuntuforums.org/showpost.php?p=5572415&postcount=2](http://ubuntuforums.org/showpost.php?p=5572415&postcount=2)

-Tim

---

### Post by Mirrorball on 2008-08-12
My password had been randomly generated. 8 characters, including letters and numbers. The username wasn't a dictionary word.

---

### Post by Joeb454 on 2008-08-12
include some special characters like a * or something, that often helps

---

### Post by FakeOutdoorsman on 2008-08-12
I highly recommend reading the [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/").  It's up to date and comprehensive, yet easy to follow.

Also, if you haven't wiped your machine yet here are some interesting forscenics:
[Dead Linux Machines do Tell Tales]("http://www.giac.org/practical/GCFA/James_Fung_GCFA.pdf") [link to pdf]
[Holiday Cracking]("http://blog.gnist.org/article.php?story=HollidayCracking")

---

### Post by Mirrorball on 2008-08-12
I haven't wiped my server yet, thank you for the links. I never thought this thread would have so many replies with so much helpful advice.

---

### Post by Vishal Agarwal on 2008-08-13
I have created one shell script to run the following command.
> logwatch --mailto mymailid1,mymailid2

This command gives me the detailed log report for all the happenings to my server.
Which includes even the
1. All regarding mail (Addresses white listed from SpamAccessin etc.)
2. All the Mail bounced.
3. All the login attempts to my server (I can chase my ISP thru this log report)

and much more.

Try this command, and set cron entry for daily execution. 
And check your report daily. In my opinion, Hacking can not be done in a single day. The hacker might be trying for some some days. So any unusual entry will be marked out by you.

I hope this will help.

---

### Post by MJN on 2008-08-13
> **Vishal Agarwal said:**
> In my opinion, Hacking can not be done in a single day. The hacker might be trying for some some days.

Software vulnerability exploits are immediate, as are password compromises (keylogger, over-the-shoulder observation etc). In the OPs case they had a strong password and so you can almost rule out bruteforce/dictionary attacks which the logs would have otherwise picked up on.

Not that I'm saying watching the logs, particularly through a log parser/analyser, is not a very good idea - just pointing out that they are not the be all and end all and are no substitute for good security in the first instance.

Mathew

---

### Post by Vishal Agarwal on 2008-08-14
> **MJN said:**
> Software vulnerability exploits are immediate, as are password compromises (keylogger, over-the-shoulder observation etc). In the OPs case they had a strong password and so you can almost rule out bruteforce/dictionary attacks which the logs would have otherwise picked up on.


Can be True. I am not very much confident, Regarding my knowledge for Hacking.

---

### Post by Vishal Agarwal on 2008-08-14
Can any body help me knowing what are the different common ways for hacking?

---

### Post by MJN on 2008-08-14
Well, I wouldn't consider even remotely knowledgeable about the subject - not least because much of it is by definition bleeding edge stuff - however the info is out there if you want to learn more.

As a good starter for ten check out the Wikipedia article at [http://en.wikipedia.org/wiki/Hacker_%28computer_security%29](http://en.wikipedia.org/wiki/Hacker_%28computer_security%29) - it appears to provide a nice overview and serves as a portal for learning more about specific methods and concepts etc.

Mathew

---

