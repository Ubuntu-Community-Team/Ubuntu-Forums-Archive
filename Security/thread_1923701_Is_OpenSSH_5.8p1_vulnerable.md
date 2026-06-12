---
title: "Is OpenSSH 5.8p1 vulnerable?"
date: 2012-02-11
forum: Security
---

### Post by Trinley on 2012-02-11
Hi!

I installed OpenSSH twice and twice I got a 'friendly' visitor.
The first time I noticed a manual install of ssh: I removed OpenSSH package, but there was still a sshd being started. I noticed a config file in /etc that appeared to have come from an OpenBSD or FreeBSD distro.

I am planning to use ubuntu server edition on my server - but it is scary if there is a vulnerability in OpenSSH!

I am using a separate install of ubuntu oneiric on eeepc that is backup'ed and can be restored in minutes. I am using this install to play around and also to visit dangerous websites, so there is a chance that they are using other programs like firefox as way in, what wouldn't be a problem on the server. Also, I haven't bothered with iptables, what makes me wonder why ubuntu is not coming with some default rules?

Does anyone have experience with the EnGarde security community distro?

On the OpenSSH website they say that Portable OpenSSH prior to 5.8p2 is vulnerable.
[http://www.openssh.org/security.html](http://www.openssh.org/security.html)

Thanx for any input!

Trinley

---

### Post by unspawn on 2012-02-11
> **Trinley said:**
> I installed OpenSSH twice and twice I got a 'friendly' visitor.
Best limit SSH exposure by denying root access (should be off by default), only using pubkey auth and blocking access using 'fail2ban' or equivalent (: AND, not OR!). 


> **Trinley said:**
> The first time I noticed a manual install of ssh: I removed OpenSSH package, but there was still a sshd being started. 
What do you mean with "manual install of ssh"? In short all package ops require root privileges so this is either mis-perception (service not stopped on or prior to package removal) or a rogue SSH daemon (ranging from argv[0] mimicking to elevated privileges). Unfortunately it's a common error for experienced and new Linux users alike to delete anything anomalous immediately instead of properly investigating the (perceived) situation.


> **Trinley said:**
> I noticed a config file in /etc that appeared to have come from an OpenBSD or FreeBSD distro.
The default configuration files OpenSSH-portable is shipped with have BSD comments in them because the package originates from OpenBSD.


> **Trinley said:**
> Also, I haven't bothered with iptables, what makes me wonder why ubuntu is not coming with some default rules?
I'd say that instead of wondering you should just create the appropriate rules.


> **Trinley said:**
> On the OpenSSH website they say that Portable OpenSSH prior to 5.8p2 is vulnerable.
Yes, but not *BSD, Linux, OS X or Cygwin as they don't use 'ssh-rand-helper'. Always make it a habit to check the advisories for details, in this case [http://www.openssh.com/txt/release-5.8p2](http://www.openssh.com/txt/release-5.8p2) .

---

### Post by Trinley on 2012-02-11
> **unspawn said:**
> 
What do you mean with "manual install of ssh"? In short all package ops require root privileges so this is either mis-perception (service not stopped on or prior to package removal) or a rogue SSH daemon (ranging from argv[0] mimicking to elevated privileges). Unfortunately it's a common error for experienced and new Linux users alike to delete anything anomalous immediately instead of properly investigating the (perceived) situation.
The default configuration files OpenSSH-portable is shipped with have BSD comments in them because the package originates from OpenBSD.


Well, I removed (purged) the package and next day I still found sshd. As the OpenSSH package was already purged one boot before, I killed the process and deleted sshd manually, just to be sure for the moment. Then I looked in /etc and I found a conf file with few settings, like the option about root-login was completely missing... I dunno, does root-login have to be explicitly denied? Well, after that I just wiped the install, meaning I restored it using partclone (just overwriting everything).

Well, I visit insecure websites and I noticed that firefox is getting affected (sometimes the context menu won't work properly anymore), just today after writing the first posting I noticed that I could'nt restart Ubuntu, and again I wiped it ;)

I know you won't like it but, at least, ubuntu is not as save out-of-the-box as it could be!
Why isn't the firewall active by default?
Just as packages come with appamour-profiles, they could also ship with specific iptable-rules, couldn't they?

Ok, whatever, there are some nice tutorials from bodhi...something... (a fellow buddhist?), I will study them and maybe I can turn my 'adventure'-install into a kind of forensic honeypot ;)

Trinley

---

### Post by unspawn on 2012-02-11
> **Trinley said:**
> Well, I removed (purged) the package and next day I still found sshd. As the OpenSSH package was already purged one boot before, I killed the process and deleted sshd manually, just to be sure for the moment. 
You didn't say you already rebooted the machine. Anyway, deleting the binary means you don't have any "evidence" so you can't search the file system for similar MAC times or look for other clues running 'strings' on it.


> **Trinley said:**
> Then I looked in /etc and I found a conf file with few settings, like the option about root-login was completely missing... 
AFAIK packages install OpenSSH configuration in /etc/ssh/ and not /etc.


> **Trinley said:**
> I dunno, does root-login have to be explicitly denied? 
IIRC the default for PermitRootLogin is "yes".


> **Trinley said:**
> Why isn't the firewall active by default?
See [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) .

---

