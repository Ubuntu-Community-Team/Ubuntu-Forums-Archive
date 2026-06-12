---
title: "Questions about GPG"
date: 2010-02-16
forum: Security
---

### Post by Th3Professor on 2010-02-16
I haven't used gpg in a while but am getting back into it again.

Beyond the basic encrypt/decrypt functions, which I've managed to pick up and remember, I'm curious to know about some ways of using multiple keys for different contexts.

I understand it is some how possible to have more than one secret key.

How do I create a new secret key but still use it with the same "key ring" that my current secret key is used on?

I understand that "-r" works with designating the recipient but I'm unfamiliar with an option/flag for designating which of my secret keys I'm encrypting it with.

How do I encrypt something using only one of my secret keys?

I would like to be able to designate a "group" of users who will be able to encrypt/decrypt data but without having to include each user in a list of keys. Basically I'd like to have some kind of "shared" key that the group can use so that any time a new person joins the group they can simply use that key to decrypt previously encrypted data as well as new data from within that group.

How might I do that?

Thanks!

---

### Post by jfparis on 2010-02-16
**Generating a second key**

Use the command

```
gpg --gen-key
```Then you list your keys

```
gpg --list-key yourname
```You can then find out the key ideas

**Using the two keys**

One precision: You sign with your key (to certify who the sender is) and you encrypt to the key of somebody else (so only that somebody can read)

When sending an email the only thing you can choose is which key gonna be use to sign the email. The key that will be use to encrypt is the one from the person you are writing to

```
gpg --default-key 83897E12 --sign -r BF4B709E
```In this example:

[LIST]
[*] BF4B709E is the key of the person you write to
[*]83897E12 is one of your two keys
[/LIST]
 You can have encrypt to multiple users by using the -r option several times. So you can have -r THESPECIALKEYID each time so all you email are also encrypted to this special key

When receiving an email, the sender will have encrypted it to one or several keys. You need to have one of those to be able to read it

---

### Post by Th3Professor on 2010-02-16
> **jfparis said:**
> **Generating a second key**

Use the command

```
gpg --gen-key
```Then you list your keys

```
gpg --list-key yourname
```You can then find out the key ideas

**Using the two keys**

One precision: You sign with your key (to certify who the sender is) and you encrypt to the key of somebody else (so only that somebody can read)

When sending an email the only thing you can choose is which key gonna be use to sign the email. The key that will be use to encrypt is the one from the person you are writing to

```
gpg --default-key 83897E12 --sign -r BF4B709E
```In this example:

[LIST]
[*] BF4B709E is the key of the person you write to
[*]83897E12 is one of your two keys
[/LIST]
 You can have encrypt to multiple users by using the -r option several times. So you can have -r THESPECIALKEYID each time so all you email are also encrypted to this special key

When receiving an email, the sender will have encrypted it to one or several keys. You need to have one of those to be able to read it
Thank you for the response.

So basically it looks like adding another secret key is just a matter of generating a new one.

Let's say I have my secret key A and secret key B... if I don't select one when encrypting it defaults to, let's say, key A... so if I want it to encrypt using key B specifically, I have to designate that key with "--default-key", right? (Even if key A is technically the "default" key?)

Can I use a means of designating which key by something other than 3E819A71 type stuff? Like the name or email that is associated with it?

As far as -r (recipient) goes, I understand that I can include multiple individual public keys so those individuals can decrypt a file, what I'm curious about is how to use a "group key" so that if someone new comes along later all they need is the group key and they'll be able to access/decrypt the data. (But this is without requiring multiple individual recipients, only using 1 "group" recipient.) How might that be done?

Thanks for the help!

---

### Post by jfparis on 2010-02-17
Just to be sure we understand each other

When you send an email, you use your key to sign it and you use the key of recipient key to encrypt is (so only those recipient can read it)

The --default-key options gonna be useful for choosing the signing and the -r options gonna be used to specify the recipients

You can use email instead of the key idea, but using the key idea is the only sure way to know which key gpg gonna use if you have more than one key with the same email.

gpg apparently has a "--group" option which might be useful in you case. You will have to read the manual. Never used it

---

### Post by Th3Professor on 2010-02-17
Sorry, I never mentioned anything about sending email. I'm simply talking about the core features of gpg, i.e. from the command line and encrypting/decrypting files (not emails). My reference to names associated with keys might include email addresses but I'm not talking about actually using email. Sorry if that was confusing.

> **jfparis said:**
> Just to be sure we understand each other

When you send an email, you use your key to sign it and you use the key of recipient key to encrypt is (so only those recipient can read it)

The --default-key options gonna be useful for choosing the signing and the -r options gonna be used to specify the recipients

You can use email instead of the key idea, but using the key idea is the only sure way to know which key gpg gonna use if you have more than one key with the same email.

gpg apparently has a "--group" option which might be useful in you case. You will have to read the manual. Never used it

That makes sense, using the key will make sure I select the specific key that I want to use (instead of the email address), which I can see as mixing things up with email address if I have the same address or even a similar one for 2 keys.

"--group"? VERY COOL. I will look into it.

Edit:

Okay I found this:

--group 

Stick in your gpg.conf file:

group name_you_want_to_use = keyid1 keyid2 keyid3 keyid4

What's that all about? Kind of confusing. The man file is too.

---

### Post by Th3Professor on 2010-02-19
bump

EDIT:

...nevermind.

---

