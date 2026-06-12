---
title: "Public-key cryptography question (scenario)"
date: 2007-06-20
forum: Server Platforms
---

### Post by cygnus81 on 2007-06-20
I've been doing some reading about public-key cryptography, and I have one question in mind.

When a client logs in to a server, it encrypts the username & password using its private key before sending them to the server. Then the server uses the client's public key in order to decrypt the message, right ?

Now, if some third-party happens to get a hold of the client's public key, and sniff the connection, it can decrypt the message and get the username & password, right ?

However, the stolen username & password wont help that third-party to log in to the server, since it needs to encrypt them using the private key before sending them to the server, right ?


Now, if all the above happens with the username & passphrase instead of the username & password, than the third-party has the username & passphrase now. It tries to use them to log in, but fails because it cannot encrypt them correctly (becuse it needs the private key to do that). And even if the server is configured to fallback and ask for   a password if the passphrase fails, it will do no good, since the third-party has only the username & passphrase.

However, if the above happens with the username & passphrase & password (the server required both a passphrase and a password and the third-party stole them both), than now this could happen:
* the third-party fails to send the passphrase (because it doesnt have the private key to encrypt it right).
* the server falls back and asks for a password.
* the third-party sends the password, unencrypted.
* the server doesnt try to decrypt the password (because of the fallback) and grants access.

In short, if
* a third-party gets a hold of the public key, and
* the third-party successfully sniffs the username & passphrase & password, and
* the server is configured to fallback
then that third-party can access the server.

Is that scenario possible or did I miss something ?

---

### Post by tact on 2007-06-20
I presume you are talking about ssh and using PKI in that scenario.  Sorry - I have never played in that pool and so don't know explicitly how ssh and PKI work together.

I would think that your description (login is encrypted with private key and decrypted by the server with your public key) cannot possibly be how it works tho.

In normal use, PKI, there are TWO public keys and TWO private keys.   Yours public/private pair and the other person's (servers?) public/private pair.

I would imagine (and as noted above its pure speculation from me here)... that any ssh server will create a private and public key pair.  It will send the public key to any client (legit client or bad guy - does not matter) and ESSENTIALLY keep its private key securely PRIVATE.

The client then encrypts login using the SERVER's public key ...  and the ONLY key that can decrypt that login info is the server's only private key.

On the other side your client would also generate a private and public key pair and pass the public key to the server.   The server can then encrypt any responses to the client using the client's public key.  ONLY the right client with the right private key can decrypt.

---

### Post by dfreer on 2007-06-20
> **tact said:**
> I presume you are talking about ssh and using PKI in that scenario.  Sorry - I have never played in that pool and so don't know explicitly how ssh and PKI work together.

I would think that your description (login is encrypted with private key and decrypted by the server with your public key) cannot possibly be how it works tho.

In normal use, PKI, there are TWO public keys and TWO private keys.   Yours public/private pair and the other person's (servers?) public/private pair.

I would imagine (and as noted above its pure speculation from me here)... that any ssh server will create a private and public key pair.  It will send the public key to any client (legit client or bad guy - does not matter) and ESSENTIALLY keep its private key securely PRIVATE.

The client then encrypts login using the SERVER's public key ...  and the ONLY key that can decrypt that login info is the server's only private key.

On the other side your client would also generate a private and public key pair and pass the public key to the server.   The server can then encrypt any responses to the client using the client's public key.  ONLY the right client with the right private key can decrypt.

Isn't what your describing true to any public/private key auth? SSL, SSH, GPG, I'm pretty sure it holds true across all of them. What you said tact sounds just about right.

---

### Post by tact on 2007-06-20
Hey dfreer,

Yep... I was just speaking from a more general knowledge, general application, of PKI.  As I noted I have no idea how it really works in the kind of specific application the original poster mentions...but should be similar to the general principles.  :)

The biggest risk/threat to a good PKI system is the "man in the middle" attack....  for the original poster - this is where the bad guys fool you into thinking you have your desired server's public key but in reality its their own public key.   

Anything you encrypt with the bad guy's public key can be read by them...  and just possibly the bad guys could act as a relay - sending your messages on to the server and relaying responses back to you.  (reading everything that passes thru them).

This attack is minimised by ensuring you have a trusted source for the public keys that you will place any trust in.

---

### Post by donheff on 2007-06-20
Tact is correct.  All PKI infrastructures rely on parties communicating by sending using the recipient's public key.  Only the recipient can decrypt (with the private key).  The recipient responds using the sender's public key to encrypt - only the sender has the private key to decrypt the response.

---

### Post by cygnus81 on 2007-06-20
OK. Thank you all. You really clarified this. I am pretty new to all this :-)

Any idea then, how ssh works? Is all that done automatically or do I need to do something to make sure ssh uses PKI?

---

### Post by Mr. C. on 2007-06-20
It is actually a little more complex than this.

A challenge is encrypted with the key, and that challenge is sent to the other side to decode.  They keys themselves are not exchanged.

MrC

---

### Post by cygnus81 on 2007-06-21
> **Mr. C. said:**
> It is actually a little more complex than this.

A challenge is encrypted with the key, and that challenge is sent to the other side to decode.  They keys themselves are not exchanged.

MrC

Now I'am confused... You said:
> 
... The server provides a challenge, your **private key** is used to **encrypt** that challenge, and the challenge sent back to the server. The server then takes this authenticator and **decrypts** it using you ***pubic*** key. Therefore the server needs the public key, all the clients you use need the private key.


Isn't the public key (the padlock) used for encryption and the private key for decryption ?

---

### Post by Mr. C. on 2007-06-21
It should be confusing - there was a series of snowballed, logical-swap (client/server, public/private) errors in my previous statement, making them inconsistent and incorrect.  I should have reviewed what I wrote.

The statement should read:

... The server provides a challenge, your **public** key is used to encrypt that challenge, and the challenge sent back to the **client**. The **client** then takes this authenticator and decrypts it using your ***private*** key. Furthermore, the client hashes the combination of session id and challenge,  and sends the hashed value to the server. Therefore the server needs the public key, all the clients you use need the private key.

I'm sorry for the confusion.  My point in this thread's post was that the keys themselves didn't cross the wire.

Thanks for pointing this out.  I've corrected the previous thread.

MrC

---

### Post by dfreer on 2007-06-21
> **cygnus81 said:**
> OK. Thank you all. You really clarified this. I am pretty new to all this :-)

Any idea then, how ssh works? Is all that done automatically or do I need to do something to make sure ssh uses PKI?

SSH by default only uses username/password to authenticate users (although it encrypts that traffic using the servers key's, much like SSL). To use private/public key authentication instead of username/password (which seriously helps with brute force attempts, although probably not as much as fail2ban), you need to generate a keypair for each user, add the public key to ~/.ssh/authorized_keys for each user (not sure of the required syntax in ~/.ssh/authorized_keys, it seems really picky about extra whitespaces before and after the key), and then edit your /etc/ssh/sshd_config. On what to change in /etc/ssh/sshd_config I can't quite remember, sorry about that I'll try to find a guide or look at mine here in a little bit.

But that should give you a quick headsup on what is required.

---

### Post by cygnus81 on 2007-06-21
So if the server has my public key it can encrypt communication in that direction server->client.

But how can I (the client) encrypt the other direction: client->server ? Specifically the username&password I send to login? I mean, I don't have the server's public key, Or do I?

Thank you all for holding on with me 8-[

---

### Post by Mr. C. on 2007-06-21
There are a number of stages and steps involved.

The public/private key pair are usable in both directions.  I encrypt with a private key, you can decrypt with public key.  You encrypt with public key, i can decrypt with the private key.  If the encryption path were this trivial, it would be subject to interception and man-in-the-middle attacks.

First, an encrypted communication channel must be established.  This also provides a unique, encrypted session identifier to be used next.  The basic process is:

[LIST=1]
[*]Client connects to server, and they negotiate SSH protocol
[*]Packet protocol is initiated
[*]Server identifies itself by sending host key, server key, check bytes, methods list.  Both sides create session id which ids this SSH session.  (when you install SSH, a unique key is generated, and is used by the SSH server: it should be clear now that the client has a private key, and the server has its own private key).  You (via the client) have the opportunity to reject or accept this server's ID - that big, nasty-looking warning dialog)
[*]Client creates and sends double-encrypted secret session key; this is encrypted w/server's public host key, and again with server key.  Only server can decrypt this.
[*]Encryption is enabled by both client/server
[/LIST]
Second, authentication occurs over this encrypted channel, using a hashed amalgam of session identifier and key.  Authentication is client-driven (since you have the private key).

Rather than re-writing more of the explanation, have a look at brief description at [http://en.wikipedia.org/wiki/SSH](http://en.wikipedia.org/wiki/SSH), esp. starting with "SSH Architecture."  I also recommend the O'Reilly SSH book, which explains SSH in much more detail.

MrC

---

### Post by tact on 2007-06-21
At some point in the process of any PKI encrypted exchange, public keys (of all participants - server and clients)  have to be either made "public" or at least somehow distributed amongst the participants.

Mr C says his point is that this does not happen down the wire when a session is established and I have no reason to doubt this, but also cannot confirm it  (as said all along I have zero knowledge how SSH or SSL specifically works).

The sourcing/transport/exchange of public keys has to take place BEFORE any encrypted conversation can take place. Thats simple logic if nothing else.  :)

It is in the GETTING of the public key that you must take great care - great care to ensure you have the RIGHT public key for the person you want encrypted dialog with.  

You dont have to take ANY care at all with the right key once you have it.    It does not matter if the RIGHT public key of your friend falls into nasty hands.  No harm at all.  

What matters is that YOU have zero doubt that you have the RIGHT public key, your friend's key, not a fake one slipped in there by the bad guys.

Of course - you must also take great care to keep your PRIVATE key safe and private.  Goes without saying huh?  :)

---

### Post by Mr. C. on 2007-06-21
There are multiple layers:
[LIST=1]
[*]Establishing the secure channel (which does *not* involve your public or private key), and

[*]Authentication (which involves you placing your public key on the server in advance).  Your public and private keys do not get exchanged, nor are revealed.
[/LIST]

It is the server's host key and its server key, plus additional data that is exchanged; you determine acceptance of this connection, and this server information is stored in the client's host table for future connections and verification.

In neither 1 nor 2 are your rsa_id or rsa_id.pub keys exchanged during the protocol.  They don't need to be - you've already had to place your public key *manually* on the server ahead of time.

MrC

---

### Post by cygnus81 on 2007-06-22
OK. Thanks all - I think I've finally got it figured out :)

---

