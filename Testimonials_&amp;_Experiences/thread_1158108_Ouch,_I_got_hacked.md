---
title: "Ouch, I got hacked"
date: 2009-05-13
forum: Testimonials &amp; Experiences
---

### Post by lazyart on 2009-05-13
Was snooping around my log files yesterday while on a quest for something else and found some strange activity:  attacks on my ftp server, cron jobs I didn't know about and accounts logging in.  Yep, I've been hacked.

How did this happen?  Well, years ago when I built my Windows domain I put in some test accounts to try some stuff and learn some other stuff about group policy and such.  I used then for a while but left them alone, and quite frankly forgot about them.

Fast forward a couple years, I've moved into another house, brought my servers over, then got into Ubuntu.  Then I joined it to my Windows domain using SADMS and then later Likewise-Open.  All is well.  Then I forwarded port 22 to my Ubuntu desktop so that I could access files from my Linux Netbook when on the road.

Even with fail2ban shutting out connections for 10 minutes after 3 failed attempts, someone uncovered one of the test accounts and using dictionary attack cracked the password.  My Windows Server wouldn't have allowed login with the test account, so I never thought about it.  But since my Linux desktop is a client machine, it authenticated through.  Looking into my /home/DOMAINNAME I found a folder for the test account.  Later I snooped around and found the cron job attributed to the account as well.

First thing to do was delete the test account from the domain, then chown and delete the offending home and cron job.  Then I installed DenyHosts from synaptic and let it comb through my auth.log and permanently ban future attackers using /etc/deny.hosts

I feel better now, but in the meantime I'm looking at my logs more often.

---

### Post by squaregoldfish on 2009-05-13
Depending on the usage of your server, you may find it helpful to change the SSH port to something other than 22. My SSH port is set somewhere way over 10000, and I've not seen a single attempt to log in.

Of course, the other security steps should be used as well...

Steve.

---

### Post by scottuss on 2009-05-13
I agree, set your SSH port waaaay high, those pesky snooper scripts don't get a look in. I went from several hundred probes an hour to zero in about a year.

:D

---

### Post by waspbr on 2009-05-13
I have been playing with ssh and remote desktops lately, thanks for the tip.

---

### Post by Crafty Kisses on 2009-05-13
Denyhosts!

---

### Post by scottuss on 2009-05-13
> **Codename said:**
> Denyhosts!

Codename, how did you get it to say <3 Katy Perry in the side? lol

---

### Post by weresheep on 2009-05-13
Moving the ssh daemon to another port does not make your box any more secure. The problem you had seems to be that any account is remotely accessible. This can be corrected by editing sshd_conifg and adding the AllowUsers directive to limit the accounts that have SSH access.

For example...

```
AllowUsers lazyart
```

With this in place (assuming the SSH daemon has restarted/reloaded the configuration changes) only account names listed after the AllowUsers will be allowed to log in through SSH. Of course, you also need to make sure those accounts have STRONG passwords or even move to key only based access.

Some additional tips for sshd_config are to make sure root login's are disabled

```
PermitRootLogin no
```

and to only use version two of the protocol

```
Protocol 2
```

There are plenty of online resources about setting up SSH securely and its worth spending some time reading up on it.

One last thing to mention is that if your box has been compromised then you cannot trust your logs to find out what an attacker has done. For peace of mind a format and reinstall may be the only way to go :cry:

-weresheep

---

### Post by Joeb454 on 2009-05-13
> **scottuss said:**
> Codename, how did you get it to say <3 Katy Perry in the side? lol

Members with over 3,500 posts (and forum staff) are allowed to choose their own user titles :)

---

### Post by Crafty Kisses on 2009-05-13
Ha beat me to it Joe. But yeah, just make 3500 useful posts. :)

---

### Post by Joeb454 on 2009-05-14
> **Codename said:**
> Ha beat me to it Joe. But yeah, just make 3500 useful posts. :)

Who said anything about useful?

I got all mine by posting +1's & questions ;)

j/k - Codename is right :)

---

