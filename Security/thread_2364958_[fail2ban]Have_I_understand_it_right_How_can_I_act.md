---
title: "[fail2ban]Have I understand it right? How can I activate it agains port 587 and 53."
date: 2017-06-30
forum: Security
---

### Post by calby on 2017-06-30
Hi,
I have been fixing a bit with my fail2ban config, but I just must make sure that I have been understanding everything correct.
I'm running Ubuntu 16.04 LTS and the latest stabile version of fail2ban.

**Quastions:**
**1.** The jail.local file are overriding every other setting, is that correct?
**2. **In my jail.local file under [DEFAULTS] I have stated some things, is it necessary to write the same rules under the filter settings in the jail.local file? Or is it only necessary if I want to go over the [DEFAULT] settings?

**3.** This is my jail.local file, does it look correct? And question that are touching the no 3 question, all of my filter setups(?) does have a maxretry of 3 as it's stated in [DEFAULTS] then it's not nessecary to write it in the filter setup in the jail.conf file correct?

```

[DEFAULT]
ignoreip = 127.0.0.1/8 192.168.1.3
bantime = 3600
findtime = 600
maxretry = 3
action = %(action_mwl)s


[sshd]

enabled  = true
port     = 2342
filter   = sshd
logpath  = /var/log/auth.log
bantime = 86400

[sshd-ddos]

enabled  = true
port     = 2342
filter   = sshd-ddos
logpath  = /var/log/auth.log
bantime = 86400

[nginx-http-auth]

enabled  = true
filter   = nginx-http-auth
port     = http,https
logpath  = /var/log/nginx/*error.log
bantime = 86400

[nginx-noscript]

enabled  = true
port     = http,https
filter   = nginx-noscript
logpath  = /var/log/nginx/*access.log
bantime = 86400

[nginx-badbots]

enabled  = true
port     = http,https
filter   = nginx-badbots
logpath  = /var/log/nginx/*access.log
bantime = 86400

[nginx-nohome]

enabled  = true
port     = http,https
filter   = nginx-nohome
logpath  = /var/log/nginx/*access.log
bantime = 86400

[nginx-noproxy]

enabled  = true
port     = http,https
filter   = nginx-noproxy
logpath  = /var/log/nginx/*access.log
bantime = 86400

[nginx-botsearch]

enabled = true
port     = http,https
filter = nginx-botsearch
logpath  = /var/log/nginx/*error.log
bantime = 86400

[seafile]

enabled  = true
port     = http,https
filter   = seafile-auth
logpath  = /home/xxx/tinytechnet/logs/seahub.log

```

**4.** And I have only change the "bantime" in the filter setups on the filters that I want to go outside the [default] rules I'm guessing that's correct?
**5.** I have opend port 587 for outgoing e-mail, can I somehow activate a filter in Jail2ban for that port?
**6.** I have also opend the port 53 for outgoing trafic as I need that port to update Ubuntu, can I activate Jail2Ban on that port also?


I'm just hoping that I have done this correct with fail2ban, the security in Ubuntu is endless I guess.
I have also activated the ufw firewall and made it block all traffic in/out beside the ports that I have manually opened.
The server is behind a router with firewall as well.

---

### Post by Habitual on 2017-06-30
> **calby said:**
> Hi,
I have been fixing a bit with my fail2ban config, but I just must make sure that I have been understanding everything correct.
I'm running Ubuntu 16.04 LTS and the latest stabile version of fail2ban.

**Quastions:**
**1.** The jail.local file are overriding every other setting, is that correct?
**2. **In my jail.local file under [DEFAULTS] I have stated some things, is it necessary to write the same rules under the filter settings in the jail.local file? Or is it only necessary if I want to go over the [DEFAULT] settings?
looks good here.
All of that is covered in /etc/fail2ban/jail.{conf,local}

Are you serving DNS on port 53?
You could just use ufw or another to "deny" all ports 53/587

Good Luck!

---

### Post by calby on 2017-06-30
> **Habitual said:**
> looks good here.
All of that is covered in /etc/fail2ban/jail.{conf,local}

Are you serving DNS on port 53?
You could just use ufw or another to "deny" all ports 53/587

Good Luck!

I need port 53 to update Ubuntu, if I block that port I can't update Ubuntu trough apt-get.
Port 587 I need open to send e-mail trough gmail.

---

### Post by Habitual on 2017-06-30
I don't know then, sorry.
I have port 53 closed and I can update without issue. It's used for DNS so that may be your clue.

I see 3 jails.
ssh nginx-* and seafile

I don't see these:
```
action_ = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]

action_mw = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
              %(mta)s-whois[name=%(__name__)s, dest="%(destemail)s", protocol="%(protocol)s", chain="%(chain)s"]

action_mwl = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
               %(mta)s-whois-lines[name=%(__name__)s, dest="%(destemail)s", logpath=%(logpath)s, chain="%(chain)s"]
``` in your jail.local

Omitted here or not  in the jail.local?

---

### Post by Habitual on 2017-06-30
See also [https://ubuntuforums.org/showthread.php?t=2305198](https://ubuntuforums.org/showthread.php?t=2305198)

I suggest defaults to get acclimated to fail2ban.

If```
 [jail]
maxretry = 1
```
is missing
then fail2ban looks to [DEFAULT] for the "maxretry = " assignment there.

If you are in a .local file then it would scan the .conf that came with the package for the missing directive assignement.
Or that is my understanding.

Any files made that are not part of the package as installed, will be left behind.

How are you planning to exclude Ubuntu-related repos if you decide to scan 53?
```
ignoreip = 
```
accepts CIDR designations but what are they? There must be a couple of 100 hosts identified as ubuntu-repos?

There is something wrong, IMO if you have to allow port 53 to be "open" for updates.
Using fail2ban in this situation will not help.

But it's a Great Tool to know, so have fun!

---

### Post by calby on 2017-06-30
> **Habitual said:**
> I don't know then, sorry.
I have port 53 closed and I can update without issue. It's used for DNS so that may be your clue.

I see 3 jails.
ssh nginx-* and seafile

I don't see these:
```
action_ = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]

action_mw = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
              %(mta)s-whois[name=%(__name__)s, dest="%(destemail)s", protocol="%(protocol)s", chain="%(chain)s"]

action_mwl = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
               %(mta)s-whois-lines[name=%(__name__)s, dest="%(destemail)s", logpath=%(logpath)s, chain="%(chain)s"]
``` in your jail.local

Omitted here or not  in the jail.local?

I got it in the Default section in Jail.local "action = %(action_mwl)s" or isent that right?

```

[DEFAULT]
ignoreip = 127.0.0.1/8 192.168.1.3
bantime = 3600
findtime = 600
maxretry = 3
action = %(action_mwl)s

```

---

### Post by Habitual on 2017-06-30
> **calby said:**
> I got it in the Default section in Jail.local "action = %(action_mwl)s" or isent that right?
I don't know what's "right", but I simply advise 2 things.
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
and only put enabled jails in /etc/fail2ban/jail.local

Good Luck!

---

### Post by calby on 2017-06-30
> **Habitual said:**
> I don't know what's "right", but I simply advise 2 things.
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
and only put enabled jails in /etc/fail2ban/jail.local

Good Luck!

Well this is confusing as I don't know if I can trust my config then... =/

nvm:

[According to the Manual 8 0]("http://www.fail2ban.org/wiki/index.php/MANUAL_0_8")

  "Every .conf file can be overridden with a file named .local. The  .conf file is read first, then .local, with later settings overriding  earlier ones. Thus, a .local file doesn't have to include everything in  the corresponding .conf file, only those settings that you wish to  override. Modifications should take place in the .local and not in the .conf. This  avoids merging problem when upgrading. These files are well documented  and detailed information should be available there."
     
So just put what you want in the .local file, if something is missing then it get's it from the jail.conf file.

---

### Post by Habitual on 2017-07-05
> **calby said:**
> Well this is confusing as I don't know if I can trust my config then... =/

nvm:
Your fail2ban deployment is likely ineffective as you don't have a named
```
**[COLOR="#FF0000"]banaction[/COLOR]** = 
``` directive in either [DEFAULT] or in any shown jail.
What is "banaction = " in /etc/fail2ban/jail.conf?

nvm? Am I to suppose you're all "good to go"?
I put a lot of time and thought into your solution, so a "nvm" sorta stings.

---

