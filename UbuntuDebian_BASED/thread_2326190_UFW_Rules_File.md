---
title: "UFW Rules File"
date: 2016-05-29
forum: Ubuntu/Debian BASED
---

### Post by Geoff_Lane on 2016-05-29
Folks,

My main system is Ubuntu but this does relate to UFW installed on a Debian Raspberry Pi

Installed fine, enabled fine but treading gently as accessing using my Ubuntu machine via ssh.

Initially enabled ssh and port 80 but cannot see in any file where this is listed. Checked the before, before6, after and after6 rules. checked sysctrl,conf and ufw.conf and can find nothing.

Cannot find a file either that lists the default policy.

Can anyone advise what file changes when rules are added.

Geffers

---

### Post by jim_deadlock on 2016-05-30
When you add custom rules they go into /etc/ufw/user.rules and user6.rules

---

### Post by Geoff_Lane on 2016-05-30
Haven't got those Jim, only before and after with and without 6 so 4 files.

Geffers

---

### Post by jim_deadlock on 2016-05-30
I use gufw to add my rules so the user files may be created by it. Anyway you can use mine as templates if you like, my rules are on the lines below 'tuple' (no idea what that means)

user.rules
```
*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-before-logging-input - [0:0]
:ufw-before-logging-output - [0:0]
:ufw-before-logging-forward - [0:0]
:ufw-user-logging-input - [0:0]
:ufw-user-logging-output - [0:0]
:ufw-user-logging-forward - [0:0]
:ufw-after-logging-input - [0:0]
:ufw-after-logging-output - [0:0]
:ufw-after-logging-forward - [0:0]
:ufw-logging-deny - [0:0]
:ufw-logging-allow - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
### RULES ###

### tuple ### allow tcp 21 0.0.0.0/0 any 216.38.55.114 in
-A ufw-user-input -p tcp --dport 21 -s 216.38.55.114 -j ACCEPT

### tuple ### allow udp any 0.0.0.0/0 any 10.0.0.4 in_eno1
-A ufw-user-input -i eno1 -p udp -s 10.0.0.4 -j ACCEPT

### END RULES ###

### LOGGING ###
-A ufw-after-logging-input -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-after-logging-forward -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-I ufw-logging-deny -m conntrack --ctstate INVALID -j RETURN -m limit --limit 3/min --limit-burst 10
-A ufw-logging-deny -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-logging-allow -j LOG --log-prefix "[UFW ALLOW] " -m limit --limit 3/min --limit-burst 10
### END LOGGING ###

### RATE LIMITING ###
-A ufw-user-limit -m limit --limit 3/minute -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT
-A ufw-user-limit-accept -j ACCEPT
### END RATE LIMITING ###
COMMIT
```

user6.rules
```
*filter
:ufw6-user-input - [0:0]
:ufw6-user-output - [0:0]
:ufw6-user-forward - [0:0]
:ufw6-before-logging-input - [0:0]
:ufw6-before-logging-output - [0:0]
:ufw6-before-logging-forward - [0:0]
:ufw6-user-logging-input - [0:0]
:ufw6-user-logging-output - [0:0]
:ufw6-user-logging-forward - [0:0]
:ufw6-after-logging-input - [0:0]
:ufw6-after-logging-output - [0:0]
:ufw6-after-logging-forward - [0:0]
:ufw6-logging-deny - [0:0]
:ufw6-logging-allow - [0:0]
:ufw6-user-limit - [0:0]
:ufw6-user-limit-accept - [0:0]
### RULES ###

### END RULES ###

### LOGGING ###
-A ufw6-after-logging-input -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw6-after-logging-forward -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-I ufw6-logging-deny -m conntrack --ctstate INVALID -j RETURN -m limit --limit 3/min --limit-burst 10
-A ufw6-logging-deny -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw6-logging-allow -j LOG --log-prefix "[UFW ALLOW] " -m limit --limit 3/min --limit-burst 10
### END LOGGING ###

### RATE LIMITING ###
-A ufw6-user-limit -m limit --limit 3/minute -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw6-user-limit -j REJECT
-A ufw6-user-limit-accept -j ACCEPT
### END RATE LIMITING ###
COMMIT
```

---

### Post by deadflowr on 2016-05-30
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Geoff_Lane on 2016-05-31
I'm reluctant to make any major changes until I understand (a bit) what happens.

I'll study your reply on my bigger computer, on the phone at the moment &#128514;

Thank you for quick reply Jim.

Geffers

> **deadflowr said:**
> *Thread moved to **Ubuntu/Debian BASED**.*

Deadflower, I can't find Ubuntu/Debian Based anywhere in the list of forums.

I want to ask a similar themed question but can't see where to post it.

Geffers

---

### Post by howefield on 2016-05-31
> **Geoff_Lane said:**
> ...I can't find Ubuntu/Debian Based anywhere in the list of forums...

Forum Index Page > Other Discussion and Support > Other OS Support and Projects > Ubuntu/Debian BASED

or

[http://ubuntuforums.org/forumdisplay.php?f=452](http://ubuntuforums.org/forumdisplay.php?f=452)

---

### Post by Geoff_Lane on 2016-05-31
> **howefield said:**
> Forum Index Page > Other Discussion and Support > Other OS Support and Projects > Ubuntu/Debian BASED


Wow, that's quite obscure. Appreciate I did say this was installed on a Pi but thought as it was an Ubuntu program (I think) managed using a terminal on my Ubuntu desktop that the desktop was the correct section.

Never mind, apologies for any problem caused.

Geffers

---

