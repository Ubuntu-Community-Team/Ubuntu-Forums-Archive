---
title: "Change ownership of PGP key"
date: 2009-07-12
forum: Security
---

### Post by JT9161 on 2009-07-12
I recently created a PGP key, and do to always getting an error when trying doing so as a normal user, I had to create it as root. While this allowed the creation to go fine, it leaves me unable to use my key from my normal user account. 

So I ask how I can make use of my key from my normal account ?

When trying to create a key in seahorse I received:
> Couldn't generate PGP key

General error In gpg from the command line:
> gpg: no writable public keyring found: eof
Key generation failed: eof(my apologies if I'm not making much sense, its rather late.)

---

### Post by kevdog on 2009-07-12
Just a few things to consider -- I dont know if these are the answers.  However the keyrings are just files.  Can't you just change the owner and group of the individual files just as you would any other file?

---

### Post by JT9161 on 2009-07-12
> **kevdog said:**
> Just a few things to consider -- I dont know if these are the answers.  However the keyrings are just files.  Can't you just change the owner and group of the individual files just as you would any other file?

Yes I was considering just exporting the key, changing the ownership of the file, and importing it. or uploading it to a key server and importing it from there.

---

### Post by JT9161 on 2009-07-12
Well I managed to export it from root to a .asc and import into my user account as a private key, listed with "gpg -K", But I'm not sure what use it is to me in that state (I'm rather new to cryptography), and it is still not shown in seahorse.

---

### Post by Nkosi on 2009-07-13
I managed to fix the same problem today. My method may be dangerous, there may be a better way, as I'm still a newbie, but seahorse is up and running now.  Here's what I did:
- Uninstalled and "Removed Permanently" the following programs using Synaptic Package Manager:
  * seahorse
  * gnupg
  * gnupg-agent
  * gpgsm
  * gpgv
- Using Nautilus file manager, I manually deleted the configuration files created by those programs (above list) in /etc/ and /home directories
- Rebooted, then re-installed the same programs
- Ran seahorse again and clicked on generate new key and voila, it worked. 

Good luck.

---

### Post by kevdog on 2009-07-13
JT

I think the keyrings that gpg keeps (within ~/.gnupg) are different than the keyrings that seahorse uses.  These are located somewhere else -- in fact I know this for a fact.  The problem is that I don't use seahorse.  I'm sure some forum searching (as it has been mentioned her before) will turn up the answer as to the location of the seahorse keyrings.

---

