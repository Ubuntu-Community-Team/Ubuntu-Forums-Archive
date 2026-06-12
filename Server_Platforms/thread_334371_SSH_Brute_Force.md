---
title: "SSH Brute Force"
date: 2007-01-08
forum: Server Platforms
---

### Post by kooseefoo on 2007-01-08
Hey!

I'm running Ubuntu Server Edition 6.10 (aka Edgy).

I have the system configured as a server for many causes, but the one thing that concerns me is SSH. Although I need the SSH functionality, my entire network is compromised if somebody gets in.

After looking through the system logs, I've found that my server is subject to several brute-force style attacks on its SSH server every day. Each attacker might make 200 or even 1000 attempts to break in. Although my passwords are all reasonably secure, I'd like to find a way to prevent these attacks from the off-chance of getting anywhere.

What I'm looking for is a lockout after 3 or 5 attempts sort of deal, but I can't find any such functionality for SSH.

Any pointers?


Thanks in advance,
Chris

---

### Post by capitalistpiglet on 2007-01-08
Ive looked at this as well and i cannot find a way to do this. But the good news is as long as you use a secure password then the chances of somebody guessing it is extremely remote. 
There are some ways you can secure it however, you can limit the range of ip addresses/blocks to ones you know your going to be logging in from.
Or you can get rid of passwords altogether and only allow login using encryption keys, this is really only a option if your the only person logging in, because setting it up for many different users would be a pain.

---

### Post by chrisfay on 2007-01-08
Although most will run port scans you can escape a large portion of the attempts by running your SSH server on a non-standard port. I had hundreds of daily brute force attacks until I changed mine. Not a single one since...

Other option is to drop passwords completely, generate a pair of keys and require that as your authorization.  I personally use keys and wouldn't do it any other way.

---

### Post by maggotbrain on 2007-01-08
Hello,
Here is an article and script/app that can block ssh attempts by IP address and invalid login attempts. I have only tested it briefly on one of my lab machines(non-live Internet/production box) and it seems to work as advertised:

**Preventing SSH Dictionary Attacks With DenyHosts:**

[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts")

Some other suggestions to mitigate scripted, brute-force attacks:
- move sshd to another, non-standard port
- authenticate against a known_host_file
- disable interactive keyboard use(use private-key auth only)

Hope this helps you

k

---

### Post by edafe on 2007-01-08
Public/private key authentication and no passwords:

[http://www.edafe.org/ubuntu/index.html#pubkey](http://www.edafe.org/ubuntu/index.html#pubkey)

Regards,
Edafe

---

### Post by s04bf1c2 on 2007-01-09
One way you to prevent this kind of attack is Port Knocking [http://en.wikipedia.org/wiki/Port_knocking]("http://en.wikipedia.org/wiki/Port_knocking").

---

### Post by az on 2007-01-09
Ssh will not provide that functionality, but there are tons of tools in the repositories.  Just search for firewalls, portscan or intrusion detection systems.

For example, fail2ban is probably one tool that does what you are looking for:
[http://packages.ubuntu.com/dapper/net/fail2ban](http://packages.ubuntu.com/dapper/net/fail2ban)
Monitors (in daemon mode) or just scans log files (e.g. /var/log/auth.log, /var/log/apache/access.log) and temporarily bans failure-prone addresses by updating existing firewall rules. Currently, by default, supports ssh/apache but configuration can be easily extended for scanning the other ASCII log files. Firewall rules are given in the config file, thus it can be adopted to be used with a variety of firewalls (e.g. iptables, ipfwadm). 

There are many of other tools.  Search the repositories for tools to build a comprehensive approach to security.

---

### Post by MJN on 2007-01-10
I would second the Fail2Ban suggestion - it, like many tools, does the job of scanning for failed login attempts in the logs and bans any IPs that trip specified levels. Works well out of the box (5 failed attempts and you're out for 10 minutes - in my experience this time limit is surprisingly effective as the bots generally/nearly-always move straight on - you might want to increase it however although bear in mind making it indefinite could come back to bite you if you lock yourself out!)
 
Where Fail2Ban stands out from the crowd in my opinion is its simplicity - the config files are nice and short with good in-file explanations of what all the options do.
 
Denyhosts, on the other hand, also works well - however its config is more difficult and getting banned IPs out of the lists is troublesome (as it uses multiple files as ban lists depending what sort of 'trip' was registered). It perhaps goes one step further than Fail2Ban in that it can connect to a central repository listing known compromised machines and other bots currently doing the rounds however this is more for the obsessive than anyone else as if these machines connect to you you'll soon be blocking them for yourself anyway.
 
All-in-all it, combined with decent passwords, is a good balance of security whilst not making unncessary sacrifices or variations-from-the-ideal to you and your users.
 
Mathew

---

### Post by PetePete on 2007-01-10
i agree with fail2ban..... brilliant little program.

sudo apt-get install fail2ban 

thats all you need to do and after that any IP with 5 failed attempts will be banned for 10 minutes (for ssh.)

---

