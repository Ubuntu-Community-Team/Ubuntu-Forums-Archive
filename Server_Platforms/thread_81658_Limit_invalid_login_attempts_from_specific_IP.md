---
title: "Limit invalid login attempts from specific IP?"
date: 2005-10-24
forum: Server Platforms
---

### Post by OneSeventeen on 2005-10-24
> 
Oct 24 19:52:07 hr sshd[25603]: Invalid user allen from 69.44.157.241
Oct 24 19:52:07 hr sshd[25603]: reverse mapping checking getaddrinfo for [www.bestsellingpages.com](www.bestsellingpages.com) failed - POSSIBLE BREAKIN ATTEMPT!
Oct 24 19:52:07 hr sshd[25603]: (pam_unix) check pass; user unknown
Oct 24 19:52:07 hr sshd[25603]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=69.44.157.241
Oct 24 19:52:09 hr sshd[25603]: Failed password for invalid user allen from 69.44.157.241 port 54836 ssh2
Oct 24 19:52:10 hr sshd[25605]: Invalid user allison from 69.44.157.241
Oct 24 19:52:10 hr sshd[25605]: reverse mapping checking getaddrinfo for [www.bestsellingpages.com](www.bestsellingpages.com) failed - POSSIBLE BREAKIN ATTEMPT!
Oct 24 19:52:10 hr sshd[25605]: (pam_unix) check pass; user unknown
Oct 24 19:52:10 hr sshd[25605]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=69.44.157.241
Oct 24 19:52:12 hr sshd[25605]: Failed password for invalid user allison from 69.44.157.241 port 55426 ssh2
Oct 24 19:52:16 hr sshd[25607]: Invalid user almost from 69.44.157.241
Oct 24 19:52:16 hr sshd[25607]: reverse mapping checking getaddrinfo for [www.bestsellingpages.com](www.bestsellingpages.com) failed - POSSIBLE BREAKIN ATTEMPT!
Oct 24 19:52:16 hr sshd[25607]: (pam_unix) check pass; user unknown
Oct 24 19:52:16 hr sshd[25607]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=69.44.157.241
Oct 24 19:52:19 hr sshd[25607]: Failed password for invalid user almost from 69.44.157.241 port 56658 ssh2
Oct 24 19:52:27 hr sshd[25609]: Invalid user alpha from 69.44.157.241
Oct 24 19:52:27 hr sshd[25609]: reverse mapping checking getaddrinfo for [www.bestsellingpages.com](www.bestsellingpages.com) failed - POSSIBLE BREAKIN ATTEMPT!
Oct 24 19:52:27 hr sshd[25609]: (pam_unix) check pass; user unknown
Oct 24 19:52:27 hr sshd[25609]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=69.44.157.241
Oct 24 19:52:30 hr sshd[25609]: Failed password for invalid user alpha from 69.44.157.241 port 58188 ssh2


And of course I cut off the first 5 or 10 pages for size reasons.

Is there a way to write a script that will detect login attempts, and put the valid logins in one file, and the invalid ones in another file, and if the same IP tries more than 2 different invalid logins, or unsuccessfully tries to login more than 5 times in a row, have it block that particular IP for a week or until I physically remove their IP from a block list?

Or, better yet, is it possible to limit SSH logins to specific IPs, and limit FTP logins to a specific subnet?  (using vsftpd and your standard SSH)

---

### Post by cbkm on 2005-10-25
[QUOTE=OneSeventeen]Is there a way to write a script that will detect login attempts, and put the valid logins in one file, and the invalid ones in another file, and if the same IP tries more than 2 different invalid logins, or unsuccessfully tries to login more than 5 times in a row, have it block that particular IP for a week or until I physically remove their IP from a block list?
[/QUOTE]

Yes, [fail2ban]("http://fail2ban.sourceforge.net") does something very similar.


> Or, better yet, is it possible to limit SSH logins to specific IPs, and limit FTP logins to a specific subnet?  (using vsftpd and your standard SSH)

Yes, you can use iptables to allow certain ips access to ssh(22) and ftp(21) while, by default., REJECTing/DROPping all other ips.

For example:
```

$ sudo iptables -A INPUT -i $IFACE -p tcp -s $source_ip --dport 22 -j ACCEPT
$ sudo iptables -A INPUT -i $IFACE -p tcp --dport 22 -j DROP
```
(substitute $IFACE and $source_ip as appropriate)

---

### Post by hav0x on 2005-10-31
I have this really neat sshdfilter bash script this guy i know hooked me up with.
After 3 failed logins it adds the ip for the iptables to DROP.

---

### Post by LordHunter317 on 2005-10-31
Filtering invalid logins is rather silly, typically.  Just use strong password or keypair authentication where you can and it's not an issue, and you can just ignore the logging attempts.

---

### Post by riggsd on 2005-11-01
I use [DenyHosts]("http://denyhosts.sourceforge.net/") for this. It uses /etc/hosts.deny rather than firewall rules, as I'm not sure I want any automated system mucking with my firewall. What I'd like to find is a PAM module or something that continually increases the time between login attempts so these attackers are slowed down (similar to tarpit for spammers).

I disagree with people who say to simply ignore these brute-force attacks, they obviously don't have to look after a fleet of multi-user machines. If your machine is on the wide-open internet, there is no such thing as "too secure".

---

### Post by Kaah on 2006-01-16
What repositories should i use to apt-get fail2ban?

---

### Post by LordHunter317 on 2006-01-17
[QUOTE=riggsd]I disagree with people who say to simply ignore these brute-force attacks, they obviously don't have to look after a fleet of multi-user machines.[/quote]I love people who use irrelevant personal attacks in their defense, without even consdering the problem.

Here's a list of why the brute-forces should be ignored:[list][*]The dictonaries and perturb algorithms for some of the worms are available, so you can test your passwords to 100% assurance they can't be compromised[*]Regardless, the problem space *assuming they **know the username** and that **the password is 8-characters long in a base-64 space*** is 64^8, which is a huge number.  Much too huge to ever potentially brute force.  And those two assumptions decrease the problem space by several orders of magnitude.  Assuming they don't know the username and try only 8-character names in a base-64 space, that raises the problem by itself to 64^16.  Considering from 1-8 adds a summation term from 1-n on the power.  Widening the character space to attempt raises the base by one for each character you add in.  All of these activities make the problem space much wider.

And obviously, if you can't solve 64^8, you can't solve 64^16.
[*]Setting and enforcing a password policy is absolutely trivial, technically speaking.[/list]

>  If your machine is on the wide-open internet, there is no such thing as "too secure".There is such thing as paranoia though, and these sorts of responses are such.  A simple password policy will stop such attacks cold.  The only reason to ever consider this as a technical countermeasure would be if you couldn't set a password policy.  Just about any sane password policy will stop the remote attacks cold.

---

### Post by joehill on 2006-01-24
One way to block everyone from even getting to the SSH login in the first place is to use the SSH Faker ([http://freshmeat.net/projects/ssh-faker/)](http://freshmeat.net/projects/ssh-faker/)), which allows you to add whatever machine you're on to the "hosts.allow" list by doing "telnet mymachine.myhost.net 22" then typing in a passphrase.  There is no list in "hosts.deny".  Instead, you insert a line instructing to call the ssh-faker into the "hosts.deny" file.  You'll never see a string of attempted logins again if you try this, and even if someone manages to figure out the system you're using (a worm can't do this) it means they have to figure out 2 passwords.  It may not be useful if you're a sysadmin with thousands of users who may not take the time to understand the system, but it's a very simple solution for a computer with not many users.

---

