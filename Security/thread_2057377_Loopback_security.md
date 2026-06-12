---
title: "Loopback security"
date: 2012-09-13
forum: Security
---

### Post by dotchristopher on 2012-09-13
Hi all!

**I have a question regarding the security of the loopback interface**. *It's particularly vague and deliberately conceptual as I'm  not looking for answer along the lines of (considering the example below)- "well Tor's really secure so you don't have to worry about it" please! I'm happy to clarify where parts are unclear, and will gratefully accept all consignments of tin foil and hat making instructions :)*

**So far as I can tell, anyone who gets hold (read compromises) a user account on a machine can write and read to and from the loopback interface.*Is this bad news?* **

Say you have a service, like many of us do, which speaks to another service on localhost. localhost is an alias to 127.0.0.1, which is the loopback device. Say the service makes a connection to localhost:555 (really, any port). This traffic travels unencrypted, in plain IP (with varying protocols: T_SQL, HTTP, SMB, etc), over the loopback to the service it must contact and the response does the same. 

It is possible to sniff the loopback, e.g: wiki.wireshark.org/CaptureSetup/Loopback

Consider the case where someone has, unknown to you, compromised a user account your machine, (possibly the system account of another unprivileged service, through a vulnerability within the software code of that service). Your attacker can now open a connection to localhost and sniff the loopback device. That connection can be used to read the data traveling over the loopback, which may contain passwords or other sensitive data. From there, the attacker has all she needs- either the data she was looking for or the passwords that may let her get what she seeks.

Is this even a possibility? Or am I just being too paranoid- I do know that it is still possible to obtain user level/shell access through software vulnerabilities (although someone did mention 3.x kernels make it (their highlight) **impossible** *Is this true- the comment is in a post I made for the curious, and I've only made, like 4?* for (at least) system users to gain root access). 

If it is possible, I don't understand how I'd be able to protect against this kind of attack- in the case where the compromised system account is different to the two who are in communication, an encrypted connection over the loopback would (I guess) suffice. But what about if the compromised system account was one of the two involved in the communication? Then the attacker would have access to the encryption method and properties, rendering the whole exercise useless (the key or other encryption property's integrity cannot be verified).

This is particularly important if you consider a simple common setup:

SERVER : OTHERPORT       [e.g. Backend service]
    |  ^
    V  | 
  LOOPBACK
    |  ^
    v  |
SERVER : PORT  <---->  GATEWAY/FW : PORT  <----> INTERNET <----> Loser 

[e.g. Web Service]

The gateway can't have any prior knowledge of malicious traffic, and it would be unwise to trust it to make decisions which affect the security of the server (this is common sense- everything at the server, regardless of theoretical or reported origin, should be untrusted). But the service could easily become compromised. Even if the port is protected through something as complex as access control, the underlying control could become compromised, feeding in packets which should be untrusted through a connection on which only trusted packets are expected. Therefore the port cannot be trusted to remain secure, and neither can anything that can be read by the service bound to the port

If an attacker could come to gain access to a system account they could sit all day and explore otherwise closed ports, attempt to communicate with those ports without anything being logged or counteracted. They could attempt to brute force passwords of services running on common ports, a possibility that is more alarming if you don't detect the initial break in, etc, etc. 

**But here's the catch**- if you do encrypt the loopback traffic between the two services, the web service will need a private key. That private key will need to be readable by, er, the web service (or at least, it will be in the memory of the system at an address the user running the service can request to read), so if the webservice is ever compromised, that particular channel is now open to be read by the attacker. It defeats any and all PK type secured communication to any services which trust the web service port (there might be more than the one communication need present on any given machine than shown in the basic example above). 

Worse, what if a service was 'protected' behind a reverse proxy but relied on a backend which demanded communication over the loopback in plain protocol? What if this service was an OCSP responder- then anyone could arbitrarily alter the status of certificates for which the responder was responsible, just by getting hold of the loopback. What if that service was a database with service generated weak passwords- then anyone watching could either have a go at cracking it where they sat or retrieve the value to a remote system to do the same. 

I've seen IPTABLES can be used to "tag" incoming packets (for example, helping with rate limiting). Could the same mechanism be used to restrict traffic on the loopback to packets which have a corresponding request from the internet? Are there any tricks out there which can help me avoid the loopback? Would using UNIX sockets instead of the loopback suffer from the same transport security 'risks'?


Obviously, care with user accounts is a fundamental must. Thanks for listening, any response whatsoever is appreciated!

---

### Post by CharlesA on 2012-09-13
Physical access == root access. Ensure you user accounts are using strong passwords and you have locked down any services that are accessible from the internet.

I don't believe loopback communication needs to be encrypted because it never leaves the machine. Control physical and remote access if you don't want someone getting on your machine without your permissions/knowledge.

---

### Post by Ms. Daisy on 2012-09-13
If someone has access to loopback, then you've already been compromised. 

You don't install plastic sheeting on the floor to prevent a criminal from tracking dirt in when they break into your house.  Instead you install better locks to prevent the break-in.  Likewise, the basic security wiki might be a good start for figuring out how to prevent a compromise in the first place.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by dotchristopher on 2012-09-14
> **Ms. Daisy said:**
> You don't install plastic sheeting on the floor to prevent a criminal from tracking dirt in when they break into your house.  Instead you install better locks to prevent the break-in.
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

> **CharlesA said:**
> 
I don't believe loopback communication needs to be encrypted because it never leaves the machine. Control physical and remote access if you don't want someone getting on your machine without your permissions/knowledge.


Sincere apologies for the awful formatting here, I can't track down the cause :(

Thanks both for your time and posts! Of course, I understand all of this, and I do take (perhaps) extreme care with machines under my control. Of everything mentioned, AppArmour is perhaps the most interesting, however I don't see much difference between it and properly chroot()ing a service? Would you be able to quickly describe it's advantages please?
@CharlesA, perhaps I didn't describe myself well enough- the loopback traffic never leaves the machine, but what if someone came to you?- surely that loopback traffic, in plain text, would be visible to *any* account on your system (what about cron, lp, sma, uucp, news, colord, mailman, cyrus, www, www-data, etc, etc, all of which could be compromised remotely)? Surely that data could also be replayed, repeating "known unique" transactions or obtaining an authentication token?
[For others with foil hats, please note: here I don't know anything beyond theory]

Whilst I agree with the "better locks" idea as a general principal, sometimes there are instances when it is not possible. I also err towards an attitude that better locks will only keep out the mass of automated and uninspired attempts which aren't designed to lift information from the machine, but instead add it to a botnet or simply trash the disks or data consistency for fun. 
The better locks idea requires that all of the locks around the machine are excellent, and it has been proven that effective management will keep a machine alive despite a barrage of incoming known exploit attempts. Back to the analogy sometimes you require a window, perhaps in another room. Although you can, for example, proxy a less secure service with a tried and tested webserver this isn't bullet proof (does anyone know, for example, how secure the service behind a proxy is from memory overrun or illegal operations being sent to it, and whether this differs for sockets?) - the webserver could be (and in the past, "solid" webservers have been) compromised, again leading to access to the machine. This access in itself wouldn't be dangerous in a properly configured machine beyond the likely loss of the service and configs. But it would allow access to the loopback, which breaks the security advantages UNIX permissions allow (as well as also breaking the rule that true secrets should remain secret even if everything but the key is known- here there is fully another method of finding the data whilst outwardly, the system is "secure"). 

Let's take another example, this time with sensitive data. A common example of this is ActiveSync. Running ActiveSync requires at least two services: 
1. HTTPS Webserver 
2. Backend database for storing the data

Even if the webserver was the only service (and therefore user) exposed to the internet, if someone knew that the machine contained sensitive data (or was able to watch for a pattern of transmissions that correlated to a system signature, leading to the same conclusion), they may be able to compromise the webserver without or, more importantly, before your knowledge (depending on the method of attack very little could be logged by the machine, although I appreciate it is unlikely that *nothing* would appear unless they gained root which you'd hopefully notice). That would allow them to sit on the loopback, find out where the backend was kept (i.e. the port) and brute force or otherwise tease/exploit it open (you might notice the increased resources, they might not be significant, the attacker may be pitching for stealth over speed). That is very bad news. Security updates are, by definition, post-mortem. Someone has analysed the code and noticed a gap. It is safe to assume more exist undiscovered, and not a significant leap to realise that some are discovered and active, some are discovered and active *and* fully unpatched ([http://www.theregister.co.uk/2012/09/03/java_cleanup/](http://www.theregister.co.uk/2012/09/03/java_cleanup/)) and that some might be being kept for when they might be needed.

Alternatively, particularly with more complex systems, they could sit on the lookback and look for passwords or certificates or service definitions/signatures (anyone with a brain here would be unlikely to attempt an attack on a second service, although internally it would not be noticed on 'the wire'- do you log or rate limit your loopback?!), and (regardless of your security rotation policy) authenticate themselves as a valid user. There'd be no point in having the world's most impressive client PK rotation system when you couldn't verify that ONLY the person (assuming she is trustworthy and cautious) to whom you gave the token was the one accessing the service, and the one receiving the updates to continue with this access. You can see that this exploit model could be expanded to systems which run on physically distinct machines, as well as distinct VMs on (a) physical machine(s).

I guess then, what I'm really asking (and thanks for bearing with me whilst I think out loud) is what's the best way to monitor a running (in memory) service/daemon for exploits? Is it possible? I guess I'd also need to check pre-start that the binaries themselves are 'safe'? You might put down plastic if wanted to know whether or not a burglar was present in the first place.

Thanks again, particularly if you'd read this far!

---

### Post by CharlesA on 2012-09-14
If someone is on your machine and you did know authorize it or know about it, the box is compromised.

Secure the box and you will be fine.

Also get in the habit of looking thru your logs.

As for monitoring running processes for exploits - if they are from trusted sources and the exploit isn't a zero-day, they should be patched as part of your normal update process. If an exploit is a zero-day, a patch is usually pushed immediately so plug the hole.

---

### Post by Ms. Daisy on 2012-09-14
> **dotchristopher said:**
> Whilst I agree with the "better locks" idea as a general principal, sometimes there are instances when it is not possible. I also err towards an attitude that better locks will only keep out the mass of automated and uninspired attempts which aren't designed to lift information from the machine, but instead add it to a botnet or simply trash the disks or data consistency for fun. 
**Hence Risk Assessment.  **No one can harden their machines/networks against every threat known to man.  You'll drive yourself nuts if you try. Plus you'll waste all kinds of time and energy (and money in some cases) on something that will ultimately have no effect.

Figure out what the threats are FOR YOU.  Harden your system against the most likely threats.   Yes, you are absolutely vulnerable to a targeted highly-skilled attack.  But what is the likelihood that a highly-skilled attacker even knows you exist, let alone will actually target you? What on earth do you have stored on your server that's worth all that work to steal?  Do you think that maybe banks, governments, defense contractors, etc. are a tiny bit more attractive to target?

To stick with the house metaphor... My house has deadbolt locks, the windows have locks, it's illuminated at night. The house is not impenetrable.  It is secured against the most likely threats to a typical house in suburbia, which are basic burglars looking for quick and simple ways in.  If the best cat burglar decided he needed in my house, he would be inside in about 2 milliseconds.  I could install bullet-proof glass, high-tech motion/ temperature detectors, retinal scanners, perimeter walls, thermite drive erasers, etc.  But the odds of the best cat burglar giving the slightest crap about my house are so extremely low that I don't worry about it.  And the stuff I have in my house is not valuable enough to warrant such extreme security measures anyway.

---

### Post by rookcifer on 2012-09-14
> **dotchristopher said:**
> Sincere apologies for the awful formatting here, I can't track down the cause :(

Thanks both for your time and posts! Of course, I understand all of this, and I do take (perhaps) extreme care with machines under my control. Of everything mentioned, AppArmour is perhaps the most interesting, however I don't see much difference between it and properly chroot()ing a service? Would you be able to quickly describe it's advantages please?

chroot sandboxes were not designed for security and there are *many* ways to break out of them.  They are also limited in their scope and what they can confine.

AppArmor is a MAC system designed for security in mind and it cannot be broken out of unless:

1) The profile is incorrect or too permissive.

2) There is a kernel flaw that allows an attacker to get root, thus bypassing AppArmor all together.  

But no matter what system you use (SELinux, SMACK, Grsecurity), if an attacker has a direct path to a vulnerable portion of the kernel, it's game over.

One solution to this is a true microkernel, but there are really none that are widely available or that have lots of app compatibility.  Moreover, there is usually a performance hit with a microkernel which is why they never got popular in the first place.

There will never be perfect security until we discover a way to formally verify code to prove its correctness.  This is extremely hard (and maybe impossible) to do.

---

