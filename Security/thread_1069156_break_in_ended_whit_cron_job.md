---
title: "break in ended whit cron job"
date: 2009-02-13
forum: Security
---

### Post by Geir102 on 2009-02-13
I had a break-in attempt. Where they tried to brute force ssh.  It lasted for a couple of quite a wile. Then there was a cron job and it stoppt. Can this mean they got in?

Feb 13 23:09:32 linux sshd[16426]: Failed password for root from 124.207.43.211 port 13269 ssh2
Feb 13 23:10:01 linux CRON[16428]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 13 23:10:02 linux CRON[16428]: pam_unix(cron:session): session closed for user root

---

### Post by punx45 on 2009-02-13
> **Geir102 said:**
> I had a break-in attempt. Where they tried to brute force ssh.  It lasted for a couple of quite a wile. Then there was a cron job and it stoppt. Can this mean they got in?

Feb 13 23:09:32 linux sshd[16426]: Failed password for root from 124.207.43.211 port 13269 ssh2
Feb 13 23:10:01 linux CRON[16428]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 13 23:10:02 linux CRON[16428]: pam_unix(cron:session): session closed for user root

the cron sessions should be normal.  even if you never set up a cron job yourself, many programs do, but to be on the safe side you can see what is in the root crontab.

[code] sudo crontab -l [/code}

the failed password does mean someone was trying to get in, but they did not succeed.   this is bound to happen to any computer with ssh open to the world.   you can install and configure fail2ban or denyhosts.   either of these programs monitors the auth.log and will block a string of failed attempts with iptables.

and of course, as you set up user accounts, try not to use common names and always use strong passwords, as this is the first and easiest implemented line of defense against dictionary attacks

---

### Post by bodhi.zazen on 2009-02-13
Those last two enteries look normal.

You can find many more similar enteries with

```
grep root /var/log/messages | grep "cron:session:
```More concerning :

1. Secure your ssh server (use keys, change the port, disallow root logins, use denyhosts / fail2ban / iptables )

2. look for successful log ins :

```
grep sshd /var/log/messages
```

Edit: hope I got those logs correct, :lolflag:

---

### Post by brian_p on 2009-02-13
> **Geir102 said:**
> I had a break-in attempt. Where they tried to brute force ssh.  It lasted for a couple of quite a wile. Then there was a cron job and it stoppt. Can this mean they got in?

No, they don't stand a chance of getting in if you have a strong password or are using key based authentication. Either of these is the **only assurance** of your security. Changing the port sshd runs, using iptables or programs like denyhosts can give you a warm fuzzy feeling you are combating the attack but they contribute little to protecting your network.

---

### Post by bodhi.zazen on 2009-02-13
> **brian_p said:**
> No, they don't stand a chance of getting in if you have a strong password or are using key based authentication. Either of these is the **only assurance** of your security. Changing the port sshd runs, using iptables or programs like denyhosts can give you a warm fuzzy feeling you are combating the attack but they contribute little to protecting your network.

I strongly disagree with those last few comments.

Changing the port is IMO critical. This is not security through obscurity rather it is a simple fact that there are thousands of automated scripts that hammer port 22.

Simply change to a different port and watch your logs, you will see a dramatic drop off in brute force attempts.

Second both iptables and denyhosts certainly add security, they will block brute force attempts (by blacklisting troublesome IP addresses) altogether (as will fail2ban).

Sure these attempts will not stop a determined cracker, but saying "they contribute little to protecting your network" is, IMHO a bit of a mis characterization, and is simply your opinion.

---

### Post by HermanAB on 2009-02-13
It is very easy to stop this kind of cruft with a one liner in /etc/rc.d/rc.local:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Cheers,

Herman

---

### Post by brian_p on 2009-02-14
> **bodhi.zazen said:**
> 

Sure these attempts will not stop a determined cracker, but saying "they contribute little to protecting your network" is, IMHO a bit of a mis characterization, and is simply your opinion.

The mathematics is in my court. Having taking the critical step of devising a strong password the time to crack it can be measured in billions of years. In practical terms there is complete security from the pathetic automated login attempts experienced by Geir102.

Changing port or using denyhosts reduces the annoyance factor but, as is evident, provides no significant extra security. It's akin to using a mosquito repellent after being innoculated against yellow fever.

---

### Post by Geir102 on 2009-02-14
Thanks for all the replies:) Its amassing how helpful people on this forum are:)

Only one thing when i run chrontab it's saying "no crontab for ". Why is it running then?

---

### Post by brian_p on 2009-02-14
> **Geir102 said:**
> 

Only one thing when i run chrontab it's saying "no crontab for ". Why is it running then?

From my /etc/crontab:

```
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
```

run-parts is running any scripts in /etc/cron.hourly at 17 minutes past each hour.

---

### Post by bodhi.zazen on 2009-02-14
Note: Off topic, ranting, argumentative tolling posts are going to be removed from these (security) discussions.

Please keep your comments on topic, professional, and appropriate.

---

### Post by punx45 on 2009-02-14
> **Geir102 said:**
> Thanks for all the replies:) Its amassing how helpful people on this forum are:)

Only one thing when i run chrontab it's saying "no crontab for ". Why is it running then?

crontab is your user crontab.   sudo crontab will show you roots crontab, and that is what is creating entries in the auth.log.

---

### Post by brian_p on 2009-02-14
> **bodhi.zazen said:**
> Note: Off topic, ranting, argumentative tolling posts are going to be removed from these (security) discussions.

So why then was my last but one post deleted considering it displayed none of these characteristics? Ok, I'll admit to putting forward a sound, logical argument. Is that the problem?

> Please keep your comments on topic, professional, and appropriate.

I'm not sure of the etiquette or efficacy in following up in this forum but, as with all my posts, I think I can tick all three boxes with this one.

---

