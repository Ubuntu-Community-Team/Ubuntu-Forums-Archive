---
title: "Traffic From China"
date: 2011-07-11
forum: Server Platforms
---

### Post by elroyinc on 2011-07-11
I am running a small web server out of my house (ubuntu server 10.04), for personal use  only.  No domain name, just an IP address, And I seem to be getting a  lot of traffic from China and a "unresolved/unknown" area.  I was  wondering if I should be worried about this?  Someone told me today that  I shouldn't worry to much about China, but if I start seeing traffic  from Russia and eastern Europe then I should worry (I don't know how  valid that information is).  I went looking through my logs yesterday  and didn't see anything that struck me as odd, however I am just a  novice as best.  I followed "[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)" when building my server, I don't know if that would help at all to see what I have running here.  If you look at this page "[http://70.126.188.158/webalizer/](http://70.126.188.158/webalizer/)" you will see the traffic that I am talking about.

Any help would be much appreciated.  Thanks in advance.

---

### Post by tgalati4 on 2011-07-11
sudo apt-get install fail2ban
man fail2ban

After a few days, check your logs:

cat /var/log/fail2ban.log

---

### Post by elroyinc on 2011-07-11
root@server1:/home/administrator# cat /var/log/fail2ban.log
2011-07-10 06:25:06,915 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.4-SVN
2011-07-10 06:25:10,026 fail2ban.filter : INFO   Log rotation detected for /var/log/auth.log
2011-07-10 06:26:02,081 fail2ban.filter : INFO   Log rotation detected for /var/log/auth.log
2011-07-11 08:07:39,352 fail2ban.actions: WARNING [ssh] Ban 93.186.196.77
2011-07-11 08:07:39,395 fail2ban.actions.action: ERROR  iptables -n -L INPUT | grep -q fail2ban-ssh returned 100
2011-07-11 08:07:39,395 fail2ban.actions.action: ERROR  Invariant check failed. Trying to restore a sane environment
2011-07-11 08:17:40,144 fail2ban.actions: WARNING [ssh] Unban 93.186.196.77
2011-07-11 12:39:28,510 fail2ban.actions: WARNING [ssh] Ban 61.130.156.146
2011-07-11 12:49:29,193 fail2ban.actions: WARNING [ssh] Unban 61.130.156.146


I already had fail2ban installed so this was my result.  Forgive me but I'm not 100% sure what this all means, and I'm not 100% sure what fail2ban is/dose.

---

### Post by arrrghhh on 2011-07-11
It basically detects brute-force attacks on SSH and blocks the IP.  Did you read the manpage as he suggested...?

---

### Post by elroyinc on 2011-07-11
"Did you read the manpage as he suggested...?"
do you mean where it says "man fail2ban"? 

"sudo apt-get install fail2ban
[SIZE=3][COLOR=Red]man fail2ban[/COLOR][/SIZE]
After a few days, check your logs:
cat /var/log/fail2ban.log"

If so, I get this in return...

root@server1:/var/log# man fail2ban
No manual entry for fail2ban

I did however read up on the wiki page about fail to ban.  If I am understanding correctly, is it "baning" the IP address which is "attacking", and then a short time later "unbanning" that IP address?

---

### Post by Dangertux on 2011-07-11
> **elroyinc said:**
> "Did you read the manpage as he suggested...?"
do you mean where it says "man fail2ban"? 

"sudo apt-get install fail2ban
[SIZE=3][COLOR=Red]man fail2ban[/COLOR][/SIZE]
After a few days, check your logs:
cat /var/log/fail2ban.log"

If so, I get this in return...

root@server1:/var/log# man fail2ban
No manual entry for fail2ban

I did however read up on the wiki page about fail to ban.  If I am understanding correctly, is it "baning" the IP address which is "attacking", and then a short time later "unbanning" that IP address?

Long story short you are correct. If it detects a series of failed authentications to ssh it will ban the IP address , it does this only temporarily (which will stop a brute force attack).

As far as traffic from China, this is pretty normal, as well as Eastern Europe.

---

### Post by msandoy on 2011-07-12
Actually regarding the origin of the attacks, I kept track of the offending IP addresses attacking my server for a while, the attacks comes from 3 different regions, Far east, China, Korea, Taiwan and Thailand. Eastern europe, with most of the earlier russian states. Then there is one country that stands for the same amount of attacks as the whole far east, and that is USA. Just be aware of that even if the attack usually comes from already comromized servers. The offender might be on the complete other side of the world.

---

