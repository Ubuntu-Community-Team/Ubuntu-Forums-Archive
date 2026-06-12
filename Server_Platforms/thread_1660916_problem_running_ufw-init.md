---
title: "problem running ufw-init"
date: 2011-01-06
forum: Server Platforms
---

### Post by boblu on 2011-01-06
I just bought a VPS, and want to use ufw on it.
After install ufw package, I use

```
sudo ufw enable
```

to enable ufw.

However, every time, I get the following error message, and my system stops to respond to ssh or ping after that.

```

Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
ERROR: problem running ufw-init

```

Can anyone help me on this?

---

### Post by MrSketch on 2011-01-23
By default ufw will deny all access to the computer, so before you enable the firewall, you should at least allow ssh access:
```
sudo ufw allow 22
```Then you should be able to enable ufw without disruption:
```
sudo ufw enable
```Granted, you will still get the message about disrupting ssh connections, but hopefully you won't get the error with ufw-init.  If you're still getting the error with ufw-init, try running it directly and see what the error is:
```
sudo /lib/ufw/ufw-init start
```If it says it's already started, you may need to run:
```
sudo /lib/ufw/ufw-init force-reload
```and see what errors you get.  Sometimes, they are module issues and you have to load the ufw modules (according to [http://plugcomputer.org/plugforum/index.php?topic=176.0](http://plugcomputer.org/plugforum/index.php?topic=176.0)).   I once had a typo in one of my rules that was causing the error with ufw-init (I had -j ALLOW instead of -j ACCEPT) and when I ran the force-reload command I got output similar to:
```
iptables-restore v1.4.4: Couldn't load target `ALLOW':/lib/xtables/libipt_ALLOW.so: cannot open shared object file: No such file or directory

Error occurred at line: 66
Try `iptables-restore -h' or 'iptables-restore --help' for more information.

Problem running '/etc/ufw/before.rules'
```Of course, if you have module errors, you may see output similar to:
```
$ sudo /lib/ufw/ufw-init start
FATAL: Could not load /lib/modules/2.6.22.18/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.22.18/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.22.18/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.22.18/modules.dep: No such file or directory
iptables v1.4.1.1: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```Hope that helps!

Note: ufw-init may be in a different location on your system.  I'm running 10.04 and it was there, but in some forums, I've seen them refer to the file in /usr/share/ufw/ufw-init

---

### Post by l0co on 2012-03-27
Might be one of the problems mentioned there [http://blog.bodhizazen.net/linux/how-to-use-ufw-in-openvz-templates/](http://blog.bodhizazen.net/linux/how-to-use-ufw-in-openvz-templates/)

---

### Post by darkod on 2012-03-27
It just happened to me today. It is usually some error in a rule.

Did you make any changes to /etc/ufw/before.rules or /etc/ufw/after.rules? Does the provider provide these files as default or they have some changes in them?

If you have everything by default you shouldn't get that error.

And as already mentioned, make sure you open at least your SSH port (22 or another if you changed it) because enabling ufw without a rule to allow the port will kick you out and lock you out immediately.

---

### Post by DocHoss on 2012-05-02
I'm having a similar problem.  Whenever I do "sudo ufw enable" it throws the ufw-init error as above.  But if I enable it again it succeeds.  I did troubleshooting by doing the force-reload of ufw-init, and it tells me there's an error in before.rules on line 72.  Line 72 and 73 were the lines I entered into before.rules to allow icmp for ping.  Here are those two lines...is there something I did wrong?  

Also...ping doesn't work!  With those two lines commented out, ufw loads without an error, but ping doesn't work.  If I uncomment the lines, ufw throws an error (but still loads on the second attempt) and ping still doesn't work.  If UFW is disabled, ping works.

```

# allow outbound icmp
-A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p icmp -m state --state ESTABLISHED,RELATED -j ACCEPT

```

---

### Post by valugi on 2012-06-12
Still a problem. 
Using ufw 0.30pre1-0ubuntu2

---

### Post by darkod on 2012-06-12
> **valugi said:**
> Still a problem. 
Using ufw 0.30pre1-0ubuntu2

As already discussed, this is not a problem with ufw itself. It's usually a problem with a syntax of a rule you have set up.

Double check the rules you have added into before.rules or another ufw file.

---

### Post by Synchro on 2012-06-15
I'm seeing this too. To eliminate issues with rules I completely removed ufw and all config files:
```
aptitude remove ufw
aptitude purge ufw
rm -rf /etc/ufw /lib/ufw
iptables -F
```
I then check iptables to ensure it's all gone:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Then I reinstalled ufw. As part of the install it creates new config files:
```
Creating config file /etc/ufw/before.rules with new version
Creating config file /etc/ufw/before6.rules with new version
Creating config file /etc/ufw/after.rules with new version
Creating config file /etc/ufw/after6.rules with new version
```

I then enable it, and get the same ufw-init error. Running strace on the enable showed me it was missing modules for FTP and irc, so I disabled all extra modules in /etc/default/ufw. Enabling still failed, this time complaining about the before script (which doesn't refer to the removed modules), even though it is absolutely stock.

```
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
read(3, "iptables-restore: line 66 failed"..., 8192) = 33
read(3, "iptables-restore: line 30 failed"..., 8159) = 33
read(3, "\n", 8126)                     = 1
read(3, "Problem running '/etc/ufw/before"..., 8125) = 79
read(3, "", 8046)                       = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
```

The line numbers (30 and 66) mentioned in before.rules are:
```
-A ufw-before-input -m state --state INVALID -j DROP
COMMIT
```
Those look good to me.

It appears that running enable a second time does not trigger the error and things seem to work; the issue is that the first time it's run, not only does it not work, but it also blocks all new connections - so as long as I still have an open connection I can recover, but that's not a nice place to be.

---

### Post by mpollmeier on 2012-07-05
Same here with a fresh install of Ubuntu Server 10.04 and ufw. 
Running 'ufw enable' twice does the job, but it probably means that ufw isn't started automatically ;(

---

### Post by tohvanah on 2012-10-10
Same issue on 11.04 server in VPS. Any resolution? The ICMP rules are not being applied, and ping is not responding... Normal TCP rules are in effect.

---

### Post by pylover on 2012-12-17
Same problem in 11.04 vps server.

after adding allow ICMP rules:

```


root@baghali:~# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
ERROR: problem running ufw-init


root@baghali:~# /lib/ufw/ufw-init start
Skip starting firewall: ufw (not enabled)


root@baghali:~# /lib/ufw/ufw-init force-reload
Skipping  (not enabled)

```

but after :
```

apt-get purge ufw -y --force-yes

apt-get update; apt-get upgrade -y --force-yes

apt-get install ufw

```

problem was solved.

---

### Post by Synchro on 2012-12-17
That may have fixed it for you, but I don't think that's a general fix - mine turned out to be missing kernel modules, something that's quite likely to happen in a VPS.

---

### Post by Hugolp on 2013-02-01
> **Synchro said:**
> That may have fixed it for you, but I don't think that's a general fix - mine turned out to be missing kernel modules, something that's quite likely to happen in a VPS.

Can you tell us what you had to do, or at least a link to a solution? Im having the same problem.

---

### Post by darkod on 2013-02-01
> **Hugolp said:**
> Can you tell us what you had to do, or at least a link to a solution? Im having the same problem.

Did you double check your rules for syntax errors?

---

### Post by Synchro on 2013-02-01
It was my ISP that dealt with it so i don't know exactly, but you should look into using a different kernel, for example the stock ubuntu-virtual one, which has more modules enabled. Some cloud/VPS providers let you do this (e.g. Linode does), otherwise take it up with their support people.

---

### Post by gimmerealroot on 2013-07-17
I have the same issue.  I added only one line to before.rules.  When I comment it out, enable works as it should.  Here's the section in before.rules which I've edited:

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT
#-A ufw-before-input -j LOG --log-level warn
#I added this line above

Note the commented out line which seems to be probably a syntax error...

---

### Post by delany.middleton on 2013-11-14
It's an upstart service:

```
sudo service ufw start
```

---

