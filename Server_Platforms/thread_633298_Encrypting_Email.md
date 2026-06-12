---
title: "Encrypting Email"
date: 2007-12-06
forum: Server Platforms
---

### Post by WarholsGhost on 2007-12-06
Hello,

I want to be able to send encryped email through my thunderbird mail browser, is there a way i can do that and can you include a tutorial?

thanks

---

### Post by p_quarles on 2007-12-06
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

---

### Post by josefa on 2007-12-06
If you use Gmail you should be able to encrypt the messages you send and receive through your email client.

[http://mail.google.com/support/bin/answer.py?hl=en&answer=38343](http://mail.google.com/support/bin/answer.py?hl=en&answer=38343).

---

### Post by HermanAB on 2007-12-06
Of course the problem is that the recipient has to use it too...

The only really simple way to have encrypted email, is by setting up your own mail server with webmail on https. Then give all your friends free accounts.  Since SSL is built into all web browsers, all email between users of that server will then be encrypted with zero effort.

The simplest way to to the above is with Citadel.  As a bonus, it will also provide you and your friends with a Forums, Chat and IM.

Cheers,

Herman

---

### Post by michaelzap on 2007-12-06
Er... I think this person is asking how to encrypt email messages, not how to use SSL or something like that to encrypt their connection when sending/receiving email. At least that's what it sounds like to me.

I use GPG with Seahorse to create and manage my key files and the OpenPGP add-on for Thunderbird to easily encrypt/decrypt right in my email program. It's basically the same as PGP for Windows, and you can communicate with people using PGP as well. You do have to exchange keys with the people you correspond with, and they also need a similar setup, but it's very secure and easy to use.

It is a good idea to check your email using SSL, of course (especially to protect your password), but that's a whole other topic.

---

### Post by HermanAB on 2007-12-06
All I'm saying is that if everybody is on the same server and using SSL via a browser, then all email between all parties is encrypted end to end, with zero effort.

The main reason no-one use email encryption, is because it is difficult/inconvenient to use.  A SSL webmail system takes all the hassle away.

Cheers,

H.

---

### Post by michaelzap on 2007-12-06
> **HermanAB said:**
> All I'm saying is that if everybody is on the same server and using SSL via a browser, then all email between all parties is encrypted end to end, with zero effort.

The main reason no-one use email encryption, is because it is difficult/inconvenient to use.  A SSL webmail system takes all the hassle away.


Sort of. The email is probably not encrypted while it's on the server using the system that you describe, however. So if you do not have control of the server (or you lose control of it, it's taken from you, etc.), the email is all compromised.

Likewise email that you send/receive by your method will be unencrypted on your computer if you download it using an email client, but if you only use webmail and make sure that your browser does not cache SSL pages then that's not a problem.

Plus most SSL connections are not very strong encryption (it can be broken).

Depending upon what you're worried about, none of that may matter to you, but it's important to know the vulnerabilities in any system that you use so that you don't wrongly assume that something is secure when it isn't.

---

### Post by HermanAB on 2007-12-07
Exactly, that is why I suggest setting up your own mail server.  That is the only way that you will ever be sure that it is secure.  DIY is the way to go.  Don't trust anybody else.

---

### Post by wieman01 on 2007-12-07
You need to install a package called ["enigmail"]("http://enigmail.mozdev.org/") (in the repositories) next to Thunderbird. It lets you send & receive encrypted emails using GPG. I recommend it as I have been using it successfully for years.

---

