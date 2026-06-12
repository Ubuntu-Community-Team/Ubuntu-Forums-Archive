---
title: "Recover from compromised machine"
date: 2009-09-28
forum: Security
---

### Post by marcos904 on 2009-09-28
Hello,

Earlier today I noticed that my internet connection was much busier than it should have been and after some checking I discovered that someone had broken into my Ubuntu 9.04 box, created an account for themselves (with the name 'jessie'), downloaded some files into /var/tmp/..., and was running pbscan2 and psybnc.  

I immediately unplugged the ethernet cable from the computer and started looking at the logs.  In doesn't appear that whoever broke in tried to obscure their tracks, the .bash_history files for the root and jessie accounts appear intact and complete (if anyone is interested I can post them).

I realize the system logs can be erased or falsified but there aren't any gaps in the auth.log files and for all the world it looks like they broke in by knowing the root password, which bothers me since I never enabled the root account (the first thing they did after logging in as in root was run 'passwd') and the only port I have open on my firewall is 22 and my system is current with updates.  

At this point I have two concerns: making sure the only files they added or modified are the ones I know about (i.e. no trojans in /bin) and figuring out how they broke in in the first place so I can make sure it doesn't happen again.

Suggestions?

marcos

---

### Post by renkinjutsu on 2009-09-28
I'm not security expert, but if the attacker indeed modified some bin files or replaced them, you can probably search for them using the `find` command with the `-mtime` parameter to list all the files modified within a certain amount of time (you can go back weeks... months even)

---

### Post by amac777 on 2009-09-28
If you enabled port 22 (SSH) and your username / password are both guessable, then the hacker probably first logged in to your account, then enabled the root account themselves from your account, and then started using root and making the other account(s).

So the weak link in the chain might be your password. 

Anyway, once a system is compromised, best to never trust it again. Keep it unplugged until you have a good idea how they got in, and then reinstall and make sure that hole is plugged up tight.

---

### Post by rookcifer on 2009-09-28
Yet another example of a machine being rooted via a non-existent or weak ssh password.

---

### Post by doas777 on 2009-09-28
rebuild. if you can confirm illicit access, then you have just cause, and to be honest, it's the only way to know it's clean.

---

### Post by ApEkV2 on 2009-09-28
Could I take a look at your logs, as i've never seen a system compromised before. 
I've tried to get mine compromised quite a few times (public services, weak passwords, dmz, and other etc), but never happened.
I would like to know what it looks like in the logs so I can spot an attempt at compromise.

---

### Post by marcos904 on 2009-09-28
> **amac777 said:**
> If you enabled port 22 (SSH) and your username / password are both guessable, then the hacker probably first logged in to your account, then enabled the root account themselves from your account, and then started using root and making the other account(s).

So the weak link in the chain might be your password. 


There is no evidence of that anyone guessed my username or password.  In particular there are many "Failed password for" messages in the auth.log files, but none with my username (just the usual ones: root, test, support, tomcat, fabio (?), ...).  Also all of the succeeded logins with my username are from IP addresses that I recognize.  I know the logs could have been altered, but they left so much other evidence I don't believe they did.

marcos

---

### Post by norm7446 on 2009-09-28
Never use the same password for all your account's, as once that has been compromised all things you do on the Internet can be accessed.

---

### Post by rookcifer on 2009-09-28
> **marcos904 said:**
> There is no evidence of that anyone guessed my username or password. 

They got in somehow and since port 22 is the only port you had listening, it *had* to be through ssh.  Perhaps they brute forced it or perhaps you were the victim to an unknown ssh exploit (doubtful).  Either way, I would wager ssh is the culprit.  

People come on here almost daily after someone cracked their box via ssh.  It happens all too often and is quite disappointing that many people cannot even take the time to set-up a password.

---

### Post by aesis05401 on 2009-09-28
> **rookcifer said:**
> ... *snip* People come on here almost daily after someone cracked their box via ssh.  It happens all too often and is quite disappointing that many people cannot even take the time to set-up a password.

Last I checked passwords were discouraged for ssh accounts.  Is anyone recommending anything but key authentication at this point?

---

### Post by amac777 on 2009-09-28
> **marcos904 said:**
> There is no evidence of that anyone guessed my username or password.  In particular there are many "Failed password for" messages in the auth.log files, but none with my username (just the usual ones: root, test, support, tomcat, fabio (?), ...).  Also all of the succeeded logins with my username are from IP addresses that I recognize.  I know the logs could have been altered, but they left so much other evidence I don't believe they did.
marcos

Hmmm.. Do you have any other accounts on your machine then? For example a "test" account with password "test" or something like that you made a long time ago and forgot about but that account actually has sudo access? Or perhaps you enabled remote desktop access (VNC) one time just to try it and forgot to turn it off and a hacker found it and broke that password? Or do you run a personal webserver that allows file uploads? There are so many ways to make your computer insecure while testing all the fun software that can be installed on ubuntu. It's a learning experience for sure. Really technical exploits by hackers that don't require the user to do anything silly are possible (in theory) but very rare in actuality. I'd say the odds are you (or somebody using your computer) opened up a hole that the hacker simply walked through. Just need to figure out that hole now so you don't do it again after you reinstall.

---

### Post by rookcifer on 2009-09-29
> **aesis05401 said:**
> Last I checked passwords were discouraged for ssh accounts.  Is anyone recommending anything but key authentication at this point?

No, you're right, key authentication is definitely the way to go.  But I find that often people wont even use good passwords, much less key authentication.

---

### Post by mohnkern on 2009-09-29
Honestly, if someone had root access on your box they only way to be 100% sure there isn't something stray hanging around is to rebuild the box.  It is a big pita, but that's the unfortunate truth.

Was the box completely updated before the compromise?  Are you sure you didn't have anything else running that might have been exploited?

netstat -Nl will let you know whats running.  It's not uncommon to have amail server and a sql server running on the box.

---

