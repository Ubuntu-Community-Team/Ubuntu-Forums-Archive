---
title: "Public/Private Key Placement Thoery"
date: 2009-11-29
forum: Server Platforms
---

### Post by NertSkull on 2009-11-29
So I'm still new to this stuff, but trying to learn fast.  Here is a thought I haven't been able to explain to myself, or found an answer anywhere.

When setting up SSH server/client setups, everything I've read has said have the client generate the private/public keys.  Then put the public key on the server.

Then if you have multiple people accessing the server, you would just keep putting the public keys at the end of the 'authorized_keys' file.

What I don't understand is why not just have the server create the private/public keys.  Then have the server retain ONE private key.  And give out the public key to family/friends/whoever you want to access your server.  That way only one keyset is needed.  Why is it not done this way?  Can it be done this way?

I understand that if the public key is out there anyone could access yourserver, but the same is true if someone steals the individual's private key.  Because the client key is on a computer, if someone stills the private key they will have access to the server, so why not just make them public keys (with the private on the server) and save the hassle of making lots and lots of appends to the 'authorized_keys' file?

I'm sure there is a valid reason, I'm just not seeing it.  The only thing I can come up with is the idea that private keys can have passphrases so only a few people can use them.  But from my understanding most people leave the passphrases blank so they can put them in scripts (or the script itself with the passphrase could just as easily be stolen).  So I'm not sure I buy the passphrase reasoning?

Any thoughts?  Or ideas of where to go to read more on this?

---

### Post by mobilediesel on 2009-11-30
> **NertSkull said:**
> So I'm still new to this stuff, but trying to learn fast.  Here is a thought I haven't been able to explain to myself, or found an answer anywhere.

When setting up SSH server/client setups, everything I've read has said have the client generate the private/public keys.  Then put the public key on the server.

Then if you have multiple people accessing the server, you would just keep putting the public keys at the end of the 'authorized_keys' file.

What I don't understand is why not just have the server create the private/public keys.  Then have the server retain ONE private key.  And give out the public key to family/friends/whoever you want to access your server.  That way only one keyset is needed.  Why is it not done this way?  Can it be done this way?

I understand that if the public key is out there anyone could access yourserver, but the same is true if someone steals the individual's private key.  Because the client key is on a computer, if someone stills the private key they will have access to the server, so why not just make them public keys (with the private on the server) and save the hassle of making lots and lots of appends to the 'authorized_keys' file?

I'm sure there is a valid reason, I'm just not seeing it.  The only thing I can come up with is the idea that private keys can have passphrases so only a few people can use them.  But from my understanding most people leave the passphrases blank so they can put them in scripts (or the script itself with the passphrase could just as easily be stolen).  So I'm not sure I buy the passphrase reasoning?

Any thoughts?  Or ideas of where to go to read more on this?

If the user's public key is on the server and their computer gets stolen, all you do is delete their public key from the server and you don't affect your other users. I believe you can also set it up so certain keys are only allowed from certain IP addresses. That reduces the chance of a client computer being used to log into the server it the client is stolen.

You can try [http://en.wikipedia.org/wiki/Public_key_infrastructure](http://en.wikipedia.org/wiki/Public_key_infrastructure) for a bit more info.

I'm no expert on this so someone else could probably explain better.

---

### Post by Bachstelze on 2009-11-30
One thing you don't understand is that when you use SSH key-based authentication, each user must have a copy of the **private** key on his computer.

From there, the rest is trivial.

---

### Post by BkkBonanza on 2009-11-30
Using a public key for each user allows removing users when they are no longer allowed access. The other way around would mean creating and distributing a new server key every time some users's access permission changed.

Doing it this way is also much more secure. Each client has an identity and the server controls access. Your suggestion would be that each client has keys for the servers it can access and the server has no control. That allows clients to copy the server key and give them away to enemies. Oops.

Adding a key for each user is trivial anyway, just use the ssh-copy-id script on your client and it will automatically login, and add the public key to the authorized users file. First time you need password but after that you can use the key.

---

### Post by NertSkull on 2009-11-30
excellent! thanks everyone, that all makes lots of sense.

---

