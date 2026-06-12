---
title: "Use a public key to decrypt a private-key encrypted message!"
date: 2009-09-25
forum: Security
---

### Post by tenmoi on 2009-09-25
Hi all,

I am reading a book titled Master Openldap and there's this section on openssl/tls and digital certificate. I am just curious as to how this digital signing works so I did some googling around and came across this one: [http://youdzone.com/signature.html](http://youdzone.com/signature.html). 

What's so confusing is this sentence, "Pat's software decrypts the signature (using Bob's public key) changing it back into a message digest". 
What! using a public key to decrypt the signature that was encrypted by a private key! I assume that this man at least knew what he was writing. I googled some more and those tutorials read to the same effect.  

So please help me clear this thing up.

THank you.

---

### Post by Sarmacid on 2009-09-25
Here's how asymmetric encryption works(Or at least how I think it does):

You encrypt a message with a public key and use the private key to decrypt it, so anyone can encrypt a message going to you and only you can decrypt it.

You sign a message with your private key and use the public key to verify the signature, that way any signed messages you send can be verified by anyone.

---

### Post by tenmoi on 2009-09-25
Tx for the quick reply.
But if you read this, "Pat's software decrypts the signature (using Bob's public key)"
How can Pat decrypts the signature with the public key? I know we can encrypt sth with a public key, but we do not and cannot decrypt with the public key.

Or does "decrypt" mean verify? sorry English is not my mother toungue. 
I am wondering how they can verify (if decrypt means verify, too) the signature that is encrypted? do they send the signature to a CA, which then verifies it for them?

Tx.

---

### Post by jflaker on 2009-09-25
Not a very difficult concept, but unless explained correctly, can be confusing

[http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)

---

### Post by tenmoi on 2009-09-25
> **jflaker said:**
> Not a very difficult concept, but unless explained correctly, can be confusing

[http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)

Tx. And yes, it is even more confusing when I read this [http://en.wikipedia.org/wiki/File:Public_key_signing.svg](http://en.wikipedia.org/wiki/File:Public_key_signing.svg)

a sentence quoted from this wiki page: A message that is signed (encrypted) with the private key can be verified (decrypted) with the public key

I now have a basic understanding of asymetric key cryptograpy but am at a loss as to this kind of statements, i.e decrypt with a public key. How can that be done? please help!

---

### Post by doas777 on 2009-09-25
ok, IIRC, the mesage body cannot be decrypted via a public key, but the signature can. that is only logical because the creator signs with their own key, and wants that verification to be vissible to others. when you're talking about messages, you encrypt to the recievers public key, but with a sig, it couldn't use any key but your own. now the reciever needs to verify the authenticity, but the only key she has of yours is is your public one.

jsut remember that signing and encrypting use a differant algorithm and it shoudln't cause you too much cognitive dissonance.

---

### Post by doas777 on 2009-09-25
> **tenmoi said:**
> Tx. And yes, it is even more confusing when I read this [http://en.wikipedia.org/wiki/File:Public_key_signing.svg](http://en.wikipedia.org/wiki/File:Public_key_signing.svg)

a sentence quoted from this wiki page: A message that is signed (encrypted) with the private key can be verified (decrypted) with the public key

I now have a basic understanding of asymetric key cryptograpy but am at a loss as to this kind of statements, i.e decrypt with a public key. How can that be done? please help!


remember encryption has dual purposes when talking about asymmetric PKI. you encrypt to the remote parties public when sending data that you want to keep confidential. I think you have that part down. the other goal is authenticity and tamperproofing. the key system was designed with this in mind. remember with a private key you can discern the public, but not the other way arround. since no one but me has my private key (presumably, anyway) the only key that someone could use to verify me, would be my public.

---

### Post by tenmoi on 2009-09-25
> **doas777 said:**
> ok, IIRC, the mesage body cannot be decrypted via a public key, but the signature can. that is only logical because the creator signs with their own key, and wants that verification to be vissible to others. when you're talking about messages, you encrypt to the recievers public key, but with a sig, it couldn't use any key but your own. now the reciever needs to verify the authenticity, but the only key she has of yours is is your public one.

jsut remember that signing and encrypting use a differant algorithm and it shoudln't cause you too much cognitive dissonance.

Tx. I did not have this cognitive dissonance till I started learning a little bit about digital signing. Maybe it's an acquired syndrome and I do hope to recover real fast. But if you could clear it up for me, I am very grateful. (I now know quite well how people can exchange data secretly and confidentially using public key.)

So you said signing is different from encrypting. I could not agree more according to this youdzone.com/signature.html and this: [http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg](http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg)

The confusion is:
-according to: [http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)
quote "Messages are encrypted with the recipient's public key and can only be decrypted with the corresponding private key"
-according to: [http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg](http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg)
The message digest MD is encrypted with the private key and the result is this number 111**, which must be visible I think.
Now we can use the PUBLIC KEY to DECRYPT the number to come up with this hash 101***, which is then compared with the hash produced by crunching down the data.

My question is, (no, my plea for help) "is the public key capable of decrypting an encrypted message?" I mean I read that it is used for encrypting only. 

:confused:

---

### Post by doas777 on 2009-09-25
> **tenmoi said:**
> Tx. I did not have this cognitive dissonance till I started learning a little bit about digital signing. Maybe it's an acquired syndrome and I do hope to recover real fast. But if you could clear it up for me, I am very grateful. (I now know quite well how people can exchange data secretly and confidentially using public key.)

So you said signing is different from encrypting. I could not agree more according to this youdzone.com/signature.html and this: [http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg](http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg)

The confusion is:
-according to: [http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)
quote "Messages are encrypted with the recipient's public key and can only be decrypted with the corresponding private key"
-according to: [http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg](http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg)
The message digest MD is encrypted with the private key and the result is this number 111**, which must be visible I think.
Now we can use the PUBLIC KEY to DECRYPT the number to come up with this hash 101***, which is then compared with the hash produced by crunching down the data.

My question is (no, my plea for help) is the public key capable of decrypting an encrypted message? I mean I read that it is used for encrypting only. 

:confused:

to the best of my knowledge, no, a public key can only decrypt a signature, not a message. the private key has sufficient information within it to create a cipher that can be opened by the corresponding public key, but only a private key can decrypt a message encrypted against a pubic key. if you sign/encrypt with one, you can only decrypt/verify with the other. 

since I could sign somthing with your public key (as it is easily accessible via PKI) it is not a good way to ascertain that the message came from you (in this case it would have come from me). so using a private key is the only way to tell that it is your signature.

---

### Post by Nepherte on 2009-09-25
It pretty much comes down to this:
[list]
[*]You encrypt a message to "Bob" with Bob's public key. Bob decrypts it with his private key. With this you are sure that only Bob will be able to read the message (unless someone else got access to Bob's private key).
[*]You sign a message to Bob with your own private key. Bob verifies that you're the actual sender of the message with your own public key (unless someone got a hold on your private key).
[/list]

Conclusion: Public keys can be published and are hence public. Private keys should not be published and kept private.

It's pretty logical if you think of it.

---

### Post by tenmoi on 2009-09-25
Tx.
I am wondering how they can "decrypt" the signature with the public key, even though this signature was encrypted by a private key. Are there any special attributes to this signature when it is encrypted TO BE A SIGNATURE? 
:confused:

---

### Post by doas777 on 2009-09-25
> **tenmoi said:**
> Tx.
I am wondering how they can "decrypt" the signature with the public key, even though this signature was encrypted by a private key. Are there any special attributes to this signature when it is encrypted TO BE A SIGNATURE? 
:confused:

well, the message would not be decryptable, whereas the sig would be. thats all. all the special features are contained in the private (it can infer the corresponding public without any additional information). the key is just a cipher string. you can encrypt/decrypt with it at will. the Diffie-hillman algorithm is the only thing saying it can't, and thats just a "business rule". granted, without that rule the whole pki approach falls appart, but hey...

there is nothing stoping you from writing your own software to encrypt all your files agains your own public key. it woulnd't be terribly useful, but you can do it.

---

### Post by tenmoi on 2009-09-25
> **Nepherte said:**
> It pretty much comes down to this:
[list]
[*]You encrypt a message to "Bob" with Bob's public key. Bob decrypts it with his private key. With this you are sure that only Bob will be able to read the message (unless someone else got access to Bob's private key).
[*]You sign a message to Bob with your own private key. Bob verifies that you're the actual sender of the message with your own public key (unless someone got a hold on your private key).
[/list]

Conclusion: Public keys can be published and are hence public. Private keys should not be published and kept private.

It's pretty logical if you think of it.


I know this. But I think the wiki is misleading or incorrect as far as signature certifying is concerned.

I think it goes this way.
1. Sender A sends you his/her certificate signed by XYZ CA.
2. YOu wonder if this certificate is authentic. YOu send it to the XYZ CA asking it to authenticate the certificate.
3. XYZ CA then decrypts the signature with its private key and does other things to verify. If the certificate checks out, the CA tells you, "yes, this cert is authentic". and you start exchanging data with Sender A.

WHat do you think?

---

### Post by doas777 on 2009-09-25
> **tenmoi said:**
> Tx.
I am wondering how they can "decrypt" the signature with the public key, even though this signature was encrypted by a private key. Are there any special attributes to this signature when it is encrypted TO BE A SIGNATURE? 
:confused:

yes, when your software is signing somthing it knows it's signing it. its a different process.

---

### Post by Nepherte on 2009-09-25
> **tenmoi said:**
> I know this. But I think the wiki is misleading or incorrect as far as signature certifying is concerned.

I think it goes this way.
1. Sender A sends you his/her certificate signed by XYZ CA.
2. YOu wonder if this certificate is authentic. YOu send it to the XYZ CA asking it to authenticate the certificate.
3. XYZ CA then decrypts the signature with its private key and does other things to verify. If the certificate checks out, the CA tells you, "yes, this cert is authentic". and you start exchanging data with Sender A.

WHat do you think?
I'm not sure how it works with certificates, but I do know how it works with pgp/gnupg. The message that is sent contains both the normal unencrypted text and a hashed version. The recipient will hash the unencrypted text and see if it matches the hashed text. If the recipient's hashed text is the same as the sent hashed text, you are sure that the message is not altered in any way and that the sender is who he says he is.

---

### Post by solitaire on 2009-09-25
*ignore*

---

### Post by doas777 on 2009-09-25
> **solitaire said:**
> I think it does NOT decypt the signature. 

But the public key creates a signature of the message and compares it to the signature made by the private key. if they checksums match then all's good

But I might be totally wrong...

you encrypt the checksums (or in this case the MD) to prevent tampering, and use your own private key in the signing, so that it can be assured that the message came from you.

---

### Post by tenmoi on 2009-09-25
> **Nepherte said:**
> I'm not sure how it works with certificates, but I do know how it works with pgp/gnupg. The message that is sent contains both the normal unencrypted text and a hashed version. The recipient will hash the unencrypted text and see if it matches the hashed text. If the recipient's hashed text is the same as the sent hashed text, you are sure that the message is not altered in any way and that the sender is who he says he is.

No, anyone can create text data, hash it and send to you the hash and the data. How can I the receiver know if you are who you claim to be? that's why we need a third party here to verify.

---

### Post by Nepherte on 2009-09-25
Because the signed part is based on the private key of the sender. First the message is hashed (usually md5), then the hashed part is encrypted with the private key. The sender does the reverse operation: it decrypts the encrypted part with the public key to get the hashed message. It hashes the original message and compares it with the received decrypted hashed message and sees if they are the same.

Obviously everything stands or falls with the trustworthiness of the public key.

In pgp or gnupg, there is no "third party". All communication and verification happens between the sender and receiver by means of public/private key pairs.

---

### Post by kevdog on 2009-09-25
I wrote a GPG tutorial explaining these advanced concepts.  I really dislike the term public and private because their abilities get thrown around a lot.

Take a look at this writeup (its incomplete and I'm not sure when or if I'm going to finish it):
[http://ubuntuforums.org/showthread.php?t=687173](http://ubuntuforums.org/showthread.php?t=687173)

---

### Post by movieman on 2009-09-25
> **tenmoi said:**
> I am wondering how they can "decrypt" the signature with the public key, even though this signature was encrypted by a private key.

The simplest way to look at it is that if you encrypt something using the public key, then you need the private key to decrypt it, whereas if you encrypt something using the private key, you need the public key to decrypt it. The keys are mathematically linked so that whichever of the two keys you use to encrypt the message, the other key is required to decrypt it.

So if you're sending a secret message to Bob, you encrypt it with Bob's public key, and he then uses his private key to decrypt it. If Bob wants to send a message which allows anyone to verify that it was sent by the holder of that private key, he encrypts the message using his private key, and then people can use the public key to decrypt it; more precisely, in the normal course of events he encrypts a checksum for the message, which people can decrypt and compare to the message to verify that it's genuine.

---

### Post by tenmoi on 2009-09-25
So, according to you, the idea of public-private key cryptography goes like this:

(and "public" still means "known to everyone")

1. I encrypt an MD with my private key to come up with B.
2. Some recipient, with my matching public key, uses it to decrypt B to get back the original MD. This also means anyone with the matching public key can decrypt B, which renders the cryption process useless.

My counter-argument is like this:
A public key is in NO WAY meant for decryption, otherwise the whole foundation of this p-p key crypty thingy is crippled. Anyway, if this were to be the case, what would you need a private key for? Clear-text exchange suffices here.

Of course I am reasoning in the context of the wiki-based information only. I know they can "decrypt with a public key" plus something else, but certainly they won't do it the way explained in the wiki.

---

### Post by doas777 on 2009-09-25
> **tenmoi said:**
> 
2. Some recipient, with my matching public key, uses it to decrypt B to get back the original MD. This also means anyone with the matching public key can decrypt B, which renders the cryption process useless.

first remember, the **message** is ciphered with the **recipients public key.** after that, the md is calculated, and then that value is signed (ciphered)** against the senders private key**. it is sent along side the message, but they are two different units of data. a message and  a signature.

a listening party can decrypt the sig, but not the message. the key is that they can't modify the md. they would have to be able to resign the MD, if they wanted to alter either the message or the digest, because they don't have access to the signing (private) key. 

the signature is designed to allow ANYONE to authenticate the message as coming from you. there is no reason to hide the sig or the md. we dont care who can decrypt it, we just want to make sure no one can change it without being detected. in this case, if they modified the message or the digest or both, they wouldn't be able to reencrypt it, so you would know instantly that hte message had been intercepted and altered. no one can decypt the message except it;s intended reciepient, since it is ciphered by the reciepients public key. only the sig can be checked via the public key.

the general idea at play with signing is that to sign a message, you MUST have access to the private key. If i could sign a message based on your public key, then i could pretend to be you, and that would mean that the system was broken.

---

### Post by tenmoi on 2009-09-25
Eureka! The actual meaning of the proverb "look before you jump" has dawned on me!
I've missed one PARAMOUNT sentence: What is encrypted with a private key can be decrypted with a public key and VICE VERSA. The lesson is "Do not ever encrypt any thing with your private key (excluding where certification is concerned, of course)"; use the public key.

Thank you all. It's been very fruitful discussing with you.

---

### Post by jflaker on 2009-09-26
> **Nepherte said:**
> I'm not sure how it works with certificates, but I do know how it works with pgp/gnupg. The message that is sent contains both the normal unencrypted text and a hashed version. The recipient will hash the unencrypted text and see if it matches the hashed text. If the recipient's hashed text is the same as the sent hashed text, you are sure that the message is not altered in any way and that the sender is who he says he is.

The concept is the same....

I get the server's/user's public certificate the user/server keeps the private certificate....
using the key pairs, the encrypt/decrypt is able to happen...the difference here is that I am using the USER'S (the server's) public certificate as my decypher.....I don't need to have my own, which allows more people to use encryption than pgp/gpg concept.  The most common use of this type of encryption is HTTPS web pages.

---

