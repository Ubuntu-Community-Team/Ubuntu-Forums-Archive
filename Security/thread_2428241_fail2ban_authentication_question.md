---
title: "fail2ban authentication question"
date: 2019-10-01
forum: Security
---

### Post by Frank P on 2019-10-01
Just starting to try and understand fail2ban
If my index.html page is a php script that verifies user/password against a MySQL database do I still need an .htaccess file in the configuration directory to trigger fail2ban

---

### Post by TheFu on 2019-10-01
Need? No.

fail2ban can be told which log files to watch, using regex to match different patterns, then based on the pattern, take an action, like adding an iptables firewall rule. The action could be anything, really.  There are many existing examples of fail2ban rules and actions in /etc/fail2ban/ , but most of the time, it is worth setting up a specific setup for your specific service.

Users/passwords alone are a very poor method of authentication.  Please use something stronger.

Most of the time, I block all direct internet access and force a VPN to be used to access any of our company services, including email.  That makes lots of people unhappy, but they won't have to explain to the company owners when we get hacked because some user had a crappy password.

---

### Post by Frank P on 2019-10-01
Can you point me to someplace I can get a good explantion of what the risks are or,  if you got time I'd really like to understand the vulnerabilities.
This is a personal/hobby site.
There are no static pages except the login page which authenticates via MySQL userid/password. All response pages are built with PHP from data in a MySQL database. All response pages also require a MySQL userid/password to proceed.
All user input - userid/passwords are PHP sanitized 
Only ports 80 & 443 would be open. 
Would there still be the possibility of intrusion
Thanks for your time
Frank

---

### Post by TheFu on 2019-10-01
> **Frank P said:**
> Can you point me to someplace I can get a good explantion of what the risks are or,  if you got time I'd really like to understand the vulnerabilities.
This is a personal/hobby site.
There are no static pages except the login page which authenticates via MySQL userid/password. All response pages are built with PHP from data in a MySQL database. All response pages also require a MySQL userid/password to proceed.
All user input - userid/passwords are PHP sanitized 
Only ports 80 & 443 would be open. 
Would there still be the possibility of intrusion
Thanks for your time
Frank

Hobby or not. Attackers don't care.  A Linux system on the internet can be used for all sorts of things, C&C, phishing, spamming emails, virtual domains. [https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/](https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/) has a nice graphic for all the ways a hacked PC can be used. 

If you have a website on the internet, you are at risk for being hacked. If the code isn't 100% correct [https://www.sans.org/top25-software-errors/](https://www.sans.org/top25-software-errors/) is a short list. It is likely possible to open a reverse ssh connection to anywhere which would allow the attacker back in.  Or they can use bash or nc to do it unencrypted, unless the firewall prevents output connections and not just inbound connections  Setting up a task to do that once every 7:38 h:mm for 7 minutes is easy.  

Wouldn't hurt to join your local OWASP group to keep security on your mind daily, as you build application and tools. Also, seeing how other people tackle their issues is helpful.

---

### Post by Frank P on 2019-10-02
Okay, thanks.
I'll do some further research. I'm pretty confident that my php code is safe against all the common attacks, my server is completely up to date, and with no incoming SSH or FTP and fail2ban installed it should eliminate brute force attacks.  Now I have to find out what to be aware of
Frank

---

### Post by TheFu on 2019-10-02
> **Frank P said:**
> Okay, thanks.
I'll do some further research. I'm pretty confident that my php code is safe against all the common attacks, my server is completely up to date, and with no incoming SSH or FTP and fail2ban installed it should eliminate brute force attacks.  Now I have to find out what to be aware of
Frank

There are always bugs in code.  Always.  I wouldn't be nearly so confident.  

I've been writing code since the 1980s, sometimes in extremely high quality environments where code quality mattered more than schedule.  We found bugs in our formally reviewed code at all stages of development.   In 1994, we had a belief that no more critical errors existed in the software because none had be found in over a year.  Jump forward to 2010 ... and looking back at the critical errors discovered showed over 100 critical errors had been found that were in the 1994 code.  This was at a CMMI-5 environment. [https://cmmiinstitute.com/learning/appraisals/levels](https://cmmiinstitute.com/learning/appraisals/levels) Every bug was thoroughly researched by each different team, some in different companies, reporting up to different executive sponsors at the client organization.   We had different checklist for all the different checklists to be included for each type of review. No less than 10 people would review each code modification.

In my 5 yrs working in that environment, I caused only 1 critical error that got beyond our internal review processes.  That bug made it all the way to 7th-level testing before being caught.  I had specifically brought the single line of code with the bug to the attention of at least 3 review teams because I didn't understand how it interfaced with some hardware over the different channels. Even doing that, didn't help.  

All code has bugs. That's what I've learned.

---

### Post by Frank P on 2019-10-03
Didn't mean to sound over confident . I've been writing custom software since dBase III+ days. I know all about bugs :-) But this is simple CRUD stuff and I'm the only user. Maybe I should reword my question and ask it again.

What I'd like to find out is how sites are hacked from the outside. [LEFT][COLOR=#222222][FONT=Verdana]I know if any pc behind the server is compromised then everything can be compromised.
If I 
  keep server fully patched
  block all incoming ports except 80
  install fail2ban
  apply all PHP techniques to sanitize userid/password
  authenticate via MySQL user/password
  only allow one user (me) to login

What else should I reasonably do?

Should I repost as a new question or just try it :-)

Thanks
[/FONT][/COLOR][/LEFT]

---

### Post by TheFu on 2019-10-03
There are too many different ways that sites are hacked to list them all.  Any list would miss many, because the attackers are always changing tactics.  

HTTP connected to any dynamic webapp scares me, even my own webapps.  I use ruby and perl.  HTTPS would be better, especially if passwords must be used. Passwords alone are a huge problem.

I'd rather see ssh with ssh-keys enabled than HTTP/HTTPS with passwords open to the internet. ssh shouldn't be using passwords over the internet.

OWASP has some lists and techniques for the different languages commonly used in webapps.  For a long time, the OWASP checklist for php began with harsh warnings about the php language.  [https://www.owasp.org/index.php/Category:PHP](https://www.owasp.org/index.php/Category:PHP)  Web searches for "php security" returns thousands of lists, pages, flaws, and techniques.  Forewarned is forearmed. 

I try to only allow requests from the outside world that should be allowed.  Anything not in my whitelist of requests is logged and dropped. That makes setting up fail2ban regex for each possible.  It became clear that lots and lots of universities in China were attacking, to rather than play whack-a-mole, I just started blocking China subnets using ipset. The subnets change all the time, so every few weeks, I'll add more to the ipset block rule of my public webapps.

Only you can decide what is reasonable.  I'm not allowed to let php webapps be available over the internet directly. That was the decision from our CSO. We were already providing VPN for our people, so they have to use that to access all internal-only webapps now.

There are some really skilled php devs here. If you start a new thread about *php webapp security*, might put that in the title to get their attention.

---

