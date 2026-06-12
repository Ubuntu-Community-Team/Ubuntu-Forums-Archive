---
title: "SSH and security question"
date: 2005-02-19
forum: Server Platforms
---

### Post by negativ on 2005-02-19
I frequently find stuff like this in auth.log:

```
Jan 27 04:02:48 localhost sshd[23914]: Invalid user jordan from 67.15.40.2
Jan 27 04:02:49 localhost sshd[23916]: Invalid user michael from 67.15.40.2
Jan 27 04:02:49 localhost sshd[23918]: Invalid user nicole from 67.15.40.2
Jan 27 04:02:49 localhost sshd[23920]: Invalid user daniel from 67.15.40.2
Jan 27 04:02:49 localhost sshd[23922]: Invalid user andrew from 67.15.40.2
Jan 27 04:02:50 localhost sshd[23924]: Invalid user nathan from 67.15.40.2
Jan 27 04:02:50 localhost sshd[23926]: Invalid user matthew from 67.15.40.2
Jan 27 04:02:50 localhost sshd[23928]: Invalid user magic from 67.15.40.2
Jan 27 04:02:51 localhost sshd[23930]: Invalid user lion from 67.15.40.2
Jan 27 04:02:51 localhost sshd[23932]: Invalid user david from 67.15.40.2
Jan 27 04:02:51 localhost sshd[23934]: Invalid user jason from 67.15.40.2
Jan 27 04:02:52 localhost sshd[23936]: Invalid user ben from 67.15.40.2
Jan 27 04:02:52 localhost sshd[23938]: Invalid user carmen from 67.15.40.2
Jan 27 04:02:52 localhost sshd[23940]: Invalid user justin from 67.15.40.2
Jan 27 04:02:52 localhost sshd[23942]: Invalid user charlie from 67.15.40.2
Jan 27 04:02:53 localhost sshd[23945]: Invalid user steven from 67.15.40.2
Jan 27 04:02:53 localhost sshd[23947]: Invalid user brandon from 67.15.40.2
Jan 27 04:02:53 localhost sshd[23949]: Invalid user brian from 67.15.40.2
Jan 27 04:02:54 localhost sshd[23951]: Invalid user stephen from 67.15.40.2
Jan 27 04:02:54 localhost sshd[23953]: Invalid user william from 67.15.40.2
Jan 27 04:02:54 localhost sshd[23955]: Invalid user angel from 67.15.40.2
Jan 27 04:02:55 localhost sshd[23957]: Invalid user emily from 67.15.40.2
Jan 27 04:02:55 localhost sshd[23959]: Invalid user eric from 67.15.40.2
Jan 27 04:02:55 localhost sshd[23961]: Invalid user joe from 67.15.40.2
Jan 27 04:02:55 localhost sshd[23963]: Invalid user tom from 67.15.40.2
Jan 27 04:02:56 localhost sshd[23965]: Invalid user billy from 67.15.40.2
Jan 27 04:02:56 localhost sshd[23967]: Invalid user buddy from 67.15.40.2
Jan 27 04:02:56 localhost sshd[23969]: Invalid user jeremy from 67.15.40.2
Jan 27 04:02:57 localhost sshd[23971]: Invalid user vampire from 67.15.40.2
Jan 27 04:02:57 localhost sshd[23973]: Invalid user betty from 67.15.40.2
Jan 27 04:02:57 localhost sshd[23975]: Invalid user henry from 67.15.40.2
Jan 27 04:02:57 localhost sshd[23977]: Invalid user max from 67.15.40.2
Jan 27 04:02:58 localhost sshd[23980]: Invalid user nicholas from 67.15.40.2
Jan 27 04:02:58 localhost sshd[23982]: Invalid user robin from 67.15.40.2
Jan 27 04:02:58 localhost sshd[23984]: Invalid user system from 67.15.40.2
Jan 27 04:02:59 localhost sshd[23986]: Invalid user johnny from 67.15.40.2
Jan 27 04:02:59 localhost sshd[23988]: Invalid user lucy from 67.15.40.2
Jan 27 04:02:59 localhost sshd[23990]: Invalid user market from 67.15.40.2
Jan 27 04:03:00 localhost sshd[23994]: Invalid user maria from 67.15.40.2
Jan 27 04:03:00 localhost sshd[23996]: Invalid user rose from 67.15.40.2
Jan 27 04:03:01 localhost sshd[24000]: Invalid user god from 67.15.40.2
Jan 27 04:03:01 localhost sshd[24002]: Invalid user barbara from 67.15.40.2
Jan 27 04:03:01 localhost sshd[24004]: Invalid user operator from 67.15.40.2
Jan 27 04:03:02 localhost sshd[24006]: Invalid user larisa from 67.15.40.2
Jan 27 04:03:02 localhost sshd[24008]: Invalid user shell from 67.15.40.2
Jan 27 04:03:02 localhost sshd[24010]: Invalid user jane from 67.15.40.2
Jan 27 04:03:03 localhost sshd[24012]: Invalid user dog from 67.15.40.2
Jan 27 04:03:03 localhost sshd[24015]: Invalid user blue from 67.15.40.2
Jan 27 04:03:03 localhost sshd[24017]: Invalid user red from 67.15.40.2
Jan 27 04:03:03 localhost sshd[24019]: Invalid user yellow from 67.15.40.2
Jan 27 04:03:04 localhost sshd[24021]: Invalid user green from 67.15.40.2
Jan 27 04:03:04 localhost sshd[24023]: Invalid user black from 67.15.40.2
Jan 27 04:03:04 localhost sshd[24025]: Invalid user pub from 67.15.40.2
```

Unfortunately, I do not have the option of setting up firewall rules to only allow incoming ssh connections from certain places.  This is because I often need to ssh from new locations.  

I do use a strong username / password combo, but the above makes me want to take it a step or two further.

One idea that occurs to me is to have the system refuse subsequent connections from an IP after a number of invalid user names has been attempted from that address.  How would one go about this?

---

### Post by GilGalad on 2005-02-19
Uhm.. Now that you say it, I also having the same log in my auth.log. Seems like somebody scanning... Time to configure iptables.

---

### Post by Jad on 2005-02-19
Had same problem, auto blocking those scanners wont help because you will end up with blocking the earth. 
Changing SSH port will solve it.

---

### Post by piedamaro on 2005-02-19
Also use gpg authentication instead of password, and you can configure sshd to allow only certain ips.

---

### Post by sgbeamer on 2005-02-19
Configure SSH to use a non-standard port and most of this will go away.

---

### Post by az on 2005-02-19
What about an intrusion detection system?  Would this detect the problem and block those ip addresses for some period of time?

---

### Post by Jad on 2005-02-19
those scanners are growing and growing, it started with about 5 scanns a day, until it reached about 1500 scann a day
so change the default port, disable direct root login and sleep well.

---

### Post by dewey on 2005-02-19
There are tons of worms that run dictionary attacks on SSH servers.
Change the default port number.
And disable root logins. (Isn't so much of a deal in ubuntu, since the root account is disabled by default)
And use only trusted ips, or certificates.

---

