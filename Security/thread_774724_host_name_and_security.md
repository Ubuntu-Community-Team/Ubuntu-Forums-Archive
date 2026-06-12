---
title: "host name and security"
date: 2008-04-29
forum: Security
---

### Post by pytheas22 on 2008-04-29
By default, the Ubuntu installer will give a machine a host name of "user-desktop," where "user" is the name of the account created during install.  I was wondering if this poses any kind of security risk, because it would give attackers a valid account name that they can use in conjunction with password brute-force attacks against ssh and so on.  Aren't we making it easier for attackers by advertising the name of the default user account?  Or is this not really something to be worried about?

---

### Post by The Cog on 2008-04-29
I agree it's a slight issue - much more of one if you don't use key based authentication and don't use strong passwords.

---

### Post by Monicker on 2008-04-29
I think its a valid point.  Knowing half of a username/password is certainly better than not knowing either; having the just username is arguably better than just the password, since a large number of people tend to use weak passwords. And this is an account which is automatically given sudo privileges.

You can change it during the install, but I am sure many people will not take the time to do so.  They should have the installer prompt for a unique computer name, instead of automatically putting the user account in there; perhaps even go so far as to make sure the hostname cannot contain the initial account name.

---

### Post by cdenley on 2008-04-29
How would a remote user retrieve the computer name from ubuntu? The only way I could think of is if samba is installed.

---

### Post by Dr Small on 2008-04-29
[quote=cdenley]How would a remote user retrieve the computer name from ubuntu? The only way I could think of is if samba is installed.[/quote]

I pose the same question.
Because SSH is not installed by default, and even if it was, the prompt would be user@ip (user is the remote user).

Please show me how this is a valid threat.

Dr Small

---

### Post by pytheas22 on 2008-04-29
> How would a remote user retrieve the computer name from ubuntu? The only way I could think of is if samba is installed.

There must be some way to get the host-name using a port scan, isn't there?  Even if you can't, which would surprise me, many people do you samba.

I opened up my ssh port the other day to the Internet and have been surprised by how often brute-force attacks occur.  In the last twenty-four hours, I've had two.  I have OSSEC running with active-response, so it shuts down any attacks as soon as they start, but I was still a little scared to realize how often people try to break in, because this is just a workstation, behind a proxy, in my house.  If people are trying to brute-force against my desktop machine, it must be much worse for a server on a corporate or academic network.

---

### Post by Dr Small on 2008-04-29
No, Servers generally use stronger security and non-standard ports. It eliminates the scriptkiddie bruteforces drastically.

And no. Portscanning will not tell you the hostname of the victim.

If you are behind a router / firewall, then it is easier to use this to direct requests to your computer. For people behind a router, they generally don't have to worry about Samba opening a port on their computer to the world. It would have to first be opened at the router.

Dr Small

---

### Post by Monicker on 2008-04-29
> **Dr Small said:**
> 

Please show me how this is a valid threat.

Dr Small


Maybe I am just overly paranoid, but I don't see why you would give out that information unnecessarily.

I have read about javascript and java applets that can determine your local ip and local hostname when you view a web page.  Flash was found to have the ability to initiate socket connections on the local machine and be used to port scan the internal network.  Javascript was also found, in theory at least, to be able to connect to the web interface of the typical home router.



Sky is falling threat? Probably not.

Something to be concerned about? I think so.

---

### Post by Dr Small on 2008-04-29
You can always install NoScript and FlashBlock for extra security.

---

### Post by pytheas22 on 2008-04-29
I've also noticed that a lot of the headers for mail I send contain my host name, so anyone I email (or who sniffs and reads my mail while it's in transit) knows it if he wants it.  This is not a big deal, as the chances of someone looking at a mail header and exploiting the information in this way are very, very low, but my understanding of computer security is that no matter how safe you think you are, you should still try to do better.

Anyway, I just wanted to know if this was a legitimate concern (even if there are a lot of more pressing things to worry about).  Thanks all for the information.

---

### Post by pedja_portugalac on 2008-04-30
> **pytheas22 said:**
> I've also noticed that a lot of the headers for mail I send contain my host name, so anyone I email (or who sniffs and reads my mail while it's in transit) knows it if he wants it.  This is not a big deal, as the chances of someone looking at a mail header and exploiting the information in this way are very, very low, but my understanding of computer security is that no matter how safe you think you are, you should still try to do better.

Anyway, I just wanted to know if this was a legitimate concern (even if there are a lot of more pressing things to worry about).  Thanks all for the information.

I also ask myself the same question some time ago. That's why I have changed that automatic naming. On the other hand I have few misunderstandings with chkrootkit and rkhunter warnings. Hardy, from witch I write in this moment have only firestarter, chkrootkit and rkhunter installed apart from the box realize packages and it still warn me about hidden "something" in /dev/  and chkrootkit warning is even worst, it warns me about possible troyan. Scary, isn't it? :lolflag:

---

### Post by brian_p on 2008-04-30
> **pytheas22 said:**
> Anyway, I just wanted to know if this was a legitimate concern (even if there are a lot of more pressing things to worry about).  Thanks all for the information.

Access to your sshd is protected by the very strong password you have chosen or the ssh keys you have set up. Knowing a username on the machine is completely irrelevant and does not affect the security you have in place.

Think in terms of at least thousands of years to brute force a ssh key. ssh probes are short lived, directed against weak security, have no intelligence behind them and stand no serious chance of succeeding.

---

### Post by movieman on 2008-04-30
> **Monicker said:**
> Javascript was also found, in theory at least, to be able to connect to the web interface of the typical home router.

Who needs Javascript? Some home routers can be reprogrammed by an <IMG> tag (see the recent DNS reprogramming attack in Mexico).

While I agree that SSH should rely on strong passwords or keys, I still lean towards giving an attacker as little information as possible; if they don't know your username then it's much harder to try to break in, which is why login programs no longer tell you that you entered an invalid user ID.

---

### Post by cdenley on 2008-04-30
> **movieman said:**
> Who needs Javascript? Some home routers can be reprogrammed by an <IMG> tag (see the recent DNS reprogramming attack in Mexico).

While I agree that SSH should rely on strong passwords or keys, I still lean towards giving an attacker as little information as possible; if they don't know your username then it's much harder to try to break in, which is why login programs no longer tell you that you entered an invalid user ID.

I agree, but how is using your user name as part of your computer name giving up information? As far as I can tell, there is no way to retrieve the computer name remotely unless they are running a server which broadcasts it like samba, or an application such as flash is compromised, in which case they could probably just as easily get a list of users as they can your computer name.

> I have read about javascript and java applets that can determine your local ip and local hostname when you view a web page.

Are you sure you're not talking about [this hostname]("http://www.displaymyhostname.com/")?

---

### Post by Monicker on 2008-04-30
> **cdenley said:**
> 
Are you sure you're not talking about [this hostname]("http://www.displaymyhostname.com/")?

Nope.  The methods were for retrieving the local hostname.

---

### Post by cdenley on 2008-04-30
> **Monicker said:**
> Nope.  The methods were for retrieving the local hostname.

Any reference? Was this a feature or a bug? If it was a bug, was it fixed? If it was a feature, did it retrieve linux hostnames?

---

### Post by movieman on 2008-04-30
> **cdenley said:**
> I agree, but how is using your user name as part of your computer name giving up information?

For one example, if they can get onto your local network and see a bunch of other machine names, that allows them to attack those machines more easily. Now, it may well be that all those machines have the same users listed in their password file anyway so there's no benefit.

I don't know whether it's still the case, but a lot of network services used to have the host name in the banner, which would allow remote access to the name.

---

### Post by brian_p on 2008-05-01
> **movieman said:**
> While I agree that SSH should rely on strong passwords or keys, I still lean towards giving an attacker as little information as possible; if they don't know your username then it's much harder to try to break in, which is why login programs no longer tell you that you entered an invalid user ID.

We're talking about focussed ssh break in attempts here, right? So not your usual automated dross which hasn't any knowledge of the system it is probing.

User ID known and a 2048 bit key to brute force. What is our expectation that this will be done within 1,000,000 years? How about zero? So, a 100% secure account.

User ID unknown so the attacker guesses 100, none of which exist on that machine. Expectation of success? Zero. So again we have a 100% secure account. But not knowing the username hasn't increased security. I'm prepared to give out a list of user IDs used here and reckon it will not detract from the security of ssh communication.

---

