---
title: "Strange IRC Connects from my Server - Comprimised?"
date: 2008-03-20
forum: Server Platforms
---

### Post by chrisi99 on 2008-03-20
Hi there!

Today I was checking my netstat (used to do that once in a while) and ran over some very strange thing:

```

tcp        0      0 debian.localdomain:smtp 184.14.218.87.dyna:3036 TIME_WAIT
tcp        0      0 debian.localdomai:33311 undernet.xs4all.nl:ircd ESTABLISHED
tcp        0      0 debian.localdomai:33305 undernet.xs4all.nl:ircd ESTABLISHED
tcp        0      0 debian.localdomai:33297 undernet.xs4all.nl:ircd ESTABLISHED
tcp        0      0 debian.localdomai:33325 undernet.xs4all.nl:ircd ESTABLISHED
tcp        0      0 debian.localdomai:46118 debian-mirror.mirro:www TIME_WAIT
tcp        0      0 debian.localdomai:50627 efnet.teleglobe.ne:ircd ESTABLISHED
tcp        0      0 debian.localdomai:36671 irc2.saunalahti.fi:6666 ESTABLISHED

```

the first line is my mailprogram, but i cant figure out, what might possibly connect to an IRC-Channel from my Server?!

I immediately checked my logs, but didn't find logins except from my machine, some attempts though, but the were all blocked by denyhosts.

Has anyone else had that behaviour and/or can offer me a solution?

The server is basically just serving emails, no ftp, a tiny webpage (apache2), nothing else...


best regards
Christoph

PS: excuse my english, I am from Austria

---

### Post by SmarterThanMyPhone on 2008-03-20
you might be sporting a nice rootkit, if your seeing change in disc space it could be using your server to distribute warez on one of the channels on those servers. if you see traffic and not size change Id suspect spamming, and if its just idle or has little traffic, it might just be a worm listening for a connection off of one of the servers.
If that is the case, you may want to try a rootkit detection program, I used to use them for the windows machines in my office all the time, I dont however know of any for a linux box.

---

### Post by chrisi99 on 2008-03-20
I did the usual: chkrootkit and rkhunter, all thumbs up there..

a netstat -p gives me a process name /bash... which does not look too good...

any advice how to proceed from here? Though there is nothing critical on my server i just dont have the time to set it up all new, so a repair at least for the next month would be greatly appreciated! :)

best regards

---

### Post by FakeOutdoorsman on 2008-03-20
A lack of logs could be considered suspicious since they can be removed to hide suspicious activity.  Check for new users on your system with "cat /etc/passwd" or if there are other users with shell access with "sudo cat /etc/shadow".  Look in /tmp and /var/tmp for odd files.  Run the "w" command to show who is logged on and what they are doing.

Here is a case study: [Holiday cracking]("http://blog.gnist.org/article.php?story=HollidayCracking").
Other links: [How to restore a hacked Linux server]("http://www.ducea.com/2006/07/17/how-to-restore-a-hacked-linux-server/"), [Dead Linux Machines Do Tell Tales]("http://www.sans.org/reading_room/whitepapers/honors/1491.php?portal=1dc404247f44e66822a183dc17da1ca6") [PDF file]

The most secure thing to do is backup, wipe the drive, and make a fresh reinstall.

Don't apologize for your English.  I wouldn't have guessed it is a second language for you.

---

### Post by chrisi99 on 2008-03-20
> **FakeOutdoorsman said:**
> 

Don't apologize for your English.  I wouldn't have guessed it is a second language for you.

well, the only flattering thing after a long day of hard underappreciated work ;) Thank you for that...

the passwd showed no new accounts nor were other accounts altered (at least the dates match).

a clamscan didn't bring anything unusual up, the manual check on the tmp-folders brought up nothing either....

a netstat -p shows:

```

tcp        0      0 debian.localdomai:39993 undernet.xs4all.nl:ircd ESTABLISHED 2608/bash
tcp        0      0 debian.localdomai:40000 undernet.xs4all.nl:ircd ESTABLISHED 2608/bash
tcp        0      0 debian.localdomai:44610 irc2.saunalahti.fi:ircd ESTABLISHED 2608/bash

```

is there a way to find out where the altered bash may be located on my system or restore the original bash?

lsof:```
lsof -p 2608
COMMAND  PID USER   FD   TYPE DEVICE    SIZE   NODE NAME
bash    2608 root  cwd    DIR    8,1    4096 114585 /lib/security/etc
bash    2608 root  rtd    DIR    8,1    4096      2 /
bash    2608 root  txt    REG    8,1  492135 117521 /lib/security/etc/bash
bash    2608 root  mem    REG    0,0              0 [heap] (stat: No such file or directory)
bash    2608 root  mem    REG    8,1   67364 130844 /lib/tls/i686/cmov/libresolv-2.3.6.so
bash    2608 root  mem    REG    8,1   17840 130833 /lib/tls/i686/cmov/libnss_dns-2.3.6.so
bash    2608 root  mem    REG    8,1   38372 130835 /lib/tls/i686/cmov/libnss_files-2.3.6.so
bash    2608 root  mem    REG    8,1 1241392 130822 /lib/tls/i686/cmov/libc-2.3.6.so
bash    2608 root  mem    REG    8,1   88164 114551 /lib/ld-2.3.6.so
bash    2608 root    0w   REG    8,1     251 117524 /lib/security/etc/LinkEvents
bash    2608 root    1u  IPv4   9391            TCP debian.localdomain:40000->undernet.xs4all.nl:ircd (ESTABLISHED)
bash    2608 root    2u  IPv4   9007            TCP debian.localdomain:44610->irc2.saunalahti.fi:ircd (ESTABLISHED)
bash    2608 root    3u  IPv4   8879            UDP *:32773
bash    2608 root    4u  IPv4   8974            TCP debian.localdomain:39993->undernet.xs4all.nl:ircd (ESTABLISHED)

```



A new built from scratch would be the best as I am well aware of, but out of question because of my lack of time atm....
 best regards
Chris

---

### Post by FakeOutdoorsman on 2008-03-20
Also check "sudo cat /etc/shadow".  Old accounts could have been given shell access.  These accounts will have longer character strings than the others.  Now find all bash history files:
```
find / -name .*history -exec ls -la {} \;
```
and
```
sudo updatedb
locate .bash_history
```

Look inside these files for any odd commands.

---

### Post by chrisi99 on 2008-03-20
hm i dont recall typing in those 3 lines, but they may be from a Script i used from our university to connect to the vnc viewer...

```

netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1|sort|uniq -c|sort -nk 1
netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1|sort|uniq -c|sort -nk 1
tcpdump -npi eth0 port http

```

anyway, they don't look suspicious to me in the matter we are discussing right now...

i checked all the auth-logs, showed some failed login attemps, but that is not too unusual since i recently got a new IP and there may have been another server at that address...

oh i hate those unclear situations.. i surely do :(

---

### Post by FakeOutdoorsman on 2008-03-20
Others have been connected to this IRC channel:  [Someone broke into my machine today.]("http://ubuntuforums.org/showthread.php?t=124108")

---

### Post by koenn on 2008-03-20
> **chrisi99 said:**
> hm i dont recall typing in those 3 lines, but they may be from a Script i used from our university to connect to the vnc viewer...

```

netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1|sort|uniq -c|sort -nk 1
netstat -plan|grep :80|awk {'print $5'}|cut -d: -f 1|sort|uniq -c|sort -nk 1
tcpdump -npi eth0 port http

```

anyway, they don't look suspicious to me in the matter we are discussing right now...

i checked all the auth-logs, showed some failed login attemps, but that is not too unusual since i recently got a new IP and there may have been another server at that address...

oh i hate those unclear situations.. i surely do :(
I wouldn't dismiss them yet. 
These are commands to track http traffic, i don't see why a script to  connect to vnc would need that
. The tcpdump runs interactively, it wouldn't make much sense in a script beause it would continue to show packets of http connectins until the user hits ctrl+C

---

### Post by FakeOutdoorsman on 2008-03-20
Take a quick look though /var/log/auth.log files again:
```
grep "Accepted password" /var/log/auth.*
```

A bit easier to read and will show successful logins via a password.

---

### Post by chrisi99 on 2008-03-20
seems to be related to my case... unfortunately there is no obvious process in the list to be killed and deleted....

I could bite myself in the *** as we use to say in Austria, where could that stupid script be hidden - my system partition is quite small and no large change of file sizes occured (as for the danger to be distributing warez)...

---

### Post by chrisi99 on 2008-03-20
> **FakeOutdoorsman said:**
> Take a quick look though /var/log/auth.log files again:
```
grep "Accepted password" /var/log/auth.*
```

A bit easier to read and will show successful logins via a password.

did that similar before, the only thing i couldn't make sense of is the change of format (it is my IP though):

```

/var/log/auth.log:Mar 18 23:13:56 debian sshd[26137]: Accepted password for notroot from 84.119.48.221 port 1423 ssh2
/var/log/auth.log:Mar 19 04:10:12 debian sshd[25744]: Accepted password for notroot from ::ffff:84.119.48.221 port 1170 ssh2

```

---

### Post by chrisi99 on 2008-03-20
> **koenn said:**
> I wouldn't dismiss them yet. 
These are commands to track http traffic, i don't see why a script to  connect to vnc would need that
. The tcpdump runs interactively, it wouldn't make much sense in a script beause it would continue to show packets of http connectins until the user hits ctrl+C


the dump is from me, sry for that, missed that one on the copy&paste!

---

### Post by |{urse on 2008-03-20
do a /who to see who is currently logged in, for giggles. also, if you have a rootkit, chances are its already been removed and an nfs mount has been made for whoever hacked you ( if anyone did ) you may be botted =/ at any rate /who , you may at least get a unmasked ip to report or um do whatever with ^^

---

### Post by |{urse on 2008-03-20
sorry type
 who

without the /slash
/me has had too much irc :lolflag:

---

### Post by chrisi99 on 2008-03-20
if there is no way to be logged in "hidden" it is just me logged in...

---

### Post by |{urse on 2008-03-20
[http://linux.softpedia.com/get/Security/Rootkit-Hunter-4460.shtml]("http://linux.softpedia.com/get/Security/Rootkit-Hunter-4460.shtml")
I youre worried about a rootkit though it might be a good idea to scan for one.
heres a pretty decent scanner.

---

### Post by |{urse on 2008-03-20
if you need help installing that.

tar zxf rkhunter-<version>.tar.gz
    cd rkhunter-<version>
    ./installer.sh --layout default --install

---

### Post by chrisi99 on 2008-03-20
Thank you, but i already did that one as mentioned before ;)

---

### Post by |{urse on 2008-03-20
well crap, i dint see that. :) jut for present and future monitoring you might want to use an advanced system logging program like syslog -ng 
it costs $299 us /yr for my company but i think it's gpl'd. ill go look.

yeah it is. here's the source for most everything in the suite

[URL="http://www.balabit.com/downloads/files/syslog-ng/sources/stable/src/"[/URL]

---

### Post by chrisi99 on 2008-03-21
```
netstat -p
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 debian.localdomai:43771 irc2.saunalahti.fi:ircd ESTABLISHED2608/bash
tcp        0      0 debian.localdomai:43764 irc2.saunalahti.fi:ircd ESTABLISHED2608/bash
tcp        0      0 debian.localdomai:43778 irc2.saunalahti.fi:ircd ESTABLISHED2608/bash

```


this is the lsof of the only resisting "infection" still on my system:

```

# lsof -p 2608
COMMAND  PID USER   FD   TYPE DEVICE    SIZE   NODE NAME
bash    2608 root  cwd    DIR    8,1    4096 114585 /lib/security/etc
bash    2608 root  rtd    DIR    8,1    4096      2 /
bash    2608 root  txt    REG    8,1  492135 117521 /lib/security/etc/bash
bash    2608 root  mem    REG    0,0              0 [heap] (stat: No such file or directory)
bash    2608 root  mem    REG    8,1   67364 130844 /lib/tls/i686/cmov/libresolv-2.3.6.so
bash    2608 root  mem    REG    8,1   17840 130833 /lib/tls/i686/cmov/libnss_dns-2.3.6.so
bash    2608 root  mem    REG    8,1   38372 130835 /lib/tls/i686/cmov/libnss_files-2.3.6.so
bash    2608 root  mem    REG    8,1 1241392 130822 /lib/tls/i686/cmov/libc-2.3.6.so
bash    2608 root  mem    REG    8,1   88164 114551 /lib/ld-2.3.6.so
bash    2608 root    0w   REG    8,1     824 117524 /lib/security/etc/LinkEvents
bash    2608 root    1u  IPv4 180300            TCP debian.localdomain:43764->irc2.saunalahti.fi:ircd (ESTABLISHED)
bash    2608 root    2u  IPv4 180411            TCP debian.localdomain:43771->irc2.saunalahti.fi:ircd (ESTABLISHED)
bash    2608 root    3u  IPv4   8879            UDP *:32773
bash    2608 root    4u  IPv4 180480            TCP debian.localdomain:43778->irc2.saunalahti.fi:ircd (ESTABLISHED)

```

any ideas? Thanks for the help so far, I very much appreciate that! :)

---

### Post by Tx1491 on 2008-03-21
Were any parameters passed to that bash process? You can check with "ps -p 2608 -O comm="

Also, as far as I know under /lib/security there should be nothing but pam modules so I'm guessing /lib/security/etc and everything within is part of the infection.

Definitely /lib/security/etc/LinkEvents is. It's a file from energymech and in case you wasn't sure yet, that means they definitely got root since /lib/security is, by default at least, only writable by root

I might also be worth dumping tcp data so you can see what's going on and possibly track someone down. tcpdump isn't my strong point but I think it's "tcpdump -s 512 -w irc-tcp-dump dst port 6667 or 43771 or 43764 or 3778" to monitor the 4 ports being used, then "tcpdump -A -r irc-tcp-dump" to read the data once you're done dumping

Lastly, I would guess the bash process you are seeing isn't actually /bin/bash, it's /lib/security/etc/bash since the lsof output says the cwd is /lib/security/etc and the third line of lsof output isn't /bin/bash like normal

---

### Post by chrisi99 on 2008-03-21
guys, you are great! Thank you all for your help. My server is running silently for over 5 hours now, i doublechecked accounts etc and tightend the login-security by more restrictive denyhosts rules!

i hope this thread can be closed :)

until further notice - best regards
Chris

---

### Post by FakeOutdoorsman on 2008-03-21
Good news that you silenced the bot.  I wonder how they gained access initially.  This seems obvious, but once you backup, wipe, and reinstall make sure to use new account passwords.  I knew a system that was compromized and reinstalled but was using the same passwords as before.

---

