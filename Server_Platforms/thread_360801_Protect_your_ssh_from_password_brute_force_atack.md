---
title: "Protect your ssh from password brute force atack"
date: 2007-02-13
forum: Server Platforms
---

### Post by Rommidze on 2007-02-13
Greetings!

I just finished ubuntizing the pam-abl security module. This plugin can protect [ssh server from password brute force atack]("http://tech.tolero.org/blog/en/linux/ssh-password-brute-force-protection"). Installation is very easy with my package. Initial configuration is fully automated by a package, and makes machine secured right after package installation.

Any comments and opinions about the package are awaited!

---

### Post by Azakus on 2007-02-13
Cool. Thanks for deb. That will make me much less concerned about ssh'ing to my pc.

---

### Post by nigelenki on 2007-02-14
I always figured the best way to do it was to give network authentication, sudo, and su a limiting module; and make only login and gdm capable of ignoring this.  Let's call this 'pam-ratelimit'.  Basically:

[LIST]
[*]Console log-in logs in as normal
[*]GDM logs in as normal
[*]All other log-in apps (su, sudo, ssh, etc) log in using pam-ratelimit
[*]Every time you log in, 'pam-ratelimit' immediately notes the time
[*]Before authenticating, 'pam-ratelimit' checks to see if in the last 1 second interval, N failed log-in attempts for the given user name have occurred (where N=3, N=5, whatever)
[*]If the above check returns true (i.e. there were 3 failed log-ins in the past second?), 'pam-ratelimit' logs a failure and denies access, without checking your password
[*]If in any case the user doesn't exist, 'pam-ratelimit' does nothing; pam just fails anyway
[/LIST]

Note that failed log-ins on the console don't count; 'pam-ratelimit' would log fails only on logins it was protecting, such as ssh and sudo.  It would also only make these log-ins fail; if your 'root' is being brute forced, you will have to log in directly via console.

This method would provide blanket protection against distributed brute force attacks; if an attacker controls 1 million nodes, he can perform 3 attacks per second if N=3.  If you do it by IP address, the attacker can perform N*num_nodes attacks per second, so 3 million for N=3.  Also note that if the attacker is going faster than the rate limit (i.e. 4 attacks per second), all his attempts will continue to fail; a failure due to too many recent failures still counts as a failure, and until you actually stop for a second you will just perpetuate the non-login time.

DoS attacks on this method are possible.  I could launch a distributed attack to hammer ssh and keep you from logging in remotely; of course, an adaptive firewall would help squelch this (pam-ratelimit getting too many failures from the same IPs, decides that anyone who fails on the offending log-in name due to too many attacks is bad, notifies a daemon which sets iptables or other firewall rule for 1 hour).  The module could also recognize IPs with repeatedly good log-ins and be kind enough to reduce the firewall period to 10 minutes for those (logging this, of course, as a form of intrusion detection).

---

### Post by elst on 2007-02-14
DenyHosts also seems to address this issue, although I haven't used it yet. I think that it's synchronization feature is interesting - this enables servers to share blacklists, so that an identified attacker will be blocked by all hosts.

---

### Post by gaten on 2007-02-14
You could also disable password authentication and use public key. More secure in that brute force attacks are useless (unless they steal your key anyway, but then they are guessing THAT password) and it requires two-factor authentication (they need the key to even get access, AND the key is password protected). 

A non-ubuntu guide might help (this applies):
[http://www.astro.caltech.edu/~mbonati/WIRC/manual/DATARED/setting_up_no-password_ssh.html](http://www.astro.caltech.edu/~mbonati/WIRC/manual/DATARED/setting_up_no-password_ssh.html)

Short but suffice. 

Please note, I'm not knocking the threat starters PAM solution, simply offering another one that can be used in many cases (but not all).

---

### Post by sco01 on 2007-02-15
I tried to find a soluiton to this myself a while ago by googling around. I use this in my iptables config:

```

#drop ssh-login trials if more than three in one minute
 iptables -I INPUT -p tcp --dport 2201 -i eth0 -m state --state NEW -m recent  --set
 iptables -I INPUT -p tcp --dport 2201 -i eth0 -m state --state NEW -m recent  --update -seconds 60 --hitcount 3 -j DROP

```

Are there any disadvantages to this approach (other than the obvious less secure pw-login) compared to the other methods suggested here?


//SCO

---

### Post by Rommidze on 2007-02-15
> **nigelenki said:**
> I always figured the best way to do it was to give network authentication, sudo, and su a limiting module; and make only login and gdm capable of ignoring this.  Let's call this 'pam-ratelimit'.

Good aproach!
Which things do you use exactly?
Pam module, script, log analyser or anything else? Share the details please. Maybe it is also can be packaged and automated.

---
[SIZE="1"]my homble [vista linux comparison]("http://tech.tolero.org/blog/en/linux/bbc-os-comparison-vista-linux-os-x").[/SIZE]

---

### Post by Rommidze on 2007-02-16
> **gaten said:**
> You could also disable password authentication and use public key. More secure in that brute force attacks are useless (unless they steal your key anyway, but then they are guessing THAT password) and it requires two-factor authentication (they need the key to even get access, AND the key is password protected). 

Keys are very good solution. Except the reqirenments to carry a key always on a flash, and long speech with clients, who also using the same server. Password authentification still much more easy understandable to users than the keys :-(

I'am also using the keys where it's possible, and think it is the best security variant. Otherways I'm using [libpam-abl]("http://tech.tolero.org/blog/en/linux/ssh-password-brute-force-protection").

______________________________
My technical ideas on [how to protect the forum from spam]("http://tech.tolero.org/blog/en/web/blogs-and-forums-spam-bots-protection") without users disturbing.

---

### Post by Ramses de Norre on 2007-02-16
> **elst said:**
> DenyHosts also seems to address this issue, although I haven't used it yet. I think that it's synchronization feature is interesting - this enables servers to share blacklists, so that an identified attacker will be blocked by all hosts.

I use it and it works perfect (I can tell, I locked myself out once by giving three times a typo in my password and couldn't possibly manage to get in again...)

---

### Post by Rommidze on 2007-02-16
> **Ramses de Norre said:**
> I use it and it works perfect (I can tell, I locked myself out once by giving three times a typo in my password and couldn't possibly manage to get in again...)

That is a significant imperfection. If I understand *denyhost* principle, it will ban failed host on any machine it is installed on at once.

---

### Post by Rommidze on 2007-02-17
> **sco01 said:**
> I tried to find a soluiton to this myself a while ago by googling around. I use this in my iptables config:

```

#drop ssh-login trials if more than three in one minute
 iptables -I INPUT -p tcp --dport 2201 -i eth0 -m state --state NEW -m recent  --set
 iptables -I INPUT -p tcp --dport 2201 -i eth0 -m state --state NEW -m recent  --update -seconds 60 --hitcount 3 -j DROP

```

Are there any disadvantages to this approach (other than the obvious less secure pw-login) compared to the other methods suggested here?

Only lack of protection from a distributed attack from a various IP addreses.

---

### Post by Ramses de Norre on 2007-02-20
> **Rommidze said:**
> That is a significant imperfection. If I understand *denyhost* principle, it will ban failed host on any machine it is installed on at once.

It will add hosts that try to login to hosts.deny according to the rules in the config file, I had mine set to do so whenever someone gave in a wrong password or username three times.
It adds these hosts only to the hosts.deny file of the machine they're trying to log on to, as far as I know.

---

### Post by MJN on 2007-02-20
> **Ramses de Norre said:**
> It adds these hosts only to the hosts.deny file of the machine they're trying to log on to, as far as I know.
 
Although if you've got synchronisation turned on it will also provide the offending IP to the central server for consideration for 'global banning'. Of course, this won't happen on the strength of just your submission alone otherwise that'd be a nice little DOS enabler...
 
Mathew

---

### Post by jetole on 2008-02-26
> **sco01 said:**
> I tried to find a soluiton to this myself a while ago by googling around. I use this in my iptables config:

```

#drop ssh-login trials if more than three in one minute
 iptables -I INPUT -p tcp --dport 2201 -i eth0 -m state --state NEW -m recent  --set
 iptables -I INPUT -p tcp --dport 2201 -i eth0 -m state --state NEW -m recent  --update -seconds 60 --hitcount 3 -j DROP

```

Are there any disadvantages to this approach (other than the obvious less secure pw-login) compared to the other methods suggested here?


//SCO
 
I am actually familier with this method and have used it in the past before I switched to all keys. There is a minor concern with with it IMHO other then what was mentioned about multihosts distributed attack. My concern with it, and the whole reason I am looking at PAM today is because, by default on most systems, multiple login attempts are allowed in one TCP session. This means they are getting more then their 3 tries. 

The reason I found this room today is because I would like to know how to limit SSH to allow one login try for each connection attempt and AFAIK this MAY be able to do be done through PAM (and not directly through sshd) but I am not sure how. 

This is not for my own personal system since I only use keys but for an affiliate of mine that requires passwords. If you have the option to only use keys then do so as it vastly increases your level of security. 

To analyze this fairly, a password can contain 94 characters I believe while examining my own us pc105 keyboard. Now if I have a 32 character password then I have a field of 92^32 or 6.937619471e+62 possible passwords that can be created and if I brute force the last one then I that means I will have to try 6.937619471e+62 to get access.

Now if I am trying to brute force a 2048 bit RSA key then that means I have a field of 2^2048 or 3.231700607e+616 possible passwords to try to gain access. dividing 3.231700607e+616 by 6.937619471e+62 = 4.658226962e+553 which means a 2048 bit RSA key is 4.658226962e+553 times as complex as a random password of 32 chars containing 94 characters. 

Now let's examine the real world. Where I work, I see users using between 5 and 8 alnum (letters + numbers alone) when creating passwords. So if I look at the max of 8 chars to the 36 (all lower case characters + numbers) then that only gives me 324518553658426726783156020576256 possible passwords. Now if I am trying passwords between 5 and 8 chars ((5^36)+(6^36)+(7^36)+(8^36)) then that gives me 327180613481000099157333022547538 possible password combinations. A 4096 bit key on the other hand gives me 1.044388881e+1233 possible combinations which is 3.218271712e+1200 times as complex as the 8 char lower alnum and 3.192086688e+1200 times as complex as the 5 - 8 char alnum.

Well that about sums it up. If you still want to use passwords then all your base r belong to us :P

---

