---
title: "gpg private key export/import"
date: 2009-06-19
forum: Security
---

### Post by zelhar on 2009-06-19
Hey all, 

I created an open pgpg key using "passwords and encryption keyes"
Then I typed a text in gedit, and encrypted it using that key through the gedit encryption addon.

I exported the opengpg key and imported it but it then placed it as a public key and so I can't decrypt the text. What do I have to do so I can decrypt it on another machine ?

---

### Post by blackxored on 2009-06-19
copy the .gnupg from the home directory to the other machine.

---

### Post by zelhar on 2009-06-19
OK I see...

Perhaps then there is a gui app for ubuntu that can just use a pass phrase to encrypt and decrypt ?

---

### Post by kevdog on 2009-06-21
firegpg works with gnupg and google mail.  Thunderbird or Enigmail is a mail program that provides a frontend for gpg and allows for encryption/signing, etc.

---

### Post by zelhar on 2009-06-21
thank you for your advice. 

I found since my last post that kgpg enables exporting of secrete keys through the right-click pop-up menu. it also allows for encrption/decryption of files and texts, and integrates into the dolphin file manager.

---

### Post by kevdog on 2009-06-22
Thanks - I didn't know about kgpg.  I'm not a KDE user (although I would love to check it out), so I was unware of the product.  I'll pass your advice along the next time anyone asks for a GUI frontend.

---

### Post by Agent ME on 2009-06-22
GPG can encrypt with a passphrase instead of using keys, but I don't know of any GUI programs that can do the encryption (I guess that most of them can do the decryption), but doing it via a terminal is very simple.

In a terminal, type "gpg -ca". *(The c means cipher, for symmetric passphrase encryption, and the a means ASCII-armored, so that it can be text-viewable.)*

After you press enter, it will ask you for the passphrase to encrypt with and double check it. After that, type your message (it can be several lines). When you're done, press ctrl-d. GPG will then give you a signed message, looking something like this:

-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.9 (GNU/Linux)

jA0ECQMCrv5AHa/06SNg0l0BUKHoshcsUwLHK3EaSp8QXk4oklJoR626AFLC0/G0
T6HvYrPT2q/o760W3NosYndsHQlE6dw9K1kWXvGOCCrA2Ai8S0WlY2AKgzvRw6tS
FzfWfOFpYnDZrKoHx0s=
=tiv4
-----END PGP MESSAGE-----

The passphrase to that is '123'. You can decrypt it with gpg in the terminal easily.
Simply start gpg in the terminal with "gpg", and copy+paste that text to it. It will immediately ask you for the passphrase. After you enter it, press ctrl-d, and it will give you the decrypted text.


**=======Encrypting files==========**

If you want to encrypt a file with a passphrase instead of a piece of text, simply do "gpg -c *filename*". This will create a file called *filename.gpg*, which is encrypted with the passphrase.
To decrypt *filename.gpg*, enter "gpg *filename.gpg*". It will prompt for the passphrase, and then create the decrypted file with the original filename.

 [SIZE="1"].[/SIZE]

---

### Post by kevdog on 2009-06-23
Its called symmetric encryption versus asymmetric encryption.  Under normal operations GnuPG always uses a hybrid encryption scheme whereby a random session key is used to symmetrically encrypt the data contents.  The session key is the "passphrase".  This randomly generated session key is then asymmetrically encrypted using the public key of the intended recipient.  When the recipient receives the data, the recipient uses the private key to decrypt and recover the session key, which in turn is used as the password to decrypt the original data.

By specifying or using the -c option as you referenced, you basically are bypassing the generation of the session key (since basically you are specifying what key you would like to be used), and also bypassing the asymmetric encryption process.

Just an FYI to provide further details of what is going on behind the scenes.

Please note that I was able to use the GUI program FireGPG to actually decrypt your symmetrically encrypted data.  I did not have to default to using the command line to perform the decryption.

---

### Post by zelhar on 2009-06-23
Kgpg can do symetric encryption too. But it is always good to have a simple command line alternative as well.

---

