---
title: "Help, server under attack."
date: 2009-02-03
forum: Server Platforms
---

### Post by spynappels on 2009-02-03
Hi,

 Several of my servers have been under attack over the last few days from SSH Brute Force Attacks, and I have question about an entry in one of the logs.

```
Feb  2 04:45:00 server sshd[32118]: reverse mapping checking getaddrinfo for dsl-tn-dynamic-002.254.164.122.airtelbroadband.in [122.164.254.2] failed - POSSIBLE BREAK-IN ATTEMPT!
```
Can someone explain to me what the above means?

Also, I got an email from somebody else saying my server was attacking them. I didn't think the cracker had actually got into my system, but there were some lines in the log referring to http_proxy which I didn't understand. Is it possible to make it look like an attack is coming from a different IP than it really is, or do I need to search through the logs again for a successful login that I don't recognise?

Thanks for your help.

---

### Post by linux_tech on 2009-02-03
Sometimes the error can happen if you are logging in via ssh and your hosts file is not set up for reverse dns. Try logging in by ssh and check the timestamp on the error.

---

### Post by mregister on 2009-02-03
I recommend installing fail2ban if  you have ssh open. I had a box up for 2days before I got around to installing it and the next day after installing  I had a nice sized fail2ban log.

---

### Post by tubezninja on 2009-02-03
I've seen this literally hundreds of thousands of times in my logs.  If not millions by now.

Unfortunately, this is a fact of life running a linux server.  People - or rather, bots - are actively probing IP addresses, and searching for either WIndows machines to infect with malware, or linux servers with easily guessed usernames and passwords to break into and turn into supernodes.

The barrage will continue and will be constant.  You'll see ebss and flows, and periods where activity spikes, but the activity isn't going to stop anytime soon.

When I first saw it, I freaked out too.  I've since gotten over it.  Sadly, that's just the way things are.

I would recommend the following steps:

- Use usernames and passwords that aren't easy to guess.  Usernames like "john" "kate" "payroll" "accounting" "tech" should be avoided.

- Keep your root password disabled.  The first thing most bots try is to guess the root password.

- Install a script like [DenyHosts]("http://ubuntuforums.org/showthread.php?t=450853") or [fail2ban]("http://www.ubuntux.org/preventing-brute-force-attacks-with-fail2ban-on-debian-etch").  These are scripts that will actively block IPs if they exhibit brute force activity.  You can customize how long the bans last, how long it takes to deem an IP suspicious, etc.

In the 4+ years I've run linux servers of my own, I've seen countless attempts at brute force and dictionary login attacks.  Using the above measures, not one has been successful to date.

There are other options as well, like changing the port on which SSH listens.  Security through obscurity shouldn't be the only defense though.

---

### Post by Thirtysixway on 2009-02-03
Yes use fail2ban and also try changing the port that ssh runs on.  I did this and it stopped most if not all brute force attempts.

---

### Post by glotz on 2009-02-03
[QUOTE=scaredpoet]- Install a script like DenyHosts or fail2ban[/QUOTE]

Unfortunately also the bad guys get wiser. [http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html](http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html)

It's still a good idea and will stop many script kids.

---

### Post by Dr Small on 2009-02-03
> **glotz said:**
> Unfortunately also the bad guys get wiser. [http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html](http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html)

It's still a good idea and will stop many script kids.
Woah. Now that's a story and a half.

---

### Post by HermanAB on 2009-02-03
It is easy to stop brute forcers:

Iptables nowadays has a very nice rate limit module which can prevent all kinds of abuse.

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Cheers,

Herman

---

