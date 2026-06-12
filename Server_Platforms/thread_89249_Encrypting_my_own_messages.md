---
title: "Encrypting my own messages"
date: 2005-11-12
forum: Server Platforms
---

### Post by rpw on 2005-11-12
Hello,

this is certainly not an ubuntu problem but I'll ask anyway.

Since a few weeks I've got a GPG-key, a private and a public one, that's loaded up on a keyerserver. Since this time I'm mailing only crypted with a friend. And now I just got one problem (maybe a stupid one...):

When I send a mail to this friend that is crypted with his public key, he is (of course) able to encryptd and read it. The same in the opposite direction when he sends me a mail that is crypted with my public key.

And now the problem. I can't read the mail I sended to him from my sendbox. When I try to do I get an error message like this:

Could not parse S/MIME message
gpg: armor header: Version: GnuPG v1.4.1 (GNU/Linux)
gpg: public key is 44xxxxxx
gpg: using subkey 44xxxxxx instead of primary key AExxxxxx
gpg: encrypted with 3072-bit ELG-E key, ID 44xxxxxx, created 2005-01-30
"mailadresse"
gpg: decryption failed: secret key not available

I know only a person (in this case the receiver of the mail) with a private key can encrypt a received mail, but also the sender cannot encrypt his own sended mails?

I'm using Ubuntu 5.10 with the latest updates (system and all installed programs), got GnuPG 1.4.1 and tried it with different mailclients like Evolution, Thunderbird and Sylpheed.

A gpg --list-keys shows me my own key (privat and public) and his public key, that I gave full trusts.

Any ideas what I'm doing wrong or what I can/have to do? I'v searched this forum as well as google, but unfortunatly without a helping result.

Thank's very much,

rpw

---

### Post by Quirky on 2005-11-12
You can't decode a message you have encoded for someone else using their public key. The reason is obvious if you think about it: you don't have their private key. For example, I have the public key for 'Super Mario' and I want to send him a secret message:

```

$ cat message
Hello Mario!
$ gpg -e -r 'Super Mario' message
$ ls message*
message  message.gpg
$ gpg -d message.gpg
gpg: encrypted with 1024-bit ELG-E key, ID BF4956C5, created 2004-03-27
      "Super Mario <mario@nintendo.com>"
gpg: decryption failed: secret key not available

```

In this case, I still have the original message, so I don't really need to decode the encoded version. In your case, you only have the encoded message in your mailer's outbox, which you now have no way to read. Only the person intended to recieve the message can decode it. You need to save a plain text version of the message before sending it, or get the other person to mail you the message again, coded for you this time.

PS. In english 'encrypt' is understood as the the act of changing a plain text message into a coded or ciphered message. 'decrpyt' is the opposite, you take a message that is unreadable and decode it into something you can read.

---

### Post by poptones on 2005-11-12
Saving a plaintext version of the message pretty much defeats the entire point of using gpg, and it also makes your recipient vulnerable to attack. This is NOT a good idea. 

If you are using Evolution, here is the place you check to make sure it saves the message encrypted BOTH to your recipient and to yourself. Thunderbird has a similar option but I am unable to provide a screenshot.

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=poptones]Saving a plaintext version of the message pretty much defeats the entire point of using gpg, and it also makes your recipient vulnerable to attack. This is NOT a good idea. [/quote]How in the world does it do the latter?

---

### Post by poptones on 2005-11-12
Ummm... you are saving messages encrypted to that recipient. Therefore, if you are compromised the attacker will have cleartext messages that have been sent to that person. They also have your private key and your public key. Even without knowing that recipient's private key, having both cleartext and encrypted versions of a message makes the task of cracking them that much easier.

Even if the attacker cannot get your private key, if they have both cleartext and encrypted versions of a message it simplifies decryption.

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=poptones]Ummm... you are saving messages encrypted to that recipient.[/quote]Yes, meaning if the text is what's important, you've loss all security.  But that doesn't necessarily compromise the reciepent in anyway.

> They also have your private keyNope, they won't.  They might get your key ring in a total system compromise, but that doesn't yield the private key, mearely an encrypted form of it that's not trivial to brute-force.

> and your public key.Which is meaningless.

> having both cleartext and encrypted versions of a message makes the task of cracking them that much easier.No, it's not clear at all that really makes a difference in factoring the private key from the public key.

Mostly because we can verify the factoring was done correctly without any message already created by the key.

---

