---
title: "Server newbie, questions about SSH keys"
date: 2011-11-28
forum: Server Platforms
---

### Post by darkod on 2011-11-28
I'm fairly familiar with the desktop version but still making my first steps with the server. :)
To help me improve, I'm setting up a home NAS. Nothing special, network storage with open access to all.

I was reading about SSH and using keys, and have couple of questions:
1. If I understood correctly, using keys will still ask me for the passphrase every time I connect. I was under the impression that one characteristic of using keys is not to ask for passwords. If you have the key you get in. :)
Did I understood it right? Will it ask for the passphrase? This will influence the decision how complicated to make the passphrase.

2. Again, if I understood it right, you generate the keys on the client machine and copy the public to the server. I was under the impression that you do it the other way around. You generate on the server, the private stays there, and you copy the same public key to all machines you want access from.

I have a desktop and a netbook, both dual booting Win7 and Ubuntu. That makes a "total" of 4 systems, if we look from that angle.
Does that mean generating 4 pairs of keys? Should I generate on the server anyway and copy the public to all machines?
From win7 I will use Putty which has an option to specify the key, although I haven't used it with keys so far.

Any advice about the easiest way to set it up is welcomed. Thanks.

---

### Post by arrrghhh on 2011-11-28
1. You can choose to enter no passphrase, and it will let you in immediately.  The one caveat here is if someone gets a hold of your private key, they will also have password-less access to your server.  It is recommended you use a passphrase, so if someone does manage to get the key they still have a password to go thru.  You make the choice here, knowing the consequences.

2. Correct, you generate the keys on the client and push them to the server.  ssh-copy-id is the easiest method, as it takes care of 99.9% of the dirty work for you.

I recommend reading the [OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) Ubuntu Community doc.  It took me a while to grasp the concept, I had to read and re-read to really 'get it' ;).

---

### Post by darkod on 2011-11-28
Thanks, I already read that, it helped me understand it better (and produced my questions). :)

I also know about the blank passphrase but didn't consider that. That's why I said it will always ask you, I have no intention leaving it blank.

---

### Post by darkod on 2011-11-28
So, generating the keys on the client is the only way? No options?

If it's the only way, I guess this thread is solved. :)

---

### Post by arrrghhh on 2011-11-28
> **darkod said:**
> Thanks, I already read that, it helped me understand it better (and produced my questions). :)

I also know about the blank passphrase but didn't consider that. That's why I said it will always ask you, I have no intention leaving it blank.

It will always ask for a passphrase if you have one entered.  It'll never ask if you leave it blank ;).

> **darkod said:**
> So, generating the keys on the client is the only way? No options?

If it's the only way, I guess this thread is solved. :)

Well you can create one key on one client and copy them over to the other clients.  Not exactly the best for security either...

---

### Post by Dangertux on 2011-11-28
Just to clarify something -- the passphrase on the key does not effect the strength of the key. It is only there to unlock the key, in the event an attacker obitains it. It is designed to buy you enough time to realize you've been had and generate new keys. It is relatively easy to crack.

---

### Post by darkod on 2011-11-29
> **Dangertux said:**
> Just to clarify something -- the passphrase on the key does not effect the strength of the key. It is only there to unlock the key, in the event an attacker obitains it. It is designed to buy you enough time to realize you've been had and generate new keys. It is relatively easy to crack.

Yeah, I'm aware of that, thanks.

---

