---
title: "Forgotten my gpg password is all lost?"
date: 2008-12-21
forum: Security
---

### Post by geekyhawkes on 2008-12-21
I setup gpg a while ago and have now forgotten the password i used (stupid i know!).  

I remember a the time being forced into entering a password that would meet certain rules but i cannot remember what they were (ie one upper case or special character etc.)

I have a backup copy of my secret key, but i am pretty sure i know the answer to the following question; is all lost with this key now i dont know my password?

If i make a new key for the same gmail account is there any way i can delete the old key off the keyservers?  

Thanks

---

### Post by teddks on 2008-12-21
No, there isn't really anything you can do. The lesson here is, generate revocation certificates as soon as you make a key, in case it gets compromised/you forget the password.

---

### Post by geekyhawkes on 2008-12-22
Does this mean there is no way i can add a second key to the same email account with a new password?  There must be someway i can use gpg on this account by starting over?

---

### Post by teddks on 2008-12-22
> **geekyhawkes said:**
> Does this mean there is no way i can add a second key to the same email account with a new password?  There must be someway i can use gpg on this account by starting over?

Yup, nothing will stop you from doing that. 

But generate a revocation certificate after you make your key, and keep it in a safe place.

---

### Post by Sarmacid on 2008-12-22
> **geekyhawkes said:**
> I have a backup copy of my secret key, but i am pretty sure i know the answer to the following question; is all lost with this key now i dont know my password?
Not everything is lost, it just depends on how patient you are. I once lost my gpg passphrase too, and the only way I managed to get it back was making a couple of scripts to bruteforce it. If there are other ways to do it, I couldn't find them but this one worked for me(it made it A LOT easier that I remembered most of the rules I used to generate the passphrase into first place).

---

### Post by insane_alien on 2008-12-22
your only hope is if you are able to brute force it, although depending on the length of your password this may be impossible using current technology(although you could assist it if you can remember some of the characters in the passphrase, i forgot only the 11th character in mine so a brute force script handled it in less than a second).

a note for the future is to have a set of rules on how you come up with passwords, (an example of an insecure one would be to 1337-ify the name of what you use it for, like U6uN7Uf0rUm5 for your forum password, if anybody reading this has that as their password i would advise changing it NOW.) it should produce a random looking output.

---

### Post by geekyhawkes on 2008-12-22
Thanks guys.  Is there an easy way i can delete the current key from all the key servers?  Trust me, i will make sure i have the password well remembered next time!

---

### Post by Gamma746 on 2008-12-22
Nasty ([http://www.vanheusden.com/nasty/](http://www.vanheusden.com/nasty/)) is a proof-of-concept GPG passphrase recovery program.  You could try that.

---

### Post by geekyhawkes on 2008-12-23
thanks, but i think il just start over lol. brute forcing with no idea of the passphrase could take some time!

---

### Post by tubbygweilo on 2008-12-23
> brute forcing with no idea of the passphrase could take some time!
That is the general idea:)

---

### Post by fjf314 on 2009-02-11
I hate to resurrect a thread, but I'm having a similar issue. I messed around with encryption back when I first upgraded to 8.10 and now I actually need to use it for something but I can't remember my password.

Since I don't need to worry about rescuing any previously encrypted files, I just need to figure out how to delete the old key and start over again. Sadly, I'm fairly stumped with this. System > Preferences > Encryption and Keyrings doesn't seem to offer any options for this. I tried using a Terminal and running "pgp --delete-keys" but it doesn't seem to do anything.

Can anyone help me out with just starting over?

Okay, I actually figured this out. If anyone else happens to be confused and see this post, the commands to delete the keys actually work. If the old key is still listed under Encryption and Keyrings, it's relatively inconsequential. If you go to encrypt something after running it, the generator will pop up prompting you to create a new key. If you do that, the old one will no longer appear under Encryption and Keyring. I guess the slow update of that application confused me.

---

### Post by shane2peru on 2011-02-25
Ok, this is an old thread, I know, but I was wondering if anyone figured out how to use nasty?  both nasty and rephrase are in the repos, running rephrase now, but would like to try nasty, but can't figure out the proper way to run it.  Man page is sparse, and no example of running it.  Hope someone has info on this!

Shane

---

