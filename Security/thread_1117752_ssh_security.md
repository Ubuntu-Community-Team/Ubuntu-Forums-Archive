---
title: "ssh security"
date: 2009-04-06
forum: Security
---

### Post by hellz99 on 2009-04-06
I've read that using public key auth is more secure than passwords...I'm guessing because of the length.  

I typically run password, but set my hosts.deny to ALL and my hosts.allow to 192.168. for my local network and one other IP which is outside (it's work).  I'm thinking this is about as safe as I can get....am I missing something?

My reason for not going to keys vs passwords is because I dont want my key on my computer at work, and I like to use a pw if I'm sshing from another computer on my local network.  Is there something I could do to secure a bit more?

---

### Post by HermanAB on 2009-04-06
That is fine, just use looooong passwords.  I use 16 char semi pronounceable and has never been hacked.  Common password dictionaries go up to 8 characters, so obviously you got to use a password longer than that.

---

### Post by cdenley on 2009-04-06
> **HermanAB said:**
> That is fine, just use looooong passwords.  I use 16 char semi pronounceable and has never been hacked.  Common password dictionaries go up to 8 characters, so obviously you got to use a password longer than that.

While increasing the password length does strengthen your password against brute-force exponentially, I don't agree that there is a magic number such as greater than 8 characters which protects you from dictionary attacks. I once set up a honeypot that logged what passwords were used when attackers tried to authenticate on an SSH server. 32 of 205 attempts used a password greater than 8 characters. For the FTP honeypot, 2,365 of 64,791 attempts used a password greater than 8 characters.

---

### Post by bodhi.zazen on 2009-04-06
Keys are more secure then passwords, and since you allow a log in  from the internet I suggest you use keys.

Just my 2c ;)

You can also append your /etc/ssh/sshd file

AllowUsers <You>@ip_address

or better , configure your /etc/hosts.allow and /etc/hosts.deny

---

### Post by hellz99 on 2009-04-06
> **bodhi.zazen said:**
> Keys are more secure then passwords, and since you allow a log in  from the internet I suggest you use keys.


Yes, but then I'd need to have that key file on a computer at work which doesn't seem secure to me.  On the other hand, the password may be weaker, but it's only location is in my skull.

---

### Post by bodhi.zazen on 2009-04-06
The ssh key can be on a flash drive and one needs both the key and a password to log in (keys use passwords too).

---

### Post by jdong on 2009-04-07
(1) Keys are stronger because they tend to be 2048 to 4096 bits, which corresponds to 256 to 512 character long completely random passwords, and much longer than that if you consider how many letters you can actually type of the 7-bit ASCII encoding.

(2) Keys are also stronger because you can identify each public key separately. If you make a private key per machine and one machine gets stolen, all you have to do is revoke its corresponding key, not to mention you can also check if anyone else used that key in question. This is a much lesser headache than a password compromise.

For those reasons, I highly recommend the SOLE use of SSH keys for servers or desktops that are logged in via SSH fairly often.


Note that unless you create a passwordless key (NOT RECOMMENDED), the key itself is encrypted by a password of your choice, which means you still need to have both the key and a local password to unlock the key. This should make it fairly safe to store your key even on public-access file storage mechanisms.

---

### Post by Stupendoussteve on 2009-04-07
If you are really concerned, you could also run the ssh server on a non-standard port. I do this, along with key based authentication, and have yet to have a log of someone other than myself even connecting to the ssh server, let alone trying to login with incorrect credentials.

---

### Post by jdong on 2009-04-07
> **Stupendoussteve said:**
> If you are really concerned, you could also run the ssh server on a non-standard port. I do this, along with key based authentication, and have yet to have a log of someone other than myself even connecting to the ssh server, let alone trying to login with incorrect credentials.

Well security through obscurity only works until someone figures out your obscurity -- and if someone had reason to specifically target YOU, I think it's fairly obvious to work around SSH on a different port.

The only place where I move SSH to a different port is on power-sensitive or CPU-crippled devices where 20-30 SSH accesses per second actually puts a huge load on the system.

On my servers with 1.6GHz+ chips I could care less if someone is hammering full time at my pubkey-only accounts.

---

### Post by kevdog on 2009-04-08
Run a port knocker such as fwknop to provide enhanced security measures.  The knock sequence can also use either a password or gpg key.  The password is encrypted and then sent over the wire.  I'm not sure if transmission of the ssh password is hashed or encrypted. Something tells me its still plain text, however I could be wrong.  The password for fwknop is passed in a packet containing other information such as a randomly chosen non-replayable session key, so hence you couldn't replay the packet to gain access to the ssh server even if you were able to isolate the packet containing the password.  I'm not sure if ssh provides such security.

SSH in combination with rate limiters offered by iptables in combination with tools such as modification of the /etc/hosts files (allow and deny) make up a very secure method to lock down the server.  That is just my two cents.  Port knockers usually don't get mentioned in the same breath as these approaches because they originated as a hacking tool, however with projects such as fwknop they have developed into yet another security measure that can be implemented.

---

### Post by inphektion on 2009-04-08
I needed to find a nice tradeoff between useability/flexibility and security.  For a few of my ssh linux boxes I need to be able to get to them from anywhere.
So I did the following
1. set it up on a non standard port
2. create one user who could ssh in and only gave him access so obviously Permitrootlogin is set to no.
3. configured fail2ban so anyone trying 5 or more attempts was IP banned for 20 minutes.

So after #1 that stops a lot of automated scripts.  The ones that find the port based on protocol and still run in my logs they used to try hundreds of different username/passwords combo's to guess.  I've made sure the one username I give ssh access to is something they would not normally guess, like (jyx54p2).
Even if they guess that username they have limited attempts until they are IP banned.  Try running a dictionary attack with 5 attempts every 20 minutes.  Good luck.

So this gives me pretty good ssh security without the restrictions using a key would put on me.

---

### Post by jdong on 2009-04-08
> **kevdog said:**
> Run a port knocker such as fwknop to provide enhanced security measures.  The knock sequence can also use either a password or gpg key.  The password is encrypted and then sent over the wire.  I'm not sure if transmission of the ssh password is hashed or encrypted. Something tells me its still plain text, however I could be wrong.  The password for fwknop is passed in a packet containing other information such as a randomly chosen non-replayable session key, so hence you couldn't replay the packet to gain access to the ssh server even if you were able to isolate the packet containing the password.  I'm not sure if ssh provides such security.


The password is exchanged in an encrypted manner over a challenge-response manner; you cannot replay the login sequence at a later time and expect it to work.

Using a portknocker does make it less obvious that you are running a SSH service, but IMO for most people that fact isn't a big deal.

> 
SSH in combination with rate limiters offered by iptables in combination with tools such as modification of the /etc/hosts files (allow and deny) make up a very secure method to lock down the server.  That is just my two cents.  Port knockers usually don't get mentioned in the same breath as these approaches because they originated as a hacking tool, however with projects such as fwknop they have developed into yet another security measure that can be implemented.

If you're being harassed quite a bit via SSH (I've heard of cases where people can't log in due to the amount of SSH hammering hackers are causing), then a portknocker is a good idea of moving the port doesn't succeed, but IMO it shouldn't be something that everyone should automatically set up. Of course, it doesn't hurt to have it.

---

### Post by Dr Small on 2009-04-08
> **jdong said:**
> Using a portknocker does make it less obvious that you are running a SSH service, but IMO for most people that fact isn't a big deal.

Using a portknocker is quite secure, but it got too boring that I wasn't getting any ssh hits, so I've gotten rid of that and watching DenyHosts now :) (psst! Don't tell kevdog, though ;))

---

### Post by dslink on 2009-04-08
timelox for ssh is a big help to stop brute force...
[http://wwwx.cs.unc.edu/~hays/dev/timelox_and_TheHand/](http://wwwx.cs.unc.edu/~hays/dev/timelox_and_TheHand/)

not sure if it works on linux but i use it on freebsd machines...

---

### Post by kevdog on 2009-04-09
Its always fun to look see when you get hits -- so yes unless you are logging packets, a port knocker does make life more interesting.

> Using a portknocker does make it less obvious that you are running a SSH service, but IMO for most people that fact isn't a big deal.

I would contend that using fwknop's implementation which makes use of iptables -- its actually nearly impossible to detect that a ssh service is running behind the firewall -- not just less obvious.

---

