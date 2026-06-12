---
title: "Howto set the Ubuntu password with less than 6 characters"
date: 2008-06-25
forum: Security
---

### Post by multisimple on 2008-06-25
This is a how to change your password with less than 6 characters.

Why? in case you need to.

This post is split into 2 different ways to do this.

1. **First way** and easiest to change password
```
sudo passwd multisimple
```

where multisimple is the user name you want to change
Done.


2. **Second way**, a bit harder but gets the job done
```

sudo gedit /etc/pam.d/common-password
```

add the min=?
where ? is a number, add it at the end of password

```
password   requisite   pam_unix.so nullok obscure md5 min=1
```

now open terminal

```
passwd
```

and set your new password

Problem - what if the password is rejected because password is too similar?

remove obscure from the line

```
password   requisite   pam_unix.so nullok md5 min=1
```

now open terminal

```
passwd
```

and set your new password

hope this helps

thanks to the cog for helping out

---

### Post by wootah on 2008-06-25
:(

---

### Post by Dr Small on 2008-06-25
A simpler way, would be to run:
```
grub-md5-crypt
```

Enter your shorter password, and when finished, it will output the md5crypt string for you. Then edit the /etc/shadow file and replace the password respectively.

---

### Post by wootah on 2008-06-25
> **Dr Small said:**
> A simpler way, would be to run:
```
grub-md5-crypt
```Enter your shorter password, and when finished, it will output the md5crypt string for you. Then edit the /etc/shadow file and replace the password respectively.
:)

---

### Post by multisimple on 2008-06-28
> **Dr Small said:**
> A simpler way, would be to run:
```
grub-md5-crypt
```

Enter your shorter password, and when finished, it will output the md5crypt string for you. Then edit the /etc/shadow file and replace the password respectively.

this is only for grub?, this thread is for the main ubuntu/user/root password

---

### Post by The Cog on 2008-06-28
Simplest I know would be
**sudo passwd cog**
or whatever the username you wnat to change is, because root doesn't have that 6-character limit.

---

### Post by multisimple on 2008-06-28
> **The Cog said:**
> Simplest I know would be
**sudo passwd cog**
or whatever the username you wnat to change is, because root doesn't have that 6-character limit.

thank you!
that saves me alot of trouble!

updated my post

---

### Post by rlhawk1 on 2008-12-09
Thanks!

---

### Post by pietjanjaap on 2008-12-09
Ofcourse this is not safe, so do not do this.

---

### Post by HermanAB on 2008-12-10
Hmm, remember to send out an invitation to all the script kiddies to run their password crackers against your machine.

Every time I have to repair a hacked server, it is due to someone who thought it is cool to have a 4 character password.

Good luck (you'll need it),

Herman

---

### Post by bodhi.zazen on 2008-12-10
See this thread for an example :

[http://ubuntuforums.org/showthread.php?t=1007280](http://ubuntuforums.org/showthread.php?t=1007280)

---

### Post by koenn on 2008-12-11
> **HermanAB said:**
> Hmm, remember to send out an invitation to all the script kiddies to run their password crackers against your machine.

Every time I have to repair a hacked server, it is due to someone who thought it is cool to have a 4 character password.

Good luck (you'll need it),

Herman

no need to send out invitations - those kiddies will come uninvited :)

---

### Post by lavinog on 2008-12-11
> **koenn said:**
> no need to send out invitations - those kiddies will come uninvited :)

And if the computer doesn't have internet access how do they come?

---

### Post by Dr Small on 2008-12-11
> **lavinog said:**
> And if the computer doesn't have internet access how do they come?
The only secure system is the one not connected to the internet, and even that can be cracked by the person sitting at the terminal.

---

### Post by go_beep_yourself on 2008-12-12
Not a good idea. I think the feature that prevents you from making a password less than 6 characters was made for a good reason. If you choose a short password, it is a weak one and easier to crack with bruteforce and other ways.

---

### Post by koenn on 2008-12-12
> **lavinog said:**
> And if the computer doesn't have internet access how do they come?

> **Dr Small said:**
> The only secure system is the one not connected to the internet, and even that can be cracked by the person sitting at the terminal.
^+1 

I could tell you a couple of stories of office computers I logged on to by guessing short, simple passwords, or about PC's for public used that were networked (although not connected to the internet), where a knowledgeable user could gain network access and try to log on to a server ... 

weak passwords = false sense of security, no matter what the circumstances are. 
If security is not an issue, don't use passwords at all.

---

### Post by lavinog on 2008-12-12
> **koenn said:**
> 
weak passwords = false sense of security, no matter what the circumstances are. 
If security is not an issue, don't use passwords at all.

There are some setups where security isn't an issue. Not all computers will be used in a corporate/office enviroment.

I find it interesting that if I want to build a setup with no keyboard for a community computer for everyone to use, with no password (no keyboard makes entering passwords difficult), I find many ubuntu users that believe that there should be no reason to have any user accounts with no password.
Ubuntu gives you the freedom to do what ever you want as long as you have a password with more than 6 characters...security is everything, but everyone forgets that a live cd can bypass any security...If a system dual boots to windows a user can manipulate the files on the ubuntu partition also.

passwords = false sense of security

---

### Post by Dr Small on 2008-12-12
> **lavinog said:**
> 
Ubuntu gives you the freedom to do what ever you want as long as you have a password with more than 6 characters...security is everything, but everyone forgets that a live cd can bypass any security...If a system dual boots to windows a user can manipulate the files on the ubuntu partition also.

passwords = false sense of security

I respectfully disagree.
A system that has full disc encryption can not be accessed without a "false sense of security" (aka, password). The only thing keeping intruders from reading my encrypted documents is this annoying thing called a "password".

I understand the realm of the discussion, as to where anyone can boot a livecd and bypass a users password. Yes, that is trivial. But to make a blanket application and say that passwords in general are a false sense of security? They are the only thing that is keeping the intruder out, and allowing us in.

One could say that a lock on your front door is a false sense of security, as one could easily break the window and enter. But the lock is what keeps the criminal from entering through the door, hence effectively keeping him out.

I understand that there are ways around our security methods, such as loading a liveCD and changing the password, or opening a unlocked window and changing the lock. But to say in the general sense that passwords are useless is to nullify our best means of authentication.

---

### Post by lavinog on 2008-12-12
> **Dr Small said:**
> 
I understand that there are ways around our security methods, such as loading a liveCD and changing the password, or opening a unlocked window and changing the lock. But to say in the general sense that passwords are useless is to nullify our best means of authentication.

I agree with your points. I wasn't meaning it to be in general. I was trying to point out that weak passwords can be no different than strong passwords (in certain circumstances):
If the computer does not have remote access, then the hacker has no choice but to locally access the machine...why would he bother with brute force or dictionary attacks on it if he can bypass the security with a bootable cd. In this case the machine would need a bios password to prevent booting the cd (which if the hacker really wants, he can just reset the bios password)
In some enviroments, the stricter the password requirement, the easier for a hacker to find someone's password laying around on. My school, for instance, has a 60 day expiration, 10 character minimum, and requires mixed case alpha-numeric with at least one symbol. Many students have their passwords written down in their notebook, and many are predictable enough to just increment the number each time they change the password.

I also agree that a 6 character minimum is not a big deal. I guess I just don't know why 6 characters is really so much better than 5...the only reason I can think of is brute force attacks, but if the attacker knows that every ubuntu system requires a minimum of 6 characters, then they can start with 6 character passwords. If the attacker isn't concerned with time then the system will be compromised reguardless.

I am not trying to say passwords are useless or that reducing the strength of the password is a good idea...I just think there can be circumstances where security has to be approached differently.

---

### Post by Dr Small on 2008-12-12
Thanks for the clarification. :)

---

### Post by koenn on 2008-12-12
> **lavinog said:**
> There are some setups where security isn't an issue. Not all computers will be used in a corporate/office enviroment.

I find it interesting that if I want to build a setup with no keyboard for a community computer for everyone to use, with no password (no keyboard makes entering passwords difficult), 

like I said, if security is not an issue, forget about passwords

---

### Post by koenn on 2008-12-12
> **lavinog said:**
> 
I also agree that a 6 character minimum is not a big deal. I guess I just don't know why 6 characters is really so much better than 5...the only reason I can think of is brute force attacks, but if the attacker knows that every ubuntu system requires a minimum of 6 characters, then they can start with 6 character passwords. If the attacker isn't concerned with time then the system will be compromised reguardless.
simply trying every combination of  4 characters is a matter of minutes. 6 characters can take hours, or days if you have to take into account numbers, punctuation marks etc. 5characters is in between. simple [a-z] 5 characters is still a matter of minutes, complex 5 char passwords can take a few hours. 6 characters complex passwords is a good rule of thumb.

The timing matters because 
a/ as an attack takes longer, chances to be caught increase
b/ skript kiddies don't target specifiek machines, they just seek out low hanging fruit, so they scan entire address ranges and spend a few seconds / minutes on each target, trying to crack weak passwords. If they fail, they move on to the next target, but if they succeed, you're toast.

---

### Post by Dr Small on 2008-12-12
> **koenn said:**
> simply trying every combination of  4 characters is a matter of minutes. 6 characters can take hours, or days if you have to take into account numbers, punctuation marks etc. 5characters is in between. simple [a-z] 5 characters is still a matter of minutes, complex 5 char passwords can take a few hours. 6 characters complex passwords is a good rule of thumb.


That's why I use 10 character passwords.

---

### Post by lavinog on 2008-12-13
> **koenn said:**
> simply trying every combination of  4 characters is a matter of minutes. 6 characters can take hours, or days if you have to take into account numbers, punctuation marks etc. 5characters is in between. simple [a-z] 5 characters is still a matter of minutes, complex 5 char passwords can take a few hours. 6 characters complex passwords is a good rule of thumb.

What are you basing this on?
Are you talking about testing out passwords on a login or doing a brute force on password hashes?

a 4 character password with only lowercase letters would yeild 26^4=456976 combinations.
if each login attempt takes 1 sec ( I believe 6 secs is what it actually takes) we have 456976/3600s=126.9 hours to try every combination...if we allow mixed case and numbers then the time goes up significantly (I think 50^4/3600=6250000/3600=1736 hours is pretty close)
Granted the hacker will find the password before finishing every possible combination. Also if the user is using a weak password formed by a word or name, then the time could be in less than a couple of mins.

If the hacker is checking password hashes, then my point is that the machine was already comprimised and even a 12 character password can be brute forced in a short period of time.

In the real world though, hackers have more tools at their disposal and generally don't do brute force attacks like this (trying every possible combination instead of dictionary based attacks) unless they are really desperate to attack your machine.

---

### Post by koenn on 2008-12-13
> **lavinog said:**
> What are you basing this on? ..;
several sources, this one a.o. : [http://users.telenet.be/mydotcom/program/shell/bruteforce.htm](http://users.telenet.be/mydotcom/program/shell/bruteforce.htm)
Granted, this measures the time it takes to *generate* passwords. Actually trying them against an interactive login program might take longer, as network latency and response time of the login program need to be factored in.
On the other hand, password crackers will speed up the process by parrallelising the attack, e.g. by initiating multiple attempts against the same machine, or just randomly attack a range of machines and see which ones breaks first. 
So, as an indication of the order of magnitude, I think this is valid.

This simulator seems to return similar results :
[http://www.hackosis.com/projects/bfcalc/bfcalc.php?](http://www.hackosis.com/projects/bfcalc/bfcalc.php?)


> **lavinog said:**
> 
a 4 character password with only lowercase letters would yeild 26^4=456976 combinations.
if each login attempt takes 1 sec ( I believe 6 secs is what it actually takes) we have 456976/3600s=126.9 hours to try every combination...if we allow mixed case and numbers then the time goes up significantly (I think 50^4/3600=6250000/3600=1736 hours is pretty close)

[http://freeworld.thc.org/thc-hydra/hydra_start.jpg](http://freeworld.thc.org/thc-hydra/hydra_start.jpg)
this is a screenshot of a parrallized brute force crack. It shows ~14500 attempts per minute, This would handle your 456976 combinations in approx 32 minutes, i think.


> **lavinog said:**
> 
Granted the hacker will find the password before finishing every possible combination. 
 I don't know much about statistics and probability, but I'd guess that there's a 50% probability that the password is found with only half of the combinations tried, and therefore half of the time, the password will be cracked in half of the time it takes to test all possibilities. 

> **lavinog said:**
> 
Also if the user is using a weak password formed by a word or name, then the time could be in less than a couple of mins.

Very good point. Someone who's tempted to use short, easy to remember passwords will presumably also be tempted to use dictionary words, names, repetitions of characters or syllables, or predictable formats (append a number, ...). Password crackers will try those too.

> **lavinog said:**
> 
If the hacker is checking password hashes, then my point is that the machine was already compromised and even a 12 character password can be brute forced in a short period of time.
there are levels of compromised. A cracker my have broken in to an account or an application and use that to retrieve a password hash, then go on to crack the hash to gain access to the more interesting accounts. 

> **lavinog said:**
> 
In the real world though, hackers have more tools at their disposal and generally don't do brute force attacks like this (trying every possible combination instead of dictionary based attacks) unless they are really desperate to attack your machine.
True. And what if a cracker/script kiddie figures that he can increase his chances by adding some 'random' strings to his wordlists (like strings of spaces, random combinations of 2,3 or 4 characters, ...) or uses a dictionary cracker that also tries permutations and common variations of dictionary words ?

---

### Post by lavinog on 2008-12-13
> **koenn said:**
> several sources, this one a.o. : [http://users.telenet.be/mydotcom/program/shell/bruteforce.htm](http://users.telenet.be/mydotcom/program/shell/bruteforce.htm)
Granted, this measures the time it takes to *generate* passwords. Actually trying them against an interactive login program might take longer, as network latency and response time of the login program need to be factored in.
On the other hand, password crackers will speed up the process by parrallelising the attack, e.g. by initiating multiple attempts against the same machine, or just randomly attack a range of machines and see which ones breaks first. 
So, as an indication of the order of magnitude, I think this is valid.

This simulator seems to return similar results :
[http://www.hackosis.com/projects/bfcalc/bfcalc.php?](http://www.hackosis.com/projects/bfcalc/bfcalc.php?)



[http://freeworld.thc.org/thc-hydra/hydra_start.jpg](http://freeworld.thc.org/thc-hydra/hydra_start.jpg)
this is a screenshot of a parrallized brute force crack. It shows ~14500 attempts per minute, This would handle your 456976 combinations in approx 32 minutes, i think.

Yes, parallelizing the attack would speed it up. The screenshot for hydra was showing a ftp connection. and the README file for thc-hydra says:
> through the parallizing feature, this password cracker tool can be very
fast, however it depends on the protocol. The fastest is generally POP3,
then FTP, then Telnet, and the least IMAP.
Ftp and telnet is disabled in ubuntu because of the security issues.
I think there may be no limit on how many concurrent login attempts can be made with them, but for ssh the number is much less.
The defaults for openssh are:
> MaxAuthTries
             Specifies the maximum number of authentication attempts permitted
             per connection.  Once the number of failures reaches half this
             value, additional failures are logged.  The default is 6.

     MaxSessions
             Specifies the maximum number of open sessions permitted per net-
             work connection.  The default is 10.

     MaxStartups
             Specifies the maximum number of concurrent unauthenticated con-
             nections to the SSH daemon.  Additional connections will be
             dropped until authentication succeeds or the LoginGraceTime ex-
             pires for a connection.  The default is 10.

So to correct my response earlier: if a login attempt takes 1 sec on one connection, then with parallelization, 10 login attempts can be made in 1 sec.
so 12.69 hours to try every combination of a 4 lowercase letter character password.
Also the attacker needs to know a username for the attack since root isn't available by default in ubuntu.
I might see if I can compile that hydra program...it says i need to get some libraries.

---

### Post by Chayak on 2008-12-13
Yet most of this discussion (argument) is based on the fact that someone lazy enough to use only six characters in a password won't be lazy enough as well to use a word from a dictionary.  The attack time decreases greatly because your not looking for a randomly generated six character password but a short possibly modified dictionary word.

---

### Post by koenn on 2008-12-14
> **lavinog said:**
> 
Ftp and telnet is disabled in ubuntu because of the security issues.
I think there may be no limit on how many concurrent login attempts can be made with them, but for ssh the number is much less.

Also the attacker needs to know a username for the attack since root isn't available by default in ubuntu.


Which only goes to show that security is complex : it's a combination of measures that complement and reinforce each other. 
Therefor, weakening 1 aspect (such as using a weak password) weakens the overall system. It's obviously up to you to decide/guestimate how acceptable that risk is and make an informed decision.
On the other hand, you may ask your self what you gain by having to type 2 characters less when you log in.

---

