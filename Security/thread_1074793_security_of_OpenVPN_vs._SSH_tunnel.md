---
title: "security of OpenVPN vs. SSH tunnel"
date: 2009-02-19
forum: Security
---

### Post by Starship on 2009-02-19
Hello,

I was wondering about the security of OpenVPN and SSH tunnels, respectively.

I'm still pondering about two issues:

(1) If I decide to set up an OpenVPN server using a *static* key (yes, I know that the security buffs will now tell me that static keys are inherently insecure anyway...), will it be vulnerable to a man-in-the-middle attack? I would reckon no, because I assume that if anyone tricked me into trying to connect to a bogus server, he would only receive encrypted rubbish he couldn't decipher without the key. Hence, static keys would automatically act as some sort of authentication, too. Am I correct with that reasoning?

(2) Do I need certificates for SSH logins using key files? If the server doesn't know my public key (which I could keep a secret if I only connect remotely to a machine administered by myself), then no one could lure me into logging into a machine that doesn't know my public key -- hence, no certs required. Again, am I right?

Thanks a lot for your advice,
Starship

---

### Post by cryogen on 2009-03-12
> **Starship said:**
> 
(1) ... Hence, static keys would automatically act as some sort of authentication, too.

Don't count on it.  If I recall correctly, have a look at the tls-auth parameter for help with man in the middle attacks.  openvpn won't even start the handshake procedure unless the tls key is presented by the client.  This has the nice side benefit of making the vpn port silent to scanners as well.

And yes, you probably shouldn't be using static keys in the first place. ;)

> 
(2) Do I need certificates for SSH logins using key file
s? If the server doesn't know my public key (which I could keep a secret if I only connect remotely to a machine administered by myself), then no one could lure me into logging into a machine that doesn't know my public key -- hence, no certs required. Again, am I right?


I'm not entirely sure what you mean here.  SSH and openvpn don't use each others certs or keys, though I suppose you _might_ be able to make them do so if you tried really hard.  You can use any authentication type you wish with SSH (use public key authentication, it's simple to set up), and it will have no effect on openvpn.  If you're thinking about running ssh over the vpn just make sure the ssh server listens on the vpn server address (10.8.0.1 is the default).

---

### Post by HermanAB on 2009-03-13
Note that OpenVPN and OpenSSH both use the same Open SSL libraries from the OpenBSD OpenSSH project ([http://www.openssh.com/](http://www.openssh.com/)).  So inherently they are EXACTLY the same.

Cheers,

Herman

---

### Post by Starship on 2009-03-13
Hi Cryogen, hi Herman,

thanks for the replies. Sorry if I expressed myself unclearly. I do not intend to use OpenVPN and SSH simultaneously -- I was rather comparing them to each other to figure out which one suits my needs better.

What I was asking is
(1) Assuming that I keep my static key really secure (i.e., nobody gets a hold of it), is an OpenVPN with static keys necessarily less secure than one with pub/sec keys? I know that static keys do not offer perfect forward secrecy, but if I am willing to sacrifice that advantage, a static key seems good enough for me for a single-user, point-to-point connection...
What would happen if -- e.g., by DNS spoofing -- someone made me try to connect to a server that is not the one I do want to connect to? He would only receive encrypted traffic he could not decipher without knowing the static key, and the login procedure would fail. Is that correct?

(2) Using SSH, I was also wondering if I need to sign the keys or use certificates to reduce the likelyhood of MITM attacks. From what I have understood, there will be no successful login if the pub/sec key do not match -- which should be obvious. So if a potential attacker doesn't know the private key, he has no chance to log into my box. And if I am tricked into logging into a bogus machine, the attacker would not be able to make any conclusions about my private key? And finally, SSH would not log into the bogus machine because my pub key is not stored on that machine (provided that I do not make my pub key publically available but only copy it to the trustworthy machine I intend to log into)? 

I hope I made myself clearer this time ;) and am looking forward to any replies!

Cheers,
starship

---

### Post by kevdog on 2009-03-13
Im not sure either can protect from MOM attacks, however the likelihood of such an attack is extremely small.  SSH is the poor man's VPN, however it is usually much faster due to less overhead.  If you need to tunnel like 1 or 2 applications, I would probably choose ssh.  If you need every application to tunnel, openvpn is probably your better bet.  I think this is the more relevant question rather than which is more secure!  As Herman said, they both are built from OpenSSL, and so the security levels are similar.

---

