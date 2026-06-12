---
title: "Input for securing my server- am I missing anything?"
date: 2008-07-24
forum: Security
---

### Post by sp0nge on 2008-07-24
Hello all!

I am almost ready to take my LAMP server live! I want to ensure I have everything as secure as I possibly can before hand, so here is my list (please let me know if I've overlooked anything):

IPtables: I have configured this for ssh and http to be accessed from outside. Do I need to allow another port for sFTP or can it share a port with ssh? 

rkhunter, chkrootkit and rkdet: Are they necessary? From all I hear about the difficulty of these things in the wild makes me wonder how effective they are. Input or suggestions? 

failban: I'm considering using this, although I've installed postfix to set up a mail server at some point, and from what I've heard the two don't mesh well. 

System Screening: I've been reading a lot about tiger. This seems to me a worth-while package. I'd like to hear from people who've used it with any feedback. 

Log Watch: I don't know which logs to really keep an eye on. Is this worth the install? I don't think there can be a replacement for looking the logs over manually. Is this a good choice or no? 

After that, I think I got most of my bases covered. It's almost time to toss up some simple pages and start looking for holes.

---

### Post by dfarrell07 on 2012-02-15
SFTP uses port 22, so you don't need to open another one for it if SSH is open. 

Consider changing the default ports you run services out of. Automated scanners could still pick this up, but many attackers are looking for low hanging fruits and want to scan quickly, so they don't cover the full port range, only the most used ones (--top-ports with nmap, for example).

---

### Post by unspawn on 2012-02-16
> **sp0nge said:**
> I am almost ready to take my LAMP server live! I want to ensure I have everything as secure as I possibly can before hand, so here is my list (please let me know if I've overlooked anything):
You're bound to get a lot of advice. My first advice to you would be to make a checklist of things to do. That way you don't lose oversight while you prioritize and ponder details. 

The first thing I would suggest is to get acquainted with your distributions documentation. (And if this is you first publicly accessible server I strongly suggest you get acquainted with server administration tasks before doing anything else or your may find your learning curve may become really steep in times of trouble.) Reading your distributions documentation will provide you with the basics of securing and hardening your machine. Next to that the "Securing Debian" manual is one of the oldest almost all-encompassing documents you could glean nfo from.

Speaking from experience a lot of security incidents occur because of sloppy admin work that can be easily avoided: not cleaning up installation files, not restricting access to web-based administration panels, lax access permissions, running default daemon configurations, running home-brewn code w/o any checks or ignoring to treat user input as untrusted, running stale versions of any software in the web stack and no or insufficient monitoring.
In short: 0) know what you run and ensure that what you run is up to date and 1) what you don't log you don't know.

On top of your distributions documentation SANS (generic security and hardening docs), CIS (security benchmarks) and OWASP (web stack) documentation may help you fine-tune hardening further. A lot of people will offer advice but fail to point out that *any change you make should be tested for*. 


> **sp0nge said:**
> rkhunter, chkrootkit and rkdet: Are they necessary? From all I hear about the difficulty of these things in the wild makes me wonder how effective they are. Input or suggestions?
The first thing you should realize is these days it's more common to find vulnerabilities in anything the web stack offers to be exploited (think web-based management panel, forum, shopping cart, statistics package, plugin or photo gallery vulnerabilities) rather than seeing traditional rootkits being deployed. Next to that Chkrootkit and Rootkit Hunter are passive, post-incident auditing tools. They may (or may not) help you find remnants of malicious activity. 
In short: system hardening, logging and alerting are of primary importance.


> **sp0nge said:**
> failban: I'm considering using this, although I've installed postfix to set up a mail server at some point, and from what I've heard the two don't mesh well. 
Fail2ban blocks connections through the firewall (don't use /etc/hosts.deny) based on regexes applied to logs. If it is too aggressive regexes may be tuned.


> **sp0nge said:**
> System Screening: I've been reading a lot about tiger. This seems to me a worth-while package. I'd like to hear from people who've used it with any feedback. 
I often deploy GNU/Tiger as a first host-based assessment tool. It provides me with a list of things to address, investigate and correct. Note though it's host-based so it should be accompanied with a remote scan using something like OpenVAS (or OVAL or Nessus but nmap definitely is *not* sufficient) to validate hardening.


> **sp0nge said:**
> Log Watch: I don't know which logs to really keep an eye on. Is this worth the install? I don't think there can be a replacement for looking the logs over manually. Is this a good choice or no? 
While you're right there is no substitute fo reading logs Logwatch provides you with an efficient list of things to investigate. Definitely a good tool to have *as long as somebody actually reads reports*.

HTH

---

### Post by HermanAB on 2012-02-18
You missed the very first step:
Ensure that you have decent (>12 chars) passwords for all user accounts.

---

