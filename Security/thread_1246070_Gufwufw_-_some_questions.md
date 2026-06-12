---
title: "Gufw/ufw - some questions"
date: 2009-08-21
forum: Security
---

### Post by oygle on 2009-08-21
I have recently changed from Firestarter to Gufw, and would like to know a bit more about Gufw/ufw please.

1. Is ufw started automatically upon boot ?

2.  Does either Gufw or ufw need to be running at all, as they are only used to adjust the iptables rules aren't they ?

3. Does iptables run by default ? The reason I ask this is because upon boot today, I could see no intrusions in the syslogs, which normally has quite a few of course.

4. The firewall did not seem to be "enabled" until I did this ..

```

ufw default deny

```

and then ran Gufw.

5.  If the firewall was not enabled, how can I tell if there were any attempts to hack into the computer ? (File auth.log only shows the commands I have run from the terminal).

There seems to be no documentation for Gufw.

Oygle

---

### Post by automaton26 on 2009-08-21
1. Should be, yes - if you press ESC during boot, you should see ufw being started.

2. ufw is just a configuration utility for iptables, so I don't think ufw has to be running but it does by default. gufw is just a UI front-end for ufw, so that only runs when you run it under the desktop.

3. Yes, and I think iptables allows all by default: [https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

4. I had problems when going from firestarter/guarddog back to the default ufw - make sure you purged firestarter properly, and check "sudo ufw status" after a reboot.

[INDENT][http://ubuntuforums.org/showthread.php?t=1221868#9]("http://ubuntuforums.org/showthread.php?t=1221868#9")[/INDENT]

5. Haven't investigated logging myself yet, sorry.

---

### Post by oygle on 2009-08-21
automaton26 - Thanks for your replies, most helpful.

I have done this, and no rules via GUFW.

```

~$ sudo ufw enable
[sudo] password for xxxxxxxx: 
Firewall is active and enabled on system startup
~$ sudo ufw status
Status: active

```

and started to see some attempts in the syslog a while later. Previously there were none there, so I have to assume that prior to the 'enable', all ports were 'open' to incoming (gulp).

I did run tiger, and everything looks okay.

Thanks,

Oygle

---

### Post by automaton26 on 2009-08-21
Great.

Somebody else might clarify this, but I think all ports would still have been closed. I was behind a router with a static IP, and I always have a strong random password, so I hope I wasn't briefly exposed either :)

---

### Post by The Cog on 2009-08-21
You can always see what iptables rules are in place with this command:
**sudo iptables -nvL**
and a fully open system looks like this:
```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

```
You need not worry about firewall rules at all unless you install a server such as openssh-server because a default Ubuntu install isn't listening for incoming connections anyway, so all ports are closed. 

Even if you install a server of some sort, unless you have a specific firewall requirement such as only allowing certain IP addresses to connect then isntalling a firwall is pointless. After installing it (which would block access to your service), you will just have to reconfigure it to allow that service through again. Like building a wall just so you can knock a doorway through it.

---

### Post by automaton26 on 2009-08-21
Thanks, Cog - that makes sense.

It sounds like someone would have to make quite specific changes to expose a default Ubuntu installation then.

But I still wish Gufw was part of the default (K)ubuntu installation, then ex-Windows users like me would be less likely to monkey around with firestarter/guarddog, and end up conflicting with ufw :)

---

### Post by cariboo on 2009-08-21
In a default installation, there is nothing listening on any ports, except for cups on port 631, and that can only be accessed locally.

If you are behind a router, there really isn't any need for a firewall at all. I've been running without a firewall on any of my computers for the last 8 years, and haven't encountered any problems yet. :)

---

### Post by oygle on 2009-08-22
> **The Cog said:**
> You can always see what iptables rules are in place with this command:
**sudo iptables -nvL**
and a fully open system looks like this:
```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

The output I can see is slightly different, I guess because iptables + UFW = new set of iptables, or something like that. Anyway, here is the first one ..

```

sudo iptables -nvL
Chain INPUT (policy DROP 3 packets, 152 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1579 1073K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1579 1073K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10   908 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10   908 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10   908 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0    

```

and when I look in syslog, there have been 3 INPUTs dropped.
> **The Cog said:**
> 
You need not worry about firewall rules at all unless you install a server such as openssh-server because a default Ubuntu install isn't listening for incoming connections anyway, so all ports are closed. 


Okay, UFW is slightly different than Firestarter. With Firestarter it was all INPUT closed, and I always had to go and define a rule for every port that I wanted to use for OUTPUT. For example, port 110 for POP3, etc, etc.

With UFW, it is all INPUT are closed (because I specified 'ufw default deny'), **but** it seems all OUTPUT are open with UFW. I haven't had to define any rules at all, as you say.

Thanks,

Oygle

---

### Post by bodhi.zazen on 2009-08-22
Filtering output is much more complex then input and in general there is no need.

All outgoing connections are imitated by you and so there is no reason to block them.

The only reason to block outgoing connections would be to limit escalation of privileges on a system that has already been cracked or to prevent applications / spyware to "hone home".

In the first case, a firewall will do little to help, and in the second there are none known.

If you wish to filter outgoing connections you are best off, IMO, learning iptables or using an alternate tool such as shorewall or a router specific distro.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

What is it exactly you are wanting to filter on the outgoing side ? If you do not know the answer to that question you can almost certainly skip it.

FYI Avahi is also listening. [Avahi Home Page]("http://bodhizazen.net/Tutorials/iptables/avahi%20=%20http://avahi.org")

I typically disable Avahi and bluetooth on my installs. although Avahi complains that it will cause breakage or problems it will not hurt anything to disable it. If you need it , re-enable it.

If you do not know what it is you probably do not use it.

---

### Post by oygle on 2009-08-24
> **bodhi.zazen said:**
> Filtering output is much more complex then input and in general there is no need.

Okay, having used Firestarter since i first used Ubuntu, it (Firestarter) blocked all input and all output, and so I only had to open the ports for OUTPUT , that I needed.

With GUFW/UFW, it is different. I can do a 'deny all', which only denies all INPUT, and it opens all OUTPUT ports. In fact, although I have GUFW/UFW set to 'enable' and 'default deny', it appears that UFW is not set to 'default deny' upon each boot. I have to enter it in the terminal, and then I can see INPUT's being blocked ??

> **bodhi.zazen said:**
> 
All outgoing connections are imitated by you and so there is no reason to block them.


I would prefer to only open the OUTPUT ports that I use, that way I can tell if there is an unsolicited program trying to open an OUTPUT port.

> **bodhi.zazen said:**
> If you wish to filter outgoing connections you are best off, IMO, learning iptables or using an alternate tool such as shorewall or a router specific distro.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)


Thanks for the link. I really only want to use a gui like GUFW to setup a few rules, but it seems I don't even need to, with UFW.

> **bodhi.zazen said:**
> 
What is it exactly you are wanting to filter on the outgoing side ? If you do not know the answer to that question you can almost certainly skip it.


I would prefer to only open the ports I use, which is maybe, only 10 or 12 at the most.

> **bodhi.zazen said:**
> 
FYI Avahi is also listening. [Avahi Home Page]("http://bodhizazen.net/Tutorials/iptables/avahi%20=%20http://avahi.org")

I typically disable Avahi and bluetooth on my installs. although Avahi complains that it will cause breakage or problems it will not hurt anything to disable it. If you need it , re-enable it.

If you do not know what it is you probably do not use it.

Yes, I do not know what Avahi does, so I won't worry about it.

Thanks,

Oygle

---

### Post by bodhi.zazen on 2009-08-24
Well, that is not the way outgoing ports work.

Let us assume you are using firefox to a server , foo.com

Firefox will use an unprivilaged, pseudo random port to connect to port 80 on the server.

Open firefox, and a few other network programs, connect to a few servers, and check your ports.

You would handle this in iptables by specifying the destination port, ie the port on the server, not the soruce port, ie the port on your server.

Same with wget, curl, etc.

So once you open all the ports on your client, any malware would use the same ports.

So you can not really accomplish your goals with iptables or a firewall. 

The closest thing to an application firewall would be something like apparmor, but you would need to run a restricted shell, but even then, you would need to know the malware.

Malware of the type you are trying to guard against does not exist in Linux and if your system is cracked these measures add little, if anything, to any meaningful defense.

Basically, in a nutshell, on the outgoing side, if you let firefox out you will be letting everything else out as well. You can not restrict outbound traffic to firefox and not wget, curl, or any other application with a firewall (in linux).

I understand Windows has an application level firewall, but it is easily circumvented.

---

### Post by oygle on 2009-08-25
> **bodhi.zazen said:**
> 
Let us assume you are using firefox to a server , foo.com

Firefox will use an unprivilaged, pseudo random port to connect to port 80 on the server.

Open firefox, and a few other network programs, connect to a few servers, and check your ports.


Yes, I understand this, thanks.

> **bodhi.zazen said:**
> 
You would handle this in iptables by specifying the destination port, ie the port on the server, not the source port, ie the port on your server.

Same with wget, curl, etc.


Yes, but iptables should not have (for example) port 80 (destination) open, as I have not specified it in GUFW/UFW, **yet** I can access web pages. This is the problem with GUFW/UFW, it seems to have all destination ports open, even though I have done this

```

~$ sudo ufw enable
~$ sudo ufw default deny

```

and GUFW is running, and the applet is displayed with 'enabled' and 'deny all'. My question is, surely with 'deny all' I would have to specify which destination ports are 'allowed'.

Here are some of the rules (destination ports allowed) that were used in Firestarter

> 
DNS, 53, firewall,
HTTP, 80, firewall,
SMTP, 25, firewall,
POP3, 110, firewall,
HTTPS, 443, firewall,


Yet, I don't have to specify any ports at all in GUFW/UFW, even though the default is "deny" ?  Here is what one site says about the use of the 'default' command (use either 'accept or 'deny')

> 
Accept or drop incoming packets to (can see what services are available with ’status’ (see below)). can be specified via service name in /etc/services, ‘protocol:port’, or via package meta-data. ‘allow’ adds service entry to /etc/ufw/maps and ‘deny’ removes service entry from /etc/ufw/maps.


So, the 'deny' only drops incoming packets, and does not make provision for specifying which destination ports are allowed (part of services).

> **bodhi.zazen said:**
> 
So once you open all the ports on your client, any malware would use the same ports.


No, I have not opened all the ports on the client, all ports _should_ be closed, as I have used "default deny" in GUFW/UFW.

> **bodhi.zazen said:**
> 
The closest thing to an application firewall would be something like apparmor, but you would need to run a restricted shell, but even then, you would need to know the malware.


It is not my objective to use an application firewall.

> **bodhi.zazen said:**
> 
Basically, in a nutshell, on the outgoing side, if you let firefox out you will be letting everything else out as well. You can not restrict outbound traffic to firefox and not wget, curl, or any other application with a firewall (in linux).


The above is true for port 80 of course, and that is port 80 on the destination (server). I had to open these ports with Firestarter, but GUFW/UFW appears to have **ALL** destination ports open.

I do not wish to have a firewall do this, of course, very dangerous.

Thanks,

Oygle

---

### Post by bodhi.zazen on 2009-08-25
It is not "very dangerous" and I do not think you understand firewalls. This is not windoes and there are not programs that "phone home". In addition, by time you allow traffic to (destination) ports 21,22,25,53,80, and 443 any malware you feel you are blocking can now use those ports for whatever they wish. Malware does not use exotic destination ports (well you may be able to find and example of a few, but the vast majority will use the default ports).

Back to the technical discussion,

At any rate, how did you remove firestarter ? You need to purge all the firestarter config files or they conflict with ufw/gufw.

```
sudo apt-get remove --purge firestarter
```

Of course you may need to re-isntall firestarter to then purge it.

Second, no , by default UFW does not block outgoing traffic. So default deny will not affect outgoing traffic. You will need an alternate config tool or write iptables rules yourself. If you write rules yourself you will need to edit them into the ufw config files.

See : [Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

Again, as I said earlier, in the time you have spent on this you could have written a few simple rules for iptables and be done with it.

```
# Add in any other ports you wish:
sudo iptables -A OUTPUT -p -tcp -m multiport --dport 80,443 -j ACCEPT
sudo iptables -A OUTPUT -p -udp --dport 53 -j ACCEPT
sudo iptables -A OUTPUT -j DROP
```

iptables is not *that* complicated and what you are doing is rather straight forward.

---

### Post by oygle on 2009-08-27
> **bodhi.zazen said:**
> In addition, by time you allow traffic to (destination) ports 21,22,25,53,80, and 443 any malware you feel you are blocking can now use those ports for whatever they wish. Malware does not use exotic destination ports (well you may be able to find and example of a few, but the vast majority will use the default ports).


If I had malware on the computer, the above would be an issue, however I don't have malware. Destination ports need to be open anyway, for example, how would a person use a web browser without allowing destination port 80 ?

> **bodhi.zazen said:**
> 
At any rate, how did you remove firestarter ?

With the following ..

```
sudo apt-get remove --purge firestarter
```

> **bodhi.zazen said:**
> 
Second, no , by default UFW does not block outgoing traffic. So default deny will not affect outgoing traffic.


Okay, so the following command ..

```

sudo ufw default deny

```

doesn't affect outgoing traffic ?  What does UFW 'deny' then, with this command ?

> **bodhi.zazen said:**
> 
You will need an alternate config tool or write iptables rules yourself. If you write rules yourself you will need to edit them into the ufw config files.


That seems addition work, which I don't want, that is why I wanted to use a GUI for the firewall. It seems if I use UFW, it will update iptables, and if I write my own iptables rules and don't use UFW, then it is less work than writing my own iptables rules plus using UFW (.. the additional work method).

> **bodhi.zazen said:**
> 
.. in the time you have spent on this you could have written a few simple rules for iptables and be done with it.


Using a gui for the firewall (e.g firestarter or gufw, etc) should negate the need for me to ever be concerned about iptables. I really don't want to spend the time fiddling about with iptables, when a gui _should_ save me the time, plus the learning curve.

> **bodhi.zazen said:**
> 
```
# Add in any other ports you wish:
sudo iptables -A OUTPUT -p -tcp -m multiport --dport 80,443 -j ACCEPT
sudo iptables -A OUTPUT -p -udp --dport 53 -j ACCEPT
sudo iptables -A OUTPUT -j DROP
```


Thanks for supplying that code. I assume it accepts ports 80, 443 and 53 OUTPUT (destination), and DROPs all other destination ports.

> **bodhi.zazen said:**
> 
iptables is not *that* complicated and what you are doing is rather straight forward.

Yes, I'm sure iptables is not that complicated for people who know what they are doing, or for people who wish to spend time learning Linux commands. I have learning difficulties and cognitive disabilities, so it is not the same for all people. ;)

Thanks,

Oygle

---

### Post by bodhi.zazen on 2009-08-27
Well, you can't have your cake and eat it too.

Either you are going to go with the defaults or you are going to learn how to firewall. Learning how to firewall is complex, GUI or no. It is a very common problem with say Shorewall, in fact their documentation even warns against locking yourself out (from a remote server) if you do not know what you are doing.

After learning this myself I will tell you , you need a fair amount of background information about general networking and networking protocols. If you have the requisite knowledge, the iptables commands are quite simple. If you do not, the GUI tools are complex.

If you want an easy way to configure  your firewall, use either ufw or gufw. Both are default and both are configured by people who konw what they are doing.

The easiest way is in fact ufw, two commands and you are done.

```
sudo ufw enable
sudo ufw default deny
```

If you choose to go further then please allow me to point you in the right direction.

Let us simplify your firewall. You are not installing a router or virtualization, so not port forwarding or NAT.

You have 2 tables, input and output. You can accept or deny (drop) packets or traffic.

If you set the default policy to drop all input you will have not internet connection. Same if you drop all output.

Now look at the tcp protocol. You send a request for a web page. You want that traffic to go through. So you accept outgoing traffic and related incoming traffic (you allow the response to the request back in).

So if you look at the defaults, with ufw default deny, what happens /

On the output side, all traffic is allowed.

On the input side, all traffic related to your requests is allowed, but all attempts at a new connection is denied. This is what default deny means, all attempts to establish a new connection (with your box acting as a server) are dropped. All connections you initiate (your computer is acting as a client) are accepted.

Now if you wish to understand and modify the default behavior, you will have to look at the rules.

Do this with :

```
sudo iptables -L -v
```

Look up each rule and what it is doing.

In terms of your desire to block OUTPUT, buy your own admission, this is much to do about nothing. Setting rules for OUTPUT is more "advanced" and really does nothing to increase your security. 

As you say, either:

1. There is no malware on your computer to block, so nothing is gained.

2. You do have or acquire malware, in which case the rules you write for OUTPUT will not protect you, so again nothing is gained.

So learn as much or as little as you want about your firewall. If it is too complicated for you there is really no reason to go with anything but the defaults. The defaults are quite well written and it will take you many hours to improve on them. Most of the improvements would be rather esoteric iptables rules or logging.

If you wish to increase your security, learn to use Apparmor or take a look at the security sticky.

---

### Post by oygle on 2009-09-07
> **bodhi.zazen said:**
> If you want an easy way to configure  your firewall, use either ufw or gufw. Both are default and both are configured by people who konw what they are doing.

The easiest way is in fact ufw, two commands and you are done.

```
sudo ufw enable
sudo ufw default deny
```


I uninstalled gufw, as it wasn't doing anything (no rules specified), and also each time I booted, it forced me to enter the sudo pwd each time, so it was a pain, and doing nothing, therefore I removed it.

I still have ufw, although one thing puzzles me. I have to enter the 2 commands as you have posted above, before the syslogs show any attempted intrusions. It seems as if every port is 'open' (INPUT) until I 'enable' ufw. Or, it could be just co-incidence that no attempted intrusions 'happen' for a while after boot. I don't know, it's puzzling.

> **bodhi.zazen said:**
> 
If you choose to go further then please allow me to point you in the right direction.

Okay, thanks. If the iptables commands are not _too_ hard for me, I'd rather just use them. My needs are simple, I just use http, https, smtp, pop3, sftp and a few other ports.

I also use ICS (internet connection sharing), across the lan, to use another Ubuntu computer, so that IP (192.168.nnn.nnn) needs to be allowed access.

Also, I tried samba and it was a bit painful between 2 Ubuntu computers, I would like to get that going. It seems a simple approach is posted [here - post #17]("http://ubuntuforums.org/showthread.php?t=1014509&page=2") . I'm mentioning this, because it will no doubt affect how iptables is set up.

> **bodhi.zazen said:**
> 
Let us simplify your firewall. You are not installing a router or virtualization, so not port forwarding or NAT.


Correct, and I don't have a (hardware) router either, as I use a USB dongle to connect with wireless broadband. That said, I thought iptables, in it's basic form, was a NAT firewall ??

> **bodhi.zazen said:**
> 
You have 2 tables, input and output. You can accept or deny (drop) packets or traffic.

If you set the default policy to drop all input you will have not internet connection. Same if you drop all output.


Now, this I don't understand. With Firestarter, all INPUT was denied, and I only allowed OUTPUT for a few ports (80, 110, etc).

> **bodhi.zazen said:**
> 
Now look at the tcp protocol. You send a request for a web page. You want that traffic to go through. So you accept outgoing traffic and related incoming traffic (you allow the response to the request back in).


Okay, port 80 out, and related incoming traffic assigned to some random port. This is what I thought NAT was, that no incoming traffic can happen, unless there is first a request (in this example) for a web page. It had to be initiated from this computer.

> **bodhi.zazen said:**
> 
So if you look at the defaults, with ufw default deny, what happens /

On the output side, all traffic is allowed.

On the input side, all traffic related to your requests is allowed, but all attempts at a new connection is denied. This is what default deny means, all attempts to establish a new connection (with your box acting as a server) are dropped. All connections you initiate (your computer is acting as a client) are accepted.


Okay, I _think_ I understand what you are saying.

> **bodhi.zazen said:**
> 
Now if you wish to understand and modify the default behavior, you will have to look at the rules.

Do this with :

```
sudo iptables -L -v
```

Look up each rule and what it is doing.


There are many rules there, if each rule is a 'chain'. Is it 'safe' to post the contents of my iptables ??

> **bodhi.zazen said:**
> 
In terms of your desire to block OUTPUT, buy your own admission, this is much to do about nothing. Setting rules for OUTPUT is more "advanced" and really does nothing to increase your security. 

As you say, either:

1. There is no malware on your computer to block, so nothing is gained.

2. You do have or acquire malware, in which case the rules you write for OUTPUT will not protect you, so again nothing is gained.

So learn as much or as little as you want about your firewall. If it is too complicated for you there is really no reason to go with anything but the defaults. The defaults are quite well written and it will take you many hours to improve on them. Most of the improvements would be rather esoteric iptables rules or logging.

If you wish to increase your security, learn to use Apparmor or take a look at the security sticky.

Thanks, I might have a look at Apparmor. I use 'no script' with Firefox, and I don't download files, nor receive email attachments. Cookies and browser cache are cleared after closing firefox, and I only visit safe and reputable websites. I actually thought the need for any 'anti-malware' tools was unecessary with Ubuntu (see [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812"). I do have tiger installed and it finds nothing, except a few warnings. I did have WINE installed but uninstalled it completely, and the only program I did run under it was Pegasus mail.

Thanks for your help,

Oygle

---

### Post by rookcifer on 2009-09-07
> **oygle said:**
> 
Thanks, I might have a look at Apparmor. I use 'no script' with Firefox, and I don't download files, nor receive email attachments. Cookies and browser cache are cleared after closing firefox, and I only visit safe and reputable websites. I actually thought the need for any 'anti-malware' tools was unecessary with Ubuntu (see [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812").


Anti-malware software *is* unnecessary in Ubuntu.  AppArmor is not "anti-malware" software.  It is a [Mandatory Access Control]("http://en.wikipedia.org/wiki/Mandatory_access_control") system that utilizes the [LSM]("http://en.wikipedia.org/wiki/Linux_Security_Modules") hooks and calls in the kernel.  However, AppArmor will certainly act as "anti-malware" software if its configured properly.  In fact, MAC systems like AppArmor and SeLinux are *far* superior to any old-fashioned and obsolete "anti-virus" software that is peddled by unscrupulous companies to unsuspecting computer users.

---

### Post by oygle on 2009-09-08
Thanks, I will definitely install AppArmor.  :)

---

### Post by ybres on 2009-09-09
I have read the topic and would like a conclusion. Lets say I am a home user with an open internet connection (NO router) and would like to be secure using an easy GUI application...
1. Should I install Gufw (deny all + rules for http, shh, skype, dc++) or I would be better off without any firewall.
2. If I will use Gufw should I check that it opens at every session and it is present in the task bar, or just open it once so it configures iptables and the close it?

Thank you for your time! :)

---

### Post by bodhi.zazen on 2009-09-09
> **ybres said:**
> I have read the topic and would like a conclusion. Lets say I am a home user with an open internet connection (NO router) and would like to be secure using an easy GUI application...
1. Should I install Gufw (deny all + rules for http, shh, skype, dc++) or I would be better off without any firewall.
2. If I will use Gufw should I check that it opens at every session and it is present in the task bar, or just open it once so it configures iptables and the close it?

Thank you for your time! :)

Well only you can decide your comfort level and what you want to do with the information.

I suggest that security is not simply installing some gui tool and forgetting about it, this approach is not much better then doing nothing.

If you do not want to be bothered, Ubuntu out of the box is more secure then a Hardened installation of Windows and that may be sufficient for your needs.

If you wish to go beyond that, start with the stickies : 
 
[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

There is a reason they are stickies :p

A firewall is a tool, you install it because you wish to do something with it.

I advise you open a terminal and type two commands:

```
sudo ufw enable
sudo ufw default deny
```

If that is more then you are willing to do then just go with the defaults.

---

### Post by ybres on 2009-09-09
Thank you for the post. I see what you are saying... :D There is nothing I am not willing to do for medium security.
Using that command will ufw stay enabled after every restart?
sudo ufw default deny - means that all ports are blocked by default right?
Will i have to separately allow access to firefox, skype or dc++, or will they just open a port and the close it after?

Thank you again.

---

### Post by bodhi.zazen on 2009-09-09
Yes, your firewall will remain active, even if you reboot, until you disable it 

You disable it with :

```
sudo ufw disable
```

In terms of "open ports" your concept of how they work is a bit off.

By default there are no open ports, so unless you install a server, there is nothing to firewall.

Second, traffic is divided into outgoing and incoming. Those settings I have you allow all outgoing traffic.

Incoming traffic is divided into new and established connections. Those settings block all new connections but allow all established connections.

So when you start firefox (or any other client) the outgoing request is allowed, and the incoming (established) response is also allowed.

This is not opening a port.

If you want to learn the gory details, you will need to be willing to read.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by oygle on 2009-09-10
> **bodhi.zazen said:**
> Yes, your firewall will remain active, even if you reboot, until you disable it 

I find that I have to do this after each boot, for the firewall to 'work'.

```

sudo ufw enable
sudo ufw default deny

```

If I do not issue those commands, there are no entries in syslogs to show attempted intrusions. If I do enter those 2 commands, syslogs show the attempts.

Just why this is so, I have no idea ??

Oygle

---

### Post by bodhi.zazen on 2009-09-10
> **oygle said:**
> If I do not issue those commands, there are no entries in syslogs to show attempted intrusions. If I do enter those 2 commands, syslogs show the attempts.

Just why this is so, I have no idea ??

Oygle

I am not sure about that. Did you have other applications installed that change your rules / preferences ? Are or did you run GUFW ? If so make sure logging is enabled in GUFW.

Personally I use IPTables directly :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

I understand it takes some time to learn, but once you do it is very straight forward :twisted:

Also I do not log packets that are dropped via iptables, it fills the logs and I drop literally thousands of packets and filling the logs just makes them harder to read.

If you wish to monitor your traffic use an appropriate tool such as snort.

---

### Post by oygle on 2009-09-13
> **bodhi.zazen said:**
> I am not sure about that. Did you have other applications installed that change your rules / preferences ? Are or did you run GUFW ? If so make sure logging is enabled in GUFW.

I originally had Firestarter installed, but it was 'completely' removed. Then I did have GUFW installed, with no rules though, and it also was completely removed.

Thanks for the link to the IPTables tutorial; I will try and digest it.

I might take a look at snort; yes, it makes the syslogs hard to read with all the dropped packets.

Thanks,

Oygle

---

### Post by ybres on 2009-09-17
Thank you @bodhi.zazen, your two lines of code were very useful and easy to use.```
sudo ufw enable
sudo ufw default deny
```Firefox, messenger... work well, still in order to use DC with search I had to open a port:
```
sudo ufw allow 12789
``` and configure the DC to use that port for tcp and udp. Same with BitTorrent.

Just to make sure: now all ports are closed by default except for 12789 and others I might add, right?

---

