---
title: "[OpenSSH] Password login limitation to 1 specific user on a specific subnet"
date: 2015-07-31
forum: Security
---

### Post by Frank_Barmentlo on 2015-07-31
Hello All,

I run multiple 14.04.2 servers at home, which I access with SSH using keys.
Wishing to reduce maintenance time, I wrote various scripts to automate tasks.

Between my servers and the internet is a Sophos UTM.

Wanting to publish my servers through the HTML5-portal of the UTM, I ran into a specific issue, which requires me to use password authentication.
Not really what I want, at all.

I already found how I can enable password-auth for a single subnet, using
[code=sshd_config]
Match address 192.168.4.0/24
        PasswordAuthentication yes
[/code]

Can I restrict this to a single user on this one subnet?
So a Match-block, within a Match-block

Thanks for taking the time to read & reply,
Kind regards,
Frank

---

### Post by Lars Noodén on 2015-07-31
You should be able to put several conditions in your [Match](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) block:

```

Match User frank Address 192.168.4.0/24
        PasswordAuthentication yes

```

Mistakes can be hard to spot.  If you make a mistake, the error will show up in /var/log/authlog but sshd will otherwise reload.

---

### Post by Frank_Barmentlo on 2015-08-01
It seems to work so far,
Thanks for your help!

---

