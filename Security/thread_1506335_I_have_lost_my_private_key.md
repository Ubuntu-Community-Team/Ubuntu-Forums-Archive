---
title: "I have lost my private key"
date: 2010-06-10
forum: Security
---

### Post by opengl_cpp on 2010-06-10
Hi guys. 3 moths ago I registered into launchpad and it asked my OpenPGP public key. I installed GPG and created a pair of keys, but when I installed ubuntu 10.04 I lost my ./ssh directory and its content. Now I just have my public key that I once added to launchpad, but my private key is gone. Now I need to know:

1) Is there a way to retrieve my private key?(i dont think so)
2) If I create a new private key, is there a way to relate it to my existing public key or I have to dismiss my public key too
3) What about my signature?
4) How should I protect my public/private keys and signature form loss? can I copy them into somewhere else? how?

I'm a little bit confused with OpenPGP.
thanx

---

### Post by anomie on 2010-06-10
Just to reduce ambiguity a bit, GnuPG is an implementation of the "OpenPGP standard". GPG(2) is the utility that manages keys, encryption, and signing. Henceforth, if you're so inclined, we can refer to the whole ball of wax as GPG. 

[list=1]
[*] No, there is no way to rebuild or recover your secret key (i.e. your private key). 
[*] Not that I know of. 
[*] Ditto. 
[*] Back it up somewhere safe and secure! If you lose your secret key, it's game over. You can either back up your entire ~/.gnupg directory, or you can review the various --export* commands in the gpg(1) manpages.
[/list]

---

### Post by rookcifer on 2010-06-10
> **opengl_cpp said:**
> Hi guys. 3 moths ago I registered into launchpad and it asked my OpenPGP public key. I installed GPG and created a pair of keys, but when I installed ubuntu 10.04 I lost my ./ssh directory and its content. Now I just have my public key that I once added to launchpad, but my private key is gone. Now I need to know:

SSH is not GPG.  Did you mean to type ./ssh or did you mean ./gnupg?  They are different.

And, no, you cannot replace the private key.  Hopefully you created a revocation cert when you created the key so that you can upload it to the key servers.  If not, the key will always be "out there" and listed as active, which is a PITA, but not the end of the world.

Moral of the story: always back up your keys.  Ubuntu One is good for this (give your private key a strong pass phrase then upload your entire ./gnupg folder).

---

