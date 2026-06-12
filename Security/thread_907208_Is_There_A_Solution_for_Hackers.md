---
title: "Is There A Solution for Hackers?"
date: 2008-09-01
forum: Security
---

### Post by matey3 on 2008-09-01
I recently got to check my auth.log file on one of my servers (which is a xen/virtual server running  Ubuntu 7.04 Feisty) and is the root server for  other virtual/xen servers and one of those v-servers is our company's web server and I noticed there has been several attempts for breaking in!

I am a Newbie in Linux and wondered if there is any files where I could put these IP addresses in a blacklist so they cant even connect let alone try to log in?
(I would really like to have a script where if any IP address tried 3 times to get in and failed, then their IP would automatically go in that file (the *hit-list file)!?but I know that is a little too much...for now I'll be happy with any info...)



The log file states the same IP addresses and several names (including root) trying to hack in and that has us worried as to what if the idiots get in?

I know it is not so easy...specially after I ran the recent updates I can't log in as root my self via ssh any more and have to log in as another user then su or log in to the master server then do a xm console to the server I  want to log in and only then I can get in.
 
Still looks like some one is running a script and taking a guess at the names of users and passwords...

I have a difficult password installed (not any word in dictionary or anything just a long, random alphanumeric password)...


My other Question is, is there any thing I can do to get rid of these hackers?

look at this idiot please:
(just a couple of lines from 100s of lines in that log file):

 Sep  1 04:37:21 tyr sshd[32765]: Failed password for invalid user  gerbertus from 79.187.241.62 port 29389 ssh2
Sep  1 04:37:25 tyr sshd[344]: Invalid user hupertus from 79.187.241.62
Sep  1 05:09:32 tyr sshd[18848]: Failed password for invalid user max from 79.187.241.62 port 15211 ssh2
Sep  1 05:09:36 tyr sshd[18896]: Invalid user maximilian from 79.187.241.62
Sep  1 05:09:36 tyr sshd[18896]: (pam_unix) check pass; user unknown



or this one:

Sep  1 13:53:20 tyr sshd[25487]: Failed password for root from 82.179.130.135 port 54748 ssh2
Sep  1 13:53:20 tyr sshd[25519]: Invalid user sbin from 82.179.130.135
Sep  1 13:53:20 tyr sshd[25519]: (pam_unix) check pass; user unknown
Sep  1 13:53:20 tyr sshd[25519]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=unixway.tversu.ru 
Sep  1 13:53:22 tyr sshd[25519]: Failed password for invalid user sbin from 82.179.130.135 port 55187 ssh2
Sep  1 13:53:23 tyr sshd[25545]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=unixway.tversu.ru  user=root


and at least 3 more IP addresses since Aug 29th,( 2008 )from different parts of the world...


Thank You!

---

### Post by yaztromo on 2008-09-01
You can use denyhosts to block the IP after x failed attempts:

[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

---

### Post by Nepherte on 2008-09-01
You could also change the port the ssh server listens to for incoming connections. Most of these attacks are only scripts that target port 22 (the default ssh port).

---

### Post by matey3 on 2008-09-01
> **yaztromo said:**
> You can use denyhosts to block the IP after x failed attempts:

[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

Thank You for the link...

I was wondering about that file myself but I could Not find a clear example off google yet!? I am not sure how the IP addresses go in that .deny file? Many ppl suggested using a firewall but I have not had a very good experience with firewall before and I dont want to lock myself out lol..
Thanks for the reply !


> **Nepherte said:**
> You could also change the port the ssh server listens to for incoming connections. Most of these attacks are only scripts that target port 22 (the default ssh port).

Thanks very much for the suggestion. You are right bcs I saw the port 22 in that log file.
I appreciate your reply as well!
:)

---

### Post by mellowd on 2008-09-01
You could also set up a vpn, a refuse any connections not going through that vpn

---

### Post by rogeriopvl on 2008-09-01
Just changing the SSH port will dramatically decrease to 0% of hacking attempts.

I had an ssh server running for one day, with the default port and had like, 90 attemps, which is insane. After I changed the port to a higher one, the server is running for about half a year, and still no attempts.

---

### Post by mellowd on 2008-09-01
> **rogeriopvl said:**
> Just changing the SSH port will dramatically decrease to 0% of hacking attempts.



Decrease yes, 0% no

---

### Post by rogeriopvl on 2008-09-01
> **mellowd said:**
> Decrease yes, 0% no

Well, that's the experience I had with my personal server. So far is 0%.

I never that experience with big servers because changing the SSH port was out of question.

---

### Post by Dr Small on 2008-09-01
Just install denyhosts and you should be fine. Unless you have a weak password on a user called root, the script attacks won't do anything but fill your logs. I really wouldn't worry with it.

---

### Post by Oldsoldier2003 on 2008-09-02
> **Dr Small said:**
> Just install denyhosts and you should be fine. Unless you have a weak password on a user called root, the script attacks won't do anything but fill your logs. I really wouldn't worry with it.

+1
Denyhosts and a strong password is rock solid. If you are even more paranoid go with public key auth, and allow authorized ssh users only.

---

### Post by gtdaqua on 2008-09-02
Before installing denyhosts, I used to have thousands (yes, thats right) of attempts with usernames starting from A to Z and other dictionary words. None was successful!

Then I installed denyhosts a few months ago and as of now I have exactly 160 blacklisted IPs. Definitely denyhosts is a must to keep hackers away.

It can not only blacklist IP addresses service wise, it can also block the IPs entirely (all services).

---

### Post by Thomas00 on 2008-12-29
"Norton is genius anti virus software and famous for his work efficiency. The [www.search-and-destroy.com](www.search-and-destroy.com) is also proved his name is the market of anti virus software i suggest you this one that try it.

Thank You."

---

