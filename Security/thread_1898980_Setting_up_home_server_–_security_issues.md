---
title: "Setting up home server – security issues?"
date: 2011-12-22
forum: Security
---

### Post by pulck on 2011-12-22
I'm a novice Ubuntu user trying to set up a home server and wondered if anyone who has done something similar could offer some pointers.

I want it to be a file/print server for my home network, sharing folders via SAMBA. I also want to be able to remotely access the machine's desktop both on my home network (the server will be headless) and over the internet. Naturally security is a high priority.

I have a HP Microserver N36L on which I've installed Ubuntu 10.04 Server (with Gnome desktop). I've installed SSH and played around with port forwarding, NX Server, VNC, etc. but I've ended up with more questions than answers.... Can anybody help?

[LIST=1]
[*]If I set my router to port-forward to my server, and my server is set to use an SSH authentication key (with password authentication disabled), is this really secure enough?
[*]Is there a way to use NX Server/Client via SSH tunnel if I disable password authentication on the server? (I've tried everything to get this working, but I cannot log in. If I switch SSH password back on, I can log in no problem)
[*]If NX Server is not an option, is there a decent and secure alternative? (Standard VNC clients seem slow by comparison)
[*]SAMBA shares seem to be straightforward enough to set up, but are there any security issues there?
[*]How can I check if intruders are being effectively fended off by my security measures? I have inspected '/var/log/auth.log' but what am I looking for to see if attacks are being rejected?
[*]Is there any point to a firewall if SSH security is working properly?
[*]Are there any security issues with setting up a standard domain name to point to my server's dynamic IP address? (I am thinking of using no-ip.com's free service for this)
[/LIST]

Any guidance at all would be hugely appreciated. And be easy on me - I'm learning a lot here.

---

### Post by Dangertux on 2011-12-22
> **pulck said:**
> I'm a novice Ubuntu user trying to set up a home server and wondered if anyone who has done something similar could offer some pointers.

I want it to be a file/print server for my home network, sharing folders via SAMBA. I also want to be able to remotely access the machine's desktop both on my home network (the server will be headless) and over the internet. Naturally security is a high priority.

I have a HP Microserver N36L on which I've installed Ubuntu 10.04 Server (with Gnome desktop). I've installed SSH and played around with port forwarding, NX Server, VNC, etc. but I've ended up with more questions than answers.... Can anybody help?

[LIST=1]
[*]If I set my router to port-forward to my server, and my server is set to use an SSH authentication key (with password authentication disabled), is this really secure enough?
[*]Is there a way to use NX Server/Client via SSH tunnel if I disable password authentication on the server? (I've tried everything to get this working, but I cannot log in. If I switch SSH password back on, I can log in no problem)
[*]If NX Server is not an option, is there a decent and secure alternative? (Standard VNC clients seem slow by comparison)
[*]SAMBA shares seem to be straightforward enough to set up, but are there any security issues there?
[*]How can I check if intruders are being effectively fended off by my security measures? I have inspected '/var/log/auth.log' but what am I looking for to see if attacks are being rejected?
[*]Is there any point to a firewall if SSH security is working properly?
[*]Are there any security issues with setting up a standard domain name to point to my server's dynamic IP address? (I am thinking of using no-ip.com's free service for this)
[/LIST]

Any guidance at all would be hugely appreciated. And be easy on me - I'm learning a lot here.

Hi, hopefully this can help you.

1 - SSH is generally accepted as relatively secure when keys are used. 

2 - It should function with SSH keys. Consult this information to configure the set up you're looking for : [http://www.nomachine.com/documents/admin-guide.php](http://www.nomachine.com/documents/admin-guide.php)

3 - Do not use VNC, configure NX. Preferably don't use a desktop environment, but that's your choice.

4 - Tons, make sure your Samba server is not externally exposed. As well as using strong authentication with Samba , and proper permissions. More information for Samba security here : [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html) 

5 - Your log file (auth.log/security) should dispaly failed login attempts as well as other security issues. If it does not just give it some time, it will.

6 - This is debatable. I say both a well configured firewall and mandatory access controls are vital to a well secured machine, though your opinion and mileage may vary. My opinion is that both a firewall and mandatory access controls (apparmor) can mitigate the risk to exposed services greatly.

7 - Not really, I use no-ip's service, they are pretty good. Of course the client does except input from an external source - so it's another thing that could be compromised. 

Hope this helps.

---

### Post by pulck on 2011-12-22
> **Dangertux said:**
> Hi, hopefully this can help you.

1 - SSH is generally accepted as relatively secure when keys are used. 

2 - It should function with SSH keys. Consult this information to configure the set up you're looking for : [http://www.nomachine.com/documents/admin-guide.php](http://www.nomachine.com/documents/admin-guide.php)

3 - Do not use VNC, configure NX. Preferably don't use a desktop environment, but that's your choice.

4 - Tons, make sure your Samba server is not externally exposed. As well as using strong authentication with Samba , and proper permissions. More information for Samba security here : [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html) 

5 - Your log file (auth.log/security) should dispaly failed login attempts as well as other security issues. If it does not just give it some time, it will.

6 - This is debatable. I say both a well configured firewall and mandatory access controls are vital to a well secured machine, though your opinion and mileage may vary. My opinion is that both a firewall and mandatory access controls (apparmor) can mitigate the risk to exposed services greatly.

7 - Not really, I use no-ip's service, they are pretty good. Of course the client does except input from an external source - so it's another thing that could be compromised. 

Hope this helps.

This is very helpful. Many thanks. A couple of follow-up questions.

1 - Great.

2 - On the page you referred me to [http://www.nomachine.com/documents/admin-guide.php]("http://www.nomachine.com/documents/admin-guide.php") under '4. NX Server Authentication' it says that SSH authentication without password is not supported. It talks about an alternative authentication method, but I'm guessing that allowing password authentication on the server is a serious security issue?

3 - I will steer clear of VNC. Are all forms of VNC a security hazard? How about VNC via SSH tunnel?

4 - My shares are already password protected and read-only, but I will study the document carefully.

5 - When you write 'auth.log/security' I'm not exactly sure which file you are referring to. The file 'auth.log' contains my login attempts. Presumably this is the file you're referring to?

6 - I will try to configure a firewall (is there a preferable one?) and apparmor. Previously firewalls have mucked up the accessibility of my SAMBA shares, but I will persevere if there is a security risk without one.

7 - Great news.

Thanks again.

---

### Post by Dangertux on 2011-12-22
> **pulck said:**
> This is very helpful. Many thanks. A couple of follow-up questions.

1 - Great.

2 - On the page you referred me to [http://www.nomachine.com/documents/admin-guide.php](http://www.nomachine.com/documents/admin-guide.php) under '4. NX Server Authentication' it says that SSH authentication without password is not supported. It talks about an alternative authentication method, but I'm guessing that allowing password authentication on the server is a serious security issue?

3 - I will steer clear of VNC. Are all forms of VNC a security hazard? How about VNC via SSH tunnel?

4 - My shares are already password protected and read-only, but I will study the document carefully.

5 - When you write 'auth.log/security' I'm not exactly sure which file you are referring to. The file 'auth.log' contains my login attempts. Presumably this is the file you're referring to?

6 - I will try to configure a firewall (is there a preferable one?) and apparmor. Previously firewalls have mucked up the accessibility of my SAMBA shares, but I will persevere if there is a security risk without one.

7 - Great news.

Thanks again.

Hi again,

here's some more info for your follow ups

2 - I don't use NX so  you might be right. Though I've heard NX touted as more secure than VNC (I've never tried it).

3 - VNC is innately insecure in the length of the password is capped at 8 characters. This is an extremely low entropy rate. Keeping VNC internal by utilizing SSH tunneling or a VPN certainly reduces the risk.

5 - auth.log in the case of ubuntu it's called security on redhat based distributions, I just said that for clarity sake in the off chance you switch to CentOS or some other RHEL based distro midway through. 

6 - The 'firewalls' you actually see are all front ends for iptables/netfilter. On a server I prefer configuring netfilter directly via iptables. However UFW is also a nice front end for iptables. GUFW being it's graphical counterpart, I don't recommend Firestarter though. In any case the choice is your the final outcome is pretty much the same since they are all controlling the same thing.

Hope this helps.

---

### Post by jramshu on 2011-12-22
> **pulck said:**
> 
4. How can I check if intruders are being effectively fended off by my security measures? I have inspected '/var/log/auth.log' but what am I looking for to see if attacks are being rejected?


Here is an example from my logs:

```
Dec 19 13:59:07 server1 sshd[7697]: Invalid user r00t from 218.232.105.126
Dec 19 13:59:09 server1 sshd[7700]: Invalid user r00t from 218.232.105.126
Dec 19 13:59:32 server1 sshd[7727]: refused connect from 218.232.105.126

Dec 22 03:35:05 server1 sshd[9559]: Did not receive identification string from 75.126.129.21
Dec 22 03:36:41 server1 sshd[9562]: Address 75.126.129.21 maps to experiencecommerce.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Dec 22 03:36:41 server1 sshd[9562]: Invalid user globus from 75.126.129.21
Dec 22 03:36:42 server1 sshd[9565]: Address 75.126.129.21 maps to experiencecommerce.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!

```

Gives you an idea. I reckon I need to check out the website, could be shelled.

---

### Post by azmyth on 2011-12-22
2. Is there a way to use NX Server/Client via SSH tunnel if I disable password authentication on the server? (I've tried everything to get this working, but I cannot log in. If I switch SSH password back on, I can log in no problem)

There's an option in I think in the server.cfg to turn on the nx database. You also have to enable password. From there, you have to add a user to the nx database and set a password. This will bypass the ssh key auth.

---

### Post by pulck on 2011-12-23
> **jramshu said:**
> Here is an example from my logs:

```
Dec 19 13:59:07 server1 sshd[7697]: Invalid user r00t from 218.232.105.126
Dec 19 13:59:09 server1 sshd[7700]: Invalid user r00t from 218.232.105.126
Dec 19 13:59:32 server1 sshd[7727]: refused connect from 218.232.105.126

Dec 22 03:35:05 server1 sshd[9559]: Did not receive identification string from 75.126.129.21
Dec 22 03:36:41 server1 sshd[9562]: Address 75.126.129.21 maps to experiencecommerce.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Dec 22 03:36:41 server1 sshd[9562]: Invalid user globus from 75.126.129.21
Dec 22 03:36:42 server1 sshd[9565]: Address 75.126.129.21 maps to experiencecommerce.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!

```

Gives you an idea. I reckon I need to check out the website, could be shelled.

Thanks, that's helpful. Looks like it's quite clear when someone is trying to break in.

I don't have anything like that in my log... yet. But I've got a lot of lines like this:

```
Dec 23 03:17:01 CRON[19737]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 23 03:17:01 CRON[19737]: pam_unix(cron:session): session closed for user root
```

Any idea what this means?

---

### Post by pulck on 2011-12-23
> **azmyth said:**
> 2. Is there a way to use NX Server/Client via SSH tunnel if I disable password authentication on the server? (I've tried everything to get this working, but I cannot log in. If I switch SSH password back on, I can log in no problem)

There's an option in I think in the server.cfg to turn on the nx database. You also have to enable password. From there, you have to add a user to the nx database and set a password. This will bypass the ssh key auth.

Thanks for this. Have just tried it, but to no avail.

I think I'll try reinstalling NX server and starting again at the beginning.

---

### Post by Lars Noodén on 2011-12-23
> **pulck said:**
> Thanks, that's helpful. Looks like it's quite clear when someone is trying to break in.

I don't have anything like that in my log... yet. But I've got a lot of lines like this:

```
Dec 23 03:17:01 CRON[19737]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 23 03:17:01 CRON[19737]: pam_unix(cron:session): session closed for user root
```

Any idea what this means?

That's just [cron](http://manpages.ubuntu.com/manpages/oneiric/en/man5/crontab.5.html) running.  

As far as the other log goes, the one where you see sshd getting hammered on, you can use iptables to restrict the number of attempts from the same IP number:

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```

---

### Post by azmyth on 2011-12-23
In the server.cfg file set EnableUserDB and EnablePasswordDB to 1.

Then

sudo path/to/nxserver --useradd username
sudo path/to/nxserver --restart

---

### Post by pulck on 2011-12-23
> **Lars Noodén said:**
> That's just [cron](http://manpages.ubuntu.com/manpages/oneiric/en/man5/crontab.5.html) running.  

As far as the other log goes, the one where you see sshd getting hammered on, you can use iptables to restrict the number of attempts from the same IP number:

```

   ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```

Thanks. I think I need to do some reading... the iptables stuff is completely indecipherable to me!

---

### Post by pulck on 2011-12-23
> **azmyth said:**
> In the server.cfg file set EnableUserDB and EnablePasswordDB to 1.

Then

sudo path/to/nxserver --useradd username
sudo path/to/nxserver --restart

I did a reinstall of NX Server first and then followed your instructions and it worked brilliantly. Many thanks!

The fact that NX Server is able to bypass SSH authentication is quite surprising. Does this not mean that NX Server represents something of a security flaw? i.e. could intruders hack into my server simply by guessing my username and password?

Another question... is Wake On Lan possible to do over the internet securely? Ideally I don't want to leave my server up and running 24/7.

---

### Post by azmyth on 2011-12-24
Which version of Nx are you using? I'm using NX 4 and if someone guessed my user and pass then they could get in. Personally I prefer ssh key auth but I couldn't get it to work with NX 4.0. I ran ssh in debug mode and it connected and then it said nxserver times out. I do like NX as it seems the overhead is much lower than x2go and some others.

---

### Post by dirtrider1 on 2011-12-25
I think these are all good points, I just wanted to mention that I think you would benefit greatly from using a VPN. I personally use Openvpn its available in the repos and it works great you can push all the services you want securely over it including Samba shares,ftp,ssh,vnc, web traffic etc. SSH is awesome and it has a lot of the same functionality but I feel Openvpn would provide a better long term and stable solution that would probably be less hassle in the end.

---

### Post by pulck on 2011-12-26
> **dirtrider1 said:**
> I think these are all good points, I just wanted to mention that I think you would benefit greatly from using a VPN. I personally use Openvpn its available in the repos and it works great you can push all the services you want securely over it including Samba shares,ftp,ssh,vnc, web traffic etc. SSH is awesome and it has a lot of the same functionality but I feel Openvpn would provide a better long term and stable solution that would probably be less hassle in the end.

Thanks for the suggestion. Is it as secure as SSH though?

---

### Post by pulck on 2011-12-26
> **azmyth said:**
> Which version of Nx are you using? I'm using NX 4 and if someone guessed my user and pass then they could get in. Personally I prefer ssh key auth but I couldn't get it to work with NX 4.0. I ran ssh in debug mode and it connected and then it said nxserver times out. I do like NX as it seems the overhead is much lower than x2go and some others.

I'm  using NX free edition (v.3.5) - the one that is currently downloadable from the website.

I think enabling DB password makes NX bypass the SSH key. I suppose once you do that, it all comes down to how strong your password is. Doesn't seem to be the most secure system in the world to me. But aren't the alternatives even less secure?

---

### Post by unspawn on 2011-12-27
> **Lars Noodén said:**
> As far as the other log goes, the one where you see sshd getting hammered on, you can use iptables to restrict the number of attempts from the same IP number:
(If the OP only allows SSH for management purposes only access could be tied down to one or more IP addresses or ranges.) IMO it would be more efficient to install fail2ban or any equivalent as it takes care of (un)blocking access through the firewall and logs access violations. 


To advise already given I'd like to add: file system verification using Samhain, Aide or even tripwire (knowing what's on the file system makes it easier to weed out false positives, esp. with distributions that don't allow for fine-grained verification through package management), log reporting using Logwatch, SEC or equivalent (having early warnings at least allows you the chance to deal with threats timely) and *actually testing* the machine remotely, depending on what you run: nmap, Nikto, OpenVAS, etc, etc (should be common sense, how else to know changes work?).

---

### Post by dirtrider1 on 2011-12-27
> **pulck said:**
> Thanks for the suggestion. Is it as secure as SSH though?

Yes it certainly is if not more by default. Openvpn uses SSL/TLS and bidirectional authentication using certificates. All the crypto is handled by the OpenSSL library.

Check out the docs- [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

---

### Post by pulck on 2011-12-28
> **dirtrider1 said:**
> Yes it certainly is if not more by default. Openvpn uses SSL/TLS and bidirectional authentication using certificates. All the crypto is handled by the OpenSSL library.

Check out the docs- [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

Thanks. I will have a good look at VPN as well then.

Will also look at the different Firewall/iptable options. My previous experience with Firewalls has not been good, but then this is a server so setting it up correctly is more critical this time round.

Would still like to be able to wake the machine up remotely though, if possible. Is this something which can be done securely?

---

### Post by Lars Noodén on 2011-12-28
> **pulck said:**
> Would still like to be able to wake the machine up remotely though, if possible. Is this something which can be done securely?

[Wake-On-LAN](https://help.ubuntu.com/community/WakeOnLan) can be done, but only from another machine on the local area network.

---

### Post by pulck on 2011-12-28
> **Lars Noodén said:**
> [Wake-On-LAN](https://help.ubuntu.com/community/WakeOnLan) can be done, but only from another machine on the local area network.

Ah, okay. Had thought that it was possible over the internet.

---

### Post by Lars Noodén on 2011-12-28
It looks like you might be able to do it if your router supports DD-WRT 

[http://www.dd-wrt.com/wiki/index.php/WOL](http://www.dd-wrt.com/wiki/index.php/WOL)

or, obviously, any other form of Linux.

---

