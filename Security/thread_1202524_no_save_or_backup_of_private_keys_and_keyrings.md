---
title: "no save or backup of private keys and keyrings"
date: 2009-07-02
forum: Security
---

### Post by aadx on 2009-07-02
Untill last week I used Windows and PGP for many years. I think I am fairly familiar with PGP.
Last week I installed Ubuntu 9.04 (jauntry; Gnome).
I was happy that with Ubuntu's application "Passwords and keys" I could import my private keyring (pubring.pkr) and my secret keyring (secring.skr) I made quite some time ago with PGP under Windows. The import went without any delay and flawless.

Now I have two problems:
1. I can sign email, but I cannot check signed email and I cannot encrypt email. A pop up shows that it could be because of "a broke pipe". I do not understand that. Maybe someone reading this can help. 

Much more important is however:
2. I cannot save or backup my private keys.  According to the associated Help document there should be a some key for that: 
chapter "Backing up Keyrings", Choose  **Key &#9656; Back up Keyrings**.
I cannot find such key in any GUI.
If an encryption key is meant, OK, I see them, but I am unable to get something like **Backup Keyrings**. I can't even find the words "backup" and "keyring" outside the Help document.
In Synaptic packet manager I saw that gnupg was installed, but a gnup2 was not. So I installed gnup2. Nothing changed. So I removed gnupg2.
I thought a GUI was missing, so I installed libcrypt-gpg-perl. Nothing changed, so I removed it.

If I export a (new test-)key, I  then remove it from the application's list, if I import the key is only the public one. The private key of the pair was nowhere to find. That seems to prove that** it is impossible to save private keys or keypairs**. Of course that makes it to dangerous to use those private keys (you might loose them) and thus useless to encrypt things by using the associated public keys.

Where did I go wrong and/or what can I do to solve the problem(s)?
By the way, I am not realy keen on using a terminal window.

I would really like to get some assitance from you.

Aad van der Arend

---

### Post by aadx on 2009-07-04
May I please ask your attention to the following thread:
[http://ubuntuforums.org/showthread.php?t=1202524](http://ubuntuforums.org/showthread.php?t=1202524)

I really need to save my private keys and keyring.

At the moment I can only use my old PGP private and public keyrings.

I can generate and use a new keypair, but I can only save the public key of the pair. As a consequence the new pair is worthless bearing in mind that the private key can be lost.

Aad

---

### Post by Trebaruna on 2009-07-05
This is just a really elaborate "bump" of yours...

---

### Post by Trebaruna on 2009-07-05
I do not like the GUI. Everytime I click on "synchronize" it tells me a gazillion keys are going to be synchronized without telling me whether it's going to be uploading, or indeed anything about what it's doing. Good thing the GUI is only crafted to serve as a front end of gpg.

Do you have any reason for disliking the terminal? It's fairly easy to export (secret) keys using the command line gpg tool. Just do:
```

gpg --output <file> --export-secret-keys <key ID>

```Use "--armor" to get a human-readable keyfile.

Of course I do not need to tell you that backing up a key is also dangerous: keep it in a secure place!
Please note that using the seahorse GUI really just manipulates gpg and its files. In other words, there's no problem in using both. If you want to backup your keyrings just copy the .gpg files in ~/.gnupg/
To get a better idea of how to use gpg, either look at its manpage ("man gpg" in the terminal) or search the tubes.

The most important thing I take away from your post, though, is that it might be time for you to generate a new key. Check this page for why and how:
[http://www.debian-administration.org/users/dkg/weblog/48](http://www.debian-administration.org/users/dkg/weblog/48)

---

### Post by aadx on 2009-07-05
Trebaruna,

Thank you for your reply. 

You asked for my reason why I dislike the terminal window. My answer is that it is much easier to click on a single button of a GUI to save a key or keyring, than to open a terminal window and to type all kind of language specific commands in the right order and with the right filenames and parameters.
As from about 1970 I have learned some programming languages: Algol, Fortran, Pascal, DOS, (Visual) Basic, Delphi, HTML, PHP. I might forget one or two.
In spite of that I do not understand the command line you wrote. 
[COLOR=Blue]Therefore I think I must learn another language to get familiar with the terminal window and the commands I often see for use therein. 
I would appreciate it if you advised me about the language(s) relevant for use with Linux. UNIX?[/COLOR]

I just found out that I use Seahorse, which appears to be a GUI for GnuPG and which comes with GNOME. 
In Applications > Add/Remove I found another GUI for GnuPG: GNU Privacy Assistent. 
I installed it and I tested GNU Privacy Assistent with keypairs, which I just generated for this purpose.

[B]GNU Privacy Assistent resembles more with the PGP GUI for Windows than Seahorse. 
More important, GNU Privacy Assistent allows a user to make a backup of a specific keypair. 

With both GUI's, exporting and importing is for public keys only.[/B]
[B]With both GUI's, all keys are saved together in two keyrings (pubring.gpg and secring.gpg) in folder <personal folder>.gnupg.
If you move the rings to a different, safe place the GUI's don't show keys anymore. Once you moved or copied the rings back to ~.gnupg the keys are shown again in both GUI's (GNU Privacy Assistent must be closed first).[/B]

Therefore I think GNU Privacy Assistent is the right GUI for me.
Therefore also I think my problems are solved.

Thank you all very much for the assistance.

Aad van der Arend

---

### Post by mihaicn on 2010-03-21
Indeed **GNU Privacy Assistant** is the best choice.

I had used Seahorse until my file system crashed and I wasn't able to recover the secret key. I was just started using gpg and I encrypted a lot of valuable personal information, but I didn't make a backup copy. Seahorse is culpable for that, because when exporting your key you can only export your public key. I didn't knew how important is to backup your secret key, and I wasn't in a hurry to do that. 

Now I saved my encrypted files, along with the public key, hoping someday to find a way to decrypt them by brute force. :p

---

### Post by leonardo_neo on 2010-04-08
> Indeed GNU Privacy Assistant is the best choice.

I had used Seahorse until my file system crashed and I wasn't able to recover the secret key. I was just started using gpg and I encrypted a lot of valuable personal information, but I didn't make a backup copy. Seahorse is culpable for that, because when exporting your key you can only export your public key. I didn't knew how important is to backup your secret key, and I wasn't in a hurry to do that.

Now I saved my encrypted files, along with the public key, hoping someday to find a way to decrypt them by brute force. 

Exactly the same thing happened to me. I am new to PGP and GPG thing. I created my private and public keys and to be on safe side I also 'exported' my keys believing that seahorse is going to backup all the required keys which I could import in future.

Unfortunately after upgrading to 10.04, when I imported my saved keys, I came to know that they are only 'public' keys, and hence useless!

Sad that seahorse GUI can't export personal keys.

Learned a lesson in a hard way :)

P.S.[B]
I just discovered that seahorse GUI can actually export personal keys.[/B] select properties of any key---> Go to 'details'---> press the button next to "export complete key"
This should export the private key.

---

### Post by ratcheer on 2010-04-08
I found this webpage to be invaluable in helping me understand how to safely manage my keys: [http://blogs.koolwal.net/2009/04/01/gpgpgp-part-5-backing-up-restoring-revoking-and-deleting-your-gpgpgp-keys-in-debian/](http://blogs.koolwal.net/2009/04/01/gpgpgp-part-5-backing-up-restoring-revoking-and-deleting-your-gpgpgp-keys-in-debian/)

Tim

---

### Post by thatsmyboy on 2012-04-08
Applications > Accessories > Passwords and Encryption Keys > My Personal Keys > Right Click Account > Properties > Details > Export complete Key > Export

---

### Post by ottosykora on 2012-04-09
+1

can not understand what all people are trying to do.

BTW : the Privacy Assistant work well ,but properly only with gpg2 which again has some compatibility issues so far.

and if it is just for backup, one can simply copy the keyring files. Pasting them back restores the keyring.
If I set up new system, I would spent hours in importing all my keypairs and those 300+ public keys. No thanks, I just copy the keyrings and that is it.

---

### Post by oldos2er on 2012-04-09
Closed, necromancy.

---

