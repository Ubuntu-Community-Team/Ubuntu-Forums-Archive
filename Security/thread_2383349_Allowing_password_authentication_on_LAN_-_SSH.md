---
title: "Allowing password authentication on LAN - SSH"
date: 2018-01-23
forum: Security
---

### Post by sniper8752 on 2018-01-23
I would like to allow for password authentication when I am on my lan on my network.  I found this way to do it:

```
PasswordAuthentication no
ChallengeResponseAuthentication no

Match Address 10.0.0.0/8,172.16.0.0/12,192.168.0.0/16     PasswordAuthentication yes
```

Are there any security risks with doing this?  Is this a safe way to do this?

---

### Post by DuckHook on 2018-01-24
Please use standard fonts and styles, especially in your [noparse][CODE][/noparse] box. Odd fonts and formats make posts difficult to read.

I have always been uneasy with passwords on ssh. It's different if you are using something like *Telnet* or *FTP* which have nothing better, but *ssh* has a real security module that uses public/private keys. Why still use passwords, especially on a local lan where presumably no casual user needs access? I recommend RSA keys at all times, even in a relatively secure LAN environment.

[LIST=1]
[*]It's a good habit to cultivate, and
[*]It's far easier to use once the initial setup is done. No authentication needed because successful key match implies authentic user.
[/LIST]

---

### Post by TheFu on 2018-01-24
I think it will work, assuming the directive is on the line below and all the Match Address stuff is at the bottom of the config file.

I always run fail2ban on systems with ssh. If the default ssh port 22/tcp is used, then fail2ban config is good enough.

I always disable remote root ssh sessions, except withoutpasswd and only from the backup server.

BTW, for managing these settings, something like Ansible is helpful.

---

### Post by sniper8752 on 2018-01-24
So if I were to put my private key on my phone, and also add a passphrase to the key, would that be safe?  I'd be concerned with someone, at worst case scenario, stealing my phone while it's unlocked.  I guess phone encryption and password, and passphrase on the key would be good layers of security, so I would assume this would be ok.

---

### Post by TheFu on 2018-01-24
If any applications show advertising, forgetaboutit.  But we all have different risk acceptance comfort levels.

I don't consider any iOS or Android devices as secure because I find them useless without at least (1) 3rd party application.
An argument could be made that if you use a stock device, with the actively-supported, stock, OS, and never load any 3rd party applications (apps not from the OS vendor), then that *might* be secure enough to be trusted.  

Assuming complex, large, systems are secure is a bad idea, IMHO.

---

### Post by HermanAB on 2018-01-24
Use a long password (>12 characters) and you should be fine.

---

### Post by TheFu on 2018-01-24
> **HermanAB said:**
> Use a long password (>12 characters) and you should be fine.

Cracking passwords under 15 characters requires less than 24 hrs these days. 20+ characters (not words) is really needed to stay ahead of the technology. [https://arstechnica.com/information-technology/2013/03/how-i-became-a-password-cracker/](https://arstechnica.com/information-technology/2013/03/how-i-became-a-password-cracker/) explains how password cracking is done.  It is much different than most people expect AND much easier.

IMHO.

---

### Post by sniper8752 on 2018-01-24
> **TheFu said:**
> I don't consider any iOS or Android devices as secure because I find them useless without at least (1) 3rd party application.
An argument could be made that if you use a stock device, with the actively-supported, stock, OS, and never load any 3rd party applications (apps not from the OS vendor), then that *might* be secure enough to be trusted. 

Wouldn't this also apply to windows/mac/linux today?  Almost every eco system, I'd say, has 3rd party apps that we use on a daily basis.

---

### Post by TheFu on 2018-01-24
True, but Linux doesn't bypass local DNS settings and local firewall rules like Windows and Android do.  

Android app developers have a culture of spying and taking without asking. Ubuntu Desktop was doing this a few years ago too - I never used it then.  When Canonical did it, it was tied to things called "lenses", which were easily disabled and removed from a system. I've been running Ubuntu Server w/ openbox on my "desktop" systems since Unity was first made the default desktop.

---

### Post by sniper8752 on 2018-01-25
so if I allowed password authentication from 10.0.0.0/8, is there any way someone from the outside could say that they are in the ip range (maybe use ip spoofing), and bypass the key exchange?

---

### Post by TheFu on 2018-01-25
Spoofing IPs isn't useful for TCP connections.  Spoofing UDP is most often used for DDoS attacks.

Security should be layered. Don't trust a single roadblock, since it is common for a mistake to take 1 of those layers out. A config mistake or a program bug.
Edge firewall, system firewall, tcp-wrappers, fail2ban AND ssh-keys.  Passwords are the worst method for security.  In the business, we consider password use a complete failure. 

Getting "inside" isn't as hard as most people think.

---

### Post by Doug S on 2018-01-25
> **TheFu said:**
> Cracking passwords under 15 characters requires less than 24 hrs these days. 20+ characters (not words) is really needed to stay ahead of the technology. [https://arstechnica.com/information-technology/2013/03/how-i-became-a-password-cracker/](https://arstechnica.com/information-technology/2013/03/how-i-became-a-password-cracker/) explains how password cracking is done.  It is much different than most people expect AND much easier.That statement is in conflict with the very reference you referred to. A good 15 character password would take a very long time to crack.

---

### Post by TheFu on 2018-01-25
That reference is from early 2013. GPUs have been improved in 4 yrs. Cracking tools have improved. They deal with the xkcd "good" password methods.

But everyone has a different risk tolerance level.

---

### Post by QIII on 2018-01-25
For anything that might be exposed (and your LAN can be compromised) keys are a must -- passwords a NO GO.  And it's just not a good idea to get into bad habits even behind your router.

For services you consume on the web, if 2FA is offered, do that.  But even that is not likely to last much longer.  Multifactor authentication is probably going to be a must soon.

Using CPUs for cracking is old school.  High-powered GPUs have made the task orders of magnitude easier.  Just about any article more than 3 years old that predicts how long cracking takes and how quickly that will be done in the future is hopelessly outdated.  Even keys are at risk.

---

### Post by Doug S on 2018-01-27
> **QIII said:**
> Using CPUs for cracking is old school.  High-powered GPUs have made the task orders of magnitude easier.Yes, GPUs and clouds are included in one of the graphs in the article. However, even if things are magnitudes easier, I entered a 15 character password into a couple of cracking estimators and got 4,476,650,254,127 years, 8 months and infinity. Lets say the non infinity one is in error by a factor of a billion, that's still over 4 thousand years.

Lets look at it a different way: Assume the password character set is 84 characters (26 upper case, 26 lower case, and 32 other)(I've seen 95 used also). That would be 15**84 = 6e30 possible combinations.

I am not trying to derail the discussion, however, I can not let the statement of 24 hours stand, as it is misleading.

---

### Post by TheFu on 2018-01-31
I think we have different assumptions about what people will come up with around password choice.  I assume that a human will "choose" a terrible password, so making it longer and as random as possible will be helpful. Human created "good passwords", aren't good.

Brute forcing passwords over 13 characters is hard.  People cracking passwords don't do that except as a last resort. They use human intelligence and optimize their attacks.  Humans are terrible at creating passwords.  All those smart ideas that we think nobody else knows ARE known.

[http://www.netmux.com/blog/cracking-12-character-above-passwords](http://www.netmux.com/blog/cracking-12-character-above-passwords) explains how cracking 3-word passphrases using popular password selection methods is possible in 2 minutes. That was a 26-character password, but it followed a well-know pattern that can be tested very quickly.

An often referenced article on this: [https://www.troyhunt.com/im-sorry-but-were-you-actually-trying/](https://www.troyhunt.com/im-sorry-but-were-you-actually-trying/)
An interesting statistical study of known passwords from huge dumps: [https://p16.praetorian.com/blog/statistics-will-crack-your-password-mask-structure](https://p16.praetorian.com/blog/statistics-will-crack-your-password-mask-structure)  Over 50% of those passwords fit the patterns for the top 13 patterns.

My method is to avoid knowing as many passwords as possible and have as many as possible as long, random, computer created, different passwords for every login.  If it is a website and I can't use 2FA, then a 45+ character random password is the best I can do.  Plus, I'll never type it in, so why not use long, random, nearly impossible-to-type password?   12 or 55 characters - doesn't matter to my password manager.  For really important accounts, I don't know the login either.  It was randomly created to be long and strange too.  Of course, that only prevents attacks from people who don't have a list of valid logins.

The only shorter passwords I use are for systems with physical access.  Only my laptop uses 2FA during boot to unlock the encrypted disk and it isn't really 2FA - just a password and a long static passphrase programmed into a yubikey.  I tried using NFC to authenticate with a Nexus4, but it was very flakey. Being locked out of a phone isn't an option.  When on travel, I triple the phone unlock code, but around home, it is fairly easy to type. 
I'm still looking for a great way to use U2F for local logins that isn't too hard to implement and works disconnected.  But life keeps putting higher priority jobs in the way.

---

