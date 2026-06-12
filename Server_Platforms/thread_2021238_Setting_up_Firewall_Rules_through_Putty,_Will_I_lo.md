---
title: "Setting up Firewall Rules through Putty, Will I lose Connection?"
date: 2012-07-08
forum: Server Platforms
---

### Post by Wiking on 2012-07-08
Hi, I got a samba server running, I connect to it remotely using putty through my main pc.

I want to enable the firewall, and set some rules for ports. In Putty I get a warning that I may lose connection.

Can I set up the firewall remotely or do I have to do it physically on the server machine?

ufw is not enabled as of now.

---

### Post by SeijiSensei on 2012-07-09
Yes, you can lock yourself out of the server if you're not careful.  I've done it myself.

The simplest solution is to make sure one of the first rules in the list includes a blanket ACCEPT for the IP address from which you are connecting.  Something like:

```

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptablas -A INPUT -s your.own.ip.addr -j ACCEPT

etc.

```

---

### Post by spynappels on 2012-07-09
If you use iptables-restore and have the rules in a file, you could set up a backup of the current rules to dump to a file so you have a new_rules file and an old_rules file.

before applying the new rules, schedule an **at** job for **now + 10 minutes** or so, reloading the old_rules file. This means that if you are locked out by the new rule set, it will be for 10 minutes max as after 10 minutes the old rules will be applied.

If you are not locked out, you can use atrm to delete the at job.

I vaguely remember there is an easier way to achieve this, but for the life of me I cannot find the reference to it, maybe BodhiZazen will come along and remind us.

---

### Post by Wiking on 2012-07-09
I was reading the ufw man page and it said to to use the following command before enabling ufw:

 ```
ufw allow proto tcp from any to any port 22
```

Here's a small exscript of the man page:

> before  running  &#8217;ufw enable&#8217;. The rules will still be flushed, but the ssh port will be open after enabling the  firewall.  Please  note  that once  ufw  is  &#8217;enabled&#8217;,  ufw will not flush the chains when adding or removing rules (but will when modifying a rule or changing the  default policy).  By  default, ufw will prompt when enabling the firewall while running under ssh. This can be disabled by using &#8217;ufw --force  enable&#8217;.

So I type:

```
ufw allow proto tcp from any to any port 22
```

then

```
ufw --force  enable
```

Then I can configure iptables using ufw without losing the connection. 

What does it mean by 'flushing chains'?

Is the ```
ufw allow proto tcp from any to any port 22
``` permanent?

Or temporary? If permanent how would I remove it?

Would it be?

```
ufw **deny** proto tcp from any to any port 22
```

---

### Post by Wiking on 2012-07-09
I got this in ufw status:


```
To                         Action      From
--                         ------      ----
22/tcp                     DENY        Anywhere
22                         ALLOW       Anywhere
22/tcp                     DENY        Anywhere (v6)
22                         ALLOW       Anywhere (v6)
```

Shouldn't it be:

22/tcp               ALLOW 

?

---

### Post by darkod on 2012-07-10
If you ran the Deny it exists as rule too. You don't delete rules by using Deny, you only set a Deny rule with that.

But note that if you delete all Allow rules for port 22, you WILL lock yourself out as ufw will block you.

To delete rules, first output the status with numbers. If I remember correctly it was:
sudo ufw status numbered

That will have a number in front of each rule. Then you simply run like:
sudo ufw delete <number>

Note that as you delete, other rules move towards the top. So don't list the status only once and then start deleting bunch of rules, because some will move and you might delete a wrong one.

After deleting, you will have to disable and enable ufw at which point it makes your change permanent:
sudo ufw disable && sudo ufw enable

Not sure how good you are with iptables, but I would recommend using iptables directly, not their front ufw. It makes the rules much cleaner.

---

