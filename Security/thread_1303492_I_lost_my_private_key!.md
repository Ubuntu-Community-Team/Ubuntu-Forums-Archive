---
title: "I lost my private key!"
date: 2009-10-28
forum: Security
---

### Post by jimmio on 2009-10-28
I lost my private key file but know my private passcode. How do I decrypt? gpg -d myFile.pgp doesn't work. I have my old public key, but not the private one, and I have no way of decrypting. I also tried creating another key, but they're different.

These files are irrecoverable and on a backup device. Seems the backups don't help if I can't decrypt the files...

Someone help me...

-Jim

---

### Post by insane_alien on 2009-10-28
The whole point of encryption is that you cannot decrypt the information without the private key(or pass phrase depending on the type of encryption)

there isn't any magical way to decrypt the file. i'm afraid there isn't anything we can do.

next time, have a backup of key's i have several copies of mine including a printed version.

---

### Post by jimmio on 2009-10-28
You're telling me... That I can't decrypt my files despite having the public key and the passcode that made the key? I need the private key which I never exported from 9.04?!...

---

### Post by Barriehie on 2009-10-28
> **jimmio said:**
> You're telling me... That I can't decrypt my files despite having the public key and the passcode that made the key? I need the private key which I never exported from 9.04?!...

That's pretty much the idea.  I managed to lose mine also now that info. is backed up, printed out, etc.  See [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

Barrie

---

### Post by Sarmacid on 2009-10-28
Well, pretty much you're done, the only 2 options you have are doing some forensics on your disk and hope the key is still there or make a cluster the size of a building and start bruteforcing it.

---

### Post by jimmio on 2009-10-28
*big sigh* Seems like I only encrypted my backups... so I think I have everything except 2 videos. A lot less worse than I thought.

I just made a new key, synced it with ldap://keyserver.pgp.com and hkp://keyserver.ubuntu.com:11371 and saved out the full key to my backup device. Did I do that correctly? I opened the properties of my key and went to details and exported from there. Is that the full key?

I now use 9.10. I can't figure out how to encrypt/decrypt my files. In 9.04, I used to be able to right click the file and click Encrypt. and then .pgp files would open automatically with the decrypting program, but that doesn't do that anymore. How can I make it do that again?

-Jim

---

### Post by jimmio on 2009-10-28
I figured out how to use the encrypt/decrypt. I had to install a seahorse-plugins package named Decrypt File which added both decryption and encryption to Nautilus. I have to be more careful...

Thanks all

---

