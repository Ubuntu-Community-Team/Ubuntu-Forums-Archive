---
title: "Suggestions for GNuPG frontends?"
date: 2010-06-19
forum: Security
---

### Post by StewartM on 2010-06-19
Hello there,

I'm using Ubuntu Hardy 8.04 on my desktop, and Ubuntu 9.10 on my laptop. I would like to find out what people have found to be the best frontend for using GNuPG (GNU Privacy Guard).

I have downloaded and installed:

Seahorse

Kgpg

GPA

And have used the Seahorse Evolution mail plug-in. Here are is my estimation of their shortcomings.



1) **Seahorse** does not have the ability to encrypt material on clipboards. Seahorse is claimed to "integrate well with Gedit" but I don't see how. Seahorse does integrate with Nautilus, but does not allow ascii output, only binary as far as I can see.

2) The **Seahorse-Evolution** mail plug-in does not:

a) allow one to preview the encrypted content before sending--so unless you checked everything right, you be sending cleartext! (That has happened the first time).

b) Does not allow for encryption requiring keys that have ids not matching any email addresses. Some users do not label their keys by email addresses. There is no "select key" dialogue when using keys.

3) **KGPG**

a) Has a text editor, but does not have a "sign and encrypt" option. You can sign and then encrypt, but not both at the same time. 

b) You can't send a message to multiple users, save yourself and one recipient. Nothing happens when you select multiple users.

c) Does not implement with Nautilus. If it allows for a one-step sign/encrypt and allow for encryption to multiple users using Dolphin (which I've not tried) please let me know.

4) **GPA (Gnu Privacy Assistant)**

Does not allow for multiple recipients at least under Hardy. Selecting more than one key on the keyring when trying to encrypt and sign a file causes it to crash.

What I'd like is a frontend that--

Ideally allows for signing/encryption to be done from the clipboard (using a text editor say) where multiple keys can be chosen if the message was to go to multiple recipients, without having to have key IDs that match any email addresses (like Evolution does). I would also like to preview the results before sending to know that it's been done right. 

Finally, I'd like one where the passphrases I typed in were not hidden--I think hiding your passphrase as you type it in is actually not a good security idea, or at least an overhyped one, because when you can see your passphrases you can and will use longer and better ones. (The counter-argument that either someone might be looking over your shoulder and memorizing what you type, or that a camera could capture the passphrase if it's not hidden, is rather silly IMHO--I mean, if an attacker had access to your computer could install a hidden camera nearby wouldn't be easier to just install a keylogger instead??)

PGP 6.5.8ckt, which I used to use back in my Windows days, did everything I wanted and more, but won't work well under Wine (I can manage older keys with it, but can't encrypt/decrypt even using Notepad as the text editor in Wine). The ideal program I want would mimic what it could do. I also know I could issue the relevant commands in the command line (which I used to do in PGP 2.6.xx) but that's a hassle and still doesn't avoid (I think) the hidden passphrase problem.

Any ideas or comments? :?

StewartM

---

### Post by FuturePilot on 2010-06-19
I use Seahorse.

> Seahorse does not have the ability to encrypt material on clipboards. Seahorse is claimed to "integrate well with Gedit" but I don't see how. Seahorse does integrate with Nautilus, but does not allow ascii output, only binary as far as I can see.
You can add the Encryption panel applet to gnome-panel and it will allow you to encrypt/decrypt content from the clipboard. Make sure you have the gedit-plugins package installed and enable the Encryption plugin in the plugins dialog in Gedit.

---

### Post by StewartM on 2010-06-20
> **FuturePilot said:**
> 
You can add the Encryption panel applet to gnome-panel and it will allow you to encrypt/decrypt content from the clipboard. Make sure you have the gedit-plugins package installed and enable the Encryption plugin in the plugins dialog in Gedit.


Aha! Thank you, thank you! This does almost exactly everything I want---I can now encrypt to multiple recipients, from the text editor, and see the output before copying-and-pasting into Evolution or another client. :cool: I still would prefer the passphrase not being hidden while typed, as I said, but this is much better. (Regrettably, I may have to shorten my passphrasses as I've already forgotten one for a 2.6 legacy key and am in the process of trying to recover it so I can revoke the key--and hiding the typing does not help. (That was before there were programs like Revelation to store passphrases).

Final quesion: is there anyway to word-wrap to 64 characters a line in Gedit? That would be to make sure that clearsigned messages won't be corrupted in transit by the mail or news conduit re-wrapping the messages.:-k

StewartM

---

### Post by StewartM on 2010-06-20
I marked this as "unsolved" just to ask another question.

What does the "Unknown Key: ANSIENTTRANSIENT" Mean in the Seahorse Cache Keys menu? It shows up as a cached key along with my regular key.

I've done some Googling, and it seems that others have experienced this, and that it's a bug in Seahorse, but most of those threads are several years old. I realize I'm still running Hardy (waiting for the Lucid upgrade to be pushed out in July) but still if anyone knew the answer. Having an unknown cached key is not something you would want.

StewartM

---

### Post by WasMeHere on 2010-07-25
thank you stewartm for good questions and
thank you futurepilot for a good answer!

this is valuable also for me

best regards/olle

---

### Post by clevertomato on 2010-08-19
I've been in the same boat as StewartM looking for a good GnuPG frontent. I'm running Lucid. I've looked for the Encryption Panel Applet with no success, and I've installed gedit-plugins even though it lists nothing about GPG keys. What am I missing? I want a GUI app that does all of what StewardM named, but I'm willing to settle for Seahorse and clipboard encryption/decryption.

---

### Post by rookcifer on 2010-08-19
Just curious, why is clipboard encryption important?

---

### Post by clevertomato on 2010-08-20
Clipboard encryption / decryption is handy because every application will never support GPG (heck, the list seems to be shrinking now), so it's always a quick solution to copy to clipboard, encrypt or decrypt, then paste into the same or different application.

---

### Post by clevertomato on 2010-08-20
AHA! Thanks to rww on IRC I learned that there's a package called seahorse-plugins and it apparently includes some functionality that gedit-plugins used to, like the Clipboard Text Encryption applet. It also added the encrypt / decrypt option to the file context menu in Nautilus. This covers much of my "must have" list for GPG. Hopefully this post will help someone else. Why this seemingly basic functionality (that goes along with what Seahorse is already supposed to do) is not included by default, I have no idea.

---

### Post by rookcifer on 2010-08-21
> **shawnboy said:**
> Clipboard encryption / decryption is handy because every application will never support GPG (heck, the list seems to be shrinking now), so it's always a quick solution to copy to clipboard, encrypt or decrypt, then paste into the same or different application.

If I am writing a "Word" document, for instance, I just write it in OpenOffice, save it to disk, then right click it to encrypt it (with GPG).  Likewise, if I am writing an e-mail, my e-mail client has an encrypt and sign button (Thunderbird with Enigmail).

I guess I am just having a hard time seeing where clipboard encryption is really all that handy.

---

### Post by clevertomato on 2010-08-23
rookcifer: What if you're sending an email through a browser on Yahoo! or one of the lesser-known web email accounts? FireGPG apparently used to be great but is now dead. With clipboard you simply type it into ANYTHING encrypt clipboard, then paste. What if you're like me and use Evolution, which has built-in GPG functions, but it sends the encrypted email immediately without letting you confirm visually that you've encrypted it. It's easy to forget that sometimes. This way, you encrypt the clipboard, then past into Evolution (or anything else) and THEN hit send, knowing for certain that your message is encrypted.

If you don't have a need for it, that's great. There are times, however, that some people find it useful.

---

### Post by rookcifer on 2010-08-23
> **shawnboy said:**
> rookcifer: What if you're sending an email through a browser on Yahoo! or one of the lesser-known web email accounts? 

I use Gmail and I have it setup in Thunderbird so I don't have that problem.

Now, I don't think Yahoo allows you to use a third party client, so Thunderbird obviously wont work with it.  If I were going to use Yahoo! or another similar service I would probably write my e-mail in Oo or Gedit and then encrypt it from the command line into ASCII armor format.  From there you can merely cut and paste that into the e-mail.

Just do:

```
gpg -ea my_email.txt

```

Then cut and paste the output into Yahoo!.

---

### Post by clevertomato on 2010-08-25
I'm not quite that proficient with CLI yet, at least not when it comes to GPG. It just seems easier and quicker to do it in a GUI with the clipboard. I found the applet that does it anyway, so we're all happy.

---

