---
title: "Encryption for single file"
date: 2009-12-29
forum: Security
---

### Post by Arla on 2009-12-29
I want to e-mail myself a single encrypted file, while I've looked at using Truecrypt (and I do use Truecrypt for some other things) it seems massive overkill (and probably extra overhead) for a single file.

Looking around gpg seems to be one option, and includes a number of possible front ends to avoid use of terminal (not sure whether this is really important to me or not, but it's something).

Is this a good choice? Are there other better choices?

---

### Post by Sarmacid on 2009-12-29
I think both are fine choices, and I use them both for their different features. However for single files I'd just use GPG.

---

### Post by rookcifer on 2009-12-29
For single files, GPG definitely.  There are GUI front-ends that allow you to simply right-click a file and encrypt it.

---

### Post by Lars Noodén on 2009-12-29
Another vote here for GPG.

---

### Post by BkkBonanza on 2009-12-29
I was reading that Seahorse (which is now installed by default I believe) is supposed to add a plugin for Nautilus to handle gpg encrypting files. I haven't found that though - does anyone know where they hid that in Nautilus?

I use gpg at the command line sometimes but it would be handy to have it by right-click in Nautilus too.

---

### Post by __p1n__ on 2009-12-29
gpg

It's as simple as:

# gpg --recipient "target" --encrypt fname

where target is the name associated with the encryption key on your keyring and fname is the file that you want to encrypt.

No one is a big enough drooler to not be able to handle that.

---

### Post by BkkBonanza on 2009-12-29
Ok. Found the info for Nautilus right-click menu. Google!

I guess when seahorse is installed the plugins don't get installed. You can install them with,

apt-get install seahorse-plugins

After that you have to logout and back in. Then Nautilus will have Encrypt and Sign right-click menu items. And if you choose a .pgp file it will have a Decrypt item.

---

### Post by Arla on 2009-12-30
So, here's where I'm lost (again)

I installed the seahorse-plugins, created a PGP key (under My Personal Keys) and encrypted the file, no problems (yay)

I can (on that same machine) decrypt the file, no problems (yay) however, when I copy the file to my other machine, I can't seem to do anything with it? I exported the PGP key from the first machine, and imported it into the second machine (although I can't get the validity to change from Unknown?) and trying to decrypt the file via Nautilus does nothing? How do I go about decrypting the file (my concern would be if my PC crashes and I have to reload, right now it looks like I wouldn't be able to get access to the file again)

---

### Post by Lars Noodén on 2009-12-30
My guess is that you only exported and transfered one of the keys.  

Both are needed: 
You need the private key to decrypt and the public key to encrypt.

---

### Post by Arla on 2009-12-30
See now I'm even more lost, I only created one key? I have a single PGP key under the "My Personal Keys" on the computer where I encrypted the file. Currently I'm creating a personal key on the recieving computer so I can try to sign the imported key and see if that makes any difference.

---

### Post by gradinaruvasile on 2009-12-30
There is a simple little program called ccrypt that encryptts single files. No GPG keys or anything required. Just 

apt-get install ccrypt

Usage (simplest version, has some other options that can be listed with ccrypt --help):

ccencrypt filename

The file will be encrypted, will have a .cpt extension appended. No need for the extension though, it seems it is only informative, you can rename it as you wish.
Decryption:

ccdecrypt filename

Also there is a Windows version of  ccrypt.

[http://ccrypt.sourceforge.net/](http://ccrypt.sourceforge.net/)

---

### Post by Sarmacid on 2009-12-30
When you generate keys with gpg, it always generates a key pair. So anyone can encrypt with your public key and only you can decrypt with your private key, you can read more on it here [http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)

You can go to the pc where you created the key and open up the passwords and encryption keys program. There select the key and export it. Just take the .asc file into the other pc and double click it, ubuntu should recognize it as a private key and import it for you.

However if you think this is too complicated, you can always use gpg symmetric encryption from the command line, and the only thing you'll have to worry about is the passphrase you assign to it.```
gpg -c file
```

---

### Post by Arla on 2009-12-30
Sarmacid,

Okay, thanks for the help, still trying to get this to work right, on the PC I created the key on, I clicked it and export, got a .asc file, imported that into the other computer and ended up with the key in "Other keys" section of Passwords and Encryption Keys.

However, looking more closely, when I do an export from "Passwords and Encryption Keys" it appears to only export the public key, not the private key, so I'll need to figure that out, think that's the problem.

Edit:

And yes, that would appear to have been the issue, needed to use the Properties > Details > Export option, rather than just File > Export

---

### Post by Sarmacid on 2009-12-30
Right, forgot it wasn't that easy. Go to your key, right click -> properties, details tab and click export.

---

### Post by BkkBonanza on 2009-12-30
Regarding GPG/Seahorse,

When you generate a key it always creates a key pair with both a public key and private key. The public one goes on your public ring and the private on your secret ring. Usually the key listing shows your public ones, which may also have other peoples as well.

When you encrypt something it asks you the receivers and uses the public keys for each receiver to encrypt. Only they can decrypt because only they have the private key to match. The simplest form of this is encrypting for yourself when it uses your own public key and you need your own private key to decrypt.

On your own machine it has no problem because both keys are present and it knows which to use. When you export your key it usually only exports the public key, as that is what gets put on keyservers and shared around. (Look in the exported file and you see it says "public"). So moving that to your other machine is not enough to decrypt a file.

When encrypting files for use by yourself elsewhere you can generate a second key on the other machine and export the public key back to yours, then encrypt with that. (This is considered the right way). 

Or you can copy the ~/.gnupg/secring and ~/.gnupg/pubring files to your other machine so the original key pair is in both places. I think it's generally considered less safe to have private keys kicking around here and there. Some people keep it only on a usb key with them. When using the private key you will know because it will prompt for the passphrase.

There is a command line option for exporting the secret key (--export-secret-key) as well but I don't think it shows up in seahorse. (edit: yes, I see it in can export the complete key from details only). It is a very good idea to have a safe backup for both the secring and pubring files. If you lose the secring then your key-pair becomes useless.

This stuff seems convoluted at first but once you get the hang of it, it's fairly easy to use.

---

