---
title: "Does this look like someones shelled into my box?"
date: 2008-04-26
forum: Security
---

### Post by Biggus on 2008-04-26
Comment Deleted

---

### Post by Monicker on 2008-04-26
It looks to me like an established connection.  Did you check auth.log to see what it shows?

---

### Post by Biggus on 2008-04-26
Comment Deleted

---

### Post by Chayak on 2008-04-26
No matter what you do you are never 'crackproof' security as it is is making yourself a hard target and keeping as low a profile as possible.  Though two of the biggest things in making yourself a difficult target are using strong passphrases and changing your ssh service to a nonstandard port.  Most bots and quick scans only look at the services in the first 1024 'known' ports.  If you move your ssh service up to 2222 or such you'll dramatically decrease the number of attacks.

---

### Post by Anduu on 2008-04-27
Since most hack attempts are brute force type attacks,denyhosts goes a long ways to protect SSH

---

### Post by Oldsoldier2003 on 2008-04-27
> **Chayak said:**
> No matter what you do you are never 'crackproof' security as it is is making yourself a hard target and keeping as low a profile as possible.  Though two of the biggest things in making yourself a difficult target are using strong passphrases and changing your ssh service to a nonstandard port.  Most bots and quick scans only look at the services in the first 1024 'known' ports.  If you move your ssh service up to 2222 or such you'll dramatically decrease the number of attacks.

A properly secured server wont be cracked by a script kiddie. Yes moving to a higher port will decrease the amount of script kiddies that probe you, but in itself it doesn't **do** anything for *security*.

IMO the steps to securing SSH are more along the lines of:

disable root login
disable ssh1 protocol
use allow users and limit the users list to those that need access (not all accounts "need" ssh)
disable password authentication and require public key auth (if you do this you don't need fail2ban or denyhosts)

Upping to port 2222 is an issue... because, well its a port above 1024. I know not everyone needs the lower privileged ports and its a throwback to the past. I guess i just have issue with using nonstandard ports for standard services :) If I were to change the port, I wouldn't select 2222 because it is commonly used for SSH by people that change the default port. I'm sure the advanced script kiddies know that too, so instead of every script kiddie banging on your box you'll only get half. Besides that, if a semi serious craker wants to probe your box they'll find the open services anyhow and they'll do it in a manner that doesn't set off the warning flags that the brute forcing SK's will. So instead of security by obscurity I'll opt for actually locking down the box.

Just my 2 cents take it with a grain of salt and do as you will.

---

### Post by Oldsoldier2003 on 2008-04-27
> **Anduu said:**
> Since most hack attempts are brute force type attacks,denyhosts goes a long ways to protect SSH

+1 

to the OP if you use denyhosts be sure to setup /etc/hosts.allow so that you don't lock yourself out. Also monitor /etc/hosts.deny and use the info you gain there to deny access to all services since denyhosts only blocks SSH connections to "banned" hosts

---

### Post by Biggus on 2008-04-27
Comment Deleted

---

### Post by Dr Small on 2008-04-27
SSH Keybased Auth is easy. I use it for every machine on the network (that has SSH), and the key can be passwordless (but this decreases security if your private key would ever be stolen).

But by setting up a SSH key, and enabling KeyBasedAuth in for the SSH Server, it will automatically reject requests without the proper private key. They wouldn't even be given the chance to bruteforce your password.

I have a simple guide for setting it up at my blog, albeit for a passwordless key, you don't have to have passwordless. It should give you the fundamentals for setting up a SSH key and enabling KeyBasedAuth on the server.

[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

Dr Small

---

### Post by brian_p on 2008-04-27
> **Biggus said:**
> Hi guys.

I came home drunk last night, and, having upgraded to 8.04 the other day, thought I would have a mess around to see what sort of stuff had changed.

I loaded firestarter up, and had a little mess around, when I noticed what looked to be someone shelled into my box.

I've taken a screenshot, and attached it to this post hopefully, and, unless I'm reading the display incorrectly, it appears to show that a remote host has an open connection to my box on port 22.

Could this be correct? If so, doesn't that mean that, essentially, my ssh server, and subsequently, my box, have been 'cracked'?

(Oh yeah, my own IP is blurred in the attatchment)

Looks like another one of these pathetic attempts to log into a box via ssh. Your logs will tell you for sure and confirm it did not succeed. Even if your password could be stronger it is highly doubtful a valid username was guessed so, if I were you, I'd go for ssh keys and have another few drinks.

Oldsoldier2003 gives the best reason for not moving sshd from port 22 but another one is why let yourself be intimidated into changing the default port? Actually, it is can be fun keeping an eye on the doomed attempts at cracking.

I'm unsure quite what role firestarter was supposed to play but it didn't appear to do much.

---

