---
title: "Guide to secure LAMP server"
date: 2016-10-03
forum: Server Platforms
---

### Post by fernandoch on 2016-10-03
Hello,

Any guide to secure a LAMP server?

Thank you

---

### Post by Vegan on 2016-10-03
1) make sure all management accounts are using 128-bit or better passwords
2) use a firewall if you are hinked up over hanging a server over the internet

---

### Post by TheFu on 2016-10-03
Every server is a little different. Security for all of them is the same, the OS doesn't matter.
Depending on your level of expertise, the answers for each of these things will be different. 

* remove any unused services.
* don't leave development tools on a production system.
* stay patched. There are thousands of unknown issues on every OS. Fortunately, most attackers use known attacks.
* don't allow required open ports to be accessed by anyone who doesn't need that access.
* use multiple methods to secure each open port. Firewalls, authentication, key-based auth, and 2FA, encryption, you get the idea.
* use proper security and proper encryption for the likely attack vectors. What those are depends on the content and tools used on the website.
* run the minimal service needed to accomplish the job. Avoid "kitchen sink" solutions.
* don't use passwords as a security technique. Passwords are for use the 1st time, then keys should be used and password access disabled.
* lock down the file permissions to provide just-enough permissions required for the program to do the task. No more.
* consider running each service inside a jail/container, especially high-risk services like web, email, and DNS.
* do not run any public-facing services as root.
* do not use a normal userid to run services. Use a specific userid for a specific service.
* kernel parameters to protect against attacks like the syn/ack style.
* never run plain FTP. Use sftp instead.

So ... for each service you run, run through that list and lock each down each with multiple layers of protection.

Then use the available tools to check that what you've done is working. Save those scripts so that you can re-run them after every patch gets applied. Consistency.

And learn how to hack your own site.  Not all attacks come straight on. Crackers are a craft bunch and they will avoid the front entrance with the steel door when a small hacksaw through the sidewall will work easier and still get inside.  If you have a banking website, the protections need to be much greater than for a cat-picture website.

Plus I'm a real believer in 1 service per system, so the idea of having the DB running on the same machine as the website seems just wrong. I put webservers behind a reverse proxy so another layer of protection is available. Limit the attacks that the real webserver had to contend with. 

Over the last 20+ yrs as a server admin, I've learned a few things. Some by reading. Some from mentors, some from mistakes.

Make daily, versioned, backups and store them elsewhere.  Pull the backups, don't push them. THAT IS THE SINGLE MOST IMPORTANT security ADVICE THAT I HAVE.

Lots and lots of people have written "Ubuntu server guides" - read those. Think through what they say. Implement what makes since and research things that don't until you get why they are important. Next look for apache security guides, then mysql/mariaDB security guides, then find everything you can about the "P" you've chosen to use. IF that is php, good luck. Writing secure php is non-trivial and seems to take years of study to become proficient.  Review the OWASP guides for each of these things too.

Assuming your server has been hacked daily. Act accordingly.  There are over a million LAMP servers currently hacked. Don't be one of those for lack of trying.

Security is hard. It changes every day thanks to different attacks being invented all the time. Anything written is out of date, but at least that level of security is necessary.

---

### Post by Seb_Boffen on 2016-10-03
Personally I setup fail2ban (together with a firewall (shorewall)) to accomplish my needs and ban forever, fail2ban needs extra tweaks. The tweaks are for fail2ban to use and build the same ip blacklist as shorewall likes to use (the firewall) and block spam ip's, ssh logins, remote sessions logon to 127.0.0.1, everything thats escapes the default, I add manually to the blacklist, which btw is not much, I my case it's spam related.

---

### Post by fernandoch on 2016-10-04
> **Vegan said:**
> 1) make sure all management accounts are using 128-bit or better passwords
2) use a firewall if you are hinked up over hanging a server over the internet

Thanks, I normally use ufw and fail2ban, anything else?

> **TheFu said:**
> Every server is a little different. Security for all of them is the same, the OS doesn't matter.
Depending on your level of expertise, the answers for each of these things will be different. 

* remove any unused services.
* don't leave development tools on a production system.
* stay patched. There are thousands of unknown issues on every OS. Fortunately, most attackers use known attacks.
* don't allow required open ports to be accessed by anyone who doesn't need that access.
* use multiple methods to secure each open port. Firewalls, authentication, key-based auth, and 2FA, encryption, you get the idea.
* use proper security and proper encryption for the likely attack vectors. What those are depends on the content and tools used on the website.
* run the minimal service needed to accomplish the job. Avoid "kitchen sink" solutions.
* don't use passwords as security technique. Passwords are for use the 1st time, then keys should be used and passwords disabled.

So ... for each service you run, run through that list and lock each down each with multiple layers of protection.

Then use the available tools to check that what you've done is working. Save those scripts so that you can re-run them after every patch gets applied. Consistency.

And learn how to hack your own site.  Not all attacks come straight on. Crackers are a craft bunch and they will avoid the front entrance with the steel door when a small hacksaw through the sidewall will work easier and still get inside.  If you have a banking website, the protections need to be much greater than for a cat-picture website.

Plus I'm a real believer in 1 service per system, so the idea of having the DB running on the same machine as the website seems just wrong. I put webservers behind a reverse proxy so another layer of protection is available. Limit the attacks that the real webserver had to contend with. 

Over the last 20+ yrs as a server admin, I've learned a few things. Some by reading. Some from mentors, some from mistakes.

Make daily, versioned, backups and store them elsewhere.  Pull the backups, don't push them. THAT IS THE SINGLE MOST IMPORTANT security ADVICE THAT I HAVE.

Lots and lots of people have written "Ubuntu server guides" - read those. Think through what they say. Implement what makes since and research things that don't until you get why they are important. Next look for apache security guides, then mysql/mariaDB security guides, then find everything you can about the "P" you've chosen to use. IF that is php, good luck. Writing secure php is non-trivial and seems to take years of study to become proficient.  Review the OWASP guides for each of these things too.

Assuming your server has been hacked daily. Act accordingly.  There are over a million LAMP servers currently hacked. Don't be one of those for lack of trying.

Security is hard. It changes every day thanks to different attacks being invented all the time. Anything written is out of date, but at least that level of security is necessary.

Wow, this is a huge list with things to do, thanks. What do you mean by pulling the backups?

> **Seb_Boffen said:**
> Personally I setup fail2ban (together with a firewall (shorewall)) to accomplish my needs and ban forever, fail2ban needs extra tweaks. The tweaks are for fail2ban to use and build the same ip blacklist as shorewall likes to use (the firewall) and block spam ip's, ssh logins, remote sessions logon to 127.0.0.1, everything thats escapes the default, I add manually to the blacklist, which btw is not much, I my case it's spam related.

Why shorewall and not ufw? Is there a good integration between fail2ban and shorewall? I will have to check that...

---

### Post by TheFu on 2016-10-04
> 
Wow, this is a huge list with things to do, thanks. What do you mean by pulling the backups?

Backups left on the same system are a failure. They need to be on a different system or the hackers can just delete them. If you *push* the backups, then the hacker using control over the LAMP system can do whatever the backup tools allow. That usually includes removing old backups. What if they remove all old backups on the remote system?  If the backups are *pulled*, then the attacker shouldn't have access to the other backup server.  ssh-keys are 1-way ... so the backup server is locked down and pulls backups through ssh-key based authentication.

Fail2ban is fine, but doesn't do anything for parallel attacks.  After you see the first 1,000 attacks coming from 500 different IPs, all coordinated, you'll begin to understand. That doesn't mean you shouldn't use fail2ban, just that it handles unorganized attackers.  Those people aren't the real threat.  Block all IPs, except those that actually need access.  For example, ssh access isn't needed by anyone outside your country, right?  If you have a static IP, you can limit it to just your IP. That effectively blocks all those ssh attacks from 1,000-1,000,000,000,000 others.

The specific interface into netfilter doesn't matter. iptables, ufw, whatever. Doesn't matter.

I think shorewall is meant to be run on a different system - basically it is a router distro.  I assumed the edge router was secured, running on a different system, and only allows the necessary ports and protocols through.  Network security is different from server security, but still needed.

Passwords - don't use passwords. If you are still thinking that way, then you've already lost the security battle.

Are you beginning to understand how complex this can get and why your level of skill matters with our responses?  Nobody mentioned kernel tuning or protection against TCP attack methods ... there's lots and lots and lots to be done, but some of that would be a complete waste of time if the site hosts cat photos.  The security posture needs to reflect the data/network being protected.

Of of everything mentioned, the biggest threat to security really is the php code run.  Be very careful with any 3rd party "themes" and addons. Those are a constant problem for WP sites world-wide.  I know the WP dev team (family relation). The core guys at the company are very good with php.  It is all the theme/addon vendors who really cause the WP security issues.  Well, plus - don't use plain FTP. Always use sftp.

I've been doing this stuff for 25+ yrs now. Not all advice is good. Just sayin'.

---

### Post by fernandoch on 2016-10-04
> **TheFu said:**
> Backups left on the same system are a failure. They need to be on a different system or the hackers can just delete them. If you *push* the backups, then the hacker using control over the LAMP system can do whatever the backup tools allow. That usually includes removing old backups. What if they remote all old backups?  If the backups are *pulled*, then the attacker shouldn't have access to the other backup server.  ssh-keys are 1-way ... so the backup server is locked down and pulls backups through ssh-key based authentication.

Fail2ban is fine, but doesn't do anything for parallel attacks.  After you see the first 1,000 attacks coming from 500 different IPs, all coordinated, you'll begin to understand. That doesn't mean you shouldn't use fail2ban, just that it handles unorganized attackers.  Those people aren't the real threat.

The specific interface into netfilter doesn't matter. iptables, ufw, whatever. Doesn't matter.

I think shorewall is meant to be run on a different system - basically it is a router distro.  I assumed the edge router was secured, running on a different system, and only allows the necessary ports and protocols through.

Passwords - don't use passwords. If you are still thinking that way, then you've already lost the security battle.

Are you beginning to understand how complex this can get and why your level of skill matters with our responses?  Nobody mentioned kernel tuning or protection against TCP attack methods ... there's lots and lots and lots to be done, but some of that would be a complete waste of time if the site hosts cat photos.  The security posture needs to reflect the data/network being protected.

Of of everything mentioned, the biggest threat to security really is the php code run.  Be very careful with any 3rd party "themes" and addons. Those are a constant problem for WP sites world-wide.  I know the WP dev team (family relation). The core guys at the company are very good with php.  It is all the theme/addon vendors who really cause the WP security issues.  Well, plus - don't use plain FTP. Always use sftp.

I've been doing this stuff for 25+ yrs now. Not all advice is good. Just sayin'.

OK, I understand what you mean, local vs remote backups.

I just use shells for my backups and I do them locally, then I move them to some other secure place.

What do you use then for parallel backups?

---

### Post by fernandoch on 2016-10-04
Duplicate post.

---

### Post by TheFu on 2016-10-04
> parallel backups?
Don't understand.

cron, shell/perl scripts, ssh, rdiff-backup. Nothing fancy.

BTW, no need to quote the entire post. Selective quotes are appreciated.

---

### Post by SeijiSensei on 2016-10-04
Poorly-written PHP scripts can pose a security threat.  Filter user inputs to avoid things like SQL injection attacks.  If you use cookies, make them unguessable; I use random MD5 strings as cookie identifiers.  The same applies to user IDs or any other strings that will appear in GET URLs.  Make sure to use POST rather than GET for forms input whenever possible.

---

### Post by fernandoch on 2016-10-05
> **TheFu said:**
> Fail2ban is fine, but doesn't do anything for parallel attacks.  After you see the first 1,000 attacks coming from 500 different IPs, all coordinated, you'll begin to understand. That doesn't mean you shouldn't use fail2ban, just that it handles unorganized attackers.  Those people aren't the real threat.  Block all IPs, except those that actually need access.  For example, ssh access isn't needed by anyone outside your country, right?  If you have a static IP, you can limit it to just your IP. That effectively blocks all those ssh attacks from 1,000-1,000,000,000,000 others.

What do you use to block parallel attacks?

---

### Post by TheFu on 2016-10-05
> 
What do you use to block parallel attacks? 
I use what is described in the text you quoted.  
Also, I move services to non-standard ports. Sure, it isn't really any additional security, but since moving ssh off 22/tcp, the number of attempts has dropped 1,000x.  Every once in a while I'll see attacks on the non-standard port, but nothing like it was on 22/tcp.

---

