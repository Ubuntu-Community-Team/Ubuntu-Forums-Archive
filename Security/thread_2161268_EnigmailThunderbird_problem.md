---
title: "Enigmail/Thunderbird problem"
date: 2013-07-10
forum: Security
---

### Post by Baldrick_NZ on 2013-07-10
Hi there,

So I've successfully installed this onto both my wife's and my PC.

The problem is, neither of us are given the option to 'attach my public key' when we click on 'OpenPGP' when composing an email.

The only options open to us are in the screenshot attached.

Also, when my wife sent me an encrypted email, Thunderbird didn't ask me for her public key. It seems there is nowhere to enter this either??

Any help to resolve this would be much appreciated!

Baldrick[ATTACH=CONFIG]244579[/ATTACH]

---

### Post by Irihapeti on 2013-07-10
I've only ever used it for signing messages, so I'm no expert.

But from what I can see, you need to set it up in the preferences for the email account.

[ATTACH=CONFIG]244580[/ATTACH]

My guess is that it's not something you could change on the fly.

---

### Post by Baldrick_NZ on 2013-07-10
Thanks for the reply!

I was clicking the wrong box, so can now attach the public key.

However, now that I've done this and sent another encrypted email to my wife, when she receives it Thunderbird doesn't ask her for the public key in order to read it. It just displays itself in the encrypted state. The key is attached to the email. 

There is also a message in pink background that says "Open PGP: Error - secret key needed to decrypt message; click on 'Details' button for more information". Clicking on details doesn't offer a solution.

---

### Post by Irihapeti on 2013-07-10
I think that you need to encrypt any message to your wife using _her_ public key. Then she uses her private key to unencrypt it.

Otherwise, if other people need _your_ private key to unencrypt, it would be too easy for it to escape into the wild.

---

### Post by Baldrick_NZ on 2013-07-10
Hmmm... Ok, so now that she has sent me an encrypted message with her public key attached, how would I 'install' it so that my system recognises her key?

I've tried to import the attachment she sent, and I get this message...
> baldrick@baldrick:~/Documents$ gpg --import 0xC31BB208.asc.pgp
gpg: [don't know]: invalid packet (ctb=65)
gpg: read_block: read error: invalid packet
gpg: import from `0xC31BB208.asc.pgp' failed: invalid keyring
gpg: Total number processed: 0


---

### Post by Irihapeti on 2013-07-10
I think that as a rule, public keys are uploaded to keyservers. E.g. if you go to my Launchpad profile, you'll see one there.

If I get a message that's signed by someone (not encrypted), I get prompted to download the public key from a keyserver.

It might be worth your while doing some reading, such as 

[http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)
[http://aplawrence.com/Basics/gpg.html](http://aplawrence.com/Basics/gpg.html)
[http://www.pgpi.org/doc/pgpintro/](http://www.pgpi.org/doc/pgpintro/)

(a random selection from my bookmarks that I've found useful)

I found GPG/PGP rather bewildering to begin with, and still don't quite understand parts of it. So you're not alone. :)

---

### Post by Baldrick_NZ on 2013-07-10
Bewildering, that's the word!

I found this, and have followed the bit regarding exporting to the mit server, for both my wife and I. Still trying to import them now... hasn't returned any results yet - even after 10 mins! 
[HTML]https://nsrc.org/workshops/2009/pacnog6-ws/presentations/exercises-pgp.html[/HTML]

Might have to try one of the other servers tomorrow, as it propogates to other servers within a few hours accoring to the text.

Thanks again for your help!

---

### Post by Baldrick_NZ on 2013-07-10
Wow, this is weird!

My wife can now send encrypted and receive decrypted email from me, but I can only send encrypted to her. Whenever she send to me, it remains encrypted...

Any ideas?

---

### Post by Irihapeti on 2013-07-10
I wonder if she's using the right key. She needs to use your public key.

---

