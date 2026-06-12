---
title: "How secure is ubuntu?"
date: 2006-12-03
forum: Server Platforms
---

### Post by rigdzinthar on 2006-12-03
well,
how secure is ubuntu?
I have valuble information on my computer that i do not want compromised,
will it be safe?
...

---

### Post by dbbolton on 2006-12-03
more secure than windows.

---

### Post by johnnymac on 2006-12-03
So - security is only as good as the individual using the system.  Ubuntu is a good as any if you manage your security correctly.

---

### Post by atoponce on 2006-12-03
As secure as the user is who is maintaining the system.

However, with that said, Ubuntu applications do not listen for requests on the network.  I think Ubuntu is the only distro, at least major distro, that does this.

---

### Post by rigdzinthar on 2006-12-03
that sounds good...
then how do i be a secure user?

---

### Post by atoponce on 2006-12-03
Well, for starters
[LIST]
[*]  Pick a good strong passphrase for your user account, and don't pass it out.
[*]Don't enable the root account on your system (learn how to use sudo).
[*]Don't enable untrusted 3rd party repositories (if you can do without the latest and greatest, the better).
[*]If running a server, run the daemons on ports different than default.
[*]Don't run an FTP server, use OpenSSH.
[*]ALWAYS run and install updates from Ubuntu.
[*]ALWAYS patch separately installed software.[/LIST]Basically, just use your head. :)

---

### Post by aysiu on 2006-12-03
This won't help much for servers, but if you're thinking desktop security, read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by houstonbofh on 2006-12-03
> **atoponce said:**
> Well, for starters
[LIST]
[*]  Pick a good strong passphrase for your user account, and don't pass it out.
[*]Don't enable the root account on your system (learn how to use sudo).
[*]Don't enable untrusted 3rd party repositories (if you can do without the latest and greatest, the better).
[*]If running a server, run the daemons on ports different than default.
[*]Don't run an FTP server, use OpenSSH.
[*]ALWAYS run and install updates from Ubuntu.
[*]ALWAYS patch separately installed software.[/LIST]Basically, just use your head. :)
Good advice, but my SSH is getting brute forced a lot more than my FTP.  A good firewall (not firewall software, but a firewall on a different box) only allowing FTP or SSH access from specific IP addresses or subnets would also help.  And keep an eye on /var/log/auth.log.0 while you are at it.  (It may depress you)

---

### Post by atoponce on 2006-12-03
> **houstonbofh said:**
> Good advice, but my SSH is getting brute forced a lot more than my FTP.  A good firewall (not firewall software, but a firewall on a different box) only allowing FTP or SSH access from specific IP addresses or subnets would also help.  And keep an eye on /var/log/auth.log.0 while you are at it.  (It may depress you)

Change the port of your SSH and FTP (my advice, would be to ditch the FTP) to something high.  Way high.  Like, 32466 for SSH and 44567 for FTP (two random numbers off the top of my head).  I think you'll find that your brute force attacks will pretty much cease.  8)

---

### Post by coach-x on 2006-12-03
> **houstonbofh said:**
> Good advice, but my SSH is getting brute forced a lot more than my FTP.  A good firewall (not firewall software, but a firewall on a different box) only allowing FTP or SSH access from specific IP addresses or subnets would also help.  And keep an eye on /var/log/auth.log.0 while you are at it.  (It may depress you)

We changed our ssh port about a year ago after having non stop brute force attacks on our servers.  Have not had one unauthorized connection attempt since.

---

### Post by houstonbofh on 2006-12-04
> **coach-x said:**
> We changed our ssh port about a year ago after having non stop brute force attacks on our servers.  Have not had one unauthorized connection attempt since.
As I block more and more of Asia in my firewall, I get less and less attacks.  Many ways to skin a cat...

---

### Post by Patrick-Ruff on 2006-12-05
yeah, mostly with ubuntu you are as secure as your password, if you pick a password that would take a password cracker 5 days to guess, you're fine. most-often you'll restart your computer and break the connection to the hacker before then.

most of the time though, passes like 39xrd52 take years to crack :).

good luck

---

### Post by MJN on 2006-12-05
5 days?! That ain't a password... 

To put it into perspective, an 8-digit character password using letters/characters/symbols should be your minimum and would take upto 500 years to crack running at 500,000 attempts/second.

(Edit: There's a nice table with figures at [http://lastbit.com/rm_bruteforce.asp](http://lastbit.com/rm_bruteforce.asp) if anyone's curious)

However, if the only way into your machine is via SSH then you ought to be restricting anyone that can manage 500,000 login attempts per second... ;)

Mathew

---

### Post by Patrick-Ruff on 2006-12-05
hah yeah. all of my passwords are codes, so I guess I'm safe :)

just realized something . . . MJN has been here as long as I have, and we have almost equal posts :D.

awesomeness.

---

### Post by az on 2006-12-05
> **atoponce said:**
> Well, for starters
[LIST]
[*]  Pick a good strong passphrase for your user account, and don't pass it out.
[*]Don't enable the root account on your system (learn how to use sudo).
[*]Don't enable untrusted 3rd party repositories (if you can do without the latest and greatest, the better).
[*]If running a server, run the daemons on ports different than default.
[*]Don't run an FTP server, use OpenSSH.
[*]ALWAYS run and install updates from Ubuntu.
[*]ALWAYS patch separately installed software.[/LIST]Basically, just use your head. :)

Most importantly, "Keep up to date with security updates."

---

