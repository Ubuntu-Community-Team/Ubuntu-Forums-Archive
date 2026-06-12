---
title: "fun with firewalls"
date: 2011-07-21
forum: Security
---

### Post by deesto on 2011-07-21
I'm a bit confused about Ubuntu firewalls, and after reading documentation on UFW, I've been asking in a few places in the forums ([1]("http://ubuntuforums.org/showpost.php?p=11036280&postcount=10"), [2]("http://ubuntuforums.org/showpost.php?p=11060406&postcount=36"), etc.) but still don't have a clear understanding.

In short: let's say I need to programmatically and persistently automate system firewall rules (via Puppet), and I want to block all incoming connections, except for SSH and X connections from a specific host.  In another OS, I'd do this via iptables rules in /etc/sysconfig/iptables.  But Ubuntu doesn't support this (at least not this specific file) and suggests that rules be done instead via `sudo ufw ___` commands, or put in /etc/ufw/*.  But my attempts to create ufw rules aren't working (e.g, I create `allow` and default `deny` rules, and then everything gets denied and the allow is ignored), and it's not clear to me where in /etc/ufw/* these rules should be placed.  

When I created `ufw` rules by hand, they didn't seem to have been written into the config files.  Where did they go?  I assumed they would go in `before.rules`, but they weren't there.  Where does UFW store persistent rules defined via CLI?

If I want instead to disable UFW completely and use iptables directly instead, what is the Ubuntu replacement or version of /etc/sysconfig/iptables for persistent iptables rules?

---

### Post by bodhi.zazen on 2011-07-21
> **deesto said:**
> I'm a bit confused about Ubuntu firewalls, and after reading documentation on UFW, I've been asking in a few places in the forums ([1]("http://ubuntuforums.org/showpost.php?p=11036280&postcount=10"), [2]("http://ubuntuforums.org/showpost.php?p=11060406&postcount=36"), etc.) but still don't have a clear understanding.

In short: let's say I need to programmatically and persistently automate system firewall rules (via Puppet), and I want to block all incoming connections, except for SSH and X connections from a specific host.  In another OS, I'd do this via iptables rules in /etc/sysconfig/iptables.  But Ubuntu doesn't support this (at least not this specific file) and suggests that rules be done instead via `sudo ufw ___` commands, or put in /etc/ufw/*.  But my attempts to create ufw rules aren't working (e.g, I create `allow` and default `deny` rules, and then everything gets denied and the allow is ignored), and it's not clear to me where in /etc/ufw/* these rules should be placed.  

When I created `ufw` rules by hand, they didn't seem to have been written into the config files.  Where did they go?  I assumed they would go in `before.rules`, but they weren't there.  Where does UFW store persistent rules defined via CLI?

If I want instead to disable UFW completely and use iptables directly instead, what is the Ubuntu replacement or version of /etc/sysconfig/iptables for persistent iptables rules?

iptables-save and iptables-restore or iptables-apply

iptables-save is the iptables command to generate a list of your rules, and unlike the distro you are coming from Ubuntu does not wrap that in the init script.

You can use any location / file you like, personally I use /etc/iptables.save

Run these commands as root

Save:
```
iptables-save > /etc/iptables.save
```

To restore those rules (edit them as you wish)
```
iptables-restore < /etc/iptables.save
```

If you are working on a headless server, use iptables-apply

```
iptables-apply /etc/iptables.save
```

You can add these commands to your network interface scripts, using post-up.

See this page : [https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup](https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup)

for 3 suggestions, or use /etc/rc.local

---

### Post by deesto on 2011-07-22
Hi bodhi.zazen, and thank you.  I have seen the recommendation for iptables-[apply|save] before, but was hoping for something that I wouldn't have to exec in order to enact, e.g., a config somewhere that automatically gets read on boot and pushed into iptables or the kernel.  That said, iptables-save is certainly doable.  

In this situation, do you recommend skipping (and explicitly disabling) the UFW bit altogether and pursuing iptables?  I assume so based you your response, but wanted to verify.  And after a list of iptables rules on a host on which ufw is disabled, and seeing a slew of ufw chains in the output (empty but there all the same and each listing 1 reference), I'm still hopeful but not confident that things will work as expected.

---

### Post by haqking on 2011-07-22
> **deesto said:**
> Hi bodhi.zazen, and thank you.  I have seen the recommendation for iptables-[apply|save] before, but was hoping for something that I wouldn't have to exec in order to enact, e.g., a config somewhere that automatically gets read on boot and pushed into iptables or the kernel.  That said, iptables-save is certainly doable.  

In this situation, do you recommend skipping (and explicitly disabling) the UFW bit altogether and pursuing iptables?  I assume so based you your response, but wanted to verify.  And after a list of iptables rules on a host on which ufw is disabled, and seeing a slew of ufw chains in the output (empty but there all the same and each listing 1 reference), I'm still hopeful but not confident that things will work as expected.

UFW is simply a Uncomplicated interface for IPTables.

Netfilter/IPtables is hardcoded into the linux kernel, UFW/GUFW, Firestarter etc are just ways to interface with IPtables.

well thats how i understand it anyways, i might be wrong

---

### Post by deesto on 2011-07-22
Right haqking: that's my understanding as well, with the caveat that iptables itself is also an interface to netfilter.  UWF is seeming less and less "uncomplicated" to me and more like a somewhat obfuscated layer on top of iptables (even the rules are similar).

---

### Post by bodhi.zazen on 2011-07-22
Personally I use ufw for desktops / netbooks and iptables for servers / routers.

So, IMO, most desktop users behind a router do not need a firewall, but if they wish, and they do not want to learn iptables, a simple

```
sudo ufw enable
sudo ufw default deny
```

Is sufficient for 99.99999 % , simple, easy to instruct on the forums, done.

Similar for basic severs if you simply want to allow all traffic to a web server.

But, once you understand the basics, I use iptables on servers. In that event, simply disable ufw, you can remove it if you wish.

```
sudo ufw disable
```

And use the methods I described. iptables-apply is nice for remote connections, you might like it.

At any rate, the rules for iptables must be applied by some script. In the system you came from it was an init script.

You can write an init script for Ubuntu if you want, add it to the network scripts, add it to NetworkManager, or add it to /etc/rc.local

One nice feature of Ubuntu is the network scripts, there is a set of command pre-up, post-up, pre-down, post-down. You use these to call commands.

On a server, look in /etc/network/interfaces, you will see something like

> iface eth0 inet static
address your_public_ip
netmask your_netmask
gateway your gateway

Just add in the post-up ;)

```
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
post-up iptables-restore < /etc/iptables.save
```

See the man page for details

[http://manpages.ubuntu.com/manpages/oneiric/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/oneiric/man5/interfaces.5.html)

Also see the link I gave you, use whatever technique you prefer.

to clear the ufw rules, you need to clean up iptables with -X and -F

---

### Post by deesto on 2011-07-22
Thanks for that bodhi.zazen, especially the post-up bit.  That helps me to make sense of a lot of this.  Other OS flavors have similar network configs and scripts, but use different names (obviously).

BTW, to answer one of my own questions: a friend pointed me to this file, which I don't see described in detail in the docs:
**/lib/ufw/user.rules**

As it turns out, _this_ is where ufw CLI rules end up.

---

### Post by bodhi.zazen on 2011-07-22
> **deesto said:**
> Thanks for that bodhi.zazen, especially the post-up bit.  That helps me to make sense of a lot of this.  Other OS flavors have similar network configs and scripts, but use different names (obviously).

I understand, I especially like the post-up commands in debian/ubuntu network scripts, wish they had them in rpm based distros.

---

### Post by deesto on 2011-07-22
Actually, there's something I can't figure out: adding a default allow rule for outgoing traffic (via ufw CLI) does _not_ seem to get written to /lib/ufw/user.rules, as the other rule commands for specific hosts/ports do.  Any idea into what file the `default [allow|deny]` rules end up?  I see that something `touch`es this file, as well as /etc/ufw/after.rules, when the command gets run, but the content of those files isn't changed.

---

### Post by bodhi.zazen on 2011-07-22
> **deesto said:**
> Actually, there's something I can't figure out: adding a default allow rule for outgoing traffic (via ufw CLI) does _not_ seem to get written to /lib/ufw/user.rules, as the other rule commands for specific hosts/ports do.  Any idea into what file the `default [allow|deny]` rules end up?  I see that something `touch`es this file, as well as /etc/ufw/after.rules, when the command gets run, but the content of those files isn't changed.

grep the files in /etc/ufw/ for '-P'

---

### Post by deesto on 2011-07-22
> **bodhi.zazen said:**
> grep the files in /etc/ufw/ for '-P'
Hmmm ... null result.  Lots of '-p' but no '-P' in /etc/ufw/*.

---

### Post by deesto on 2011-07-25
What the ... if UFW isn't iptables, why does it have its own 'iptables' directory, with rules separate from those of the same name in the directory above that, which are separate from the ones in /lib/ufw/?

And why don't these user rules match the ones I'd created, which ended up in /lib/ufw/?

```
$ ll /usr/share/ufw/iptables/
total 32
drwxr-xr-x 2 root root 4096 2011-04-28 13:14 ./
drwxr-xr-x 4 root root 4096 2011-04-28 13:14 ../
-rw-r--r-- 1 root root  913 2011-03-22 16:45 after6.rules
-rw-r--r-- 1 root root 1004 2011-03-22 16:45 after.rules
-rw-r--r-- 1 root root 2634 2011-03-22 16:45 before6.rules
-rw-r--r-- 1 root root 2021 2011-03-22 16:45 before.rules
-rw-r--r-- 1 root root  107 2011-03-22 14:00 user6.rules
-rw-r--r-- 1 root root  307 2011-03-22 14:00 user.rules

$ ll /usr/share/ufw/
total 84
drwxr-xr-x   4 root root  4096 2011-04-28 13:14 ./
drwxr-xr-x 383 root root 12288 2011-06-30 11:36 ../
-rw-r--r--   1 root root   913 2011-03-22 16:45 after6.rules
-rw-r--r--   1 root root   186 2011-03-22 16:40 after6.rules.md5sum
-rw-r--r--   1 root root  1004 2011-03-22 16:45 after.rules
-rw-r--r--   1 root root   305 2011-03-22 16:40 after.rules.md5sum
-rw-r--r--   1 root root  2634 2011-03-22 16:45 before6.rules
-rw-r--r--   1 root root   315 2011-03-22 16:40 before6.rules.md5sum
-rw-r--r--   1 root root  2021 2011-03-22 16:45 before.rules
-rw-r--r--   1 root root   372 2011-03-22 16:40 before.rules.md5sum
-rwxr-xr-x   1 root root  6044 2011-03-22 14:00 check-requirements*
drwxr-xr-x   2 root root  4096 2011-04-28 13:14 iptables/
drwxr-xr-x   2 root root  4096 2011-04-28 13:14 messages/
-rw-r--r--   1 root root   312 2011-03-22 16:45 ufw.conf
-rw-r--r--   1 root root   107 2011-03-22 14:00 user6.rules
-rw-r--r--   1 root root    61 2011-03-22 16:40 user6.rules.md5sum
-rw-r--r--   1 root root   307 2011-03-22 14:00 user.rules
-rw-r--r--   1 root root    60 2011-03-22 16:40 user.rules.md5sum
       
$ ll /lib/ufw/
total 44
drwxr-xr-x  2 root root  4096 2011-07-22 17:18 ./
drwxr-xr-x 21 root root 12288 2011-05-17 11:09 ../
-rwxr-xr-x  1 root root  1695 2011-03-22 16:45 ufw-init*
-rwxr-xr-x  1 root root 15409 2011-03-22 16:45 ufw-init-functions*
-rw-r-----  1 root root   533 2011-07-22 17:17 user6.rules
-rw-r-----  1 root root  1593 2011-07-22 17:18 user.rules
```

Who named this the "uncomplicated" firewall?

---

### Post by bodhi.zazen on 2011-07-25
> **deesto said:**
> What the ... Who named this the "uncomplicated" firewall?

Well it is "uncomplicated" as one can enable it and make a few simple rules without a deep understanding of iptables.

I agree, if you are going to want to make substantial changes or complex rules, I find it quite complicated in terms of both trying to work through the custom chains and config files.

Thus, when doing anything much beyond the basics, I fall back to iptables.

---

### Post by deesto on 2011-07-26
> **bodhi.zazen said:**
> Well it is "uncomplicated" as one can enable it and make a few simple rules without a deep understanding of iptables.

I agree, if you are going to want to make substantial changes or complex rules, I find it quite complicated in terms of both trying to work through the custom chains and config files.

Thus, when doing anything much beyond the basics, I fall back to iptables.

Agreed: it's nice to have the option of falling back to iptables, as well as using the up/down script method to control things.  But that's not quite the same as having an init or service script to help manage the firewall, restart it when necessary, etc.  It seems a strange implementation to provide the service on a system, but not the tools to fully manage it as a "service".

---

