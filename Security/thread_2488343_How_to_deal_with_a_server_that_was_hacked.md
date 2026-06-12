---
title: "How to deal with a server that was hacked?"
date: 2023-07-03
forum: Security
---

### Post by 4-null-nan on 2023-07-03
My server was hacked and locked me out.  I had to read the hard drive to get some data and log files.  The data appears to be intact.  Not so much sensitive data, but I really don't like getting hacked, and tried very hard to keep the system up to date, and blocking bad IPs, ranges of IPs, connections that are  clearly bad ...

Now, I got the log files and the hard drive.  I know a good hacker would cover their track, but still, I need help with finding out what was going on as much as I can, in order to prevent future hacking, and to learn. 

Any advise is greatly appreciated.

---

### Post by ixeous on 2023-07-03
Nothing too specific here, but...

1.  Too late for this one, but having a remote syslog server where everything is sent is helpful.  Hopefully if anything happens, bad guy can't destroy those records.  Anything local is now suspect.
2.  Check auth.log
3.  lastlog
4.  Focus on services that were open.  SSH, HTTP, others.  Look for those things in the logs.
5.  If you log your firewall, those entries may help narrow it down.

For basic level of prevention
1.  Follow hardening guides for any services that are open
2.  Use MFA where possible.  libpam-google-authenticator for SSH.
3.  Use firewall to limit outbound traffic.  This can be difficult on a server, but if you limit where your system can to out to on ports 80 and 443, then your system can't reach out to c&c servers or to download various malicious payloads.  This limit can make updates a bit more painful too though so be careful with it.
4.  Automatically update if possible.
5.  Run tools such as AIDE.
6.  Now that I think if it as I type this, [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

### Post by DuckHook on 2023-07-03
Are you sure you were actually hacked?

Not to be unduly sceptical, but we've had a number of such claims on these forums over the years and often they turn out to be due to misconfigurations, bad updates, HW failures or even stray cosmic rays (these last will easily flip some crucial bits in your RAM or spread havoc on your HDD).

It is important to rule out other more likely causes before drawing the conclusion that you've been hacked. Also, modern hacking follows certain evidentiary patterns. If yours doesn't follow any such patterns, then the cause is likely something else.

[LIST=1]
[*]Has your HDD been encrypted?
[*]Did you get a ransom screen?
[*]What was your server used for? What ports were exposed to the outside Internet?
[*]Was the server still operational after you were locked out?
[*]If so, what was its activity level? What did it continue to do?
[*]Have you engaged security professionals? If not, why not? If so, what did they tell you?
[/LIST]

---

### Post by 4-null-nan on 2023-07-03
It is highly likely that it's hacked.  Someone added so many rules to the iptables that I don't recognize them at all.
I was able to login and checked it out.  Then I think they noticed it, and blocked my IP.

While I was there, I captured some of the iptables rules.  I am still debating whether to post it here, out of concern if the hacker visits this page.
Please see below for my answer inline.

[QUOTE=DuckHook;14149155]Are you sure you were actually hacked?

Not to be unduly sceptical, but we've had a number of such claims on these forums over the years and often they turn out to be due to misconfigurations, bad updates, HW failures or even stray cosmic rays (these last will easily flip some crucial bits in your RAM or spread havoc on your HDD).

It is important to rule out other more likely causes before drawing the conclusion that you've been hacked. Also, modern hacking follows certain evidentiary patterns. If yours doesn't follow any such patterns, then the cause is likely something else.

[LIST=1]
[*]Has your HDD been encrypted?
No 
[*]Did you get a ransom screen?
No, I don't think there is much value for them to get any ransom, or they tried to use it for something.  I do not know the extend how much they were able to access the system. 
[*]What was your server used for? What ports were exposed to the outside Internet? Port 80 and SSH (22).  I don't recall if port 433 was opened or not.  Port 22 was only accessible using my IP (unless they tricked it) and to login, SSH is used with a security key file. The server is used for a few Web applications that I developed for my own uses.
[*] Was the server still operational after you were locked out? I didn't check
[*]If so, what was its activity level? What did it continue to do? I wasn't sure 
[*]Have you engaged security professionals? If not, why not? If so, what did they tell you?
With the app and the data I had, there was not much value for hiring someone doing it
[/LIST]

---

### Post by DuckHook on 2023-07-03
You've clearly assembled enough data to validate your hacking concern and the way that events played out also reinforces your conclusion.

I doubt that pasting the iptable rules will do much harm or much good either way. Some of the network gurus on this forum may be able to give you some insights, but that would only serve the purpose of assuaging your curiosity. When it comes to solving your problem, I don't think that such data would add anything.

The following are my thoughts:

You've done everything properly on SSH, but I will mention only three additional points of attention:

[LIST=1]
[*]Even though you have instigated keys, make sure that you are using a strong modern protocol (the old ones are weak) and that you've turned off passwords altogether. Some people forget to turn off passwords even though they have turned on keys. Under no circumstances permit root login.
[*]I always set SSH to a high port. The default port 22 is spammed by script kiddies looking for easy entries into misconfigured accounts. Properly configured SSH won't be vulnerable, but the sheer quantity of tries will spam your logs and make diagnosis impossible.
[*]Install, configure and use fail2ban. It is your single best defence against brute force attacks.
[/LIST]

Your web functions are a whole different can of worms. Web sites are probably the single weakest vulnerability in servers. They require a lot of expertise to be designed, written and implemented securely: skills that are far beyond my pay grade. I would guess that your web structure was where you were hacked, but that is nothing more than conjecture.

I am also concerned by your mention of "web apps". A static web site is relatively easy to secure, but once you allow scripting and interactivity, then the vulnerabilities mount exponentially. When you implement actual "web apps", you open yourself up to the scumbags and really need to be a black belt in self defence. I have no idea what level of security expertise you have, but you may wish to rethink your strategy.

If these web apps are mission critical (you must have them) and only you or a restricted cohort of people use them, then you might consider isolating them within a private intranet that can only be accessed through a VPN. Once they cease to be public facing, they cease to be targeted by bad guys. I've recently switched from OpenVPN to Wireguard which has been a very nice surprise, as Wireguard is much easier to implement, more reliable and slightly faster.

If these apps are both mission critical and must be public facing, then the only advice I can give is to have them professionally vetted and professionally pen tested. I know of no other way to prevent a repeat of what you have been subjected to.

I assume that the server has been taken offline and that you are now dissecting the HDD using inspection tools. I'm not sure how fruitful this will be. It may not be worth your time unless you are interested in self education and enhancing your security chops. If you just want to get back on track with your life, then the VPN solution would be my most important piece of advice.

---

