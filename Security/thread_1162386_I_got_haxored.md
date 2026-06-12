---
title: "I got haxored"
date: 2009-05-17
forum: Security
---

### Post by rtconner on 2009-05-17
So one of the accounts on my server got hacked. I caught it about an hour afterward when I noticed my bandwidth usage was through the roof. I locked the compromised account, and killed all threads owned by that user.

Am I safe now? Do I need to re-install my server? Delete some software?

I attached the bash log of the compromised account. It seems they installed psybnc-linux.tgz, eggdrop, and parduc.tgz. I don't actually know what any of these do. What was the hacker actually trying to do?

If I remember right, when I did a ps -aux there were like 50 processes running under that user named "./atack 800". I think that was the exact process name. Like I said, I shut them all down.

Any help in getting to the bottom of this, and making sure I'm safe would be appreciated. And out of morbid curiosity I'd really like to know what they were trying to do.

---

### Post by Greyfox_75 on 2009-05-17
If they managed to get root access through that account your entire system could have been affected.  They could have then dome something as simple as replace the rm command with a version of their own that would allow then to gain full access again as soon as you run sudo rm.  I wouldn't trust it. Back it up, then nuke and pave.

---

### Post by rtconner on 2009-05-17
The account didn't have sudo. Or really it didn't have access to anything outside of it's own home directory. I looked around and can actually find no trace of any of those problems being installed currently.

Anyways, really I'm just curious if anyone knows what the hacker was trying to do with my system.

---

### Post by whoop on 2009-05-17
I am (nearly) always against doing a re-install. However there is one exception for me: If the system got compromised (in any way or form).

Your attachment gave some information on what the culprit did. What is far more important is how did the culprit get in.
Let me guess. Ssh with username and password as authentication?

---

### Post by Greyfox_75 on 2009-05-17
> **rtconner said:**
> The account didn't have sudo. Or really it didn't have access to anything outside of it's own home directory.


I figured that much but if the hacker was good enough they may have found something in your system that they could have exploited to escalate their privileges. 

From the history this eggdrop thing looks to be a IRC robot?  The attacker may have installed a IRC server / client so that he could issue commands to your box from an IRC channel instead of over the SSH.  He also deleted the folder .bash renames psybnc to .bash  do scripts / his script in .bash get run every time the user logs in?  This would mean that when you log back in to that user his processes may run again.  Although it may just be an attempt to hide the folder by making it a name that you wouldn't suspect.

Come to think of it why is he running wget on all that text? Maybe a buffer overflow attempt?

Any idea how long this was going on?  You would think a good hacker would have cleared the bash history.

---

### Post by Dr Small on 2009-05-17
From observing the bash history log, it looks like some n00b script kiddie that was probably running a bot across different SSH servers that writes the SSH username/passwords to a file that it bruteforced (and gained authentication). Very easy to do with an expect script.

Then, he downloaded psybnc-linux to /var/tmp/, and eventually moved it to bash. Downloaded eggdrop (an IRC bot), compiled it, removed it, and looked over his shoulder to see if anyone was snooping on him.

Then he downloaded parduc.tgz from the FTP server ftp.atw.hu, and extracted it, deleted the archive and moved the directory to .par in /var/tmp/. Then he was running all of the commands on the last line from inside /var/tmp/.par/

I would say that there is no need to reformat. Just nuke /var/tmp, harden your SSH server (key authentication only) and change the credentials on your exploited account.

Dr Small

---

### Post by rtconner on 2009-05-17
Ok I had a friend look at this also. I think I'm pretty safe.

The hacker got in because the username was equal to the password for that account. I told the owner of it to change his password. Obviously he never did. The server itself is less than a month old. Either way, account is deleted now.

Greyfox_75: I caught him in the middle of it, and locked the account and killed everything before he could finish.

Dr Small: Thanks. You're right there is a bunch of files in /var/tmp/.par - Maybe some of you are interested in looking at whats in there. I'm posting that all as a bz2 file. It looks to be a lot of brute force hacking.

Interesting stuff.

---

### Post by ktrnka on 2009-05-17
I looked over the logs and this script kiddie was using your machine to ssh attack others and trying creating a botnet controlled via encrypted IRC. Nice snag on your part!
+1 to you for stopping the botnet spread. Kudos! :KS

---

### Post by HermanAB on 2009-05-18
Yup, all Linux compromises that I have had to repair were due to some kool d00d using a 4 character password.  It is important that you configure the system to require good quality passwords.

---

### Post by ktrnka on 2009-05-18
> **HermanAB said:**
> Yup, all Linux compromises that I have had to repair were due to some kool d00d using a 4 character password.  It is important that you configure the system to require good quality passwords.

Agreed

---

### Post by Greyfox_75 on 2009-07-06
[http://www.us.debian.org/security/2009/dsa-1826](http://www.us.debian.org/security/2009/dsa-1826)

"It was discovered that eggdrop is vulnerable to a buffer overflow, which could result in a remote user executing arbitrary code. The previous DSA (DSA-1448-1) did not fix the issue correctly."

Your attacker was able to configure and install this program...  I noticed that the copy of eggdrop that the attacker used is every old 6.17 is from august 2004.  It seems strange to me that the attacker is using such an old version.  Possibly an attempt to use a older much more vulnerable version of eggdrop that he could run an exploit against.

Google eggdrop milw0rm and the first result on google is an exploit called "Eggdrop Server Module Message Handling Remote Buffer Overflow" Tested on eggdrop 6.18

If this were my server I would wipe it.  If he was able to execute the buffer overflow and gain root access he could have easily installed some kind of backdoor, rootkit, add accounts, change passwords, anything, and these things may not have showed up on this users bash history.

I would assume that any good hacker trying to create a bot net is equally concerned with his true target, as he is to maintaining access to his bots.

---

### Post by jrusso2 on 2009-07-06
If he was that good of a hacker he would have edited the logs.

---

### Post by philcamlin on 2009-07-06
> **jrusso2 said:**
> If he was that good of a hacker he would have edited the logs.

true you dont just leave it :D

thats liek trying to remote desktop someone while their on the computer :P

FAIL!

---

### Post by credobyte on 2009-07-07
At least from now on you'll know what "password" means :p

---

### Post by Valkyrie12 on 2009-07-09
You wanted to know what they were doing? well Eggdrop is a IRC bot so i dont know what they were doing with that on a SERVER psybnc.linux.tgz is a IRC Daemon..again no clue what he could be doing with a bunch of irc stuff on your server. and i couldent find out about parduct.tgz sorry

---

### Post by credobyte on 2009-07-09
> **Valkyrie12 said:**
> You wanted to know what they were doing? well Eggdrop is a IRC bot so i dont know what they were doing with that on a SERVER psybnc.linux.tgz is a IRC Daemon..again no clue what he could be doing with a bunch of irc stuff on your server. and i couldent find out about parduct.tgz sorry


[LIST=1]
[*]He could activate "ping" on 1000 computers at once ( which could lead into a server being destroyed ).
[*]He could delete all his documents ( or even steal them ).
[*]He could attack NASA website ..
[*]He could .. he could probably do whatever he wants ;)
[/LIST]
Everything depends on what type of "controller" he wanted to install ( can be built in a rush with a lot of "options" ).

---

