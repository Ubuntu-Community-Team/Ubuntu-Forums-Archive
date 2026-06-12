---
title: "ssh hack attempt.."
date: 2005-04-14
forum: Server Platforms
---

### Post by CrustyDOD on 2005-04-14
hey

I checked Firestarter and i saw someone trying to loggin into ssh server. Then i did a lookup hostnames and it was from asia somewhere i think..

I stopped SSH, edited /etc/ssh/sshd_config and set PermitRootLogin to No..

restarted SSH and then i went into System Log Viewer to check if my hunch was correct.. it was!

localhost sshd[18200] Invalid user anonymous from ::ffff:210.86.143.194
localhost sshd[18204] Invalid user bruce from ::ffff:210.86.143.194
localhost sshd[18207] Invalid user chuck from ::ffff:210.86.143.194
localhost sshd[18210] Invalid user darkman from ::ffff:210.86.143.194
localhost sshd[18214] Invalid user hostmaster from ::ffff:210.86.143.194
localhost sshd[18217] Invalid user jeffrey from ::ffff:210.86.143.194
localhost sshd[18220] Invalid user loverd from ::ffff:210.86.143.194
localhost sshd[18223] Invalid user eric from ::ffff:210.86.143.194
localhost sshd[18227] Invalid user lauren from ::ffff:210.86.143.194
localhost sshd[18229] Invalid user mark from ::ffff:210.86.143.194
localhost sshd[18231] Invalid user sin from ::ffff:210.86.143.194
localhost sshd[18235] Invalid user richer from ::ffff:210.86.143.194
localhost sshd[18238] Invalid user fluffy from ::ffff:210.86.143.194
localhost sshd[18241] Invalid user gold from ::ffff:210.86.143.194
localhost sshd[18244] Invalid user tomcat from ::ffff:210.86.143.194
localhost sshd[18248] Invalid user cosinus from ::ffff:210.86.143.194
localhost sshd[18250] Invalid user httpd from ::ffff:210.86.143.194
localhost sshd[18254] Invalid user squirrelmail from ::ffff:210.86.143.194
localhost sshd[18257] Invalid user trash from ::ffff:210.86.143.194
localhost sshd[18259] Invalid user kent from ::ffff:210.86.143.194
localhost sshd[18263] Invalid user ace from ::ffff:210.86.143.194
...

This is just about 10% of his tries to login, lot more tries were logged!!

My questions is:
I changed permit root login to No and that's it. Is there anything else that's should be set to No..

And most important question, how in the earth do i kill a user when he's trying to login into SSH?
Is there a command for this? something like: kill user/ip/..??
Cause restarting SSH server to get him disconnected is just stupid :)

---

### Post by ebrowne on 2005-04-14
Hey, You may want to also what to change the following
UsePAM no
RSAAuthentication yes
PubkeyAuthentication yes 

Before you make this change make sure that your users have a Public Key and know how to use them to login.  If your realy paraniod you can add the range of IPs to /etc/hosts.deny

---

### Post by p!=f on 2005-04-14
```

[~] > whois 210.86.143.194

```
gaves that address belongs some company in Thailand / Bangkok. There're also some email addresses mentioned so you may try to write them a question what that supposed to be.
Another advice is to install snort and acidlab (web server & php & mysql required)
```

snort - Flexible Network Intrusion Detection System
acidlab - Analysis Console for Intrusion Databases

```
to get more informations.
If you're running firewall (you should in this case :)) you might want to blacklist that ipaddress.
Hope it helps.
EDIT: Typos.

---

### Post by p!=f on 2005-04-14
[QUOTE=ebrowne]
If your realy paraniod you can add the range of IPs to /etc/hosts.deny[/QUOTE]
Just a note: /etc/hosts.deny will only work if ssh server runs under [tcpwrappers](http://www.clug.org/presentations/security/tcpwrappers.html) which, correct me if wrong, does not by default.

---

### Post by CrustyDOD on 2005-04-14
[QUOTE=ebrowne]
UsePAM no
RSAAuthentication yes
PubkeyAuthentication yes 
[/QUOTE]
Did change the first one, other two were already set..
Thx for tips..

[QUOTE=p!=f]gaves that address belongs some company in Thailand / Bangkok. There're also some email addresses mention so you may try to write them a question what that supposed to be.[/QUOTE]
Already did :)

[QUOTE=p!=f]
Another advice is to install snort and acidlab (web server & php & mysql required)
[/QUOTE]
Any configuration needed? I had snort installed on Warty but all i did was install it and that was it..

Oh and i also blocked that ip :)

So i guess there is no way to kill someone manually if he's trying to access my box?

---

### Post by p!=f on 2005-04-14
[QUOTE=CrustyDOD]
Any configuration needed? I had snort installed on Warty but all i did was install it and that was it..
[/quote]
There's no need tu run mysql and acidlab if you're happy with the "plain-vanilla" snort. However, with [AcidLab](http://acidlab.sourceforge.net/) you get more informations in a nice web interface.
[quote=CrustyDOD]
So i guess there is no way to kill someone manually if he's trying to access my box?[/QUOTE]
Actually, there is no connection made so there's nothing to kill (invalid usernames). For a nice write-up about TCP/IP (scroll down to "Opening a TCP connection") click [here](http://www.scit.wlv.ac.uk/~jphb/comms/tcp.html).
If you want to experiment try to deploy honeynet (google to get plenty of informations) to try to catch that spammer. ;)

---

### Post by az on 2005-04-14
An intrusion detection system scans your logs for this kind of thing and blocks access to those Ip addresses for a period of time.

Do these attempts occurr at random or when you do things like visit certain internet sites through a web browser?

---

### Post by jdong on 2005-04-14
[QUOTE=azz]An intrusion detection system scans your logs for this kind of thing and blocks access to those Ip addresses for a period of time.[/QUOTE]

Actually, you're talking about a **Network** Intrusion **Prevention** system. An Intrusion detection system is (in the non-BlackICE world) usually thought of as a:

1) **Network Intrusion Detection System** -- Like snort, logs suspicious activity over the network using more complicated, heuristics rules. Usually a method for sysadmins to monitor networks for suspicious activities. It requires meticulous tweaking and monitoring in order to be effective. Usually, there is no 'active response' -- that is, the NIDS does nothing to prevent an attack or to stop one; just to log that it's occurred. Nonetheless, the most difficult part about recovering from an intrusion is **realizing you've been intruded**. :)

2. **HOST Intrusion Detection System** -- like Tripwire, monitors critical files on your system for modification, and notifies sysadmins when files are modified. Useful for notifying you that you've been compromised, but does nothing to proactively defend your system. Like noted above, detecting an intrusion is the hardest part of recovering from an attack.



SSH scans (like the ones you've logged) are extremely common nowadays. They really cause no harm, unless you have passwordless user accounts or REALLY short passwords. Since SSH forces a 5-second (or more) pause between password retries, brute-forcing a 5+character password is practically an impossible task.

Also, avoid really common usernames (like the ones it's trying to probe!)

---

### Post by CrustyDOD on 2005-04-15
azz: Nah it was the first time it happened and no sites were open..

I think some asian girl is just pissed at me cause i didn't send her flowers  :grin:

---

### Post by ubuntu_demon on 2005-04-15
[QUOTE=ebrowne]Hey, You may want to also what to change the following
UsePAM no
RSAAuthentication yes
PubkeyAuthentication yes 

Before you make this change make sure that your users have a Public Key and know how to use them to login.  If your realy paraniod you can add the range of IPs to /etc/hosts.deny[/QUOTE]
 what is this "UsePAM no" option can you give more information about it ?

So the standard configuration of ssh is safe enough except PermitRootLogin and UsePAM ?

---

### Post by speedman on 2005-04-15
Definitions of configuration variables for the ssh daemon can be found in man sshd_config.

Script kiddies typically scan a range of IPs looking for ssh on it's assigned port, which is 22.  Rarely do they bother to scan the complete range of 65535 TCP ports for a block of IPs as it is too time consuming.  As such, it's a good idea to configure ssh to listen on a non standard port to obfuscate it's presence.

Example:

sudo vi /etc/ssh/sshd_config

... and change:

Port 22

... to something non assigned like:

Port 39174

... then:

sudo /etc/init.d/ssh restart

The following syntax would then be required to ssh, or scp to the system:

ssh -p39174 user@host

scp -P39174 /local/path/to/file user@host:


Regards,

speedman

---

### Post by ebrowne on 2005-04-15
Hey,
It's not that UsePAM is insecure but if you turn it off it forces your users to have a Public Key to authenticate.  Anyone trying to access ssh without a key is denyed.

---

### Post by speedman on 2005-04-15
[QUOTE=ebrowne]It's not that UsePAM is insecure but if you turn it off it forces your users to have a Public Key to authenticate.  Anyone trying to access ssh without a key is denyed.[/QUOTE]

Unless somebody enables:

PasswordAuthentication yes

... in sshd_config, which would still permit password auth for logins.  Fortunately the default for this option is "no".


Regards,

SM

---

### Post by vague- on 2005-04-15
That namelist looks similar to one that hit my server about a week or so back.  I would not worry too much, stuff like this happens all the time.  If you do not want (or cannot) force all your users to use public key authentication, then just make sure they have good passwords - in as far as you can.  There are libraries you can plug in for PAM that will do rough checks on the approximate strength of a password at the time it is set - they do a reasonable job of detecting obvious passwords, trust me it annoyed a lot of users as it kept refusing their crap passwords :)...of course, they just try to get away with the simplest password that beats the checker, but at least it is usually better than what they were trying.

---

### Post by ubuntu_demon on 2005-04-15
But if you have the option "usepam no" then you can't login from anywhere anymore. Or you have to write down the private key on a piece of paper. But that's a long key isn't it ?

How do you guys do this in practice ?

---

### Post by speedman on 2005-04-15
man ssh-keygen has all the information you need demon.

You can also check here for more assistance:

[http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=ssh-keygen+howto](http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=ssh-keygen+howto)


Regards,

SM

---

### Post by ubuntu_demon on 2005-04-15
[QUOTE=speedman]man ssh-keygen has all the information you need demon.

You can also check here for more assistance:

[http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=ssh-keygen+howto](http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=ssh-keygen+howto)


Regards,

SM[/QUOTE]
 sorry I was a bit lazy. But I was especially wanting to know your settings/thoughts and stuff.

But in my case I have a gateway/server at home I want to be able to login from anywhere. The piece of paper method sucks and I don't have an usb key. I think I'll manage with a normal password.

---

### Post by dataw0lf on 2005-04-15
[QUOTE=speedman]Definitions of configuration variables for the ssh daemon can be found in man sshd_config.

Script kiddies typically scan a range of IPs looking for ssh on it's assigned port, which is 22.  Rarely do they bother to scan the complete range of 65535 TCP ports for a block of IPs as it is too time consuming.  As such, it's a good idea to configure ssh to listen on a non standard port to obfuscate it's presence.

Example:

sudo vi /etc/ssh/sshd_config

... and change:

Port 22

... to something non assigned like:

Port 39174

... then:

sudo /etc/init.d/ssh restart

The following syntax would then be required to ssh, or scp to the system:

ssh -p39174 user@host

scp -P39174 /local/path/to/file user@host:


Regards,

speedman[/QUOTE]

This is a decent idea: it'll certainly cut down on the random scans you'll encounter day to day.  However, I'd like to let the 'newbies' here know that it doesn't make your server 'secure' by changing the port.  Security through obscurity is generally not a good idea.
Still, with ssh, it isn't a bad idea;  as I said, it will cut down on the number of brute force scans you'll receive.

---

