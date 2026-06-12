---
title: "Can't encrypt/decrypt PGP file"
date: 2012-06-09
forum: Security
---

### Post by PDA1 on 2012-06-09
I just "upgraded" to 11.10 and found that I can't do right click encrypt/decrypt file stuff with Nautilus.

How in the world do decrypt my existing files now?!

---

### Post by spynappels on 2012-06-10
There is the Terminal....

---

### Post by Enigmapond on 2012-06-10
I think you need seahorse-plugins in order for nautilus to do that.

---

### Post by ottosykora on 2012-06-11
yes, today called seahorse-nautilus, you can also go to synaptic or software center and search for seahorse, then install all components.

The decryption is simple, still the same procedure with the right click, but beware: encryption in the current version of seahorse-nautilus with the right click is offered, but buggy, it selects random keys from your keyring to which it will encrypt the file.

---

### Post by spynappels on 2012-06-11
Running the encryption/decryption from the CLI is less buggy and almost as simple.

The man page is also worth a look.

[http://www.gnupg.org/documentation/manpage.en.html](http://www.gnupg.org/documentation/manpage.en.html)

---

### Post by PDA1 on 2012-06-11
Seahorse plugins are not available for Ubuntu 11.10

See- [http://askubuntu.com/questions/74067/why-has-seahorse-plugins-been-removed](http://askubuntu.com/questions/74067/why-has-seahorse-plugins-been-removed)


Synaptic Manager doesn't exist in Ubuntu 11.10- only Software Center and Seahorse plugins aren't available there either.

Terminal for decryption/encryption works, but, I don't have the rest of my life to type the commands in for each file. 

Any suggestions?

---

### Post by sudodus on 2012-06-11
> **PDA1 said:**
> Seahorse plugins are not available for Ubuntu 11.10

See- [http://askubuntu.com/questions/74067/why-has-seahorse-plugins-been-removed](http://askubuntu.com/questions/74067/why-has-seahorse-plugins-been-removed)


Synaptic Manager doesn't exist in Ubuntu 11.10- only Software Center and Seahorse plugins aren't available there either.

Terminal for decryption/encryption works, but, I don't have the rest of my life to type the commands in for each file. 

Any suggestions?

You can make aliases for a couple of typical commands, encode and decode, which makes it straightforward to use. Test the alias directly in a terminal window, as this example

[FONT="Courier New"]# gpg -se -r Bob file    # sign and encrypt for user Bob[/FONT]

```
alias encode='gpg -se -r Uncle\ Sam'
```
```
encode file.txt
``` creates the file [FONT="Courier New"]file.txt.gpg[/FONT] (after you have entered a correct passphrase).

```
alias decode='gpg'
```
```
decode file.txt.gpg
```
creates [a copy of] the original file (after you have entered a correct passphrase).

When it works, you can use a text editor and enter the alias commands to your ~/.bashrc file to make the aliases persistent.
```
alias encode='gpg -se -r Uncle\ Sam'
alias decode='gpg'
```

---

### Post by spynappels on 2012-06-11
Elegant. I hadn't considered using alias for this. Very nice indeed.

---

