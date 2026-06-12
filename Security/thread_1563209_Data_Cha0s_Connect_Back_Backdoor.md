---
title: "Data Cha0s Connect Back Backdoor"
date: 2010-08-28
forum: Security
---

### Post by CodPair on 2010-08-28
Has anyone encountered this particular backdoor before? I'm not posting the script for obvious reasons.

I believe that the attacker somehow got in through the ssh daemon(OpenSSH 5.3p1) on June 12. From here, a user account named "crond" was created(can anyone confirm weather this is normal?) and according to the log, this account was accessed several times between Jun 12 and Jun 18 from the same ip address.

Also on Jun 12, the MOTD on the ssh server was messed up and remained that way until it was reinstalled. The default ssh client(OpenSSH 5.3p1) was made completely non-functional.

I became alerted to the problem when my ISP advised me to run a virus scan on the machines on my network. Not knowing of any linux based anti-virus software, I decided to check for suspicious files on my hard drive. I found one, in the /tmp directory was a subdirectory called ".popscan". Inside was a script and a list of about 40 very default sounding usernames and passwords. 

There was also a file called "back.txt" in the root of my filesystem. Which is a pearl script that aparently spawns a shell.

At this point I disconnected the server from the internet and mirrored the drive. I found a suspicious home directory for "crond"

Does anyone know where I should go from here? I'm hesitating on setting up the server again for fear that it might just get rooted again. I would also like to find out how he got in so it can be prevented for other people aswell.

---

### Post by wacky_sung on 2010-08-28
Probably your SSH server got compromised using password based login method.

Check this out on the sticky thread in regard to configure SSH server.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by cariboo on 2010-08-28
If you still have /var/log/auth* for that date, you can check the log to see if it tells you anything. My server only keeps the auth logs for a month.

The only course of action you should take, is to do a new install, hopefully you've got your data backed-up, so that it can be reinstalled. 

Then use tcp-wrappers(xinetd) to control access.

---

### Post by BkkBonanza on 2010-08-28
It does sound like someone got in. Probably via a weak password. And they sure weren't subtle about it. A skilled hacker would have installed a rootkit and not left files laying around for you to see, and fixed the logs to remove his access trail. You would have a hard time knowing he got in. 

So this was likely some amateur. Back up needed data, re-install, choose better paswords or if using any remote access then use keys and disable ssh passwords.

---

### Post by CodPair on 2010-08-29
My auth.log goes back to Jul 10th(note, In my original post, I accidentally put Jun. All events happened in July).

I grepped it for "Accepted" and found maybe 100-120 logins to "crond" during that time period(Jul 12-Aug 6). The ip addresses are mostly from AOL Germany(Dial Up) and Romania Data Systems.

I found no unauthorized access on any other user accounts and "crond" was not a user account that I started with. User accounts tester, logic, and rootlogin with UID 0.

Rootlogin was used 4 times.

Whats weird to me is that there are only a handful of IP addresses, I don't think the hacker even used a proxy.

As for my server: no data loss, just a pain to get set back up.

---

### Post by CodPair on 2010-08-29
By the way, Is it normal to constantly have someone trying to hack into you? Because my auth.log has about 7 megabytes of failed password attempts for the past month...

---

### Post by BkkBonanza on 2010-08-29
Yes, it's common to get hit by attempts. But there are various things you can do to cut that down a lot. You see attempts from a few IPs because likely this hacker was on a regular ISP dynamic connection, and they tend to change between a limited number of IPs. As mentioned, amateur. AOL? Ha.

So in future to prevent gaining access (because he will come back!):

1. Strong password or even better use key auth. There are guides around on how to set that up. It's very easy and way more secure. Then turn off password access.

2. Change ssh listening port to some other high number. This is set in /etc/sshd_config. This cuts out most port scans as they tend to always scan port 22. This isn't really more secure but most hackers will pass you by. Before changing be sure any firewall you have opens the new port.

3. Install software to ban an IP that makes too many attempts to login. Someone is bound to post a suggestion within seconds (they always do), but I don't recall the name off hand as I haven't done that.

Edit: oh ya, Fail2Ban - that's it.

---

