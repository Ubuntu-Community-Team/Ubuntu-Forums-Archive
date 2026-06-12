---
title: "server setup"
date: 2013-10-04
forum: Server Platforms
---

### Post by mourgolikos on 2013-10-04
hello everyone
This is my first attempt to create my own server and make it public. I am running ubuntu server 12.04.3 on an old laptop.
I have installed webmin, phpmyadmin etc etc and I am planning on hosting a web-site for a project of mine. I also want to have remote access via FTP and store my databases using mySQL. I have a couple of questions but first things first!
I have set everything up and working locally (ftp access using filezilla and my webpage). I forwarded the required ports and I managed to have access remotely as well. I used no-ip.com to create a domain name and that worked fine as well for both the FTP and the website. 
I restarted my router and my public ip was reset (my ISP provides me with a dynamic ip). Now every time my router restarts I need to lookup my new public IP to access my files and page. Is there any way I could work that out?

Thank you

---

### Post by TheFu on 2013-10-04
Congratulations!  Many people started out just like you. Fun stuff.

A - don't restart your router very often. You are providing services on the 24/7/365 internet now to the entire world. It doesn't matter if you don't know about those foreign users, they have certainly discovered your FTP site already. ;)
B - setup a no-ip Dynamic DNS server that will auto-update the no-ip DNS records. Be certain that your DNS TTL is 30 min or so.  There is a no-ip package for Ubuntu that does this.
C - FTP probably isn't the best service to run unless you want anyone, anywhere in the world to have access to your machine (and not just the FTP areas you specify). See, the most popular FTP servers have been hacked a few times - back doors added.  Plus FTP doesn't have any encryption, so using logins are just providing credentials to anyone between the remote system and your box.  [Almost everyone should stop using FTP.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")
D - Webmin and phpmyadmin are security issues waiting to be exploited.  ****Both**** have been exploited before, so if you must run them, then please, pplease, please, please do not allow external access.
E - Never allow external access to your MySQL DBs. NEVER, NEVER, NEVER.

The best service to allow on the internet for home users is ssh - nothing else.  With it, you can avoid using password - **ssh-keys ROCK!**. You can scp, sftp,  remote shell and remote desktop back to the system over ssh-tunnels. With keys, it is actually more convenient AND more secure.  [Things to help secure ssh/scp/sftp/etc ... ]("http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")  The main methods to secure ssh are:
* run an iptables-based firewall
* use ssh keys for all authentication outside the LAN.
* install fail2ban so that failures are blocked quickly (using the firewall)

Backups - versioned backups.  These are the most important thing to running a public service. Restore files from yesterday, last week or last month, since we don't usually notice being hacked for a day or 10. ;)  Backups are good for other reasons too.

Anyway - have fun and I hope you don&#8217;t get hacked.  OTOH, being hacked was some of the best education that I've ever had.

---

### Post by mourgolikos on 2013-10-04
> **TheFu said:**
> Congratulations!  Many people started out just like you. Fun stuff.

A - don't restart your router very often. You are providing services on the 24/7/365 internet now to the entire world. It doesn't matter if you don't know about those foreign users, they have certainly discovered your FTP site already. ;)
B - setup a no-ip Dynamic DNS server that will auto-update the no-ip DNS records. Be certain that your DNS TTL is 30 min or so.  There is a no-ip package for Ubuntu that does this.
C - FTP probably isn't the best service to run unless you want anyone, anywhere in the world to have access to your machine (and not just the FTP areas you specify). See, the most popular FTP servers have been hacked a few times - back doors added.  Plus FTP doesn't have any encryption, so using logins are just providing credentials to anyone between the remote system and your box.  [Almost everyone should stop using FTP.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")
D - Webmin and phpmyadmin are security issues waiting to be exploited.  ****Both**** have been exploited before, so if you must run them, then please, pplease, please, please do not allow external access.
E - Never allow external access to your MySQL DBs. NEVER, NEVER, NEVER.

The best service to allow on the internet for home users is ssh - nothing else.  With it, you can avoid using password - **ssh-keys ROCK!**. You can scp, sftp,  remote shell and remote desktop back to the system over ssh-tunnels. With keys, it is actually more convenient AND more secure.  [Things to help secure ssh/scp/sftp/etc ... ]("http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")  The main methods to secure ssh are:
* run an iptables-based firewall
* use ssh keys for all authentication outside the LAN.
* install fail2ban so that failures are blocked quickly (using the firewall)

Backups - versioned backups.  These are the most important thing to running a public service. Restore files from yesterday, last week or last month, since we don't usually notice being hacked for a day or 10. ;)  Backups are good for other reasons too.

Anyway - have fun and I hope you don’t get hacked.  OTOH, being hacked was some of the best education that I've ever had.

thanks for the reply and the tips
I forgot to say that I don't know that much about linux and servers.
A-I am not planing on restarting but it happens from time to time
B-It was impossible for me to install the no-ip update client because I was getting errors after the extraction (make install) so I downloaded the ddclient and set it up for noip. It doesnt seem to work yet but I am going to try it a bit more by myself and then ask for help.
C-I stopped the ftp service. how do I setup and use the sftp? any guides?
D-As I said I am new to the field. How do I block the external access? using the gui of webmin?
E-My database will not be linked to my website atm(if this is the reason why it is dangerous). I just want to create it and give access to a friend (logging from another ip)

Ps I dont worry about being hacked because there is nothing valuable at all in my server. It is 100% for educational reasons. :-)

---

### Post by TheFu on 2013-10-05
> **mourgolikos said:**
> thanks for the reply and the tips
I forgot to say that I don't know that much about linux and servers.

We all started not knowing much. I've been learning about UNIX/Linux for over 20 yrs. Feels like I know about 10% today.
> **mourgolikos said:**
> 
A-I am not planing on restarting but it happens from time to time

I think my router has been restarted 3 times the last 2 years. It is on a UPS.  A properly running router shouldn't need to be rebooted "just because."
> **mourgolikos said:**
> 
B-It was impossible for me to install the no-ip update client because I was getting errors after the extraction (make install) so I downloaded the ddclient and set it up for noip. It doesnt seem to work yet but I am going to try it a bit more by myself and then ask for help.
Good plan. try, try, try, google, ask.  I had it running a few years ago, but have since switched to officially static IPs. We still use no-ip as 1 of the DNS services.  I thought there was an Ubuntu package for this?

> **mourgolikos said:**
> 
C-I stopped the ftp service. how do I setup and use the sftp? any guides?

sftp is included automatically with ssh ---- **apt-get install ssh-server** is my guess.  My setups are automatic. Even so, when I install a fresh server the ONLY service I enable at install time is the ssh-server.  NEVER anything else.
> **mourgolikos said:**
> 
D-As I said I am new to the field. How do I block the external access? using the gui of webmin?

I wouldn't know anything about web-based administration tools. They have a place, but not on any of my servers.  Security risk.  The easy way is to block the port on the router and setup a firewall on the machine that blocks all access from non-LAN IPs.  If you have IPv6 enabled, be certain to do that for IPv6 addresses too.
> **mourgolikos said:**
> 
E-My database will not be linked to my website atm(if this is the reason why it is dangerous). I just want to create it and give access to a friend (logging from another ip)  Well, that is exactly the behavior I'm saying you shouldn't allow. Disable that access until you learn how to block it for everyone else. Until you learn that, you aren't ready, grasshopper. ;)

> **mourgolikos said:**
> 
Ps I dont worry about being hacked because there is nothing valuable at all in my server. It is 100% for educational reasons. :-)
That is a complete crock. Seriously, they (you know .. "them" ) aren't out to get just you. They are out to get everyone foolish enough to put an non-secure system on the internet.  Then they just want your bandwidth to launch attacks, [This Washington Post article will explain.]("http://voices.washingtonpost.com/securityfix/2009/05/the_scrap_value_of_a_hacked_pc.html")   Updated[ version.]("http://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/") Setup your RSS reader to follow Brian Krebs - you'll thank me and he will open your eyes.

Running a server on the internet makes you into a paranoid person since there are attacks against your machine constantly ... if that machine falls, your entire internal network is gone too. If you have a smart-TV - it will be hacked too. Do you think about patching your TV, microware, toaster and every other "networked" device?  Once inside the trusted LAN, gaining access to other devices is much easier.  I haven't been hacked since 2002 and was hacked in 1995 while on a government LAN connection. They took over my machine, deleted my account and changed the root password in less than 20 minutes ... over a dial-up connection.  Government security took the HDD and investigated. I never heard about it again and didn't get my HDD back.

Being paranoid now will save you from hassles. Sure, you don't think you have much to lose today, but imagine when every device on your LAN has been compromised. What will you do then?

---

### Post by mourgolikos on 2013-10-05
I have not yet managed to set up correctly ddclient (it stopped displaying the errors but it does not update my ip).

There is no ubuntu **server** package for noip I am afraid! Although, instructions on how to download and install the client (which did not work for me) can be found here: [http://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/](http://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/)  

Anyway, I have ssh server already installed (chose it during installation of the OS) but I need to create new user accounts to log in! don't I? And then I guess I will connect using filezilla?! The port which I should be using is 22?

Any suggestions on the firewall I should use?

What you are saying about the database is that I should block all incoming connections except from specific IPs?

I surfed a bit on [http://krebsonsecurity.com/](http://krebsonsecurity.com/) It looks REALLY interesting. It seems like I am going to spend days on it :-p thank you

PS paranoid mode: on

---

### Post by CharlesA on 2013-10-05
> **TheFu said:**
> I think my router has been restarted 3 times the last 2 years. It is on a UPS.  A properly running router shouldn't need to be rebooted "just because."

You too, huh? So far mine has only rebooted due to a move. I usually have it plugged into a battery backup, but not right now.

> I wouldn't know anything about web-based administration tools. They have a place, but not on any of my servers.  Security risk.  The easy way is to block the port on the router and setup a firewall on the machine that blocks all access from non-LAN IPs.  If you have IPv6 enabled, be certain to do that for IPv6 addresses too.
  Well, that is exactly the behavior I'm saying you shouldn't allow. Disable that access until you learn how to block it for everyone else. Until you learn that, you aren't ready, grasshopper. ;)

Likewise, I don't really like web-based admin tools but if you need to use them, firewall them so that they can only be accessed from certain IP addresses to limit your attach surface.

I've only ever used a db server that listens on localhost, so it won't accept any external connections.

> That is a complete crock. Seriously, they (you know .. "them" ) aren't out to get just you. They are out to get everyone foolish enough to put an non-secure system on the internet.  Then they just want your bandwidth to launch attacks, [This Washington Post article will explain.]("http://voices.washingtonpost.com/securityfix/2009/05/the_scrap_value_of_a_hacked_pc.html")   Updated[ version.]("http://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/") Setup your RSS reader to follow Brian Krebs - you'll thank me and he will open your eyes.

Good links. I've had a ton of brute force attacks (and mod_proxy attacks too!) on both my VPSes, but so far no one has been able to get in. Reading logs to get familiar with what is normal and what isn't is a good way to keep an eye on things. I use logwatch for the most part, but it doesn't catch everything.

> Running a server on the internet makes you into a paranoid person since there are attacks against your machine constantly ... if that machine falls, your entire internal network is gone too.

That is why I use a VPS for my web and mail servers instead of hosting it at home. :p If it was hosted at home, I'd be sure to isolate it from the rest of the network.

As far as firewalls go, iptables ftw! Although, you can also use ufw, I prefer iptables.
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by TheFu on 2013-10-05
> **mourgolikos said:**
> I have not yet managed to set up correctly ddclient (it stopped displaying the errors but it does not update my ip).

ddclient ... isn't that for dyndns?  Unless you are paying for an account, you still **must** manually login monthly to keep your account active. I think this changed in May.  I'm grandfathered there from there 1990s.  Many routers will handle DynDNS for you - no need for a separate client.

> **mourgolikos said:**
> There is no ubuntu **server** package for noip I am afraid! Although, instructions on how to download and install the client (which did not work for me) can be found here: [http://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/](http://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/)  
Last time I used it, it was trivial for me to setup.  OTOH, I've worked as a professional C/C++ dev for over a decade and have learned a deeper level of understanding for building software. Plus I *like* perl. ;)

> **mourgolikos said:**
> Anyway, I have ssh server already installed (chose it during installation of the OS) but I need to create new user accounts to log in! don't I? And then I guess I will connect using filezilla?! The port which I should be using is 22?

ssh uses your normal login (i.e. system) account.  This ain't windows.  You connect using any ssh/sftp/scp client that you like in the world. There must be 500 of them across all the different platforms.  There is an ssh-client package for Ubuntu that I use, plus putty for Windows and under Android there must be 50 different Apps - I like **Terminal IDE** because it includes the things I miss about Linux for android.  Remember, ssh is a remote login, sftp is a file copy interface designed to be like plain-unsecure-FTP and scp is a file copy interface designed to mirror rcp.  On UNIX, almost all tools that worked with rcp, ftp, and rsh work unchanged with scp, sftp, and ssh  - the interfaces were designed for backwards compatibility.  I've worked places with hardcoded system() calls to these older tools, so we just used aliases or modified the PATH to use the secure, encrypted versions instead. Same, same, but with security.

I've never used Filezilla - WinSCP is nice, however.

Be certain to setup your ssh-keys and push the public keys to those remote systems you want to connect. Google is your friend for this. To make life even easier, setup a ~/.ssh/config file with aliases for all the remote systems you use. You can change the userid, port, server-name ... and it will keep a record of remote systems where you have accounts ... plus you probably are religious about backing up your HOME, right?  That means this data is secure should something bad happen to the HDD.

> **mourgolikos said:**
> Any suggestions on the firewall I should use?
There is only 1 firewall for Linux, iptables.  Anything else is a GUI/CLI over that.  I use iptables directly to have complete control. google with "ubuntu firewall" will probably yield suggestions.  This isn't Windows.  You are learning an entirely new language with 10% similarities, but 90% differences from the last language you used.

> **mourgolikos said:**
> What you are saying about the database is that I should block all incoming connections except from specific IPs?  That really isn't what I'm saying. You shouldn't allow remote access to any DB, but you probably won't listen to me.  I'd rather see you give your friend a login on your box ... using ssh ... then allow the DB interface on the internet.

> **mourgolikos said:**
> I surfed a bit on [http://krebsonsecurity.com/](http://krebsonsecurity.com/) It looks REALLY interesting. It seems like I am going to spend days on it :-p thank you
You might enjoy my blog too, though I don't have as much to say these days. jdpfu.com/tag/linux

> **mourgolikos said:**
> PS paranoid mode: on

I don't think the average person understands how open the internet is - it is like the wild west still.  Ok - just for fun, I did a little grep on my reverse proxy logs ... this is where I block blatant hacking attempts ... any SQL injection and any php (my security mind doesn't allow php to be use on internet services).

Attempts just for PHP:
 * attempts against the generic IP (not using a domain at all) - 34
 * attempts against a non-published dns name - 1
 * attempts against my blog - 404
 * attempts with malformed requests - 65

Attempts to inject SQL:
 * attempts against my blog - 101
 * attempts against a non-published dns name - 3

These logs are swapped daily. The DNS name that isn't published is known to 4 people in the world. There is no reason for anyone else to use it, so they clearly did a port scan, found an open service and started attacking it.

These are modest attempts. A popular server would see thousands of attempts hourly.

---

### Post by mourgolikos on 2013-10-05
It seems like I got loads of studying to do. There are so many things you mentioned and I had no idea about! I will try to gather some info about all that new stuff and I will be back with more questions :-p

---

### Post by Laice on 2013-10-05
my newest best friend as a serveradmin is Denyhosts.  Put it this way it's banned me once, but with the 500 people it's legitimately banned today i can live with that!  (resolved that issue by adding my static ip to /etc/hosts.allow)

sudo apt-get install denyhosts

---

### Post by mourgolikos on 2013-10-06
ddclient successfully set to update my no-ip account.

Next up: iptables to block all remote access but ssh

Q: How can I edit the services that start when the server boots?

---

### Post by TheFu on 2013-10-06
> **mourgolikos said:**
> ddclient successfully set to update my no-ip account.

Next up: iptables to block all remote access but ssh

Q: How can I edit the services that start when the server boots?

A: It depends on how the service was created/setup by the developer.  If you aren't using **man pages** already - please start. The documentation for almost every command on your box is there.

When you don't know the name, use **whatis**
$ whatis startup 
$ whatis init
$ whatis upstart

Then switch to either **apropos** or **man** to learn more.
$ apropos start
Ah .... getting somewhere now.
$ man start
Ah .... looks like there is start, stop, restart, reload, status commands built in.
$ status ssh
interesting, but only slightly useful.

Ok - I know an answer - see there are many different ways to accomplish the same thing. In the old days, I'd copy a script from /etc/init.d/ and modify it to my need with start/stop/status/restart/reload options.  These days, the scrips are pre-built and there is a tool to manage under which runlevel each starts or stops.  That tool is **update-rc.d** - **man update-rc.d** is really what you want.  All it does (or did before they changed the way daemons are started/stopped in the last few yrs) is manage symlinks into the /etc/rc{N}.d/ directories.  As a budding admin, understanding those will become more important.
$ man runlevel

BTW, **man** has lots of options.  How do you learn about those?  **man man** of course.  You'll see that sometimes there are different "sections" for the same command. I'll leave it to you for why.

Knowing how to find answers is a key skill for an admin. Your system will tell you almost all those answer, if you ask it and learn to interpret the output.  Reading manpages for the greatest effect took me about 6 months to "get" - since that time, I find them mostly amazing, with a few exceptions of crap. Usually the "crap" manpages are for newer commands where the developer prefers to create a huge website instead of following the standard.  If you want to see how great a manpage can be, a few of the best:
* man ssh
* man sudoers
* man bash
* man fstab

Too much to know.

Anyway, have fun, use man and google, feel free to ask for help.  I will not spoon-feed commands, but I'm happy to discuss the "why" **after** you've googled and RTFM. ;)

---

### Post by mourgolikos on 2013-10-07
hey, I am currently working on another project as well as my coursework for uni so I will not be updating that often.
first of all the commands "theFu" mentioned were really helpful and thank you.
I went through some tutorials and I ve done some reading and I managed to get an overall understanding of what iptables are and how they work.
I DROPed all incoming & connecions and then i set new rules to accept input and output to ssh, http and (temporarily) webmin.
I will post the code so that you might help me understand whether or not my configuration is the one I should have. 
I read the previous posts and I realized I havent really understood whether "TheFu" suggested what I ve actually done or something completely different.
Are my setting correct?
Is there anything I should change/consider?
```

**> iptables -L**
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh state NEW,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http state NEW,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:webmin

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:ssh state ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:http state ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:webmin

```

---

### Post by CharlesA on 2013-10-07
Looks fine to me. Personally I would limit access to webmin so that it is only accessible from certain ip addresses and not open to the public.

---

### Post by mourgolikos on 2013-10-07
is this done using the following code?
```

[FONT=Monaco]iptables -I INPUT -p tcp -s 123.456.7.8 --dport 10000 -j ACCEPT
[/FONT][FONT=Monaco]iptables -I OUTPUT -p tcp -s 123.456.7.8 --sport 10000 -j ACCEPT
[/FONT]
```

---

### Post by CharlesA on 2013-10-07
The output rules need to be fixed, otherwise you won't be able to get out to the internet thru the firewall. The computer uses a random high port as the source and sends packets to whatever destination port, so if you want to keep the output rules.

I do not using any output rules, but some people feel they increase security.

---

### Post by TheFu on 2013-10-08
Did you look at other firewall front-ends first?  ufw?
Also, let **fail2ban** manage your ssh connection rules.  No need to reinvent that wheel.

Honestly, it is easiest just to block everything and only allow ssh ... then let fail2ban handle those connections.

---

### Post by CharlesA on 2013-10-08
> **TheFu said:**
> Honestly, it is easiest just to block everything and only allow ssh ... then let fail2ban handle those connections.

I use iptables to deal with ssh instead of fail2ban, but your point is sound. :)

---

### Post by sandyd on 2013-10-08
If you think fail2ban is hard, look into csf/lfd as well

CSF/LFD is much easier to configure than iptables/fail2ban if you are just starting with firewalls

Download CSF from [http://configserver.com/free/csf.tgz](http://configserver.com/free/csf.tgz)
Extract, and run install.sh

Just make the following edits in /etc/csf/csf.conf

```

#Add TCP ports that should be open to everyone here
TCP_IN="80"
#Allow all ports out
TCP_OUT="0:65535"

#Add UDP Ports that should be open to everyone here
UDP_IN=""
#Allow all UDP ports out
UDP_OUT="0:65535"

```

Now, walk over to /etc/csf/csf.allow, and add IP Restrictions in the following format

```

tcp|in|d=[destination port]|d=[destination address]
tcp|in|d=[destination port]|s=[source address]

```

ex:
```

tcp|in|d=10000|d=127.0.0.1
tcp|in|d=10000|s=172.16.2.111
```

The rest of the comments are self explanatory (remember to **enable** csf by setting TESTING to 0 at the top of the file)

To reload csf (and apply changes)
```

csf -r
service lfd restart
```

LFD is the login failure detection, and it bans IPs from connecting to your server after failing to SSH 3 times (default, configurable in csf.conf)

Make sure you dont run iptables -F unless you want to lock yourself out - just adjust the firewall with CSF

---

### Post by mourgolikos on 2013-10-09
I did set iptables setting to default and I installed + configured ufw and fail2ban.
I am not pretty sure how to test it but everything seem to work up to now.
fail2ban status:
```

|- Number of jail:    1
`- Jail list:             ssh

```

ufw status:
```

To                              Action            From
--                              -------           -----
22                              ALLOW           Anywhere
22                              ALLOW           Anywhere (v6)

```

> **TheFu said:**
> Did you look at other firewall front-ends first?  ufw?
Also, let **fail2ban** manage your ssh connection rules.  No need to reinvent that wheel.

Honestly, it is easiest just to block everything and only allow ssh ... then let fail2ban handle those connections.
If I only allow ssh how will my webpage be available?

Q: Is it safe to allow root remote access via ssh?

---

### Post by TheFu on 2013-10-09
> **mourgolikos said:**
> I did set iptables setting to default and I installed + configured ufw and fail2ban.
I am not pretty sure how to test it but everything seem to work up to now.
fail2ban status:
```

|- Number of jail:    1
`- Jail list:             ssh

```

ufw status:
```

To                              Action            From
--                              -------           -----
22                              ALLOW           Anywhere
22                              ALLOW           Anywhere (v6)

```

Perfect. 
> **mourgolikos said:**
> 
If I only allow ssh how will my webpage be available?

Allowing inbound port 80/443 is easy with ufw.  ```
ufw in allow http
``` should do it, I think.  Let me check the man page. Once again, I was WRONG!  man page says it should be ```
ufw allow in http
``` instead. The "http" part is found in the /etc/services file ... BTW, the man page has examples too. ;)

Anyone know the difference between these:
```
ufw allow in http
```
and
```
ufw allow in 80/tcp
```
??  It isn't completely clear to me.  If google starts using UDP ... lots of firewall rules will need to be updated, methinks. ;)

> **mourgolikos said:**
> 
Q: Is it safe to allow root remote access via ssh?

Never.  Remote root is never a good idea and should be blocked by the ssh config file(s).  Always login using a different userid, then sudo to do root things. Using ssh-keys (never passwords after the 1st time) should also be standard security.
* ssh-keygen on the client
* ssh-copy-id from the client
done.  60 seconds to happiness. Seriously. ;)

I like to avoid downloading software that isn't part of the repos ... even 3rd party PPAs can get our installs into trouble. Being in "APT hell" is not fun, but managing tgz source downloads is even less fun, for me.

---

### Post by mourgolikos on 2013-10-10
> **TheFu said:**
> 
Never.  Remote root is never a good idea and should be blocked by the ssh config file(s).  Always login using a different userid, then sudo to do root things. Using ssh-keys (never passwords after the 1st time) should also be standard security.
* ssh-keygen on the client
* ssh-copy-id from the client
done.  60 seconds to happiness. Seriously. ;)

I like to avoid downloading software that isn't part of the repos ... even 3rd party PPAs can get our installs into trouble. Being in "APT hell" is not fun, but managing tgz source downloads is even less fun, for me.

I have currently deactivated the root remote login but even when I log as a user and try to use sudo (i am using the winSCP command line) I get an error "access denied error 3". I want to edit some of the files of my website and with my current settings it seems impossible! What can I do about it?

PS Next up is ssh-keys (I only log in within my local network currently using my user and pass)

---

### Post by TheFu on 2013-10-10
> **mourgolikos said:**
> I have currently deactivated the root remote login but even when I log as a user and try to use sudo (i am using the winSCP command line) I get an error "access denied error 3". I want to edit some of the files of my website and with my current settings it seems impossible! What can I do about it?

PS Next up is ssh-keys (I only log in within my local network currently using my user and pass)

i've never used winscp except to transfer files. It is not an editor or a file system mounting tool. sftp, scp do not work that way.  If you want that, then you need an sshfs tool - don't know of any for Android, but I haven't looked.

I didn't know that sftp supported sudo? Does it?

None of these tools will override normal Linux file system permissions and ownership.  Changing the owership and groups for certain files should happen thru ssh.

---

### Post by CharlesA on 2013-10-10
> **TheFu said:**
> 
I didn't know that sftp supported sudo? Does it?

It does not. Last I checked, you can't send terminal commands via sftp.

That is why I have my web root chown'd to my main user instead of root.

---

### Post by mourgolikos on 2013-10-10
> **CharlesA said:**
> 
That is why I have my web root chown'd to my main user instead of root.
How can I do  that? I should set the folder (www) permission to main user?? Is it safe?
I tried
```
sudo chown username filepath
```
can't tell if it works.. did not display any message

Edit: just tried to alter some stuff. it works! thank you

---

### Post by CharlesA on 2013-10-10
> **mourgolikos said:**
> How can I do  that? I should set the folder (www) permission to main user?? Is it safe?
I tried
```
sudo chown username filepath
```
can't tell if it works.. did not display any message

```
sudo chown user:group /path/to/folder
```

Use -R if you want to make it recursive.

It's safe because www-data still only had read access to the web root.

---

### Post by TheFu on 2013-10-10
> **mourgolikos said:**
> How can I do  that? I should set the folder (www) permission to main user?? Is it safe?

There are pros/cons for doing this.  A good understanding of user and group permissions should be your next step. There are tutorials online.  15 minutes now will pay off for the next 40 yrs. Highly recommended.

I wouldn't be doing you any favors by telling you the exact command to type at this pointt.  Until you learn about the permissions, owners, groups, blindly typing commands isn't a good idea.  The core of UNIX security is based on these same permissions.  If you understand that 99.9999% of things are "files" on UNIX systems, then you'll understand how critical understanding file permissions is.

On my systems, www-data is the userid and groupid for web servers.  The web server runs as user:www-data, so whatever I elect, that user **must** have the rights it needs to the files it needs to  access. Sometimes read-only is fine, but other times, read-write is needed. Knowing when 1 is needed and the other is not is key.

Another option is to add your ID to the www-data group AND to ensure that any files placed under your web-server area has that group ownership with r or rw permissions, as needed.  This is the method that I use.  In your tutorial learning, pay careful attention to the "sticky bit" stuff.

Be certain that you experiment with different file/directory permissions until it "clicks" for you. There are some pretty neat ways to allow access to files, but not let a userid "see" the list of filenames inside a directory. It is also possible to prevent specific users or groups from having any access to files, while allowing everyone else full access. Elegant solutions are cool.

BTW, there are very, very, very few times when typing "chmod 777" into a terminal is a good idea. When you see that in any instructions, it means the person telling you to do it doesn't have a good understanding of permissions.

---

### Post by SeijiSensei on 2013-10-10
> **mourgolikos said:**
> I want to edit some of the files of my website and with my current settings it seems impossible! What can I do about it?

The best free SSH client for Windows is [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").  Just log into the account and edit the files there with a text editor like nano or emacs.  

> **TheFu said:**
> If you want that, then you need an sshfs tool - don't know of any for Android, but I haven't looked.

[JuiceSSH]("https://play.google.com/store/apps/details?id=com.sonelli.juicessh&hl=en") for Android is a fine SSH client.  I doubt there is an sshfs client for Android, since unless you have rooted your phone, you cannot mount external filesystems.  SFTP/SCP file transfers are in the pipeline for future versions.

---

### Post by mourgolikos on 2013-10-11
thanks to your replies it's all working now. 
Now I want to be able to receive e-mails (from my server to my desktop) for either server reports or my "contact me" page (using PHP). 
how is this possible? do i have to set and configure ssmtp on my server?

---

### Post by mourgolikos on 2013-10-28
bump

---

### Post by coldraven on 2013-10-28
I would just like to say that I am amazed at the level of good quality advice that you're  getting here.
i set successfully setup a virtual server on my laptop for only one user but I found out that by enabling DMZ on my router also enabled FTP and Telnet ports.
When my internet access slowed down I realised that people were trying to access my router.
It's a wild world out there, take care. These guys are good!

---

### Post by CharlesA on 2013-10-28
> **mourgolikos said:**
> thanks to your replies it's all working now. 
Now I want to be able to receive e-mails (from my server to my desktop) for either server reports or my "contact me" page (using PHP). 
how is this possible? do i have to set and configure ssmtp on my server?

I just set Postfix up to send mail from localhost. That's different from ssmtp, but it works for me.

---

### Post by mourgolikos on 2013-10-31
I will check it out CharlesA. I think that the thread should be closed now because it is going off topic. I will create a new thread if any problems occur! Thanks for all the help so far everyone!

---

