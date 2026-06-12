---
title: "SSH host key question"
date: 2006-05-06
forum: Server Platforms
---

### Post by Azrael on 2006-05-06
I was thinking for a minute and realised I didn't really understand how SSH host keys work. Imagine an SSH server A, an SSH client B, and a man in the middle attacker C sitting on the route in between A and B. What prevents C from recording A's host key and using it as its own when answering to a session started by B? Why is a host key unique? What underlying math ensures this?

I'm tired and I'm going to sleep now. I look forward to reading your enlightening reply in the morning. ;)

---

### Post by LordHunter317 on 2006-05-07
For SSHv2, look up Diffie-Hellman encoding, which is used to protect the session.

---

### Post by Azrael on 2006-05-07
[quote=LordHunter317]For SSHv2, look up Diffie-Hellman encoding, which is used to protect the session.[/quote] I was asking about the host key (e.g. RSA signature). What you are referring to is the session key, I think. From [http://www.oreillynet.com/pub/a/oreilly/networking/news/silverman_1200.html]("http://www.oreillynet.com/pub/a/oreilly/networking/news/silverman_1200.html"): "The Diffie-Hellman method by itself is vulnerable to MITM, however, which is why both the SSH and SSL protocols require that server authentication guard against this."

From [http://en.wikipedia.org/wiki/RSA]("http://en.wikipedia.org/wiki/RSA"):
"RSA can also be used to sign a message. Suppose Alice wishes to send a signed message to Bob. She produces a hash value of the message, raises it to the power of *d* mod *n* (as she does when decrypting a message), and attaches it as a "signature" to the message. When Bob receives the signed message, he raises the signature to the power of *e* mod *n* (as he does when encrypting a message), and compares the resulting hash value with the message's actual hash value. If the two agree, he knows that the author of the message was in possession of Alice's secret key, and that the message has not been tampered with since."

In relation to host keys, I don't understand what the point of the above is. A mitm attacker could just impersonate as Bob and read the resulting signature (hash ^ d mod n) from Alice and relay it to Bob as if it were his own. Bob would know for sure that the message is unaltered, but *so what*? Why would a mitm attacker need to alter the message at this stage anyway? As far as I can see you don't need to alter any data at all in order to intercept and impersonate as Alice (as long as you have control over routing decisions between Alice and Bob).

What am I overlooking? Anyone?

---

### Post by tribaal on 2006-05-07
Well I think what makes the whole thing "secure" is not only the key, but the mixing of Key + hostname/IP. You basically trust a host the first time, then compare subsequent connection info with the info submitted on the first contact.

This way a man-in-the-middle attack is really hard, since you need to have the same IP/hostname *and* the RSA key the victims submitted each other *on their first contact* :)

- trib'

---

### Post by Azrael on 2006-05-07
[quote=tribaal]This way a man-in-the-middle attack is really hard, since you need to have the same IP/hostname *and* the RSA key the victims submitted each other *on their first contact*[/quote]
I hardly see any added difficulty here. Once the attacker is able to acquire a mitm position in the network topology, all traffic between server and client passes through the machine controlled by the attacker, therefore making it trivial for him to detect the ip/hostnames being used and spoof them accordingly.

---

### Post by LordHunter317 on 2006-05-07
[QUOTE=Azrael]I was asking about the host key (e.g. RSA signature). What you are referring to is the session key, I think.[/quote]Yes, which is sort of the point.  The host key is protected because it's never sent over the wire, it's only used to sign the key.  Unlike SSHv1 where you could acquire the host key from a session, SSHv2 currently requires you to either:[list][*]Compromise the machine and steal the keypair (requires root)[*]Factor the public key[/list]Neither are trivial activities.  I should have said this last nite, but was really tired.  I apologize.

> In relation to host keys, I don't understand what the point of the above is. A mitm attacker could just impersonate as Bob and read the resulting signature (hash ^ d mod n) from Alice and relay it to Bob as if it were his own.No, he can't.  He needs the private key to compute the hash.  The hash attached is the hashed value of the unencrypted message, if it were encrypted.  This is why the SHA1 and MD5 collision attacks are a big deal, they allow me to subtitute a random message and violate the integrity of the signature.

>  Bob would know for sure that the message is unaltered, but *so what*?ITYM altered and cryptography is useless without integrity.

> Why would a mitm attacker need to alter the message at this stage anyway?If I intercept an email between the two I change something like "Attack Russia at dawn" to "Attack France at dawn" or equally bad.

> As far as I can see you don't need to alter any data at all in order to intercept and impersonate as AliceYes, you do.  You didn't read the stuff very carefully.  You must have the private key.  The same applies to SSHv2.

> Well I think what makes the whole thing "secure" is not only the key, but the mixing of Key + hostname/IP. You basically trust a host the first time, then compare subsequent connection info with the info submitted on the first contact.Nope.  This just makes it eaiser for to realize a MITM attack is possible.  The real security is in the fact that the private key is nearly impossible to derive/acquire.

---

### Post by Azrael on 2006-05-07
> The host key is protected because it's never sent over the wire, it's only used to sign the key.  In that case I think I may have used the wrong terminology. If you try to establish a SSH session with a server not in your list you'd get a message like this:

The authenticity of host 'ssh.inter.net (12.18.429.21)' can't be established.
  RSA key fingerprint is 98:2e:d7:e0:de:9f:ac:67:28:c2:42:2d:37:16:58:4d.

At first I assumed that this fingerprint/signature was in fact the host key, but I guess the 98:2e:bla:bla:58:4d sequence is actually what is called the *public key*(??) and is the result of (hash ^ hostkey mod n)? Correct my terminology here if I'm wrong.
> [quote] In relation to host keys, I don't understand what the point of the above is. A mitm attacker could just impersonate as Bob and read the resulting signature (hash ^ d mod n) from Alice and relay it to Bob as if it were his own.No, he can't. He needs the private key to compute the hash. The hash attached is the hashed value of the unencrypted message, if it were encrypted.[/quote]Sorry, but I still don't really understand. What hash does the attacker need to compute? Why can't the attacker just relay the above 98:2e:bla:bla:58:4d sequence to Bob? ..brain.. melting... 
> [quote]Bob would know for sure that the message is unaltered, but *so what*?ITYM altered and cryptography is useless without integrity.
> Why would a mitm attacker need to alter the message at this stage anyway? If I intercept an email between the two I change something like "Attack Russia at dawn" to "Attack France at dawn" or equally bad.[/quote] Yes, obviously. What I mean though was that an attacker doesn't *need* to alter anything in order to be mischievous. Being able to just read the data (e.g. usernames and passwords) is of course bad enough.

---

### Post by Azrael on 2006-05-07
I finally found a fairly detailed review of SSH here: [http://www.tacc.utexas.edu/services/userguides/ssh_detailed/]("http://www.tacc.utexas.edu/services/userguides/ssh_detailed/")

I'll need to read it at least one more time.. #-o

---

### Post by LordHunter317 on 2006-05-07
[QUOTE=Azrael]In that case I think I may have used the wrong terminology. If you try to establish a SSH session with a server not in your list you'd get a message like this:[/quote]Acually you *may* get a message like that, depending on certain configuration options and circumstances.  SSH will trust certain keys by default for you.

> The authenticity of host 'ssh.inter.net (12.18.429.21)' can't be established.
  RSA key fingerprint is 98:2e:d7:e0:de:9f:ac:67:28:c2:42:2d:37:16:58:4d.

At first I assumed that this fingerprint/signature was in fact the host key, but I guess the 98:2e:bla:bla:58:4d sequence is actually what is called the *public key*(??) and is the result of (hash ^ hostkey mod n)? Correct my terminology here if I'm wrong.No, it's the fingerprint of the *public key*.  The actual public key is stored in ~/.ssh/known_hosts or /etc/ssh/known_hosts for system-wide known hosts.  The fingerprint is displayed because it's much shorter than the actual key, so it's eaiser for two humans to exchange.  I don't know the fingerprinting scheme used under SSH, but it's essentially some basic hashing scheme.

> Sorry, but I still don't really understand. What hash does the attacker need to compute? Why can't the attacker just relay the above 98:2e:bla:bla:58:4d sequence to Bob? ..brain.. melting... You misunderstand how public-key cryptography works.  I'll give a basic explanation, hopefully it's clearer.

Let's say you and I want to communicate.  I generate a public-private keypair and give you my public key.  You do the same.   To send me an encrypted message, you use my public key to encrypt it, and I use my private key to encrypt it.  The fundamental security assumption here is that the private key is very hard to acquire.  That way, even if an attacker intercepts the encrypted message, they cannot decrypt it.

Now, let's say I want to sign a message to verify the contents weren't tampered.  I sign it with my private key and you use my public key to decrypt it.  **NB:** the keys each party uses here are reversed.  That's how the scheme works: the encryption is done with one public<->private pair, the signing done with the other public<->private pair, in the opposite direction.  So in order to change both halves, you effectively need to be both Alice and Bob,meaning the scheme is already totally broken.

If someone intercepts the encrypted message and changes it, they have to change the signature as well, otherwise I know you tampered.  But to do that requires my private key, which is difficult to acquire.  No one has it but me.

SSHv2 is no different, but what is signed is the Diffie-Hellman exchange.

> Yes, obviously. What I mean though was that an attacker doesn't *need* to alter anything in order to be mischievous.Yes, they do. They have to alter the signature otherwise I know the message was compromised.

---

### Post by Azrael on 2006-05-08
Thanks Lordhunter, your explanation together with the wikipedia article on public key cryptography made me understand. (And feel kinda stupid. :-\")

This bit from the wiki for me was the clearest example:
"In an asymmetric key system, Bob and Alice have separate padlocks. First, Alice asks Bob to send his open padlock to her through regular mail, keeping his key to himself. When Alice receives it she uses it to lock a box containing her message, and sends the locked box to Bob. Bob can then unlock the box with his key and read the message from Alice. To reply, Bob must similarly get Alice's open padlock to lock the box before sending it back to her."

 
An interceptor could impersonate as Bob and do either of the following two:

 *send Alice Bob's padlock, but then the interceptor wouldn't have Bob's private key, so he wouldn't be able to decrypt the message he gets from Alice. The interceptor can pass on the encrypted message to Bob, but Bob will only reply after he gets a padlock from Alice to which only she has the key. The interceptor won't have the private key on either side and, being unable to decrypt anything, he won't be able to take part in any Diffie-Hellman session key exchange, so he can't do any mitm attack.
*send Alice his own padlock. This would enable a succesful mitm attack if this were the first time Bob and Alice attempted communication with each other. If there had been any previous communication, Alice would abort the session because she'd immediately recognize that the padlock she receives this time is a different one from what she usual gets from Bob.

In the end I guess the primary obstacle for me was just getting the semantics/terminology straight...

---

### Post by LordHunter317 on 2006-05-08
Yes.  Public Key crypto is relatively conceptually simple, but all the implementations are inherently complicated (it's very much a simple idea, difficult to actually do thing).  I think what was stopping you was trying to understand based on a implementation, which is always harder. :)

---

