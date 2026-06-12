---
title: "block IP after attempts"
date: 2005-03-17
forum: Server Platforms
---

### Post by wxlidar on 2005-03-17
I was looking through my logs the other day and noticed that there are several entries where someone was trying random usernames to login via SSH. I use Firestarter to limit access to the machine to specific IP's, and SSH is the only open service. 

But let's say I want to block an IP after 3 unsuccessful login attempts. How would I do it? I'd like to prevent the person from getting any response from the machine after the 3rd attempt.

Thanks,
Dave

---

### Post by mario8723 on 2005-04-06
Try this:

sudo apt-get install snort

---

### Post by nemin on 2005-04-08
[QUOTE=wxlidar]I was looking through my logs the other day and noticed that there are several entries where someone was trying random usernames to login via SSH. I use Firestarter to limit access to the machine to specific IP's, and SSH is the only open service.[/QUOTE]
First of all, I want to mention you don't have to take this really serious, often these entries come from simple worm attacks.
[QUOTE=wxlidar]
But let's say I want to block an IP after 3 unsuccessful login attempts. How would I do it? [/QUOTE]
Just a thought, you could write a script wich parses the logfiles and block the IP with iptables or /etc/hosts.deny.

---

### Post by jdong on 2005-04-08
I'd have to say that blocking after three unsuccessful attempts is probably an unwise idea, as a bit of spoofing can cause someone to lock your IP out! If you really want to, the shell-script parse to iptables idea is probably your best bet.


If you're worried about brute-force password guessing, SSH has got you covered -- it halts for a good 5 seconds before allowing you to try another password, which will take a ludicrous amount of time even to guess a 3-letter password.

---

### Post by pedrobl on 2005-04-26
Check this page [http://www.pettingers.org/code/SSHBlack.html](http://www.pettingers.org/code/SSHBlack.html). It contains a script that can be used to block IPs (using iptables) after a number (configurable) of failed login attempts. The time (days) the IPs are block is also configurable. 

Very nice script that does just what I needed. Hope that helps...

pedro.

---

### Post by nemin on 2005-04-26
[QUOTE=pedrobl]Check this page [http://www.pettingers.org/code/SSHBlack.html](http://www.pettingers.org/code/SSHBlack.html). It contains a script that can be used to block IPs (using iptables) after a number (configurable) of failed login attempts. The time (days) the IPs are block is also configurable. 

Very nice script that does just what I needed. Hope that helps...[/QUOTE]Thanks for your suggestion, very nice script indeed :) I was looking for such thing either.

---

### Post by jdong on 2005-04-26
I still have no clue why you'd want to...

It takes approximately 5 seconds to try a given username/password combination. If you have a 4-letter username and 4-letter password, it'll take 5((26P4)^2) seconds, or [size=+1]**643,687,200,000 [size=2]seconds,[/size]**[size=2] or in other words, [/size][/size][size=+1]**7,450,083.33 **days[size=2] to try all combinations of 4-letter usernames+passwords.

This grows exponentially with respect to the number of letters in the username or password.


In other words, SSH is already VERY RESISTANT to brute force attacks, and IPTables scripts to block after a number of attempts don't improve security anywhat, but do add an interesting prank:

I know you use IP 123.123.xxx.xxx, so I'll run a script that guesses wrong passwords and spoofs itself to be all 64,000 IP's in that range. Now, you're locked out of your system. In addition, IPTables will have to support 64,000 new rules about IP's that probably don't even exist. Nice denial of service attack.

Congrats, you took a computer with NO SECURITY THREAT, then made it a computer with a VERY REALISTIC denial-of-service vulnerability. See what wonders paranoia does? ;)
[/size][/size]

---

### Post by localzuk on 2005-04-26
The only thing I did (I run a webhosting server with many clients - no ssh access to them though), is disable root log in via ssh. I get around 3 worm attempts a day via ssh trying a variety of rediculous names/passwords.

I wouldn't bother with any other form of blocking if I were you.

---

### Post by sjmurdoch on 2005-07-03
I think that SSH brute forcing is a credible threat as I know of at least two computers in my institution which have been compromised by this kind of attack. Sure, a good password will protect you, but in the case of a shared machine, it is difficult to stop users choosing poor passwords. Blocking hosts if there are too many failed attempts sounds like a reasonable step to take, in addition to encouraging good passwords.

[QUOTE=jdong]I'd have to say that blocking after three unsuccessful attempts is probably an unwise idea, as a bit of spoofing can cause someone to lock your IP out! If you really want to, the shell-script parse to iptables idea is probably your best bet.[/QUOTE]

SSH runs over TCP, so it should not be possible to spoof an connection without sniffing the network between your computer and the Internet gateway. If you are able to trust your LAN and ISP in this respect, this should not be a problem. Still, 3 attempts seems a bit extreme, in case you make a few mistakes in entering your password.

[QUOTE=jdong]If you're worried about brute-force password guessing, SSH has got you covered -- it halts for a good 5 seconds before allowing you to try another password, which will take a ludicrous amount of time even to guess a 3-letter password.[/QUOTE]

During one connection, yes, but SSH brute force tools in the wild run many sessions in parallel. Also, typical attackers will have access to many machines.

---

### Post by LordHunter317 on 2005-07-03
[QUOTE=sjmurdoch]I think that SSH brute forcing is a credible threat as I know of at least two computers in my institution which have been compromised by this kind of attack. Sure, a good password will protect you, but in the case of a shared machine, it is difficult to stop users choosing poor passwords.[/quote]No, it isn't.  You can install programs that force password complexity controls.

>  Blocking hosts if there are too many failed attempts sounds like a reasonable step to take, in addition to encouraging good passwords.It's not, really.  

> SSH runs over TCP, so it should not be possible to spoof an connection without sniffing the network between your computer and the Internet gateway.Which is pretty trivial to do.  You can also do all sorts of blind and bounce attacks without needing to sniff anything in the middle, if you have the proper resources.

> During one connection, yes, but SSH brute force tools in the wild run many sessions in parallel.Not against the same machine though, because there's a limit on how many simulatenous unauthenticated SSH sessions you can have.  It defaults to 10.  Not enough to actively try a large parallel attack.

---

### Post by Fexx on 2005-07-03
Well I havent used snort but

[http://rfxnetworks.net/bfd.php](http://rfxnetworks.net/bfd.php)

BruteForceDetection is good, highly recommend AdvanceFirewallPolicy from there also but as a desktop, you could proberly stick with firestarter.

Vinh.

---

### Post by sjmurdoch on 2005-07-10
[QUOTE=LordHunter317]No, it isn't.  You can install programs that force password complexity controls.[/QUOTE]

These are not always tolerated by users and in most cases security is not the only, or even top priority in an organisation, so forcing password policies is impossible. In my situation, this is not an option. Also forcing password policies often has undesirable consequences, such as users having the same password everywhere, or writing them down. In any case, defence in depth is better, all other things being equal.

[QUOTE=LordHunter317]Which is pretty trivial to do.[/QUOTE]

It depends on the environment. If you trust the network up to the backbone, sniffing anywhere else is almost impossible as the data is travelling far to fast for any standard hardware to sniff.

[QUOTE=LordHunter317]You can also do all sorts of blind and bounce attacks without needing to sniff anything in the middle, if you have the proper resources.[/QUOTE]

I don't see how blind and bounce attacks apply, because these allow you to send single packets and reset connections, but to make an SSH connection you need a complete TCP connection. I am not of aware of any attacks which allows you to get the ISN from the response to a spoofed SYN, or make a connection without the ISN. I am assuming the server produces unpredicatable ISNs in SYN ACKS, but this has been the case on Linux for some time.

[QUOTE=LordHunter317]Not against the same machine though, because there's a limit on how many simulatenous unauthenticated SSH sessions you can have.  It defaults to 10.  Not enough to actively try a large parallel attack.[/QUOTE]

How will this limit help? If it is on unauthenticatated sessions, after entering an incorrect password you close the session, then you open another one and try again. This sounds more like a DoS defence rather than against brute forcing.

---

### Post by LordHunter317 on 2005-07-10
[QUOTE=sjmurdoch]These are not always tolerated by users and in most cases security is not the only, or even top priority in an organisation, so forcing password policies is impossible.[/quote]While I understand the social issues, it doesn't change the fact it's simply retarded to try to implement weak technical countermeasures in response to a political problem.

> Also forcing password policies often has undesirable consequences, such as users having the same password everywhere, or writing them down.SSO is generally a desirable thing.

>  In any case, defence in depth is better, all other things being equal.The problem is, your suggested measures don't actually add any depth.

> If you trust the network up to the backbone,And the majority people don't.

>  sniffing anywhere else is almost impossible as the data is travelling far to fast for any standard hardware to sniff.Acquiring hardware to do it isn't hard.

Besides, all that is irrelevant, as they don't stop bounce or blind attacks.  You don't need to be able to sniff any traffic but your own (which you can conceptually do) in a bounce attack.


> I don't see how blind and bounce attacks apply, because these allow you to send single packets and reset connections,You can do more with them.  Look at the TCP RST attacks that were brought about recently as a form of connection hijacking.  

> but to make an SSH connection you need a complete TCP connection. I am not of aware of any attacks which allows you to get the ISN from the response to a spoofed SYN, or make a connection without the ISN.You can brute-force the connection blindly pretty trivially.

> How will this limit help?It prevents an attacker from trying multiple combinations in **parallel**.  Which slows their attack speed greately.

>  This sounds more like a DoS defence rather than against brute forcing.Yes, but it limits the speed at whcih an attacker can brute force.

---

### Post by LordHunter317 on 2005-07-10
I should point out the fact that the blind and bounce attacks aren't really relevant to the discussion at hand, and so I don't feel like discussing them any further.

It doesn't change the fact that blocking based on IP is a good way to lock yourself out, especially in the face of a clever attacker.

It also doesn't change the fact that the only correct solution to SSH brute-force password attacks is to set a strong password(s).  Doing anytrhing else doesn't assure you that you're really secure.

---

### Post by sjmurdoch on 2005-07-10
> **LordHunter317]Yes, but it limits the speed at whcih an attacker can brute force.[/QUOTE]

Not greatly, since you can avoid the 5 second penalty by closing the connection after each wrong password. This doesn't count towards the 10 unauthenticated sessions in that case.

I just ran a test using [THC-Hydra](http://thc.org/thc-hydra/) and could bruteforce SSH at about 11 passwords per second. You can get most weak passwords with a wordlist of about 4,000 passwords and you could do this at 6 minutes per host. jdong's estimate of 7,450,083 days was unrealistic firstly because you can try a lot more than 1 password per 5 seconds. Secondly because the attacker can probably already work out the username, e.g. root (although not on Ubuntu) or based on a webpage in ~something, or email address. And thirdly because passwords are not chosen uniformly said:**
> It also doesn't change the fact that the only correct solution to SSH brute-force password attacks is to set a strong password(s).  Doing anytrhing else doesn't assure you that you're really secure.

I would say a better solution is to switch to public key authentication only, but I agree that is not always an option. You can never be really secure, but you can aim to choose the appropriate cost/security tradeoff, based on the circumstances.

---

### Post by LordHunter317 on 2005-07-10
[QUOTE=sjmurdoch]Not greatly, since you can avoid the 5 second penalty by closing the connection after each wrong password. This doesn't count towards the 10 unauthenticated sessions in that case.[/quote]Changing it to make it count would be trivial.  You'd do that 10 times and lock yourself out, and everyone else.

In fact, I'm kind of shocked OpenSSH doesn't count a torn-down failed connection against the unauthorized limit.  In fact, I suspect it's a bug if it doesn't.

> I would say a better solution is to switch to public key authentication only, but I agree that is not always an option.Not with untrusted users.  If you're in a situation where you need to implement password policy, then keys likely don't gain you anything long-run, though they will stop brute-force attacks.

---

### Post by sjmurdoch on 2005-07-10
[QUOTE=LordHunter317]In fact, I'm kind of shocked OpenSSH doesn't count a torn-down failed connection against the unauthorized limit.  In fact, I suspect it's a bug if it doesn't.[/QUOTE]

I don't think it is a bug; I think it is designed to prevent memory exhaustion DoS attacks, not brute force password guessing. Limiting the number of unauthenticated open connections is perfectly sensible in this goal as these are the only ones that require state to be stored on the server. This limit will be good at preventing DoS attacks which try to get the server to allocate memory for many open connections. Once the connection has been been torn down, the memory can be freed so they should no longer be counted against the limit. What it does not do is to prevent brute force attacks.

In the default configuration its value is dubious because it introduces a further DoS problem. By keeping 10 sessions open at any time, no one else can log in. I have confirmed this to be the case when I am running my brute force checks.

What does seem stupid, at least to me, is the 5 second delay between password attempts. This provides no obstacle to brute force attacks, as shown with Hydra, but does make it annoying for users with legitimate clients when they mistype their password a couple of times.

---

### Post by Fenton619 on 2007-05-24
Actually, most of these fallacies are already discussed here : [http://www.pettingers.org/code/sshblack-notes.html#notes1](http://www.pettingers.org/code/sshblack-notes.html#notes1)

on the "notes" page of the sshblack page.

---

