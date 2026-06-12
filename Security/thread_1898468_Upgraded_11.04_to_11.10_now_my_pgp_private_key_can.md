---
title: "Upgraded 11.04 to 11.10 now my pgp private key can't decrypt"
date: 2011-12-21
forum: Security
---

### Post by cackerso on 2011-12-21
I use Kgpg.  I had a bunch of keys that I had generated in PGP including my private key.  When I was using 11.04 I just put my sec and pub folders in the .gnupg folder and all the keys were there and I could use them all (private and public).  Since the upgrade to 11.10 I can't decrypt files encrypted with my public key.  The key pair still works in PGP and files encrypted with my public key can be decrypted by PGP in Windows.  But I can't decrypted files encrypted with my public key with the private part of the pair in Kubuntu.

I suppose I could re-install gpg but a lot of other stuff depends on it an I can see some real trouble there. In my .gnupg folder there are secring and pubring folders for both PGP and GPG.

If folks here aren't sure of how to proceed can you direct me to a GNUpg forum that might have an answer?

---

### Post by Paddy Landau on 2011-12-21
I am not an expert on GPG, but as no one has answered you I will give it a bash.

Firstly, reinstalling GPG will do nothing -- that will simply replace the program with itself. It does not reset settings (as, say, Windows would do).

Have you tried importing the keys rather than just placing them in the directory?

---

### Post by jeremywc on 2011-12-21
> **Paddy Landau said:**
> Have you tried importing the keys rather than just placing them in the directory?

This sounds like the issue to me. You need to import the keys into your keyring and set the trust level to ultimate.

---

### Post by cackerso on 2011-12-22
Actually I tried importing the keys.  In fact, I deleted the old key pair and then re-imported them.  I'll try it again but I think something else is going on.

---

### Post by Ex-windows on 2011-12-24
Not sure if this will help but I found this post while searching for my keyring issue. There are a couple of links that seem to have some good info. Hope it helps
[http://ubuntuforums.org/showthread.php?t=1375522&highlight=pgp&page=2](http://ubuntuforums.org/showthread.php?t=1375522&highlight=pgp&page=2)

---

### Post by cackerso on 2011-12-24
I think my problem is a bit different, although I'm out of my depth here.  I get an error message:

You need a passphrase to unlock the secret key for
user: ...
  private key ...

gpg: problem with the agent - disabling agent use
Enter passphrase: 


When I enter the passphrase, I get nothing.

---

### Post by Ex-windows on 2011-12-25
Sorry it didnt help, perhaps an email to the folks at gnome pgp.If I should find any new links I'll post them just in case...
Good luck

Found these by searching for=gpg: problem with the agent - disabling agent use

[http://ubuntuforums.org/showthread.php?t=604092](http://ubuntuforums.org/showthread.php?t=604092)
[http://forums.fedoraforum.org/archive/index.php/t-234903.html](http://forums.fedoraforum.org/archive/index.php/t-234903.html)
[http://kodemaniak.de/?tag=gpg](http://kodemaniak.de/?tag=gpg)

---

### Post by cackerso on 2011-12-26
Thanks for the suggestions.  I tried them all and none work.  I'm not sure how to refer this to someone who has a lot of knowledge about Kgpg, but it seems like it's time to do that.

---

### Post by cackerso on 2011-12-29
Just a note.  On the advice of a knowledgeable person at the Kubuntu forum I referred this problem to KDE as a bug.

---

